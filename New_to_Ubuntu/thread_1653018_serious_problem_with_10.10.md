---
title: "serious problem with 10.10"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by rs87424 on 2010-12-26
Hey

I have had 10.10 on my computer for a little while now and I have had no complaints until now. I turned the computer on and immediately ubuntu says that the "/home" device is not ready or not connected. I am guessing the home partition is not working for some reason? It will eventually come to the start up screen but I can't move anything and I can't type anything and I can't log into ubuntu..this seems very serious and I have no idea what is wrong or how to fix it. Help would be much appreciated

---

### Post by diablo75 on 2010-12-26
How did you install Ubuntu?  In other words, did you download and ISO file, burn it and boot from the CD?  Or did you Autorun the CD from within Windows and use the Wubi Installer to install Ubuntu?  Is Windows on the computer?  During the install, did you select any sort of manual partitioning?

It is possible that you simply have a small filesystem error that can be corrected from recovery terminal.

This might not be quite the right way to do it, but it works for me.

When you boot your computer, you should usually see a grub menu screen that displays a list of kernels that you can boot into.  The second item down is a recovery mode for the most recent kernel.  Select that.  When it's booted, a menu will appear asking what you want to do.  Hit the down arrow to select, "Drop to root prompt/terminal" (don't remember the exact wording).

From the root prompt, type:

```
sudo fsck -a
```

This will walkthrough the filesystems specified in your fstab and auto-repair any errors it finds.  This will take some time.

When it's finished, you can restart the computer by typing:

```
init 6
```

---

### Post by Elfy on 2010-12-26
Do the fsck first ... 


Not knowing what you've recently done I would first boot to recovery mode root prompt.

Check what home is supposed to be on with 

```
cat /etc/fstab
```

Then check the UUIDs 
```
blkid
```

Do they match? 

That assumes that home is on a seperate partition. 

If the UUIDs do not match for some reason 

nano /etc/fstab

Change the uuid - ctrl+X then Y then enter

reboot.

If the uuids match boot with the livecd and get meirfra's bootinfo script and run it.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by rs87424 on 2010-12-26
I downloaded ubuntu from a burnt cd and I am using Windows vista...dual booted...I will try the fsck first and let you know the result

---

### Post by kiran r on 2010-12-26
did u tried the recovery mode?

---

### Post by rs87424 on 2010-12-26
ok...I tried the recovery mode and it came up to a window... I tried the fsck thing... then it said "if you say yes (y) then serious damage can occur to the file system... I said yes.. then nothing happened so I rebooted... and then it said something like "grub rescue"... so I just put the ubuntu installation disk in because I was too frustrated to continue...

---

