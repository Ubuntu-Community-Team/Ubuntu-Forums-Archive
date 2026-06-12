---
title: "vncviewer -listen"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-12-22
I'm trying to get reverse VNC working. The problem is, when I use "vncviewer -listen" command then initiate the reverse VNC on the customer's end, it accepts the connection on my end, but nothing shows up on the screen. Here's the output of "vncviewer -listen"

> 
cuco@cucopc:~$ vncviewer -listen
vncviewer -listen: Listening on port 5500
vncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.8I'm using a virtualized Win7 machine as the "customer's computer" if that helps. Firewall is turned off on both computers.

---

### Post by Cuco3 on 2009-12-22
Anyone?

---

### Post by asmoore82 on 2009-12-22
which flavor of VNC are you using on the Win7 "machine?"

---

### Post by Cuco3 on 2009-12-22
> **asmoore82 said:**
> which flavor of VNC are you using on the Win7 "machine?"UltraVNC SC.

---

### Post by asmoore82 on 2009-12-22
Make sure UltraVNC is set to allow [relatively]insecure connections.

---

### Post by Cuco3 on 2009-12-22
> **asmoore82 said:**
> Make sure UltraVNC is set to allow [relatively]insecure connections.Thanks. How would I go about that? I'm pretty sure I don't have UltraVNC installed on the "tech computer"

---

### Post by juancarlospaco on 2009-12-22
Use NX NoMachine...

---

### Post by Cuco3 on 2009-12-22
Will try, thanks.

---

### Post by Cuco3 on 2009-12-22
I was able to install the client, but the node and server version have broken dependencies.

---

### Post by pricetech on 2009-12-22
NX always works for me.  I've not had a dependency problem.  Still the installer you're using should at least give you a clue how to solve them.

I've found that UltraVNC just doesn't work.  Use TightVNC on your winders box and see if that helps.

---

### Post by Cuco3 on 2009-12-22
I found an answer.

First, uninstall these programs:

```
sudo apt-get remove tightvncserver
sudo apt-get remove xtightvncviewer
sudo apt-get remove vnc4-common

```Then, run these commands to install an older version of the removed programs.```
wget http://ftp.nl.debian.org/debian/pool/main/v/vnc/vnc-common_3.3.7-14_i386.deb
sudo dpkg -i vnc-common_3.3.7-14_i386.deb

wget http://archive.ubuntu.com/ubuntu/pool/universe/t/tightvnc/xtightvncviewer_1.2.9-22_i386.deb
sudo dpkg -i xtightvncviewer_1.2.9-22_i386.deb

```After this, you'll want to configure Synaptic to not upgrade tightvncviewer to the new version that doesn't work with UltraVNC SC. To do this, go to System > Synaptic Package Manager. Once there, type in "tightvnc" and select the tightvncviewer program. Then go to Package > Lock Version. After that, you'll have to run the following command to "ensure that synaptic and apt-get respect the same locks":
 ```
 sudo ln -fs /var/lib/synaptic/preferences /etc/apt/preferences
```
When you use the "vncviewer -listen" command, use this command instead
```
vncviewer -listen -encodings copyrect
```Source:
[http://ubuntuforums.org/showthread.php?t=1024015](http://ubuntuforums.org/showthread.php?t=1024015)
[http://ubuntuforums.org/showthread.php?t=821902&highlight=disable+updates+specific+packages](http://ubuntuforums.org/showthread.php?t=821902&highlight=disable+updates+specific+packages)
[http://www.averyjparker.com/2005/11/25/running-ultravnc-viewer-under-wine/](http://www.averyjparker.com/2005/11/25/running-ultravnc-viewer-under-wine/)

Thanks for everyone's help.

---

