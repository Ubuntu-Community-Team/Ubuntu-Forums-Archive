---
title: "how o start &quot;nvidia xconfig&quot;"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by thewizardx on 2009-01-27
i am a absolute beginner and i would like to have some start help i get this message when starting nvidia setting

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

where do i start

---

### Post by perlluver on 2009-01-27
> **thewizardx said:**
> i am a absolute beginner and i would like to have some start help i get this message when starting nvidia setting

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

where do i start

Have you enabled restricted drivers?  System>Administration>Hardware Drivers, and check to see if they are installed.

---

### Post by Ben Page on 2009-01-27
do this code in terminal:

gksudo gedit /etc/X11/xorg.conf

But that error reminds me of not installed proprietary driver. Remember to restart after the driver is installed, look for x server in the administration menu (if its there, than the driver is installed - it is green with Nvidia logo).

---

### Post by tkb608 on 2009-02-17
Hello, first post here. I Ran into this same issue just now while installing mythbunutu 8.10 . The setup utility suggested running nvidia-xconfig but that utility did not exist yet. I exited the nvidia setup and went to System>Administration>Hardware Drivers as perlluver suggested. There was a proprietary driver acceptance screen waiting for me there. Once I "yesed" the screen the nvidia driver was installed along with the nvidia-xconfig utility. The I ran "sudo nvidia-config" at the command line. There were several "warnings" but everything seems ducky.
  Hope that helps someone. Thought I'd post here since this is the first hit for the google search "mythbuntu nvidia-xconfig"

---

