---
title: "let me get this"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by pvplahing138 on 2009-12-09
let me get this straight
ok fresh linux install now firewall installed right? so i need to have firestarter or any other firewall?
next i want to be secure and then i use avast for linux
and thats basiclly it
this is all correct right? i need to have firewall or it is already installed but where to find it?
sorry for very very newbie question

---

### Post by bodhi.zazen on 2009-12-09
Linux is more secure out of the box then Windows, so you are best off with this thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

The default configuration tool in Ubuntu is ufw. It has a gui called gufw.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

---

### Post by Sef on 2009-12-09
> sorry for very very newbie question

No need to apologize.  We all started out where you are at some point in time.

---

### Post by iponeverything on 2009-12-09
An attack needs a vector. The other os has/had kindly provides multiple vectors - 

-mechanisms that make "drive by downloads" possible.
 
-fertile os design for viruses and spyware. 

-fertile default server settings for worm propagation. 

=======

None of these are applicable under the normal default end user installation of Ubuntu. 

Please note that all bets are off when you are using Linux in a server setting with complex in-house or third party server applications.

---

### Post by donato roque on 2009-12-09
The best explanation regarding setting up firewalls[ is here.]("https://help.ubuntu.com/community/Firewall")

    Let me start you off on some terms.  Linux "firewall" is called netfilters and you are right they are already installed (they come with your default installation).  iptables, uncomplicated firewalls(ufw), firestarter, firewall builder and others are tools that users can use to manipulate the netfilters.  

    I'm guessing that you're new to linux :) , I think I would serve this question better if I point you to a more general discussion of security in Ubuntu.  Please [read this.]("http://ubuntuforums.org/showthread.php?t=510812")

    To keep my advice simple, after a fresh install, all a user has to do is enable the netfilters.  You make one rule in netfilter and that's to deny all incoming signal.  You open gnome terminal and type:  

    ```
sudo ufw default deny
```

    This will create a rule in netfilter to deny all incoming signal.  Then to enable your netfilter (with one rule)type:

    ```
sudo ufw enable
```

    Afterwards you are set.  You don't need to do anything else nor download anything else.  

    I frankly don't use AV.  But if you interact with Windows machines a lot (like swap usb sticks) I recommend clamav.  This is for the Windows users' benefit not yours.  I on the other hand jumped out of Windows XP to escape AV's :).  

    As a Linux user now, what we have to focus on is updates, browser security, root kits, strength of passwords and social engineering.

---

### Post by 3rdalbum on 2009-12-09
You don't need a personal firewall. Ubuntu doesn't listen to any incoming ports by default. If you install some server services that you don't want to be accessable from outside your computer, then you will want a firewall; but if you want them to be accessible from your network or from the Internet then you don't.

If you have an ADSL/cable router, then that probably already contains a firewall that protects your whole network - in which case, you'll never need a firewall running on your computer.

Also, you don't want anti-virus on Linux.

---

