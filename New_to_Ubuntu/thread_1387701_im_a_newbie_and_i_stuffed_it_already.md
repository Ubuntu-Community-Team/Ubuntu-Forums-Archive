---
title: "im a newbie and i stuffed it already"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by u-bun2 on 2010-01-22
Hello i am still learing all about linux but i think i reall did manage to break it
when ever i try to look for updates i get a message

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out - 
this the first time and when i tried again i got this

failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release](http://archive.canonical.com/ubuntu/dists/jaunty/Release)  Unable to find expected entry  partner/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz](http://dl.google.com/linux/deb/dists/stable/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

and cannot update any software at all i get lots of errors all the time for everything and am starting to think that maybe i should go back to windows am getting sick of errors and just want a working machine again and this first occured when i id an update and i think it was a big one that didnt work properly because some things say i have jaunty and others say i have karmic (not sure on the differences)
anyways internet works ok at first once first error occured i have to use another pc t get new web browser (went from firefox and that stopped working after update)to swiftfox 
have been doing reserch and tried a few things but i think the synaptic package manager is a broken package(whatever that means)
Please help !!!
also tried using pidgin and empathy with yahoo email acc and it just comes back saying network error 

Thanks in advance
p.s if no one can help i will return back to the dark side(Windows)

U-bun2 thanks U

---

### Post by Alex De Duck on 2010-01-22
Hello there, I can't help with much but I can tell you this: Jaunty Jackalope and Karmic Koala are different releases. Releases are alphabetical, so Karmic is the latest. Around the forum you'll find a bunch of helpful topics. I hope you'll stay on the good side, we have better cookies!

---

### Post by fromthehill on 2010-01-22
I think the problem lies with your internet-connection, not with apt

what is the output of 'ifconfig'?

---

### Post by drpjkurian on 2010-01-22
> **u-bun2 said:**
> Hello i am still learing all about linux but i think i reall did manage to break it
when ever i try to look for updates i get a message

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

and cannot update any software at all i get lots of errors all the time for everything and am starting to think that maybe i should go back to windows am getting sick of errors and just want a working machine again and this first occured when i id an update and i think it was a big one that didnt work properly because some things say i have jaunty and others say i have karmic (not sure on the differences)
anyways internet works ok at first once first error occured i have to use another pc t get new web browser (went from firefox and that stopped working after update)to swiftfox 
have been doing reserch and tried a few things but i think the synaptic package manager is a broken package(whatever that means)
Please help !!!
also tried using pidgin and empathy with yahoo email acc and it just comes back saying network error 

Thanks in advance
p.s if no one can help i will return back to the dark side(Windows)

U-bun2 thanks U

Hi
This error usually happen when there is network problem or server problem. You have also mentioned that firefox also has network error. So please check out your network connection.

---

### Post by Grenage on 2010-01-22
```
archive.ubuntu.com:80 (1.0.0.0)
```

IP 1.0.0.0?  Yeah, something is horribly wrong.

---

### Post by u-bun2 on 2010-01-23
> **fromthehill said:**
> I think the problem lies with your internet-connection, not with apt

what is the output of 'ifconfig'?

like i say very new to this stuff not sure how to do that but can tell you that swift fox works fine but fire fox did not alot of issues with this machine pls let me know what i need to do to help you help me :D
Thanks in advance
by the way my internet is adsl broadband running through w/less router using 26 hex wep ket and thats all i can tell you without knowing what to do....
p.s i look forward to your answers and assistance:)

*****EDIT******
just thought i might try and type it into termanal window and got this 
eth0      Link encap:Ethernet  HWaddr 00:16:36:15:59:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:d1:63:87  
          inet addr:192.168.0.152  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fed1:6387/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:724481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:643490 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:678009855 (678.0 MB)  TX bytes:67922391 (67.9 MB)
          Interrupt:17 Base address:0x6000 Memory:b0101000-b0101fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.5 KB)  TX bytes:1500 (1.5 KB)


U-bun2 thanks U

---

### Post by mick222 on 2010-01-23
> 

failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
This looks like you have the cdrom selected in software sourcego to system->administration software sources and  untick use cdrom  and check for the best server.Also open synaptic and click fix broken packages.

---

