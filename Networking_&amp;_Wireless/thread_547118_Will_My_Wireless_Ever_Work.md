---
title: "Will My Wireless Ever Work?"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by Johnny_Too_Bad on 2007-09-09
I have tried so many solutions from multiple HOWTOs and Guides and whatnot, but no matter what I do, my wireless simply does not work.  The closest I've come to getting anything to work is by enabling roaming and selecting my home network, which it then somehow connects to, but still no internet, and it continually asks for the network key.  I'm so frustrated I could spit.  Please someone tell me what to do and how to fix this, because if this keeps going on like this, I'm just going to have to go back to Windows which I really do not want to do.

---

### Post by HereInOz on 2007-09-09
First up, tell us what wireless card you are using.  That will help a great deal.

Also, tell us what the result is when you type ifconfig in a terminal.  That will also help.

---

### Post by Johnny_Too_Bad on 2007-09-09
It's a Broadcom something or other.  I'm not sure exactly which one it is, but I know many people have trouble with it.

As for the ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:F9:2E:A6  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fef9:2ea6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82762234 (78.9 MiB)  TX bytes:4180481 (3.9 MiB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6893 (6.7 KiB)  TX bytes:6893 (6.7 KiB)

```

I really do appreciate any help possibly given.  All I want is my internet.  Is that really too much to ask??

---

### Post by HereInOz on 2007-09-09
Yes, you are going to have problems with a Broadcom chip, particularly running Dapper.  There has been some great work done on Gutsy with Broadcom wireless support, so things are looking good for the future, but Dapper did not do well with Broadcom chips.

You may find the following tutorial useful, unless, of course, you have already been there and found it not to your benefit.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Other than that, I would suggest that you wait a little while until Gutsy Gibbon is released and you will probably find that the support for the Broadcom 43xx chips is a lot better than Dapper.

Having said that, the support in Gutsy is not "out of the box" but there are only a couple of easy steps and a bit of software installation to get it working.

Be aware also that many Linux wireless drivers do not support WPA all that well, so it is always best to start up your network as an open, unsecured system, and if you get connection, then start to lift the security level bit by bit and see what happens.

Good luck.

---

### Post by Johnny_Too_Bad on 2007-09-09
I'm actually running Feisty (sorry for not mentioning it), and I really had hoped it would work with my wireless card.  It's too bad, too.  I really have tried everything, but even with a signal, I get nothing.  Perhaps, however, it is because of the security level.  I can't say I've ever tried turning it off, which would make me feel really dumb if that was the only reason.  However, I guess it's best to just wait till Gutsy comes out.  Hopefully it should be smooth sailing by then.

---

### Post by Wiebelhaus on 2007-09-09
if it's asking for a WEP key then just provide it.

---

### Post by Johnny_Too_Bad on 2007-09-09
I have been entering the key, but to no avail.  I enter it, sit, wait for Firefox to time out, and then the box comes up asking for it again.  It continues like this in a vicious cycle until I'm tired of entering my password over and over again, as there is no clear end in sight.

---

### Post by SactoBob on 2007-09-11
It is possible that although your router supports the type of encryption, your wireless card does not?  So your router asks for the  key, and you provide it, but your card cannot handle the encryption?

Try turning off security temporarily on your router and see if you can connect.

Purchase of a software bridge puts and end to all these wireless headaches for about $60.  [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

---

### Post by Johnny_Too_Bad on 2007-09-11
When I was running Windows on it, the card fully supported encryption, so I don't know why that would suddenly change with the installation of Linux.

Did I mention it's an Acer Aspire 3620?  I know there's a thread for that, but the instructions I've followed don't work, and I keep getting error messages in the terminal when following them.  Perhaps if there were another, better forum (than the link from the Broadcom HOWTO) it might solve my problems.

I will have to try turning off encryption, though.  That seems to be the easiest method.

---

### Post by johnaaronrose on 2007-10-30
Hi Johnny_Too_Bad,

I have a Dell Inspiron 1501 with a Min1390 card which is based on the Broadcom BCM4311 chip. On Feisty & Gutsy it didn't work without the use of ndiswrapper. On Gutsy, it intermittently worked using the Restricted Drivers Manager, so I reverted to ndiswrapper use. Only disadvantage of ndiswrapper is that it doesn't allow WEP cracking (i.e. hacking into a WEP network) which is illegal in Britain anyway.

Have you tried ndiswrapper yet? Please post output from commands (in Terminal) for each of: 
sudo lshw -C network
lspci -v|grep Ethernet
lspci -n
sudo iwconfig
sudo modprobe -l
sudo iwlist scan 

There are a number of tutorials on ndiswrapper. I recommend  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28feisty%29%7C%28bcm43xx%29%7C%28wifi%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28feisty%29%7C%28bcm43xx%29%7C%28wifi%29)

There is an excellent Wireless Troubleshooting guide at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29%7C%28troubleshooting%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29%7C%28troubleshooting%29)
(above commands are described in it).

---

