---
title: "Help setting up a media server"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2011-01-15
I've got a computer laying around that I want to install ubuntu on and use it as a media server.  After initial setup I'm not planning on having keyboard/mouse/monitor connected to it.

I'm planning on the server hosting a variety of files for my whole family, but also being used to stream media to an xbox 360 for our tv.  From what I've been reading it sounds like I'm looking for either mediatomb or fruppes for the streaming portion of it.  I think I'd also like to handle file transfers through an FTP server, as that seems like the most reliable way for some of our older windows computers to access the server.

So the question I have is, is there a way to make it so that fruppes or mediatomb (whichever I go with) as well as an FTP server will start as a service with the computer and not require the system to be logged in?  If not, should I setup the computer to auto-log in to a username and not require the password and all that somehow instead?  Also, what FTP server software would be best to use?  On windows I've used filezilla server for years, but I'm not really sure what the best choice would be to use over here.  The FTP will be exposed to the internet, so it would be best if it wasn't something that was hard to secure.

---

### Post by Brandon Williams on 2011-01-17
I don't use either fruppes or mediatomb, but [here](https://help.ubuntu.com/community/MediaTomb) is an old how-to about mediatomb in the commmunity docs. It looks like mediatomb runs as a service with a standard install (i.e. no login required).

For file transfer, I suggest you avoid FTP. Use ssh instead. You can perform file transfers with sftp. Just install openssh-server and you're ready to go. There is ssh software available for any version of Windows that you might still be running on the client machines (e.g. putty).

If any of this is accessible via the internet, you should use non-standard ports. It won't help if a serious hacket decides to try to break in, but it will foil the script kiddies.

---

### Post by scared0o0rabbit on 2011-01-19
One of the things I like about ftp in windows is that I can setup an ftp to basically work almost exactly like a network folder.  Are you aware of any way to have windows explorer do this?  For most of the users I'd want it to be a seamless experience in windows explorer, I'd rather they didn't have to open a separate program.

---

### Post by scared0o0rabbit on 2011-01-19
One of the things I like about ftp in windows is that I can setup an ftp to basically work almost exactly like a network folder.  Are you aware of any way to have windows explorer do this?  For most of the users I'd want it to be a seamless experience in windows explorer, I'd rather they didn't have to open a separate program.

---

### Post by scared0o0rabbit on 2011-01-19
One of the things I like about ftp in windows is that I can setup an ftp to basically work almost exactly like a network folder.  Are you aware of any way to have windows explorer do this?  For most of the users I'd want it to be a seamless experience in windows explorer, I'd rather they didn't have to open a separate program.

---

### Post by Brandon Williams on 2011-01-21
This isn't really the right forum for getting information about how to do things in Windows. I tried google for you and found [this possible solution](http://superuser.com/questions/67551/mounting-ssh-sftp-shares-on-windows-7). Unfortunately, the goals of security and ease-of-use often conflict, so I wouldn't be surprised if you can't find a method that's quite as simple as ftp would be.

---

### Post by Paqman on 2011-01-21
> **scared0o0rabbit said:**
> One of the things I like about ftp in windows is that I can setup an ftp to basically work almost exactly like a network folder.  Are you aware of any way to have windows explorer do this?  For most of the users I'd want it to be a seamless experience in windows explorer, I'd rather they didn't have to open a separate program.

Why not just use Samba?

---

### Post by scared0o0rabbit on 2011-02-01
> **Brandon Williams said:**
> This isn't really the right forum for getting information about how to do things in Windows. I tried google for you and found [this possible solution](http://superuser.com/questions/67551/mounting-ssh-sftp-shares-on-windows-7). Unfortunately, the goals of security and ease-of-use often conflict, so I wouldn't be surprised if you can't find a method that's quite as simple as ftp would be.

Yeah, that's why I was thinking of sticking with FTP.  I mean nothing really critical is going to be there, and I don't expect to become the target of anyone, so alternate ports with passwords is probably enough.

So back to the question(s) I still have:

Which ftp server would people recommend?  I notice in the repositories it recommends you don't run plain vanilla ftpd.  It suggests vsftpd, proftpd, and pure-ftpd.  I'm not super concerned about the security, so perhaps someone can give me some tips on which to choose based on this info:

-It needs to be able to run without a user logged in (I suspect all 3 can do this)
-I'm thinking I may want to make it so that the server isn't accessible from the internet, so I'm thinking I'd like to be able to filter IPs using a whitelist.
-Preferably, I'd like it if it was extremely easy to setup.  I'm not totally opposed to editing config files, but the less of that I have to do the better.

The network this will be on is less than 10 computers, and will have maybe 5 users, so ease of use over mega reliability is probably the way I'm leaning.  Any suggestions would be most helpful.

---

### Post by scared0o0rabbit on 2011-02-01
> **Paqman said:**
> Why not just use Samba?

Historically, my family can't ever seem to make all their windows pc's talk to each other as it is.  I gave up on windows file sharing years ago and have been using FTP in it's place ever since.  I've recently started using windows 7 on occasion, and noticed it works better, but half the pcs on the network are xp still.

---

### Post by sdowney717 on 2011-02-01
[http://minidlna.sourceforge.net/](http://minidlna.sourceforge.net/)

I have used this and it worked very well and easy

---

### Post by taseedorf on 2011-02-02
use ushare for the sharing of files to the xbox 360

Samba for sharing with windows machines

---

