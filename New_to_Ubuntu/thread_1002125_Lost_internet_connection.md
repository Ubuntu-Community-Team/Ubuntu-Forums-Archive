---
title: "Lost internet connection"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by SANDKON on 2008-12-04
Ubuntu 8.10 on external hard disk. Dual boot. I was de-installing some applications via package manager and I seem to have deleted network manager as I can no longer get access to internet and the icon that appeared which showed me connected to the intenet has now disappeared. Problem is that I can't re-install the missing packages as under ubuntu I have no internet connection. Help!!!

---

### Post by Michael.Godawski on 2008-12-04
Do you have perhaps access to a wired connection?
Try to download the deb from here from another machine:
[http://ppa.launchpad.net/network-manager/ubuntu/pool/main/n/network-manager-applet/](http://ppa.launchpad.net/network-manager/ubuntu/pool/main/n/network-manager-applet/)

Perhaps you can install it from the Live CD too. Just add the cd to the sources, run  ```
sudo apt-get update
```, and ```
sudo apt-get install network-manager
```

---

### Post by SANDKON on 2008-12-04
Will try as suggested. Must log out of windows and back into ubuntu to give it a go. Will let you know. Thanks.

---

### Post by SANDKON on 2008-12-05
couldn't get into ubuntu. Booted as normal and loaded kernel but after just had blank screen. Drive was still working as it was making sounds but even after 1 hour ubuntu did not launch. I have live cd. Can I repair using this?

---

### Post by Michael.Godawski on 2008-12-05
> I was de-installing** some applications **via package manager and I seem to have deleted network manager

A broken network manager alone  cannot be responsible for a failure at start up. Can you remember what else you have deleted? Did you try to boot into Ubuntu after the Network Manager stoped working or is this the first time you tried it?

No error messages during the booting process?

---

### Post by SANDKON on 2008-12-05
I had installed digikam ( a kde application) and I didn't want it so I had to remove it through synaptic package manager. I was deleting all the packages which were marked for KDE as I have the gnome default desktop. I think I must have deleted things which were necessary. I don't remember what I deleted. Is there no way to see what the missing packages are? I also removed items from the residual config section. I have truly made a mess! There are no error messages at boot up. It loads the kernel but nothing else appears and the screen shows the message "out of range".  I have used live cd and it shows all my files but I didn't do anything in case I make the situation worse.

---

### Post by SANDKON on 2008-12-05
I did boot after deleting files and then once more with the live cd.

---

### Post by SANDKON on 2008-12-07
Still no luck with this problem. I can't get into ubuntu. Have tried to reinstall ubuntu from live cd onto the external hard disk where the original ubuntu is but the there is always a problem at the partition stage. I'm afraid that Ubuntu is losing a supporter. Can it be so difficult to repair?

---

### Post by pp. on 2008-12-07
> **SANDKON said:**
> Still no luck with this problem. I can't get into ubuntu. Have tried to reinstall ubuntu from live cd onto the external hard disk where the original ubuntu is but the there is always a problem at the partition stage. I'm afraid that Ubuntu is losing a supporter. Can it be so difficult to repair?

Given that the installation of Ubuntu takes rather less than a hour, you might want to reflect on the best course of action for your particular situation.

Also, randomly removing packages is a nice way to render your system useless. That is one thing that's the same in most OSs: you also can render Windows useless by randomly removing stuff.

---

### Post by SANDKON on 2008-12-07
> **pp. said:**
> Given that the installation of Ubuntu takes rather less than a hour, you might want to reflect on the best course of action for your particular situation.

Also, randomly removing packages is a nice way to render your system useless. That is one thing that's the same in most OSs: you also can render Windows useless by randomly removing stuff.

Yes, I have learnt that the hard way. But it still doesn't help me to state the obvious. If I get ubuntu working again and stick with it I'll make sure I'm more careful with the package manager. But after all this thread is asking for help to find a solution. Thanks

---

### Post by ugm6hr on 2008-12-07
> **SANDKON said:**
> Can it be so difficult to repair?

Yes. Without knowing what the problem is.

Can you go to a command line interface with a wired connection?

Have you tried to enter the Grub menu and select the "Recovery" boot option with a wired connection?

If so. *sudo apt-get install ubuntu-desktop* may be enough to repair the situation.

Otherwise, a fresh reinstallation is in order.  make sure you have backed up all necessary files before going any further though.

I see you have tried a fresh reinstallation already: exactly what problem have you had with partitioning at that stage?

---

### Post by pp. on 2008-12-07
> **SANDKON said:**
> this thread is asking for help to find a solution. Thanks

Please excuse me for stating the obvious.

I think the most straightforward solution consists of:
- Copying the contents of /home to another media
- Re-installing Ubuntu from scratch
- Restoring /home

BTW, I seem to remember seeing some Linux distros which offered to 'repair an installed system' as an option on the liveCD. Doesn't Ubuntu do that?

---

### Post by ugm6hr on 2008-12-07
> **pp. said:**
> BTW, I seem to remember seeing some Linux distros which offered to 'repair an installed system' as an option on the liveCD. Doesn't Ubuntu do that?

The Alternate CD may well be able to do that, essentially by acting as a repository to reinstall the ubuntu-desktop package.

Don't think the LiveCD does it though.

---

### Post by SANDKON on 2008-12-07
Probably the easiest is to use the alternate cd to fix the installation? Or could the problem be with GRUb?

---

### Post by ugm6hr on 2008-12-07
> **SANDKON said:**
> Probably the easiest is to use the alternate cd to fix the installation? Or could the problem be with GRUb?

It is not Grub.  If it was, you would not be able to boot at all.

If you can get to the Gnome desktop, then yes, try using an Alternate CD.

If not, then re-install.

---

