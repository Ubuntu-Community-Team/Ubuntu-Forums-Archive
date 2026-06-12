---
title: "Gparted"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by garthcrocker on 2009-03-03
I'm running Ubuntu 8.10 successfully and wanted to resize my 250 Gb sda/1 partition to create some vacant space. Gparted starts up ok and recognises the drive but the commands are greyed out. How do I make it actually do something? I've tried clicking on everything in sight but no joy.:(

---

### Post by avtolle on 2009-03-03
The drive is mounted. You will need to run GParted from the live CD (either its own or the Ubuntu Live CD used for installation).

EDIT: After booting from the Live CD, of course. By booting up from the HDD, the drive is mounted, as it must be for you to run the o/s.

---

### Post by st33med on 2009-03-03
```
sudo gparted
```

You need root permissions to do this.

Also, it is not recommended to do this on the HDD. Try using the Gparted CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by garthcrocker on 2009-03-03
Many thanks. I'm scared stiff of causing a melt-down.

---

### Post by stchman on 2009-03-03
> **st33med said:**
> ```
sudo gparted
```

You need root permissions to do this.

Also, it is not recommended to do this on the HDD. Try using the Gparted CD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

The gparted package when installed in Ubuntu is in the System--->Administration section.  It prompts you for your admin password.

---

### Post by stchman on 2009-03-03
> **garthcrocker said:**
> I'm running Ubuntu 8.10 successfully and wanted to resize my 250 Gb sda/1 partition to create some vacant space. Gparted starts up ok and recognises the drive but the commands are greyed out. How do I make it actually do something? I've tried clicking on everything in sight but no joy.:(

Run the Ubuntu LiveCD.  Gparted is on there.

You can launch gparted and resize the partition.  Make sure you have your data backed up before doing this.

---

### Post by garthcrocker on 2009-03-03
Is it possible to boot up from another system on an external HDD on USB?

---

### Post by stchman on 2009-03-03
> **garthcrocker said:**
> Is it possible to boot up from another system on an external HDD on USB?

Yes, a lot of systems have an F12 boot option or you go into the BIOS and tell it to boot from USB.

---

### Post by garthcrocker on 2009-03-03
Many thanks. Had a look but that doesn't seem to be an option on this box. It's one of these lightweight Asus desktops that's got a half-size tower. Comes of going for the cheap option - but at least the fan is quiet. Last one I had sounded like I was working in the boiler-room and made about the same amount of heat!

---

