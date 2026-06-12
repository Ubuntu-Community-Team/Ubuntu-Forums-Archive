---
title: "Proftpd"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by string on 2006-11-10
Hey, I got a prob with my proftpd. I use Edgy. I installed Proftpd and left default settings. I forwarded port 21 in my router on my ip. When I use my ftp locally (from localhost or other machines of the network) it works fine.
But problems comes up when I use ot from the internet : I manage to log in (it throws me if I use a bad password so the connection is real), I can do CWDs (cd in yafc) as much as I want : it changes only when the directory exists so it means that the client is really connected.
But it fails any time I do put, get or ls (I'm talking in yafc commands, but their meaning are obvious) : it does nothing (no error message) until it timeouts (connect() failed it says).
The /var/log/proftpd/proftpd.log gives no valuable information (its content is the same as when I connect locally and it works).

---

### Post by lloyd_b on 2006-11-10
It's a firewall issue.  The FTP protocol initially connects on port 21, but when you execute a command that involves a data transfer (put, get, ls), it opens a connection on another port, and the data is sent via that connection.

Something is blocking that second connection.

A question: Are you using "active" FTP (the PORT command), or passive FTP (The PASV command).  What you will need to do depends on which you are using.

Also - when you mention "connecting from the internet", could there be another firewall (besides your router) between you and the FTP box?  If so, it could be the source of the problem.

For a good explanation of the difference between passive and active FTP look [here]("http://slacksite.com/other/ftp.html")

Lloyd B.

---

### Post by string on 2006-11-10
To be perfectly honest it worked until I installed my router (linksys WRK54G).

I don't know what I use (active or passive) but I didn't change a thing.

There cannot be any firewalling problem from the internet as it used to work before the router came up.

I know the problem must be solvable from the router, but don't know how.

If you have ideas, please...

Thanks, you've been helpful already.

---

### Post by lloyd_b on 2006-11-10
By default, those "extra" connections use ports starting at 1024.  Try forwarding ports 1024 thru 1060 to that machine, and see if that helps.

Note: Depending on your machine's configuration, once a port has been used, it may be a certain amount of time before it can be re-used.  So if you're transferring a large number of small files, and it acts flaky after so many files, then you need to open up more ports.....


Lloyd B.

---

### Post by string on 2006-11-10
Thanks, Ill try as soon as I get home. But, it's a bit weird isn't it ? not being able to guarantee such server working no matter what ?

---

### Post by dannyboy79 on 2006-11-10
> **lloyd_b said:**
> It's a firewall issue.  The FTP protocol initially connects on port 21, but when you execute a command that involves a data transfer (put, get, ls), it opens a connection on another port, and the data is sent via that connection.

Something is blocking that second connection.

A question: Are you using "active" FTP (the PORT command), or passive FTP (The PASV command).  What you will need to do depends on which you are using.

Also - when you mention "connecting from the internet", could there be another firewall (besides your router) between you and the FTP box?  If so, it could be the source of the problem.

For a good explanation of the difference between passive and active FTP look [here]("http://slacksite.com/other/ftp.html")

Lloyd B.

I don't believe this is the issue, I have a Netgear NAT router/firewall and all I have forwarded is port 21 and mine works fine. I have noticed that when it connects it does say it's using passive mode within the log using filezilla. This is what it states:
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entring Passive Mode (*,*,*,*,203,85
Command:	PORT 10,90,118,166,12,9
Response:	200 PORT command successful
Command:	LIST
Response:	150 Opening ASCII mode data connection for file list
Response:	226 Transfer complete.
Status:	Directory listing successful
Command:	TYPE A
Response:	200 Type set to A

I stared out my ip address but left what was immediately following it. Is it possible that whereever you are connecting from has blocked port 21 going outbound? I know you said it used to work, well maybe they say traffic on this port and blocked it? Don't know, merely trying to help you troubleshoot this as it does sound weird. Then when I uploaded something, this is what it had in the log, maybe this will help ya?
Status:	Connected
Status:	Starting upload of C:\Documents and Settings\drarfste\Desktop\Copy of 46006-126_2_true_scale.ai
Command:	PWD
Response:	257 "/" is current directory.
Command:	CWD /upload/dans-stuff/
Response:	250 CWD command successful
Command:	PWD
Response:	257 "/upload/dans-stuff" is current directory.
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entring Passive Mode (*,*,*,*,228,108
Command:	PORT 10,90,118,166,12,40
Response:	200 PORT command successful
Command:	STOR Copy of 46006-126_2_true_scale.ai
Response:	150 Opening BINARY mode data connection for Copy of 46006-126_2_true_scale.ai
Response:	226 Transfer complete.
Status:	Upload successful
Status:	Retrieving directory listing...
Command:	TYPE A
Response:	200 Type set to A
Command:	PASV
Response:	227 Entring Passive Mode (*,*,*,*,214,222
Command:	PORT 10,90,118,166,12,42
Response:	200 PORT command successful
Command:	LIST
Response:	150 Opening ASCII mode data connection for file list
Response:	226 Transfer complete.
Status:	Directory listing successful
Command:	REST 0
Response:	350 Restarting at 0. Send STORE or RETRIEVE to initiate transfer
Command:	PWD
Response:	257 "/upload/dans-stuff" is current directory.

I wish I could help more but since you say it worked prior to you getting a router, and you have forwarded the port correctly, and you say that you can log in? Are you sure that you have the correct settings in your proftpd.conf? I know you said it worked before but I just want to rule this out. Here are my settings:
</Limit>
<Directory /home/ftp>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory /home/ftp/download/*>
Umask 022 022
AllowOverwrite off
        <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
        DenyAll
        </Limit>
</Directory>
<Directory> /home/ftp/upload/>
Umask 022 022
AllowOverwrite on
        <Limit READ DELE>
        DenyAll
        </Limit>
        <Limit STOR RMD RNFR RNTO CWD MKD>
        AllowAll
        </Limit>
</Directory>
I used this guide here ([http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd](http://www.ubuntuforums.org/showthread.php?t=79588&highlight=proftpd)) which is awesome, Frodon did a great job. I did however add something to my upload folder so that anyone could change the name of a folder. Using his default settings, a user could create a folder but if he screwed up on the name, it wouldn't allow him to rename it. Other than that, I think that's all I changed from his guide. Well, the name of the folder obviously. I think his is FTP-Shared where mine is just ftp. ZHope you get it fixed!

---

### Post by string on 2006-11-10
Thanks.
First, the problem doesn't come from my remote machine : I connected to other ftp servers successfully.
I kept looking on the net and found this : [http://linuxfr.org/forums/10/12222.html](http://linuxfr.org/forums/10/12222.html)
It works fine if I enter set passive off before connecting so the problem is probably there.

What do you guys think I should do ?
Thanks :)

---

### Post by dannyboy79 on 2006-11-10
well I can't read whatever langauge that is, i only can read english and very little spanish. comprende? just kidding, if you don't know spanish than comprende means, understand. so your problem is weird, i do use passive mode and only have 1 port forwarded within my router and it DOES work, now your saying that if you turn passive mode OFF, it works for you, that's the opposite of me? huh. i wish I could help but I can't anymore.

---

### Post by string on 2006-11-10
It's french. And even if I knew you probably could not read the language, the pure technical part was clear enough to show it was my problem that wasd illustrated.

You're right it's weird, because I also used to forward only one port on my previous router.

But now I knew it was about the passive mode, I searched better and found 2 links :
[http://www.ubuntuforums.org/showthread.php?t=290365&highlight=proftpd](http://www.ubuntuforums.org/showthread.php?t=290365&highlight=proftpd)
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html)

The interesting part :
> However, one big problem still exists. The passive FTP connections will use ports from 1024 and up, which means that you must forward all ports 1024-65535 from the NAT to the FTP server! And you have to allow many (possibly) dangerous ports in your firewalling rules! Not a good situation.
> To resolve this, simply use the PassivePorts directive in your proftpd.conf to control what ports proftpd will use for its passive data transfers:

  ```
PassivePorts 60000 65535	# These ports should be safe...
```

PS: I know you probably don't care, but ... what if you did, ... didn't cost me anything to post that here, and I felt I had to explain what the problem was, is some other guy comes across.

---

### Post by dannyboy79 on 2006-11-11
> **string said:**
> It's french. And even if I knew you probably could not read the language, the pure technical part was clear enough to show it was my problem that wasd illustrated.

You're right it's weird, because I also used to forward only one port on my previous router.

But now I knew it was about the passive mode, I searched better and found 2 links :
[http://www.ubuntuforums.org/showthread.php?t=290365&highlight=proftpd](http://www.ubuntuforums.org/showthread.php?t=290365&highlight=proftpd)
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-NAT.html)

PS: I know you probably don't care, but ... what if you did, ... didn't cost me anything to post that here, and I felt I had to explain what the problem was, is some other guy comes across.

Why would you say I probably don't care? Why would I post here if I didn't care? I don't understand what you are saying here about not costing anything to post here?

So back to the subject at hand, I wonder if that means my router doesn't have or do NAT? That's weird what you have posted because if you notice my previous post the ftp log shows those numbers after the *'s, the stars were my ip address, are those numbers ports I wonder? If so, then what you posted about passive mode using ports betwene 1024 and up isn't correct because you can clearly see that m filezilla was using ports way under 1024 and it also clearly stated that passive mode was used, huh?? well, i guess my questions are for another thread, this is for your problem, di dyou get is resolved?

---

