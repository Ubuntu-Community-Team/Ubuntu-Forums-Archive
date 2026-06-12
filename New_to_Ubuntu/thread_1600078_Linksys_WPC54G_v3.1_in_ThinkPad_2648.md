---
title: "Linksys WPC54G v3.1 in ThinkPad 2648"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by alanrose on 2010-10-18
Hello. Just getting started with Ubuntu.

I've installed "Lucid Lynx" (can't remember the version number and can't find it) and used NDISwrapper to load the Windows driver, but I'm not getting connected to my wireless router. I know the hardware is good because I was using the same computer, adapter, and router before replacing Windows with Ubuntu and everything was good.

Perhaps I have the wrong driver. The one I've got is net5211.inf.  Can anyone tell me if that's what I SHOULD have?

Thanks in advance.

     --Alan Rose

(Also: How DO you find the version number for Ubuntu?)

---

### Post by jtarin on 2010-10-18
No time but to post a link.
[http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://linuxwireless.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian)

---

### Post by Hippytaff on 2010-10-18
Lucid is 10.04...the new one 10.10 is called maverick...lets us know how the solution in the link jtarin posted works out.

---

### Post by alanrose on 2010-10-19
Thanks, jtarin. The link took me to instructions which worked very smoothly and installed the firmware on the laptop. I appreciate the help.

Still not working, though.

My desktop PC is currently reporting the network from my wireless router, but when I open "Network Connections" on this Ubuntu-running laptop and choose "wireless", I'm not seeing any information, even though the Linksys adapter is in its slot and its power light is on. Is there somewhere else I should be looking?

Thanks again.

     --Alan Rose

---

### Post by Hippytaff on 2010-10-19
Before we do a bit more digging Have you tried clicking on the 'hidden wireles networks' in the network manager?

---

### Post by SuaSwe on 2010-10-19
> **alanrose said:**
> 
... when I open "Network Connections" on this Ubuntu-running laptop and choose "wireless", I'm not seeing any information, even though the Linksys adapter is in its slot and its power light is on.


If I'm reading that right, that box being empty just means that Ubuntu doesn't have any saved connections yet, so wouldn't worry about that. :) Do you have the network indicator applet thingy on any of the panels? If so, right-click and make sure that Enable Wireless is ticked, then left-click and see if it's reporting any networks (which would if so be listed under Available). If wireless is disabled it will say "Wireless disabled" when left-clicking.

---

### Post by alanrose on 2010-10-19
Hippytaff:  Thanks for your help.

I don't seem to have a "network manager" (nor is that expression found in the index of Keir Thomas's "Beginning Ubuntu Linux"). I've looked in "Network Connections", "Network Proxy Preferences", "Network Tools", and "Network" (under "Places") and haven't found a "hidden wireless networks" to click.

SuaSwe:  Thanks for your help.

I think I know the thingy you mean, but when I right-click it, it doesn't offer anything about "wireless". I see "Enable Networking" (checked) "Enable Notifications" (checked) Connection Information (grayed out), "Edit Connections..." and "About".

"Edit connections" just takes me to the "Network Connections" box, where I can choose "Wireless" and see nothing.

Left-clicking on the thingy shows me "Wired Network" (grayed out and followed by "disconnected", and "VPN Connections". 

Suggestions are welcome, and thanks again.

     --Alan Rose

---

### Post by Hippytaff on 2010-10-19
can you post the output of these commands in the terminal

```

lspci

```

```

iwconfig

```

```

rfkill list

```

:-)

---

### Post by SuaSwe on 2010-10-20
> **alanrose said:**
> 
I see "Enable Networking" (checked) "Enable Notifications" (checked) Connection Information (grayed out), "Edit Connections..." and "About".


To my knowledge this basically means that Ubuntu isn't seeing an enabled wireless adapter (possibly a driver issue as per your initial query). I second Hippytaff's suggestions below - let's have a look at the PCI and network peripherals!

---

### Post by jtarin on 2010-10-20
I've had some success with "wicd" when network manager failed.

