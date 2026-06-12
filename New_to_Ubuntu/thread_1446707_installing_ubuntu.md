---
title: "installing ubuntu"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Marctwane on 2010-04-04
Hi, I tried Ubuntu once as a double boot with Windows Vista when I first built my computer. That didn't work well at all, so I had the Ubuntu removed. Now I want to give it another try. I have added a second hard drive, with a selector switch, to be used solely for Ubuntu. I want to try installing it myself, but would like to see some specific instructions for putting it on a blank HD. Most I have read seem to assume that you are adding it to a HD with Windows on it allready. And what about my motherboard's drivers? Will they have to be added to the new HD? And are their special MB drivers to be used with Ubultu? Help!

---

### Post by uRock on 2010-04-04
First you may want to boot the LiveCD to see how well the release on ubuntu that you want to install works with your system. Once you decide to go forward, the install will go easy when using the full drive. 

When you get to the partitioner you can select to use the full HDD and let the installer make its own partitions, which is the easiest way to install, or you can choose to manually select partitions where you will be able to set up a more robust configuration.

If you decide to create your own partitions, you can make them one at a time and create the following partitions for a happily running system;

1. Partition one will be EXT4, mount point / and between 10 and 15 Gigabytes. This is where the actual operating system will be installed.

2. Partition two will be Linux Swap, which is usually 1.5 times that amount of RAM you have. THe Linux Swap partition acts the same as the Virtual Memory folder does in Windows, which is basically an overflow storage in case you fill your RAM and need extra memory and is also used when Hibernating your system.

3. Partition three should be EXT4, mount point /home and will take up the rest of the space on the HDD. This partition will contain configuration files along with any personal files you store on the system. 

The great part about using the three partition set up is that should you have to reinstall or if you want to use the next release's CD to do a clean install instead of upgrading, you will be able to keep al of our settings and not have to worry about losing personal files, though backups are always good.

As far as mother board drivers are concerned, you do not have to worry about them, the LiveCD has drivers on it for most modern motherboards.

If you'd like to post your system's spec, we can go into more detail on whether or not you may have problems or if you need to download any drivers, which is usually painless.

Cheers,
Ronnie

---

### Post by uRock on 2010-04-04
Here is a screenshot of one of my single boot systems. I have the partitions in a different order, but it doesn't really matter what order you put them in. 

From left to right mine are Swap, /home, and /.

This setup is on an old P4 system and is pretty fast.

Cheers,
Ronnie

---

### Post by Sef on 2010-04-04
Check out the [Illustrated Dual Boot]("http://members.iinet.net/%7Eherman546/index.html").

---

### Post by admldj on 2010-04-05
hi first time user here im thinking of installing ubuntu on my machine sick of vista if i do will i be able to keep my personal files or will i have to do a back up on a removeable drive also i know this is an ubuntu forum but is it really much better than windows? any help would be appreciated

---

### Post by 3rdalbum on 2010-04-05
> **admldj said:**
> hi first time user here im thinking of installing ubuntu on my machine sick of vista if i do will i be able to keep my personal files or will i have to do a back up on a removeable drive also i know this is an ubuntu forum but is it really much better than windows? any help would be appreciated

To the first poster (Marc): When you're installing Ubuntu as the only operating system, it's immediately obvious what to do - there's an option saying "Erase entire disk", which is what you choose.

**Admldj**, this should have gone into a different thread because you're asking a different question. But anyway, there are two ways of installing Ubuntu.

The first is to erase the hard disk and install Ubuntu as the only operating system. This will erase your personal files and Windows.

The second way is to resize the Windows side of your drive downwards (so it no longer takes up the whole drive), and install Ubuntu onto the newly-freed space. The Ubuntu installer can do both of those steps for you, and they do not usually result in any data loss; but you should back up anything that you don't want to lose.

Some people take to Linux really well, they really like it and become passionate about it. Some other people have trouble getting used to the differences, and end off going back to Windows. Ubuntu is very easy to use, but it's so incredibly different to what you may be used to with Windows. I personally think Ubuntu is better than Windows, but you really need to try Ubuntu for a couple of months to see if you like it better.

---

### Post by lisati on 2010-04-05
> **admldj said:**
> hi first time user here im thinking of installing ubuntu on my machine sick of vista if i do will i be able to keep my personal files or will i have to do a back up on a removeable drive also i know this is an ubuntu forum but is it really much better than windows? any help would be appreciated

Installing a new operating system is a big step, and can be daunting for someone who has never done it before. 

It is always a good idea to make a backup of important data, even if you change your mind about installing Ubuntu, just in case something goes wrong. If your computer didn't come with a set of Vista recovery disks, it might be a good idea to make a set - many computers these days come with software installed that can help you with this task.

Ubuntu can be run off CD without actually installing it. This can help you decide if you like it.

---

