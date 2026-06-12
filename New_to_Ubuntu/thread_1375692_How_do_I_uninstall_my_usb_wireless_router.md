---
title: "How do I uninstall my usb wireless router"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-08
How do I uninstall my usb wireless router to try a different one. I'm having huge issues trying to get my internet working on Ubuntu so I want to try a different router before I uninstall Ubuntu. Can anyone tell me how to go about swapping them over? Thanks.

---

### Post by lisati on 2010-01-08
Depends on how you installed it....... :)

---

### Post by lavinog on 2010-01-08
Please give a model number.
Swapping a USB device should only involve swapping the devices. You don't need to reinstall anything.

---

### Post by ThePinkWitch on 2010-01-08
Thanks for answering ..I thought I would have to uninstall drivers and reinstall new ones
The one I want to try is a D-link DWA-110

---

### Post by caravel on 2010-01-08
USB router?  You need to provide the model number.  Chances are that router can be plugged in to an ethernet port.  At the moment you may have it running as just a modem.

---

### Post by ThePinkWitch on 2010-01-08
> **caravel said:**
> USB router?  You need to provide the model number.  Chances are that router can be plugged in to an ethernet port.  At the moment you may have it running as just a modem.

Is it a router? I don't know..the usb dongle thing that plugs in to my computer and talks to my wifi modem. Its 11:30pm here and I've been trying to sort out my internet all day so I'm a bit tired and delerious LOL. D-Link DWA 110.

---

### Post by 3rdalbum on 2010-01-08
Just unplug it and plug in the new one.

---

### Post by lavinog on 2010-01-08
you don't need to install/uninstall any drivers.  They are part of the kernel modules.

I see from your other threads that you were having problems connecting to a dns server.

Using dhclient you got an ip address of 10.0.0.2
but your dns server you listed is 192.168.1.1

Your dns server doesn't look right.

To test my theory try this:
```

ping 74.125.95.104 -c 4

```
you should get 4 lines that say something like this:
```

64 bytes from 74.125.95.104: icmp_seq=1 ttl=46 time=873 ms

```
and a line that says:
```

4 packets transmitted, 4 received, 0% packet loss, time 3065ms

```

then try
```
ping www.google.com -c 4

```
If the last line says 0 received, then it is a dns problem.

---

### Post by lavinog on 2010-01-08
Can you explain your internet setup?
I am assuming you have some sort of wireless router connected to a modem.
Is the computer a laptop or a desktop?
It would simplify things if you can attach the computer to the router using an ethernet port until the wireless is fixed.

Also, are you sure you are using the correct encryption settings?

---

### Post by ThePinkWitch on 2010-01-08
> **lavinog said:**
> you don't need to install/uninstall any drivers.  They are part of the kernel modules.

I see from your other threads that you were having problems connecting to a dns server.

Using dhclient you got an ip address of 10.0.0.2
but your dns server you listed is 192.168.1.1

Your dns server doesn't look right.

To test my theory try this:
```

ping 74.125.95.104 -c 4

```
you should get 4 lines that say something like this:
```

64 bytes from 74.125.95.104: icmp_seq=1 ttl=46 time=873 ms

```
and a line that says:
```

4 packets transmitted, 4 received, 0% packet loss, time 3065ms

```

then try
```
ping www.google.com -c 4

```
If the last line says 0 received, then it is a dns problem.

I changed to the D-link dongle and it's working fine. Internet is still slow but not dropping out so far (Fingers crossed :D) I did what you said and got this:

kayte@SuperCow:~$ ping 74.125.95.104 -c 4
PING 74.125.95.104 (74.125.95.104) 56(84) bytes of data.
64 bytes from 74.125.95.104: icmp_seq=1 ttl=46 time=261 ms
64 bytes from 74.125.95.104: icmp_seq=2 ttl=46 time=262 ms
64 bytes from 74.125.95.104: icmp_seq=3 ttl=46 time=261 ms
64 bytes from 74.125.95.104: icmp_seq=4 ttl=46 time=262 ms

