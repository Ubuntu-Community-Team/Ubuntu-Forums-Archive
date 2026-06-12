---
title: "Banshee Iphone Mp3's import problem"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by 23494asd on 2011-06-15
I used the Banshee music export function, to transfer mp3's to my iphone 4 with ubuntu 11.04. Beside Banshee reports all finished and takes some time, the songs do not end up on the device. Though erasing of existing songs work. The device is jailbroken.

Ideas?

Thanks!

---

### Post by DarkAmbient on 2011-07-14
Found this on launchpad. Credit goes to m0sia.

> The following steps works for me:
1. Jaibreak the phone (via [http://jailbreakme.com](http://jailbreakme.com))
2. Install openssh from cydia
3. ssh to the phone
4. change DBVersion to 4 in the /system/library/lockdown/Checkpoint.xml
5. Generated HashInfo following the link [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
6. copy HashInfo to the folder /var/mobile/Media/iTunes_Control/Device/
7. Reboot the phone
8. Mounted device automatically using Ubuntu Natty (libmobiledevice, ifuse and so on already installed)
9. Sync using Banshee

I can add that step 5 and 6 is only if you haven't used your iDevice with iTunes, or doesn't plan todo so in the future. What you are doing with step 5 & 6 is removing Apples restriction to third-party-software.

I personally skipped part 5 & 6, only changed DBversion in that XML file to 4. And rebooted, now I can sync with Banshee.

Good luck!

---

### Post by mikejonesey on 2011-07-14
hardcore just for music sync lol...

---

