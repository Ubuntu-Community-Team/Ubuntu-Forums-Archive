---
title: "Wireless networks help please."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-10
So seeing as how I just have downloaed and started using Ubuntu in the last few days PLEASE be patient with me...

How do you scan for open wireless networks with Ubuntu? (hardy heron)  I experimented with this some last night and here is what happened with it..

I disconnected my ethernet cable reset the cable modem and then plugged into my router... I then restarted the machine....

after this the network connections icon in the top right hand corner had an alert that said I needed to enable this... when I would click on enable networking it never seemed to enable this..  Is this because my WiFi isn't working yet?

I did print out the terminal commands that were listed in another thread in case I need them.....

I beleive in Windows my WiFi card was listed as an Atheros 5007... but when I went to terminal > lspci  It was listed as an AR242x... Do I need to run those terminal commands to activate my card?

The drivers for them do show up when I go to System, Administration, Hardware drivers..

It then shows this.
Device Driver
Atheros Hardware Access Layer (the enabled box is checked) then it is checked as in use

then
Support for Atheros 802.11 wireless LAN cards (then enabled box is checked) and this is also checked as in use...

So if these 2 drivers are installed and in use it should be working correct?  Or is there something I am just not getting in this?  I am basically a Linux Virgin(but love it so far!!) so I guess I just don't understand why it wouldn't be working I guess....

---

### Post by cptrohn on 2009-01-10
Ok... when I go to Network settings it does not list a wireless connection,  so this means that my WiFi is not being recognized correct?

---

### Post by cptrohn on 2009-01-10
> **cptrohn said:**
> Ok... when I go to Network settings it does not list a wireless connection,  so this means that my WiFi is not being recognized correct?

LOL hello.... anybody out there?

---

### Post by Captain_tux on 2009-01-10
Silly question, but... Is your wifi enabled? Near the top right of your monitor near the time clock, do you see a little icon with two computers or a set of bars?

---

### Post by cptrohn on 2009-01-10
> **Captain_tux said:**
> Silly question, but... Is your wifi enabled? Near the top right of your monitor near the time clock, do you see a little icon with two computers or a set of bars?

I tried this when I disconnected my computer from the ethernet and it would do nothing.... Also in network settings there is no place to enable a wireless card either..?

---

### Post by Abu_Dayya on 2009-01-10
Are you using a laptop? is the switch for your wifi turned on?

---

### Post by Captain_tux on 2009-01-10
Right click on the icon and ensure that **Enable Networking** and **Enable Wireless** are both ticked.

---

### Post by cptrohn on 2009-01-10
> **Abu_Dayya said:**
> Are you using a laptop? is the switch for your wifi turned on?
The switch won't work at all.....

---

### Post by Abu_Dayya on 2009-01-10
> **cptrohn said:**
> The switch won't work at all.....

What do you mean?

---

### Post by cptrohn on 2009-01-10
> **Abu_Dayya said:**
> What do you mean?
Well on both of my Compaq laptops there is a switch on them with the WiFi icon.... when it is turned on by pressing the swith it lights up blue, when it is turned off it is an orange color.

---

