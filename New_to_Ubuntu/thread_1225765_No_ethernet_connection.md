---
title: "No ethernet connection"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by sunwatt on 2009-07-28
Just got a Dell Mini 9 from the refurbish outlet. Its the basic machine, 500mb ram 8gb SSD A04 with Windows XP on it.

It arrived today, I got XP going, got online and made sure all the usb ports worked, mouse monitor keyboard & hooked up my external Dell cdrom and played music on WMP. I shut it down several times and restarted and each time it connected to the internet. So I think I have a good working piece of hardware.

I'm connected to my ethernet cable to the Visionnet adsl modem.

So I installed Mint 7 Gloria kernel 2.6.28.11 on top of XP, gave it the whole 8gb. 

Now it wont connect to the internet. I looked at the computer icon, Edit connections Auto eth0 seems to be setup right when I checked.

Right now I'm on my Dell Mini 10v Ubuntu 9.04 is installed. It came with 8.04 on it. It connected right out of the box, and after the 9.04 upgrade it connected right away.

Thanks for any help.

Jim

---

### Post by RomeReactor on 2009-07-28
Hi. On the Mini 9, open a terminal and run:
```
lspci -nn | grep Ethernet
```
and
```
iwconfig
```
and post back the output. You can also try posting your problem on the [Mint forums]("http://forums.linuxmint.com/") and the [Dell Mini forums]("http://www.mydellmini.com/forum/other-distributions/").

---

### Post by sunwatt on 2009-07-29
OK, did that, connected cable, no connection.

Rebooted still no connect.

Hope the screenshot helps.

thanks

Jim

---

### Post by sunwatt on 2009-07-29
OK, made it smaller, lets try the screenshot again

---

### Post by RomeReactor on 2009-07-29
I thought you were trying to get the wireless card going. In any case, the card should work correctly with your current kernel. Have you updated the system? Do you have other kernels installed? If so, try booting into a newer kernel and see if the problem persists.

---

### Post by sunwatt on 2009-07-29
Im in town connected to some wireless connection. So ast least it connects this way.

At home Im off the npower gridd, running on solar/bastteries, so I wud rather not use wireless at home, its another 10 watts comning out of my batteres.

At home  [I]need to vconnect to ethernet cable, direct from the dsl modem

Im relieved that wireless connects!!

(Ill be home laste today

thanks

jim
[/I]

---

### Post by superprash2003 on 2009-07-29
also post output of
1)lshw -C network
2)sudo iwlist scanning

---

### Post by sunwatt on 2009-07-29
I was going to try that last suggestion to use that code in terminal, as soon as I got home.

So I started it up, and just for the hell of it, I pluged in the ethernet cable.

BINGO, I'm connected.

What the hell?

Linux Mint fixed itself?

All I did was take the Mini 9 to town today and connected at 3 hot spots. Surfed the web, posted a reply here.

And now it works on the wired ethernet cable?

WHY?

hahahaah

Im happy, but this is strange.

So, if anyone else has this issue, tell them to take the computer to a hot spot and connect. It may fix itself
as soon as they try the wired connection.

Jim

---