---

### Post by alanrose on 2010-10-20
Sure.

lspci:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0c)
00:03.1 Serial controller: Agere Systems LT WinModem (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

rfkill list

This command produced no response except a repeat of the prompt.

Thanks again.

     --Alan Rose

---

### Post by jtarin on 2010-10-20
You'll need the Broadcom driver. Atached is a README from the downloadable driver from Broadcoms site, however read the README before making a descision to get it there.

---

### Post by Hippytaff on 2010-10-21
+1 jtarin - can be a potch this!

---

### Post by jtarin on 2010-10-21
> **Hippytaff said:**
> +1 jtarin - can be a potch this!Potch????:P

---

### Post by Hippytaff on 2010-10-21
> **jtarin said:**
> Potch????:P
 
I guess it's a colloquialism - potch - to be a pain to do, to have to mess around to achive sucess :-)
 
This might help - [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

---

### Post by jtarin on 2010-10-21
> **Hippytaff said:**
> I guess it's a colloquialism - potch - to be a pain to do, to have to mess around to achive sucess :-)
 
This might help - [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
Ah! Gotcha! Yea a pain but a lot of fun!:P

---

### Post by alanrose on 2010-10-22
I opened the readme file regarding the Broadcom driver, then decided to print the whole thing out. All seven pages.

This is going to take a while.

Thanks again.

     --Alan Rose

---

### Post by mozdog on 2010-10-24
I used the following directions with 10.10 on a Dell Inspiron 8100.
 
[http://ubuntuforums.org/archive/index.php/t-770390.html](http://ubuntuforums.org/archive/index.php/t-770390.html)
 
They worked great. No troubles at all and very very simple.
 
Mozdog

---

### Post by alanrose on 2010-11-04
[SIZE=4]I tried the instructions found at the link that jtarin suggested and got to page 3 (of 7) before getting an incomprehensible error message and having no idea how to proceed.

I tried the instructions found at the link that mozdog suggested and got to page 3 (of 4) before getting a different IEM.

I'll probably never get this laptop connected wirelessly to the net, but I'll still get some use out of it: I'm going to carry it with me wherever I go and the next person who tells me that Ubuntu is so easy to use because everything just works, I'm going to beat him to death with it.
[/SIZE]

---

### Post by Hippytaff on 2010-11-05
> **alanrose said:**
> [SIZE=4]I tried the instructions found at the link that jtarin suggested and got to page 3 (of 7) before getting an incomprehensible error message and having no idea how to proceed.[/SIZE]
 
[SIZE=4]I tried the instructions found at the link that mozdog suggested and got to page 3 (of 4) before getting a different IEM.[/SIZE]
 
[SIZE=4]I'll probably never get this laptop connected wirelessly to the net, but I'll still get some use out of it: I'm going to carry it with me wherever I go and the next person who tells me that Ubuntu is so easy to use because everything just works, I'm going to beat him to death with it.[/SIZE]

 
lol, that's one thing you can do. Broadcom aren't very well supported at the moment, but things are improving. They've only just opened up thier proprietary drivers, so the newer ones should work ok. Sorry it's not working out.

---

### Post by jtarin on 2010-11-05
[QUOTEI tried the instructions found at the link that jtarin suggested and got to page 3 (of 7) before getting an incomprehensible error message and having no idea how to proceed.][/QUOTE]I would suggest proceeding by posting your incomprehensible error message.

---

### Post by Hippytaff on 2010-11-05
> **jtarin said:**
> [QUOTEI tried the instructions found at the link that jtarin suggested and got to page 3 (of 7) before getting an incomprehensible error message and having no idea how to proceed.]> I would suggest proceeding by posting your incomprehensible error message.
 
Good suggestion :-)

---

### Post by JonR79 on 2011-02-18
I went through the instructions in the link that Mozdog put up and everything worked fine until I rebooted. Now every time I turn on the computer I have to go to the terminal and type "sudo modprobe ndiswrapper".

Is there a reason for that? And is there any way to automate it on startup?

---

