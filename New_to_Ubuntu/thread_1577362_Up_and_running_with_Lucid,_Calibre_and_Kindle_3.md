---
title: "Up and running with Lucid, Calibre and Kindle 3"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by xsyw9998 on 2010-09-18
Okay, so I probably got the order of things a little screwed up, but after a few hours of tinkering, I managed to get my new Kindle 3 (sweet!) working with Calibre under Lucid 10.04.

Apparently, Calibre creates a directory named "Kindle Main Memory" under /media -- and unfortunately, upon mounting, I discovered it only has root permissions since it's a vfat file system. 

The fix turned out to be fairly straight forward. I added the following line to /etc/fstab:

#Kindle3 Device
/dev/sdb1 /media/Kindle\040Main\040Memory vfat auto,user,rw,umask=007,noexec,uid=1000,gid=1000,utf8 0 0

[Note: the \040 substitutes for a space (blank), no need for quotation marks]

I also had to go in through gconf-editor and turn off Nautilus' "*media_automount*" and "*media_automount_open*" options (under apps/nautilus/preferences), at least initially. I'll have to try turning those back on and see what happens...

As for Calibre, I ended up installing the most current release from their web site ([http://calibre-ebook.com/](http://calibre-ebook.com/)) because the version in the repositories doesn't know about the Kindle 3. There's a story about this here: [http://www.peppertop.com/blog/?p=1054](http://www.peppertop.com/blog/?p=1054) but I couldn't get the guy's suggestion to work (arrgh!) hence the need to install the latest and greatest version from Calibre.

With the additional entry in fstab (mentioned above), the Kindle 3 *does* automount allowing access to its files via nautilus. Only trouble I have right now is that choosing "Unmount" from the nautilus context menu produces the error message "Only root can unmount /dev/sdb1 from /media/Kindle Main Memory" -- hmmm, not a serious problem, *sudo umount /media/"Kindle Main Memory"* does the trick, slightly annoying though it may be.

Anyway, once the Kindle 3 is mounted, Calibre has no problem transferring files to it.

Any additional tips, tricks and suggestions from the Ubuntu gurus out there would be appreciated to finalize this story!

Best regards,
Chris in New Mexico

P.S. This is my first post and I've been using Ubuntu since Jaunty was first released. Am I an expert yet? Hell no! But I'll tell you what, I'll *NEVER* go back to Windows! It used to take Vista what seemed like forever to shut down, despite endless tweaking to get it to shut down faster. With Ubuntu, when I say shutdown, it's like RIGHT NOW! And that's important for me, since I'm off-grid and running 100% solar. To all the Ubuntu developers, keep up the outstanding work! (Now imagine if EVERYTHING on the planet were in the open source paradigm...)

---

### Post by sandyd on 2010-09-18
> **xsyw9998 said:**
> Okay, so I probably got the order of things a little screwed up, but after a few hours of tinkering, I managed to get my new Kindle 3 (sweet!) working with Calibre under Lucid 10.04.

Apparently, Calibre creates a directory named "Kindle Main Memory" under /media -- and unfortunately, upon mounting, I discovered it only has root permissions since it's a vfat file system. 

The fix turned out to be fairly straight forward. I added the following line to /etc/fstab:

#Kindle3 Device
/dev/sdb1 /media/Kindle\040Main\040Memory vfat auto,user,rw,umask=007,noexec,uid=1000,gid=1000,utf8 0 0

[Note: the \040 substitutes for a space (blank), no need for quotation marks]

I also had to go in through gconf-editor and turn off Nautilus' "*media_automount*" and "*media_automount_open*" options (under apps/nautilus/preferences), at least initially. I'll have to try turning those back on and see what happens...

As for Calibre, I ended up installing the most current release from their web site ([http://calibre-ebook.com/](http://calibre-ebook.com/)) because the version in the repositories doesn't know about the Kindle 3. There's a story about this here: [http://www.peppertop.com/blog/?p=1054](http://www.peppertop.com/blog/?p=1054) but I couldn't get the guy's suggestion to work (arrgh!) hence the need to install the latest and greatest version from Calibre.

With the additional entry in fstab (mentioned above), the Kindle 3 *does* automount allowing access to its files via nautilus. Only trouble I have right now is that choosing "Unmount" from the nautilus context menu produces the error message "Only root can unmount /dev/sdb1 from /media/Kindle Main Memory" -- hmmm, not a serious problem, *sudo umount /media/"Kindle Main Memory"* does the trick, slightly annoying though it may be.

Anyway, once the Kindle 3 is mounted, Calibre has no problem transferring files to it.

Any additional tips, tricks and suggestions from the Ubuntu gurus out there would be appreciated to finalize this story!

Best regards,
Chris in New Mexico

P.S. This is my first post and I've been using Ubuntu since Jaunty was first released. Am I an expert yet? Hell no! But I'll tell you what, I'll *NEVER* go back to Windows! It used to take Vista what seemed like forever to shut down, despite endless tweaking to get it to shut down faster. With Ubuntu, when I say shutdown, it's like RIGHT NOW! And that's important for me, since I'm off-grid and running 100% solar. To all the Ubuntu developers, keep up the outstanding work! (Now imagine if EVERYTHING on the planet were in the open source paradigm...)
your missing a "s" from the end of "user"

---

### Post by boxcorner on 2010-10-07
Many thanks for posting this info!  I was thinking of getting a Sony PRS-650.  Knowing that the Kindle 3 is also an option is very helpful.

---

### Post by Jazzy_Jeff on 2010-10-09
If you connect the Kindle to your computer and let it mount it shows up as a removable drive. Then start up Calibre and you will not have any problems transferring files.

---

### Post by anewguy on 2010-10-10
Indeed, I have the wireless version of the Nook (competitor to the Kindle), and just letting it mount up lets me move files to/from it without any extra software.  I haven't tried Calibre, and with the wireless access of the Nook don't know if I need to, but I may try it out anyway.

Dave ;)

---

### Post by henrywm on 2010-10-18
I installed Calibre with the instructions [here]("http://helpforlinux.blogspot.com/2010/05/manage-kindle-from-ubuntu.html") but I cannot access my online library at Amazon. Any ideas?

---

### Post by Gatemaze on 2010-11-12
PRS works out of the box with calibre and can also be used as an external storage device, i.e. jsut copy your files and all done... Trying currently to get it sorted with adobe digital editions... :)

---

### Post by xsyw9998 on 2011-01-03
Addendum: Apparently it's easy to forget to unmount before unplugging, thus potentially screwing up the data on the Kindle (living proof here....arrrgh...) so if your Kindle 3 mounts as a read-only file system no matter what you do to try to fix it, the following works:

1) Make sure Kindle is NOT mounted (either as Kindle or "Kindle Main Memory")
2) sudo dosfsck -r /dev/sdb1

