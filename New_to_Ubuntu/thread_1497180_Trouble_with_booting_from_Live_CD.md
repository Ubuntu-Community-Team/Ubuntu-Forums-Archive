---
title: "Trouble with booting from Live CD"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by BGGcategoryO on 2010-05-30
Hello,
 
I was attempting to try Ubuntu 10.04 on my laptop (Dell Latitude E6410). I burned a LiveCD and tried to run it using the instructions I read [here]("http://www.ubuntu.com/desktop/get-ubuntu/download"). I got to the purple screen with a list of options (run Ubuntu without installing, install, check hard drive, etc.) but after selecting "run without installing," th escreen went blank. The DVD drive was clearly working, and after several minutes a small amount of music played, but the screen was entirely blank.
 
I found [this page]("https://help.ubuntu.com/community/BootParameters") and tried various BootParameters, but I still don't get to the desktop (at most a small amount of text flashes before the screen).
 
Is there anything else I could do? I don't know if Ubuntu is incompatible with my hardware, and I'm not sure that I could use Wubi (since it does not seem to be compatible with Windows 7).
 
Thanks!

---

### Post by jfreak_ on 2010-05-30
Hmmm , if you have nvidia graphics  card then look at [this]("http://debugmadhouse.blogspot.com/2010/05/ubuntu-1004-nvidia-plymouth-boot-splash.html")

---

### Post by nhasian on 2010-05-30
In order to see Ubuntu in your boot menu in Windows7 you will need to run Wubi in compatibility mode (Run as: Windows Vista):

1) Right-click on wubi.exe and select Properties
2) Go to Compatibility tab and check "Run this program in compatibility mode for:" and select Windows Vista from the drop-down list.
3) Press Apply and Ok.
4) Run Wubi and continue the installation as usually.

---

### Post by BGGcategoryO on 2010-05-30
Yeah, I do have an Nvidia graphics card.
 
Ok, I will look into Wubi running under Vista compatibility and post back here again.

---

### Post by Catharsis on 2010-05-31
Have you checked the disc for errors yet?

Did you try "nomodeset" from the F6 menu?

Also try "xforcevesa noapic noapci nosplash irqpoll".

---

### Post by pzkfw on 2010-05-31
If you can't boot from liveCD it's generally the fault of old hardware or obscure hardware with unreleased docs for the community to make drivers for.

I have an old windows98 machine and no distro will boot live cd from it.

A modern foxconn motherboard (~2 years old) wouldn't boot any live cd.

A live CD has to select what drivers can be included since it only has 700MB or so to work with so some drivers won't be included.

---

### Post by BGGcategoryO on 2010-05-31
I had checked the disk for errors at the beginning. Anyway, I finally got it to load by selecting nomodeset from the options menu. Thanks, everyone!

---

### Post by Catharsis on 2010-06-01
Just be aware that you might have to enable "nomodeset" during your first boot to get to the desktop. You can do that through Grub by:
1) Hold down Shift while booting. Then press 'e'.
2) Replace "quiet splash" with "nomodeset"
3) Ctrl+x to boot.

If there aren't any proprietary drivers in System->Administration->Hardware Drivers, you'll have to enable this workaround permanently:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working around bugs in the new kernel video architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working around bugs in the new kernel video architecture)

---

### Post by BGGcategoryO on 2010-06-01
@Catharsis: OK, I see what you mean.

---

### Post by Pirhoo on 2010-06-08
Hi,

I have the same computer as you (Dell Latitude E6410) and a similar problem with my screen. Have you found a solution ?

Thank you all :)

---

### Post by BGGcategoryO on 2010-06-10
Selecting "nomodeset" from the F6 menu seemed to do the trick.

---

### Post by jcolton on 2010-07-10
Before the CD boots use F6 and add the following kernel option:
*nouveau*.*modeset*=0

From then on the 'nouveau' module will be blacklisted automatically.

When you login after install, select 'hardware drivers' and install the Nvidia proprietary driver.  reboot and enjoy.

---

