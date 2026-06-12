---
title: "Thunderbird and big thunder"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by oxygenfarm on 2011-05-23
I was cleaning up my wife's computer and foolishly said 'yeah, upgrade to 11.04'. After it loaded, the graphics went screwy and the desktop menus were devastated. I am in big trouble!
First: Can I roll back to 10.10 or did the upgrade delete the old kernel?
Second: Must I re-install 10.10 to avoid further grief?
Third: If I can find the old Thunderbird profile, can I load it onto a newly installed 10.10...and how?
I think other data can be recovered but have no idea how to save the TB profile. There were comments on the Forum but all were several years/versions old.
Help!

---

### Post by MyR on 2011-05-23
First I would try fixing the new version before anything else. google for the model of the laptop + ubuntu 11.04

You must re-install 10.10 if you want to go back to it.

If I recall correctly, thunderbird setting are stored in ~/.thunderbird
just make a backup of this folder onto some other hard drive before reinstalling 10.10.

Hope this helps!

---

### Post by oxygenfarm on 2011-05-24
OK. I put in another HD (to keep the old one intact) then installed 10.10 onto the new HD and copied over the contents of /home, then deleted the (new) .thunderbird and inserted the old profile as ~/.thunderbird but Thunderbird will not read/import the old profile.

Should I just buy a newer graphics card and reinsert the old HD (with its 11.04)?

---

### Post by oxygenfarm on 2011-05-24
Maybe? After many restarts, and a lot of blank patches on the desktop, I finally got into _System>Administration>login screen_, and was able to set the display to Ubuntu Classic (no effects).
For the moment, Ubuntu 11.04 is behaving well on this old computer.
Thanks for the input.
Perhaps the suggested easy upgrade is much more dangerous than trying a Live CD would be?

---

### Post by oldfred on 2011-05-24
I am running Maverick and installed Natty in another partition. After reverting to Gnome I do not see much difference. On my desktop I of late, have had to use nomodeset to boot first time then install nVidia drivers.

I regularly move my Thunderbird from my desktop to my laptop & back. But I have it in a shared NTFS partition to also use with XP. Did you start TB once before copying? 

I find it easiest just to start it to create a new default profile and copy the lower level file with xxxxx.default and edit the profile.ini to use the XXXX.default folder I just copied.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by satanselbow on 2011-05-24
Have you checked the file permissions on the copied ~./thunderbird folder?

I had a very similar issue with a ./mozilla firefox profile folder which temporarily locked me out / failed to load ;)

Specifically checked the ownership - even if you used the exact same Ubuntu username on the new install ;)

```
sudo chown user:user /home/user/ -R  
```

will take ownership of your entire home folder :D

---

### Post by oxygenfarm on 2011-05-24
Thanks. I think I solved the TB problem by resolving the display on the original (now 11.04) HD to Ubuntu Classic (no effects).

---

