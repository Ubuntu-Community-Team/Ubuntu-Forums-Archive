---
title: "Won't Boot?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by ken0069 on 2010-01-15
OK so I pulled a second hard drive out of my computer that was a multiboot system with Windows and Ubuntu 9.10 and now Ubuntu hangs at the Grub screen and when I hit enter for it to go ahead and boot it shows the first splash screen then video goes off and it just sits there doing nothing?  I can connect that second drive back up and it will boot but it won't boot with it disconnected?  WTF is it with this?](*,)

---

### Post by Cabs21 on 2010-01-15
sounds like your Boot layer is on that first drive that you removed.

---

### Post by kansasnoob on 2010-01-15
> **ken0069 said:**
> OK so I pulled a second hard drive out of my computer that was a multiboot system with Windows and Ubuntu 9.10 and now Ubuntu hangs at the Grub screen and when I hit enter for it to go ahead and boot it shows the first splash screen then video goes off and it just sits there doing nothing?  I can connect that second drive back up and it will boot but it won't boot with it disconnected?  WTF is it with this?](*,)

Boot your Ubuntu Live CD and then follow these instructions to post the output of the Boot Info Script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by ken0069 on 2010-01-16
> **Cabs21 said:**
> sounds like your Boot layer is on that first drive that you removed.

 Shouldn't be because Ubuntu was installed without any other drive connected.  The Windows drive was disconnected during the install to prevent any grub crap from being install on it, been there, done that with Fedora, or was it Suse?    The Windows drive was disconnected the other day to do updates on Ubuntu, which was to include a 2.0 grub update.  Before the update was started I disconnected the Windows drive to prevent it from being written too but now Ubuntu won't boot without the other drive present?  As I said, the grub window comes up with the top line blinking, hit enter, it goes to the first Ubuntu splash screen and then the screen goes blank and nothing else happens.  So are you telling me that my Windows drive now has grub on it anyway?  If so, then how do I remove that? 8-(

---

### Post by steveneddy on 2010-01-21
During the install of Ubuntu you tell the installer which hard drive to install Grub to.

Referring to all the software you are trying to install as "crap" in every post or thread you start will make users that usually help new users asking for help pass you by in the future.

Settle down, take a breath and simply try to follow the instructions correctly, the first time, and you will be a happier Linux user.

And yes, it sounds like the boot sector is on the second drive.

If you removed the first drive during the install process, there is a boot sector on the first drive and now a boot sector on the second drive.

computers don't like two boot sectors very well. If you had left the HD's in the machine and simply let Grub do it's job, most of your issues would disappear.

Grub will not harm a Windows installation, and the 

```
fixmbr
``` 

command in windows will restore a windows boot sector in no time.

---

### Post by ken0069 on 2010-02-14
OK so I've got three computers that are multi-boot systems.  I guess what I need to know is how to make Ubuntu boot when a Windows drive is removed without having to reload them all?  This is especially important as one of these computers has 5 operating systems on it and you know how Window is prone to anything and everything bad on the internet.;)

---

