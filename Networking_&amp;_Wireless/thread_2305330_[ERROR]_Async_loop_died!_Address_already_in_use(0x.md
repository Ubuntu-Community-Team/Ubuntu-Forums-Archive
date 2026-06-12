---
title: "[ERROR] Async loop died! Address already in use(0x62)"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by beginner3 on 2015-12-04
I'm on Ubuntu 14.04 lts and got this problem when I tried to connect port 6703 or 6702   [ERROR] Async loop died! Address already in use(0x62) and as i got that is due to conflict in ports by searching found someone wrote that is due to

ephemeral port range was messed
up on the machines 
tried to increase /proc/sys/net/ipv4/ip_local_port_range 1024 65000

but not working
How can I solve it ?

---

### Post by matt_symes on 2015-12-05
Hi

Have you checked to see what is using those ports ?

sudo netstat -plant | egrep "6703|6702"

Kind regards

---

### Post by beginner3 on 2015-12-06
yes i checked it but it listening to my process "java" it worked for a moment then stop suddenly and got that there are another processes !! but this no another except mine , i'm working on ubuntu via vmware could it be a problem with ports ?

---

### Post by matt_symes on 2015-12-06
Hi

> **beginner3 said:**
> yes i checked it but it listening to my process "java" it worked for a moment then stop suddenly and got that there are another processes !! but this no another except mine , i'm working on ubuntu via vmware could it be a problem with ports ?

I don't understand. Let's start at the beginning.

What are you trying to run that should use ports 6702 and 6703 ? It's a Java based application ? What's it called ?

What was the name of the other process that started when you program stopped ?

I don't think the fact you're using vmware should cause you problems with ports.

Kind regards

---

### Post by beginner3 on 2015-12-06
i'm using storm "open source" it's suppose to submit my project with java code to storm with port 6703 or 6702  . every port gave me same message with same result 

i used  your command  before submit gave nothing as i think it's mean empty 
after submit gave me process on java 
tcp        0      0 0.0.0.0:6703            0.0.0.0:*               LISTEN      10213/java    
l
log file of storm  denotes that some result i received but stop and gave me this error that the port used with another process

---

### Post by matt_symes on 2015-12-07
Hi

> **beginner3 said:**
> i'm using storm "open source" it's suppose to submit my project with java code to storm with port 6703 or 6702  . every port gave me same message with same result 

i used  your command  before submit gave nothing as i think it's mean empty 
after submit gave me process on java 
tcp        0      0 0.0.0.0:6703            0.0.0.0:*               LISTEN      10213/java    
l
log file of storm  denotes that some result i received but stop and gave me this error that the port used with another process

I know nothing about storm but i would suggest you use the project's help.

I assume this is the correct website ? 

[http://storm.apache.org/documentation/Home.html](http://storm.apache.org/documentation/Home.html)

If so then look at the "Getting help" section and IRC (/j #storm-user on freenode).

Kind regards

---

