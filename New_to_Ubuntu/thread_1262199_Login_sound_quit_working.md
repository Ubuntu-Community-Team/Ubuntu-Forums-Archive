---
title: "Login sound quit working"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by blues2use on 2009-09-09
Jaunty has worked fine for the last 4 months but as of this morning, no login sound. It is properly listed in System/Preferences/Sound/Sounds/Desktop/login and the default sound file plays there as a test. The file desktop-login.ogg exists in /usr/share/sounds/ubuntu/stereo and also plays without error; but, at login time, nothing. I don't know what got changed or how...

Suggestions for fixing it would be most appreciated...

Thanks

---

### Post by community nerd on 2009-09-09
Try going to *System>Administration>Login Window *and go to the *Sounds* section. Re-install it from the location listed. Make sure your sound is not muted.

---

### Post by blues2use on 2009-09-09
> **community nerd said:**
> Try going to *System>Administration>Login Window *and go to the *Sounds* section. Re-install it from the location listed. Make sure your sound is not muted.

Nope, still nothing...sound is not muted...all other system sounds, mp3's, streaming audio work fine...the login sound, however, is still missing-in-action..

---

### Post by blues2use on 2009-09-09
> **blues2use said:**
> Nope, still nothing...sound is not muted...all other system sounds, mp3's, streaming audio work fine...the login sound, however, is still missing-in-action..

Is there a way to repair the entire gnome theme so as to re-enable the login sound and whatever else may have been affected? 

As I stated earlier, I have no idea how this happened and, for all I know, there may be other issues I haven't uncovered yet.

---

### Post by blues2use on 2009-09-09
> **blues2use said:**
> Is there a way to repair the entire gnome theme so as to re-enable the login sound and whatever else may have been affected? 

As I stated earlier, I have no idea how this happened and, for all I know, there may be other issues I haven't uncovered yet.

If I logout from the active desktop session and then login again, I get a burst of static through the speakers rather than the login sound...so, apparently, something is out of kilter here somehow...

Your help is most appreciated...

---

### Post by blues2use on 2009-09-09
> **blues2use said:**
> If I logout from the active desktop session and then login again, I get a burst of static through the speakers rather than the login sound...so, apparently, something is out of kilter here somehow...

Your help is most appreciated...

Also, my default sound for deleting mail via Yahoo in Firefox doesn't work anymore either...so, something is fouled up in my system sounds...

is there a way to reinstall the gnome defaults for system sounds?

---

### Post by blues2use on 2009-09-09
> **blues2use said:**
> Also, my default sound for deleting mail via Yahoo in Firefox doesn't work anymore either...so, something is fouled up in my system sounds...

is there a way to reinstall the gnome defaults for system sounds?

Streaming sound and internet sound (YouTube, Shoutcast, Rhapsody, etc.) are all dead now, too, so, my sound system got hosed somehow...is there a way to reinstall or repair the entire sound system in jaunty?


Thanks

---

### Post by skynet2060 on 2009-09-09
I am also baffled as to how you system sound went hey wired. The easiest thing to do is to backup your system and reinstall ubuntu from scratch. 

To be fail-safe, download ubuntu online, burn it to a CD or DVD, and install it from there. Sometimes, unnoticed, the installation CD can become damage which prevents ubuntu from installing all necessary files  caused the system to slowly crash. Installing ubuntu from a well working cd, should remedy this problem.:popcorn:

---

### Post by blues2use on 2009-09-09
> **skynet2060 said:**
> I am also baffled as to how you system sound went hey wired. The easiest thing to do is to backup your system and reinstall ubuntu from scratch. 

To be fail-safe, download ubuntu online, burn it to a CD or DVD, and install it from there. Sometimes, unnoticed, the installation CD can become damage which prevents ubuntu from installing all necessary files  caused the system to slowly crash. Installing ubuntu from a well working cd, should remedy this problem.:popcorn:

Found this in an old thread...Here's what I did:

Removed these packages

(1) sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


Reinstalled those same packages

(2) sudo apt-get install linux-sound-base alsa-base alsa-utils

(3) sudo apt-get install gdm ubuntu-desktop

(4) Reboot

---