--- 74.125.95.104 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 261.307/261.977/262.835/0.831 ms
kayte@SuperCow:~$ ping [www.google.com](www.google.com) -c 4
PING [www.l.google.com](www.l.google.com) (74.125.127.105) 56(84) bytes of data.
64 bytes from pz-in-f105.1e100.net (74.125.127.105): icmp_seq=1 ttl=46 time=237 ms
64 bytes from pz-in-f105.1e100.net (74.125.127.105): icmp_seq=2 ttl=46 time=240 ms
64 bytes from pz-in-f105.1e100.net (74.125.127.105): icmp_seq=3 ttl=46 time=238 ms
64 bytes from pz-in-f105.1e100.net (74.125.127.105): icmp_seq=4 ttl=46 time=237 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 237.811/238.525/240.184/0.963 ms
kayte@SuperCow:~$

---

### Post by ThePinkWitch on 2010-01-08
> **lavinog said:**
> Can you explain your internet setup?
I am assuming you have some sort of wireless router connected to a modem.
Is the computer a laptop or a desktop?
It would simplify things if you can attach the computer to the router using an ethernet port until the wireless is fixed.

Also, are you sure you are using the correct encryption settings?

I have a desktop computer. I have adsl with wifi modem and a usb dongle. Looking around the forums my WG111V2 dongle has a lot of problems with ubuntu. The DWA 110 seems to be working a lot better. My internet is still slow but at least it's working. YAY!!!! Thanks for all your help guys.

---

### Post by ThePinkWitch on 2010-01-08
> **lavinog said:**
> Can you explain your internet setup?
I am assuming you have some sort of wireless router connected to a modem.
Is the computer a laptop or a desktop?
It would simplify things if you can attach the computer to the router using an ethernet port until the wireless is fixed.

Also, are you sure you are using the correct encryption settings?

I have desktop computer I have ADSL with wifi modem and usb dongle.....and No I'm not sure I am using the right encryption settings :D I said in another post I think I may have put in the wrong settings when I set it up. I'm a Noobette :)

---

### Post by Darce on 2010-01-08
Hey Pinky !

The D-Link DWA-110 is a USB Wireless Dongle ( network card )
Can you also give the model number of the wireless router/modem you are trying to connect to ?
It's probably the box that you connected your phone line to ( should have an aerial sticking out of it )

Cheers,

Tim

---

### Post by ThePinkWitch on 2010-01-08
> **Darce said:**
> Hey Pinky !

The D-Link DWA-110 is a USB Wireless Dongle ( network card )
Can you also give the model number of the wireless router/modem you are trying to connect to ?
It's probably the box that you connected your phone line to ( should have an aerial sticking out of it )

Cheers,

Tim

Hey :) my modem is a SpeedStream 6520. I guess it's quite old now. Maybe I need a new one. My internet is not dropping out tonight so I'm making progress :) This is the first time I've been on the forums on Ubuntu So cool. I usually have to reboot to windows.

---

### Post by Darce on 2010-01-08
> My internet is still slow but at least it's working.What signal stregth do you get when you hover you mouse over the Wireless Signal Bars ?

In the pic mine is 95%

---

### Post by ThePinkWitch on 2010-01-08
> **Darce said:**
> What signal stregth do you get when you hover you mouse over the Wireless Signal Bars ?

In the pic mine is 95%

97% at the moment. Signal strength has been good right from the start. 

It's 2:45am I'm off to bed. Thanks for your help  goodnight..  :)

---

### Post by caravel on 2010-01-08
> **ThePinkWitch said:**
> Hey :) my modem is a SpeedStream 6520. I guess it's quite old now. Maybe I need a new one. My internet is not dropping out tonight so I'm making progress :) This is the first time I've been on the forums on Ubuntu So cool. I usually have to reboot to windows.
That's wireless router.  If Windows PCs can see that and connect to it without issue, then I wouldn't worry about that for the moment.  The issue has probably more to do with the USB wireless adaptor(s) as that's what Linux installs drivers for.

The WG111V2 seems to be a Realtek RTL8187L chipset.  Those are supposed to be supported in the kernel I think?

The DWA-110 is the RT73 - also kernel support AFAIK?

---

### Post by ThePinkWitch on 2010-01-08
Apaprt from being very slow to connect this morning its working and a lot better. It must have been the WG111v2 dongle. The D-Link is much better. Thankyou everyone :) I think it's ok for now.

---

