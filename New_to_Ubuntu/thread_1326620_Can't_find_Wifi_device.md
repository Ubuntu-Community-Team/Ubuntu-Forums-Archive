---
title: "Can't find Wifi device"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by jimtyler on 2009-11-14
Hi, I'm running Ubuntu 9.10 off a CD, and trying to get it to recognize my Wifi card. I read the help section on the subject, and it tells me to click on the "Network Manager Icon" in the "System Notification Area". I searched all the menus, and everywhere else I could think of for the System Notification area, but couldn't find it. Could somebody please tell me where this is located? Thank you much.

jim

---

### Post by coldReactive on 2009-11-14
Give us the output of lspci from terminal.

---

### Post by steveneddy on 2009-11-14
Here - look at pic

---

### Post by donroher on 2009-11-14
> **jimtyler said:**
> Hi, I'm running Ubuntu 9.10 off a CD, and trying to get it to recognize my Wifi card. I read the help section on the subject, and it tells me to click on the "Network Manager Icon" in the "System Notification Area". I searched all the menus, and everywhere else I could think of for the System Notification area, but couldn't find it. Could somebody please tell me where this is located? Thank you much.
 
jim
 
 
I am having the same problem with a seria 881 usb date card...

---

### Post by sandyd on 2009-11-14
> **jimtyler said:**
> Hi, I'm running Ubuntu 9.10 off a CD, and trying to get it to recognize my Wifi card. I read the help section on the subject, and it tells me to click on the "Network Manager Icon" in the "System Notification Area". I searched all the menus, and everywhere else I could think of for the System Notification area, but couldn't find it. Could somebody please tell me where this is located? Thank you much.

jim

its located on the top right corner of your screen(on the panel)

---

### Post by cariboo on 2009-11-14
As much as there have been a lot of threads about doing things with a gui instead of the terminal, it is one of the best troubleshooting tools available. To both posters, go to Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

You will be asked for your password, enter the password you created when you installed Ubuntu, it will not echo back to you. 

The above command will print out a listing of all your network devices, and whether they have been detected and the driver loaded. Paste the output in your next post.

To copy and paste from a terminal, just highlight the text, next click where you want to paste the tesxt and press the wheel on your wheel mouse, if you don't have a wheel mouse press both buttons at once.

---

### Post by jimtyler on 2009-11-14
Cariboo907 says to type in my password that I created when I installed Ubuntu. I haven't installed it yet. I'm just booting off the CD. Do I need to install it for it to recognize my Wifi device? If I install it, how much disk space will it take? I've already got a 512MB partition for Puppy, which I'm not using anymore. Will it automatically use that partition? It will probably need to be made bigger, I would think. I don't want my Windows partition disturbed. Thanks ---- jim

---

### Post by jimtyler on 2009-11-14
Does anybody know if I can use the Internet when booted on a CD?

---

### Post by JREAM on 2009-11-14
> **jimtyler said:**
> Does anybody know if I can use the Internet when booted on a CD?

Yes you should be able to.

---

### Post by jimtyler on 2009-11-14
Now when I try to boot Ubuntu off of the CD I get several pages of errors, including many saying "Can't open page", or words to that effect. Does anybody have any ideas on why it will no longer boot on the CD? Thanks.

---

### Post by jimtyler on 2009-11-16
OK. I burned another CD, which seems to working OK so far. But, I'm still having problems getting Ubuntu to recognize my wifi card. I went to termilal and typed in: sudo lshw -c network, and got this result:

ubuntu@ubuntu:~$ sudo lshw -c network 
  *-network               
       description: Wireless interface 
       product: RT2760 Wireless 802.11n 1T/2R Cardbus 
       vendor: RaLink 
       physical id: 1 
       bus info: pci@0000:02:00.0 
       logical name: ra0 
       version: 00 
       serial: 00:1c:df:8e:1e:9e 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless 
       resources: irq:11 memory:24000000-2400ffff

Can anybody tell me what to do next? Thank you much.

---

