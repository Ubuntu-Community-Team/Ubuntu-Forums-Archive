---
title: "Browser crashes"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by antalves on 2011-01-25
Any Browser Crashes after a few minutes watching videos on the Web. This happens with FFox or Chrome. I have checked that using FFox in SafeMode it does not close!
I'm using Ubuntu 10.10. I've repaired Broken Packs, with no results at all

What can I do besides reinstall Ubuntu?:(

---

### Post by cipherboy_loc on 2011-01-25
Have you tried running it from the command line and posting the output?

The terminal is located under Applications -> Accessories -> Terminal, and you can launch Firefox with:

```

firefox
## __ OR if you are using Firefox 4.0b__
firefox-4.0

```

Chrome is:
```

chromium-browser

```


Cipherboy

---

### Post by antalves on 2011-01-25
I already did that and the browser also shut down . I have not read the message on the terminal because, when browser closes  opens a screen asking for changing the user !...

---

### Post by cipherboy_loc on 2011-01-25
Try redirecting the output to a file:

```

firefox 2>~/ff.stderr.log.txt >~/ff.stdout.log.txt

```


Cipherboy

---

### Post by khelben1979 on 2011-01-26
Is this problem you are having with your web browsers isolated to when you only use web browsers or is it other applications which crashes too?

In some cases it can be because of your hardware is getting too hot and don't get the proper cooling it needs, but so far we don't know that.

---

### Post by antalves on 2011-01-26
Event is unique to Browsers. The temperature measured by screenlet is within the limits

---

### Post by antalves on 2011-01-26
> **cipherboy_loc said:**
> Try redirecting the output to a file:

```

firefox 2>~/ff.stderr.log.txt >~/ff.stdout.log.txt

```


Cipherboy

Look: none log file has been created!...

---

### Post by khelben1979 on 2011-01-27
Is this issue isolated to: watching videos on the web? If so, it could be that it's using flash and that this is the source of the problem.

Report back what this says: ```
http://www.adobe.com/software/flash/about/
```

---

### Post by antalves on 2011-01-27
Message: *You have version 10,1,102,65 installed*

It only happens with videoa thru internet

---

### Post by khelben1979 on 2011-01-29
> **antalves said:**
> Message: *You have version 10,1,102,65 installed*

It only happens with videoa thru internet

Looking at the version, it looks good. 

I'm wondering if we can isolate the cause to YouTube, and if so, then it can be your video drivers which don't play nicely to flash content in your web browser.

Report back what version of your video drivers which you are presently using. Type ```
lspci
``` and cut and paste the information to this support thread, then we should see how that looks like including some information from your computer hardware.

---

### Post by antalves on 2011-01-29
Same results in YouTube, Metacafe, etc
Log:

antonio@antonio:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
antonio@antonio:~$

---

### Post by khelben1979 on 2011-01-30
Interesting to see that video card! 

I would like to know what it says in the nVidia Control panel what version you got for that Geforce card. It would be nice to be able to rule out any problems with the nVidia drivers. Have you tried with other drivers?

Also, if the computer has gotten a bit old, there could be your powersupply which does not provide sufficient power to that nVidia card nowadays (looses in efficency with old age) which can make the graphics to crash, but we don't know this yet.

---

### Post by antalves on 2011-01-31
I have here screenshots of some NVidia data:

---

### Post by khelben1979 on 2011-01-31
Looks good! I've tested the 260.x drivers myself and so that should not be the problem here.

What is the age of your [power supply]("http://en.wikipedia.org/wiki/Power_supply")?

---

### Post by antalves on 2011-01-31
It is about 2 years old. It's specifations match the one needed for that video card. Besides, if I can see "normal" video, it's innocent, I suppose
I think there was some corruption in Ubuntu

---

### Post by ben889 on 2011-01-31
i was having problems with browser crashing but i was using a 64 bit os with 32 bit flash. there is firfox addon that fixes that not sure what post i found the link though
 
 
found the link 
 
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by khelben1979 on 2011-01-31
> **ben889 said:**
> i was having problems with browser crashing but i was using a 64 bit os with 32 bit flash. there is firfox addon that fixes that not sure what post i found the link though
 
 
found the link 
 
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

I'm very sceptical about install a web browser plugin to solve instability in graphics. More Firefox addons can even make things worse because of addon conflicts + increases memory usage which reduces performance on a weak computer system.

Have you looked for dust in the Geforce fan? It might need to get cleaned.

---

### Post by antalves on 2011-02-01
Here is what I did: I have changed nVidia 260 driver for 173.14.28. Is ok now

---

### Post by khelben1979 on 2011-02-01
Sounds good!

---

