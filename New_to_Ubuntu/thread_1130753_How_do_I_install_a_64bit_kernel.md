---
title: "How do I install a 64bit kernel?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-20
Hi

I built a Hardy Ubuntu machine on a 32 bit platform with an i386 kernel. I then changed the motherboard to an AMD 64bit architecture and simply used the same hard drive with Ubuntu installed. It worked.

However, I am now having problems with Skype on the machine (no or garbled sound) and would like to try the 64bit Skype which I know works fine on my other AMD 64bit machine. If I try to download the Skype 64bit version it reports incompatible architecture.

How do I change the i386 kernel to an AMD64 kernel whilst preserving my home directory and have everything running ok?

---

### Post by nandemonai on 2009-04-20
I'm 99% sure you'll need to reinstall with a x86_64 ISO as it's not just the kernel that is 64 bit but all the binaries and libs as well.

Obviously backup all your data first though :)

You can safely move your /home/ data back into the new install.

---

### Post by Paqman on 2009-04-20
> **nandemonai said:**
> I'm 99% sure you'll need to reinstall with a x86_64 ISO

I'm 100% sure :)

---

### Post by bwallum on 2009-04-20
Ok so it's a rebuild. Can I just save the 'home' directory to preserve data? One thing that comes to mind is the .evolution configuration files with contacts etc. If I save that directory from the 32bit system will it work ok in the 64bit version? There are a number of others such as .openoffice. Will these work saved from the 32bit and copied over to the default 64bit? I guess I could survive with just the .evolution files if push came to shove.

---

### Post by Paqman on 2009-04-20
> **bwallum said:**
> If I save that directory from the 32bit system will it work ok in the 64bit version? 

Yep, they're just text and xml files. Totally portable between systems. Make sure you save all the hidden folders, but you seem to know where to find those since you mention .evolution and such. 

If you've got multiple users on your system you might want to make sure the right user has ownership of the files after you copy them onto the new setup. If it's a single-user system that's highly unlikely to be a problem.

---

### Post by fballem on 2009-04-20
> **bwallum said:**
> Ok so it's a rebuild. Can I just save the 'home' directory to preserve data? One thing that comes to mind is the .evolution configuration files with contacts etc. If I save that directory from the 32bit system will it work ok in the 64bit version? There are a number of others such as .openoffice. Will these work saved from the 32bit and copied over to the default 64bit? I guess I could survive with just the .evolution files if push came to shove.

Actually, when you're running Evolution, you can backup your e-mails, calendars, preferences, and accounts by running File > Backup Settings ... from the menu and follow the prompts. Copy the resulting file to an external drive (the file may be quite large).

