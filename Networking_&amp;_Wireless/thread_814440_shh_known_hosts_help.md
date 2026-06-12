---
title: "shh known hosts help"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by nothingspecial on 2008-05-31
I`ve done a clean Gutsy install on my pc where I keep all my media files. In doing so I seem to have messed up ssh. I can connect from the laptop to the pc but not the other way round. If I try to connect using the terminal I get -


@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
blahblahblahblah...........................
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:1
RSA host key for my-desktop has changed and you have requested strict checking.
Host key verification failed.


If I try to connect using places>connect to server I get - 


Can`t display location "sftp://me@my-desktop/"
Host key verification failed

Where do I find the key?
Which machine`s /root/.ssh/known_hosts file am I adding the key to?
How do I fix this.
Many thanks to anyone who can help me with this.

---

### Post by holiday on 2008-05-31
The file is in ~/.ssh. Its name is known_hosts. 

Try this:

- open a terminal window (applications.accessories.terminal on your main menu) and type in this:

cd ~/.ssh
ls

You have changed to your personal hidden ssh configuration directory and requested a listing of the files it contains. 

You want to edit one of those files so type this:

vi known_hosts

vi is one of the unix constants. If you find yourself on any but the most weird unix system you will find vi, and if you know vi you'll find yourself at home. There are some vi variants but you can google your way if you know about uname.

vi will display the trusted hosts file. The file is divided into lines so that if you maximize your window you will see how the gobbledee-gook is listed in lines. 

The error you're reporting shows that line 1 of that file has a suspicious key. Unless you're working in a bank or for some other organization who might put you in jail for losing money or giving away secrets, just go ahead and delete that line. To delete it, type d.

d will delete the line at the cursor, and since you've just opened the file you're on line 1. Lucky.

type :wq

The colon tells vi you're going to type a command, and the wq tells vi to write the file and quit.

You're done. Try the connection now. If it doesn't work, I'm sorry.

---

### Post by nothingspecial on 2008-05-31
No luck I`m afraid. Many thanks for helping.:KS

---

### Post by jac0117 on 2008-10-21
Hey "holiday", your directions worked perfect for me.  Thanks.

---

### Post by powerslave12r on 2008-10-25
> **holiday said:**
> The file is in ~/.ssh. Its name is known_hosts. 

Try this:
.....
Hey thanks, this solved it out for me too.

---

### Post by nilgiri on 2009-03-27
Great help for me too!  I have been fighthing with this since switching to Ubuntu.  Until I read this thread, it never occurred to me that ```
Offending key in /root/.ssh/known_hosts:1
``` was indicating the line number on the end.  Of course!

---

### Post by Francewhoa on 2009-06-26
Same here. I found a solution on this post: [http://ubuntuforums.org/showpost.php...9&postcount=10]("http://ubuntuforums.org/showpost.php?p=7521619&postcount=10")

---

