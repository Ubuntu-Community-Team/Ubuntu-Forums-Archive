---
title: "no sound"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by 007casper on 2011-05-27
no sound.  I remember there was a way to turn sound on in terminal.  I cant figure it out.  Thanks. 

    *-multimedia UNCLAIMED
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: latency=0 maxlatency=5 mingnt=2
          resources: memory:fe024000-fe027fff

---

### Post by 007casper on 2011-05-27
removed pulseaudio

sudo apt-get autoremove pulseaudio

then typed
alsamixer
cannot open mixer: No such file or directory

reinstall pulseaudio from synaptic.  Now dont even get the speaker icon to add to the top kicker

---

### Post by dcsoldschool53 on 2011-05-28
> **007casper said:**
> removed pulseaudio

sudo apt-get autoremove pulseaudio

then typed
alsamixer
cannot open mixer: No such file or directory

reinstall pulseaudio from synaptic.  Now dont even get the speaker icon to add to the top kicker

Did you check to see if alsamixer was installed on your system after you removed pulseaudio in Synaptic package manager? I think it is alsa-utils or something like that in Synaptic.I think it is the program for alsamixer

---

### Post by 007casper on 2011-05-28
thanks for your help.  I reinstalled the whole system. This time it worked.  Somehow it didnt pick up the hardware before.

---

