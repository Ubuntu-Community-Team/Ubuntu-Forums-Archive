---
title: "New user having a couple of issues."
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Jehjoa on 2010-06-19
Hello everyone, please welcome me as a new Linux user! ;)

Installing Ubuntu 10.04 64 bit went mostly without issues, save for 3 problems.

My PS/2 keyboard is acting strangely during the boot process. If I do a cold boot, the caps- and numlock lights flash once, and I can press DEL to enter BIOS setup. When I'm in the BIOS however, the keyboard doesn't respond anymore, and I have to hit the reset switch. I also can't use it in the GRUB bootloader menu, so I can't go back to Windows without changing the default entry. After booting, the keyboard works fine as evidenced by me typing this. :) If I do a warm reboot, I can't even enter the BIOS. But the keyboard does still work when fully booted. I searched this forum for posts relating to this, but they all talk about USB keyboards.

In Quake Live, a free-to-play first person shooter, sound is delayed for about 1.5 seconds, and sometimes it goes silent all together. I'm not much of a gamer, but I really want this one working.

Youtube videos don't go fullscreen. In fact, most of the buttons on the youtube player hardly work, unless I go to System > Preferences > Appearance and set Visual Effects to None. I believe setting it to any other setting loads compiz, which I guess is causing the problem (correct me if I'm wrong).

My system is the following:
Intel Core2Duo e6600 CPU
2GB of RAM
Nvidia GeForce 9600 graphics card. I installed the restricted drivers for it by going to System > Administration > Hardware drivers.

I really like the idea behind free software so I hope to get these things fixed. But if I can't, I will have to go back to Windows... Please help. :(

---

### Post by philinux on 2010-06-19
Keyboard problem in bios means the OS has no part to play, grub or OS have not even been loaded. Try another keyboard.

For flash use this. [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by JKyleOKC on 2010-06-19
If you have a USB keyboard available, try plugging it in, removing the PS/2 plug temporarily, and booting with that setup. If it works that would indicate that the BIOS is only recognizing USB for some reason, possibly some BIOS setting.

I've had the reverse situation several times, where a USB keyboard would not be recognized until after boot was complete but a PS/2 one would work. Changing a BIOS setting so that it would handle legacy i/o solved my problem, so there may be such a setting involved in yours!

---

### Post by Jehjoa on 2010-06-19
OK I just tried an different PS/2 keyboard and a USB keyboard, both gave the same problem. The strange thing is that I had no problems with my keyboard before I installed Ubuntu...

That flash plugin helped, at least. That is to say, I can go fullscreen on youtube now though it all seems a bit shaky. Sometimes I have to click a button a couple of times before it is registered.

Still haven't fixed the sound delay in Quake Live. I have no idea what could be causing it.

I just tried to watch a movie in VLC player and noticed that there is a lot of tearing going on. I messed around with the vsync options in nvidia-settings and looked for anything vsync related in VLC's settings, but no dice. My screen becomes a big mess when there's a lot of action going on.

I am not very impressed by Ubuntu so far. People saying that it's ready to take the desktop market by storm need to wake up and taste reality. How is a Regular Joe going to deal with such issues?

I'll keep hanging in there for a bit though, trying to beat it into submission.

---

