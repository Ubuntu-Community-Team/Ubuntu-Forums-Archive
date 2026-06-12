---
title: "&quot;Checking File Systems&quot; on start-up - how do I remove this?"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-14
Every time I start my laptop I get (after the ubuntu splash status bar start-up) a text list that starts by telling me that it is checking file systems with lots of text with <OK> after each sentance.

I have installed start-up manager but I still do not find any settings to stop this happening each time I boot, any ideas?

---

### Post by Paqman on 2009-02-14
It should really be doing this on every startup. You can tell it how often you want it to check using the terminal command:
```
tune2fs -c 30 -C 1 /dev/yourdevice
```

Just change the 30 to how often to want to check.

However, it's a bit of a worry that it thinks it needs to be checked. You might want to look into the command fsck and run a good thorough scan of your drive to check for (and fix) any errors.

---

### Post by vanadium on 2009-02-14
> it is checking file systems with lots of text with <OK> after each sentance.
This does not indicate that the file systems are being checked. It suggests that you are seeing the startup messages instead of the graphical splash screen.

This is controlled from the gedit /boot/grub/menu.lst file.

```

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c9cb8b29-152a-47ac-b952-5b9909a290ba ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```
Look at the file in an editor ("gedit /boot/grub/menu.lst") and check wether, for you, the options "quiet" and "splash" are there in the line "root=...".

---

### Post by listerdl on 2009-02-14
> **vanadium said:**
> 

This is controlled from the gedit /boot/gtrd		/boot/initrd.img-2.6.24-23-generic
quirub/menu.lst file.



Sorry about this, i am a still new to this all, how do I access the above?

---

### Post by Paqman on 2009-02-14
> **listerdl said:**
> Sorry about this, i am a still new to this all, how do I access the above?

You can check the file just by navigating to that location and clicking to open it. If you need to make any changes you'll need to open it with root privileges. To do that:
```
gksu gedit /boot/grub/menu.lst
```

Btw, disregard my first post, I misinterpreted what you were describing.

---

### Post by listerdl on 2009-02-14
> **vanadium said:**
> This does not indicate that the file systems are being checked. It suggests that you are seeing the startup messages instead of the graphical splash screen.

This is controlled from the gedit /boot/grub/menu.lst file.

```

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=c9cb8b29-152a-47ac-b952-5b9909a290ba ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```
Look at the file in an editor ("gedit /boot/grub/menu.lst") and check wether, for you, the options "quiet" and "splash" are there in the line "root=...".

Hi when i look at this script i think that my "quiet" and "splash" options have been registered:

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7a6807af-b421-4520-ae11-f592a27caf8d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a6807af-b421-4520-ae11-f592a27caf8d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7a6807af-b421-4520-ae11-f592a27caf8d
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7a6807af-b421-4520-ae11-f592a27caf8d ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		7a6807af-b421-4520-ae11-f592a27caf8d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a6807af-b421-4520-ae11-f592a27caf8d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		7a6807af-b421-4520-ae11-f592a27caf8d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=7a6807af-b421-4520-ae11-f592a27caf8d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		7a6807af-b421-4520-ae11-f592a27caf8d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thanks I really appreciate your help

---

### Post by drs305 on 2009-02-14
Just to get back to the first post and startupmanager, the option to turn on and off the text scrolling is accessed from the "Boot Options" tab, "Show text during boot". When selected, it removes "quiet" from the *kernel* line of grub's menu. When not ticked, it adds "quiet" to the line so the text isn't displayed.

More information about *startupmanager* options is available through the link in my signature line.

---

### Post by listerdl on 2009-02-15
Hi, I appreciate all your assistance, and I have tried all the above advice, but I am still experiencing this irratating long boot-up process.

To explain the processes:

1. I turn on the power
2. The Ubuntu status bar behaves normally and completes its bar.
3. Then, I have to endure about 3 minutes of being told what programs have been started etc - things like setting kernel variables etc
4. Then it goes to the password and username stage
5. Everything works 100%

--

I have checked and unchecked the "Show text during boot" from the start-up manager and no joy. I really am at a loss with this. Is there any other setting that I can change?

Or, do you think I am to do a clean re-install? Thing is that once I have logged in everything works great....seems a little odd....

Thanks for all replies.

---

### Post by listerdl on 2009-02-15
Is it possible that I have 'duplicated' the start-up mechannism for ubuntu to load?

---

### Post by drs305 on 2009-02-15
I've been following your posts (and saw your related question on the grub tutorial page). Seeing the processes during boot is normal if you have the menu.lst "quiet" option off. Normally, for me at least, I don't see the orange progress bar and *then* the text describing what is happening. I never see the progress bar, just the text. If you have Startup-Manager's Boot Options "Show text during boot" I am not sure why you are seeing the processes scroll on your system during boot.

Taking 3+ minutes to boot is something that to me would be more annoying than seeing what is happening (which I have enabled by choice anyway). 

A couple of things you can take a look at since your boot is taking 3 minutes or longer: System, Preferences, Sessions. Look at the items you don't really need and deselect them (bluetooth?). One that takes more resources than I care to use is Tracker. 

You could also just take a quick look at the contents of /etc/init.d  These are processes that are called during various runlevels. You may not know what most of them are, but it's worth checking to see if something looks out of place.

There are threads about speeding up the boot process which can give you more details. (As an aside, one of jaunty's goals is to speed up boot times.)

---

