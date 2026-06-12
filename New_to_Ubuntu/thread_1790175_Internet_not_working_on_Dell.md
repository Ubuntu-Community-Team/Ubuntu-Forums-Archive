---
title: "Internet not working on Dell"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by twinkz826 on 2011-06-24
My friend told me about Ubuntu and told me that I should try it, so far I like it but I can't get the internet to work.

I installed the latest version of Ubuntu on a _Dell Vostro 1500_ with a CD. 
I believe I have a _Dell Wireless 1395 WLAN Mini-Card_ (that's what it says anyway (I think))

If anyone could please help me figure this out it would be extremely helpful. If you need anymore information then let me know.

Jaime

---

### Post by kuifje09 on 2011-06-24
With wireless, is always a little more complicated. My advice, if you can try with a wire, I certainly would try that. Then setup the wireless. But with wireless itself I am not very handy. But if you want to try, try it first the easy way. ( thats all I can say )

---

### Post by twinkz826 on 2011-06-24
I have to use a wireless connection. My neighbor lets me use his.

---

### Post by bkratz on 2011-06-24
> **twinkz826 said:**
> I have to use a wireless connection. My neighbor lets me use his.



 The Dell 1395 is a Broadcom 4312 device more often known as
 Broadcom Corporation BCM4312 802.11b/g LP-PHY .

from this page readme file
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)


4312 2.4 Ghz	    0x14e4	0x4315  	Dell 1395


This is the ultimate thread on that device

[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

Unfortunately you probably will need wired access to activate it.

---

### Post by Rex Bouwense on 2011-06-24
You will need a wired connection to activate.  I have a Dell Inspiron with a Dell 1390 card which is also a broadcom device.  The only way I could get it working was download the driver using a wired connection.  Works fine now.

---

### Post by a.chaos on 2011-06-24
Wooh, 


Me too. Im using a HP pavillion. My wireless is not working. Just installed 11.04 the other day and have yet to connect to the internet.


I suppose its time to go looking for that darn ethernet cable...

;)

---

### Post by a.chaos on 2011-06-24
So I tried installing the missing driver (the STA wireless driver) and restarted the computer to update but it didnt stick. 

still no wireless...


?

---

### Post by trizrK on 2011-06-24
connect via ethernet (if possible) and install the firmware for the drivers. If you cant use the liveCD the firmware is embedded in there. I believe their is a page that tells you how to do this, with b43 fwcutter or bcm43xx.
here it is:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
sorry that is for bcm43xx specifically

---

### Post by a.chaos on 2011-06-24
> **trizrK said:**
> connect via ethernet (if possible) and install the firmware for the drivers. If you cant use the liveCD the firmware is embedded in there. I believe their is a page that tells you how to do this, with b43 fwcutter or bcm43xx.
here it is:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
sorry that is for bcm43xx specifically

like I previously stated...i tried installing the driver using the ethernet. it didn't install for some reason. no wireless access still. 


went to link you provided. tried installing the driver using the terminal but got errors.

attached is a screen shot...


?

---

### Post by trizrK on 2011-06-24
try these commands:
sudo apt-get install b43-fwcutter
sudo apt-get install b43-fwcutter firmware-b43-installer

then go to: [B]System > Administration > Hardware/Additional Drivers 
[/B]and see if the drivers are there
sometimes it just works automatically with the first two commands.
see if that works

---

### Post by a.chaos on 2011-06-24
alrighty. I'll try that. 

Unfortunately I went to Synaptic -> Mark for Reinstallation .... and now my computer is upset with me. Everything completely froze...

---

### Post by a.chaos on 2011-06-24
mmhm.

Didn't work. 

:/

---

### Post by twinkz826 on 2011-06-24
I have another hard driver for the same computer but I have windows xp and the internet works just fine on there

---

### Post by trizrK on 2011-06-25
> **a.chaos said:**
> mmhm.

Didn't work. 

:/
Hmm..
try these commands:
sudo apt-get update 
sudo apt-get install bcmwl-kernel-source

then see if you have a connection.

---

### Post by trizrK on 2011-06-25
Also if that didn't work do you mind typing in **lspci** in a terminal window and posting the output here? thanks

---

### Post by jtarin on 2011-06-25
Issue the command "lsmod" (without quotes) in a terminal and post results

---

### Post by kidknapp on 2011-06-25
> **twinkz826 said:**
> I have another hard driver for the same computer but I have windows xp and the internet works just fine on there

You can install ndisgtk through synaptic package manager in System>Administration>. or in the terminal....

```
sudo apt-get install ndisgtk
```

It should show up in System>Administration>Windows Wireless Drivers.

This allows you to use your windows wireless drivers by 'wrapping' them in a windows API that linux can use. You will need a copy of your wireless drivers files - If you know the number you can usually find them in c:\DELL on your windows partition if they came from dell- or you can download a new one and extract it so you know which one it is. This is somewhat undesirable but it has saved me a few times where the linux and broadcom drivers just didn't find my card....

---

### Post by twinkz826 on 2011-06-26
Thank you everyone that tried to help me. I downloaded 10.04  and installed that version instead. Than I went to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) (thanks trizrK) and just fallowed the steps for b43 no internet access and it worked just fine. After i read the steps and downloaded 10.04 and the two other files i had the new system with internet in about 15-20 min.

---

### Post by jtarin on 2011-06-26
Might mark this thread as solved as it will help someone else.

---