### Post by Captain_tux on 2009-01-10
Post the output of **lspci** run as sudo... be sure to wrap code tags around it (the # sign just above this box as you type text).

---

### Post by cptrohn on 2009-01-10
> **Captain_tux said:**
> Right click on the icon and ensure that **Enable Networking** and **Enable Wireless** are both ticked.

Ok... there is not even an option for enabling wireless listed there... just for the wired network.

---

### Post by Abu_Dayya on 2009-01-10
> **cptrohn said:**
> Well on both of my Compaq laptops there is a switch on them with the WiFi icon.... when it is turned on by pressing the swith it lights up blue, when it is turned off it is an orange color.

So, is it blue or orange?

---

### Post by cptrohn on 2009-01-10
> **Captain_tux said:**
> Post the output of **lspci** run as sudo... be sure to wrap code tags around it (the # sign just above this box as you type text).

Ok, how do I do that?


I did it once earlier but forgot how I did it...

---

### Post by cptrohn on 2009-01-10
> **Abu_Dayya said:**
> So, is it blue or orange?
Orange.... has been since I installed Ubuntu and the key won't work at all.

the metwork connections also doesn't list any wireless cards available and the connection manager doesn't list any wireless available to turn on either.

---

### Post by Abu_Dayya on 2009-01-10
So, it looks like your wifi is turned off. Thats why you don't see the "Enable Wireless" button when you right click on the network manager icon. I'm sorry, I don't know what to do to get it turned on. Maybe some of the guys here can help you with it. Bit the good thing is now we identified your problem

---

### Post by Abu_Dayya on 2009-01-10
Try to google if there is a way in ubuntu that enables you to get the wifi switch on

---

### Post by Captain_tux on 2009-01-10
> **cptrohn said:**
> Ok, how do I do that?

I did it once earlier but forgot how I did it...

Open a terminal and type **sudo lspci** (you'll be prompted for the admin password).

---

### Post by cptrohn on 2009-01-10
> **Captain_tux said:**
> Open a terminal and type **sudo lspci** (you'll be prompted for the admin password).

Well here are 2 lines from that, I don't know if they are what is right though..

00:1fe.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)


and then this about the card I guess.

01:00.0 Ethernet controller: Atheros Communications Inc. AR 242x 802.11abg Wireless Express adapter (rev 01)

---

### Post by Guille Damke on 2009-01-10
Hi,

At least in intrepid, the Atheros card works installing backports modules. Probably it works also in Hardy.

What we do is:

1. Uninstall/Disable all the Atheros drivers in System>Administration>Hardware_drivers.

2. Install backports modules, in Intrepid (8.10) they are named: linux-backports-modules-intrepid
What I did in a friend's laptop, was to install linux-backports-modules-intrepid-generic, since his kernel was 2.6.27-9-generic and he has Ubuntu 8.10. You can check your kernel doing
```
uname -r
```
To install backports in your machine, you can look for backports in Synaptics.

3. Reboot your machine, when it is up again, the Network Manager should be working. This method works in Intrepid very well.

Good luck.

---

### Post by cptrohn on 2009-01-10
Ok.. I think I might have found a fix but need some basic help from a more experinced user to answer a couple of questions.


This is the article I found:

[http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html](http://ubuntu-snippets.blogspot.com/2008/12/making-atheros-ar242x-wireless-chipset.html)

Just a couple of quick questions..

The first thing it says to do is to blacklist the ath_pci and the ath_hal   How do you go about doing this?  do you just type those into the terminal?


then it says to "Now add the following line to the file /etc/modprobe.d/ndiswrapper   at the end.

alias wlan ndiswrapper


How do you add the line to this?

Sorry, if it sounds easy to the more experienced folks here... but I just am not sure and would much rather ask than mess something up..

---

### Post by cptrohn on 2009-01-10
Ok... I have tried this one and when I get to this part```
sudo ndiswrapper -i net5211.inf
``` it says in the terminal ```
no ndiswrappers found
```  Now from the install page it says that this will install the 32 bit driver for ndiswrapper.. is this right?  Or have I done something wrong?

---

### Post by CBHedricks on 2009-01-10
Did you ever get the "switch" to work? That wireless switch may be the issue with your notebook computer and the problems that you are having making connections with your wireless hardware.  HP/Compaq are good with Linux (HP/UX) but unfortunately they will ONLY offer support for your notebook computer in it's original "as shipped" condition.  This would mean that you are only eligble for HARDWARE support at this point since you have elected to remove the installed version of Windows that was originally installed.

The hardware is recognized and the drivers have loaded, but the hardware is not activating because the SWITCH hardware is missing out on it's drivers...

Workaround would be to pickup a wireless USB adapter and then try treading around HP/compaq forums or send a email to their HQ asking about how that button is supposed to work with Linux over Windows.  

Unless you get the light on that card to turn BLUE your wireless will not work at all.  I will see if I can dig up some answers for you (I still have contacts within HP, unless they got RIFF'ed).

Good luck.

CB

---

