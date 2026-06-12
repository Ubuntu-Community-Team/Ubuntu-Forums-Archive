---
title: "2 ubuntu machines on connected to the same router."
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by xl_cheese on 2007-07-23
One is connected wireless the other wired.

How can I make them fully shared to each other?  

Well, I guess the first step is how can I share a single folder?

The both have samba.  I went to shared folders and played with that, but the two computers can't see each other?

Any help would be appreciated.  Or a link to the right thread.

thanks.

---

### Post by t4thfavor on 2007-07-23
Don't forget to set the samba password.
Type Alt+F2 and then smb://ip_address_of_sharing_pc

it should ask you to log in, Do so, then browse to the correct share.

If you are using linux on both machines, why not use NFS?

---

### Post by newlinux on 2007-07-23
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_folders_the_easy_way)

may help

---

### Post by xl_cheese on 2007-07-26
I must be an idiot.

I cannot make it work?:confused:

Any other ideas?

---

### Post by newlinux on 2007-07-26
what did you do and what errors are you getting? can you ping both computers from each other?

---

### Post by xl_cheese on 2007-07-26
On each computer:

I right clicked the folder and clicked share folder.  NFS allowing the  ipaddress between the opposite computer and the router.

Only problem is on one computer there is no option for nfs.  Only has the windows network option.

I can go to network tools and ping each computer.

---

### Post by newlinux on 2007-07-26
So no errors or anything? You may want to try mounting them commandline.

---

### Post by xl_cheese on 2007-07-26
> **newlinux said:**
> So no errors or anything? You may want to try mounting them commandline.

how do I do that?

Really, I shouldn't have to.  

Does anyone know why one of my computers does not give me an option for a linux network?  Only a windows one.

---

### Post by buntunub on 2007-07-26
Ok this is just too easy. Try this how to

[http://ubuntuforums.org/showthread.php?t=430312&highlight=wireless+disconnects](http://ubuntuforums.org/showthread.php?t=430312&highlight=wireless+disconnects)

Took me all of about 15 minutes to get this setup and running. Samba flat out SUCKS! Dont even bother with that trash imo. sshfs gives you super fast and secure file mounts. Follow the guide about 3/4 down the page to setup shared rsa keys too. Anyway, it sucks being a linux nub at first but you get the hang of it. Hang in there!

---

### Post by newlinux on 2007-07-26
> **xl_cheese said:**
> how do I do that?

Really, I shouldn't have to.  

Does anyone know why one of my computers does not give me an option for a linux network?  Only a windows one.

Instructions for how to do it are in the link I provided you in the earlier post. 

No, you shouldn't have to, but there are some advantages to mounting. You can set it up permanently and to any directory you want and some applications won't be able to access the files without mounting them.

Sshfs mounting works fine as well, although I believe the file transfer rate may be slower.

---

### Post by xl_cheese on 2007-07-27
I didn't realize, but both my computers had the same machine name...  I think that threw a wrench in the spokes.

---

### Post by newlinux on 2007-07-27
yeah, that could cause some problems.

---

