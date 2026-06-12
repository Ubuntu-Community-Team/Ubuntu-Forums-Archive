---
title: "How do I setup an FTP server in an easy and simple way?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-07-19
Ok so I'm kinda dumb, a novice with this stuff so please help me. I haven't been this frustrated working on Ubuntu ever!

I need to setup an ftp server on my computer. I need someone else to log in and download files off me. How do I set this up? When I was on windows, I could just download a simple ftp software, where I could set the username and password, the directory, the access control for the shared directory, and the program would tell me what my IP address is, which I could provide to the person trying to log in with the client software.

I have tried vsftpd, proftpd all that stuff and it's way too complicated. I just need something that is simple, and easy to set up. Something with a simple front end.

Please HELP!

---

### Post by Sanjeevtrip on 2010-07-19
check webmin, maybe it will help you.

---

### Post by HermanAB on 2010-07-20
Both VsFTPD and ProFTPD work out of the box.  So, just install it and then - drum roll - do nothing.  Although in your case, you should open an account for this other person.

---

### Post by blukes on 2010-07-20
I use proftpd and like it...very easy to set up.
  	 	 	 	 	
sudo apt-get install proftpd gadmin-proftpd

---

### Post by koba101 on 2010-07-20
maybe you can share what problems you're facing...what went wrong when you tried to install vsftpd for example?

---

### Post by house7 on 2010-07-20
update : oo geez my mistake i thought an ftp client. Sorry.. :|

Hmm.. try this 
Go to Places - Connect to server - and choose FTP (with login).

---

### Post by nhasian on 2010-07-20
you could install [openssh-server]("apt:openssh-server") by clicking the link or copy/pasting the following terminal command:

```
sudo apt-get install openssh-server
```

then you can use sftp to securely connect to your computer.

---

### Post by pricetech on 2010-07-20
vsftp is "falling off a log" easy to set up.  There's even a page in the documentation giving you all the instructions.

[https://help.ubuntu.com/10.04/index.html]("https://help.ubuntu.com/10.04/index.html")

Just click on Advanced Topics, Ubuntu Server Guide, then FTP Server under File Servers.

You should have a working FTP server in a matter of minutes.

---

### Post by snip3r8 on 2010-07-20
> **pricetech said:**
> vsftp is "falling off a log" easy to set up.  There's even a page in the documentation giving you all the instructions.

[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

Just click on Advanced Topics, Ubuntu Server Guide, then FTP Server under File Servers.

You should have a working FTP server in a matter of minutes.

using open-ssh  is also that easy

---

### Post by pricetech on 2010-07-20
> **snip3r8 said:**
> using open-ssh  is also that easy

Maybe even easier, but the OP did say he wanted an FTP Server.

---

### Post by stmiller on 2010-07-20
Don't use ftp. It is insecure and a security risk to your computer and data. Someone can easily intercept the login/password.

Just install openssh-server then create a new user account for your friend. He can then connect securely via sftp instead of ftp.

It will be over port 22, so you may have to open that up in your router for your computer.

---

### Post by cchhrriiss121212 on 2010-07-21
> **pricetech said:**
> vsftp is "falling off a log" easy to set up.  There's even a page in the documentation giving you all the instructions.

[https://help.ubuntu.com/10.04/index.html]("https://help.ubuntu.com/10.04/index.html")

Just click on Advanced Topics, Ubuntu Server Guide, then FTP Server under File Servers.

You should have a working FTP server in a matter of minutes.

I am in the same position as the OP, so this link was a good start. The only problem is that the guide you linked to only shows how to set up the server (which I have done), so how does a client access the server?
I have two machines both using the same wireless network.

---

### Post by koba101 on 2010-07-21
> **stmiller said:**
> Don't use ftp. It is insecure and a security risk to your computer and data. Someone can easily intercept the login/password.

Just install openssh-server then create a new user account for your friend. He can then connect securely via sftp instead of ftp.

It will be over port 22, so you may have to open that up in your router for your computer.

I second this

---

### Post by carljason on 2010-07-22
I currently use [Wing FTP Server]("http://www.wftpserver.com"), it is very easy to use, and I believe it has the most beautiful GUI too.

---

### Post by pricetech on 2010-07-22
> **cchhrriiss121212 said:**
> I am in the same position as the OP, so this link was a good start. The only problem is that the guide you linked to only shows how to set up the server (which I have done), so how does a client access the server?
I have two machines both using the same wireless network.

If you want an easy to use client, I like FileZilla.  It's in the repos for Lucid and is available for windows as well, so you can use the same client on both platforms.

As to the security of FTP:
I agree with those who are raising concerns about security.  SSH is much better and a windows client is available (winscp) which I have used more than once on windows boxen I support.
But:
If an FTP server is what's wanted or needed, then we should help the OP set up an FTP server.  Yes we should warn him / her about the security risks, but we should also just answer the question and help if we can.

There, I said it.

---

### Post by cchhrriiss121212 on 2010-07-22
> **pricetech said:**
> If you want an easy to use client, I like FileZilla.  It's in the repos for Lucid and is available for windows as well, so you can use the same client on both platforms.
Great I have Filezilla installed now, but what do I do from here?
How do I find my host name and what protocol prefix do I use?
What port do I use? If I need to allocate one what should it be? Does this require port forwarding?
Username and password are setup how?

 Remember this is the Absolute Beginner forum and any simple pointers that explain things are appreciated. The manuals I can see often glaze over the simple stuff using technical terms not everyone is familiar with.

---

### Post by pricetech on 2010-07-22
> **cchhrriiss121212 said:**
> 
How do I find my host name and what protocol prefix do I use?

Host name is either the Fully Qualified Domain Name or IP address of the FTP server you want to access.  For example I might want to access "ftp.microsoft.com" or my internal FTP server at 10.1.10.111.

> **cchhrriiss121212 said:**
> 
What port do I use?

FTP uses ports 20 and 21 by default.  You will rarely, if ever have to change that in your client.

> **cchhrriiss121212 said:**
>  Does this require port forwarding?

Not for the client.

> **cchhrriiss121212 said:**
> 
Username and password are setup how?


Filezilla gives you a place to enter that information.  If it's something other than an anonymous FTP server, you'll need to get the credentials from whomever is running the server. If it's your FTP server created on your Ubuntu box, you'll use the same credentials that you use to log in the computer itself, assuming you configure it to allow authenticated logins rather than anonymous only.

> **cchhrriiss121212 said:**
> 
 Remember this is the Absolute Beginner forum and any simple pointers that explain things are appreciated. The manuals I can see often glaze over the simple stuff using technical terms not everyone is familiar with.

Indeed it is and indeed they do.  Sometimes you have to look in more than one place to make sense of the information you get.

---

