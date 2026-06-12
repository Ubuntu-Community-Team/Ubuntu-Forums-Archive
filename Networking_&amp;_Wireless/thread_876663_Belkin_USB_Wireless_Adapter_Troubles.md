---
title: "Belkin USB Wireless Adapter Troubles"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by k scott on 2008-08-01
I tried to get help with this in Absolute Beginner Talk without much response.

Ok, so I installed Hardy on my computer and I can't get this wireless adapter to work.  I read up on the topic a bit and this is what Ive done so far.  I copied the inf and sys file from the installation CD to my computer and loaded them into Windows Wireless Drivers.  When I do this it looks as if it works okay, and it says "Hardware Present."  However, when I go to System > Administration > Network, "Wireless Device" does not show up.  I am really new to all of this and I would appreciate some help.

---

### Post by james_vanb on 2008-08-01
I've always used ndiswrapper for this Wireless Adapter.  Process is as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```
add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```
Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

### Post by pennyminstrel on 2008-08-03
Hi there, 

I've been trying to follow the instructions above, but when I open the install cd, instead of the 3 files mentioned, there's a whole list and I'm afraid I've no idea which are the ones I need. Here's the list:

AUTORUN.INF
BCM43XX.CAT
BCMRNDIS.INF
DATA1.CAB
DATA1.HDR
DATA2.CAB
F5D7051.DLL
ICON.ICO
IKERNEL.EX_
LAYOUT.BIN
RNDISMPK.SYS
Setup.exe
Setup.ini
Setup.inx
START.EXE
USB8023K.SYS

I'd be really grateful if someone could tell me which ones to use.

Thanks

Penny

---

### Post by james_vanb on 2008-08-03
Looks like you are using a Belkin F5D7051. The above is for the F5D7050.  The driver your card is using is the Broadcom BCM43XX.  Depending on what Distro you are using, you may be able to get it working by enabling Restricted Drivers in System menu.  Otherwise, Google BCM43XX Ubuntu and you will find threads related to your card.

Good luck.

Penny - See this tutorial:

[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcw43xx](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcw43xx)

---

### Post by pennyminstrel on 2008-08-05
Thanks ever so much for your reply - feel a bit stupid posting about the wrong adapter! But I will try your suggestions.

Penny

---

### Post by james_vanb on 2008-08-05
> **pennyminstrel said:**
> Thanks ever so much for your reply - feel a bit stupid posting about the wrong adapter! But I will try your suggestions.

Penny

No problem.

If you haven't already seen this, this tutorial may get you sorted out:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c9037d4dac23680f0939e488c2291413ce831ef3](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-c9037d4dac23680f0939e488c2291413ce831ef3)

---

### Post by pennyminstrel on 2008-08-05
Hi

I've been trying for days to get my belkin 7051 to work. I know this isn't for the exact same model, but I thought if I substituted the appropiate inf file it might work. It was ok till I put in sudo modprobe ndiswrapper, when I got the answer FATAL: Module ndiswrapper not found.

Is there something I did wrong or do I need to find specific instructions for a 7051?

Penny

---

### Post by james_vanb on 2008-08-05
Haven't had this problem.  However, found what may be a solution:

[http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/](http://hansengel.wordpress.com/2007/07/24/ubuntu-710-wireless-adapter-problems/)

or;

[http://www.linuxquestions.org/questions/debian-26/fatal-module-ndiswrapper-not-found-498947/](http://www.linuxquestions.org/questions/debian-26/fatal-module-ndiswrapper-not-found-498947/)

---