When you re-install (using the 64-bit ubuntu) and start Evolution for the first time, you will see an option to restore from backup. Select this option and browse to your backup (that's on the external drive).

The first time you do a Send/Receive, you will have to provide the passwords for your accounts. Other than that, everything else will be there.

Hope this helps,

---

### Post by gn2 on 2009-04-20
> **bwallum said:**
> Ok so it's a rebuild. Can I just save the 'home' directory to preserve data? One thing that comes to mind is the .evolution configuration files with contacts etc. If I save that directory from the 32bit system will it work ok in the 64bit version? There are a number of others such as .openoffice. Will these work saved from the 32bit and copied over to the default 64bit? I guess I could survive with just the .evolution files if push came to shove.

**[COLOR="Red"]Before attempting any of this it is essential that you back up any files you wish to keep to separate media, e.g. DVD or external hard drive.[/COLOR]**

Yes that can be made to work.
Do you have a separate /home partition in your existing 32-bit installation?
If you do, just install 64-bit using the same username and password, select manual partitioning and retain the /home partition.

The next suggestion is one I have seen suggested elsewhere, I haven't tried it myself, but I see no reason why it shouldn't be able to work.

If you don't have a separate /home partition, boot a live CD and delete everything apart from /home then copy the entire contents of /home (including the all important .hidden files and folders) to / 
Next, resize the partition down to leave room for a new / partition and install 64-bit using manual partitioning and mount the old / partition (containing all your old /home config) as /home

---

### Post by bwallum on 2009-04-20
I have a /home partition in filesystem under root as default installation. What do you mean by 'separate' and if I install 64 bit at what stage will I be prompted to keep the existing /home partition?

I like the idea of simply installing 64bit from a cd and leaving the /home partition intact. That would do it for me.

---

### Post by ushills on 2009-04-20
Personally I would create a seperate /home partition and move the home folder there.

See this guide

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then using the information here ([http://www.ushills.co.uk/2008/02/backup-and-restore-installed.html](http://www.ushills.co.uk/2008/02/backup-and-restore-installed.html))create a list of your installed packages.

Now reinstall 64bit ubuntu, don't reformat the /home partition and it will keep your /home after install.

Then reinstall the packages using the above guide.

I did this myself earlier this month.

You will end up with a 64bit OS with all the applications and settings as before you upgraded.

---

### Post by Paqman on 2009-04-20
> **bwallum said:**
> 
I like the idea of simply installing 64bit from a cd and leaving the /home partition intact. That would do it for me.

If you /home is mounted on a separate partition, then that's easy. You'd know if you machine was set up that way, because you'd have had to do it manually when you originally partitioned.

Alternatively,it's also pretty easy to just back up your /home and then copy it back after installing, providing you've got enough backup storage.

---

### Post by zvacet on 2009-04-20
You can run 32 bit Ubuntu on 64 architecture.That is not problem.Only thing I can think of for using 64 is ram.If you have more then 4GB of ram then 64bit is way to go even you can tweak your 32 bit to use all ram.if you still want to reinstall follow advices about making separate home partition.

---

### Post by Slim Odds on 2009-04-20
> **Paqman said:**
> I'm 100% sure :)

Well... I'm 110% sure!! :KS

But, as some others have said, your config files are text/xml etc.

I have always kept my /home on a separate partition. I recently moved from 32 to 64 bit and had no issues. Just reinstalled and mounted that partition as /home.

---

### Post by stchman on 2009-04-20
> **bwallum said:**
> Hi

I built a Hardy Ubuntu machine on a 32 bit platform with an i386 kernel. I then changed the motherboard to an AMD 64bit architecture and simply used the same hard drive with Ubuntu installed. It worked.

However, I am now having problems with Skype on the machine (no or garbled sound) and would like to try the 64bit Skype which I know works fine on my other AMD 64bit machine. If I try to download the Skype 64bit version it reports incompatible architecture.

How do I change the i386 kernel to an AMD64 kernel whilst preserving my home directory and have everything running ok?

Yes, you will need to download the AMD64 version of Ubuntu.  A complete reinstall will be necessary.

---

### Post by bwallum on 2009-04-21
Thanks to you all, I've just learnt that it is best to keep /home on a seperate partition.

Bonus thanks to nandemonai for first response, paqman, fballem, gn2 and Ushills for the links and that little bit of extra knowledge and Silm Odds and stchman for confirmation.

The 32bit OS does indeed run on AMD 64bit hardware, thanks to zvacet for pointing that out.

The 32 bit OS machine will be upgraded once I've sorted out moving /home to a new partition on my machine. Perhaps this should be the default for a new installation? I've bought an external hard drive to make sure nothing is lost.

EDIT: Ouch, be very careful!

I decided to put my/home directory on a new internal harddrive. I used gparted and called the partition /dev/sdc1. I copied my /home directory on to it. Perfect at that point.

I then used a live cd to remove my /home directory on my startup partition (/dev/sda1)

I then added a line to my /etc/fstab file```
# /dev/sdc1
/dev/sdc1	/home	ext3	nodev,nosuid	0	2
``` so that the new harddrive would be mounted when the machine next booted.

Then the problems started with .dmrc and .ICEauthority warnings and the system refused to boot. Recovery mode failed too. I restarted with a live cd, ran ```
chown -R bob:bob /home/bob
```and checked all the above, then shut down and rebooted from the harddrive.

It worked....but all of my configuration files including emails, browser bookmarks, openoffice templates etc were lost. Somehow all my dot files in my new /home directory had been replaced with default settings. The loss of all emails and contacts was particularly painful.

BEWARE.... Make sure you save all your dot configuration folders separately to an external source that can be disconnected from the system before you try this.

On the upside I now have a very quick system with the security of having all my stuff on a separate hard drive. All of my Documents, Music, Pictures, Videos survived thankfully.

---

