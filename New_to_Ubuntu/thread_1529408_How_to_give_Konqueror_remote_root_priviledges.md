---
title: "How to give Konqueror remote root priviledges?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Mariane on 2010-07-12
To run Konqueror as root on the local machine I guess I could simply type "sudo Konqueror" in the terminal. But how do I give it root priviledges on a remote machine? 

I type in Konqueror location bar [ftp://admin@whatever.com](ftp://admin@whatever.com) and give my password to look at remote files. But this does not give me root access on the remote machine, some files there remain invisible. If I want to work on them I have to: 

Open a terminal window and:
Type ssh [email]admin@whatever.com[/email]
Give the password
Type su (the remote machine equivalent of sudo, except you only have to type it once)
Give the password again
Find the file I want with the terminal
Copy it to some location where Konqueror can see it
Chown and Chmod so Konqueror can see it
Do what I want with it from Konqueror
Chown and Chmod it to what it was before
Copy it back to where it was before

I can't type [ftp://root@whatever.com](ftp://root@whatever.com) in Konqueror, the remote machine refuses this login. It says the password is incorrect when it is not. 

I can't type "Konqueror" once I am root via the ssh login through the terminal, the remote machine does not have Konqueror (and I am not going to try to install it, I am supposed to take care of this server not mess it up, I do "apt-get update" and "apt-get upgrade" occasionally but then the packages come from a source local to the server and not from the normal repositories. Trying to bypass these settings would be a bad idea, I am quite certain I would do something really stupid. My knowledge is sufficient to enable me to really mess things up but insufficient to enable me to sort them out again later). 

I can type ssh://admin@whatever.com in Konqueror location bar but this simply opens a terminal-like window. 

Any ideas please?

Mariane

---

### Post by cariboo on 2010-07-12
Try sftp, or install konqueror on the remote computer and use X-forwarding eg:

```
ssh -X user@server
```

then start kongueror from the command as root:

```
sudo kongueror
```

---

