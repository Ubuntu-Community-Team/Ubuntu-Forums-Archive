---
title: "console from Windows"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by lulon on 2007-12-19
Hi!!

I want to access to Ubuntu from Windows. People have recommended me to install Samba, but it's not what I need, because with Samba I can only share files.

I want to access to Ubuntu with a user and a password, and run a console from Windows for run commands, like I was in the computer with Ubuntu.

I don't know if you understand me, sorry I'm not English speaker.

I have a computer with Ubuntu and Apache Tomcat (with jsp and servlets), and one database. This computer works like a Server.
I have other computer with Windows and I want to run a console to modify, create, etc files in the Server, stop and restart the Server, etc.

Thanks a lot.

---

### Post by reckless2k2 on 2007-12-19
i think you mean you want to install putty on windows. then you can ssh into your ubuntu box as long as you have ssh installed on that windows box. 

now if you want to have the ubuntu desktop on your windows box, you will need cygwin or other similar programs to give you an X server on windows. i use xwinlogon.

---

### Post by lswest on 2007-12-19
if you want a bash terminal in windows cygwin is the way to go.

---

### Post by timcredible on 2007-12-19
if you want to access your machine as though you're in front of it, you want to run xdm remotely.  i have an article about that [here.]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27")

---

### Post by Junglizer on 2007-12-19
> **timcredible said:**
> if you want to access your machine as though you're in front of it, you want to run xdm remotely.  i have an article about that [here.]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27")

Thats good, but I think lswest was on the ball with this one, since they only want to be able to start/stop services, and do mostly CLI stuff anyways, PuTTY is the way to go. Just be sure to have sshd running, for best results, don't allow root login over ssh, and block everyone but use the /etc/hosts.allow file to only let specific IP's access it. 

[Download PuTTY here]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")

[If you've never used it before, here is the Wikipedia entry]("http://en.wikipedia.org/wiki/PuTTY")

---

### Post by lswest on 2007-12-20
lol no matter how much i'd like to claim that that idea came from me, it didn't.  I suggested cygwin so he can install & run some linux commands & programs in a bash from windows, and reckless suggested PuTTy (which was the reason i didnt suggest that lol)

---

