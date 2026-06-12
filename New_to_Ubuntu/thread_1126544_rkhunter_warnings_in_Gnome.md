---
title: "rkhunter warnings in Gnome"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by mikodo on 2009-04-15
Hello Everyone,

I ran rkhunter and was given, in part, 

Performing file system checks

    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Following another thread about this I ran,
 sudo gedit /var/log/rkhunter.log 

and received in part:

Performing filesystem checks
[12:45:28] Info: Starting test name 'filesystem'
[12:45:28] Info: SCAN_MODE_DEV set to 'THOROUGH'
[12:45:35]   Checking /dev for suspicious file types         [ Warning ]
[12:45:35] Warning: Suspicious file types found in /dev:
[12:45:35]          /dev/shm/pulse-shm-45453970: data
[12:45:36]   Checking for hidden files and directories       [ Warning ]
[12:45:36] Warning: Hidden directory found: /dev/.static
[12:45:36] Warning: Hidden directory found: /dev/.udev
[12:45:36] Warning: Hidden directory found: /dev/.initramfs

Is this something to worry about? If not, can this be removed or white listed so as to not be shown again? 

I have found nothing suspicious when I run chkrootkit.

Thank you,

---

### Post by James_Lochhead on 2009-04-15
I don't have rkhunter installed at the moment but when I have used it previously I seem to remember this showing it. Apparently, it is a false positive; the rkhunter software is not perfect.

**I would make sure of this though as I am not 100% sure.**

---

### Post by gandaran on 2009-04-15
nothing to worry about, edit the rkhunter configuration file so they want show again
```
sudo gedit /etc/rkhunter.conf
```

---

### Post by gandaran on 2009-04-15
> **James_Lochhead said:**
> I don't have rkhunter installed at the moment but when I have used it previously I seem to remember this showing it. Apparently, it is a false positive; the rkhunter software is not perfect.

**I would make sure of this though as I am not 100% sure.**
it's not exactly a false positive, this is how rkhunter works, it alerts the user on anything that could be suspicious like these hidden files, it's up to the user to decide what to do!

---

### Post by mikodo on 2009-04-15
Thank you for the replies,

For the future, how can I make my own determination to decide what to do with similar situations. Is the correct answer to do an online search maybe?

Thanks again,

---

### Post by gandaran on 2009-04-15
> Is the correct answer to do an online search maybe?
yes, paste one suspicious rkhunter output line in google search bar, theres plenty information about rkhunter on the web.

---

### Post by mikodo on 2009-04-15
Thank you gandaran,

If I new how to tag this thread as solved, I would.

mikodo

---

