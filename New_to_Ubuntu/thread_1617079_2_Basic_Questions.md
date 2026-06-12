---
title: "2 Basic Questions"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by RustyWyatt on 2010-11-08
Howdy,

As you will see from my signature I have been using Ubuntu for sometime.  I have been a user and have not made to much effort to expand my Ubuntu knowledge as is found “under the hood”... 

I have generally managed to accomplish what I needed Ubuntu to do (such as basic networking) by trial and error and I probably had a real mash-up of commands/hacks to do the simplest of things without ever knowing what really worked nor how to do it again! 

As an example, I could see my NAS from my desktop but not from my laptop and yet I could see my desktop from my laptop.  I tried to get several backup/sync solutions to work but they could never see my NAS.

In the last few days I have upgraded my laptop and desktop to Ubuntu 10.10 with completely new installs and eliminated all of my M$ Window's partitions!  I also created separate partitions for “/, (root?)” and “/home” and a “swap” partition equal to my ram in each machine (thanks to all for this tip!).

I have two questions that will probably seem very basic so please be gentle ;-)

1- I need to understand networking better so I can connect my laptop, desktop and NAS (Thecus N2100SM) together for backing up and synchronizing my file systems.  I have tried to read the “man” pages am I am very confused.  I don't think I need to use any “windows” network stuff between my Ubuntu only systems and my NAS.  But I am confused re: SMBA, mounts, CIFS and Windows, shares, mounting etc ;-(
[B][I]
Can anyone point me to a simple document for setting up one network to allow me to accomplish my goals as outlined above?[/B][/I]

2 – I upgraded my laptop to 10.10 first and spent sometime configuring it to my liking.
[B][I]
Is there a simple way to clone all of my configuration modifications and program installations from my laptop to my desktop and keep the two desktop/systems sync'd in the future so that I have the same environment on both devices?[/I][/B]

All info and comments Greatly Appreciated!

Tom

PS  10.10 seems to be running great with no installation problems!
t

---

### Post by lykwydchykyn on 2010-11-08
1. "Networking" is a vague term; I'm assuming you want to share files between computers.  What's confusing about this on Linux is that you have your pick of file sharing protocols to do this with.  My personal preference is just to use SSH -- just install openssh-server on every machine, then you can browse the remote filesystem in Nautilus (I think the format is "ssh://servername/path/to/file", but I'm not sure since I use KDE and it's different).

Of course, you may not have control over what's on the NAS.  Most NAS devices will use SMB/CIFS (Samba, a.k.a. Windows file sharing) if nothing else.  

2. Depending on what sort of configurations we're talking about, it's most likely stored in your home directory.  Desktop settings, default application settings, and things like that are stored in your home.  Keeping your home directory synchronized between machines will accomplish this, though I don't know a simple way to do this.  Personally I'm averse to having scripts automatically overwriting my data, so I do these things manually.

Another possibility is to store your home directory on the NAS and mount it remotely over NFS, but that would be a problem if you take your laptop somewhere else.

If any of these suggestions bear more explanation, just ask.

---

### Post by Quackers on 2010-11-09
Clonezilla for backup disc/partition images for me :-)

---

### Post by HermanAB on 2010-11-09
Howdy,

In order to get a LAN up, you have to configure three basic things, otherwise the devices cannot talk to each other: IP address, Netmask, Default gateway.

The easiest way to accomplish the above, is to plug all devices into a home router, which will set them up via DHCP.

Windows, by default use CIFS networking (used to be known as SMB).  However, Windows can also speak NFS, FTP, SSH, HTTP and others with a little configuration work.

NFS is a free download from Microsoft called Windows Services for UNIX.  FTP is best handled with FileZilla Server and Client, while SSH is done with Cygwin or PuTTY.

On the Linux side, connecting to other servers is quite trivial.  Run the Nautilus File Browser and click File, Connect to Server, select the protocol and la voila.

---

