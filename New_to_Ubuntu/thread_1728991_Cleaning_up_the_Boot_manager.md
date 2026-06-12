---
title: "Cleaning up the Boot manager"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by mward69 on 2011-04-14
Hey folks, I want to clean up the Boot Mngr. since my wife and stepson use my laptop. here what is looks like when I boot up

: /boot/vmlinuz-2.6.35-28-generic    ***This one Boots Ubu
: /boot/initrd.img-2.6.35-28-generic
: /boot/vmlinuz-2.6.35-22-generic
e: /boot/initrd.img-2.6.35-22-generic
 memtest86+ image: /boot/memtest86+.bin
 Windows Vista (loader) on /dev/sda1
 Windows Vista (loader) on /dev/sda2    ******This one boots Vista

What I want is 2 simple options......Ubu, And Vista.......
 Any help? I am still green with Linux, I have tried a few other flavors, but fairly compfy with some commands. :D

---

### Post by oldos2er on 2011-04-14
Assuming you're using grub2, try [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by mward69 on 2011-04-14
That might be a little out of my compfort zone. Any way I could just edit the Grub Config in text editor? 
  Remove the lines at the begin and end commands....I don
t need the recovery boot {I don't think}
remove the mem test
remove the windows loaded hda1

????

---

### Post by Enigmapond on 2011-04-14
Install Ubuntu-Tweak. This is what I use to clear past kernels from GRUB. (However it's good to keep one past version of a kernel just in case.) Ubuntu-Tweak is great for this and there are some great features as well.

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak
```

It will be located in System Tools when installed. The Kernel Purge is located in the Package Cleaner section of the app.

Cheers!

I would be very careful if you do it your way with the GRUB.config. One small mistake, will cause you a world of problems.

---

### Post by Frogs Hair on 2011-04-14
I use the package cleaner in Ubuntu Tweak , it will only list unused kernels when you select clean kernels. [http://ubuntu-tweak.com](http://ubuntu-tweak.com)

---

### Post by kn0w-b1nary on 2011-04-14
+1 to ubuntu tweak...

If you want to, take a look at /etc/grub.d/

---

### Post by mward69 on 2011-04-14
> **Frogs Hair said:**
> I use the package cleaner in Ubuntu Tweak , it will only list unused kernels when you select clean kernels. [http://ubuntu-tweak.com](http://ubuntu-tweak.com)

Got it...that helped!! Thx...now when I reboot I see {can't remember the actual list}
 Ubu generic something {Ubu start}
  Linux generic {recovery}
  Memtest
   Windows loader hda1
   Windows loader hda 2 {loads Vista}

  Again, can I and how would I remove the memtest and the windows loader hda1? And is it possible to rename them to make it simple......
 example
*Linux
*Linux recov
 *Windows Vista

??

---

### Post by mward69 on 2011-04-14
Here is whats listed in /etc/grub.b

00 header
05 debian_theme
10 linux
20 Linux xen
20 memest86+
30 OS prober
40 Custom
41 Custon
read_me

---

### Post by kn0w-b1nary on 2011-04-14
as I said, look in /etc/grub.d/

Go through the files, and if you see "menuentry", it's a name you can change.

To modify hit Alt+2, then type: ```
gksu nautilus
```Then go there, right-click on a file and "Open with gedit"

Hope this helps!

EDIT: do the above with "20 memtest86+" and you can change the name. If you wanted, you could replace the name with a space, then you could still select it, and no one else notice it. :)

---

### Post by Enigmapond on 2011-04-14
> **mward69 said:**
> Got it...that helped!! Thx...now when I reboot I see {can't remember the actual list}
 Ubu generic something {Ubu start}
  Linux generic {recovery}
  Memtest
   Windows loader hda1
   Windows loader hda 2 {loads Vista}

  Again, can I and how would I remove the memtest and the windows loader hda1? And is it possible to rename them to make it simple......
 example
*Linux
*Linux recov
 *Windows Vista

??
 That GRUB-CUSTOMIZER can rename them but I wouldn't remove the memtest and things....you may need those. Also I would, again refrain from editing the GRUB.config unless you know exactly what you are doing...but this is just my opinion.

---

### Post by kn0w-b1nary on 2011-04-14
And i forgot, run this command when you are done.

```
sudo update-grub
```

Oh, and don't remove entries, you may need them. :)

---

