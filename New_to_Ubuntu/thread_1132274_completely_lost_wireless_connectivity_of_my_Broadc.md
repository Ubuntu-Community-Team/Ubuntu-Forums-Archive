---
title: "completely lost wireless connectivity of my Broadcom BCM4312 card!"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by scrypt on 2009-04-21
Can somebody help me reconfigure my wireless card to once again have web access?

I have a Dell Studio 1737 with A Broadcom BCM4312 Wireless card.

For reasons unknown, as from earlier on today I cannot connect wirelessly.

I have tried various options with no luck.

I do know that my wireless driver has disapeared and id no longer loading at bootup.

I know this from running this command:- sudo lshw -c network

which gives me this output:-
-laptop:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Can anybody point me in the right direction to rectify this please??

---

### Post by Zummy on 2009-04-21
Well I have a broadcom BCM43xx card too, this is what I followed to get connection, [http://ubuntuforums.org/showpost.php?p=5469730&postcount=13](http://ubuntuforums.org/showpost.php?p=5469730&postcount=13)  
Other than that, my knowledge is very limited, so best of luck to you.

---

### Post by scrypt on 2009-04-21
Thank's Zummy for you reply.

I will look into your link!

---

### Post by Zummy on 2009-04-21
You are welcome! I hope it helps, because I know I like fast working answers too! :D

edit: did you update your device manager (system -> Administration -> Hardware Drivers) did you update the "Broadcom B43 wireless driver?  Last time I updated that, I too, lost connection and had to reformat my linux installment.

---

### Post by stchman on 2009-04-21
I know this might sound stupid, but I have done it as well.

Check to see if your wireless on/off switch(if equipped) was bumped to the off position.  As I said I have done this before.

---

