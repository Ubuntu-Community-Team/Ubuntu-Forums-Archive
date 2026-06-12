---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Megaptera on 2011-03-13
Ran this  sudo apt-get update && sudo apt-get upgrade
 a couple of times over past week. I click "y" to this

 Setting up linux-image-2.6.32-29-generic (2.6.32-29.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-29-generic

 and got this error message:
E: Sub-process /usr/bin/dpkg returned an error code (1)


Google produces too many hits and "search" here showed nil (unless I used wrong term?)

Any ideas to solve this please?
Thanks in advance

---

### Post by Matt__ on 2011-03-13
try this in a terminal

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

and can you post everything that gets output in the terminal when you try the first command please.

---

### Post by Megaptera on 2011-03-13
Matt_________

Thanks.
first command gives:


--------@Dell:~$ sudo apt-get install -f
[sudo] password for       : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-29-generic (2.6.32-29.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-29-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 18: Syntax error: newline unexpected
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-29-generic; however:
  Package linux-image-2.6.32-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.29.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 linux-image-2.6.32-29-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
  -----@Dell:~$

---

### Post by Megaptera on 2011-03-13
Second command gives:


---------@Dell:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.32-29-generic (2.6.32-29.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-29-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 18: Syntax error: newline unexpected
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-29-generic; however:
  Package linux-image-2.6.32-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.29.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-29-generic
 linux-image-generic
 linux-generic
----------@Dell:~$

---

### Post by Matt__ on 2011-03-13
Have you messed with grub recently? Possibly changed GRUB_GFXMODE?

the first error:
/etc/default/grub: 18: Syntax error: newline unexpected


((This is tough as Im on a win box at the moment..hope Im rembering right))

---

### Post by Megaptera on 2011-03-13
> **Matt__ said:**
> Did you also run ```
sudo dpkg --configure -a
```

Have you messed with grub recently? Possibly changed GRUB_GFXMODE?

the first error:
/etc/default/grub: 18: Syntax error: newline unexpected

Hi and thanks,
I think I posted second result as you were replying.

No I've not touched grub and I wouldn't have a clue how to change GRUB_GFXMODE.

---

### Post by Matt__ on 2011-03-13
ok next.
try 

```
sudo update-grub
```

and see if it will fix it, if no error try update again, if not open up grub in gedit with.

```
gksudo gedit /etc/default/grub
```

and lets see if theres anything wrong with it (post here pls)

---

### Post by Megaptera on 2011-03-13
sudo update-grub gives the following error:
 
/etc/default/grub: 18: Syntax error: newline unexpected

gksudo gedit /etc/default/grub
gives:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1024x768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Matt__ on 2011-03-13
can you comment out the line;

GRUB_GFXMODE=>>1024x768-24<< please (put # before it) and see if grub will update (sudo update-grub) and if it does try sudo apt-get update again

(is there any reason to have your grub screen at your desktop resolution? a background image there perhaps?)

---

### Post by Matt__ on 2011-03-13
your using a proprietory driver gfx workaround to stop the splash screen looking ugly?
((quiet splash nomodeset video==uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap))

---

### Post by Megaptera on 2011-03-13
Yes, I'd forgotten about that image, sorry.

Done sudo update-grub and sudo apt-get update again  and no error messages.
Going to re-boot to see how it all goes.

---

### Post by Megaptera on 2011-03-13
Re-boot gave me the new linux-image but an awful blue screen with lines down it.

---

### Post by Matt__ on 2011-03-13
hmm ok undo the uncomment on that line in grub again.

Im at the limit of my knowledge and dont know how to fix that too lol.

I stick with the B&W 640x480 grub screen :)

---

### Post by Megaptera on 2011-03-13
Thanks for trying to help, I'll see if anyone else can finalise it for me ..
cheers anyway.

---

### Post by Matt__ on 2011-03-13
scroll down to problem 6 regarding "big and ugly plymouth logo"

[http://www.ubuntugeek.com/known-ubuntu-10-04lucid-lynx-issuesbugs-with-workarounds.html](http://www.ubuntugeek.com/known-ubuntu-10-04lucid-lynx-issuesbugs-with-workarounds.html)

good luck Mega.

---

### Post by Megaptera on 2011-03-14
Nope, no luck with that either. Just red grid at bootup and shutdown. 

Thanks for trying to help, very hacked-off now.

---

### Post by Megaptera on 2011-03-14
Went for a reinstall.

---

