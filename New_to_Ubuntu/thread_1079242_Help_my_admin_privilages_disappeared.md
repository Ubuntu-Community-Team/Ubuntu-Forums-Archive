---
title: "Help: my admin privilages disappeared"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Jerriy on 2009-02-24
And I dunno the password for the "root shell prompt" (which is accessed via recov. mode) for the purpose of fixing (i.e. restoring) the privileges of my accounts

---

### Post by roccivic on 2009-02-24
AFAIK, if you never set up a password for the root user, you are pretty much screwed. I have done this once last year, installed the system, did not set up a password for root and removed my admin privileges. Ended up reinstalling the OS ](*,)

---

### Post by Jerriy on 2009-02-24
This all means no sudo, no synaptic/add-remove rights... and so on. I just became a guest in my own pc

---

### Post by Jerriy on 2009-02-24
> **roccivic said:**
> AFAIK, if you never set up a password for the root user, you are pretty much screwed. I have done this once last year, installed the system, did not set up a password for root and removed my admin privileges. Ended up reinstalling the OS ](*,)Hehe that seem to be the case. Indeed I have not created a password for it (therefore assumed that there was none) I mean how was I supposed to know that I had to setup a password beforehand? Does Ubuntu assumes that folks are linux gurus by default?

---

### Post by theozzlives on 2009-02-24
Root is disabled by default, for security purposes.

---

### Post by sisco311 on 2009-02-24
By default the recovery mode doesn't ask you for a password.

Did you set up a root password?

