---
title: "How do i get my graphics card to work??"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by allmightymoo on 2010-01-03
Ok so i have activated my ATI Radeon 3200 graphics card in ubuntu (9.1 AMD X64) and it says it is being used but it hasnt done anything...i activated it but it isnt working...do i have to install something? i feel like i'm just missing some easy step...hopefully. (btw ubuntu calls it an 'ATI/AMD proprietary FGLRX graphics driver' thats what it says in the hardware drivers section anyway) In case its significant i'm  dual booting ubuntu and win7.

Thanks in advance.

---

### Post by emeraldgirl08 on 2010-01-03
try putting

```
glxgears
```

in terminal.

---

### Post by allmightymoo on 2010-01-03
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
1780 frames in 5.1 seconds
1740 frames in 5.1 seconds
1720 frames in 5.0 seconds
1740 frames in 5.0 seconds
1760 frames in 5.0 seconds
1760 frames in 5.1 seconds
1760 frames in 5.1 seconds
1760 frames in 5.1 seconds
1680 frames in 5.0 seconds
1740 frames in 5.0 seconds
1740 frames in 5.0 seconds
1740 frames in 5.0 seconds
1740 frames in 5.0 seconds
1740 frames in 5.1 seconds
1740 frames in 5.0 seconds
1720 frames in 5.0 seconds
1740 frames in 5.0 seconds
1740 frames in 5.0 seconds
1713 frames in 5.0 seconds
1725 frames in 5.0 seconds
1720 frames in 5.0 seconds
1555 frames in 5.1 seconds
1886 frames in 5.0 seconds
2020 frames in 5.1 seconds
2220 frames in 5.0 seconds
2280 frames in 5.0 seconds
2120 frames in 5.0 seconds
2260 frames in 5.0 seconds
1959 frames in 5.0 seconds
2261 frames in 5.0 seconds
2260 frames in 5.0 seconds
2200 frames in 5.0 seconds
1820 frames in 5.0 seconds
1620 frames in 5.0 seconds

Should i let it keep going???
What is it supposed to do??

---

### Post by staf0048 on 2010-01-03
What version of Ubuntu are you running?

To see if you get any "special effects" from your card, right click on the desktop, click "change desktop background", then go to the visual effects tab, choose "Normal" or "Extra."  It will attempt to enable desktop effects and will let you know if it's successful.

To customize the effect settings further go to Synaptic and install the Compiz settings manager.

---

### Post by emeraldgirl08 on 2010-01-03
If your graphics card wasn't working your comp would have a hard time rendering the moving gears. Are those framerates (the numbers it's spouting out) in a small window? Try maximizing it and give us some numbers.

---

### Post by allmightymoo on 2010-01-03
Yeah I've tried that too it just says 'Desktop effects could not be enabled' and i'm running ubuntu 9.1 (its the AMD X64 version)

---

### Post by emeraldgirl08 on 2010-01-03
Try looking at this link:

[[COLOR="Blue"]Hardware Support Video Cards[/COLOR]]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards")

---

### Post by allmightymoo on 2010-01-03
And no there isnt any other window the frame rate numbers i posted above were in the terminal and then there is the window with the gears in it...thats all i see

---

### Post by staf0048 on 2010-01-03
Ok, so it's not working then.

If I were you I'd try installing envyng (the qt version I believe) and see if it recommends a driver.  If all you see are red X's in envy, do not proceed.  

Other than that, I've had trouble getting my ATI card to work properly with the proprietary ATI driver on 9.10, but the open source driver pre-loaded with 9.10 seems to work fine on my machine - not the best, but good enough for what I need.

---

### Post by adam814 on 2010-01-03
I have a Mobility Radeon 3470 myself and I couldn't get anywhere with the included fglrx in Ubuntu (X wouldn't even start).  In fact the last version of fglrx I was ever able to use with Ubuntu was 9.4 with Jaunty.  I now use the open-source driver (radeon).  I use the xorg-edgers PPA and the 2.6.32.2 kernel from kernel.ubuntu.com without any major glitches in Karmic.

