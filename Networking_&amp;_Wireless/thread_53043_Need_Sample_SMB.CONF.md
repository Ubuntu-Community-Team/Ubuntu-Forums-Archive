---
title: "Need Sample SMB.CONF"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by jlacroix on 2005-07-30
Hi all, I am setting up a server that will host all users home directories. All three Pc's, mine, my wifes and the server are running hoary stable.

I already mounted the home directories with smbfs, and set them as the home directories under my user accounts.

When any logs in, it says the session has lasted less than 10 seconds and says something about permission denied trying to access the .gnome2 folder.

On the failsafe terminal, I can see all the files.

I have two users: 
Jeremy
Krystal

And their home directories on the server are:
/home/homefiles/jeremy and /home/homefiles/krystal

So basically I just need a good smb.conf to make it happen as I am about to throw my server out the window.

Please help!

---

### Post by amohanty on 2005-07-30
If all three have linux why not use the home server as NFS, easier, cleaner.

AM

---

### Post by jlacroix on 2005-07-30
I wouldn't mind it if it would work. I considered NFS first, actually. I couldn't make heads or tails over the howtos though, with the host.allow and host.deny stuff, went right over my head.

If its easier, then I'm all for it.

All I want is that when you log in you are logging into your homedirectory on the server instead of the home directory on the native pc. This possible with NFS?

---

### Post by amohanty on 2005-07-30
Of course. I will hunt down some of my bookmarks and post a link tomorrow...

AM

---

