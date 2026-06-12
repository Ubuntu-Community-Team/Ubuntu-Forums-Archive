---
title: "Can not find wireless driver for 8086:4239"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by homebound on 2010-04-19
I am new to Linux. I purchased an HP i7 laptop and need to install linux on it.

I have tried many different things to get the wireless to come up but to no avail. According to the ubuntu forums ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver%20using%20ndisgtk%20%28ndiswrapper%20graphical%20interface%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Windows%20driver%20using%20ndisgtk%20%28ndiswrapper%20graphical%20interface%29)), I need to find the windows driver for this HP laptop which uses an Intel wireless chipset (Intel 8060:4239). 

Here is the lspci output: 
02:00.0 Network controller: Intel Corporation Device 4239 (rev 35)
and 
02:00.0 0280: 8086:4239 (rev 35)

and the output for ifconfig is:
ifconfig -a
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:24:47:37  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fe24:4737/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7832593 (7.8 MB)  TX bytes:982500 (982.5 KB)
          Interrupt:35 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:14:30:de:34  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-14-30-DE-34-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


It appears that the only location that I would be able to download this driver is at [http://wiki.debian.org/iwlagn](http://wiki.debian.org/iwlagn). The instructions seem quite complex. Can someone confirm that I am going down the right path and that I have to follow the above instructions?

Thank you
Marcus

---

### Post by anewguy on 2010-04-19
Using the USB manufacturer and product code you gave, I was able to find quite a lot of information on the net.  One such reference is:

[http://intellinuxwireless.org/]("http://intellinuxwireless.org/")

Also, since this is a USB connected device (even if it is internal wireless on a laptop), please post the output of the following back here as it may a little more also:

lsusb

Please note that I am not trying to say "look elsewhere", and as such I will do everything I can to help you with this.  Given the correct device ID (it appears to be an Intel agn adapter), we can hopefully get you going.

Please post back the output of the lsusb and we'll go from there.

Dave ;)

---

### Post by anewguy on 2010-04-19
Also, I noticed you are new, so you have no way of knowing, but there are a couple of minor things to know about using the forum:

(1) Don't create duplicate threads, such as this thread and your first thread [http://ubuntuforums.org/showthread.php?t=1457726](http://ubuntuforums.org/showthread.php?t=1457726), since it just results in confustion.

(2) To put your thread back "at the top" of the thread list, we normally just add a post to the thread - this automatically  puts it back up in the top.  The normal procedure is to add this post with the word "bump" in the text portion so people know you are "bumping" the thread back to the top.

(3) Normally you should not bump until about 24 hours after your latest post.  This is all volunteer, and sometimes we just have to wait a while for help.

I've been exactly where you are in terms of being new, and someone had to inform me of the procedures as well.  And don't worry - some of use have been here quite a while but are nowhere near the path of being a guru.  We just have gotten help, so we like to try to "play it forward".  That's the whole idea of this support forum.

Dave ;)

---

### Post by lisati on 2010-04-19
> **anewguy said:**
> Also, I noticed you are new, so you have no way of knowing, but there are a couple of minor things to know about using the forum:

(1) Don't create duplicate threads, such as this thread and your first thread [http://ubuntuforums.org/showthread.php?t=1457726](http://ubuntuforums.org/showthread.php?t=1457726), since it just results in confustion.

(2) To put your thread back "at the top" of the thread list, we normally just add a post to the thread - this automatically  puts it back up in the top.  The normal procedure is to add this post with the word "bump" in the text portion so people know you are "bumping" the thread back to the top.

(3) Normally you should not bump until about 24 hours after your latest post.  This is all volunteer, and sometimes we just have to wait a while for help.

I've been exactly where you are in terms of being new, and someone had to inform me of the procedures as well.  And don't worry - some of use have been here quite a while but are nowhere near the path of being a guru.  We just have gotten help, so we like to try to "play it forward".  That's the whole idea of this support forum.

Dave ;)
The other thread has been closed, feel free to continue discussions in this thread.

---

### Post by davidmohammed on 2010-04-19
I presume its a "WiFi Link 6000 Series" - the driver was released sometime around the Karmic kernel - given that you say you cant connect I presume it missed that kernel.

You might want to try enabling "backports" in your software sources and do an update to see if that helps.

Alternatively, suggest, download the latest lucid live CD and give that a try.  Its definitely in the lucid .32 kernel.

---

