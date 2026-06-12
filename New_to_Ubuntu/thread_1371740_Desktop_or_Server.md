---
title: "Desktop or Server ?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by onclouds on 2010-01-03
Hi all,
here's my issue: I have an old desktop with Ubuntu Desktop for about a year now.. By now I already became addicted to ssh through lan and from the internet. 
Today it decided it had to crash and now.. Well.. now I'm still working on the details of backing up all my data.. But after that I will need to re-install Ubuntu and then comes my problem:
Desktop or Server edition?

I barely use this computer nowadays but to check something I'm too lazy to do via ssh so I thought of trying out Server edition, the problem is that I would still like to use some programs (like Firefox for visitors). Does a Server installation have the capability to have gnome installed over it? Is it complicated? And could I have ssh, http and other services start independently to the user session of gnome?

Please give me some guidelines (even if links to walkthroughs or comparison threads)..

thx

---

### Post by bpalone on 2010-01-03
Server Edition is command line based.  Yes, you can install Gnome, or any other X Gui of your choice.  I am not sure, but I believe you can set it up where the Gui is only available for a given user at login.

You can also set it up as a Samba Server and have your it as your file server.  Mine is hosting a couple low volume web sites and is my file server via Samba.  Works great.

---

### Post by @B6Mwu8fN9M on 2010-01-03
You can install the package
```
gnome-desktop-environment
```
to install Gnome. Alternatively, you can install 
```
ubuntu-desktop
```
for the full Ubuntu desktop.

---

### Post by Paqman on 2010-01-03
If you just want a basic Gnome setup you might want to try gnome-core instead of gnome-desktop-environment. I'd also suggest inidcator-applet-session and gnome-themes. Then for Firefox just add the package firefox-3.5-gnome-support.

---

### Post by tgalati4 on 2010-01-03
Only the desktop version has the hooks to put the machine to sleep.  So if you ever intend on putting the machine to sleep, you should stick with the desktop.  The graphical desktop will use ~10% of your cpu cycles based on a dapper drake desktop machine that I have been using as a server since June 06.

---

### Post by Paqman on 2010-01-03
> **tgalati4 said:**
> Only the desktop version has the hooks to put the machine to sleep.

I'm not 100% about this, but I believe you can get around that by using a userspace package like uswsusp.

---

### Post by NullHead on 2010-01-03
Honestly, for your uses, I would go with a desktop version of ubuntu. Really the most difference between server and desktop is different security settings, a different server optimized kernel and it comes with server oriented applications.

---

### Post by HermanAB on 2010-01-03
I would install ordinary Ubuntu, then change the startup so that Xorg doesn't start, install sshd and login remotely over SSH with X forwarding. Then you can do this:

$ ssh -X -C -c blowfish user@laptop gnome-panel

and go click happy.

---

### Post by mkoehler on 2010-01-03
I agree with both of the above responses.  If you want the graphical environment, even for limited use, you're better off installing the desktop version of ubuntu as opposed to the server edition.  The latter is rather specialized and unless you intend to use it solely as a server, you shouldn't install it.

---

### Post by slooksterpsv on 2010-01-04
My 2 cents - when I ran my own Web Server, Media Server (Gnump3d), File Server, etc. I used Ubuntu Server, then installed Gnome on it. I was able to use it just fine, I could SSH into it, run server apps, host files, etc.

You can also use the Desktop version and install those items you want from the server. E.g. Samba, SSH, etc.

EDIT: At the top I meant to say etc. I used Ubuntu Server, then ....

---

### Post by onclouds on 2010-01-04
Thx for all your input.. I will be going with the Server version if nothing else to have a better perspective of it. =)

Can anyone give me some insight on whether or not a user has to login physically or if the server just needs to be turned on?

---

### Post by onclouds on 2010-01-04
> **onclouds said:**
> Thx for all your input.. I will be going with the Server version if nothing else to have a better perspective of it. =)

Can anyone give me some insight on whether or not a user has to login physically or if the server just needs to be turned on?

also, can a Server installation with apropriate drivers and Wine run Diablo 2 (or any wine software for that matter) ?
That's the only thing I need from gnome besides Firefox =)

---

### Post by NullHead on 2010-01-05
I still recommend the Desktop version, but yes, you can run wine apps. I can't tell you if they'll run good at all, but they should technically run. 

As far as I know, ssh comes installed and setup. The only thing I think you'll need to do is get your user account setup and you can ssh in. I still recommend some monitor setup just in case.

---

