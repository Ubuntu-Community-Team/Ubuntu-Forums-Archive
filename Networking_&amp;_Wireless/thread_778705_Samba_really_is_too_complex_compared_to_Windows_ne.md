---
title: "Samba really is too complex compared to Windows networking and file sharing"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by whistlerspa on 2008-05-02
I'm unable to set up file sharing in Hardy. I've installed Samba but despite spending a lot of time trying to figure out how to do all the post installation stuff, via referral to forums wikis and Google searches have made no progress. I admit that I'm clueless as to what to do next. 

All the advice regarding creating folders , users , tweaking /etc/samba/smb.conf chmod options and so on has my head in a spin.I couldn't even manage to set up a folder to share as I didn't have the correct  'permissions'. 

I have managed all this in previous distros, which seemed easier somehow, and have been a Linux user for over a decade but can't get it this time around. Is it Hardy or Samba I wonder?

I don't want this to sound like a rant but why do we have to use something as complex as Samba for file sharing and networking in the Linux world. 

It's so difficult compared to setting up file shares and workgroups on Windows boxes. In 2008, I believe it's time there was something simpler to implement- just to share a folder on another box.

In the meantime can anyone point me to a plain English and easy to follow way of doing this stuff please?

---

### Post by Monicker on 2008-05-02
If you received an error after Hardy installed the Samba service, it was probably because of a known issue.

Take a look here:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

Other than having to log out and log back in, I had no problem sharing folder from my Ubuntu 8.04 machine which were accessible from my wife's XP machine.

---

### Post by slimx3m on 2008-05-02
i don't think that it is that complex, it is just more secure

---

### Post by mrsteveman1 on 2008-05-02
The one thing I have noticed with samba is that it is usually necessary to use smbpasswd to add a user before you can do much.

Because there is no 1:1 relationship between NT users and Unix uid they have to be mapped, and there are a number of ways to do this with Samba, but it should work by default as long as you use smbpasswd to add the user first.

This is what i have found to be the root cause of most permissions problems. Samba i believe allows guest access by default even if it isn't specified in the config file, which leads users to think its working until they go to write something or create new files.

---

### Post by StooJ on 2008-05-02
Windows networking and file sharing is for Windows to Windows boxes.

Linux to linux filesharing is very easy too.

It's when you have a cross platform environment that things start to get a bit more complicated.

Here is a great guide for you though: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by mrsteveman1 on 2008-05-02
Actually SMB started life at IBM, Microsoft however merged it with lan manager and a bunch of other stuff.

It works quite well actually especially in relation to NFS, which i hate. Its got some overhead sure but Samba and the various clients for other platforms interact seamlessly with real Windows SMB shares at this point because the samba developers spent so much time on it.

---

