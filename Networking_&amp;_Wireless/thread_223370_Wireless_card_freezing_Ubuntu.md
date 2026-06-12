---
title: "Wireless card freezing Ubuntu"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by joes_meat on 2006-07-26
I've just installed Ubuntu (Dapper Drake) on my shiny new laptop.

It is a Compaq Presario V2000.

It has a Sempron 3000+
512 RAM
ATI 200M

I'm using a DLink PCMCIA wireless card. AirPlus G DWL-G630 rev e. Google tells me this has the RT61 chipset.

I managed to get the PCMCIA wireless card working on the Live CD with minimal tinkering - so I formatted and installed Ubuntu.

However, now with the wireless card plugged in - the system hangs on bootup on "setting up network." I waited about 10 minutes with no change. I hit ctrl+c and that skipped it. It booted to the GDM screen and I logged in.

Now I'm given a plain brown screen. Will not finish booting. I can move the mouse. I can use ctrl+alt+1-7. I can use caps lock etc. It seems GNOME has just halted.

The computer boots fine when I remove the wireless card.

Can anyone point me in the right direction?

---

### Post by ireneshusband on 2006-08-13
I have just tried to insert my wavelan silver (i.e. orinoco) card into my powerbook (running dapper) and got an instant total lockup. On reboot the kernel failed to finish loading (can't remember the error message off the top of my head) and I had to boot into macos just to eject the card. 

I then tried unloading all the pcmcia modules, inserting the card and reloading the modules one by one. All went well until I tried to load "pcmcia", at which point the modprobe command hung and had to be terminated with control-C.

This suggests that there are fundamental problems with the way the dapper kernel handles pcmcia, transcending both cards and architectures. I don't think this is hot news, but I can find very little on any of the ubuntu sites explaining what is going on. Does anyone else have any more info on this?

---

### Post by JDAAINOKI on 2006-08-13
Try booting with irqpoll added to the end of your boot. I had a similar problem with my mini-pci card that uses RT2500. I would rather not have the irqpoll used, but for now it is the only way to get wifi up since my last kernel upgrade.  I've read about some problem with IRQ #s in regards to wifi (pci) and x-org (video adapter/PCI??).  I will mess around a bit and see if I can narrow it down more on my system. Please post and let me know if irqpoll worked for you. 

Good Luck,

Jay

---

### Post by Bil-E-daKid on 2006-08-25
Hey there Jay,

I, too, am having this problem with an old Celeron 333 that I'm building for a friend.  It has a linksys rt2500 based card in it and I've managed to get that going using the rt61 driver - not sure if it's the latest or not - that's the next thing to try.

I've tried the irqpoll thing on the boot line in /boot/grub/menu.lst but I still have lockups after I start the card.

The machine boots fine and I can log in and run everything ok without it going.  As soon as I open a terminal and go 'sudo dhclient ra0', the wifi card connects and I can start Firefox and away we go.  Trouble is that any gnome app (prefs, terminal etc) just lock on startup from this point on.

If I configure the card with an init script to start during boot time, then I just get a plain brown screen post-login - gnome doesn't load the desktop or splash or anything.

Any other ideas?

---

### Post by cpbrown on 2006-08-25
Hi

Im having a similar problem with a Belkin card in my notebook; when the card is in, no applications will run, and the system freezes.

Any help? I think this is a pretty big problem.

---

### Post by Bil-E-daKid on 2006-08-25
>> I think this is a pretty big problem.

Yeah - I'm with you on that one cpbrown.  This really makes for an unusable machine.

In fact, to even get Ubuntu onto that PC, I had to install breezy then dist-upgrade from CD to dapper as dapper (alternate) install would fail on various packages like linux-386 and xfont-utils.  Dapper livecd install would hang at partitioning stage.

As I don't know what to do and there doesn't seem to be a way around this (if the card driver upgrade doesn't work), then I'm going to have to try another distro.

---

### Post by dragonlor20 on 2006-08-25
> **joes_meat said:**
> I've just installed Ubuntu (Dapper Drake) on my shiny new laptop.

It is a Compaq Presario V2000.

It has a Sempron 3000+
512 RAM
ATI 200M

I'm using a DLink PCMCIA wireless card. AirPlus G DWL-G630 rev e. Google tells me this has the RT61 chipset.

I managed to get the PCMCIA wireless card working on the Live CD with minimal tinkering - so I formatted and installed Ubuntu.

However, now with the wireless card plugged in - the system hangs on bootup on "setting up network." I waited about 10 minutes with no change. I hit ctrl+c and that skipped it. It booted to the GDM screen and I logged in.

Now I'm given a plain brown screen. Will not finish booting. I can move the mouse. I can use ctrl+alt+1-7. I can use caps lock etc. It seems GNOME has just halted.

The computer boots fine when I remove the wireless card.

Can anyone point me in the right direction?



Hey. I had this problem a day or two ago. I can get you back into gnome with your card still in the computer, but after that you are on your own...

When you get hung up at the brown screen (the Ubuntu splash screen trying to start and getting hung up) press:

> ctrl + alt + backspace

That should get you back to a command line which you are going to need.

Now type:

> sudo vi /etc/network/interfaces

You are going to comment out (put # in front of every line) everything BUT

> auto lo
iface lo inet loopback

You move the cursor to where you want to edit, press insert, change it, then press escape when you are done editting...

Now go to the end of the document, and enter these lines:

> auto ra0
iface ra0 inet dhcp

Save the document by

> SHIFT + ZZ

Then type

> sudo reboot

That should get you into gnome... We turned off your networking though, so beyond this is where I am stuck, but at least from here you can easily edit everything you need to through gnome. I recommend making a .backup of /etc/network/interfaces so that you can easily get back into gnome if that file gets messed up again.

Hope this helps.

Edit: This method can also be used through recovery mode of course, just select that in GRUB...

---

