---
title: "/home partition?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-11-11
I've read up on some things regarding installation in the past couple of months. Actually skimmed would be a better word. I see that a nice thing to do is to have separate /, /home/, and /swap partitions. I've set up both my laptops this way. 

Hypothetically when I upgrade to a new version of Ubuntu how do I transfer the /home I saved to the new install? I'm also wondering if my codecs etc get transferred over with it...or do I have to reinstall those. Those slow server speeds sometimes make the experience like "watching paint dry."

---

### Post by fargle on 2009-11-11
Assuming you do a full "reformat" upgrade, just be careful in the partitioner to designate your /home partition to mount there and NOT to reformat it and you'll be good.  Having said that, it's always good to have a current backup of your /home in case you make a mistake.

Occasionally I've seen issues with your "dot files" in your home directory and the settings they contain causing problems with new versions of software in the new distribution - if that happens just move the config files for that app to, say, ".mozilla.hold" and restart the app, you'll lose your settings for that app.

Codecs and such are stored in the system partitions, so yes, you'll have to reinstall those with this method.

Finally, if you just do an upgrade-in-place, then none of this applies!

---

### Post by konqueror7 on 2009-11-11
what is stored in the /home is mainly personal configuration files, simply copying them again inside your home would do the job. and, regarding codecs and other applications, they won't be included since they are stored mainly in /usr and /bin. what you can do is backup all your currently installed application list and save it into a file, and use that file as a source to install all the programs again.

---

### Post by kansasnoob on 2009-11-11
First of all know your partitions by number (ie: sda1, sda2, etc), and also what file system type is currently used (ie: ext3 or ext4). The command "sudo fdisk -l" may help you figure that out, but if you need some help just ask here at the forums.

Anyway I love pictures so I stole some from Herman's Illustrated Dual Boot Guide:

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

Basically when you get to this screen:

[ATTACH]135749[/ATTACH]

Choose **Specify partitions manually (advanced)**, then when you get to this screen;

[ATTACH]135751[/ATTACH]

Select your / partition. You do want to format that one! Next select your /home partition you DO NOT want to format that one! Look below for what that screen looks like:

[ATTACH]135752[/ATTACH]

So, to recap, your existing / partition you'll select:
Use as: either ext3 or ext4 (your choice)
Format the partition: Yes, check the box.
Mount point: /

But your existing /home you'll select:
Use as: **Use the same file system type! Changing it could result in data loss!** 
Format the partition: **NO! Do not check the box!**
Mount point: /home

You don't need to do anything with swap because it's already swap.

Clear as mud?????????

---

### Post by kansasnoob on 2009-11-11
BTW always create a backup of anything important!

And you get to review your selected changes here:

[ATTACH]135755[/ATTACH]

That's your last chance to change your mind!

---

### Post by Zoot7 on 2009-11-11
Generally my preferred option is to install the new version of Ubuntu by telling it to just fill the empty space on my hard drive which I allocate for it beforehand. Then install all my applications I want to use, and only then activate my /home partition, by simply renaming the home directory, making a new one and specifying in fstab to mount the old home partition again.
Not sure whether it works better or not this way.

---

### Post by emeraldgirl08 on 2009-11-11
Okay so basically the /home file is basically the documents, pictures, videos, music, and downloads we find in Places right???

I don't keep anything really in any of those folders. If I download something I direct the download to an SDHC or CF card I have. I don't like filling up my hard drive with all kinds of stuff. I made a /home partition that would at least hold a temporary file for when I transcode a video etc. That gets deleted as soon as I am done burning my project.

As far as programs like K3b, Pidgin, etc those are in the / folder right?

---

### Post by Miljet on 2009-11-11
You are on the right track. But your /home folder also contains your configurations for all the applications that are installed elsewhere (Firefox, K3b, Pidgin, etc). Think about it this way, if there are two or more users on the computer, each user might want Firefox configured differently. Therefore each user will have their preferences stored in their respective /home directories.

These configuration files are normally hidden. You can view them by using Places to show your home directory. Click on View and then "Show hidden files".

---

### Post by emeraldgirl08 on 2009-11-12
> **Miljet said:**
> You are on the right track. But your /home folder also contains your configurations for all the applications that are installed elsewhere (Firefox, K3b, Pidgin, etc). Think about it this way, if there are two or more users on the computer, each user might want Firefox configured differently. Therefore each user will have their preferences stored in their respective /home directories.

These configuration files are normally hidden. You can view them by using Places to show your home directory. Click on View and then "Show hidden files".

TY. I forgot there was hidden folders! Now that I viewed them I see the configs folders for Mozilla and the other programs I have installed on my laptop.

Wow. I've still got quite a bit to learn. Thanks again!

---

### Post by Zoot7 on 2009-11-12
A separate home partition contains all your documents and settings for pretty much all your applications. It means you can re-install your OS with your home partition, and have it stay pretty much the same as it was.

---

