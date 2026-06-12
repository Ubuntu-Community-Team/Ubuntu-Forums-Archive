---
title: "Wireless drivers and tools in 7.04?"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by ThinkBuntu on 2007-04-30
I use Zenwalk with a Madwifi driver, and wireless reception is poor. I remember using Ubuntu and Linux Mint, when I was usually able to pick up a signal and hop onto an open network, whereas other distros such as MEPIS come preinstalled with the same crummy Madwifi driver.

What driver powers an Atheros card in Ubuntu? Is it simply a Madwifi, but with better implementation? What other software relating to wireless is installed? I'm currently using the 2.6.21 kernel, so I'd like to get these tools and build them from source if at all possible.

---

### Post by ThinkBuntu on 2007-04-30
BUMP. Somebody's gotta know this...

---

### Post by Floppyjoe on 2007-04-30
linux-restricted-modules and madwifi-tools from synaptic package manager?

---

### Post by ThinkBuntu on 2007-04-30
I was hoping someone close to wireless development in Ubuntu would have my answer, but I guess I'll just have to dig deep into the OS myself until I figure it out :^)

A search of "Madwifi" returns no results in a default Ubuntu install, so either they are using Madwifi and just don't include the name in the filesystem (just including the modules such as ath_pci), or they use an alternate setup for wireless. If it's just Madwifi, I'd like to know what they do to make it work better than my installations/incarnations of Madwifi 0.9.3 do with an Atheros AR5212.

---

### Post by Floppyjoe on 2007-04-30
> **ThinkBuntu said:**
> I was hoping someone close to wireless development in Ubuntu would have my answer, but I guess I'll just have to dig deep into the OS myself until I figure it out :^)

A search of "Madwifi" returns no results in a default Ubuntu install, so either they are using Madwifi and just don't include the name in the filesystem (just including the modules such as ath_pci), or they use an alternate setup for wireless. If it's just Madwifi, I'd like to know what they do to make it work better than my installations/incarnations of Madwifi 0.9.3 do with an Atheros AR5212.

If you load Synaptic package manager and search for atheros you will see that Ubuntu has Madwifi in the linux restricted modules. I'm not sure if this works for all atheros cards though. Some you may have to go to the madwifi site and build the driver for as you were suggesting.

---

### Post by ThinkBuntu on 2007-04-30
> **Floppyjoe said:**
> If you load Synaptic package manager and search for atheros you will see that Ubuntu has Madwifi in the linux restricted modules. I'm not sure if this works for all atheros cards though. Some you may have to go to the madwifi site and build the driver for as you were suggesting.
Not my point. Wireless works fine in Ubuntu. It even worked out of the box in 6.10. And I've built Madwifi to work fine in Zenwalk as well. Anyway, don't worry about it. More of a DIY thing anyway.

---

