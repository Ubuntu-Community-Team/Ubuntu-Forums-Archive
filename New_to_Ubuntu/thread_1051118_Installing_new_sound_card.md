---
title: "Installing new sound card"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Periswell on 2009-01-26
Hello

I have a Dell Dimentions 3100 and today (as its my birthday :D ) I got some sorround sound speakers. The Dell has a sound card in it already (it is fixed and cannot be removed without a hammer) but it only has one output (I think it is a 2.1 card). Anyway I managed to find a card in my heap of electronics which has more sound outputs. It is a PCI internal one. I plugged it in and loaded Ubuntu but it did not load the sound card and kept on using the old one. I reinstalled Ubuntu but this did not help. The card works as the computer used to have it in once upon a time (3 weeks ago) but I took it out as it was no use to me and it took up some valuable boot time. What I want to know is how do you tell ubuntu to use this new card and not the fixed one. Cheers in advance.

-Joshua

---

### Post by taurus on 2009-01-26
Can you go into the BIOS and turn the old soundcard off?  Or you can blacklist it in /etc/modprobe.d/blacklist.

---

### Post by Periswell on 2009-01-26
ok could you run me through how to do it (im ok with the terminal), bios isn't really my area of expertise.

-joshua

---

### Post by taurus on 2009-01-26
When you first turn on your computer (or reboot), you would see a logo or a message from the BIOS.  Either at the bottom or upper right corner of the screen, it tells you what key to press (F2, F12, or even the Del key) to get into the BIOS.  

But if you don't want to play around with the BIOS, then you can blacklist your old card so the new soundcard is the default one.

Do you know which soundcard (old one) do you have in your machine?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by Periswell on 2009-01-26
ok, i choose the blacklist one. the two audio ones are these:

> 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

03.02.0 Multimedia audio Controller: Esoniq ES1371 [AudioPCI-97] (rev 08 )


i think the one i want to get rid of is the first one. in etc/modprobe.d/blacklist, what do i write?

-joshua

---

### Post by Periswell on 2009-01-26
ok forget that, i went for the bios option and disabled my intergrated audio and now it works. thanks

---

