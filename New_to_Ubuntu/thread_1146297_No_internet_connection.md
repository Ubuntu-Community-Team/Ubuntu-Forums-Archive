---
title: "No internet connection"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by namreg on 2009-05-02
Hi

I've just installed Ubuntu 8.04.2 LTS on my slightly old desktop. I'm using a Belkin USB wireless adapter, and I am able to connect to my wireless router but I can't connect to the internet (all addresses return "Page not found"). I can't find anything that I can understand in the help pages, or find a tool that can check the status of the wireless connection.

Any ideas anyone?
Thanks in advance

Doug

---

### Post by Peter09 on 2009-05-02
Can you post the output of the following commands (from a terminal)

```
ifconfig
```

and

```
route
```

---

### Post by SnaveDogg on 2009-05-02
I had the same problem for about a week, until I took the computer to a guy who was very knowledgeable about BIOS settings, and Ubuntu in general. He found that in the BIOS settings of my computer, it Operating System was set to: WIN98. He changed that setting to "OTHER" and everything started working. Before that, nothing on the PCI bus was enabled. My ethernet card was connected to the PCI bus, and was being recognized as installed, but couldn't be used by the system, until the OS setting was changed to OTHER.

Ya might want to see if your ethernet card (if that is what you are using for internet) is on, being recognized by the OS and is enabled.

After that was done, we made sure in the Network settings that it was set to DCHP so it would automatically search for the IP address from the DSL modem we are using.

It all works now.

Keep in mind, my distribution of the OS is Xubuntu, not Ubuntu.

Hope this helps.

---

### Post by namreg on 2009-05-02
Hi Peter09

Thanks for that quick response

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:e0:18:0c:75:f9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8700 (8.4 KB)  TX bytes:8700 (8.4 KB)

route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


Doesn't mean a great deal to me!

---

### Post by SnaveDogg on 2009-05-02
never mind

---

### Post by namreg on 2009-05-02
Hi SnaveDogg

Thanks for that. How do i get in to check the BIOS, any idea?

---

### Post by Dex73 on 2009-05-02
Since you are connected to the router it could be a problem with the internet service. Can other computers use that router to get online or can you get online with a lane line?

---

### Post by namreg on 2009-05-02
Hi Dex73

Yep. That's what I'm using now, from my laptop. Nothing wrong with the router

---

### Post by Dex73 on 2009-05-02
To check BIOS data restart and watch the screen it should tell you what button to hit. It'll be a Function button(Mine's like F8 I think) Just hit it during start up.

---

### Post by namreg on 2009-05-02
The only option I get on booting the PC is ESC, which just brings up three choices of OS (Ubuntu, Ubuntu safe mode and mem test). Don't seem to get an option to edit the BIOS

---

### Post by Dex73 on 2009-05-02
I restarted just to check. Mine is F2 for BIOS and it gives me the option before GRUB loads up and then gives the ESC option. It's very quick.

---

### Post by namreg on 2009-05-02
Hi Dex
It was F1, although it doesn't show on the screen! Changed the OS to Other and bingo - sorted!

Thanks for that guys.

---

### Post by namreg on 2009-05-04
Err...I'm back again!

Having got the whole thing up and running , setting up email etc and everything was fine, until last night when, after booting up, I noticed that the internet connection had gone down again. The network icon in the top panel shows that I am connected to my router via the Belkin USB wireless adapter, so that looks OK. I've checked the wireless adapter on another old laptop and it works OK. Nothing wrong with the router otherwise I wouldn't be writing this! 8.04 installed. Checked the BIOS and the change I put in (OS = Other), which got it working before, is still there (I'd have been surprised if it wasn't)

First experience with Ubuntu and I'm a little twitchy at the moment - hope someone can help

Thanks

Doug

---

### Post by namreg on 2009-05-04
Posted to a new thread "Lost internet connection 8.04"

---

