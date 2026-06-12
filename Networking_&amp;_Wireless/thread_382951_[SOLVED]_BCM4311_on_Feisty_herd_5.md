---
title: "[SOLVED] BCM4311 on Feisty herd 5"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by T0MA on 2007-03-12
I've been trying to get my wireless card working on a Dell Inspiron E1505 laptop. The wireless is a Dell 1390 something, it usis a Broadcom 4311 chipset.

I was able to make it work on Edgy (both with ndiswrapper and with bcm43xx) but on feisty neither of them seems to work.

With ndiswrapper somehow it doesn't associate any access point with the card. Ndiswrapper loads up with a reboot without a problem, but still no access point and the wireless light doesnt turn on.

Any idea?

```
ssjtoma@ssjtoma-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
ssjtoma@ssjtoma-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ssjtoma@ssjtoma-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:A8:88:50  
          inet addr:137.99.173.89  Bcast:137.99.175.255  Mask:255.255.252.0
          inet6 addr: 2002:8963:ae90:4:215:c5ff:fea8:8850/64 Scope:Global
          inet6 addr: fec0::4:215:c5ff:fea8:8850/64 Scope:Site
          inet6 addr: fe80::215:c5ff:fea8:8850/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6162510 (5.8 MiB)  TX bytes:530515 (518.0 KiB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CF:28:24:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:dfdfc000-dfe00000 

wlan0:ava Link encap:Ethernet  HWaddr 00:16:CF:28:24:8B  
          inet addr:169.254.5.116  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:dfdfc000-dfe00000 

```

---

### Post by teaker1s on 2007-03-12
sudo apt-get install ndiswrapper-utils-1.9

---

### Post by T0MA on 2007-03-12
thats what i already had installed..

now I am reinstalling the whole ubuntu to try out something... hope it will work

---

### Post by T0MA on 2007-03-12
all right, I got it working with bcm43xx..

the problem was I used a newer version of bcmwl5.sys and probably it messed things up..  with version 3.4 it works perfectly fine.. after modprobe it was thinking a little, but the light eventually turned on..

```
ssjtoma@ssjtoma-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` bcmwl5.sys

  filename   :  bcmwl5.sys
  version    :  3.40.73.0
  MD5        :  52d67c5465c01913b03b7daca0cc4077
  microcodes :  2 4 5 
  pcms       :  4 5 

  microcode  :  2
  revision   :  0x00f5
  patchlevel :  0x005a
  date       :  2003-12-22
  time       :  20:11:21

  microcode  :  4
  revision   :  0x00f5
  patchlevel :  0x005a
  date       :  2003-12-22
  time       :  20:11:23

  microcode  :  5
  revision   :  0x00f5
  patchlevel :  0x005a
  date       :  2003-12-22
  time       :  20:11:25

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...
ssjtoma@ssjtoma-laptop:~$ sudo modprobe bcm43xx
ssjtoma@ssjtoma-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ssjtoma@ssjtoma-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:A8:88:50  
          inet addr:137.99.173.89  Bcast:137.99.175.255  Mask:255.255.252.0
          inet6 addr: 2002:8963:ae90:4:215:c5ff:fea8:8850/64 Scope:Global
          inet6 addr: fec0::4:215:c5ff:fea8:8850/64 Scope:Site
          inet6 addr: fe80::215:c5ff:fea8:8850/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23118781 (22.0 MiB)  TX bytes:644964 (629.8 KiB)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:16:CF:28:24:8B  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:5 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17116 (16.7 KiB)  TX bytes:678 (678.0 b)
          Interrupt:4 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

ssjtoma@ssjtoma-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:E0:22:FE   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chiefofthejojos on 2007-03-13
Right on!  So, how did you get the 3.4 firmware version?

---

### Post by max_power on 2007-03-13
I just wrote an Email to Broadcom imploying them to open the wireless chip architecture to open source developers. If you are sick of modprobe (ing) let them know.  heres the link to their feedback page: [http://broadcom.com/contact/feedback.php]("http://broadcom.com/contact/feedback.php")

---

### Post by T0MA on 2007-03-13
I did follow this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28bcm43xx%29]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28bcm43xx%29")

calling this command will print out a list of available bmwl5.sys version on the net.. most  of them is dead, but one of them was working

```
zless /usr/share/doc/bcm43xx-fwcutter/README.gz
```


Another problem arised though when I upgraded the kernel, it produced a bunch of errors with bcm43xx, then i had to restart and now the wireless is not working..

ill try to do bcm43xx again and see if brings it back

---

### Post by T0MA on 2007-03-13
yes, applying the same line again with the same version of bcmwl5.sys brings wireless back

