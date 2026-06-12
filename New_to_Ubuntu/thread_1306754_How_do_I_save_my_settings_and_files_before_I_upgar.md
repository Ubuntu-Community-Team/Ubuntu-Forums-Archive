---
title: "How do I save my settings and files before I upgarde?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by kapi on 2009-10-30
Whats the best advice you can give regarding backing up my settings and upgrading to 9.10

I also use LAMP and php which took me ages to get going.So I'm a bit concerned that I will spend the next month installing codecs and other stuff. Can't really afford to waste any time. just want to install and go like the upgrade for 9.04 ( which is really good)

any suggestions would be very welcome

---

### Post by mlentink on 2009-10-30
Most applications store their configs in hiudden files in your home directory. That's why I have a separate /home partition. If you back up your home directory that's a start.
But I doubt whether all of your Apache and MySQL configs are stored there (I'm suire they're not) So in you case I'd back up the whole disk, check your backup, recheck your backup and then take the dive and do the upgrade. 
The only reason I did not do so this time is that I got myself a new machine. Previously, I've done upgrades from Dapper to Jaunty, wihtout problems I didn't cause myself...

So relax a bit. It's really pretty safe to upgrade. Al lot safer than with that other OS, if you aks me...

---

### Post by akelsall on 2009-10-30
Kapi, I'm sure others can add to this, but I'd start by backing up the following files:

> 
$HOME/.bashrc 
$HOME/.bash_aliases 
/boot/grub/menu.lst
/etc/resolv.conf
/etc/fstab  [B][COLOR="Blue"](you'll want a hardcopy of this to use during the upgrade stage)
[/COLOR][/B]
/etc/network/interfaces
/etc/dhcp3/dhclient.conf 

If you don't have a separate $HOME partition, you'll want to backup any files in your $HOME partition you can't afford to lose. 

> If you're running VirtualBox, be sure to back up the following:

/etc/vbox/interfaces
/etc/udev/rules.d/20-names.rules
Your primary .vdi file (that holds all the info needed about your virtual machine(s)

Any programs you installed yourself. For example, here are a few I had to manually re-install:
[INDENT][INDENT]
amarok 
imagemagik 
gparted 
bootchart 
filelight 
ntfsprogs 
[/INDENT][/INDENT]


That should get you thinking about some things you want to backup.  Good Luck!

Andy

---

### Post by ranch hand on 2009-10-30
The upgrade from Jaunty to Karmic is pretty rough right now.

The best thing you can do, if you are having no problems with your system right now, is leave the bugger the way it is.

Jaunty has another year of support.

---

### Post by kapi on 2009-11-01
Thanks guys, i appreciate your support. I think for now I'll stay with jaunty for next couple of months.

This may sound stupid but what is the best way to back up in Ubuntu and is there a way I can transfer all the settings from one OS to the next?

I am not sure how to make a separate $home folder and use that . . .sounds ideal though. 

Thanks for your help

kapi

---

### Post by ranch hand on 2009-11-01
When I install I create my partitions first and write down the numbers so I don't screw up.

I have no idea how large your drive is but I like a root (/) partition of no less than 10Gb and a home partition (/home) of no less than 20Gb.  These sizes are what I like and are by no means mandatory,  I have 8.10 running on an old box that has a 10Gb HDD.

When you install (clean install from CD) and the partitioner comes up, choose manual, and then designate the partitions that you want the / and /home installed on.

---

### Post by slakkie on 2009-11-01
Ubuntu uses roughtly 4-6 GB on a default install. Add some space to accommodate your distribution upgrades and I would advise anything between 8-10GB for a root filesystem (/). I have 3 (x8GB) now, 1 Ubuntu, 1 Debian, 1 Misc

1 GB swap.
Then I add /var/log of about 300-500M
And I have a /opt of about 2GB (applications compiled from source which run under Debian/Ubuntu, etc etc)
And then I have a /home which takes the rest.

You can use clonezilla to backup your files. Has helped me in the past!

---

### Post by kapi on 2009-11-01
Could you tell me, is there a step by step guide for partitioning the way you described?

I am a bit of a novice and feel a little overwhelmed. How does making partitions help me save my existing data?

---

### Post by slakkie on 2009-11-01
Well, a different slice for your /home is always best, since it will keep user data seperate from OS data. Within companies/school these homedirs are often stored on the network. Making a seperate backup of your /home is often crucial. I backup my /home via clonezilla, and I make rsync backups to a remote disk. 

My OS is only backed up one via clonezilla. A reinstall is quick and I have always 2 backups from clonezilla, so if one fails I have another, or run another OS all the same.
 
I have /var/log and /opt seperate because I run a multiboot system. So all my Debian/Ubuntu installs use the same /var/log and /opt.

If you want a multiboot system the following will be different, but ask if you want to know.

You can partition with gparted (installed on Ubuntu liveCD and has a seperate liveCD), or with the tools delivered by the Ubuntu installer. Use which you prefer.

* Remove all partitions from your disk (delete them!)

Some people put their swap first, then their root slice, which ever you prefer.

* Create your root, size is somewhere between 8-10 GB.
* Create your swap, anywhere between 1/2GB (I have 1GB RAM, and 1 GB swap, if you have more RAM you might want to have .5 GB of swap, or none - whatever you prefer).
* Create a seperate slices for /opt, /var/log or whatever (OPTIONAL)
* Create your home slice, make it as big as you want

Now you can easily reinstall another OS on your root, without impacting your data in /home.

---

### Post by kapi on 2009-11-01
Sorry but I'm still lost.

So let me see. . . First I want to save my settings from the home folder so that when I upgrade I will keep things as near as possible to what I had previously in jaunty.

How do I do that?

Next I want to create a partition for a home folder apparently but am not sure how to do this, when I am to do it and what to do when it comes to upgrading to 9.10.

This is what I mean 

I take it that copying my home folder to an external drive and doing a clean install of 9.10 and then replacing the new home folder with the copy would not work?

So much to do - so little time . . .thanks for your patience

---

### Post by HermanAB on 2009-11-01
Uhmmm, most Linux problems are caused by upgrades.  So the best advice is: Don't fix it if it ain't broke.

That being said, if you do want to do upgrades regularly, ensure that you have a separate /home partition.  That way you can re-install and keep all your data - provided of course that all your data is actually saved in /home.  As for Apache, all the config files are in /etc/httpd and the data is in /usr/local/www (or something similar), so save those.  i usually make a complete backup of /etc:
tar -zcvf etc.tgz /etc

That way I can always go back and see what the settings were before.

---

