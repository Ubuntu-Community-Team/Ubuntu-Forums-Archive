---
title: "installed virtualbox to use new printer now printer not recognized"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by pilisopa on 2010-12-01
I have been working on trying to get a new Canon MF3240 working so I can start printing for the past two days to no avail.

First, the printer was not at all recognized by Lucid. Then, I did something, I can't remember what, and it recognized the printer but since there is no PPD and no support for linux, I couldn't set it up to print.

So, I got virtualbox and installed (grudgingly) XP. That works fine but it is not recognizing the printer when it's plugged into the USB port. Yes, I changed the settings in Users and Groups and yes, I allowed USBs in VB. 

I don't even need the printer to be able to work in Lucid, I just need it to properly recognize that the printer is plugged in so I can print through VB (hopefully). 

I ran lsusb and this was the result:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04a9:2684 Canon, Inc. MF3200 series
Bus 001 Device 004: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


As you can see, the printer comes up! 

One other thing: I ran "sudo apt-get autoremove" per [http://candidlook.blogspot.com/2009/07/another-ubuntu-tip-upgrade-virtualbox.html](http://candidlook.blogspot.com/2009/07/another-ubuntu-tip-upgrade-virtualbox.html) when I was uninstalling the OSE version of VB for the PUEL. Would this have affected my computer recognizing the printer USB?

PLEASE HELP!!!

---

### Post by pilisopa on 2010-12-01
Something?? I could really use some help. I just need to get my computer to recognize my printer!

---

### Post by tgm4883 on 2010-12-01
You allowed the USB in virtualbox, but did you tell virtualbox you wanted to associate that device with that guest?

---

### Post by NCLI on 2010-12-01
> **pilisopa said:**
> Something?? I could really use some help. I just need to get my computer to recognize my printer!
1. Please don't bump your thread so quickly. Wait 24 hours between bumps.

2. Are you using the Virtualbox version from the Software Center? If so, USB will not work, since that part is proprietary. You need to install the full version, with the closed source USB implementation included.

Get it [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

---

### Post by pilisopa on 2010-12-01
> **NCLI said:**
> 1. Please don't bump your thread so quickly. Wait 24 hours between bumps.

2. Are you using the Virtualbox version from the Software Center? If so, USB will not work, since that part is proprietary. You need to install the full version, with the closed source USB implementation included.

Get it [here]("http://www.virtualbox.org/wiki/Linux_Downloads").

No, I downloaded it from the site. It is the PUEL version.

tgm, no I didn't. how can I make it associate with that device if it's not recognizing the device?

---

### Post by tgm4883 on 2010-12-01
> **pilisopa said:**
> No, I downloaded it from the site. It is the PUEL version.

tgm, no I didn't. how can I make it associate with that device if it's not recognizing the device?

I guess it matters what you mean by doesn't recognize. If VB isn't recognizing it (like it does in this screenshot) then i'm not sure the issue. But this screenshot is where you would let virtualbox make the device available to the guest OS

---

### Post by pilisopa on 2010-12-01
Thank you for the help. Somehow, the USB device began to be detected. I really don't know why EXACTLY. I just kept plugging in and out and restarting and at some it started being recognized. I honestly couldn't tell you what did it.

Thank you nevertheless.

---

