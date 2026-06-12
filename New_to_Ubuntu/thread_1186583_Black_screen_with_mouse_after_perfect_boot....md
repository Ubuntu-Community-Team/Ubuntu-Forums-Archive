---
title: "Black screen with mouse after perfect boot..."
date: 2009-06-13
forum: New to Ubuntu
---

### Post by Jannes. on 2009-06-13
yesterday i installed ubuntu 9.04

but after the first reboot of the 9.04 my pc boots normal but my screen turns black and only the mouse is visible...(on the step i normally have to see my desktop) I can do CTRL+ALT+F1 and log in terminal but nothing more...

What did i do wrong???

Ive installed all of these...
- My backupfiles from windows to linux (songs, docs,...)
- Amsn
- Removed Pidgin
- Removed Evolution email
- Mozilla Thunderbird
- And as latest, i would install wolfenstein enemy territory --> followed an old thread of this forum. It said i had to go to administration --> hardware drives, so did i. There stood i had to activate two drivers but after activating the first i had to reboot (it was something with '170 (recommended)' (the best one did i take as first) After the reboot i got this problem of black screen...

Saw on different sites its maybe something with graphics card???:


My pc:
Nvidia geforce fx 5200 128mb
Harddisk 120gig
512ddr
2.8gHz
Intel pentium 4

---

### Post by mochiko on 2009-06-13
hey, i'm having the same problem but with 8.10

how did you find out the information about your driver?

---

### Post by Jannes. on 2009-06-13
I just know the info...

mhm i saw its a prolem with installing the 173 NVidia Geforce driver...

but i dont know how to solve it

plz pro'zz help us

---

### Post by mochiko on 2009-06-13
Ah, dang it then, i dunno what to do. Someone said that my kernel has updated but my driver hasn't, and that I need to fix my X server. I would totally do that if I knew how.

=__=

but thanks for the help anyways.

---

### Post by synapsys on 2009-06-13
At terminal type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Jannes. on 2009-06-13
and then?

---

### Post by synapsys on 2009-06-13
Reboot

Then find the right driver for your graphics card.

---

### Post by Jannes. on 2009-06-13
plz can u say it clear things

i only know i can reboot with pressing my power button

I pressed your code: (this is what i got)

*file; backup in /etc/X11/xorg.conf.20090614022912*

oke i did sudo reboot... still black screen

---

### Post by synapsys on 2009-06-13
When you boot you know how to press CTRL+ALT+F1 to drop to terminal. Do that, then type command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```This will reset your graphics configuration.
Once that is done type:

```
reboot
```That will reboot your system. Then you should be back to where you were before you tried to install hardware driver. Now try to login as normal.

---

### Post by synapsys on 2009-06-13
That's fine, it made a backup of your original file in case you need it. It also should have re-written your xorg.conf file so that you can boot normally.

---

### Post by Jannes. on 2009-06-13
i still got the black screen :(

---

### Post by Jannes. on 2009-06-13
Oke i found how to download packets from nvidia in terminal
[I]sudo apt-get install nvidia-glx
[/I]

Which packet do i have to choose???:

- nvidia-glx-96 96.43.10-0ubuntu1
- nvidia-glx-71 71.86.08-0ubuntu1
- nvidia-glx-180 180.44-0ubuntu1
- nvidia-glx-173 173.14.16-0ubuntu1

my card is nvidia geforce fx5200

---

### Post by synapsys on 2009-06-13
173

[http://packages.ubuntu.com/intrepid-updates/misc/nvidia-glx-173](http://packages.ubuntu.com/intrepid-updates/misc/nvidia-glx-173)

---

### Post by Jannes. on 2009-06-13
how do i install the packet from the given list??

---

### Post by synapsys on 2009-06-13
```
sudo apt-get install nvidia-glx-173
```

---

### Post by Jannes. on 2009-06-13
its already installed..

[I]the following packets are installed automaticly and are no more longer needed: tk8.4
you can delete this trough: apt-get autoremove...[/I]


what now???

i just pressed autoremove blabla and rebooted
still black screen...

I just reinstalled the 173 and rebooted, still the aaaarghhghghghhg black screen

---

### Post by Jannes. on 2009-06-13
damn im still stuck :(

---

### Post by Jannes. on 2009-06-14
is my pc for the cemetery or not :o:o i dont want to... any solutions?

maybe this??? [http://ubuntuforums.org/archive/index.php/t-80314.html](http://ubuntuforums.org/archive/index.php/t-80314.html)

but i dont understand a word of that post

---

### Post by Jannes. on 2009-06-15
Oke what i did was

-> go on the live CD of ubuntu
-> Backup all my files to my external HDD
-> Reinstall ubuntu

And now im on my fresh new ubuntu.

After every update im going to reboot so i can see where the problem is.

U will hear me later with moooree problems...

Thanx for the help and see you later

grtzz

---

### Post by mochiko on 2009-06-16
I tried that as well, both those commands and it's still giving me a blank screen.

---

### Post by Jannes. on 2009-06-17
and top of the bill, i installed the nvidia 173 driver and i can still work on my pc witouth my black screen xD

---

