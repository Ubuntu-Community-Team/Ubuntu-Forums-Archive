---
title: "help needed in Internet connection in ubuntu"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by nageshrk on 2010-07-05
hi, 

i have installed new ubuntu 10.04, 

i have tried the below steps for internet connection.

1> Switch off your modem
 2>Open the Network settings Dialog box ( System>  Administration> Network)
 3>Select  ‘Wired Connection’ and click on  the Properties.
 4> In the ‘Connection Settings’ Menu select  ‘Static IP ‘ type in  the following values and save:
 IP Address : 192.168.1.2
 /* Assigning the Ethernet Card an IP different from that of the  modem*/
 Subnet Mask: 255.255.255.0
 /* No idea why this value is always this [IMG]file:///G:/Ubuntu%20%20BSNL%20Broadband%20Connection%20%C2%AB%20With%20the%20left%20and%20the%20right%20%E2%80%A6_files/icon_smile.gif[/IMG]  */
 Gateway address: 192.168.1.1
 /* The Modem is being made the default gateway*/
 5>Switch on the Modem and wait for a few minutes for the values to  get recorded.


i am using bsnl broadband connection. 



it shows as wired connection is connected. 



when i try to open in firefox is not openinig.


what do i need to do.


please help me

---

### Post by mikewhatever on 2010-07-05
You don't seem to input anything into DNS fields. Try your gateway address there.

---

### Post by dineshs on 2010-07-05
When you are manually configuring NM try to assign an IP outside the DHCP range.Pl try this
step-1
Configure NM in [COLOR="Blue"]Automatic DHCP[/COLOR] then restart
ping default gateway (say 192.168.1.1)```
ping -c3 192.168.1.1
```
step-2
If there is reply configure your modem as in
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) under modem/CPE configurations and see whether pages are loading
If there is no reply try to configure NM as follows
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 4.2.2.1
then click apply 
Now proceed as in step-2

---

