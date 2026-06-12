---
title: "My Desktop Won't Load. I messed up. Please Help! ATI Driver Issue"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-08-06
Yes. I am a moron.

I have an Acer Laptop with an ATI Radeon Graphics card. I was running Ubuntu 10.04 LTS beautifully. When I installed it on the computer, everything was autodetected and running fine.

Then stupid me installed an ATI linux driver which was pretty useless. So then, stupider me went into Synaptic Package manager and uninstalled everything that had ATI associated with it in hopes that it would kick back to the default driver it was using.

Now, when i start up the computer, it just goes to a command prompt, asking me log in. I tried typing in "startx" but gives an error.

How do I just make it go back to the default display driver it was using? I would really appreciate your help.

---

### Post by nothingspecial on 2010-08-06
If you can get to a command line, try looking at the synaptic log to see what you installed and removed then try and put it right with apt
```

sudo cd /root/.synaptic/log
ls
```

Then ```
less whatever_the_log_is_called.log
```

---

### Post by Zorgoth on 2010-08-06
So where did you install the ATI driver from?

If you got it from ATI's website, there is a script to uninstall it in /usr/share/ati I believe.  Read the installation instructions on ATI's website; they have directions on uninstalling it.  Synaptic can't do it because it can only uninstall things you installed using a *.deb file.  If your ATI driver didn't work it is likely because you didn't run aticonfig --initial after you installed it, or because you got a version that didn't support your card.

---

### Post by Tiberion on 2010-08-06
you can also reboot and load the recovery kernel from there you should be able to restore xorg.conf.  If this is a single OS system Grub may not display when you boot.  So hit Shift key while booting will load grub options

---

### Post by seventhsamurai on 2010-08-06
It doesn't list the last install/uninstall. Only lists what I did before that. Is there a way for me to fix this booting off the installation cd, fixing it with that? Can I do a reinstall or something without deleting data?

---

### Post by Tiberion on 2010-08-06
you can reinstall from installation CD just don't format the hard drive.  All your personal data will be saved.  All system files will be overwritten

---

### Post by seventhsamurai on 2010-08-06
Attempting the reinstall. Fingers crossed!

---

### Post by seventhsamurai on 2010-08-06
Ok so I reinstalled without formatting. It seems to have restored everything almost to normal. But now my mouse won't work. Cursor just won't move. Please help

---

### Post by Tiberion on 2010-08-06
is your mouse usb?

---

