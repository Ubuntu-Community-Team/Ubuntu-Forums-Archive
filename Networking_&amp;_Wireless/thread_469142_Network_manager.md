---
title: "Network manager?"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Steve- on 2007-06-09
I was browsing the Full Circle magazine and noticed a nice wireless manager, as seen in [this image]("http://www.thinkwiki.org/images/b/b7/Available-accesspoints.jpg"). It seems to detect all the wireless networks and I am wondering why I don't have this, it comes standard with 7.04?

What I do have in my system tray is a program calling itself "NetworkManager Applet 0.6.4" which allows me a choice between wired connection and nothing else (not much a choice), and gives me access to my VPN to university. I also have a connection properties thingy, which I believe is the Gnome Connection Monitor item you can add to the panel.

At current, I can connect to an open wireless network, but I shall need access to WEP/WPA secured networks from monday onwards.

Long story short, how do I get the wireless thing I see in that picture?

Thanks,
Steve

---

### Post by merlinus on 2007-06-09
This looks to me like wlassistant, which is not installed as part of ubuntu.

It may be part of kubuntu, but since I do not run that flavor, I do not know.

You can, however, get it via Synaptic.

hth....

-merlin

---

### Post by Steve- on 2007-06-09
According to page 9 of Full Circle Magazine Issue 0, it's standard in 7.04 and includes WPA out of the box. Doesn't give an exact name though.

---

### Post by merlinus on 2007-06-09
OK.  Fired up my laptop that has a wireless adapter.

What you are looking for is a black icon resembling a computer monitor on the top taskbar just to the left of the battery icon and date and time.

I have read, however, that this is buggy when set to Roaming.

It crashed my computer, so I installed wlassistant.

YMMV....

-merlin

---

### Post by handaxe on 2007-06-09
That IS NetworkManager that comes with a normal install of Feisty.

Link : [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

As for WPA out of the box: please refer to [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

The issue is whether or not your card plays nicely with wpa-supplicant and other tools on which NM depends.

An alternative (and there are yet others too) is Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

HA

---

### Post by ugm6hr on 2007-06-09
Yep - Network Manager.

In your connection settings - try ticking the "enable roaming mode box".
Then right-click the NetworkManager Applet 0.6.4 icon - and ensure enable netowkring and enable wireless are ticked.
Then left click the same icon - and it should bring up the options - just like in the pic.

This does of course assume your wireless card behaves itself with Network Manager ;)

---

### Post by merlinus on 2007-06-09
> 
An alternative (and there are yet others too) is Wicd:


When I try to install wicd, I get a message from the Package Installer that it conflicts with ubuntu network manager.

Interesting....

-merlin

---

### Post by djmaxmalta on 2007-06-09
yes it is standard on 7.04 and not with the predesecors, but the screw up is how may i connect to a pppoe connection u know broadband from the phone line??? till know i havent found it on ubuntu but on a kde versions of linux and kde run .rpm files??? but ubuntu a dabian baesed runs .deb i need some hints on the .rpm .dep .etc....

---

### Post by merlinus on 2007-06-09
Alien will turn an .rpm into a .deb.  You can get it via Synaptic.

-merlin

---

### Post by handaxe on 2007-06-09
You can safely un-install NM and install Wicd and visa versa.  Nothing ventured, nothing gained and no loss in the offer :)

HA

---

### Post by merlinus on 2007-06-09
OK -- fair enough.

A question, however.  I am using static IP for the wired connection, and Roaming for wireless.

Will this work with wicd?

The first works perfectly, but Roaming and wireless leads to system crash, for me, with NM.

-merlin

---

### Post by handaxe on 2007-06-09
If there is a card issue - with wpa-supplicant for instance - then both Wicd and NM may wobble or not work at all.

Wicd does both wired and roaming, version 1.2.9 sets up a wired profile and can be static.

There is also wifi radar...

HA

---

### Post by spier on 2007-06-09
This title:  "Network manager?" I couldn`t resist, sorry.

Shouldn`t it be "DHCP manager"?

Seems there is a lack of network stuff to manage!

---

### Post by djmaxmalta on 2007-06-09
> **handaxe said:**
> You can safely un-install NM and install Wicd and visa versa.  Nothing ventured, nothing gained and no loss in the offer :)

HA
was this for me or another user?

---

### Post by handaxe on 2007-06-09
Sorry, not you - the OP.

HA

---

### Post by djmaxmalta on 2007-06-09
> **handaxe said:**
> Sorry, not you - the OP.

HA
okay... erm do you know how to set a pppoe connection for ubuntu or do i need to install something like on kubuntu or puppy

---

### Post by handaxe on 2007-06-09
No experience there, sorry

Is

```
sudo pppoeconf
``` from the CLI no good?

HA

---