assuming /dev/sdb1 is where your Kindle is plugged in.

If any filesystem errors are found, you'll be prompted to correct the problem (two responses will be necessary).

Sheesh. This whole Kindle/calibre thing can be tedious. I'm thinking it might just be easier to eliminate calibre and use the Kindle as a normal, mountable device.....

---

### Post by cristoper on 2011-01-26
Thank you, xsyw9998. Running dosfsck got my Kindle3 mounting as read-write again. (For others: to run dosfsck on your kindle it must be unmounted but not ejected, eg: 'sudo umount /media/Kindle').

---

### Post by kaefert66014235 on 2011-07-09
What did you guys do to get a /dev/sdb1 device for your kindle? All I get is error messages in dmesg like these:

```
[12083.977140] usb 1-2: new high speed USB device using ehci_hcd and address 34
[12084.910477] ehci_hcd 0000:00:1d.7: port 2 reset error -110
[12084.910531] hub 1-0:1.0: hub_port_status failed (err = -32)
[12085.112133] hub 1-0:1.0: unable to enumerate USB device on port 2
[12085.492089] usb 2-2: new full speed USB device using uhci_hcd and address 2
[12085.630248] usb 2-2: not running at top speed; connect to a high speed hub
[12090.653265] usb 2-2: can't set config #1, error -110
```

My Kindle Firmware Version is: "Kindle 3.1 (558700031)"
Im Running Ubuntu 10.10
My verbose lsusb output can be found here: [http://pastebin.com/0CzVxTLj](http://pastebin.com/0CzVxTLj)

Can anyone help me, anyone seen these problems before?

---

