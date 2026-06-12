---
title: "What's the limit you can do to your system without being root?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by BKbroila on 2010-10-10
I hope I have the phrasing correct: what's the most 'damage' you can do to your system (linux obviously) without being root? From what I've read, users should run Ubuntu in/as Sudo. 

I was just wondering what I could possibly do to harm my computer as Sudo.

Thanks

---

### Post by andrewthomas on 2010-10-10
The same damage you would do as root.  

Just one step at a time.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by iponeverything on 2010-10-10
> I was just wondering what I could possibly do to harm my computer as Sudo.

The administrative user using sudo can do anything a user running as root can.

---

### Post by yetiman64 on 2010-10-10
> I was just wondering what I could possibly do to harm my computer as Sudo.sudo plus the right command (which, if posted here, would have me booted off the forums [--read this link--]("http://ubuntuforums.org/announcement.php?f=326")) equals total system annihilation.
A user's sudo password is how to elevate processes to root privileges as has already been noted.
Also,> Just one step at a time. _ sometimes one step is all that is needed :lolflag: as I've found with some rather painful personal experience with Linux (prior to using Ubuntu thankfully.)

Without using sudo (note that the "root" user account in Ubuntu is disabled by default, unlike a lot of other Linux distros), your damage potential in the system is pretty much reserved to folders in your ownership (in particular your home folder). Having said this most users would generally regard their private files as important (remember to do backups :))

The link in andrewthomas' post #2 is good info for understanding sudo and its use (link #4 in my sig is the same page :)).

---

### Post by sanderj on 2010-10-10
> **BKbroila said:**
> I hope I have the phrasing correct: what's the most 'damage' you can do to your system (linux obviously) without being root? From what I've read, users should run Ubuntu in/as Sudo. 

I was just wondering what I could possibly do to harm my computer as Sudo.

Thanks

You say "users", so plural. AFAIK, this is the sudo information on Ubuntu:
- the one account that was created during install, can do 'sudo' and thus do anything.
- other accounts, created afterwards, can NOT do 'sudo', as their account does not exist in /etc/sudoers. As the normal users can not sudo, they can only harm their own directory and the can *read* other directories (including other users' directories ...).

---

### Post by iponeverything on 2010-10-11
> - other accounts, created afterwards, can NOT do 'sudo', as their account does not exist in /etc/sudoers. As the normal users can not sudo, they can only harm their own directory and the can *read* other directories (including other users' directories ...).

The cute "Users and Groups" GUI will allow you to create as many administrative users as you like. It is just that the first account created during the install defaults to administrative, subsequent ones do not.

---

