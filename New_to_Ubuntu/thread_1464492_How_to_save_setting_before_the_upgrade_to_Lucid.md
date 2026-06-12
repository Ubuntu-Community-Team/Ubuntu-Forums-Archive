---
title: "How to save setting before the upgrade to Lucid?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by Peterfc on 2010-04-28
Hi

I have my machines running good and i would like to keep my setting. Is it possable to save all my Firefox, Thunderbird, My Music, My Pictures, My Documents, My Video etc,and how?   so i can do a clean install.

Thanks

---

### Post by themusicalduck on 2010-04-28
To save all of those things and any other settings that applications have made, you can just make a backup of your home folder (/home/username). All of the configuration files for your user are saved in there in hidden folders.

Sometimes things are saved in the /etc/ file (like software sources, but they would need to be updated after upgrading anyway. Or grub2 custom changes, which you won't need to worry about unless you know of something you have changed specifically to grub)

---

### Post by warfacegod on 2010-04-28
Most of your settings can be found in your Home Folder. They are hidden so hit Ctrl+H. The easiest way is to make a copy of your entire Home folder to some other location and then move it back when you do your install.

If you made a separate /home partition for your current install then you should be fine. Just remember to make it as /home when you do your new install.

I think some of the F.F. settings are in the OS directory but I don't recall where.

Check out Remastersys. It can make a complete system backup. Find a .deb file for it. Its allot easier to install that way.

---

### Post by tica vun on 2010-04-28
No need, just restore your config files from a backup after you install lucid.

You do keep regular backups, right?

---

### Post by lovinglinux on 2010-04-29
> **warfacegod said:**
> If you made a separate /home partition for your current install then you should be fine. Just remember to make it as /home when you do your new install.

+1

> **warfacegod said:**
> I think some of the F.F. settings are in the OS directory but I don't recall where.

Not that I'm aware of. Firefox settings are all stored under FF profile folder (i.e ~/.mozila/firefox/<profile>)

---

### Post by warfacegod on 2010-05-01
Thanks for setting me straight, I wasn't sure.

---

### Post by ssulaco on 2010-05-01
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
grsync is pretty straight forward.....Ive backed up my /home with grsync , but havent had to reinstall it yet.

---

