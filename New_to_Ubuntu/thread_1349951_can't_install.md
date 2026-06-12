---
title: "can't install"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by gobode on 2009-12-08
can someone plz help!, 
Okay so my intention was to dual boot so I could play games on windows. Originally ubuntu was the only OS but since windows requires for  it to be in the first partition I installed windows and removed ubuntu. I created a partition through windows so i could install ubuntu when i was asked how i wanted to install, i chose side by side but something went wrong; something about ext4. It then took me back and said the computer had NO OS(not sure why this happened). So i decided to continue and install ubuntu on a custom install so it wouldn't be the first, but when i was setting up the partitions my computer lost power, hoping to finish i started again but i couldn't see any partitions or create new, therefore i cant install ubuntu nor windows. I am currently using the live cd, also gparted reads "no devices found". Also i am using ubuntu 9.10 and windows vista, once again plz help and thank you!

---

### Post by Sin@Sin-Sacrifice on 2009-12-08
Whats the output of ```
fdisk -l
```?

---

### Post by gobode on 2009-12-09
nothing. =/

---

### Post by 3rdalbum on 2009-12-09
> **gobode said:**
> nothing. =/

Sin should have told you to type:

```
sudo fdisk -l
```

---

### Post by madmax1735 on 2009-12-09
did u run it with sudo???


```
sudo fdisk -l
```

---

### Post by Sin@Sin-Sacrifice on 2009-12-09
Sorry...

---

### Post by madmax1735 on 2009-12-09
hey, np

so what is the output that the above command gives you??

---

### Post by gobode on 2009-12-09
yeah i used sudo; the output was the same, simply a blink then a new line allowing me to type again.

---

### Post by pdlethbridge on 2009-12-09
were you asked for a pass word?

---

### Post by m4tic on 2009-12-09
its a live session, i wont ask for password, i would suggest this guy use ubuntu 9.04 since the grub loader is easier there so he can mess with in the future

---

### Post by gobode on 2009-12-09
yeah no password, 
Grub 9.04?

---

### Post by gobode on 2009-12-09
yeah no password,
Grub 9.04?

---

### Post by tom.swartz07 on 2009-12-09
Ok- heres what to try. 
If you have your windows OS cd, pop that in and see if you could restore your computer to a state that you could run it without a livecd.

NEXT- reboot your computer and take special note of your BIOS version. when your computer boots, verify from your computer manufacturer's site that you have the newest BIOS. 
I had so much trouble installing Ubuntu on my computer until I upgraded my BIOS (it was 5 versions out of date! :-# )
The BIOS update should be relatively easy, but you NEED Windows to run the update easily, unfortunately. Thankfully, the updates to BIOS's dont happen that often.

NOW you could try to install ubuntu. For the most part you could click through everything no problem, and youll be all set!

---

### Post by gobode on 2009-12-10
okay so i did the first step but it didn't work it could not find any, so i decided to allow windows to fix errors but at 12hrs of scanning for errors i lost patience and restarted my laptop, after messing around in the bios settings i continued with the windows cd and this time i found a drive to where i could install windows but it did not meet window requirements so i popped in the live cd(ubuntu); this time i was at the final step, at 15% i encountered an error. it read; input/output error during read on dev/sda. It then reads; the creation of swap space in partition #5 of SCSl1(0,0,0) (sda) failed.  why is it happening? is it the cd?

---

