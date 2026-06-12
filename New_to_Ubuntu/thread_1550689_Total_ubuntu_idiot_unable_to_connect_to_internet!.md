---
title: "Total ubuntu idiot unable to connect to internet!"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by LibraDancer79 on 2010-08-11
Hello, I'm sure you must all be sick of seeing posts about newbies unable to connect to the internet, but I'm having problems connecting. I have looked through other threads and tried some things out but I'm still having issues.
 
Please be patient with me because I'm not technically minded when it comes to computers I'm also completely new to ubuntu and not familiar with the majority of the terminology used. :confused: I'm currently connecting to the internet through Windows and am switching between Windows and ubuntu (thinking of transferring to ubuntu permanently if I can get it to work), so if there is any information you want from me, let me know and I'll see what I can work out.
 
If there is another thread I should be looking at or somewhere else I should be posting this please tell me.
 
Thanks for your help and patience.
Trudy

---

### Post by Rubi1200 on 2010-08-11
Hi and welcome to the forums :)

First things first, are you using a wired or a wireless connection?

Next, if you go into Ubuntu then Applications > Accessories > Terminal copy and paste this into the terminal hit Enter and then post the results back here please

```
ifconfig -a
```

Also, what kind of router or wireless card do you have?

Thanks.

---

### Post by Kazade on 2010-08-11
Could you answer these questions then we may be able to help :)

1. Are you connecting to the Internet through a router or a modem connected directly to the PC?
2. If it's a router, are you connected via a cable, or wirelessly?
3. If wirelessly, do any networks appear when you click the network indicator icon in the top right of the desktop?

Edit: oops beaten by Rubi1200 :)

---

### Post by QLee on 2010-08-11
LibraDancer79,

Have a look at this thread, it's one of the "stickies" at the top of the absolute beginner topics forum. The first post has a lot of information that can help new users get their questions answered quickly and usefully.
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by LibraDancer79 on 2010-08-11
First of all thank you for your quick responses - your help is very much appreciated.
 
I followed your instructions and this is what it threw back at me:
 
ubuntu@ubuntu:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:16:d4:cd:2d:2c 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 
&#12288;
&#12288;
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:284 errors:0 dropped:0 overruns:0 frame:0
TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:21664 (21.6 KB) TX bytes:21664 (21.6 KB)
&#12288;
&#12288;
wlan0 Link encap:Ethernet HWaddr 00:19:d2:09:21:65 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
I'm connecting through wireless broadband.  When I clicked in the internet connections (top right) it shows my connection as being available and when I click on it it brings up a little dialogue box with a drop down saying:
 
WPA & WPA2 Personal (no other options available)
 
And asks me for a password - I've tried inputting the password that I use to connect through windows but it doesn't seem to accept it.
 
As for what type of router or wireless card I'm using - I'm not sure where to find this information but if you let me know where to look I will do so.
 
Thank you all again for your help :)

---

