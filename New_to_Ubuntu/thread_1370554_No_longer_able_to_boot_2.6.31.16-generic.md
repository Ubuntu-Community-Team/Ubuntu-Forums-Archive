---
title: "No longer able to boot 2.6.31.16-generic"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by cpedwards on 2010-01-02
Hi All

I've been using these forums for around 6 months now, and they've proved invaluable on many occasions (thanks guys)! Anyway, I've a problem now and while I've found some potentially useful posts, I'm somewhat at a loss as to best course of action. So to the problem:

I'm running 9.10 and recently updated to kernel 2.6.31-16-generic (using update manager). At first it was fine but yesterday it refused to boot (the logo appears, the splash screen starts (with the progress indicator moving across the screen), then just hangs there before the login screen (the hard disk light stays on) and it justs sits there like that until I force it off by holding the power button for a few seconds. I've retried several times with same result.

I've tried recovery mode, which has let me attempt to fix packages (reported nothing broken), it's run fdisk (?) and the disk appears fine, and lets me log in (in terminal mode - at which point there's not a lot I can do because my linux command line skills are rather limited).

It will boot from a earlier version of the kernel (2.6.31-15-generic works fine, apart from when I have just tried 2.6.31-16-generic recovery mode for some reason).

I'm thinking that if i can remove 2.6.31-16-generic then when I next use 2.6.31-15-generic update manager will create a new 2.6.31-16-generic entry in the grub table, but am (a) not sure how to do this and (b) not sure if there isn't a better way to resolve this?

Other info that may be relevant : install is dual boot with XP on a Dell Inspion 6000 laptop, /home is installed on a separate partion. 9.10 was a clean install following a hard drive replacement.

Thanks in anticipation of your help!

Chris

---

### Post by oldfred on 2010-01-02
I think this is why we like to recommend everyone keep two versions of the kernel in their menu as the old one may still boot.

I have seen several other users with issues with -16 but usually it was immediately on update to -16. I do not remember any fix. 

I am now on Linux 2.6.31-17-generic so you should have another update out there. Try downloading that to see it it works better.

---

### Post by charlier653 on 2010-01-02
Did that to me on initial reboot after update. Initial message was "waking up, please wait. Then nothing. Blank screen, not even so much as a blinking curser. Rebooted, and have "bad environment" error.

Now, mine gets stuck in a loop "checking file system, hit esc to cancel"

Try that on yours. Might work.

---

### Post by cpedwards on 2010-01-02
> **oldfred said:**
> I think this is why we like to recommend everyone keep two versions of the kernel in their menu as the old one may still boot.

I have seen several other users with issues with -16 but usually it was immediately on update to -16. I do not remember any fix. 

I am now on Linux 2.6.31-17-generic so you should have another update out there. Try downloading that to see it it works better.

Thanks for the prompt response! Unfortunately I don't have 2.6.31-17-generic on the grub menu and update manager insists everything is up to date - is there anyway I can force the upgrade either in  2.6.31-15-generic (synaptic manager?) or through the command line using recovery mode in  2.6.31-16-generic?

Thanks agan.

Chris

---

### Post by charlier653 on 2010-01-02
On your update manager, click settings, then add proposed changes.
31-17-generic shows up when you have it check again.

---

### Post by cpedwards on 2010-01-02
> **charlier653 said:**
> On your update manager, click settings, then add proposed changes.
31-17-generic shows up when you have it check again.

Thanks - downloading now!

Chris

---

### Post by Buuntu on 2010-01-02
2.6.31.17 must still be in development stages because I don't have it either.  I would try just uninstalling 2.6.31.16-generic and then let it reinstall it for you.
To do so you can search for the kernel image in synaptic or just run:
```
sudo apt-get purge linux-headers-2.6.31-16*
```When you reboot check for updates and download it manually if needed.

** Didn't see last two posts when I wrote this, you might want to follow their advice

---

### Post by cpedwards on 2010-01-02
> **Buuntu said:**
> 2.6.31.17 must still be in development stages because I don't have it either.  I would try just uninstalling 2.6.31.16-generic and then let it reinstall it for you.
To do so you can search for the kernel image in synaptic or just run:
```
sudo apt-get purge linux-headers-2.6.31-16*
```When you reboot check for updates and download it manually if needed.

Thanks, but I've got 2.6.31.17-generic up and running now so I'll stick with that for now assuming it runs OK (if not I'll purge 2.6.31-16/17 using the code you suggested).

Incidentally the first boot after upgrade to ~17 also hung in the same place as ~16 (and the countdown on the grub menu had disappeared), but the second time it checked the filesystem and booted normally (I've booted again and it seems OK now).

Thanks to everyone, I'll flag this as resolved.

Chris

---

