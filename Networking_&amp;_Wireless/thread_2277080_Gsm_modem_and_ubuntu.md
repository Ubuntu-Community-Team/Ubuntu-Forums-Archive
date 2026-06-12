---
title: "Gsm modem and ubuntu"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by Efstratios_Kinikli on 2015-05-06
Hello,

I am new to ubuntu and i would require some help in order to set a system that i need.My hardware is the odroid xu3 board , huawei e1750 gsm modem and the pixhawk autopilot board.The basic idea is to forward all the information from the pixhawk to a the internet to a specific ip through the gsm modem.On the other side a software will  connect to that ip in order to retrieve these information.The pixahawk is connected to the odroid by usb .The operating system  is the lubuntu 14.04.My Huawei modem comes assigned with an ip.I have managed to make the modem work with the ubuntu thus i have full connection to the internet.

As i mentioned i want to forward all the information form the pixhawk to the internet.I believe that i need to set some kind of server using the public ip provided my provider but im not sure how can i achieve that.So what im trying to find is how can i create this server that all the information from pixhawk will be forward too.

Im really confused of how this communication can be established.

The further that i reached till now is to find in what prot is my device connected by using : dmesg grep | tty
and the use the command mavproxy.py --master=/dev/ttyACM0 --baudrate 57600 --out IPADDRESS:14550 in order to forward these.

How can i find my ip adress that the info will be sent to and how can i make sure that connection is established.

Any kind of help or idea will be really usefull.

Thank you

---

