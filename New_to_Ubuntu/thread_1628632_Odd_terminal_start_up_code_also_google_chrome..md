---
title: "Odd terminal start up code? also google chrome."
date: 2010-11-22
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-11-22
I had to do a fresh install of ubuntu 10.10 but i kept my home folder. When i load up terminal i get this, everything is working fine but i would like to know what it means.

```
mkdir: cannot create directory `/dev/cgroup/cpu/user/16663': No such file or directory
bash: /dev/cgroup/cpu/user/16663/tasks: No such file or directory

```

With google chrome, flash player keeps crashing, is anyone else having this problem?

---

### Post by karlwbloedorn on 2010-11-22
Not sure about the first one.

Did you install Google Chrome or Chromium?
Which method did you use to install the flash player plugin?

I've only had flash player crash once or twice since installing chrome a couple weeks ago.

I installed it with these commands:

sudo apt-get install flashplugin-installer

sudo mkdir /opt/google/chrome/plugins

sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /opt/google/chrome/plugins

Then I edited the launcher for Google Chrome in the main menu:

Added "--enable-plugins" right before the "%U" at the end of the Command entry.

Then restarted Google Chrome and went to flash content.


I'm guessing the problem with the 1st problem is due to some leftover remnant. Hopefully someone else might know what it is so you can clean it up.

---

### Post by cariboo on 2010-11-23
It looks like you may have an error some in the work around for the kernel patch. I've attached the full raw output for the work around. I have a problem flash 32-bit crashing fairly often using chromium, I haven't bothered to look for the cause yet though.

---

### Post by Rave Gloves on 2010-11-23
> **cariboo907 said:**
> It looks like you may have an error some in the work around for the kernel patch. I've attached the full raw output for the work around. I have a problem flash 32-bit crashing fairly often using chromium, I haven't bothered to look for the cause yet though.

Thanks man that sorted it,when i did the clean install i thought it overwritten the kernel so i wouldn't have had that coding. Cheers ! :)

---

