---
title: "Installation with separate partitions"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Andy06 on 2009-01-19
I read quite a bit about people having different partitions for /,/usr, /boot,/var, /temp , /home.

Can someone please give me a full list of possible separate partitions and why it is necessary/desirable to create separate ones for each.

I always have a separate Data partition (for Docs, Pics, Music, Videos and Downloads) that I can read from any OS, so that substitutes for having a separate /home I guess. Currently whenever I install ubuntu for myself or someone else I always use the default 2 partitions, / and Swap.

Also on the above mentioned default setup, can I somehow save my programs and settings if I want to start a new install from scratch? [perhaps by copying the entire home directory elsewhere or using a back up program?]

Thank you very much

---

### Post by stefangr1 on 2009-01-19
> **Andy06 said:**
> 
Can someone please give me a full list of possible separate partitions and why it is necessary/desirable to create separate ones for each.


No, that's impossible as the number of possible separate partitions is infinitely large. For a regular desktop (for a server it's a bit different), a few things to consider:

/boot on it's own partition is practical when you have a multiboot system with different distro's.

/var can be on a different partition for security reasons: failure can cause log files to fill the disk and stop the system.

/ and your data on different partitions is practical in case you need to reinstall, then you won't have the backup but can just install over the old / partition.

---

### Post by RyanVanDiemen on 2009-01-19
I`m using only /home and / as a seperate partitions (I have an additional HDD for movies, music and other stuff formatted as NTFS to be accessible for win). It`s good to have /home as a separate partition so you don`t have to copy/backup all the stuff you have in your home directory when you re-install the system. Although whenever I re-install the system I don`t use home folders from older installations because it just never works 100% for me and I`d like to have my new installed system clean if you know what I mean. I always create new home directories and just move the stuff I want to keep from older home dirs.

---

### Post by Andy06 on 2009-01-19
> No, that's impossible as the number of possible separate partitions is infinitely large

I understand, I meant for the commonly used ones. Specifically why would you have separate partitions for:

/
/boot
/home
/var
/tmp
/usr
/etc

Is it merely a carry over of linux geeks setting up server in the above fashion for bullet proof security and organisation and then carrying over the same good habits to desktop or is there a more utilitarian reason:)

From what I gather, its all unnecessary (good and excellent habit, gives safety margin) but unnecessary. The reason I need to know is I am going to be installing on dozens of student comps and want to do it right.

The data partition is always separate so user files will be saved anyway. Other settings like Ryan said don't always work 100% so it's better to back up program settings individually (eg compiz). So ultimately all I need to create are the default /, swap and Data partition or is there a very good reason for why I should read more and ensure that I go the whole nine yards.

So far I have this:

/boot: Unnecessary because will be booting a single distro along with windows at most from the same HD

/home: Unnecessary because is redundant (for data) and doesnt work very cleanly (for settings) like Ryan explained

/var: Stefan explained but this sounds more like a rigorous habit for IT admins and advanced users than a need for casual/home/desktop use.

/tmp,/usr,/etc?

---

### Post by stefangr1 on 2009-01-19
For /tmp more or less the same holds as for /var. Some processes could generate a lot of temporary data, thus filling up your disk. /usr /etc aren't a problem.

However, I wouldn't worry about partitioning at all. As you said, if you make a separate partition for the data, one partition for / will do fine.

---

### Post by driven1 on 2009-01-19
Don't mean to hijack this thread, but I did a reinstall that created a new "/home" directory in the same partition as the "/" rather than use the "/home" directory I had in a separate partition. How can I move it back?

---

### Post by stefangr1 on 2009-01-19
> **driven1 said:**
> Don't mean to hijack this thread, but I did a reinstall that created a new "/home" directory in the same partition as the "/" rather than use the "/home" directory I had in a separate partition. How can I move it back?

Changing this back would require some knowledge about fstab, and it is somewhat dangerous since if something goes wrong and the system can't find the user folders, the gui won't work. So, maybe you should consider to stay with the situation as it is now...

First step would be to create a new partition, and format it ext3 (using gparted or another partitioner).
You make a directory to mount the new partition in and change ownership:
sudo mkdir /media/home
sudo chown -R <yourname> /media/home

In your /etc/fstab, you add a line with:
/dev/sda#   /media/home  ext3  defaults  0  2

Now you reboot, and then you verify that the new partition is indeed mounted.
give the command df and verify if the new partition shows up as it should. 

Next step is to copy everything from the old to the new home partition:
sudo cp -a /home/. /media/home/.

change /media/home to /home in your fstab

and you delete everything in your old /home:
sudo rm -rf /home/*

When you reboot this time, you should have your home directory on a separate partition.

---

### Post by jakupl on 2009-01-19
@Andy06

If you don't have a clear idea of why you want separate partitions for stuff, then it will only make life worse for you.
For normal school desktops, I wouldn't bother, except a maybe a separate partition for music, documents and stuff, if it is dual booting with windows.



@driven1

Naah, If you already have a /home Partition, than you don't need to do all that. Just do the fstab stuff.
This site helped me alot when I did it for the first time. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
It explains how to make a completely new /home partition, however you don't need that.

The next time you do a reinstall, choose manual partitioning... or something like that. It will give you the option of telling it which partition to use as /home. It,s pretty user friendly.

---

### Post by egalvan on 2009-01-19
Some links that may be of interest to folks...


[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/c23.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/c23.html)

[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

Happy reading!

ErnestG

---

