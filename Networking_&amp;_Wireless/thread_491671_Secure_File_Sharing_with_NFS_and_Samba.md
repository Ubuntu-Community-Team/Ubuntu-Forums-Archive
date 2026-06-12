---
title: "Secure File Sharing with NFS and Samba"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by Nintendud on 2007-07-03
Hello Ubuntu forums!
I have been using samba awhile now to share files easily between my Linux computers and my Windows laptop, and it has been working out wonderfully. I've recently started using NFS to share files between my two Ubuntu Desktops.

However, in August I will be moving to college, along with my laptop and two Linux PCs (yes, they will all fit in the dorm room just fine :) ). I will no longer be in my humble network of four computers, but a college network of thousands of computers. I do not want to risk all of my precious files by keeping insecure Samba and NFS settings!

So, what are your suggestions for sharing files safely on a college campus between your own computers? Please note that I like allowing these three computers write to the shares, since it is very convenient. More specifically, it's very important that my Windows laptop can write to the Linux shares, since I use it to organize my files.

The only things I can think of are:
1. Using a different workgroup than "MSHOME" on the Samba shares (since that is a default option I was too lazy to change) 

-and-

2. Defining, IP by IP, what computers can connect to the NFS shares. 

However, is that enough? My Samba shares do require my username and password.

Also, I apologize ahead of time if this is the wrong place to post this!

---

### Post by trak87 on 2007-07-03
There's a system called sshfs, which is encrypted and will give you write capabilities, but I'm not sure if it will work with Windows:

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)


I've never used tunneling protocols (vpn) but it might be worth a look as well.

---

### Post by Nintendud on 2007-07-03
Well, I would only use that if NFS isn't secure enough, or if NFS is easily exploited...

---

### Post by trak87 on 2007-07-04
In the past NFS was considered very insecure. I think that has changed in the last few years, although I haven't followed the progress.

---

### Post by nocturn on 2007-07-04
If you want to do NFS, look at getting version 4 (preferably with kerberos) working.
[https://help.ubuntu.com/community/NFSv4Howto?highlight=%28nfs%29](https://help.ubuntu.com/community/NFSv4Howto?highlight=%28nfs%29)

---

### Post by Nintendud on 2007-07-04
That sounds like a good idea... thanks for the link!

Now, I need to figure out how to secure Samba...

---

### Post by njparton on 2008-01-04
> **Nintendud said:**
> That sounds like a good idea... thanks for the link!

Now, I need to figure out how to secure Samba...

I'm interested to know what you found out about securing samba - any advice?

---

