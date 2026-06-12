---
title: "ssh setup rsa password"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by werecatomega on 2010-03-08
hey everyone,
i need to connect my ubuntu box (remote computer) to my mac box (don't ask questions) via ssh. i can connect but i need to know how to put the key in (rsa). i've read part of the [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH) but i'm confused on what i need to do. can somebody help?

---

### Post by MontelEdwards on 2010-03-08
Wait, what?

Are you trying to generate a SSH key? Who is the host OS, Mac or Ubuntu?

---

### Post by werecatomega on 2010-03-08
by host computer i guess you mean the one i'm connecting too, so the Mac is the host

---

### Post by Iowan on 2010-03-08
What part of the key process is causing confusion - the generation or copying the public key to the server?
Oh, wait - that's a question - sorry...

---

### Post by richs-lxh on 2010-03-08
Does this help?
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Key-Based%20SSH%20Logins")
> **Saving Keys on Remote Computers**

 If you can log in to a computer  over SSH using a password, you can transfer your RSA key by doing the  following from your own computer: 

ssh-copy-id <username>@<host>Where <username> and <host> should be replaced by your username  and the name of the computer you're transferring your key to. 
You can make sure this worked by doing: 

ssh <username>@<host>You should be prompted for the passphrase for your key:  
  Enter  passphrase for key '/home/<user>/.ssh/id_rsa':
  
Enter your  passphrase, and provided *host* is configured to allow key-based  logins, you should then be logged in as usual. 

You said you can connect, but you didn't say if you could login.

---

### Post by werecatomega on 2010-03-08
> **Iowan said:**
> What part of the key process is causing confusion - the generation or copying the public key to the server?
Oh, wait - that's a question - sorry...

i meant questions about why i have a mac box. i'm confused about if i generate the key on the computer i connect to and then add it to the i connect from or vice versa

---

### Post by psusi on 2010-03-08
You can generate it anywhere you like.  You just need to make sure that the public key is installed on the server you want to connect to, and the private key is installed on the computer you want to connect from.

---

### Post by MontelEdwards on 2010-03-08
Okay, so what I think you're trying to do is set up your Mac box to authenticate users that try to access it via SSH by a SSH key, right?


[http://lmgtfy.com/?q=mac+ssh+key+](http://lmgtfy.com/?q=mac+ssh+key+)

That should help you.

---

### Post by werecatomega on 2010-03-09
ok, i've got the keys generated on my ubuntu box in my .ssh folder. do i move the id_rsa or the id_rsa.pub to the server (i.e. mac box)?

---

### Post by werecatomega on 2010-03-09
never mind, i've got it working

thanks everyone

---

