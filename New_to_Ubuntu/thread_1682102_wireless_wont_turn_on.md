---
title: "wireless wont turn on"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by natman on 2011-02-05
Hi,
I have a HP pavillion dv 2278ea, running kubuntu. Yesterday morning i noticed i was getting less wireless signal strength than usual. I ignored this and when i turned my laptop on the next time the light the shows the wireless card status is always orange ( indicating its turned off ) but the switch is in the on position. I went into connection settings it just keeps telling me wireless is switched off no matter what i do. Can anyone help me out?

---

### Post by grahammechanical on 2011-02-05
Are you dual booting? If so, did you turn wireless off in the other OS and then shutdown? There is a comment in the wireless trouble shooting guide that explains that some laptops have chip that allows a certain OS to turn off the wireless adapter. If the wireless adapter is turned off in that OS it will not be turned on even by the keyboard unless it is first turned back on in the OS being referred to.

Regards.

---

### Post by natman on 2011-02-05
No its single boot, all linux. It was working fine since it was bought ( 3 years ago ) another unusual thing is that when i plug a usb wireless adaptor into it does nothing either - previoulsy it would always give me the choice to use either.

---

### Post by natman on 2011-02-05
Thanks for the replies, actuall sorted outmyself - with a lucky google search. Still dont know what caused the issue in the first place.
> I have recently installed Fedora 13 on my notebook and had some problems with the network connection. After researching the problem I found that the problem is more widespread and affects most distros. This is a solution to a soft blocked device.

I decided to restart the NetworkManager services, as root and got a strange error message I had not seen before:

operation not possible due to RF-KILL

First, if you do not already have it installed, install the rfkill command, as shown below

yum install rfkill

Now you need to issue the rfkill command with the argument unblock all, as shown below

rfkill unblock all

In order to see if the problem is really solved, issue the argument list to rfkill, as shown below

 

user@fedora-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by techunit on 2011-02-05
I was having a similar dilema on my studio 1737. Flick the switch to the off possition and power down. Then flick the switch to the on setting and power up. This should work. Else try reinstalling the drivers.

---

