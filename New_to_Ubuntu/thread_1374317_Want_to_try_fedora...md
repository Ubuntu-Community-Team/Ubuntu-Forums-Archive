---
title: "Want to try fedora.."
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-01-06
hey there, ive been reading alot about fedora 12 and im curious to try it out, i do not want to lose the data on ubuntu so i will be duo booting. what i want to know is, when installing fedora will i be asked if i want to duo boot with ubuntu or will i have to make a partition for it?. If i decide i like fedora more and i will fully install it over ubuntu. Can i set it to use the same partitions i have on ubuntu [i have /home on its own partition] will i be able to use my /home on fedora so i keep my memory? lastly when i uninstall fedora will do i just delete its partition in Gparted?

Thanks guys.

---

### Post by bodhi.zazen on 2010-01-06
Try the live CD.

If you like it you can install it.

You can share a /home so long as you have a unique user name for Ubuntu and Fedora. If you use the same user name it will not work the way you expect as the system knows you as a number, not a name.

the default UID uid for Fedora is 500, while Ubuntu is 1000

Now you could obviously work around this , but if you are new to Linux you may or may not have problems.

IMO better to use a /data partition, but up to you.

The other problem you may have is I assume you are using ext4 for Ubuntu ? I do not think the Fedora version of grub has yet been patched to boot an ext4 partition directly (you need a /boot), thus you will not be able to boot Ubuntu until you restore grub using your ubuntu /boot partition (which unless you changed it is on / ).

---

### Post by Buuntu on 2010-01-06
If you have just one hard drive, when you install Fedora your grub 2 menu will be replaced with the older grub legacy.  You should still be able to pick what partition you want to boot off of when you power on your computer, but with a slightly different menu.  

If you want to uninstall it, you can just delete it in GParted like you said.  Just make sure your MBR is not pointing to the grub menu from the partition you are going to delete.

To avoid complications if you need to remove Fedora, I would re-install grub 2 from Ubuntu after having installed Fedora.  That will replace the MBR with grub 2 and not give you strange errors when you remove Fedora (since it will be trying to access grub from a partition that doesn't exist).

First though, try the Live CD like bodhi.zazen said.  You can get it from here: [http://fedoraproject.org/get-fedora](http://fedoraproject.org/get-fedora)

---

### Post by -kg- on 2010-01-06
> I do not think the Fedora version of grub has yet been patched to boot an ext4 partition directly (you need a /boot), thus you will not be able to boot Ubuntu until you restore grub using your ubuntu /boot partition (which unless you changed it is on / ).

It has and works fine.  I have Fed 12 installed.

> If you have just one hard drive, when you install Fedora your grub 2 menu will be replaced with the older grub legacy.

No, it won't.  Fed 12 now uses GRUB2.

---

### Post by bodhi.zazen on 2010-01-06
Thank you for the update -kg- , good to know.

---

### Post by Rave Gloves on 2010-01-06
Thanks for the replies (:.  I will try the live CD and see what i make of it.

---

### Post by Guitar John on 2010-01-06
FWIW, a friend of mine who was a long time Fedora user, recently switched to Ubuntu.  [Read why]("http://12stringmusings.blogspot.com/2009/07/hello-ma-buntu-so-long-fedora.html"). 

Not trying to talk you into or out of anything, just sharing some info.

---

### Post by J V on 2010-01-06
> **bodhi.zazen said:**
> You can share a /home so long as you have a unique user name for Ubuntu and Fedora. If you use the same user name it will not work the way you expect as the system knows you as a number, not a name.Ehm... since the folder is titled of the username shoulden't that not matter? Or does linux list its users by ls-ing /home and looking for configuration files?

---

### Post by Zoot7 on 2010-01-06
I'd recommend you give it a shot in a VM. Then decide whether or not you want to install it to hard drive or not.
If/When you decide to install it, just make a partition for it and use Ubuntu's swap partition. You should also be able to use your same home partition for Ubuntu with Fedora too. :)

Fedora is a nice distro and it's generally one of the first to get the newer features and software, plus the repositories are full of stuff. However it tends to be pretty up to date or "cutting edge" and thus you're more likely to run into bugs with it than a more conservative distro. It also tends to be seen or considered as a testbed for Red Hat. Nonetheless, it's a good distro to move onto after Ubuntu.

And yes to uninstall it, you just delete the partition in Gparted. ;)

---

### Post by Buuntu on 2010-01-06
> **-kg- said:**
> 
No, it won't.  Fed 12 now uses GRUB2.
Are you sure?  Just that I recently installed Fedora 12 (about 1-2 weeks ago) and it installed grub 0.97 by default...

---

### Post by bodhi.zazen on 2010-01-06
> **J V said:**
> Ehm... since the folder is titled of the username shoulden't that not matter? Or does linux list its users by ls-ing /home and looking for configuration files?

The system identifies users and groups by number, just as servers are identified by ip address.

With web servers , names are converted to numbers by DNS. With user names, names are converted to numbers by referanceing /etc/passwd and groups by /etc/groups.

If that help you.

So the system sees /home/you as /home/1000 in Ubuntu or /home/500 in fedora.

---

### Post by -kg- on 2010-01-07
> **Buuntu said:**
> Are you sure?  Just that I recently installed Fedora 12 (about 1-2 weeks ago) and it installed grub 0.97 by default...

I have to apologize...Fed 12 does indeed install legacy GRUB.  It *is* patched to recognize ext4 /boot partitions, though.  I couldn't remember, because I've recently installed several other distros.

There's a big debate in the Fed forums about it, but the devs didn't include GRUB 2 in Fed 12 for whatever reason.  I'm going to have to look in the Yum repositories, but I'm not even sure it's available as an option.

If you have GRUB 2 under Ubuntu, though, you don't necessarily need to replace that with the legacy GRUB.  When you install Fed, opt for the manual method and select to install Fed's GRUB in the Fed /root partition instead of the MBR of the drive.  Then boot back into Ubuntu, launch a terminal, and enter:

```
sudo update-grub
```

This will autodetect the Fed installation and include it in it's boot menu.  Of course, every time you update Fed's kernel, you'll have to run this command again, since Fed will not own GRUB in the MBR, but it's not all that bad.

I'm kind of impressed with just this feature in GRUB 2.  Before, you would have to jump through all kinds of hoops to edit the menu.lst so that it would include a new OS or a new kernel.  Now it's just a matter of running the above command and it's all automated.

---