I have decent 2D acceleration, video playback, and Compiz (although I have to disable the checks compiz does).  No 3D acceleration yet (not that it's that great for gaming under Vista either).

---

### Post by allmightymoo on 2010-01-03
Yeah that page tells me to update my entire system in order for the 'hardware drivers' window thing to show my ati driver...i did this and it worked so i activated it and it was done successfully but it doesn't seem to be working...

---

### Post by allmightymoo on 2010-01-03
ok so i got envyng but when i click on it nothing happens....

---

### Post by staf0048 on 2010-01-03
Try typing "envyng -k" in the terminal and see if it pops up.

---

### Post by staf0048 on 2010-01-03
I feel I should tell you this now, just in case you do install something with envy...

If it does not work, you may be stuck at a terminal prompt or otherwise non-graphical system.  To uninstall the driver installed by envy, do:  Ctrl-Alt-F1 and log in.  Then type:  "envyng -t", this will bring up a textual interface for envy in which it will give you options to uninstall the driver it just installed.  Let it do its thing, then reboot.  You should have your graphical system back.

---

### Post by allmightymoo on 2010-01-03
ok jk i installed the wrong one...got it now. It has checks next to the ATI stuff and X's on the nvidia stuff...i have ati so i should hit 'apply'?

---

### Post by staf0048 on 2010-01-03
If its in the "recommended" section, then you *should* be ok.  Just remember my instructions on how to uninstall just in case something goes wrong.  

Post back to let us know if it works.

---

### Post by allmightymoo on 2010-01-03
It worked great! Thanks! One little thing...it changed the boot loader menu thing...like when i restart there used to just be 2 main options Win 7  and Ubuntu generic and Ubuntu recovery now there's 2 ubuntu generics and recoveries. (Did i make sense?)

---

### Post by adam814 on 2010-01-03
There was most likely a kernel update (explaining the two entries, one being the old kernel and another the new).  Ubuntu won't "autoremove" the old one in case you might have trouble with the new one.  If you don't and it bothers you to have both entries you can remove the old kernel yourself.

---

### Post by allmightymoo on 2010-01-03
hmm ok how do you remove the old kernel? (btw thanks for all the help!!)

---

### Post by sandyd on 2010-01-03
Nvm

---

### Post by adam814 on 2010-01-03
Do this:
```
dpkg --list | grep linux-image
```
That should show you which kernels you have installed.  Assuming your old one was linux-image-2.6.31-15-generic you'd do this:
```
sudo apt-get remove linux-image-2.6.31-15-generic linux-headers-2.6.31-15-generic
```

---

### Post by staf0048 on 2010-01-03
> **allmightymoo said:**
> hmm ok how do you remove the old kernel? (btw thanks for all the help!!)

I'm glad your graphics card is now working properly.  As for your multiple kernel issue, you can try this, but I'm not sure how well it works with Grub2...so bear with me.

Go to synaptic and install "startup-manager", when done open it under System > Administration > StartUp-Manager.  Go to the "advanced" tab and make sure the "limit the number of kernels in the boot menu" option is selected.  In your "number of kernels to keep" box, reduce it to 1.  Then close, allow it to do it's thing (takes about 1-2 min.)  Then restart and see if the extra kernel was actually removed.

2 things to note however:  

1 - as noted above I'm not sure how well this program works with Grub2 (and I'm not that familiar myself) so you may not have the tab or the exact options I mentioned.

2 - it might not be a bad idea to keep the other kernel around as a failsafe.  You see, if you plan on doing some tinkering on your new Linux box, it is quite possible you'll break it - to the point where you have no idea how to fix it.  If you keep the other kernel around, you'll at least have a failsafe working kernel that you can boot into.  It's not a whole different OS per se, just the kernel which is relatively small.  So if I were you, I'd keep it, at least for now, just in case...

---

### Post by allmightymoo on 2010-01-03
Thanks i just removed the image file from synaptic and it doesnt come up anymore...thanks for all your help

---

### Post by kronictokr on 2010-01-06
you can give this a try

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

[COLOR="black"][COLOR="Green"]**Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic**[/COLOR][/COLOR]


We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  

leave the nautilus window open while you do the next step

download the 64bit driver from this link
VVVVVVVV
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

now copy the downloaded file, or drag it into the file you created , (/usr/share/ati  <location reminder )still open in your nautilus window.

when you have placed the "ati-driver-installer-9-12-x86.x86_64.run" file into /usr/share/ati , close your nautilus window, and type the next command into a terminal.

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

this will take a couple minutes as it gathers the proper pakages for your ati gpu. it will create debs and a change log , that will install with the following method

sudo dpkg -i *

there will be missing dependancies, go to SYSTEM>>>SYNAPTICS , and select edit top left , scroll down to and click on fix broken pakages. the click on apply, and lastly click on reload.

now go back to your terminal (to ensure ALL neded pakages are installed, and correctly follow this process exactly)
so, like i was saying, in your terminal, enter the following commands

sudo dpkg -i *

sudo aticonfig --initial

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic


sudo dpkg -i *

sudo aticonfig --initial

sudo reboot

MAKE SURE TO COMPLETE ALL THE STEPS BEFORE YOU REBOOT!!

AFTER YOU REBOOT
vvvvvv
to confirm , in a terminal type

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9232

if you get errors, 
do this again, but i suggest you get it right the first time

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

sudo dpkg -i *

sudo aticonfig --initial

sudo reboot



references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf)

---

