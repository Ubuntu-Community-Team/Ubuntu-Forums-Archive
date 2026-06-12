---
title: "blutoothdevice"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by Viswanathan_R on 2011-08-25
I am using ubuntu 10.10.

RFCOMM connect and listen failed.

I am trying to connect the bluetooth and collect the data from the bluetooth device and store it in a file using the command.

From hcitool scan -> i was able to detect the bluetooth device. 
I was able to able to bind the bluetooth device using command rfcomm -A bind <device address> <bindaddr>

bind address is sucessfull. if you type rfcomm you will notice the bind address

Problem
*******
1. when i tried to connect to the bluetooth device using rfcomm connect <bind address> I am getting the error message no route to the host. Let me know why i am getting this error if i am able to detect and bind the address.

2.  What is the command to used to store the packet received in file. rfcomm listen will receive the packet. I want to see the contents of the each received packet?

3. what is the command to check the content of the packet being transmitted?



Regards,
Vichu:P

---

