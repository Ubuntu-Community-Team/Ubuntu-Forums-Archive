---
title: "Apparent internet problem"
date: 2016-04-07
forum: Networking &amp; Wireless
---

### Post by AlyssaVS on 2016-04-07
I now have two threads going at once. I don't know if the problems are connected. 

I am connecting my desktop through an ethernet connection. It appears to recognize the connection, reports a connection speed but when I try to download updates it fails and says to check my internet connection. I had the same problem using a usb wireless adapter. I am currently booting in recovery mode due to a graphics problem. The Windows side has no problems with any of this so it isn't a hardware issue.

I don't know how to troubleshoot this internet (or update) problem in Linux.  Any help would be appreciated.

---

### Post by QIII on 2016-04-07
Is this the second thread, or a new third thread?

---

### Post by RobGoss on 2016-04-08
Hello and welcome, I'm assuming you can connect to the internet because you're posting here so that leads me to believe the following 

Go to **Software sources** and choose another download service the one you're using may not be the best choice and might be generating this message.

---

### Post by AlyssaVS on 2016-04-10
> **RobGoss said:**
> Hello and welcome, I'm assuming you can connect to the internet because you're posting here so that leads me to believe the following 

Go to **Software sources** and choose another download service the one you're using may not be the best choice and might be generating this message.


I am posting here from my laptop. The problem is with my desktop.

> **QIII said:**
> Is this the second thread, or a new third thread?

This is the second thread. I attempted to address two problems that I am having with my desktop after recently purchasing a new monitor. I was told I had to post a new thread for the second issue (the apparent internet connection problem).

> **AlyssaVS said:**
> This is the second thread. I attempted to address two problems that I am having with my desktop after recently purchasing a new monitor. I was told I had to post a new thread for the second issue (the apparent internet connection problem).

Apparently my original post got moved to "hardware" by a moderator after I mentioned I couldn't complete updates. This is a little frustrating.....

I realize we need to post the right problem in the right forum but now it feels like I won't get anything figured out.

---

### Post by jebradley on 2016-04-11
I have to report that I have also started having internet problems with my desktop. I am running Wily on the desktop as well as in a VBox VM, and Window 8 in a VBox VM. Both VM's are setup with bridged network adapters. The problem is present in both the desktop and the Wily VM, but not in the Windows VM (which is where I'm composing this message). I am using fixed DNS addresses, 8.8.8.8 and 208.67.222.222 in all. 

I was running my desktop with a fixed IP and noticed that the broadcast address had changed from 192.168.0.255 to 192.168.1.255. After changing to automatic configuration via DHCP, ifconfig reported the correct broadcast address, but I still cannot not connect through a browser with a URL. I can ping an IP address, but can not ping a text URL. 

Any clues as to what I can do as well?

---

### Post by jebradley on 2016-04-12
I figured out the problem. Conflicting DHCP servers. I am in the middle of transitioning between DSL and Cable internet and currently have wireless routers on both, one at 192.168.0.254 and the other at 192.168.0.253. I was somehow getting the gateway from one and the DNS from the other. I've turned off the DHCP from one and everything works fine now.

---

### Post by RobGoss on 2016-04-13
Glad you found out what was causing the problem, Would you mind marking this post as Solved, you can use the **Thread Tool** at the top of this post. Thank you

---

### Post by bab1 on 2016-04-13
> **AlyssaVS said:**
> I now have two threads going at once. I don't know if the problems are connected. 

I am connecting my desktop through an ethernet connection. It appears to recognize the connection, reports a connection speed but when I try to download updates it fails and says to check my internet connection. I had the same problem using a usb wireless adapter. I am currently booting in recovery mode due to a graphics problem. The Windows side has no problems with any of this so it isn't a hardware issue.

I don't know how to troubleshoot this internet (or update) problem in Linux.  Any help would be appreciated.
You seem to have been trampled on.  That sucks.  It is real hard to fix IP connectivity problems when you are in recovery mode.  The environment changes so you can't come to any logical diagnostic conclusions.  I have no experience with graphics problems other than to say that if you have a digital monitor (one that connects by either DVI or HDMI) you most certainly have a video card conflict.  This means that the hardware section is that correct place to that issue to be solved.  If on the other hand, if you have a VGA type older monitor, you will always have problems.  The modern "digital" monitors announce there specs and the Xorg system auto-magically configures the graphics.  None of the specs are broadcast for a analog monitor.

IP connectivity can require real time monitoring to see the problem.  Unfortunately you will need to address the graphics problem first.

---

### Post by bab1 on 2016-04-13
> **RobGoss said:**
> Glad you found out what was causing the problem, Would you mind marking this post as Solved, you can use the **Thread Tool** at the top of this post. Thank you
Unfortunately @jebradley is a thread hijacker, not the OP.  Even if he could mark the thread solved he shouldn't.  It is only the OP's to mark solved.

---

### Post by RobGoss on 2016-04-14
Unfortunately I missed that one thought it was the OP that's found a fix...

---

