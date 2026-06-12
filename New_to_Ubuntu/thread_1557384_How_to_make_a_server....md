---
title: "How to make a server..."
date: 2010-08-20
forum: New to Ubuntu
---

### Post by superninja on 2010-08-20
I have a box that has Ubuntu 10.04 desktop edition installed on it and I would like to make it my server. I have done some searching on the web to figure out how to do this but I have no luck.

I would like this server to be able to connect to my windows boxes also, and I would like to be able to access my files from remote location

I need to know what to install and after that how to punch a hole through the fire wall (if necessary) to be able to access it through any web browser. Any help is appreciated.

---

### Post by bodhi.zazen on 2010-08-20
Install the appropriate server software.

for what you want you can use ssh (sshfs), http, or ftp.

Just be sure you understand how to secure the server.

See :

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by pricetech on 2010-08-20
If you're planning to expose this thing to the Internet, I wouldn't recommend anything but SSH for your files.

If you're hosting a web page, that's different, an FTP site, also different.  Just make sure you understand the security implications of each.

Having said that;  Start with SSH Server and Fail2Ban.  Samba (system-config-samba so you'll have a GUI to help configure) VSFTP for an FTP Server.  There's a chapter in the Ubuntu manual, accessible from the main site that tells you exact how to set that up.

Port forwarding in your router; depends on your router.  Default port for SSH is 22, HTTP is 80, FTP is 20 and 21.

---

### Post by superninja on 2010-08-20
I have installed sshfs on my server box, and do not know how to run it. is it equipped with a GUI? If not, is there an alternative with a GUI?

---

### Post by bodhi.zazen on 2010-08-20
> **superninja said:**
> I have installed sshfs on my server box, and do not know how to run it. is it equipped with a GUI? If not, is there an alternative with a GUI?

Why do you need a gui ?

If you really need you can use ssh -X and forward X applications.

See :

[https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo)

Be sure to secure it, I suggest you use keys.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

For sshfs see

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

From Windows use putty and winscp (winscp is a graphical interface).

---

### Post by superninja on 2010-08-21
I am figuring out how to do this :D. Is there a difference between sshfs and openssh?

---

### Post by superninja on 2010-08-21
And I'm not using a GUI... It's easier than I thought

---

### Post by drdos2006 on 2010-08-21
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by bodhi.zazen on 2010-08-21
> **superninja said:**
> I am figuring out how to do this :D. Is there a difference between sshfs and openssh?

Yep, no gui is not too bad at all =)

The server is openssh.

sshfs is a way of mounting a share from the server using ssh.

Once the share is mounted it acts as a local directory. IMO this is best for sharing over the internet as the connection is secure and encrypted.

From windows clients use putty and winscp. Winscp is a graphical interface for scp.

---

### Post by ubudog on 2010-08-21
This is a very good guide which I used a while back.

[http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

---

### Post by superninja on 2010-08-23
> **ubudog said:**
> This is a very good guide which I used a while back.

[http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841)

Awesome guide but, apache and openssh are two totally different things, right? If so, what are some of the pros and cons to both?

---

### Post by superninja on 2010-08-23
Is Apache just the way to view my files through a web browser and openssh a way to transfer them? So they would be different but have different purposes...

---

### Post by moonbasenick on 2010-08-23
> **bodhi.zazen said:**
> Install the appropriate server software.

for what you want you can use ssh (sshfs), http, or ftp.

Just be sure you understand how to secure the server.

See :

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)


Awesome site, thanks!  here is a nub question, would this be considered a DNS server? or is there a difference?

---

### Post by ubudog on 2010-08-23
Apache is designed as a web server (to host a website, eg. [www.google.com](www.google.com)) 

Openssh is an ssh server.  (you can connect to other computers and execute commands in a command line environment)

So yes, they are very different.

---

### Post by superninja on 2010-08-23
Awesome thanks for that clarification... I will definitely set up both :D

---

### Post by ubudog on 2010-08-23
> **superninja said:**
> Awesome thanks for that clarification... I will definitely set up both :D

No problem.

---

