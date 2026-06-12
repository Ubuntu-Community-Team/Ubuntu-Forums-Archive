---
title: "Wireless stopped working"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by chrisjoha on 2008-09-19
My wireless has been working perfectly for six months, but last night it just stopped working. If I click the network manager, the only options are "Wired Network" and "Manual configuration". If I right click, I'm able to see the old list of wireless networks, but I cannot do anything with them except change passoword and so on (ie no "connect" button).

I did a ```
sudo update && sudo upgrade
``` last night, shortly before it stopped working. I suspected this was the trouble, and immediately booted into an older kernel, tried recovery mode and so on. No luck.

I tried the help today and this is as far as I got:

```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
$ lspci -nn
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)
```

```
$ lshw -C network
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl3945 latency=0 module=iwl3945
```

Looks ok, but I don't really know what to check :)

Now I don't really know what more to try. Is there someway I can just reinstall the default network configuration? It worked for me before...

---

### Post by chrisjoha on 2008-09-20
Sorry to bump my own thread... Does anyone have any ideas? Anything else I can provide to make it easier? I tried another update, but no help.

---

### Post by chrisjoha on 2008-09-23
Noone has every seen anything like this? The wireless is working with other computers in the house. Still, wireless is unusable on my laptop.

Is there any way I can undo the whole update/upgrade to see if that'll fix things?

---

### Post by pastalavista on 2008-09-23
Does your laptop have a manual switch to enable/disable the wireless card? I thought I had a problem for a while with my wireless and it turned out that the switch was turned off. I felt totally ignorant when I noticed it. But live and learn. Also, you might check System>Administration>Hardware Drivers and make sure the drivers are still enabled.

---

### Post by chrisjoha on 2008-09-23
Hmm, there is some kind of button with an icon of a lock underneath the laptop, but switching it seems to do nothing. Maybe it beeds to boot? Is there a way to check (through shell or the like) if the hardware is enabled.

In my drivers window I only see the Nvidia driver. It says "prorietary drivers", and I don't think the network card was ever on that list?

---

### Post by chrisjoha on 2008-09-23
Haha, I'm such a retard. I found another button that I never saw before, and sure enough, now I'm wirelessly online again. I think maybe my daughter made the switch...

---

