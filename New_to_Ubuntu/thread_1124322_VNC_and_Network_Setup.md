---
title: "VNC and Network Setup"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by kc5hwb on 2009-04-13
I just installed xubuntu and upgraded to 8.04 LTS.  I have used Ubuntu for a couple of years now, but this is my first time with Xubuntu.  I got vnc4server installed and enabled it, but I still can't connect to the machine from another machine.  Also, from the xubuntu box, I cannot find my network.  I can get updates from Synaptic and I can browse the web, but I cannot find any other machines on the network.  I know I am probably looking in the wrong place, but can someone tell me where to look or where to find a manual for xubuntu?  I searched these forums for the vnc issue and couldn't find anything.

---

### Post by aaronp on 2009-04-13
Hi,

I'm not sure about the differences between Xubuntu and Ubuntu but I am using Ubuntu 8.04 and all I had to do was edit the remote desktop settings to allow remote connections.

Then, if you have any firewall running you need to allow the local networked PCs access.

After that I could just connect to the local IP of my Ubuntu machine with a VNC viewer program.

Again, not sure if this is as simple on Xubuntu and it is on Ubuntu.

hth
Aaron

---

### Post by kc5hwb on 2009-04-15
You shouldn't need to set anything on the router to connect to local network resources... at least I never had to before.  Yes, I set the Remote Desktop Settings on the Xubuntu box, but it still will not let me connect from another box, which is also on the LAN.

Basically, I did the exact same thing on this Xubuntu box that I have done on previous Ubuntu boxes and it isn't working the same.

---

### Post by necrit on 2009-04-15
Hrm well as i see it the settings for rdp arent tantemount to enabling remote access when you are having general network issues.  Also if you get a chance... [HERE]("http://ubuntuforums.org/showthread.php?t=669755") is the forum i think will point you in the right direction for xubuntu remote access config.

---

### Post by kc5hwb on 2009-04-15
Those threads linked from the thread you linked here look great, I will try them tonight when I get home.  Thanks.  FOR THE HORDE!

---

### Post by quinnten83 on 2009-04-15
those are actually 2 issues I have with Xubuntu.
In order to use vnc you have to install vinagre and then configure it, otherwise you won't be able to connect.
 I got the following instructions, but I can't rememeber from where:

```
Remote Desktop (VNC) Access on Xubuntu (XFCE) 8.10
Posted by Sam Lesher on December 1, 2008

Gnome on Ubuntu comes with an included “Remote Desktop” feature (vino) that allows you to VNC into your existing desktop session (usually on the :0 display). However, XFCE does not have a native VNC package built in. The best option I have found is to use vino, the same VNC app that Gnome uses. Here’s how:

Install vino:
$ sudo apt-get install vino

Configure vino:
$ vino-preferences

Then enter this command in your Autostarted Apps to start vino server:
/usr/lib/vino/vino-server

This works well for me, the only feature I have found that doesn’t work is the “disable wallpaper on remote login” setting.
```
As far as connecting to other networks is concerned, Xubuntu does not have a network browser like Ubuntu does.

---

### Post by necrit on 2009-04-15
Thats the beautiful thing though.  Synaptic package manager and then start installing your needed components :-P

Anyway here's what i found for your networking issue.

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

Could help...but dont try and reinstall the wheel to get basic INTENDED functionality to work.  Xubuntu has most if not all of the requirements already.  just needs a bit of tweaking until baked...JUST right.

---

### Post by kc5hwb on 2009-04-16
Vino doesn't work.  That is actually what I already had installed.  When I ran vino-preferences it pulled up a GUI window which I had already setup with the previous Synaptic install.  I still cannot connect to the VNC server on the Xubuntu box.

I am going to try the other options now...

---

### Post by aaronp on 2009-04-16
Not sure what the issue is here but if you are gonig to look at other options maybe take a look at FreeNX. 

It's a little bit different to VNC in that it logs you into a fresh session rather than the one that is currently open on the system.
However, this is good if someone is using that system and you want to use it too, you can use FreeNX to open up your own remote session without affecting the other open session at all (except for chewing up their RAM and CPU!!)

---

### Post by kc5hwb on 2009-04-16
Ok I followed the instructions at [this site]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html") and those do not work.  I am still getting a connection error when trying to VNC to the IP of my Xubuntu box, which is on my LAN.

---

### Post by aaronp on 2009-04-16
Can you telnet or SSH to the local IP address from the same client?

---

### Post by kc5hwb on 2009-04-17
> **aaronp said:**
> Can you telnet or SSH to the local IP address from the same client?

No, I get a Hot Key error when I try to do that, and I haven't researched it yet because I have been working on this other issue.

---

