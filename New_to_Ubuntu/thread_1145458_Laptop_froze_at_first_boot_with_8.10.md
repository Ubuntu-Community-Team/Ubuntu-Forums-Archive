---
title: "Laptop froze at first boot with 8.10"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by pikkiem on 2009-05-01
I have upgraded my HP2133 from 8.04LTS to 8.10. With the first boot the screen froze. As i battle to find my way around with the command line, i don't really know how to update the video card drivers. I have downloaded a xorg.conf file on my flash drive (via my vista pc} and would like to copy it to my ubuntu laptop but i don't even know how to see what is on the flash drive so i can copy it to the /etc directory and restart the laptop with the new xorg.conf file. Can anyone help please?

---

### Post by beastrace91 on 2009-05-01
When you plug in your flash drive it will auto mount. Then when you are in terminal use ```
cd /media
``` this will change to the directory where media is mounted to

And then use ```
ls
``` to display the contents of the drive, typically flash drives are called "disk" or something of the like then you can just use "cd <folder>" to change into the directory the flash drive is mounted to.

~Jeff

---

### Post by beastrace91 on 2009-05-01
Also just as a heads up there is a terminal based text editor called "nano" so you can edit the existing xorg.conf with out having to copy over a new one by doing ```
sudo nano /etc/X11/xorg.conf
```

~Jeff

---

### Post by pikkiem on 2009-05-01
Thank you. I can see the xorg.conf file but there is very little in it. That is why i want to copy the one on the flash drive to the laptop. I have tried with the commands given but media has only two folders in it 'cdrom' and 'cdrom)'. no flash drive under media

---

### Post by beastrace91 on 2009-05-01
Huh it doesn't sound like ur flash drive is mounting. Run ```
lsusb
``` in terminal while the flash drive is plugged and see if it pops up.

Also what driver does your current xorg.conf say its using? If the current ones aren't working typically setting the driver to the default "nv" will at least get you a GUI to work from on most systems.

~Jeff

---

### Post by pikkiem on 2009-05-03
Hi.

The first line after typing lsusb is

"Bus 004 Device 005: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive"

There are more lines but this is what you are looking for?

Also the xorg.conf file starts with the normal explanatory lines that are commented out. The important lines after that is what typed here:

Section "Device"
        Idetifier     "Configured Video Device"
Endsection

Section "Monitor"
        Identifier    "Configured Monitor"
Endsection

Section "Screen"
        Identifier    "Default Screen"
        Monitor       "Configured Monitor"
        Device        "Configure Video Device"
Endsection

And that is the total contents of the xorg.conf file. Obviously i need to alter that, but how?

If you can also assist with the network connection maybe i can copy the file from the internet, but i don't think the network is working.

Thanks for your help.

---

### Post by pikkiem on 2009-05-03
How do  you set the driver to "nv"?

---

### Post by beastrace91 on 2009-05-03
Before we go about setting drivers that might be the wrong one I forgot to ask what type of video card do you have and what drivers did you have installed in 8.04?

~Jeff

---

