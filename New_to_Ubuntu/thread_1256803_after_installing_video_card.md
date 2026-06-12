---
title: "after installing video card"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by 2roombas on 2009-09-03
i am running 9.04 on an old Dell Dimension 2350 desktop.  Everything was working fine until I tried to update the video driver because I wanted the cool visual effects that I get here on my laptop.  I used these directions...
[URL="http://www.ubuntugeek.com/how-to-install-ati-video-card-in-you-linux-system.html"]
http://www.ubuntugeek.com/how-to-install-ati-video-card-in-you-linux-system.html[/URL]

Obviously something went wrong, bc after the reboot , the screen went  black with a large black & white bar across it.  That thick bar has red lines through. 

What did I do... and is it fixable?:(   All I want to do is uninstall that driver and restore my system to how it was.

---

### Post by 3rdalbum on 2009-09-03
Did you check that your graphics card is supported by the latest ATI driver? A lot of older cards are not supported anymore (well, at least, not supported by ATI) and can only be used with the default open-source drivers.

You can find out in the ATI release notes.

---

### Post by automaton26 on 2009-09-03
You can break into the boot process and choose the "Recovery mode" option. Then it shows another menu and you can go straight to the (last?) "admin prompt" option.

If you installed in the way mentioned here, you can then call the uninstall in the same way too:

[INDENT][http://ubuntuforums.org/showthread.php?t=1205418#7]("http://ubuntuforums.org/showthread.php?t=1205418#7")[/INDENT]

---

### Post by 2roombas on 2009-09-03
> **automaton26 said:**
> You can break into the boot process and choose the "Recovery mode" option. Then it shows another menu and you can go straight to the (last?) "admin prompt" option.


I am at that menu and my options are...

resume   resume normal boot
clean   Try to free space
dpkg   Repair broken packages
fsck   File system check
grub   Update boot loader
netroot   Drop to root dhell promp with networking
root   Drop to root shell prompt
xfix  Try to auto repair graphics problem

Which one do I choose?  Again, I just want to remove that driver and go back to normal. Thank you for your help with this.

---

### Post by 2roombas on 2009-09-03
btw.. I already tried the dpkg one and that did not seem to help, same bars.  

All of these hard-crashes that I'm making while trying to fix this problem certainly can't be good. :(

---

### Post by LewRockwell on 2009-09-03
```
xfix Try to auto repair graphics problem
```

.

---

### Post by LewRockwell on 2009-09-03
> **2roombas said:**
> btw.. I already tried the dpkg one and that did not seem to help, same bars.  

All of these hard-crashes that I'm making while trying to fix this problem certainly can't be good. :(

somehow we're guessing those cool effects don't seem so kewl now...

.

---

### Post by 2roombas on 2009-09-03
> **LewRockwell said:**
> ```
xfix Try to auto repair graphics problem
```
.

Nope. that only made the red lines become tiny red dots. Same black screen with a few black and white bars across it after the ubuntu splash.

---

### Post by LewRockwell on 2009-09-03
see if this gives you any ideas or help:

[http://art.ubuntuforums.org/showthread.php?p=7791287](http://art.ubuntuforums.org/showthread.php?p=7791287)

.

---

### Post by 2roombas on 2009-09-03
> **LewRockwell said:**
> somehow we're guessing those cool effects don't seem so kewl now...

.
EXACTLY!:)  I can easily live without them on my desktop, I just want my normal screen back now.  

I sure wish ubuntu had a "restore" feature like windoze has. That was sure convenient when errors were made, but no way am I ever going back to that os.

---

### Post by LewRockwell on 2009-09-03
> **2roombas said:**
> EXACTLY!:)  I can easily live without them on my desktop, I just want my normal screen back now.  

I sure wish ubuntu had a "restore" feature like windoze has. That was sure convenient when errors were made, but no way am I ever going back to that os.

hey, it's all a learning experience...

you'll be smarter tomorrow than you are today if you keep challenging yourself!

we were all in your shoes at some point...

.

---

### Post by 2roombas on 2009-09-03
I can't even clean install, it just boots right into that screen. :(

---

### Post by 2roombas on 2009-09-03
Solved!   Well,I first tried to do clean install with my flash drive. When that went straight to that screen I  realized the boot sequence on this desktop was probably set to boot the hard drive before a usb device, so I simply used the live cd I had instead. And that did the trick!   Whew, yes, it was a learning experience!:D

---

### Post by remymarathe on 2009-09-03
You might not've needed to  reinstall  anything.    I had similar crashes last night, though I can't confirm which of several ati driver installation methods I tried caused it.

Auto-cleanup of graphics card issues didn't work for me, maybe xorg.conf is actually deprecated with gnome now so clearing it out does nothing?  Does anyone know?

I think the Recovery Menu item from above that you wanted was:

         "root-   Drop to root shell prompt"

Which brings you to a text-only console (so no crash).  Log in as root, and:

1) Navigate to where the fglrx uninstall script was
```
cd /usr/share/ati/
```2) run
```
./fglrx-uninstall.sh
```Followed by
```
apt-get remove --purge fglrx*
```

Worked for me anyway.

P.S. I did the exact same thing as you, as far as panicking on reboot when it wouldn't boot from the liveCD, only to realize that my boot order had just been changed around. At first I feared I'd actually fried something :)

---

