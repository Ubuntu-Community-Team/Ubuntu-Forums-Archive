---
title: "USB wireless question"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by Brandon_Audet on 2014-06-04
Hi folks, 
I just installed Ubuntu 14.04 LTS on an older system that I had, so that I could try it out and see if I wanted to switch from Windows 7.  I like the interface although it is a bit foreign to what I am used to.

The issue arises when I plugged my USB wireless into the system (an older Asus desktop).  I can see the Wired Ethernet Connection, but no sign of the wireless connections.  I am having to tether my desktop with Unbuntu to my Laptop with Windows 7 and a wireless card to get internet.

I saw a post that suggested I download Window Driver Installer? from the Ubuntu software Center.  I did that but I guess I don't understand Ubuntu enough to get any farther.  

I run "lsusb" in terminal and saw the wireless listed, but I cant see that it is doing anything.  No wireless networks are listed when I look at the network connections.

Any Help would be greatly appreciated.

---

### Post by Bucky Ball on 2014-06-04
*Thread moved to **Networking & Wireless**.*

You might have more luck here. People are gentle with newbies everywhere here (or at least that is the expectation!). ;)

Welcome. Firstly, with the dongle plugged in, could you open a terminal and post back the output of these two commands (one at a time):

```
iwconfig
ifconfig
```

Also, more detail, please. 

What is the brand of the wireless dongle?
When you say you downloaded the Window Driver Installer, what exactly is that? Did you mean ndiswrapper?
With the dongle plugged in and while online with a cable, could you go to 'Additional Drivers' and see if it offers anything. Might take awhile to think. Lastly, what is the dongle listed as in the lsusb read out? If we can identify the wireless chip from that then we're on our way.

PS: If you don't like Unity, there are plenty of other desktop environments to choose from and distros based around them, even! I'm and Xfce fan myself, which is used by Xubuntu (and others). Xubuntu is a bit more lightweight than Ubuntu also.

---

### Post by Brandon_Audet on 2014-06-04
here is the output for the config commands:

brandon@brandon-System-Product-Name:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

```
brandon@brandon-System-Product-Name:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:5b:d1:b5  
          inet addr:192.168.137.103  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe5b:d1b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:647857 (647.8 KB)  TX bytes:74635 (74.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20867 (20.8 KB)  TX bytes:20867 (20.8 KB)

```
Also, the USB wireless is: 

```
brandon@brandon-System-Product-Name:~$ lsusb
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
```

Yes, it was listed as "Windows Wireless Driver Installation tool"  and ndiswrapper was part of the description.

No additional drivers were located.

---

### Post by mörgæs on 2014-06-04
It's a friendly gesture towards people reading your post to use CODE tags around terminal output. 

Have edited the post above.

---

### Post by Brandon_Audet on 2014-06-04
Sorry, I'll see about the tags in future posts.

---

### Post by Bucky Ball on 2014-06-04
ndiswrapper can seriously screw things up if not required. This card is problematic, though, and that might be the only possibility for now. See here:

[http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

It is solved and only a month old.

PS: For [code] tags, edit the post mörgæs added them to and see how it's done. You can simply copy that syntax (manually add the tags around the code) or 'Go Advanced' while editing a post (or Adv. Reply for a new post), highlight the code and click the hash icon (#) in the editing toolbar. ;)

---

### Post by Brandon_Audet on 2014-06-08
Thanks all for the help, got it working.  

It took a few reboots but I finally found the broadcasts, and was able to connect via wireless.

Thanks again for the hand.

):P

---