try this:[http://ubuntuforums.org/showpost.php?p=6102358&postcount=8]("http://ubuntuforums.org/showpost.php?p=6102358&postcount=8")

---

### Post by Jerriy on 2009-02-24
Does the installation of the OS offer an option whether the user root may or may not have a password (i.e. during the installation proces)? I don't even remember any more what happened when I installed the whole thing

---

### Post by Jerriy on 2009-02-24
> **theozzlives said:**
> Root is disabled by default, for security purposes.That may or may not be the case here but how does one know?

---

### Post by Jerriy on 2009-02-24
> **sisco311 said:**
> By default the recovery mode doesn't ask you for a password.

Did you set up a root password?

try this:[http://ubuntuforums.org/showpost.php?p=6102358&postcount=8]("http://ubuntuforums.org/showpost.php?p=6102358&postcount=8")Good idea - I'll try that

---

### Post by sisco311 on 2009-02-24
You can also use the live cd to add your user to the admin group.

Boot the live cd, mount the root partition and edit the /etc/group file. 

If you need step by step instruction, then boot the live cd and post the output of: ```
sudo fdisk -l
```

---

### Post by Jerriy on 2009-02-24
No need for that Your first advise worked perfectly - thank you so much!

---

### Post by Jerriy on 2009-02-24
But I have a follow up question sisc: what should I do with the default 'root' user? Give it a password or not? I just noticed in (via "User settings") that the root user can't be deleted unlike my other users...

---

### Post by theozzlives on 2009-02-24
> **sisco311 said:**
> By default the recovery mode doesn't ask you for a password.

Did you set up a root password?

try this:[http://ubuntuforums.org/showpost.php?p=6102358&postcount=8]("http://ubuntuforums.org/showpost.php?p=6102358&postcount=8")

Yeah I di all on my own. (I'm not a very secure individual)

---

### Post by Jerriy on 2009-02-24
Oops - also noticed that the root user can't be accessed from the graphical interface

---

### Post by lswest on 2009-02-24
You can't ever delete the root account, but if you don't give it a password it is effectively disabled, so just keep that setup and you should be fine.

Also the GDM disables the root account for logins until specified otherwise.  Useful security features.  I recommend [setting up a password for GRUB]("http://ubuntuforums.org/showthread.php?t=7353") to prevent people from accessing the recovery terminal, since it should give you root access without prompting for a password.

That's all I'd recommend doing, and if you don't want to do so, that would be fine too, entirely your choice.

---

### Post by Jerriy on 2009-02-24
> **lswest said:**
> You can't ever delete the root account, but if you don't give it a password it is effectively disabled, so just keep that setup and you should be fine.

Also the GDM disables the root account for logins until specified otherwise.  Useful security features.  I recommend [setting up a password for GRUB]("http://ubuntuforums.org/showthread.php?t=7353") to prevent people from accessing the recovery terminal, since it should give you root access without prompting for a password.

That's all I'd recommend doing, and if you don't want to do so, that would be fine too, entirely your choice.Thanks for clearing that up. But me thinks that I need to setup a password for the root user so that I can access the root from the "root shell prompt" option on the recovery *menu* (as opposed to just accessing the recovery *mode*) am I correct?

---

### Post by sisco311 on 2009-02-24
> **Jerriy said:**
> But I have a follow up question sisc: what should I do with the default 'root' user? Give it a password or not? I just noticed in (via "User settings") that the root user can't be deleted unlike my other users...

If for some reason you have enabled your root account, disable it:
```
sudo passwd -l root
```
If the root account is disabled(no password is set),
then the recovery mode should not ask you for the password.
This is the default behavior in Ubuntu. 

Use sudo/gksu to run applications as root.

Learn more about sudo:
[uhelp]community/RootSudo[/uhelp]
[thread=716201]New forum policy on log-in-as-root tutorials[/thread]

---

### Post by Jerriy on 2009-02-24
> **sisco311 said:**
> If for some reason you have enabled your root account, disable it:
```
sudo passwd -l root
```
If the root account is disabled(no password is set),
then the recovery mode should not ask you for the password.
This is the default behavior in Ubuntu. 

Use sudo/gksu to run applications as root.

Learn more about sudo:
[uhelp]community/RootSudo[/uhelp]
[thread=716201]New forum policy on log-in-as-root tutorials[/thread]Disabling it was my intention. But I was wondering whether that means that the "Drop to root shell prompt" option that appears when you choose a recovery mode is also disabled?

---

### Post by sisco311 on 2009-02-24
> **Jerriy said:**
> Disabling it was my intention. But I was wondering whether that means that the "Drop to root shell prompt" option that appears when you choose a recovery mode is also disabled?
Once again, if the root password is disabled, you can access the "root shell" in recovery mode without being asked for a password.

---

### Post by Jerriy on 2009-02-24
Got it! ](*,) I've just done that. Thanks for helping. Viva Steaua!

---

### Post by albinootje on 2009-02-24
> **Jerriy said:**
> And I dunno the password for the "root shell prompt" (which is accessed via recov. mode) for the purpose of fixing (i.e. restoring) the privileges of my accounts

Use the recovery mode if you didn't set a password for root.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you did set a password for root before and you don't remember it, then boot from the Ubuntu installation cdrom, use the live session, then mount your real Ubuntu / partition, after that use the "sudo chroot mountpoint" syntax to "enter" your / partition, and type : "passwd root" to reset your root password.

---

### Post by Jerriy on 2009-02-24
Bedankt albinootje ;) maar tis al opgelost (de allereerste suggestie van sisco311 (recovery *terminal*) heb ik grprobeerd en het was meteen gelukt)

---

### Post by albinootje on 2009-02-24
> **Jerriy said:**
> Bedankt albinootje ;) maar tis al opgelost (de allereerste suggestie van sisco311 (recovery *terminal*) heb ik grprobeerd en het was meteen gelukt)

Ah, mooi zo :)
Glad to see the problem was already solved. 
Hopefully some time in the future we will get back the thread "SOLVED" button (I assume that it is still disabled?).

---

### Post by Jerriy on 2009-02-24
Done that also (hmmm so I see... it's up to the thread starter to add "solved" in the title. Phew! Never before in the history of ubuntukind has one learned so much thanks to so many in so few minutes

---

