---
title: "Wired Connection DSL, New User"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Brittaintrail on 2008-06-14
Sorry if this is sloppy, I wrote it out all nice and organized and it was like a page long and full of colorfull detail then windows crashed so I am a bit on edge....


Hello, I am new to Ubuntu but am eager to learn about this attractive OS. I have a fresh installation of 8.04 and need help with my internet connection. Here's some info though I don't know if its relavant. 
My ISP is sprint I have a linksys wireless router though the computer is plugged directly to the router.

I went through all the steps for troubleshooting in the help section of the program but basically it seemed to think it should work automatically. Is it ever that simple?

When I type "sudo pppoeconf" it sees 3 devices but after scanning them it cannot find the PPPoE access concentrator of my provider. It tells me to check my cables. They're fine.

When I try to ping 82.211.81.158 I do not recieve any packets. When I try to ping a website I am told that I am not connected.
When I try to piog ubuntu.com I am told that the address "ubuntu.com" cannot be found please enter a valid network address and try again.

P.S. Do I need to install drivers for my Mobo or anything like that? I assume not considering it seems to work.

---

### Post by superprash2003 on 2008-06-15
why not configure your linksys router to ppoe mode so it would do the dialing part

---

### Post by Paris Heng on 2008-06-15
Yes correct.

---

### Post by prshah on 2008-06-15
> **Brittaintrail said:**
> 
I have a fresh installation of 8.04 and need help with my internet connection. 
My ISP is sprint I have a linksys wireless router though the computer is plugged directly to the router.

P.S. Do I need to install drivers or anything like that? I assume not considering it seems to work.

Yes it is _usually_ as simple as plugging in your router. Sometimes, however... you need these forums!

How do you connect on Windows... do you do any dial up or just switch it on, and you're connected in a few seconds?

What is the model number of your linksys router?

---

### Post by Brittaintrail on 2008-06-15
> **superprash2003 said:**
> why not configure your linksys router to ppoe mode so it would do the dialing part

When I go to mo router settings the connection type is allready listed and was before listed as pppoe

---

### Post by Brittaintrail on 2008-06-15
> **prshah said:**
> Yes it is _usually_ as simple as plugging in your router. Sometimes, however... you need these forums!

How do you connect on Windows... do you do any dial up or just switch it on, and you're connected in a few seconds?

What is the model number of your linksys router?

In XP it used to be as simple as plugging in the eithernet cable then in a matter of seonds it would be connected. No Dialing... Linksys model # is "WRT150N"

---

### Post by esteckis on 2008-06-15
Here is a simple check, it most likely is not your problem but if it is, then easy to solve.

I am a newbie and when I first tried UBUNTU everything ran fine except my internet connection. It took me days and just by chance I came across the answer for it.  If you are using Windows and Ubuntu on the same system, if you check under windows hardware your Ethernet properties, windows has an option to disable the Ethernet when you shutdown your computer (for me, it was set to yes:( ).  That is what was happening to me.

---

### Post by Brittaintrail on 2008-06-15
> **esteckis said:**
> Here is a simple check, it most likely is not your problem but if it is, then easy to solve.

I am a newbie and when I first tried UBUNTU everything ran fine except my internet connection. It took me days and just by chance I came across the answer for it.  If you are using Windows and Ubuntu on the same system, if you check under windows hardware your Ethernet properties, windows has an option to disable the Ethernet when you shutdown your computer (for me, it was set to yes:( ).  That is what was happening to me.

Thanks for the advice but currently I have no other operating systems installed on my PC. I have a fresh install of Ubuntu 8.04. I think I remember having some issues with internet with XP but those were fixxed when I installed drives from the CD that came with my ASUS mobo. There aren't any on this dvd for linux UBUNTU.

---

### Post by prshah on 2008-06-15
> **Brittaintrail said:**
> In XP it used to be as simple as plugging in the eithernet cable then in a matter of seonds it would be connected. No Dialing... Linksys model # is "WRT150N"

Good that means you have a direct (pppoe/pppoa) Internet connection. That _should_ just work. If it doesn't we can find out why with the commands below:

Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

sudo mii-tool eth0
sudo dhclient eth0
ifconfig eth0
cat /etc/resolv.conf
ping www.google.com

```

Replace eth0 with the actual name of your interface. (Should be eth0; essentially, the first command checks if the cable is plugged in, if it fails, check other interfaces shown with the command "ifconfig").

---

### Post by Brittaintrail on 2008-06-18
when I "ifconfig" I get...

trail@trail-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:5b:8e:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:245 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:5b:9c:96  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4601 (4.4 KB)
          Interrupt:246 Base address:0x2000 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:92:5b:9c:96  
          inet addr:169.254.7.174  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:246 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64284 (62.7 KB)  TX bytes:64284 (62.7 KB)


when I "sudo mii-tool eth:avahi", "sudo mii-tool eth0", sudo mii-tool eth1", and "sudo mii-tool lo" I get the response "SIOCGMIIPHY on 'eth:avahi' failed: Operation not supported"
"SIOCGMIIPHY on 'eth0' failed: Operation not supported" "SIOCGMIIPHY on 'eth1' failed: Operation not supported" "SIOCGMIIPHY on 'lo' failed: Operation not supported"

I changed eithernet ports on the back of my PC and have the same results.

Any idea? Thankyou so much for al the help so far.

---

### Post by prshah on 2008-06-18
> **Brittaintrail said:**
> when I "sudo mii-tool eth:avahi", "sudo mii-tool eth0", sudo mii-tool eth1", and "sudo mii-tool lo" I get the response "SIOCGMIIPHY on 'eth:avahi' failed: Operation not supported"
"SIOCGMIIPHY on 'eth0' failed: Operation not supported" "SIOCGMIIPHY on 'eth1' failed: Operation not supported" "SIOCGMIIPHY on 'lo' failed: Operation not supported"

I changed eithernet ports on the back of my PC and have the same results.


Forget all ports except eth0 and eth1. give these commands```

sudo ifup eth0
sudo mii-tool eth0
sudo ifup eth1
sudo mii-tool eth1

```

and post back outputs if internet still doesn't work.

---

### Post by Brittaintrail on 2008-06-18
So...
trail@trail-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
trail@trail-desktop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
trail@trail-desktop:~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Operation not supported
trail@trail-desktop:~$ sudo mii-tool eth1
SIOCGMIIPHY on 'eth1' failed: Operation not supported


P.S. I just bought vista 64 and internet worked as soon as I installed vista...(works for vista not Ubuntu)
This doesn't mean I'm giving up though.
Also I installed Ubuntu allongside vista. I don't know if this changes anything. Thankyou so much for your persistant help with this matter.

---

### Post by prshah on 2008-06-19
> **Brittaintrail said:**
> So...
trail@trail-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
trail@trail-desktop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.


Eh? Can you post output of```
cat /etc/network/interfaces
cat /var/run/network/ifstate
```

---

### Post by Brittaintrail on 2008-06-19
trail@trail-desktop:~$ cat /exc/network/interfaces
cat: /exc/network/interfaces: No such file or directory
trail@trail-desktop:~$ cat /var/run/network/ifstate
lo=lo

---

