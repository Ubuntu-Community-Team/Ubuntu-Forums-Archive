---
title: "Mounting Samba Shares"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by Striata on 2006-11-29
I am very sorry if this is placed in the wrong category but I was pretty overwhelmed when looking at all the different options and combined with the fact that it's 3am over here at the moment I just snuck it neatly in here.

I just did a clean ubuntu install a few hours ago. I have some experience with Linux and Ubuntu in general already. Now, I installed XMMS to stream my music from my Windows-based network computer. XMMS doesn't support the samba protocol so you have to mount the samba share. I installed the smbfs package to allow this.

The command that I'm supposed to run is:

*sudo mount -t smbfs //FELLESPC /mnt/fellespc/*

(//FELLESPC is the name of the network resource and /mnt/fellespc/ exists)

However, when I run the command I receive the message:

[I]"This command is designed to be run from within /bin/mount by giving
the option '-t smbfs'. "[/I]

I've tried passing the -o parameter with the username and password as well but to no avail. I have googled around to try and find a solution to the problem but nobody seems to be having the same issue. Why does it tell me to use mount -t when that is indeed what I'm using? I've tried so much and it's VERY frustrating not figuring it out.

Thanks very much,
Striata.

PS: I am heading off to bed now. If anybody needs additional information to help me out please let me know and I'll get back to you tomorrow.

---

### Post by Striata on 2006-11-29
OK, I really noticed that this was the wrong forum to post in. Somebody can move this if needed but the issue still remains. :p

---

### Post by xethm55 on 2006-12-02
Please read [http://www.ubuntuforums.org/showthread.php?t=284436&highlight=mounting+samba+share](http://www.ubuntuforums.org/showthread.php?t=284436&highlight=mounting+samba+share)

---

