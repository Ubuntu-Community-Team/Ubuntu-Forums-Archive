---
title: "error: no suitable mode found"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by nolanbostich on 2010-06-03
Fresh install of Lucid.

I get the following message during boot:

```

error: no suitable mode found
error: unknown command 'terminal'

```

Computer hangs for about 45 seconds and then continues to boot normally.

I gather from reading that this has to do with the video mode being improperly set in grub, but all of the solutions require booting a live cd (which I cannot do).  Any suggestions?

---

### Post by cariboo on 2010-06-04
Can your system boot from USB?

---

### Post by sidzen on 2010-06-04
[https://help.ubuntu.com/community/ConsoleFramebuffer](https://help.ubuntu.com/community/ConsoleFramebuffer)

---

### Post by nolanbostich on 2010-06-04
> **cariboo907 said:**
> Can your system boot from USB?

No.  It's an older computer and the BIOS doesn't support booting from USB.  I can use a live disk from a smaller distro like puppy, but I'm not sure if I can do what needs done (and really don't understand what I need to do) without using an ubuntu disk.

---

### Post by nolanbostich on 2010-06-04
> **sidzen said:**
> [https://help.ubuntu.com/community/ConsoleFramebuffer](https://help.ubuntu.com/community/ConsoleFramebuffer)

Is that up to date?  Those instructions involve editing /boot/grub/menu.lst.  I'm using Grub2.

---

### Post by plucky on 2010-06-04
> **nolanbostich said:**
> Is that up to date?  Those instructions involve editing /boot/grub/menu.lst.  I'm using Grub2.

See [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2) for Grub2 Basics.

You need to edit the /etc/default/grub and change the GRUB_GFXMODE=640x480 to a suitable value for your PC and remove the # from the beginning of the line.Then run sudo update-grub to create a new grub.cfg.

Good Luck

---

### Post by nolanbostich on 2010-06-05
> **plucky said:**
> See [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2) for Grub2 Basics.

You need to edit the /etc/default/grub and change the GRUB_GFXMODE=640x480 to a suitable value for your PC and remove the # from the beginning of the line.Then run sudo update-grub to create a new grub.cfg.

Good Luck

Unfortunately, that didn't do it.  Thanks, though.  The Grub2 link was especially useful.  

I've been working at it for the last couple of hours, and no matter what I do, the errors remain.  Passing different boot options (disabling ACPI, xforcevesa, modesets), using the mainline kernel, altering GRUB_GFXMODE -- everything leaves me with the same error.

The only thing left that I know to do is to move to an older kernel or live with the error and just be glad that it eventually boots.

---

### Post by Dwigatjel on 2010-06-06
Hi all because I'am new on this forum.
I'm quite new user of ubuntu.
Yesterday I installed on old computer (pentium III 800Hz 192MB of RAM) Ubuntu 10.04 Server for my small home file server. Also I want to run one app under wine so i need GUI 
I Think fluxbox is the best here. So I install xorg and fluxbox and then I thinked konqueror may be usefull so I install it. Today I turned on the computer and display shows grub bug (I think )
> 
error: no suitable mode found
error: unknown command 'terminal' 			 		

How to fix it?:?:
Please don't tell me that I must reinstall the system (again...):(

---

### Post by K7AAY on 2010-06-29
> **Dwigatjel said:**
> Hi all because I'am new on this forum.
I'm quite new user of ubuntu.
Yesterday I installed on old computer (pentium III 800Hz 192MB of RAM) Ubuntu 10.04 Server for my small home file server. Also I want to run one app under wine so i need GUI 
I Think fluxbox is the best here. So I install xorg and fluxbox and then I thinked konqueror may be usefull so I install it. Today I turned on the computer and display shows grub bug (I think )

How to fix it?:?:
Please don't tell me that I must reinstall the system (again...):(

[http://wwww.ubuntuforums.org/showthread.php?t=1471399](http://wwww.ubuntuforums.org/showthread.php?t=1471399) may be helpful. Worked for me.

---

### Post by Turpin on 2010-07-29
I get this too, in Maverick alpha.  The same error messages on boot.
error file not found
no suitable mode found
and the complaint about missing terminal.
My situation may offer someone out there a clue.
My system didn't start doing this (as far as I know) until after I used squashfs-tools to compress my /usr folder for speed and space-saving.
Here's my run-through.  I don't recommend newcomers attempt this.
sudo apt-get install squashfs-tools
Don't install aufs-tools (or backup your partition or something first) because it breaks the system on karmic, or it used to (I haven't tried installing aufs-tools in maverick).
sudo mkdir /squashed
sudo mkdir /squashed/usr
sudo mkdir /squashed/usr/ro
sudo mkdir /squashed/usr/rw
 compress the /usr folder with
sudo mksquashfs /usr /squashed/usr/usr.sfs -b 65536
Add the following 2 lines to /etc/fstab, probably after the line that defines "/":
/squashed/usr/usr.sfs /squashed/usr/ro squashfs loop,ro 0 0
usr /usr aufs udba=reval,br:/squashed/usr/rw:/squashed/usr/ro 0 0
Reboot to a Puppy Linux liveusb, but you can use most any live cd or usb that you're able to boot with. Mount the hard drive, renamed /usr to /usr-old and created an empty folder named /usr. Then reboot and pray to whatever god you believe in, or Chuck Norris. He believes in you, and he'll kick....  Delete the /usr.old folder to free that space.
Typically, this little procedure will get you're usr folder down to about half size, more or less, with actually a performance increase over uncompressed usually. Maintenance on this is a recompression of the /usr folder, following basically the steps above except make the destination to /squashed-new then booting into your live usb or cd to rename the old /squashed folder to squashed-old and the new one to /squashed, then delete the old one once you know the new one is working.  I recommend the use of something like Clonezilla to make a partition backup first if you have enough storage to write the backup to, before doing something advanced like the above.

Everything else seems to be fine.  I just never used to see those error messages before and now I do.

---

### Post by kris_a on 2010-08-11
Hello,

I just had this problem with an old pc with Intel 815 graphics.

I tried all the above suggestions but they didn't work for me, I managed to get around it by editing my grub config to switch off the graphical boot and go back to text.  Log in and open a terminal then run the following:

```
sudo gedit /etc/default/grub
```

This will open the grub config for editing.  Uncomment (delete the # from) the line shown below:

```
#GRUB_TERMINAL=console
```

should become:

```
GRUB_TERMINAL=console
```

I also changed it so the menu always shows, but that is personal preference:

```
GRUB_HIDDEN_TIMEOUT=0
```

changed to:

```
#GRUB_HIDDEN_TIMEOUT=0
```

After this save the file and close gedit then run the following in the terminal:

```
sudo update-grub
```

Worked for me so long as you don't want fancy graphics while the PC loads... :D

If you want to change it back just redo the changes and run the update-grub command again.

Kris.

---

### Post by Noisehag on 2010-08-19
Thank you so much Kris!  I only did the GRUB_TERMINAL=console part and the error messages are gone.  Nice work! :D

---

### Post by Moorbilt on 2010-09-23
.

---

### Post by dwilson0767 on 2010-11-15
this worked to perfection to me. thanks for posting.

---

### Post by retmotor on 2011-02-27
Kris, helpful post -- thanks.

---

