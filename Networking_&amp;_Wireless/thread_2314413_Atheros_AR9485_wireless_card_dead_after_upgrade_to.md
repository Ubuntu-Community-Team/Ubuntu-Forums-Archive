---
title: "Atheros AR9485 wireless card dead? after upgrade to 14.04 on Dell Inspiron"
date: 2016-02-20
forum: Networking &amp; Wireless
---

### Post by Estea on 2016-02-20
I've searched and tried many things (all day!), but have had no success.  Dell N5050 laptop, finally updated to 14.04, now no internet via ethernet cable or wireless. "No network devices available" :( 

sudo lshw -C network


> *-network UNCLAIMED     
       description: Ethernetcontroller 
       product: RTL8101/2/6E PCIExpress Fast/Gigabit Ethernet controller 
       vendor: Realtek SemiconductorCo., Ltd. 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       version: 05 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpressmsix vpd bus_master cap_list 
       configuration: latency=0 
       resources: ioport:e000(size=256)memory:f1104000-f1104fff memory:f1100000-f1103fff 
  *-network UNCLAIMED 
       description: Network controller 
       product: AR9485 Wireless NetworkAdapter 
       vendor: Qualcomm Atheros 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpressbus_master cap_list 
       configuration: latency=0 
       resources:memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff 


rfkill list


> no results






iwconfig


> lo        no wireless extensions.



Thanks for any and all help. Talk to me  as though I am a complete idiot - well, I can figure out some simple fixes, but the last time this happened (with 12.04 update!) I happened to live near an Ubuntu expert who graciously helped me out in my time of need, and I obliviously did not pay attention to the details of the fix...

Estea B.

---

### Post by Estea on 2016-02-22
Ok.  Is it possible to go back to 12.04?  I'd even appreciate a link to correct thread.  I am completely lost at the overwhelming amount of info on this forum.  Appreciate any crumbs!

---

### Post by jeremy31 on 2016-02-22
What happens with ```
sudo modprobe ath9k
```

---

### Post by Estea on 2016-02-22
modprobe:  FATAL:  Module ath9k not found

---

### Post by Estea on 2016-02-22
Should add that I have wifi on another computer nearby and can transfer files via thumb etc.

---

### Post by Estea on 2016-02-22
FYI I have attempted to run the diagnostic wireless script via thumb drive and no dice - when dialog box asks to Run, I click and  terminal will flash open then close itself down very quickly. If there is something I could do to remedy this I would be happy to try it and run the DX script. Thanks!

---

### Post by jeremy31 on 2016-02-22
Download a new image- ISO of Ubuntu and then see if it works

---

### Post by Estea on 2016-02-22
Should I just do 12.04 again or stick with 14?

---

### Post by Estea on 2016-02-22
Doing fresh install of 14 via usb stick and it is going well so far - thanks so much for pointing me in the right direction - fresh install is a pain but really the only way to go with my old machine. You may delete this thread if necessary!

Estea

---

### Post by jeremy31 on 2016-02-22
There must have been an issue with the upgrade that ended up with a kernel that didn't have some modules.  The ```
sudo modprobe ath9k
``` should not have resulted in ```
[COLOR=#000000]modprobe: FATAL: Module ath9k not found
```[/COLOR]

---

