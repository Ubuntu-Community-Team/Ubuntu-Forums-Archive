---
title: "ndiswrapper didn't do anything"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by intense.ego on 2008-04-13
I just installed xubuntu on a laptop for my friend, but it has an IPN 2220 wireless card, which is not supported by default. I followed the instructions on this page ([https://help.ubuntu.com/community/WifiDocs/Device/ipn2220](https://help.ubuntu.com/community/WifiDocs/Device/ipn2220)) and it seemed to work. I downloaded the driver from here: [http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&hl=ipn2220](http://www.laptopvideo2go.com/forum/index.php?showtopic=7172&hl=ipn2220)

The output of 

```
 ndiswrapper -l 
```

was

```
 neti2220 : driver installed
        device (17FE:2220) present

```

Despite this, the option for a wireless connection does not appear on the network manager. It only shows the wired connection I am using right now. What's wrong?

---

### Post by intense.ego on 2008-04-13
anyone?

---

### Post by jack_spratt on 2008-04-13
I got a very similar problem with my belkin pcmcia f5d7010 card; ndiswrapper lists it as present and associates the correct driver, but nothing shows up in network manager. Seems there's a magic gap in Ubuntu between the ndiswrapper gui and the network manager gui. If the bridge between them isn't automatically created then there's now way for a mortal to do it :cry:

try 'lspci'/'lsusb' and 'lshw -C network' for more info on what your device is doing, and if you haven't already, check out [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) in case you can find something relevant in there. Good Luck.

FYI PCLinuxOS setup my card in 3 mins, and you may find it easier to set up your card also. So if all else fails you can try the livecd and see if you can get the wireless functioning.

---

### Post by intense.ego on 2008-04-13
Thanks, mate, I'll be sure to check that out when I have the time.

---

### Post by intense.ego on 2008-04-14
anyone else?

---

### Post by kevdog on 2008-04-14
OK, is the ndiswrapper inserted into the kernel?  You can check with lsmod | grep ndiswrapper

What is the output of lshw -C network.

If you check out the following guide at the end, since you have ndiswrapper installed, look for the troubleshooting section to see if it addresses your problem:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

