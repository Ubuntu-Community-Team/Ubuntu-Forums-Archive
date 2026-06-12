---
title: "usb modem not working"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by st_nazinger on 2009-03-15
ive got a huawei e220 usb modem which seems to be completely ignored by ubuntu 8.04 - its not listed under "places" and if i write "iwconfig" in terminal reply is "no wireless extensions"
can anybody help me??

---

### Post by ivanvajar on 2009-03-15
In Terminal, type

> sudo lsusb

and post me what it returns, please.

---

### Post by st_nazinger on 2009-03-15
Bus 003 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 003 Device 005: ID 0402:5661 ALi Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:1904 Hewlett-Packard DeskJet 3820
Bus 001 Device 001: ID 0000:0000

but i still dont know what to do

---

### Post by ivanvajar on 2009-03-15
Open Synaptic Package Manager and search for ndiswrapper. When you install it, go to System/Administration/Windows wireless drivers and with that program, you can install Windows driver for your usb modem.

---

### Post by ivanvajar on 2009-03-15
> Bus 003 Device 007: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem

This message shows that your modem was detected.

---

### Post by ivanvajar on 2009-03-15
Just to make sure: When you go to 'add new driver', you mark just *.inf file of your Windows driver.

---

### Post by dje on 2009-03-15
i would suggest using [this ppa]("https://launchpad.net/~network-manager/+archive/ppa") to upgrade your network manager to 0.7 as this has built in support for mobile broadband modems, i have done this and it works great for my huawei e160g so i would recommend this. alternatively you can use wvdial, just google for tutorials on setting it up.

hope this helps,
dje

---

### Post by ivanvajar on 2009-03-15
That would do the trick. However, I installed usb wireless modem with ndiswrapper and it works like a dream. I think both are worth trying. Thanks, dje.

---

### Post by dje on 2009-03-15
> **ivanvajar said:**
> That would do the trick. However, I installed usb wireless modem with ndiswrapper and it works like a dream. I think both are worth trying. Thanks, dje.

fair enough ivanajar :)

dje

---

### Post by st_nazinger on 2009-03-15
since my computer is not connected to the internet i cant use the ppa (if i understand it correctly).


synaptic didnt find ndiswrapper so i downloaded version 1.50 manually but i cant install it.
tried to extract it (as the INSTALL file described):

tar zxvf ndiswrapper-1.50.tar.gz

but terminal replied:

tar: ndiswrapper-1.50.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


thx for your effort guys!

---

### Post by dje on 2009-03-15
i would try wvdial then (i think it would be much easier), i followed [this guide]("http://www.troublenow.org/?p=22") and it worked for me (it talks about a phone but it works fine for a modem)

dje

---

### Post by lkraemer on 2009-03-16
st_nazinger,
If you downloaded the file to your Desktop your path is incorrect
causing the error message.

tar: ndiswrapper-1.50.tar.gz: Cannot open: No such file or directory

In a Terminal window: 
```

tar zxvf /home/userloginname/Desktop/ndiswrapper-1.50.tar.gz

```

You can always use:
```

locate ndiswrapper-1.50.tar.gz

```
to show you the correct path, then copy and paste.

pwd will also show you the path you are currently at.

lkraemer

---

### Post by anet on 2009-04-04
I am in the same boat as you were when you posted this topic, st_nazinger. Only even more of a newbie.

Thanks for posting this...I have to get on the forum and internet only while I'm booted into Windows, then I restart and boot into Ubuntu. Like Ubuntu, but pretty much useless unless I can get this Huawei EC325 modem to work in it, lol!

Will try what you've been advised and see if it works, again a total NOOB here!!

By the way, did you ever get your modem to work in Ubuntu? I mean, did this stuff work for you? 

Thanks in advance to anyone who replies.

---

### Post by anet on 2009-04-05
Ok, for anyone who wanders by here to help a Noob:

I did: sudo lsusb
I found: my Huawei modem is noted on the list
I did: open Synaptic Manager, find and install ndiswrapper
I did: go to System/Administration/Windows wireless drivers and find and install the .inf files (there were 2) on the Huawei cd. Installation showed that it worked.

What I don't know to do now:
I'm so used to a shortcut being found on the Windows desktop after installing software, and there isn't one on the Ubuntu desktop for the Huawei .inf files I just installed. I am also used to finding newly installed software in the Windows Start/Program files listing; and I don't know the Ubuntu equivalent.

So I it appears that I HAVE installed my modem software, but have no idea how to access it!!

Can anyone help, please? Thanks in advance!!

---

### Post by anet on 2009-04-05
Hi, Ivanvajar, could you look at my last post in this thread and give me advice? Thanks!!

---

### Post by anet on 2009-04-05
Hi, st_nazinger,

By the way, did you ever get your modem to work in Ubuntu? I mean, did this stuff work for you? 

If so...perhaps you can answer the question I raised about finding how to access my recently intalled windows software for Huawei (see my post above).

Thanks in advance!!

---

### Post by GeorgeVita on 2009-04-05
Hi **anet**,

boot Ubuntu 8.04 without the modem, wait system to stabilize, attach modem to the USB port, wait 15 seconds, open a terminal window, type **lsusb** and then **ls /dev/ttyU***

Finally from a terminal window run: **sudo wvdialconf**

Copy here the results. lsusb will list all USB devices, ls /dev/ttyU* will list any serial com port created to communicate with your modem, and sudo wvdialconf will try to make a configuration file for your modem.

Read the following posts regarding similar modems:
[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)
[http://forum.huawei.com/jive4/thread.jspa?threadID=322982](http://forum.huawei.com/jive4/thread.jspa?threadID=322982)

Also why not trying an **Ubuntu 8.10** version which I think with the **Network Manager 0.7** makes easier the use of 3G modems. If you do not want to install it, try booting a **LiveCD**.

Please supply also info about **your provider** to find Dial No and APN. 

Regards,
George

---

### Post by sarmad54 on 2011-03-05
> **st_nazinger said:**
> ive got a huawei e220 usb modem which seems to be completely ignored by ubuntu 8.04 - its not listed under "places" and if i write "iwconfig" in terminal reply is "no wireless extensions"
can anybody help me??

I use Ubuntu 10.10 and huawei is easily recognizable without any further setup. My problem now is with another manufacturer which is the Qualcomm USB modem. Hope this helps.

---

