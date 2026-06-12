---
title: "Do Emulators On Ubuntu Still Work?"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by NOLA345 on 2010-11-04
I just installed ubuntu 9.04.

I have found numerous articles and posts and websites detailing how to get NES and SNES emulators, but they are all very old and the actual sites for the emulator downloads go back to 1999-2000.

Is there somewhere I can get new ones that will work for ubuntu and my PS3?

For the record, I tried a few "sudo apt-get" commands using snes9x and zsnes and they did not work. 

Also, I have the NES emulator (FCE Ultra? I think) and it works, but I cannot get it to full screen. Anyway around that?

---

### Post by A_M_S on 2010-11-04
Why did you install Ubuntu 9.04?
Its no longer supported.

Why don't you try the LTS version 10.04?

---

### Post by NOLA345 on 2010-11-04
Does that mean nothing will work for the version I have????

If I got 10, would I still be in the same predicament of having outdated emulators?

---

### Post by A_M_S on 2010-11-04
> **NOLA345 said:**
> Does that mean nothing will work for the version I have????
9.04 is still functional, but canonical will not send more updates
for that version

---

### Post by NOLA345 on 2010-11-04
So it shouldn't matter which one I am using then, for now???

I still have no idea how to get the emulators on here and working.

---

### Post by waynefoutz on 2010-11-04
> **NOLA345 said:**
> Does that mean nothing will work for the version I have????

If I got 10, would I still be in the same predicament of having outdated emulators?

the problem is you are using an out of date Ubuntu version, and the repositories have been shut down, so you can no longer download anything with APT or Synaptic. 

The best thing to do would be install 10.04 or 10.10, but if you really must stick with 9.04, which no one here will recommend, because you'll get no security updates, but here is how.

run this command in the terminal:

```
sudo gedit /etc/apt/sources.list
```


then edit the file that comes up by pretty much deleting everything, and replace it all with this:

```
deb http://old-releases.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
```

save the file, exit then run 

```
sudo apt-get update
```

This should get APT and Synaptic working again, but the software you get from it will mostly be outdated. Again, your best bet would be to install a modern, still supported version.

---

### Post by mcduck on 2010-11-04
both snes9x and zsnes work just fine. Just keep in mind that they are both command-line applications, so you won't find them in your menus.

(There's snes9express if you want a GUI for snes9x, though)

The support for 9.04 has already ended, and it's software repositories are closed. So not only are you stuck with the old versions of programs, you actually can't get any more software than what comes included. That alone is enough reason to move to a release that's still supported.

---

### Post by NOLA345 on 2010-11-04
> The best thing to do would be install 10.04 or 10.10, but if you really  must stick with 9.04, which no one here will recommend, because you'll  get no security updates, but here is how.


I was just trying to avoid having to download a whole nother iso file and install it again, but I don't need to stay on 9.04. Is there somewhere I can go in 9.04 to just get it to update?

> There's snes9express if you want a GUI for snes9x, though
I downloaded this, I think. Not sure if I did it correctly. Remember I am 100% new to Linux, minus about 12 hours of fooling around today and last night after I installed 9.04 on my PS3. The sound is very garbled and the game is very slow.

---

### Post by NOLA345 on 2010-11-04
Either way, I still think I need to figure out how to tackle the full screen issue using GFCE Ultra. Anyone know this? I have checked off the full screen option, but when it goes to full screen, it just adds black space. 

[[IMG]http://img522.imageshack.us/img522/2227/screenoptions.th.jpg[/IMG]](http://img522.imageshack.us/i/screenoptions.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

[[IMG]http://img812.imageshack.us/img812/3531/notfullscreen.th.jpg[/IMG]](http://img812.imageshack.us/i/notfullscreen.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by NOLA345 on 2010-11-04
Finally, how can I use the PS3 wireless controller as my mouse? And after that, set it up for use with the emulators. I found a few links, but not sure which one I should be following:

[http://psubuntu.com/forums/viewtopic.php?f=4&t=5](http://psubuntu.com/forums/viewtopic.php?f=4&t=5)

[http://ubuntuforums.org/archive/index.php/t-23287.html](http://ubuntuforums.org/archive/index.php/t-23287.html)

[http://ubuntuforums.org/showthread.php?t=665130](http://ubuntuforums.org/showthread.php?t=665130)

[http://gizmodo.com/5143547/how+to-install-ubuntu-on-your-ps3-for-vintage-gaming-emulation](http://gizmodo.com/5143547/how+to-install-ubuntu-on-your-ps3-for-vintage-gaming-emulation)

They all have some similarities, but also some things that are different.

---

### Post by waynefoutz on 2010-11-04
It's going to be a huge headache to update, and it probably won't work anyway, since you are 2-3 versions behind the current ones. You'd save a lot of time, and bandwidth, by downloading the iso and starting fresh.

---

### Post by kingofspades8 on 2010-11-04
I don't think anyone mentioned this yet but most of the emulators are easily available and will install automatically through the Ubuntu Software Center.  

I've gotten SNES, NES, and N64 emulators all working just fine, without having to touch a command line.

---

### Post by waynefoutz on 2010-11-04
> **kingofspades8 said:**
> I don't think anyone mentioned this yet but most of the emulators are easily available and will install automatically through the Ubuntu Software Center.  

I've gotten SNES, NES, and N64 emulators all working just fine, without having to touch a command line.

true. But I don't remember if 9.04 even has Ubuntu Software Center, and even if it does,  it won't work because the repositories are gone. I guess I was addressing that issue first.

---

### Post by Paul820 on 2010-11-04
On Ubuntu 10.10 using snes9x, there is a view option on the menu bar to set your different screen sizes (without the big black space). I don't know if there is that option on the version you are using. All the more reason to update your OS if it isn't. ;)

---

### Post by anewguy on 2010-11-04
So, what everyone is saying is this:

(1) Get the 10.04 or 10.10 LiveCD
(2) Boot from the LiveCD
(3) Choose install, but the partitioning depends:

    - if you have another OS and dual-boot, you'll need to delete the old
      ubuntu partitions then create new ones

    - if you used the entire disk for ubuntu, just let the install use the
      entire disk again
(4) After the install, do:

sudo apt-get update

(5) Via "Applications/Ubuntu Software Center, install the emulators you
    want.
(6) Try out the emulator(s).  Try your full-screen to see if it's how
    you want it now.  If not, stop, post back, and let us try to work with you to solve this problem first.
(7) After the emulator(s) are working as you want and the full screen mode is working as you want, post back and we can try to tackle one thing at a time.  If using your PS3 wireless controller as your mouse is the next important thing, then we need to work on that before moving on.

I know you don't want to download another CD, so if you are in the US, and if you are willing to wait a few days, PM me with your address and I'll send you a 10.04 disk (since it's the LTS version).

Dave ;)

---

### Post by NOLA345 on 2010-11-23
Well, I tried installing the newest version (10.4) and ran into more problems than I started with. Here is a screenshot. If you can't read it, I can go ahead and go back to the monitor and type it all in.

[http://img528.imageshack.us/img528/634/104hang.jpg](http://img528.imageshack.us/img528/634/104hang.jpg)

What's my issue here?

---

### Post by NOLA345 on 2010-11-30
Any help? You guys suggested I re-install with the new so I did.

Now I'm left hanging....

---

