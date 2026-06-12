---
title: "Help With GRUB"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Minker17 on 2010-02-26
I'm running Win7 on a SSD and 9.10 on a seperate SATA drive. Everything is booting fine, except for GRUB which take 10-15 seconds to load to the OS selection screen.

I've read that this is a typical behavior of GRUB2 and that there are two solutions:

1) Revert back to a legacy version of GRUB. I have tried this and screwed up royaly and got stuck at the gub shell and couldn't boot Win7 or 9.10 so I had to rebuild.

2) Change where GRUB is installed since it can be on the wrong drive. I've read that doing this causes it to load almost immediately.

The issue I'm having is that I have no idea where I should install GRUB to or where it currently is. Does it go on the Windows MBR partition, 9.10 Filesystem, Swap, or what.

Any help would be appreciated as one of the reasons I got a SSD was for boot speed and now I'm forced to wait an extra 15 seconds before I can attempt to boot.

---

### Post by mikeyphi on 2010-02-26
Grub should be installed on your first boot HD - as listed in BIOS.

Under Grub2 there is an option to install grub on all HDs.

---

### Post by drs305 on 2010-02-26
There is actually a third option, which I find easier.

For users experiencing a delay while Grub 2 searches for the correct location of its files, the delay can be reduced by making the first drive booted by BIOS match the drive on which you have Grub 2 installed. If you just change the BIOS boot order you won't have to move Grub 2 around.

---

### Post by Minker17 on 2010-02-26
I just checked in my BIOS and I can't select which drive to boot off first, just the boot order of HDD, USB, etc. This is on a Dell, so their BIOS isn't that friendly. :)

So can I figure out what drive grub is currently installed on, and then figure out which drive I should install it on?

---

### Post by drs305 on 2010-02-26
> **Minker17 said:**
> I just checked in my BIOS and I can't select which drive to boot off first, just the boot order of HDD, USB, etc. This is on a Dell, so their BIOS isn't that friendly. :)

So can I figure out what drive grub is currently installed on, and then figure out which drive I should install it on?

You can run (the first one just makes a copy of your current grub.cfg file):
```

sudo cp /boot/grub/grub.cfg ~/Desktop/grub.cfg
sudo dpkg-reconfigure grub-pc
```
It will first ask if you want to add any options (such as "quiet splash") on the second screen. Normally you can just accept the defaults by pressing the TAB key to highlight "OK", then ENTER. Finally you will be brought to the screen which shows all the drives/partitions. Select the appropriate **drive** (drive only, not drive/partition) by using arrow keys to highlight the drive and selecting the drive by pressing the spacebar.

Once it's installed, run "sudo update-grub" just to be sure everything has been found. Before rebooting, you can check everything is as it should be by inspecting the /boot/grub/grub.cfg file or running the [boot info script]("http://bootinfoscript.sourceforge.net/").

---

### Post by Minker17 on 2010-02-26
To ask a silly question, this would be my Ubuntu drive and not my Windows drive, correct?

---

### Post by drs305 on 2010-02-26
> **Minker17 said:**
> To ask a silly question, this would be my Ubuntu drive and not my Windows drive, correct?

Yes.

---

### Post by Minker17 on 2010-02-26
Well everything seemed to work OK, but I still am having about a 15 second wait for Grub to load.

I appreciate all your help and if you think of anything else, please let me know.

---

### Post by drs305 on 2010-02-26
I would suspect if the delay is still there Grub 2 was probably just put back where it was originally and that the drive is not the first one looked at by the BIOS. But it may be something else. Perhaps meierfra.'s boot info script will provide some answers. Post the results between code tags by using the # icon in the post's menu.
[boot info script]("http://bootinfoscript.sourceforge.net/")

---

### Post by Minker17 on 2010-02-26
I would assume that my Windows drive is the first one the BIOS is seeing as it is plugged into SATA0 on the motherboard. I guess I could switch the Ubuntu drive sata slot on the MB, or would that cause other issues.

---

### Post by drs305 on 2010-02-26
> **Minker17 said:**
> I would assume that my Windows drive is the first one the BIOS is seeing as it is plugged into SATA0 on the motherboard. I guess I could switch the Ubuntu drive sata slot on the MB, or would that cause other issues.

Yes, that should work - if it doesn't you can always reverse the cables back the way they were. But UUIDs should help correctly boot into Ubuntu.

If you have problems during boot you can also highlight an entry, press "e" and then manually change the (hdX,Y) values if necessary and press Ctrl-x to boot. Check /boot/grub/device.map after you have booted and make sure the entries are correct.

---

