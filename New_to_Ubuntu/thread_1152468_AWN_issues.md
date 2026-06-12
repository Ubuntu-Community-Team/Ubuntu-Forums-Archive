---
title: "AWN issues"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by winstont11 on 2009-05-07
mesty@melbuntu:~$ sudo apt-get install avant-window navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window

I believe I was taking the right steps, but I wasnt able to get the request to go through.  Did I do the right thing?

---

### Post by raymondh on 2009-05-07
> **winstont11 said:**
> mesty@melbuntu:~$ sudo apt-get install avant-window navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window

I believe I was taking the right steps, but I wasnt able to get the request to go through.  Did I do the right thing?

> avant-window-navigator    instead of avant-window navigator

---

### Post by raymondh on 2009-05-07
once done, alt-f2 and type avant window navigator to run. AWN's wiki has got a good guide

Have fun

---

### Post by raymondh on 2009-05-07
[http://wiki.awn-project.org/FAQ](http://wiki.awn-project.org/FAQ)

Have a good read.

---

### Post by winstont11 on 2009-05-07
> **raymondhenson said:**
> once done, alt-f2 and type avant window navigator to run. AWN's wiki has got a good guide

I tried that and then I got this message "Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

I dont know how to do that, could you help or is there somewhere I could read about this?  I feel like I have silly questions.

---

### Post by raymondh on 2009-05-07
> **winstont11 said:**
> I tried that and then I got this message "Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

I dont know how to do that, could you help or is there somewhere I could read about this?  I feel like I have silly questions.

system>administration>synaptic package manager...password .... then reload (you don't have to, I just make it my habit) ... then search for compiz setting manager  .... check (syanpatic will also check necessary programs) and then apply.  Wait to finish then close

Once done, right click on any empty part of the desktop>change visual background>visual effects ... see if you can enable normal or extra

From then, alt+f2 to run awn again.  

See if this works.  Let us know

---

### Post by raymondh on 2009-05-07
No worries about having "silly questions" ..... we all are beginners

Have a good read

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by winstont11 on 2009-05-07
> **raymondhenson said:**
> system>administration>synaptic package manager...password .... then reload (you don't have to, I just make it my habit) ... then search for compiz setting manager  .... check (syanpatic will also check necessary programs) and then apply.  Wait to finish then close

Once done, right click on any empty part of the desktop>change visual background>visual effects ... see if you can enable normal or extra

From then, alt+f2 to run awn again.  

See if this works.  Let us know

I did that and then when I got to enabling normal or extra I got this message for both "Desktop effects could not be enabled"

---

### Post by winstont11 on 2009-05-07
> **raymondhenson said:**
> No worries about having "silly questions" ..... we all are beginners

Thanks

---

### Post by raymondh on 2009-05-07
> **winstont11 said:**
> I did that and then when I got to enabling normal or extra I got this message for both "Desktop effects could not be enabled"

Try a reboot.  

If no luck, let's take a look at your graphic card

on a terminal, can you please type and post

```
lspci
```

---

### Post by raymondh on 2009-05-07
I should explain .... in 9.04, there are some drivers that are blacklisted hence you cannot run compiz hence no desktop effects .... but there are documented ways around/through blacklisted drivers.

---

### Post by raymondh on 2009-05-07
Another code to check your VGA

lspci | grep VGA



PS ... have you updated your 9.04 install?

---

### Post by winstont11 on 2009-05-07
> **raymondhenson said:**
> Try a reboot.  

If no luck, let's take a look at your graphic card

on a terminal, can you please type and post

```
lspci
```

mesty@melbuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

---

### Post by winstont11 on 2009-05-07
> **raymondhenson said:**
> Another code to check your VGA

lspci | grep VGA

mesty@melbuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

---

### Post by winstont11 on 2009-05-07
> **raymondhenson said:**
> PS ... have you updated your 9.04 install?

I'm not sure.. a friend of mine configured my computer for me.  I haven't done anything to it.

---

### Post by raymondh on 2009-05-07
winstonT .... let's try a compiz-check by forlong.  Read first before executing.  Compiz-check also recommends fixes if any.

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

While you're doing that, I'm researching about VIA and compiz

---

### Post by raymondh on 2009-05-07
> **winstont11 said:**
> I'm not sure.. a friend of mine configured my computer for me.  I haven't done anything to it.

To update

sudo apt-get update

Also, have you enabled hardware drivers?  Try system > administration > hardware drivers

Then read forlongs blog and do a compiz check.  I'll search more for VIA and compiz issues

---

### Post by raymondh on 2009-05-07
winstont ... here's an ubuntu forum thread involving compiz and via unichrome cards.  Read in totality and understand before applying changes

[http://ubuntuforums.org/showthread.php?t=624045&page=2](http://ubuntuforums.org/showthread.php?t=624045&page=2)

I'll keep on searching for more answers.

something to read if you decide to use openchrome

[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=OpenChrome+driver+documentation](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=OpenChrome+driver+documentation)

---

### Post by winstont11 on 2009-05-08
> **raymondhenson said:**
> Also, have you enabled hardware drivers?  Try system > administration > hardware drivers

When I did that I got a pop up that said "No proprietary drivers are in use on this system" and it did not give me the option to enable anything.

---

### Post by gandaran on 2009-05-08
winstont11
your video card must support 3D video rendering to run compiz and AWN, if it doesn't you can still have AWN but with another AWN (trunk version), if you want to try it, remove all AWN packages you have installed and add this repository to software sources [https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa) then install the **awn-manager-trunk** in synaptic.
before running AWN trunk you need to enable the compositing manager, go to gconf-editor » apps » metacity » general » check the compositing manager box, now you can start avant-window-navigator.

---

