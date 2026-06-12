---
title: "How to install FTP on my Ubuntu box?"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-09-10
How can I install an FTP server on my Ubuntu box? I'm creating a LAN network with 4 virtual machines and I'd like to have an FTP so all the other machines on the network can access files.

All of the machines can ping each other as of now, I just need to install the FTP server.

Is there a complete step by step guide to install one? I don't need any fancy configurations just a typical anonymous usage account, some folders to be accessed be certain users and of course how to set the default FTP folder.

Thanks!):P

BTW I'm an old user here so I'm not just a hit it and quit it guy. I like this place. :)

---

### Post by HermanAB on 2010-09-10
Howdy,

Both vsftpd and proftpd work out of the box. Simply do apt get proftpd and it should be up and running.  Problems start when people change the configuration from the default, so most every FTP howto guide is bad news for a beginner...

---

### Post by papuccino1 on 2010-09-10
So which one should I install?

---

### Post by perspectoff on 2010-09-10
I like Filezilla. time honored. Stable.

sudo apt-get install filezilla

Ooops, sorry. you said FTP server. I agree with the post above.

Also consider setting up WebDAV folders.

---

### Post by ks07 on 2010-09-10
> **papuccino1 said:**
> So which one should I install?
If you've set up apache before, I'd recommend proftpd - it uses a similar kind of setup. However, by the looks of things it doesnt really matter. One thing to have in mind is that vsftpd is in the main repo - so it should receive security updates more regularly than other daemons.

---

### Post by stmiller on 2010-09-10
Be careful - ftp is not secure. The username and password are sent in plain text across the internet. 

Instead, you can simply create a regular user/password on your Ubuntu box then start ssh server.

```

sudo apt-get install openssh-server

```

Then users can connect via sftp (secure ftp) instead of ftp.

---

### Post by Jeroensum on 2010-09-11
> **papuccino1 said:**
> How can I install an FTP server on my Ubuntu box? I'm creating a LAN network with 4 virtual machines and I'd like to have an FTP **so all the other machines on the network can access files.**

All of the machines can ping each other as of now, I just need to install the FTP server.

Is there a complete step by step guide to install one? I don't need any fancy configurations just a typical anonymous usage account, some folders to be accessed be certain users and of course how to set the default FTP folder.

Thanks!):P

BTW I'm an old user here so I'm not just a hit it and quit it guy. I like this place. :)

Sounds to me like you just want to share some files, why not use NFS?

---

### Post by hhlp on 2010-09-11
read this how to :

[https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html")

---

