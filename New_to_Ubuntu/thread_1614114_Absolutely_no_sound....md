---
title: "Absolutely no sound..."
date: 2010-11-05
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-05
Hello:

I have no 'sound' at all.

ViewSonic VA1930wm with built-in speakers - no sound.

Logitech H360 Headset - no sound.

Acer AX3400-E3212 computer.

Any suggestions?

Thanks,

---

### Post by Hippytaff on 2010-11-05
I know this is probably not the problem, but it isn't muted is it? I spent hours trying to resolve a problem with sound only to find I had it muted...though I am particularly dense sometimes :-)

---

### Post by Robert.Thompson on 2010-11-05
> **Hippytaff said:**
> I know this is probably not the problem, but it isn't muted is it? I spent hours trying to resolve a problem with sound only to find I had it muted...though I am particularly dense sometimes :-)

Nope, not muted.

---

### Post by migs73 on 2010-11-05
Rob,

Post back here with the output from

```
lspci
```

when put into terminal (Applications > Accessories > Terminal  or Ctrl+Alt+T)

This will list the cards on you PCI bus, hopefully including you sound card.

BTW it is lower case LSPCI.

Mike

---

### Post by Robert.Thompson on 2010-11-05
> **migs73 said:**
> Rob,

Post back here with the output from

```
lspci
```

when put into terminal (Applications > Accessories > Terminal  or Ctrl+Alt+T)

This will list the cards on you PCI bus, hopefully including you sound card.

BTW it is lower case LSPCI.

Mike

Hi Mike, here is the output:
rob@rob-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)
rob@rob-desktop:~$

Thanks,

---

### Post by Hippytaff on 2010-11-05
Nvidia driver issues Migs?

---

### Post by Robert.Thompson on 2010-11-05
> **Hippytaff said:**
> Nvidia driver issues Migs?

:confused:

---

### Post by Hippytaff on 2010-11-05
> **Robert.Thompson said:**
> :confused:
 
Sorry, was asking the other poster (migs) if he thought it was a driver issue :-)
 
You might need to install the Nvidia driver
 
see - [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by migs73 on 2010-11-05
> **Hippytaff said:**
> Nvidia driver issues Migs?

Hmmmm... Can't find any thing on google about the drivers for nVidia audio problems as such.

Rob, have you tried clicking on System > Administration > Additional Drivers and see if it returns any for your Audio. If it is not already activated, do so and see if it helps. 

I don't even now if there are additional drivers for it to be honest but it's worth a try!!


EDIT what I have asked you to do is the same as the Psychocats page, but with the updated names (they changed in 10.04 I think).


BTW Hippytaff, my name is Mike.....to save any more confusion........mind you we are talking about audio!!

---

### Post by Hippytaff on 2010-11-05
I didn't think Nvidia audio drivers came as standard?

---

### Post by migs73 on 2010-11-05
I must be a bit dense today, Robs Mobo is nVidea. I am just used to seeing nVidea and thinking Video card drivers. When I noticed it was audio I was a bit stumped (still am!).

Probably best to look here [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

Let us know how you get on.

Mike

---

### Post by Robert.Thompson on 2010-11-05
> **migs73 said:**
> Hmmmm... Can't find any thing on google about the drivers for nVidia audio problems as such.

Rob, have you tried clicking on System > Administration > Additional Drivers and see if it returns any for your Audio. If it is not already activated, do so and see if it helps. 

I don't even now if there are additional drivers for it to be honest but it's worth a try!!


EDIT what I have asked you to do is the same as the Psychocats page, but with the updated names (they changed in 10.04 I think).


BTW Hippytaff, my name is Mike.....to save any more confusion........mind you we are talking about audio!!

So, I did this and it recommended a different driver which it installed.

The result: my headset works!!!!:)
            my monitor speakers do not.:(

Thanks a lot to both of you.

---

### Post by Hippytaff on 2010-11-05
You may need to just confirgure it for the monitorspekaers to work now, I'm not on my ubuntu box to look around, but there might be something in preferences etc

---

### Post by migs73 on 2010-11-05
Try looking in 
System > Preferences > Sound and then click on the Output tab. You may need to set it there.

EDIT; That followed on nicely from what Hippytaff just said, great minds think alike (and fools seldom differ!!)

---

### Post by owlhoot on 2010-11-05
I have the same problem on my laptop. Here is the info from the terminal command posted above:
> 
owlhoot@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
owlhoot@ubuntu:~$ 

I have already checked all my sound settings and everything shows on, and volume up, no muting. Sound test fails, for both headphones and built in speakers. Any help is appreciated.

---

### Post by Robert.Thompson on 2010-11-05
> **owlhoot said:**
> I have the same problem on my laptop. Here is the info from the terminal command posted above:


I have already checked all my sound settings and everything shows on, and volume up, no muting. Sound test fails, for both headphones and built in speakers. Any help is appreciated.

Did you do: 'System > Administration > Additional Drivers'  to see if the recommended driver is installed?

Did you select your headphones when you did: 'System > Preferences  > Sound > Hardware & Input & Output' ?


Also, [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

[COLOR="Red"]**And watch out for 'Mute'.**[/COLOR]

That is all I can suggest as I am a noob.

---

### Post by Hippytaff on 2010-11-05
> **Robert.Thompson said:**
> Did you do: 'System > Administration > Additional Drivers' to see if the recommended driver is installed?
 
Did you select your headphones when you did: 'System > Preferences > Sound > Hardware & Input & Output' ?
 
 
Also, [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)
 
That is all I can suggest as I am a noob.
 
Not that much of a noob now. You can troubleshoot sound issues :-)

---

### Post by Hippytaff on 2010-11-05
Owlhoot - your pci device is intel which would normally work out of the box, so as Robert suggested check - 
 
'System > Preferences > Sound > Hardware & Input & Output'

---

### Post by migs73 on 2010-11-05
Rob,

Does that mean your sound is now working?

---

### Post by Robert.Thompson on 2010-11-05
> **migs73 said:**
> Rob,

Does that mean your sound is now working?

Sorry Mike, my headset works but the speakers integrated with my monitor do not.

I can settle for that, I am not much of a 'listener' when I am on the PC.

Thanks again for you help,

---

