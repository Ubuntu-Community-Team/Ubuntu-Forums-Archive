---
title: "SSHing to my Public IP suddently stopped working. noob alert"
date: 2015-03-25
forum: Networking &amp; Wireless
---

### Post by jeff124 on 2015-03-25
Hi,

I have recently been using a computer running xubuntu 12.04 to run some of numerical codes for my research. 

I have a desktop and a raspberry pi, which are both connected to my router via ethernet cables. I use the desktop for the numerical codes, and my raspberry pi as a media center as well as a way to send wakeonlan commands to my desktop remotely. 

I was able to remotely connect to both using port 22 for my raspberry pi and port 27 for the desktop. I had remotely connected successfully to both on my network and at my girlfriends place, which is off the network. Additionally, I was able to use my personal hotspot of my Iphone to connect to both. I am currently using a laptop using windows 8, putty (to run the code), and filezilla (to transfer codes and results), but while transferring a set of results my connection died. I tried reconnecting (ssh) both on putty and filezilla, and the connection always timed out. 

I was able to connect to the raspberrypi, still, and from there I was able to ssh on the network to the desktop. I tried restarting ssh and restarting the computer, but I am still unable to ssh in via the public ip. I can only ssh into the raspberry pi on port 22 and then ssh on the network by typing in ssh jeffrey@192.168.1.6 -p 27. What gives? What happened to my desktop?

Best,

Jeff

---

### Post by TheFu on 2015-03-26
Did you setup static IPs for both systems on the LAN?

---

### Post by jeff124 on 2015-03-26
I remember that the raspberry pi was set up on a static IP, but I am not sure if the desktop was. I don't know how to remotely check the original IP that the ports were forwarded to on my router.

Would the IP change while the computer was still on and while I was still connected? 
Also, if the Ip changed, how was I able to SSH on LAN thru my raspberry pi? 
NOTE: ssh jeffrey@192.168.1.6 -p27 worked, but ssh jeffrey@192.168.1.6 did not work. Why did the port have to be specified over LAN?

Thank you.

---

### Post by TheFu on 2015-03-26
> **jeff124 said:**
> I remember that the raspberry pi was set up on a static IP, but I am not sure if the desktop was. I don't know how to remotely check the original IP that the ports were forwarded to on my router.

Would the IP change while the computer was still on and while I was still connected? 
Also, if the Ip changed, how was I able to SSH on LAN thru my raspberry pi? 
NOTE: ssh jeffrey@192.168.1.6 -p27 worked, but ssh jeffrey@192.168.1.6 did not work. Why did the port have to be specified over LAN?

Thank you.

I don't know why the IP might have changed - you didn't say ANYTHING about not rebooting or that a static IP was set initially. If you leave out important details, it is hard to help with relevant questions/actions.

What did you do? Can you please post the config files for sshd_config and interfaces? No comments please and please, please,please use "CODE tags" so things line up.

---

