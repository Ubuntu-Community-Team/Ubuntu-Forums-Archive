---
title: "Difficulty updating... Is this normal?"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-18
I have an installation of Ubuntu v10.04 LTS on a Dell Inspiron 9400. I have 2 profiles set up. One is an Admin, and the other is a non-admin User. I'd logged into the User profile, then tried to do an update using the terminal window. If failed, which I figured was because the User didn't have the rights to do that. I logged out and logged back in as the Admin. I tried it again from there, and was surprised that it also failed from there - and, there was a repeating of these error messages:

E: Could not open lock file /var/lib/lock - open (13: permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?

Then it went to the command prompt. I used exit, then rebooted the computer.

Logging into the Admin profile, I tried it again. Same result. Exiting the terminal window, I tried using *System/Administration/Update Manager* - and, it worked!

I'm quite puzzled by this result. My current guess, is that having the Update Manager enabled set a safeguard against manual updating. Can anybody explain my difficulties, or my eventual success? TIA!

---

### Post by androssofer on 2011-08-18
> **scruffyeagle said:**
> I have an installation of Ubuntu v10.04 LTS on a Dell Inspiron 9400. I have 2 profiles set up. One is an Admin, and the other is a non-admin User. I'd logged into the User profile, then tried to do an update using the terminal window. If failed, which I figured was because the User didn't have the rights to do that. I logged out and logged back in as the Admin. I tried it again from there, and was surprised that it also failed from there - and, there was a repeating of these error messages:

E: Could not open lock file /var/lib/lock - open (13: permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?

Then it went to the command prompt. I used exit, then rebooted the computer.

Logging into the Admin profile, I tried it again. Same result. Exiting the terminal window, I tried using *System/Administration/Update Manager* - and, it worked!

I'm quite puzzled by this result. My current guess, is that having the Update Manager enabled set a safeguard against manual updating. Can anybody explain my difficulties, or my eventual success? TIA!

i would get the same error if i had open synaptic package manager, or the software center or was going an apt-get command and i tried to update... where you doing any of those at the time?

---

### Post by Azdour on 2011-08-18
Hi,

You probably did this, but did you run the update command at the terminal via sudo while you where logged in as Admin?

---

### Post by 3rdalbum on 2011-08-18
> E: Could not open lock file /var/lib/lock - open (13: permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?

On Windows XP, the Admin user is virtually all-powerful - they can do anything at all without being prompted for a password or anything.

On Ubuntu, the Admin user is NOT directly all-powerful - they merely have the ability to run commands as 'root', which IS all-powerful. It's basically like a separation of user and administrator, with only one actual account.

If you want to run commands as the all-powerful root, then prefix them with the 'sudo' command:

```
sudo apt-get upgrade
```

The Update Manager uses a more fine-grained set of controls over permissions that doesn't require root.

---

### Post by scruffyeagle on 2011-08-18
> **androssofer said:**
> i would get the same error if i had open synaptic package manager, or the software center or was going an apt-get command and i tried to update... where you doing any of those at the time?

**_androssofer_**: No, I was doing each of these things one at a time, not overlapping.

**_Azdour_**: Yes, I used "sudo" every time.

**_ 3rdalbum_**: Yes, I did that. The command I entered via the terminal was
```
sudo apt-get update && apt-get upgrade
```

One thing I find puzzling, is that even when using "sudo", the system was demanding that I be logged in as root. I haven't set any password for root. In fact, I'm not even sure how to do that. I've been relying on the "sudo" for things that require root powers, when logged in via the profile I've given Admin powers to.

---

