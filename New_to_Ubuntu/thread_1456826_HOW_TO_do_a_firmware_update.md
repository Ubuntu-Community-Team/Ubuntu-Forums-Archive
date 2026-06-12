---
title: "HOW TO do a firmware update"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by eltonw on 2010-04-17
I am sure that the newbie instructions are somewhere out there, but I seem to be getting the *wrong results to my search*. (... what I get is instructions for flashing a mobile phone, or other external peripheral) 

PROBLEM: 
I have recently downloaded a firmware update for my network card (built-in)
I would like to find the instructions on 
:confused:**HOWTO**:
1) verify the current firmware level
2) install the hardward upgrade (a .bin file) in ubuntu / linux
.. if someone could kindly point me in the right direction to find the proper procedure?

I tend to use the GUI more often than the command line, but I am not averse to following instructions or doing the necessary via the console.

TIA

respectfully,

---

### Post by replica2010 on 2010-04-17
I don't know the prescribed way, but I've been trying to fix a network card boot error (without success) and can offer you some suggestions...

ethtool will let you write to your network card's eeprom; are you sure you need to flash the firmware and not do this?

You could also, if your card is supported, use one of the nictools:
sudo apt-get install nictools-pci

Finally, the program in linux for doing stuff like flashing seems to just be flashrom:
"flashrom  is  a  utility for detecting, reading, writing, verifying and
       erasing  flash  chips.  It's  often  used   to   flash   BIOS/EFI/core&#8208;
       boot/firmware images in-system using a supported mainboard, but it also
       supports flashing of network cards (NICs), SATA controller  cards,  and
       other external devices which can program flash chips.
"

---

### Post by eltonw on 2010-04-17
> **replica2010 said:**
> I don't know the prescribed way, but I've been trying to fix a network card boot error (without success) and can offer you some suggestions...

ethtool will let you write to your network card's eeprom; are you sure you need to flash the firmware and not do this?

You could also, if your card is supported, use one of the nictools:
sudo apt-get install nictools-pci

Finally, the program in linux for doing stuff like flashing seems to just be flashrom:
"flashrom  is  a  utility for detecting, reading, writing, verifying and
       erasing  flash  chips.  It's  often  used   to   flash   BIOS/EFI/core&#8208;
       boot/firmware images in-system using a supported mainboard, but it also
       supports flashing of network cards (NICs), SATA controller  cards,  and
       other external devices which can program flash chips.
"
THANK YOU: I'll use synaptic to see if flashrom is in the packages (...using Karmic here)

