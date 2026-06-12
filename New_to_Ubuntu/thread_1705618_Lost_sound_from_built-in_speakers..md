---
title: "Lost sound from built-in speakers."
date: 2011-03-12
forum: New to Ubuntu
---

### Post by Alexalad on 2011-03-12
My built-in speakers worked, but they didn't mute when I placed my headphones. So I found a solutions that suggested I add a   line to the /etc/modprobe.d/alsa-base file. I added it, saved, restarted, and now I don't have sound from either my speakers or my headphones. I went back to the file and changed it to the original, which only had 2 lines:
"options snd-hda-intel model=vaio


options snd-hda-intel model=3stack"

I saved, rebooted, and still no sound from either speakers or headphones. Oh, and now, anytime I try to use alsamixer in my terminal, it shows that I have no such file or directory, and I'm almost 100% sure I've installed it. So i'm kinda confused on where to even begin.

---

### Post by pi3.1415926535... on 2011-03-12
Have you tried reinstalling the programs in question?

---

### Post by Alexalad on 2011-03-12
Yes, I have.

---

### Post by Alexalad on 2011-03-12
So I've been looking around for more information on what could have happened, and I saw this on a linux wiki: 
"Warning: Do not use alsaconf if you have a PCI or ISAPNP sound card, as the entries alsaconf adds to the modprobe.conf file might break udev's autodetection."

I'm not sure if this is the type of sound card I have, but I think this is what my problem is. Unfortunately I'm still not sure as to what to do about it. :/

---

### Post by Alexalad on 2011-03-12
I used the command: sudo lshw -c sound
Which displayed:


*-multimedia UNCLAIMED  
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:92300000-92303fff

Anyone know why it's unclaimed or how to fix this?

---

### Post by Alexalad on 2011-03-12
OK. I reinstalled the alsa kernel packages from Synaptic Package Manager, and rebooted. Now I'm back to where I started. I was reinstalling the wrong packages originally.

So I've got sound from my built-in speakers, but my headphones still don't mute the speakers when I plug them in. Could someone direct me to a fix for this?

---

### Post by Alexalad on 2011-03-12
I can now run gnome alsa mixer, and it has "Conexant 5069" with volume sliders, but they change the speakers volume and the headphones volume simultaneously, so I can't mute my speakers. Any suggestions?

---

### Post by Alexalad on 2011-03-12
found a package on the internet that fixed everything after the installation and reboot:

[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

