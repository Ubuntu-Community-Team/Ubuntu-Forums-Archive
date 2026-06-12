---
title: "STFP Install"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by Matuku on 2009-07-30
I just set up Ubuntu Server on an old PC and got SSH working so I can configure it from my main computer; I want to set up SFTP on it so I can transfer files to and from it.

Now, from what I've read all I need is openssh-server, port forward on my router of port 22 and a client that supports SFTP. The ports are all forwarded fine because I can SSH into the server using Putty easily enough. But I try to use Putty SFTP and I enter my server details when it starts up and hit enter and it just sits there for about 30 seconds then the window closes. I also tried Filezilla but the operation keeps timing out. I've made sure the OpenSSH server is running (sshd) but still nothing.

Have I missed something in setting up SFTP? Do I need to something more to enable these clients to connect?

---

### Post by llamabr on 2009-07-30
When you say "main computer" you mean a windows box?

I could never get the putty sftp thing to work either, though I havn't tried very hard.  there are other gui ones that work.  one is called cuteftp.  Another is winscp.

I'm no windows guy, so I can't vouch for either.

---

### Post by Matuku on 2009-07-30
Yeah, it's a windows box that I'm trying to get it to work for atm (haven't even looked at getting it working for my ubuntu side). Just tried WinSCP but that just gave a "Connection Refused" response.

---

### Post by nhasian on 2009-07-30
you can use [filezilla]("http://filezilla-project.org/") to connect with SFTP.

---

### Post by Matuku on 2009-07-30
> **nhasian said:**
> you can use [filezilla]("http://filezilla-project.org/") to connect with SFTP.

I tried filezilla (it's my main FTP client) but it didn't work I just get a "connection timed out".

---

### Post by Matuku on 2009-07-31
*bump* Anyone?

---

### Post by XCan on 2009-07-31
That doesn't make sense. Did you select SFTP/SSH/SSH2 as the protocol in filezilla?

---

### Post by llamabr on 2009-07-31
Right.  If you're getting connection refused, it's not the ftp application, it's the settings of the server.  Can you ssh there?  Also check that the sftp port (22 I think?) is open and not blocked on the server.  This is unlikely, but possible.

---

### Post by Matuku on 2009-07-31
Yep, I selected SFTP as the servertype on Filezilla; also tried FTPES because I set up my vsftpd to work with that. The second one worked but not the SFTP.

I can SSH into it fine (using Putty) and port 22 is being forwarded to the server by the router (otherwise I couldn't SSH in as well).

---

### Post by Matuku on 2009-07-31
Ok WTF; went out so shut my computer down, and when I came back it suddenly works... but I had shut it down last night and it still didn't work this morning... the second reboot seems to have done it...

---

