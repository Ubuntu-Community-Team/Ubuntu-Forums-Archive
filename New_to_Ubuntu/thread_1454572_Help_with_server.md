---
title: "Help with server"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by mroy1300 on 2010-04-14
Hello I am setting up a home file server by following this tutorial [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver) What I need help with is this.

Will this tutorial work for ubuntu server 9.10?

Is there a way to make this setup accessible from outside the network?

Any help would be really great. Thank you!

---

### Post by Boondoklife on 2010-04-14
Alot of the info there is good, but really all you need to do is decide what service you want to share files with. Most people will use both FTP and SMB, FTP for outside of network sharing and SMB for in network sharing.

[HERE]("https://help.ubuntu.com/9.04/serverguide/C/samba-fileserver.html") is some more info on Samba (SMB) file sharing and setting it up.

---

### Post by mroy1300 on 2010-04-14
ok that is all good so I want to run this setup but add FTP. I read somewhere that when you FTP it uses a separate directory and not your directories so for instance my external HDD that i actually want to FTP to is mounted as /mnt/storage how do I access this from outside the network I use filezilla to FTP and putty to SSH.

Also how do figure out my workgroup name on windows xp home?

---

### Post by Iowan on 2010-04-14
It probably won't be long before a Lucid server how-to shows up on howtoforge (if it's not already there somewhere...)

[proftpd]("http://ubuntuforums.org/showthread.php?t=79588")?
[vsftpd]("http://ubuntuforums.org/showthread.php?t=218630")?

---

### Post by Boondoklife on 2010-04-14
Really what is available is all up to you, the best thing to do would be to have one folder for the shared files and then just make that the root for your FTP sessions and Samba shares.

---

### Post by mroy1300 on 2010-04-14
So how do I change the root directory for FTP and Samba? Also how do I access Samba? Does it just show up in my computer as a networked drive?

---