### Post by GaryTheCat on 2010-08-11
Just checking but some routers require you to press a button to get your computer to pair with them (I know mine does, it's an orange livebox).

---

### Post by Scunnered on 2010-08-11
**LibraDancer79**

You don't say where you live which would be a help.  I when installing my wireless connection was faced with the password request.  In my case as I am a Cable subscriber via Virgin Media in the UK had to provide the password agreed between Virgin and myself.

You may find that you similarly may have to provide the password that you agreed with your ISP.

Hope this assists

---

### Post by LibraDancer79 on 2010-08-11
Thanks Scunnered - I thought that was what I was being asked for but that one doesn't work.  And I live in England.

Thanks again.

---

### Post by dineshs on 2010-08-11
please see if post #9 here can help
[http://ubuntuforums.org/showthread.php?t=1550144](http://ubuntuforums.org/showthread.php?t=1550144)

---

### Post by anewguy on 2010-08-12
A couple of more questions, since it is wireless AND the driver apparently is working since you can see wireless networks:

(1) Did you set up the router yourself?

(2) Does the router have WPA or WPA2 encryption enabled (it appears so)?  If so, it is asking you to enter the encryption key you have defined in the router.

Dave ;)

---

### Post by JustinR on 2010-08-12
> **LibraDancer79 said:**
> First of all thank you for your quick responses - your help is very much appreciated.
 
I followed your instructions and this is what it threw back at me:
 
ubuntu@ubuntu:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:16:d4:cd:2d:2c 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 
&#12288;
&#12288;
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:284 errors:0 dropped:0 overruns:0 frame:0
TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:21664 (21.6 KB) TX bytes:21664 (21.6 KB)
&#12288;
&#12288;
wlan0 Link encap:Ethernet HWaddr 00:19:d2:09:21:65 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
I'm connecting through wireless broadband.  When I clicked in the internet connections (top right) it shows my connection as being available and when I click on it it brings up a little dialogue box with a drop down saying:
 
WPA & WPA2 Personal (no other options available)
 
And asks me for a password - I've tried inputting the password that I use to connect through windows but it doesn't seem to accept it.
 
As for what type of router or wireless card I'm using - I'm not sure where to find this information but if you let me know where to look I will do so.
 
Thank you all again for your help :)

Hi,

On some wireless cards, like my Broadcom card, needs the wireless router to be set to B/G (or legacy) mode only for WPA to work. 'N' wireless technology doesn't work so well with WPA on a few wireless cards.

---

### Post by LibraDancer79 on 2010-08-12
GarytheCat:  Thanks for the advice, I have tried this but it doesn't seem to work for me but thanks :)

Dineshs:  This appears to be the same problem I'm having - in that when I try to connect it asks for my password (which I input) then it asks me for the Keyring and I have tried to use my password in there too but after I've done that it keeps coming back on a loop asking me for my password again and again and again! ](*,)

anewguy: 1) The router was set up by the Virgin installation guy.  2)  Sorry to ask but where would I find out about the WPA/WPA2 encryption?  As for the encryption key - would that be the password I gave to the installation guy?

JustinR:  Sorry but where would I find out about the wireless router settings?  Just remember - I need baby steps ;)  I'm also not sure what sort of wireless card I have :???:

Thanks
Trudy

---

### Post by QLee on 2010-08-12
Was dup because I pushed stop to edit before it completed and it carried anyway.

---

### Post by QLee on 2010-08-12
[QUOTE=LibraDancer79]- I need baby steps ;)  I'm also not sure what sort of wireless card I have :???:[/QUOTE]

Well, Trudy, the "stickie" I suggested you read the first post from back in post 4 of this thread would have shown you how to obtain that information from your system with the command, lspci | grep Wireless. However, your wireless card seems to be up. You probably haven't had time to read it yet with all this going on.

Something you might try (get the system back to square one with that connection). Right click on the network manager icon and select edit connections, on the wireless tab find the connection that corresponds with the SSID that your router is broadcasting and delete that connection. With it gone ( and thus any mistakes you might have made the first time also gone ) you can try the process again by selecting the connection and carefully entering the passphrase when it prompts you for that.

---

### Post by LibraDancer79 on 2010-08-12
QLee - I did check out your link but one of my problems is knowing what I'm looking for and what information is relevant.  

I seem to be connected somehow - I'm not quite sure how I've managed it but I'm not going to look a gift horse in the mouth!

Thank you again to everyone who has helped me - it has been very much appreciated and no doubt I will be back in the near future with another problem I come up against :)

Many thanks
Trudy

---

### Post by QLee on 2010-08-12
[QUOTE=LibraDancer79]I seem to be connected somehow - I'm not quite sure how I've managed it but I'm not going to look a gift horse in the mouth![/QUOTE]

Easily explained Trudy, it's the magic of Ubuntu. From one Libra to another, good luck!

---

