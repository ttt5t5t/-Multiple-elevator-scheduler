# -Multiple-elevator-scheduler
 Scheduling multiple elevators in Siemens s7-1500 series PLC, programming by SCL 

**part 1 single elevator control
1.1  Elevator Scan Algorithm**
    Elevator always running between the highest and lowest call floor.
    We can divide the elevator into three running states： 1：UP  -1：DOWN  0：Idle
    whenever the elevator reach the highest or lowest calling floor，it MUST change its running direction. If there is no call anymore，turn to Idle.
    **Which floors should elevator to stop at？**
    The elevator internal call, External calls in the same direction，and the opposite external call in further direction（if exist）
    now we can calculate target floor. Generally, elevator calls can change at any time, so we only calculate the next target floor.
**1.2 Elevator Door Control**
    if elevator reach the target floor, now we should open the door and let passengers in or out.
    when the door open compeletly，we must clear the internal、external call of same direction、external call of opposite direction（if exist）
    after a few seconds, close the door and calculate the next target.
    **DO NOT calcu target before door closed.**
