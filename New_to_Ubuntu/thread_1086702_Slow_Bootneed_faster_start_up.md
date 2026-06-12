---
title: "Slow Boot/need faster start up"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2009-03-04
I have xubuntu and I think I have all necessary upgrades.

When I boot the little bar gets to half way, freezes for about 4 minutes before it continues loading.

How can I troubleshoot this?

In addition how do I encourage a faster boot.  I was forever trimming startup aps in windows but I have no idea how to do it in linux.

---

### Post by philinux on 2009-03-04
Open a terminal and use the command 

```
dmesg
```

Also look at the file /var/log/messages

---

### Post by shadow120 on 2009-03-04
to see what runs on start up   preferences - sessions

---

### Post by AutumnPhoenix on 2009-03-04
dmesg produces about a zillion lines of stuff.  Anything I should particularly be looking for?

And I am not sure how to check on what starts up, what is important, or how to get rid of the useless stuff.

---

### Post by rjmoerland on 2009-03-04
if you use grub to start xubuntu (you probably do), press the escape key to show the grub boot menu. Select the topmost line that starts with Xubuntu. Press the 'e' key to edit this entry. You'll be shown a few lines of text. Go to the line that starts with "kernel ..." and press 'e' again. You can then edit that line. Add to the end of the line the word 'profile', press enter and press the 'b' key to boot. Linux will now profile the boot (will take some time). It will optimize the order in which the files necessary to boot are loaded, shaving some seconds off the boot. 

Furthermore, you may get some insight as well into what is booting with bootchart: [http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)

EDIT: here's some extra reading: [http://aldeby.org/blog/index.php/speed-up-your-ubuntu-linux-boot.html](http://aldeby.org/blog/index.php/speed-up-your-ubuntu-linux-boot.html)

---

### Post by philinux on 2009-03-04
> **AutumnPhoenix said:**
> dmesg produces about a zillion lines of stuff.  Anything I should particularly be looking for?

And I am not sure how to check on what starts up, what is important, or how to get rid of the useless stuff.

Yes, look at the times on the left and look for a big gap where your system hangs.

---

### Post by AutumnPhoenix on 2009-03-04
Do you mean like this?

> 

[  151.632251] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  151.632262] pci 0000:00:02.0: setting latency timer to 64
[  151.635140] [drm] Initialized i915 1.6.0 20060119 on minor 0
[ 2305.924045] usb 5-2: new high speed USB device using ehci_hcd and address 3
[ 2306.085678] usb 5-2: configuration #1 chosen from 1 choice
[ 2306.323787] usbcore: registered new interface driver libusual


---

### Post by AutumnPhoenix on 2009-03-04
> **rjmoerland said:**
> if you use grub to start xubuntu (you probably do), press the escape key to show the grub boot menu. Select the topmost line that starts with Xubuntu. Press the 'e' key to edit this entry. You'll be shown a few lines of text. Go to the line that starts with "kernel ..." and press 'e' again. You can then edit that line. Add to the end of the line the word 'profile', press enter and press the 'b' key to boot. Linux will now profile the boot (will take some time). It will optimize the order in which the files necessary to boot are loaded, shaving some seconds off the boot. 

Furthermore, you may get some insight as well into what is booting with bootchart: [http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604)

EDIT: here's some extra reading: [http://aldeby.org/blog/index.php/speed-up-your-ubuntu-linux-boot.html](http://aldeby.org/blog/index.php/speed-up-your-ubuntu-linux-boot.html)

thanks, I'll read that and try it.  alot of this is still above my head

---

### Post by mikechant on 2009-03-04
> When I boot the little bar gets to half way, freezes for about 4 minutes before it continues loading.

How can I troubleshoot this?

In the default setup you don't see the boot messages. If you could see the boot messages while the startup was stalled, the last message (or last few messages) would probably indicate where it was stalling. To display the boot messages you can follow rjmoerland's instructions above for temprorarily editing your grub startup entry, but instead of adding 'profile' as an option, remove the options 'quiet' and 'splash'.

Incidentally, many people prefer to always display the boot messages; if you want this change to be permanent then you need to edit your menu.lst file (sudo gedit /boot/grub/menu.lst). You need to remove 'quiet' and 'splash' from the '# defoptions' line (not from the indivdual menu entries) and then after saving this change, run the command 'sudo update-grub' to actually change the individual entries.

Extra note: I don't have access to my Ubuntu machine at the moment but I have a vague feeling that having a completely blank '# defoptions=' may not work. You might have to instead change it from
# defoptions= quiet splash
to something like
# defoptions= nosplash
to avoid it being blank.
This might be a bug which has been fixed however.

All from memory, so apologies for any inaccuracies!

---

### Post by OffAxis on 2009-03-04
+1 for bootchart.

That program is great. It makes it really easy to see what's going on in your boot process.

the home page for boot chart is
[http://www.bootchart.org](http://www.bootchart.org)

---

### Post by AutumnPhoenix on 2009-03-04
> **mikechant said:**
> In the default setup you don't see the boot messages. If you could see the boot messages while the startup was stalled, the last message (or last few messages) would probably indicate where it was stalling. To display the boot messages you can follow rjmoerland's instructions above for temprorarily editing your grub startup entry, but instead of adding 'profile' as an option, remove the options 'quiet' and 'splash'.

Incidentally, many people prefer to always display the boot messages; if you want this change to be permanent then you need to edit your menu.lst file (sudo gedit /boot/grub/menu.lst). You need to remove 'quiet' and 'splash' from the '#defoptions' line (not from the indivdual menu entries) and then after saving this change, run the command 'sudo update-grub' to actually change the individual entries.

Extra note: I don't have access to my Ubuntu machine at the moment but I have a vague feeling that having a blank #defoptions= may not work. You might have to instead change it from
#defoptions= quiet splash
to something like
#defoptions= nosplash
to avoid it being blank.
This might be a bug which has been fixed however.

All from memory, so apologies for any inaccuracies!


Thanks mike

I'm still very unpracticed in Linux and kinda need direct "put this into terminal" instructions.  I'm learning slowly, beucase I don't have much time to devote to Linux.  My only goal right now is to keep my linux machiene up and running and useful to prove that someone with limited knowlege and ability can indeed use linux without all hell breaking loose.  Of course, I'm a geek and I've done basic programming, but still, a who new OS is scary for people like my roommate.  But my friends use my lappy and love its speed and clean menus so I'm winning converts.  :D

---

### Post by AutumnPhoenix on 2009-03-04
> **shadow120 said:**
> to see what runs on start up   preferences - sessions


what do I have to do to get to preferances?

---

### Post by sports fan Matt on 2009-03-04
This is under "System" at the top

---

### Post by AutumnPhoenix on 2009-03-04
nevermind if I'm being quite daft but when I go under system in the menu I don't have "preferances"

---

### Post by rjmoerland on 2009-03-04
> **AutumnPhoenix said:**
> nevermind if I'm being quite daft but when I go under system in the menu I don't have "preferances"

If you're daft then so am I :D. I think that's an Ubuntu thing. I *believe* Settings->Settings Manager and then 'Sessions and Startup ' is similar, together with 'Autostarted apps'.

---

### Post by AutumnPhoenix on 2009-03-04
ok actually very few things start up.  I can make it go even faster now!  YAY!

Now onto fixing the boot problem.

---

