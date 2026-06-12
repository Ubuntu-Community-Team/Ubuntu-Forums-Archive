---
title: "Issue with dual boot windows 7 and lucid lynx"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by pilotguy415 on 2010-09-22
I hope this is the right forum and hopefully someone can enlighten me to what is going on.

So, I have two hdds hooked up to my PC. I have windows 7 installed on my main hdd and recently installed Ubuntu 10.04 Lucid Lynx on the other 120gb hdd.

Everything went fine with the Ubuntu installation and I've only used Ubuntu for the last couple of weeks. Today I needed to access Windows to do some work in Adobe CS5. Anyway, when I restarted the computer to get to my windows drive I a screen showing:

> Verifying DMI pool data.........
AMD Data Change...Update New Data to DMI!then nothing. It just stays on that screen. I figured this might be an issue with what disk is trying to boot so I manually selected my 500gb HDD and get the same screen. I boot to the Ubuntu HDD and everything loads fine.

I tried running the windows startup disk and I just get to the screen that shows the background wallpaper and no options to do anything (issue with disk?).

I figure this might have something to do with GRUB, but I don't understand anything about setting it up. Anyone have any ideas? Any help is greatly appreciated.

---

### Post by pilotguy415 on 2010-09-22
Bump
 
Anyone have any ideas?

---

### Post by Audiosurfer on 2010-09-22
srry dude. instead of installing on separate hdd u could have used wubi and installed it side by side so when u boot up pc, it gives option as to which u wanna use. i use windows 7 home premium 64 bit and ubuntu  10.04 desktop edition with wubi. they call it windows installer when u go to ubuntu.com and click get ubuntu desktop edition. I hope this helped. Im a noob myself. Oh btw with wubi, ubuntu installs like an app, and can be uninstalled from within windows.

---

### Post by sandyd on 2010-09-22
> **pilotguy415 said:**
> I hope this is the right forum and hopefully someone can enlighten me to what is going on.

So, I have two hdds hooked up to my PC. I have windows 7 installed on my main hdd and recently installed Ubuntu 10.04 Lucid Lynx on the other 120gb hdd.

Everything went fine with the Ubuntu installation and I've only used Ubuntu for the last couple of weeks. Today I needed to access Windows to do some work in Adobe CS5. Anyway, when I restarted the computer to get to my windows drive I a screen showing:

then nothing. It just stays on that screen. I figured this might be an issue with what disk is trying to boot so I manually selected my 500gb HDD and get the same screen. I boot to the Ubuntu HDD and everything loads fine.

I tried running the windows startup disk and I just get to the screen that shows the background wallpaper and no options to do anything (issue with disk?).

I figure this might have something to do with GRUB, but I don't understand anything about setting it up. Anyone have any ideas? Any help is greatly appreciated.
[http://lmgtfy.com/?q=windows+stuck+AMD+Data+Change]("http://www.google.com/search?client=ubuntu&channel=fs&q=windows+stuck+AMD+Data+Change&ie=utf-8&oe=utf-8")

Not something to do with ubuntu.

---

### Post by Mark Phelps on 2010-09-23
I'm personally a big fan of installing different OSs to different drives.  In the long run, this saves a lot of grief with corrupted boot loaders, overwritten MBRs, etc.

What you could try for Win7 is to boot from the CD into command mode and run the following commands:
-- bootrec.exe /fixmbr
-- bootrect.exe /fixboot

Here's a link to the MS info on bootrec:

[http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

Sometimes, the Startup Repair wizard just doesn't work!

---

### Post by pilotguy415 on 2010-09-23
That did it Mark, thank you! I managed to get into the command prompt with the startup disk after leaving it running for a few hours :-/. Once in I ran the commands then began getting "BOOTMGR is missing. CTRL+ALT+DEL to restart" after that it was simply a startup repair and working!

Thanks again!

---

