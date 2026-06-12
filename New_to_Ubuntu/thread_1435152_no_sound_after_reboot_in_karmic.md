---
title: "no sound after reboot in karmic?"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by leavitodeaver on 2010-03-21
i've been running karmic for a good 2-3 weeks now, everything going smoothly, something seemed to lock up in firefox, so i figured a good restart would take care of it.  on reboot, it gave me some error msg about kernel panic (didn't write it down unfortunately), powered down completely, booted fine after that, except now i have no sound.  system>prefs>sound shows no devices, says it's using "Dummy Output Stereo."  using onboard sound card for asus p5kpl-vm.  if anyone has ideas, please respond, i can't seem to get this rockin again.

---

### Post by leavitodeaver on 2010-03-21
found another thread with same issue, tried purging alsa-base and pulseaudio, reinstalled, and sudo alsa force-reload gives me a few fatal errors, i can list if necessary.  also found lots of people removing their software modem drivers, i have no option to do this under sys>admin>hardware drivers, just nvidia graphics and removing that does nothing.   help?

---

### Post by leavitodeaver on 2010-03-21
tried everything that's been suggested to me, edited the alsa config file, still not getting anywhere.  anyone out there?

---

### Post by garvinrick4 on 2010-03-21
Seems you need a fsck, your system is in distress and asking for help.

---

### Post by leavitodeaver on 2010-03-22
ran fsck after booting into the live cd (since apparently my monitor is incapable of running single user mode), no errors.  although it took less than a second, so i might've done it wrong, i did "sudo fsck -a /dev/sdb1".  still no sound, not even booting music, everthing is up all the way, no devices recognized.  please help me fix this damn thing, i just want to watch a movie.

---

### Post by Noraphalem on 2010-03-22
Ok:

1. Post the output of the booting sequence. That might be useful.

2. Boot an older kernel. In the GRUB menu should be more entries. Maybe this solves the problem temporarly.

---

### Post by fidelandche on 2010-03-22
I did have the same problem. What I did was backup everything then reinstall Karmic and hey presto the sound was then re-working, I am not saying that this is the answer for you but it did work for me.

---

### Post by thealphamale05 on 2010-03-22
post the output of 



`sudo dmesg`
`sudo lspci`
`tail -100 /var/log/messages`

---

