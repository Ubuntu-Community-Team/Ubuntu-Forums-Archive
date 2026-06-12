---
title: "headless exception"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by KLStringer on 2009-06-09
When trying to install Crossftp I keep getting an "Exception in thread "main" java.awt.headlessexception: No x11 display variable was set, but this program preformed an operation which requires it." error.

I have zero experience using any form of *nix and have no idea what that error means but I can't get CrossFTp to install or download or whatever its trying to do when I enter in the "javaws http://www.crossftp.com/crossftpserver.jnpl" string from CrossFTP's site.

The first time I tried to install it I got a different error msg saying something about needing java and it gave me a command to run to get it which I did but now I get the error above.

I'm totally clueless as to what I need to do to download or install CrossFTP so any help will be much appreciated.

Thanks

---

### Post by treesurf on 2009-06-09
Do you have Sun Java installed? This is a prerequisite of CrossFTP.  If not, in the terminal type:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```


If all you need is a simple FTP client, then I would recommend using gFTP, available in the repositories.  Install with the following code and you will find the application in the Applications>Internet menu:

```
sudo apt-get install gftp
```

---

### Post by KLStringer on 2009-06-11
> **treesurf said:**
> Do you have Sun Java installed? This is a prerequisite of CrossFTP.  If not, in the terminal type:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

I ran that command and installed java

> **treesurf said:**
> If all you need is a simple FTP client, then I would recommend using gFTP, available in the repositories.  Install with the following code and you will find the application in the Applications>Internet menu:

```
sudo apt-get install gftp
```

Our goal is to set up an SFTP server where our clients can access recordings from and I've been tasked with getting everything working within the next week. This probably wouldn't be hard to do if I had any experience with Linux. As it is I'm learning Linix while figuring out how to get it set up, nothing like a crash course in a new server OS. #-o

---

### Post by KLStringer on 2009-06-29
Still trying to setup this sftp server and I  haven't got a clue as to what I'm doing. I've read a bunch of online tutorials and its all greek to me and I can't make heads or tails what their talking about. How do I find out whats installed and what isn't? Once its installed how do I setup the folders to be shared and lock everything else so it can't be messed with? Do I need to install a GUI? How do I install a GUI if ones needed? Somehow I think I installed the kubuntu GUI or desktop but that didn't make anything easyier and now I don't know how to get back to the command line. How do I if out what my IP address is and how do I set a static IP address? All the tutorials make it seam like its easy to do but I can't figure it out and I've already passed the date it was needed to be up and running.

If someone cares to walk me through it from a clean install I will start over from scratch but I've got to get it done A.S.A.P. I don't understand what all this repositories or etc or bin or bash stuff is or how to even get to them or what I am supposed to do once I get there. I thought Crossftp would be simple to set up be apparently it isn't.

Thanks in advance to anyone willing to teach/show me what to do.

---

### Post by halitech on 2009-06-29
no, you don't need a GUI but if you think it might come in handy, look into webmin [www.webmin.com](www.webmin.com)

If you need help setting up things, check here

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

---

### Post by KLStringer on 2009-06-29
I read something on Howtoforge on 9.04 but by about page 3 I was completely lost, is there anything thats more indepth and doesn't assume your familiar with using *nix? Currently I'm trying to set this up on 9.04, should I switch to 8.04 instead? Is there a big difference between the two?

I have no idea if a GUI will come in handy or not thats why I'm asking

---

