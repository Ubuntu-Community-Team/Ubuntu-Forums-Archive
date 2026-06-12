---
title: "Huawei E220 Keeps disconnecting"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by irfad on 2010-06-12
I have installed ubuntu 10.04, When I connect my Huawei e220 it didn't detect as a modem but as CDROM. So I did the following trick
> 
First ejected the modem from the icon and ran these commands

rmmod usb-storage
rmmod usbserial (This showed me an error)

modprobe usbserial vendor=0×12d1 product=0×1003

and it detects now in the Wireless Broadband Connection Manager and I configured and it connects with internet. 
While i browse it desconnects suddenly. It happen time to time. After I cannot reconnect unless I physically remove and pluge it again. 

Any solutions? :confused:

---

### Post by irfad on 2010-06-29
I also havin the same problem. please someone help :mad:

---

### Post by irfad on 2010-06-30
Bump

---

### Post by bumanie on 2010-06-30
Go and download these files and install them - think you have to install 'data' one first. If you get a dependencies error, install them the opposite way around.
usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb
This should cure the problem.

---

### Post by irfad on 2010-07-06
I still have the problem. modswitch works fine. it detects as modem. but after sometime i connect suddenly disconnects and cannot reconnect unless i removed and plug in again. even sometimes it wont work.  please help me with this. it's really a pain in my back :cry: plzzzzzzzzz.........

---

### Post by irfad on 2010-07-07
Any solutions?

---

### Post by irfad on 2010-07-15
Someone help me. Still am having the problem!!!

---

### Post by gandaran on 2010-07-15
> **irfad said:**
> Someone help me. Still am having the problem!!!
you shouldn't have run those commands, installing usb-modeswitch first would have fixed the issue, now maybe the fix is to undo those commands but sorry I don't know how to.

---

### Post by gerymate on 2011-07-17
I have (and had) the same problem here. I recognized that the disconnection occurs much rarely if there is network traffic through the modem. So any time I connect through the modem, I also start up a terminal, and initiate a connection with a keep-alive server:

*ping -i9 [www.some-web-server-that-responds.com](www.some-web-server-that-responds.com)*

This command sends and receives a ping message once in every 9 seconds. This is somehow enough for the Huawei modem to keep the connection alive most of the time, and even sometimes it still disconnects, I can normally reconnect after the disconnection. So I keep open this terminal and keep running this command until I shut down the computer. This is a temporary solution for the Huawei problem described above.

---

