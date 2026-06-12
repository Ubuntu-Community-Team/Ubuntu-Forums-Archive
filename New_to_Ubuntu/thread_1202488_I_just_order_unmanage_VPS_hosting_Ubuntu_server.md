---
title: "I just order unmanage VPS hosting Ubuntu server"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by HeavenWings on 2009-07-02
So I just order an unmanaged VPS hosting Ubuntu servre. I would to install GNOME and VNC on the server I order since I need to run a game server on it.  The server OS is Ubuntu and the distro is fredora. Where and how do I start installing both of these softwares on the server I order? I tried google but it I'm lost.  I already connected to the Ubuntu server with puTTy and currently have the terminal window up.  Thanks a bunch.

---

### Post by austinpsycho on 2009-07-02
> **HeavenWings said:**
> So I just order an unmanaged VPS hosting Ubuntu servre. I would to install GNOME and VNC on the server I order since I need to run a game server on it.  The server OS is Ubuntu and the distro is fredora. Where and how do I start installing both of these softwares on the server I order? I tried google but it I'm lost.  I already connected to the Ubuntu server with puTTy and currently have the terminal window up.  Thanks a bunch.
Fedora and Ubuntu are different distrobutions.  Are you sure you know which one? Also I'm not aware of any server applications(could because im fairly new at this) that would require gnome be installed.  Which game server are you trying to run?

---

### Post by austinpsycho on 2009-07-02
also usually *sudo apt-get install [name of package]* will install whatever you're looking for from terminal; try that out

---

### Post by HeavenWings on 2009-07-02
I believe its Ubuntu since I typed in uname -a in the terminal window and it show to be a 32 bit Ubuntu.  I'm trying to run a ragnarok gaming server. Where players can connect to my server. but that is later after I finish installing the softwares I said in my first post.   Ok, so VNC is for desktop access, correct? And GNOME is like a desktop environment with graphics?  I currently have VNC Viewer install on my laptop. The Ubuntu VPS server I purchased does not have VNC install yet. So how do I go about this? Also, gnome.  Thanks a bunch.   It would be easier for me if I had visual graphics since I'm new and I don't really like the terminal window.

---

### Post by austinpsycho on 2009-07-02
*sudo apt-get install x11vnc vnc-java* will install it.  i would install gnome first if you havn't
the whole process is here:
that is the whole vnc install process
[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

---

### Post by HeavenWings on 2009-07-02
> **austinpsycho said:**
> *sudo apt-get install x11vnc vnc-java* will install it.  i would install gnome first if you havn't
the whole process is here:
that is the whole vnc install process
[http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

It says E:Couldn't find package. I think I need to enable repositories but I'm not sure how to do this. How do I open the file through the terminal window that I need to edit.

---

### Post by HeavenWings on 2009-07-02
Bump

---

### Post by halitech on 2009-07-02
post the output of
```
cat /etc/apt/sources.list
```

---

### Post by HeavenWings on 2009-07-02
Here is the output:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted universe 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-security main restricted universe


Ok, let me rephrase my questions:

Hello,

I just order an unmanaged VPS hosting for a gaming server (ragnarok online) that I want to run on it. I'm currently a novice at Ubuntu Linux which is the OS for the VPS server I order.

I would like to know a couple of things.
1) How do you open and edit a text file through the terminal window? I'm currently connected to the server through puTTy and trying to open this file and edit it "/etc/apt/sources.list" so I can enable universal repositories and install things. I'm not so sure about this.
2) After I edit this file to enable universal repositories, I want to install GNOME. I read somewhere that you need to enter this command in the terminal window.
sudo apt-get install ubuntu-desktop
Is this the right command?
3) Once I finish installing GNOME, I like to install VNC (remote desktop). I already have VNC viewer on my laptop. Now I only have to install VNC server on the server. I read somewhere that the command to do this is:
sudo apt-get install x11vnc vnc-java
Is this right? Then I have to do this:
       2. Set up a password for clients. Code: x11vnc -storepasswd
       3. Open up ports 5800 and 5900 on your firewall
       4. Run the terminal command: x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800 and add it for auto-starting in future sessions
Are these the right steps for installing VNC on the server?
4) After I install both of these software, am I set to start installing and running my gaming server? Or is there any other small things I have to do? Remind you, this is a newly Ubuntu server 32 bit with nothing besides Apache and the setup files.

I greatly appreciate anyone's help.

---

### Post by HeavenWings on 2009-07-02
Ok, I finally install GNOME.

Now I need help installing VNC. I only need question 3 answer now.

I have a problem when I enter the command
sudo apt-get install x11vnc vnc-java

This is what it gives me:
root@xx-xx-xxx-xx:~# sudo apt-get install x11vnc vnc-java
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package vnc-java is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vnc-java has no installation candidate

What might be the problem?
Thanks.

---

### Post by HeavenWings on 2009-07-02
Woops I'm not sure why I was trying to install VCN java. Nevermind that.

I just need a regular VCN install on my server so I can connect to it through my laptop.

---

### Post by halitech on 2009-07-02
just drop the vnc-java part of the command then. It would allow you to connect using a web browser and java but its not needed

---