```
sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` bcmwl5.sys
```

---

### Post by davidrools on 2007-03-21
Hi all,

I've been wrestling with my bcm4311 since Edgy and still haven't found a satisfactory solution. (I'm using a USB adapter now that works fine but isn't as sleek).  

In both Edgy and Feisty, I was able to get the 4311 to "work" using fwcutter, but it moves soooooo slow.  It works so unreasonably slow (taking 30-60 seconds to load google.com) that it basically doesn't work.  Another time in edgy, it worked slowly and then stopped working after a couple minutes.  

So for now I'm still trying to get the 4311 to work with ndiswrapper, trying different versions of ndis and different firmware versions to find something that works.  

I'm on a compaq v3000z with a broadcom 4311 that used to be called that but now is detected with the Dell 1390 label.  Any suggestions ya'll have to offer are appreciated, and maybe my experience can offer you a bit of insight/confirmation or something. Happy Ubuntuing.

---

### Post by odelay on 2007-04-09
I have some very general questions about using the BCM4311 wireless card.  As a little background, I've only bothered to setup wireless on my Dell e1505 using ndiswrapper (1.17, I think) and Edgy.

1)  What are the advantages/disadvantages of using ndiwsrapper vs. using fwcutter?  Ease of setup?  Speed?  Reliability?

2)  I've read several instances of people saying you can setup ndiswrapper by just using "sudo apt-get install ndiswrapper-utils-1.9" and you don't have to compile from source.  Is this true for BCM4311?  Will it ever be true?

3)  Will any version of ndiswrapper work with Feisty?  Will any version of ndiswrapper work with Edgy?

I know these are rather involved questions, but I'm really trying to just get a general grasp of my wireless options.  Feel free to answer just one or two.  Thanks in advance.

---

### Post by liljoe76 on 2007-04-09
dunno bout fwcutter, didnt do it for me in edgy and this how to:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)
is the thing that got my 4311 going. continually from edgy to feisty. i believe there are a few threads round these parts that state fwcutter works great in feisty, but i currently have no reason to try. 
[http://ubuntuforums.org/showthread.php?t=384693](http://ubuntuforums.org/showthread.php?t=384693)

---

### Post by T0MA on 2007-06-28
> **odelay said:**
> I have some very general questions about using the BCM4311 wireless card.  As a little background, I've only bothered to setup wireless on my Dell e1505 using ndiswrapper (1.17, I think) and Edgy.

1)  What are the advantages/disadvantages of using ndiwsrapper vs. using fwcutter?  Ease of setup?  Speed?  Reliability?

2)  I've read several instances of people saying you can setup ndiswrapper by just using "sudo apt-get install ndiswrapper-utils-1.9" and you don't have to compile from source.  Is this true for BCM4311?  Will it ever be true?

3)  Will any version of ndiswrapper work with Feisty?  Will any version of ndiswrapper work with Edgy?

I know these are rather involved questions, but I'm really trying to just get a general grasp of my wireless options.  Feel free to answer just one or two.  Thanks in advance.

As far as I can tell fwcutter is a more native solution then ndiswrapper, but ndiswrapper did work for me on Edgy. I didnt try it on Feisty but I figure it would work just as well.

---

### Post by t4thfavor on 2007-06-28
> **max_power said:**
> I just wrote an Email to Broadcom imploying them to open the wireless chip architecture to open source developers. If you are sick of modprobe (ing) let them know.  heres the link to their feedback page: [http://broadcom.com/contact/feedback.php]("http://broadcom.com/contact/feedback.php")

I also wrote them a quick email, to which I received a quick response.

"website_feedback@broadcom.com" 	
to me
	
show details
	 12:47 pm (7 minutes ago) 
As the chipset supplier, Broadcom provides driver support to our customers - the manufacturers of wireless devices - that ultimately provide products to end customers, such as wireless LAN vendors, cable modem vendors, and notebook providers. It is up to these manufacturers to provide product-specific drivers and software support to their end customers. Please contact the manufacturer of your wireless device for their current drivers.



Regards,

Broadcom Support Team

Name: Chance Fulton
Subject: Web Site Feedback/Support Request - 54g Wireless LAN - Drivers
Email Address: [email]chance.fulton@Somewhere.some[/email]thing

Feedback:
Please open the source of your drivers so that the Linux community can get access to affordable quality wireless cards. As of now we as a whole shy away from anything Broadcom because we have to jump through hoops to get it to work (at all). Please take advice from Atheros, Intel, RealTek, and Prism, and allow the community to write a driver for the bcm43XX series of WLAN chips


Doesn't look like they either care nor understand about the problem.

---

