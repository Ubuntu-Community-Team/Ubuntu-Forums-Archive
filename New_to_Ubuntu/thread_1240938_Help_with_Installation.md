---
title: "Help with Installation"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by misterspiffy on 2009-08-15
Hi all.  I am trying to install ubuntu utilizing a dual boot system with my existing windows vista.  I created the ubuntu OS disc with Toschiba disc creator.  I've prepared my computer by defragmenting and running checkdisk.  I changed the boot order of my devices so it boots to my dvd-rom drive.  The problem I am is having is the boot disc won't load up and I simply get a black screen.  I don't know if the disc got written too fast with the Toshiba utility (It would not let me select a speed).  I have Daemon tools onboard and I'm wondering if I can mount ubuntu iso file virtually through windows and install that way?  Or is there some special way to access the disc when I try to boot to it that I am not aware of.  I know I could try rewriting another disc but I was wondering if anything else might work.

Thanks in advance.

---

### Post by Liolikas on 2009-08-15
> 
I have Daemon tools onboard and I'm wondering if I can mount ubuntu iso file virtually through windows and install that way?

No but you can use specialized for this task program wubi ([http://wubi-installer.org/](http://wubi-installer.org/))
---
Or just try other disk brun on lower speed with other iso burner.

---

### Post by MelDJ on 2009-08-15
you could try installing it with wubi in windows.

---

### Post by misterspiffy on 2009-08-15
Does wubi installer just install ubuntu within windows or can I do a dual boot install with it?

---

### Post by MelDJ on 2009-08-15
it installs ubuntu in windows. when u start the computer, u can choose whether u want to boot into windows/ubuntu

---

### Post by Arand on 2009-08-15
Wubi installs within windows and allows for a semi-dual-boot, i.e. you will still have to choose OS on startup, but ubuntu is contained as a file on the windows partition rather than in it's own partition.

You can not do "pure" dual-boot installs from within windows.

- Arand

---

### Post by misterspiffy on 2009-08-15
Ok, thanks.  I really a true partitioned dual boot so I am going to try burning a new disc at 4x with Daemon Tools Pro.

Is this a common problem?  My computer has been running awfully with Visa and I am assuming it's Vista since it's a pretty new system with good specs.

---

### Post by tesu on 2009-08-15
if you still have trouble with discs and you have a usb drive big enough (1gig i think should work) you can try unetbootin  it will get the live cd to boot off of a flash drive (you will need to set boot in bios to boot from usb before hard drive)

---

### Post by Bartender on 2009-08-15
Boot into Vista, then pop the CD you burned into the optical drive.  Go to the drive, click "Explore" or "Open".
If you see one huge file, you copied the download as data.  That's not what you want.  If you see several folders and a handful of files, then at least we know that you converted the doewnload to an .iso.  That's what you want to see.
ImgBurn is often suggested as an easy to use, free utility for Windows-based PC's.  I think there's another one called IsoBurn.

I don't burn .iso's faster than 8X.  You could probly get away with faster speeds, but if your Toshiba went at full crank the CD could very well be bad.

So, make sure you're burning the download as an .iso, burn it slowly, use good quality media, and don't use a CD-RW.  Those are the most common mistakes.

---

### Post by LewRockwell on 2009-08-15
I burn at my slowest which is 4X

also, I didn't see any comments on how your LiveCD test-drive went?

.

---

