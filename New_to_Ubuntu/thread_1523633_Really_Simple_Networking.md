---
title: "Really Simple Networking"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by appalbarry on 2010-07-03
Wow, this should be easy, but web searches have found nothing.

Computer A - Dell desktop with Ubuntu installed via the Windows installer. EVERYTHING works very well!

Computer B - Acer laptop with Ubuntu installed via the Windows installer. EVERYTHING works very well!

Connected via wireless router.

I want to access ONE folder/directory on the Desktop from the Laptop.  I've messed with Samba, and NFS, and anything else that looks likely but can't make it work.

Bizarrely I CAN do a remote desktop to control the desktop, and can print to the attached printer.

After ten years and maybe twenty attempts, this is the first time that I've been able to say that I can stay with Linux for EVERYTHING I do (thanks WINE!) but this one simple task is a deal breaker for me.

Help!

Ubuntu 10.04 LTS - the Lucid Lynx

---

### Post by cariboo on 2010-07-03
NFS for Ubuntu to Ubuntu is probably the easiest way to share a directory have a look [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") for a howto.

---

### Post by jimrz on 2010-07-03
try open-ssh, the client is included in the default install and the server can be easily added to your desktop via synaptic

---

### Post by HermanAB on 2010-07-04
Hmm, the easiest way to share files with Windows is via FTP and the hardest way is via Samba.

So, you could go to FileZilla project and install Filezilla server and client on Windows, then use Nautilus File, Connect to Server.

Otherwise, have a look at this:
[http://www.aeronetworks.ca/nfs-howto.html](http://www.aeronetworks.ca/nfs-howto.html)

---

### Post by appalbarry on 2010-07-17
Both systems are running Ubuntu, which is why I thought this should be easy.

---

### Post by appalbarry on 2010-07-17
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) also looks promising, but I'm out of time.  This SHOULD be easy!

---

### Post by Miljet on 2010-07-17
Do I understand correctly that both installations are WUBI? If so, I don't know what effect that will have on using the tools described above.

I agree that simple file sharing should be easier between 2 Linux machines. I use rsync and SSH to backup to an old machine I use as a server of sorts. Instructions here: [http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh](http://ubuntuforums.org/showthread.php?t=15082&highlight=ssh)

But to share files between my computer and my wife's, I use NFS. [http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs)  and [http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

There are many other ways to share files under *nix, but these two were the easiest for me.

---

### Post by egalvan on 2010-07-17
> **Miljet said:**
> 

I agree that **simple file sharing should be easier between 2 Linux machines**.

Simple file sharing between 2 Linux machines **IS **simple...

Fire up Nautilus,
 right-click on folder you wish to share
 choose "Sharing Options"
choose options needed/wanted.
All done.
Any simpler?

> But to share files between my computer and my wife's, I use NFS. [http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs)

There are many other ways to share files under *nix, but these two were the easiest for me.

NFS is the method I use for Linux-Linux network.

---

### Post by baddnady23 on 2010-07-17
NFS makes this incredibly easy.  Heres the tutorial I followed on several occasions:

[http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+Server%2FClient]("http://ubuntuforums.org/showthread.php?t=249889&highlight=HOWTO%3A+NFS+Server%2FClient")
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")

---

### Post by theozzlives on 2010-07-17
You see, with WUBI (running under Windows), you don't have two Linux machines. You have two Windows machines running virtual Linux. You'll get more out of dual boot, or strictly Linux.

---

### Post by appalbarry on 2010-07-17
"You see, with WUBI (running under Windows), you don't have two Linux machines. You have two Windows machines running virtual Linux."

Really? Still seems to run better than Windows.

---

### Post by bodhi.zazen on 2010-07-17
> **theozzlives said:**
> You see, with WUBI (running under Windows), you don't have two Linux machines. You have two Windows machines running virtual Linux. You'll get more out of dual boot, or strictly Linux.

That is not true. Wubi is often mis understood, wubi is dual booting not virtualization.

See

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by appalbarry on 2010-07-17
OK, what I've finally done is go the desktop box, right click the folder in question, and try to set sharing.

Didn't work of course because I'm a lowly user.

So I launched **sudo nautilus**, and repeated the procedure, and it would seem the folder is shared.

Still can't get to it from the laptop though, although it seems close.  I suspect that various things done following other processes might have gummed things up.

---

### Post by Miljet on 2010-07-17
> Simple file sharing between 2 Linux machines IS simple...

Fire up Nautilus,
right-click on folder you wish to share
choose "Sharing Options"
choose options needed/wanted.
All done.
Any simpler?


I'm sure that it is just that simple for you on your network. But for me and the dozens of others that ask here, the shared folder just doesn't show up on the other machines on the network without further configuration.

---

### Post by appalbarry on 2010-07-18
OK, what seemed to work was to:

1) go to the desktop PC(aka server); 
2) launch Nautilus as superuser (Terminal: sudo Nautilus)
3) Find the folder to be shared and right click; choose Sharing Options
4) Select what you need, then click OK etc.

I think that may have been all that was needed , although I had previously tried all of the complicated methods linked in previous posts.

One thing I did belatedly which really helped me, was to rename each machine.  Previously I had just accepted the UBUNTU default, so I had two computers both called "Ubuntu".  

Typing sudo gedit /etc/hostname in Terminal will allow you to change the name of the computer, in this case to "Desktop" and "Laptop" respectively.

As I say, I think that this was enough, but aren't about to reinstall to find out.

---

