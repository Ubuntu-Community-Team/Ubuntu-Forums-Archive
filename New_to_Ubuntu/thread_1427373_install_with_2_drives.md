---
title: "install with 2 drives"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Cuban Eight on 2010-03-11
I have a PC with 2 hard drives on and wanted to install ubuntu on one and leave windows on the other but the ubuntu installer ignores the spare drive and wants to install itself on the same drive as windows, I had to disable the drive with windows on to get ubuntu to install on the other drive.
Is there any way to get it to use the other drive as there is no dual boot option if I disable the windows drive to get it to install on the other one.

---

### Post by audiomick on 2010-03-11
You might have more luck with the alternate CD. I didn't do a dual-boot, but did have the problem that the graphic installer (liveCD) didn't see both of my drives.

The alternate CD uses a different partitioning tool which seems to be able to find drives that the graphic installer can't. The problem is not unkown on the forums, and most people seem to be successful with the alternate CD.

---

### Post by undecim on 2010-03-11
If you've already got the new drive installed, then you can set up the Ubuntu drive to boot first (either by setting it up in the bios, or making sure that it's plugged into the slot on your motherboard that is booted first.

Then, log into your Ubuntu install, open a terminal and run "sudo update-grub"

That should find windows and let you choose which OS to use on boot.

---

### Post by Cuban Eight on 2010-03-11
I have looked at the ubuntu Alternative download options but did not see anything like an 'alternate CD'
My BIOS does not have any options for specifying which drive boots first, they are both sata drives and it does not seem to make any difference which way they are plugged in.
And you totally lost me with "log into your Ubuntu install, open a terminal and run "sudo update-grub""

---

### Post by SecretFace on 2010-03-11
hmmm, Thats weird. I have two drives also in my case and have a fresh Ubuntu 9.10 on the first drive...the second drive has a fresh install of windows xp.  I was able to choose which drive to install Ubuntu on.

---

### Post by Cuban Eight on 2010-03-11
I'm afraid I am giving up on ubuntu, I have been looking at the version I managed to install on it's own and almost the first thing I got was a pop-up thing saying "you do not have permission to........" this was one of the things that really annoyed me about recent versions of windows. The last thing I expected was the MS type thought police to be appearing. Remembering all the hassle you have bypassing this type of thing in windows just put me completely off, I thought you were supposed to have a lot more freedom with linux, I don't want to be dictated about what files etc. I try to look at on my own PC.

---

### Post by philinux on 2010-03-11
> **Cuban Eight said:**
> I have a PC with 2 hard drives on and wanted to install ubuntu on one and leave windows on the other but the ubuntu installer ignores the spare drive and wants to install itself on the same drive as windows, I had to disable the drive with windows on to get ubuntu to install on the other drive.
Is there any way to get it to use the other drive as there is no dual boot option if I disable the windows drive to get it to install on the other one.

Manual partitioning option from the installer after scanning disk drives is completed.

---

### Post by philinux on 2010-03-11
> **Cuban Eight said:**
> I'm afraid I am giving up on ubuntu, I have been looking at the version I managed to install on it's own and almost the first thing I got was a pop-up thing saying "you do not have permission to........" this was one of the things that really annoyed me about recent versions of windows. The last thing I expected was the MS type thought police to be appearing. Remembering all the hassle you have bypassing this type of thing in windows just put me completely off, I thought you were supposed to have a lot more freedom with linux, I don't want to be dictated about what files etc. I try to look at on my own PC.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cuban Eight on 2010-03-12
Using 'sudo' sounds worse than 'taking ownership' of folders in Windows but in addition to that, in the hour or so I was looking at ubuntu I came up with quite a list of problems/annoyances, for instance, before I decided to try ubuntu I read that the linux install was very configurable but ubuntu offers very few options, it could certainly do with some control as it installed a pile of software that is of no interest to me.
And it still seems I can't install it to dual-boot with windows on the drive of my choosing.

---

### Post by 3rdalbum on 2010-03-12
> **Cuban Eight said:**
> Using 'sudo' sounds worse than 'taking ownership' of folders in Windows

I'm going to give you some hard love here.

If you don't like that your default user account doesn't have the ability to modify system files in Vista/7 and Linux, then my only advice to you is to Get Used To It. All operating systems are moving this way, and for good reason.

This is about protecting YOU from viruses and malware. If you have full permissions over your computer by default (like Windows XP), then ANY program that gets remotely attacked will have the ability to completely hose your computer, or install malware. It also means that other people with user accounts on the computer can also be spied upon, if you have full permissions.

Ubuntu's limited permissions system is easy once you get used to it, and it's not restrictive to the administrator. It's so simple: If you want to change anything that will affect other users (for instance, installing software or modifying system files), then you need to do it as 'root'. On Ubuntu, this involves running the program using the 'sudo' command. For certain programs that only work as 'root', Ubuntu will run them as root automatically (like Synaptic Package Manager) once you have provided your password. The password prompt prevents malware or remote attackers from being able to gain root permission.

So... if it's in your home directory, it's "yours". If it's outside your home directory, then it belongs to root, and you just need to switch to root using the Sudo command.

> but in addition to that, in the hour or so I was looking at ubuntu I came up with quite a list of problems/annoyances, for instance, before I decided to try ubuntu I read that the linux install was very configurable but ubuntu offers very few options, it could certainly do with some control as it installed a pile of software that is of no interest to me.

Some distros give you a very frugal install, with a desktop and almost nothing else. Some go overboard with multiple web browsers and silly frills like icon editors. Ubuntu gives you a small selection of "best of breed" software to get you started. If you want to remove any of it, be my guest. And if you want to install any more software, then go for it, it's your computer.

Some software in the default install will tell you that it will remove the "ubuntu-desktop" package, if you remove that software. Don't worry about this, it will not remove your GUI desktop or uninstall Ubuntu. The ubuntu-desktop package does not actually contain anything.

> And it still seems I can't install it to dual-boot with windows on the drive of my choosing.

You were given this answer, which I'll explain: "Then, log into your Ubuntu install, open a terminal and run 'sudo update-grub'"

Log into Ubuntu. When your desktop appears, go to the Applications menu, then Accessories, then Terminal.

Copy and paste in the following:

```
sudo update-grub
```

You will be asked for your password; type it in and press Enter (nothing will be displayed while you type). Reboot and you should be able to choose to boot into Windows.

Normally when you install Ubuntu you can choose what disk you want to use. I'm surprised it didn't give this option when you installed it.

---

### Post by Cuban Eight on 2010-03-12
Thanks for all (or maybe some) of that, as I said in a previous reply the 'sudo' things went right over my head and the info I was pointed to seemed about as clear as mud, I was initially just wanting to get a feel for ubuntu but I seemed to getting straight into a steep learning curve, I had tried the live CD but that did not seem to give a true picture as it was so incredibly slow.
I had not wanted the ability to, or tried to modify system files, I had merely clicked on a few folders in a file manager when I started getting all the 'you do not have permission' messages, surely all that is not necessary if you are just looking.
I thought I would give linux another try and am just in the middle of installing 'Mandriva' which is looking a lot more promising so far.

---

### Post by philinux on 2010-03-12
The livecd of any distro runs completely in system ram. Thats why it's slow. It has to decompress everything from the cd. 

It quite a feat to get a full OS to run this way. Windows or macos cant do it.

---

