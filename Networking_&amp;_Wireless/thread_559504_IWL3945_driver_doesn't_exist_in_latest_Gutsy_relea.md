---
title: "IWL3945 driver doesn't exist in latest Gutsy release (2.6.22-12)"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by R. McC on 2007-09-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144252](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144252) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Up until the release of 2.6.22-12, I have been using the iwl3945 driver for my wireless card with great success.  It has been much more reliable than the ipw3945 driver.  However, with the update to 2.6.22-11, it appears that the iwl3945 driver no longer *exists*; only the drivers for the 4695 wireless card now show up when I searched for "iwl" files in the 2.6.22-12 folders.  Typing sodu modprobe iwl3945 returns a no-such-module error.

Is anyone else running into this problem?  Is this an omission from the latest release for a specific reason, or is it an oversight?  Or is it just me?  Is there a way I can re-compile the driver on my system?

Help. :(

---

### Post by wirelessmonkey on 2007-09-25
I still have the iwl3945 modules... /lib/modules/2.6.22-12-generic/ubuntu/wireless/iwlwifi/iwl4965.ko

Strange.

---

### Post by R. McC on 2007-09-25
> **wirelessmonkey said:**
> I still have the** iwl3945** modules... /lib/modules/2.6.22-12-generic/ubuntu/wireless/iwlwifi**/iwl4965**.ko

Strange.
Note the bolded sections -- I too have the iwl**4965** drivers, but those don't do me any good -- I have the **3945** card, which relies/d on the iwl3945 drivers.

---

### Post by wirelessmonkey on 2007-09-25
Ah ha! My apologies.

---

### Post by R. McC on 2007-09-25
Okay, this is fixed now!  Someone appears to have included it in the latest batch of updates.

The question I now have is...how do I find out which packaged contained the update that it was located in?  Is there a way to do this, or a list of changes on the web somewhere?

Looking for info.  Thanks!

---

### Post by BigBob on 2007-09-26
> **R. McC said:**
> Okay, this is fixed now!  Someone appears to have included it in the latest batch of updates.

The question I now have is...how do I find out which packaged contained the update that it was located in?  Is there a way to do this, or a list of changes on the web somewhere?

Looking for info.  Thanks!

Hi R. McC,

Where did you see 'Someone appears to have included it in the latest batch of updates'.

Any URL where we can see these modifications ?

A++

---

### Post by R. McC on 2007-09-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/144252](https://bugs.launchpad.net/ubuntu/+bug/144252) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				That's kind of what I'm asking, actually.  I saw that it was included because after I updated yesterday, I did a search for the driver to see if it existed, and it did, whereas it hadn't that morning.  

Albert mentioned that it had been included in the bug I logged on the topic (see [here](https://bugs.launchpad.net/ubuntu/+bug/144252))

However, I don't know how to look up such a change myself.  I'm sure there must be somewhere where such changes like this are listed for reference purposes, but I'm too new to the Ubuntu community to know where to look.

Thanks!

---

