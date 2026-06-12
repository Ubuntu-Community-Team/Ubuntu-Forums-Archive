---
title: "install NVIDIA driver"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by nikhil.stephen on 2010-10-04
hi,
i want to install NVIDIA driver which requires me to close the X  server. I did that using "sudo /etc/init.d/gdm stop ". My screen goes to  the console but a cursor just blinks and after waiting for a long time,  nothing seems to happen? anybody know what i've done wrong??

---

### Post by ddnev45 on 2010-10-04
After shutting down X, I'll get a blinking cursor, and I have to hit the enter key to bring up the login prompt.

---

### Post by TBABill on 2010-10-04
Just curious why you aren't installing the driver via Synaptic?

---

### Post by nikhil.stephen on 2010-10-04
hitting enter doesn't help! the cursor keeps blinking.. finally i give up and restart.

---

### Post by nikhil.stephen on 2010-10-04
how do i do that using synaptic? i have  a "*.run " file!

---

### Post by LowSky on 2010-10-04
If you want the newest, use the PPA version... no exiting of X required
just run these commands from terminal

```
sudo add-apt-repository ppa:nvidia-vdpau/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-current nvvidia-settings
sudo nvidia-xconfig
sudo reboot
```

---

### Post by beew on 2010-10-04
Depends on your card version. The Vpdau PPA(as well as Xswat)seems to only support newer cards. If you use Lucid you can install the Nvidia driver just using "Hardware Drivers" and you don't need to shut down X either. In Maverick beta "Hardware Drivers" (it has a different name) seems to be broken, it didn't even detect the Nvidia card while Lucid detected the card, downloaded and installed the drivers flawlessly.

---

### Post by nikhil.stephen on 2010-10-04
I'm sorry for not mentioning this before! I want to install CUDA driver. Does this mean i follow the same steps?

---

### Post by nikhil.stephen on 2010-10-04
> **beew said:**
>  Lucid detected the card, downloaded and installed the drivers flawlessly.
this did happen. so i think i will have to uninstall the present driver and then install the CUDA driver if im not mistaken!

---

### Post by emoguitarist06 on 2010-10-04
> **nikhil.stephen said:**
> hi,
i want to install NVIDIA driver which requires me to close the X  server. I did that using "sudo /etc/init.d/gdm stop ". My screen goes to  the console but a cursor just blinks and after waiting for a long time,  nothing seems to happen? anybody know what i've done wrong??

Why not try logging into ubuntu cli
I beleive when grub pops up you hit tab to go to options and it'll give you an option to boot into the command line
then you'll have to type your username and password
then just "cd" to the download directory and then "./nvidia.run"

---

### Post by emoguitarist06 on 2010-10-04
real quick if grub is hidden when you turn on your comp
hold the SHIFT key once the bios pops up and grub will show

That is if you're running GRUB2 then hit "e" then ctrl+c

see here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

---

### Post by beew on 2010-10-04
He doesn't need to close down X.

---

### Post by emoguitarist06 on 2010-10-04
> **beew said:**
> He doesn't need to close down X.

From my experience installing an nvidia .run file running the "sudo /etc/init.d/gdm stop" was required to do. However when he does this it's not changing into the Command Line System correctly as it should be allow him to move forward via command line of course

BUT of course if you know a work around please do post

---

### Post by nikhil.stephen on 2010-10-04
used GRUB to log into recovery mode and then command line. installed perfectly.. but nvcc (ompiler driver that compiles CUDA programs) still isnt working.

---

### Post by emoguitarist06 on 2010-10-04
> **nikhil.stephen said:**
> used GRUB to log into recovery mode and then command line. installed perfectly.. but nvcc (ompiler driver that compiles CUDA programs) still isnt working.

YES! +1 for me!
Okay that second part is beyond my expertise :(

Okay who's up next??

---

### Post by Claus7 on 2010-10-04
Hello,

> **nikhil.stephen said:**
> hi,
i want to install NVIDIA driver which requires me to close the X  server. I did that using "sudo /etc/init.d/gdm stop ". My screen goes to  the console but a cursor just blinks and after waiting for a long time,  nothing seems to happen? anybody know what i've done wrong??

nothing, just press: Ctrl+Alt+F1

Regards!

---

### Post by beew on 2010-10-04
> **emoguitarist06 said:**
> From my experience installing an nvidia .run file running the "sudo /etc/init.d/gdm stop" was required to do. However when he does this it's not changing into the Command Line System correctly as it should be allow him to move forward via command line of course

BUT of course if you know a work around please do post

If he has Lucid he only needs to start "Hardware Drivers" and activate the Nvidia card and then reboot.

Maybe in older versions of Ubuntu or if you choose to install the drivers from Nvidia manually you need to go kill X, get into terminal etc. But I have installed Nvidia cards in two different PC (one with a new card supported by a PPA) and another time an old card using hardware drivers. Never had I have to shut down X or do anything with the cli.

---

### Post by nikhil.stephen on 2010-10-04
thnx emoguitarist06!!

---

