---
title: "wi-fi not working"
date: 2015-11-12
forum: Networking &amp; Wireless
---

### Post by art12 on 2015-11-12
Today is a big day for me. For the first time I installed Linux Ubuntu on my old, but capable laptop. I love the idea of this OS. I am also willing to learn a lot, test, improve, support and maybe latter on develop. 

Everything is new to me regarding this OS. 

The first problem I encountered today is that there seems to be no way of connecting to wi-fi internet, as it is very important for me to continue my journey on Ubuntu. 

I have gone through a several threads regarding this issue, but i was no capable of solving this issue on my own. 

I noticed people asking to submit key phrases or commands into the terminal, I also noticed that a user called chil555 was a good problem solver on issues related to wi-fi connectivity. 

Can ayone, please, help me out here. 

P.S. I noticed that people with similar issue as mine were asked to input a two line command/phrase into the terminal. Do you type in the first line, hit enter, and then type the second line and hit enter? or do you use ; or \ in between them?

---

### Post by grahammechanical on 2015-11-12
So, you have noticed that this forum has a Networking & Wireless section. That is the best place to post questions of this kind. If you wish that chili555 give you advice, then posting in the Network & Wireless section is the best place to get his attention.

We need to know what version of Ubuntu you are using. It is important that we know if you are using one of the Ubuntu family of Linux distributions such as Lubuntu because each user interface has different ways of doing things. It is always useful to tell us the hardware specification of the machine. With this problem we need to know the WiFi (wireless) adapter that is in the machine and whether a driver for it is installed. Without a driver the wireless adapter will not detect any wireless access points.

At the moment we do not know if you cannot connect to the internet by WiFI because you do not know how to do it or for some other reason. Commands are entered one line at a time and the Enter key is pressed after each line has been entered.

This machine is a laptop. To save battery power the Wireless adapter can be switched off by a keyboard combination. Also if the machine has Windows installed and wireless is switched off in Windows then the wireless adapter will not be switched on by Ubuntu. The command to use to test if the wireless adapter is switched on or off is

```
rfkill list
```

This is what I see when I run that command

> graham@sdb7-Dev:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

As you can see, on my machine the wireless adapter is not switched off in hardware but it is switched off in software. That is because I am using a wired (ethernet) connection and I have disabled WiFi from the network manager icon menu.

Regards.

---

### Post by art12 on 2015-11-12
A fun fact: after i posted the thread I shut down my laptop. Once started the laptop - the wi-fi is functioning. I probably did do something right, but did not let it apply with restarting the system. I will shut this thread down in a few moments. Thank you grahammechanical for your advice. I will try restarting the system again, just in case.

---

