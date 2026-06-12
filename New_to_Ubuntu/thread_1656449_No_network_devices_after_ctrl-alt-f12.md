---
title: "No network devices after ctrl-alt-f12"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by lbarnes on 2010-12-30
I hit ctrl alt f12, screen went black and I powered down my hp hdx 16 laptop by holding the power button down.  Now Ubuntu shows no network devices available and I have no internet wired or wireless even when booted into the live cd.  Ubuntu  10.10 64bit.  Thx.

---

### Post by lbarnes on 2010-12-30
I put lshw in terminal and got:

*-network DISABLED
        description:  Ethernet interface
        physical id:  1
        logical name:  vboxnet0
        serial:  0a:00:27:00:00:00
        capabilities:  Ethernet physical
        configuration:  broadcast=yes multicast=yes

Sounds like this may be the issue, how would I go about enabling this?

---

### Post by nebileix on 2010-12-30
> **lbarnes said:**
> I put lshw in terminal and got:

*-network DISABLED
        description:  Ethernet interface
        physical id:  1
        logical name:  vboxnet0
        serial:  0a:00:27:00:00:00
        capabilities:  Ethernet physical
        configuration:  broadcast=yes multicast=yes

Sounds like this may be the issue, how would I go about enabling this?

Can u do ```
$sudo lshw -C 'network'
``` instead. The listed above is virtualbox interface.

---

### Post by lbarnes on 2010-12-30
It's exactly the same.  I was running pclinuxos in vbox when I was trying to hit shift alt f12 to toggle desktop effects when it happened.

---

### Post by nebileix on 2010-12-30
Then u might have to go thru dmesg. ur network interface was not recognise. Try providing as much info as possible on networt interface type, model.

---

### Post by lbarnes on 2010-12-30
From hp x16-1160us:

Integrated 10/100/1000 Gigabit Ethernet LAN
Wireless Connectivity	Intel WiFi Link 5100AGN

---

### Post by lbarnes on 2010-12-30
It's working now after booting into the live cd a second time.  When I restarted from the live cd I noticed the restart screen had a lovely resolution and looked really nice compared to my pixelated boot screen currently seen in my Ubuntu 10.10 install.  How can I get the same resolution on my install?

---

### Post by nebileix on 2010-12-31
What are you refering as boot screen? The screen where u see the dots?

So can we say that your network interface issue is solve?

---

### Post by lbarnes on 2010-12-31
The dots as well as the power down screen or whatever you call that.  Network devices are available, I have a feeling it was simply from powering down the laptop with the button, weird that it took so many restarts and two live cd boots to get it back tho.

---

### Post by nebileix on 2010-12-31
hrm... will be great if you could provide screenshots of the difference... Cuz I really dun understand.. :/

---

### Post by lbarnes on 2010-12-31
> **nebileix said:**
> hrm... will be great if you could provide screenshots of the difference... Cuz I really dun understand.. :/
Purple backgrounds, it's no big deal really, I tried a tutorial but didn't work.  Wireless was my main concern.  Thx for the help tho.

---

### Post by nebileix on 2010-12-31
ahh... try this

[http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/]("http://www.omgubuntu.co.uk/2010/11/plymouth-manager-lets-you-change-boot-theme-resolution-in-ubuntu/")

---