My concern is [COLOR="Red"]related to this thread[/COLOR]:[http://ubuntuforums.org/showthread.p...52#post9121252]("http://ubuntuforums.org/showthread.p...52#post9121252")

The problem exist at the kernel level with the current linux betas (ALL DISTROS). However, even Karmic is misbehaving (sometimes): Off and on if Ieave my netbook running, it would disconnect, so I'm thinking a firmware update might improve things. 

:)The **[COLOR="Green"]_good news_[/COLOR]** is that RaLink is actively supporting linux with drivers: [URL="http://www.ralinktech.com/support.php?s=2"]
[/URL] AND there is a _backported and patched kernel_ here:[http://rsalveti.net/pub/ubuntu/kernel/lucid]("http://rsalveti.net/pub/ubuntu/kernel/lucid")

---

### Post by eltonw on 2010-04-18
> **replica2010 said:**
> I don't know the prescribed way, but I've been trying to fix a network card boot error (without success) and can offer you some suggestions...

ethtool will let you write to your network card's eeprom; are you sure you need to flash the firmware and not do this?

[COLOR="DarkRed"][FONT="Comic Sans MS"]I wouldn't say that I am sure, but rather, I _would like to verify the current firmware_ level[/FONT][/COLOR]

You could also, if your card is supported, use one of the nictools:
sudo apt-get install nictools-pci

[COLOR="DarkRed"][FONT="Comic Sans MS"]The card [RaLink 2860 / Ralink [FONT="Georgia"]device[/FONT] 2790 in Karmic], does not seem to be supported by nictools.[/FONT][/COLOR]

Finally, the program in linux for doing stuff like flashing seems to just be flashrom:
"flashrom  is  a  utility for detecting, reading, writing, verifying and
       erasing  flash  chips.  It's  often  used   to   flash   BIOS/EFI/core&#8208;
       boot/firmware images in-system using a supported mainboard, but it also
       supports flashing of network cards (NICs), SATA controller  cards,  and
       other external devices which can program flash chips.
"

I have invoked the other tools in the console via: "sudo {command}" but I confess that I_ am out of my depth_.:confused: May I trouble you for further assitance?

... your help is appreciated.

---

### Post by replica2010 on 2010-04-19
Definitely the blind leading the blind here, but sure, I've got a custom kernel with working nvidia drivers; I'll tackle anything! *grins*

To better understand what you're trying to (and to restate to make sure I understand...)

You have a built-in NIC on a netbook.

There's an updated firmware for that NIC that specifically fixes a problem you're having.

You want to use Linux to flash the firmware?

_typically_ (from my understanding), onboard NICs have their firmware in the system bios; flashrom has many many warnings saying not to use it (at this time) for laptops (which I'd classify netbooks as...).  

So, my advice, IF I understand the problem correctly, would be to use the vendor tools (ie, a DOS boot disk...) to flash it, and NOT try to flash the .bin in Linux.  If you brick your netbook, you're likely to be rather unhappy.

By the way, have you looked here?
[http://ubuntuforums.org/showthread.php?t=989130](http://ubuntuforums.org/showthread.php?t=989130)
and 
[http://www.krose.org/~krose/projects.html](http://www.krose.org/~krose/projects.html)
is that applicable to whatever problem you're having?

Also, have you already rolled your own kernel with explicit support for that card? 

I'm completely out of my league with wireless NICs; I've been using wired ones since they were 8bit isa ones... anytime anyone else with a clue wants to jump in...

---

### Post by eltonw on 2010-04-19
> **replica2010 said:**
> Definitely the blind leading the blind here, but sure, I've got a custom kernel with working nvidia drivers; I'll tackle anything! *grins*

To better understand what you're trying to (and to restate to make sure I understand...)

You have a built-in NIC on a netbook.

There's an updated firmware for that NIC that specifically fixes a problem you're having.

You want to use Linux to flash the firmware?

_typically_ (from my understanding), onboard NICs have their firmware in the system bios; flashrom has many many warnings saying not to use it (at this time) for laptops (which I'd classify netbooks as...).  

So, my advice, IF I understand the problem correctly, would be to use the vendor tools (ie, a DOS boot disk...) to flash it, and NOT try to flash the .bin in Linux.  If you brick your netbook, you're likely to be rather unhappy.

By the way, have you looked here?
[http://ubuntuforums.org/showthread.php?t=989130](http://ubuntuforums.org/showthread.php?t=989130)
and 
[http://www.krose.org/~krose/projects.html](http://www.krose.org/~krose/projects.html)
is that applicable to whatever problem you're having?

Also, have you already rolled your own kernel with explicit support for that card? 

I'm completely out of my league with wireless NICs; I've been using wired ones since they were 8bit isa ones... anytime anyone else with a clue wants to jump in...

oh!:( ... I don't have either a floppy drive or a diskette (though I still have my one (collectors' item?) 4 1/2" floppy from aeons ago!
_My onboard RaLink 2860 card ***is*** working with the current release (9.10)_ ... but there are times when it tends to be flaky.

I thought I would first: VERIFY the current firmware level and update it if it's not current. NORMALLY an update should improve / enhance performance.

OTH, I simply cannot connect with any of the current linux betas (ubuntu, mandrive, etc) ... when I boot the live CD.[http://ubuntuforums.org/showthread.php?t=1438175]("http://ubuntuforums.org/showthread.php?t=1438175")

From what I gather the current kernel in these betas sort of 'regressed' the ralink support. OTH, I did find another link with a custom kernel. in the above thread, I mention the link to Ralink who are actively supporting LINUX :biggrin:

I was hoping to simply [COLOR="Olive"]_boot and test the live CD first before deciding to install_[/COLOR]... but I haven't backed up my machine, and don't really have much time to beta test, so.... 

I'll just wait for the final release of LUCID. Hopefully this will be addressed by then: I am just one of innumerable persons who report problems with the ralink cards.

... meanwhile we can both share the  same "white cane"...:lolflag:

---

### Post by replica2010 on 2010-04-19
Haha! Funny with white cane!

For flashing from DOS, I wasn't saying use an actual floppy; heck, I've only got one machine now with a 1.44"!

You can boot to DOS via cd, or, in the case of a netbook, with a flash drive.  There are some gui apps for creating a flash boot to dos; so, if there IS a firmware upgrade, you could go that route.

Btw, for just reading the version, flashrom should do that, if it can talk to the chip.  Have you tried reading it, just to see?

Compiling your own kernel is pretty easy: if you follow the various instructions (basically, install package, run make menuconfig, select the drivers you need, make-kpgp --initrd --revision=01 --append-ralinux_support kernel_image kernel_header, dpkg -i [kernel]) when you boot up, you'll have the choice of using your custom kernel, versus your known working one, so if it doesn't work, you can always regress yourself.

If you haven't used flashrom yet (just to read, mind you, not write), here's how easy it is (sudo first...)
#flashrom
flashrom v0.9.1-r946
No coreboot table found.
Found chipset "Intel ICH7/ICH7R", enabling flash write... OK.
This chipset supports the following protocols: FWH.
Calibrating delay loop... OK.
Found chip "Intel 82802AC" (1024 KB, FWH) at physical address 0xfff00000.

That's on my system (a desktop).  Couldn't hurt to try on yours?

---

