---
title: "File Sharing between Ubuntu computers"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by levells on 2009-11-08
I'm running Ubuntu 9.04 on my desktop and 9.10 on my laptop. I only just added ubuntu on my laptop, so I want to be able to share the folders from my desktop, like Documents, Videos, etc.
I tried looking around google a bit but most of the information seemed outdated.
Can anyone help me out?

---

### Post by nakama85 on 2009-11-08
> **levells said:**
> I'm running Ubuntu 9.04 on my desktop and 9.10 on my laptop. I only just added ubuntu on my laptop, so I want to be able to share the folders from my desktop, like Documents, Videos, etc.
I tried looking around google a bit but most of the information seemed outdated.
Can anyone help me out?

I am no expert so I wont pretend to be but I hear SSH is the way to go. Perhaps you will find more info searching for that
Edit: Here is the ssh howto: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by bacardiandwatermelon on 2009-11-08
Normally Samba is the way to go when it comes to file sharing, you setup shares on one pc and then access it from another.. But I'm quite a big fan of Giver which is a drag and drop file sharer.. [http://thelinuxmovement.blogspot.com/2007/07/giver-easy-file-sharing-review.html](http://thelinuxmovement.blogspot.com/2007/07/giver-easy-file-sharing-review.html)

---

### Post by Primefalcon on 2009-11-08
> **bacardiandwatermelon said:**
> Normally Samba is the way to go when it comes to file sharing, you setup shares on one pc and then access it from another.. But I'm quite a big fan of Giver which is a drag and drop file sharer.. [http://thelinuxmovement.blogspot.com/2007/07/giver-easy-file-sharing-review.html](http://thelinuxmovement.blogspot.com/2007/07/giver-easy-file-sharing-review.html)
ssh would be the best, then you could just go to

places => connect to server

change the option to ssh and user the ip address of said computer and user and password of account you want to access, and you'll open a graphical window.....

---

### Post by louieb on 2009-11-08
I use NFS - once its setup -  its hard to tell if the shared folders are on laptop or the desktop. 

[HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")  How to is kinda old but it still works. I run Hardy on my desktop and Karmic on my laptop.   Even have it now that Thunderbird email on laptop uses the desktops Thunderbird profile and files.   

ssh is a good way to go to - both are better that samba for linux to linux sharing.

---

### Post by levells on 2009-11-08
> **nakama85 said:**
> I am no expert so I wont pretend to be but I hear SSH is the way to go. Perhaps you will find more info searching for that
Edit: Here is the ssh howto: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
I tried to install the openssh-server but received an error. My terminal output looked like:
Preconfiguring packages...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'postdrop' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

