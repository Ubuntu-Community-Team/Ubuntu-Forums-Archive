---
title: "No Wireless conection"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by xodeus on 2008-04-23
Hi.
I've compiled and isntalled the ralink rt2860sta module, and wicd sees my networks but can't connect to any of them. I've tried to turn off the security without help. 
What output do you need, to help me with that one?

---

### Post by dstew on 2008-04-23
Please post the output of ```
iwconfig
```

---

### Post by xodeus on 2008-04-23
```
mariusz@mariusz-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device ra0 has been compiled with an ancient version
of Wireless Extension, while this program support version 11 and later.
Some things may be broken...

ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.422 GHz  Access Point: Not-Associated   
          Link Quality:0  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

mariusz@mariusz-laptop:~$ 

```

---

### Post by mrbuntuman on 2008-04-23
well from the output of ur iwconfig ur AP not getting associate with ur lappy

1st off set ur ssid 
iwconfig ra0 ssid <name>
iwconfig ra0 mode managed
iwconfig ra0 key 11:11:11:11:etc etc
ifconfig ra0 up

ping 192.168.0.1
if u get a reply 
ping [www.somewebsite.com](www.somewebsite.com)
if u get a rply ur good to roll!!!

Cheers

---

### Post by xodeus on 2008-04-23
The thing is that when I get to the part where I've to put in the key I get an error and can't get further from there.
```
mariusz@mariusz-laptop:~$ iwconfig ra0 key s:korsgaard
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ra0 ; Operation not permitted.

```
 When using wicd I see all the networks but can't connect to any of them. See the attatchment.

---

### Post by mrbuntuman on 2008-04-23
long shot but try that

[http://www.ocf.berkeley.edu/~brandon/wifi1.html](http://www.ocf.berkeley.edu/~brandon/wifi1.html)

---

### Post by dstew on 2008-04-23
Try```
sudo iwconfig ra0 key s:korsgaard
```

---

### Post by xodeus on 2008-04-28
tried that too, but I does not work either.

I've in the meantime got a mail from the developer of the module Jett Chen from ralink. Hi is writing this:
> Dear Sir,

 

1.       Please turn on debug message by iwpriv, check Makefile and add &#8220;-DDBG&#8221; into CFLAGS.

After driver bring up, please input below command.

iwpriv ra0 set Debug=3
So I did ```
sudo make -CFLAGS=-DDBG
``` in the ralink source, it compiled without any warnings nor messages. So started the module then ```
iwpriv ra0 set Debug=3
``` then I got this message:
> Interface doesn't accept private ioctl...
set (8BE2): Network is down
i mailed it to him, but he hasn't answered yet, so what does this mean?

---

### Post by flyguy97 on 2008-11-01
I posted a walkthrough of what worked for me, give it a go and let me know if it works for you.

[http://ubuntuforums.org/showthread.php?t=966185]("http://ubuntuforums.org/showthread.php?t=966185")

-flyguy97

---

