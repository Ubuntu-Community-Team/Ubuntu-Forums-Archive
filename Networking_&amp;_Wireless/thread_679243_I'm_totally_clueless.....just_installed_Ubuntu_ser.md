---
title: "I'm totally clueless.....just installed Ubuntu server"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by kryth on 2008-01-26
Hi, I just installed ubuntu server with LAMP. I'm totally clueless what to do next. I want to 'ssh' into it. And share files, then go from there. First I want to be able to access it with my other ubuntu box and then win XP. Can someone explain it to me like i'm 4 years old or point me in the right direction. 
Thanks

---

### Post by louie55 on 2008-01-26
Wow, that's a big question. The first thing I will say is that I am not a Linux Expert, but I have configured some servers before.

 First of all, to ssh into it, you must install a Secure Shell (SSH) Server. To do that, run this from the command-line:

```
sudo apt-get install ssh

```

After you do that, the ssh server should be up and running. To ssh into it from a Windows machine, you can use a free program called PuTTY, which can be downloaded here:

[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)

Simply open putty.exe and type your Ubuntu Servers IP address in the Hostname field and make sure SSH is selected and click OK. Then if everything goes correctly, a box should pop up asking you want to accept the servers key. Click Yes. Then you can login with the username and password you created when you installed ubuntu server.

If you want to ssh into it from a Linux machine, simply open a command-line terminal and type:

```
ssh <SERVER-IP>
```

Just replace <SERVER-IP> with the address of your Ubuntu Server, then login.


Now sharing files.... In what manner do you wish to share files? The 2 main ways that come to mind are FTP or a Samba share. With FTP, you can access files from windows or Linux using an FTP client. With a Samba share, you can access the files from your Windows machine as if it were another windows machine with a file share. Please state which one of these methods you would like to use and someone will post a link to a HowTo or try to help you out.

---

### Post by kryth on 2008-01-26
Okay, and how do I know what my domain name is?

---

### Post by kryth on 2008-01-26
cool! Deep breath. I ssh'ed into it. Thanks

---

### Post by louie55 on 2008-01-26
EDIT:

Oops, I thought you were replying to my post with your domain name question. Disregard this post. Congratulations on SSHing!

---

### Post by kryth on 2008-01-26
Okay, installed proftpd on server now. How do I ftp into it. 

server's name is ubuntu-server
domain name is Belkin (stop laughing)

---

### Post by kryth on 2008-01-26
nevermind i figured it out

---

### Post by louie55 on 2008-01-26
I don't know what FTP Client you are using, but I recommend Filezilla:

[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by HermanAB on 2008-01-26
Hmm, you should befriend SSH since you can do *anything* with it.  SSH is the Sacred Swiss Army Knife of server administration.

Ferinstance, using SSH, you can connect to the server with X forwarding and run any GUI application remotely, while still boasting honestly to your friends that your server doesn't run X.  Hah! Beat That! My server only runs in Run Level 3! Neener, neener... ;)

$ ssh -X -c blowfish joesoap@w.x.y.z "gedit /etc/fstab"
La voila!

or if you are really degenerate:
$ ssh -X -c blowfish joesoap@w.x.y.z "gnome-panel"
;)

Similarly, you can use scp to transfer files - no need for the insecure FTP:
$ scp whatever joesoap@w.x.y.z:~/.

Or - horror of horrors - you can do it the enlightened new age way with Nautilus or Konqueror and a mouse.

Cheers,

H.

---

### Post by kryth on 2008-01-27
Oh, yeah, my server goes to 11!  (needless spinal tap refference )

How pray tell do you run a GUI app remotely? I have no gui on server box. Sounds cool although.

---

