---
title: "Trying to install Ubuntu 9.04"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by jose187 on 2009-07-22
My new computer has an AMD with ATI.

First annoying thing is that it does not boot from USB, so i had to burn a CD

I booted the computer with the new CD.

I chose to try Ubuntu without changing desktop, just to see if i was going to have any problems....

...I did. Splash screen came up, all is well, but just before it was going to take me to the desktop - the screen turned itself off. Seconds later i hear the Ubuntu welcome sound.

I am pretty sure it has to do with the video card....how can i fix it?

---

### Post by okey666 on 2009-07-22
Just a little more information first...

Do you know the exact model of your graphics card (if you are currently using windows you can use "system information" to find out). Also, does your monitor say "no signal" or similar, or is there just no display?

I was going to suggest starting up without the splash screen so we can see what the problem is but if you hear a login noise then that won't help.

---

### Post by Tyke91 on 2009-07-22
you could try hitting Control+Alt+F1 in order to drop yourself into a terminal (just to see if anything works at all)

---

### Post by jose187 on 2009-07-22
Ok,

I've checked the CD, it's good.
I can get into Windows, but it's all in Japanese, so I don't know how to get to the info i need.

I tried to boot from CD again, and it says "No Signal" as soon as it is about to go to the desktop.

I did the Alt+Ctrl+F1 and it brought the screen back to life..into the terminal

I had an old 8.04 DVD, so i tried that and it worked perfectly well...but i still would like to install 9.04 without having to upgrade from 8.04..

thanks for your help.....any more ideas?

---

### Post by jose187 on 2009-07-22
*BUMP*

Need some help with this ... please help me.

---

### Post by okey666 on 2009-07-22
Can you run:
```
lspci
```
in the terminal, this may help us to work out what your graphics card is. Post the output here in a code or quote tag please.

PS. If theres alot to copy, look for bits that mention ATI, vga, graphics or such like.

---

### Post by jose187 on 2009-07-22
Thanks,

It says
> 
VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

---

### Post by okey666 on 2009-07-22
Ok... This would be easier but you cannot reach the desktop. This may work, but if it doesn't, no harm done because its the live cd. You will need Internet access, and possibly quite a bit of ram, not sure how much though. Give it a go. 

If I am doing something stupid, could a more experienced user point it out?

Boot up into the terminal, and first try
```
sudo startx
```
That probably won't work, as it should happen automatically.

If that doesn't work, we can try using the proprietary drivers for your graphics card. Do:
```

sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
sudo startx
```

If that doesn't work the first time, just run:
```
sudo pico /etc/X11/xorg.conf

```
and scroll down until you read something like this:
> 
Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection

Make sure it says "fglrx". Thats forces ubuntu to use that graphic driver.

If it didn't say "fglrx", change it, save the changes (ctrl o I think), and then try:
```
sudo startx
```

---

