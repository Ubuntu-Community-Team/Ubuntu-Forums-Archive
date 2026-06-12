---
title: "Networking two computers with the same username?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by warped0ne on 2008-11-03
I'm trying to share folders over a router on my desktop (Ubuntu 8.10) and my laptop (Ubuntu-Mobile).  The desktop username and the laptop username are the same (e.g. johndoe), will this be a problem.

I've already tried NFS, and it didn't work using a tutorial I found at [mybeNi]("http://mybeni.rootzilla.de/mybeNi/2007/how_to_set_up_nfs_and_how_to_share_files_in_a_local_network_with_ubuntu_linux/").

Would Samba work better? or is there something with a GUI that would be easier?

Thanks for any help.

---

### Post by cariboo on 2008-11-03
NFS is a lot easier to setup than samba, try this howto:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

You can set up each computer to be a server and a client.

Jim

---

### Post by warped0ne on 2008-11-04
Isn't there something easier?  I'm new to Linux and the only networking experience I have is with Windows and in Linux with Hamachi + Samba.  I tried the instructions at the above recommended link, but I don't know:

a) what my servername is.
b) what my domain name is.
c) what "/files" is referring to (I just want to share my entire /home folder from my desktop with my laptop).

---

### Post by k9fe on 2008-11-04
I am running 5 linux machines, mix of UBUNTU 8.04 and 8.1.  Using the same user name on all, just different netbios machine names.  Not a problem.  My shares are done in SAMBA since there are also 5 Windows machines on my home network. Never had a problem.

Good Luck, Mike

---

### Post by k9fe on 2008-11-04
Sorry, forgot the second part.  Install the SAMBA GUI and it is very easy to configure.

Mike

---

### Post by warped0ne on 2008-11-04
> **k9fe said:**
> Sorry, forgot the second part.  Install the SAMBA GUI and it is very easy to configure.

Mike

I'm looking through Synaptic now and I don't see a Samba GUI.  Does it have a different name, or do I need to go to Samba's website to get it?

Thanks

---

### Post by eks on 2008-11-04
A very simple solution I've found is to install openssh on both computers. I don't remember the package, not on a Ubuntu machine now, but I think it was called openssh-client. It will install the server also. After you've done that on both machines, open nautilus and type:

sftp://<ipnumber of the other machine>

And use the login/password for the other machine.

With this solution you don't get an icon to click, but you can access all other files on the other machine. It's just a bit of pain if the IP changes...

---

### Post by lswb on 2008-11-04
> **eks said:**
> A very simple solution I've found is to install openssh on both computers. I don't remember the package, not on a Ubuntu machine now, but I think it was called openssh-client. It will install the server also. After you've done that on both machines, open nautilus and type:

sftp://<ipnumber of the other machine>

And use the login/password for the other machine.

With this solution you don't get an icon to click, but you can access all other files on the other machine. It's just a bit of pain if the IP changes...

This is one of the simplest and easiest ways to share files between linux systems. ssh-client is installed by default on ubuntu. Install the ssh _server_ on all connected systems. The package is named openssh-server. Install the sshfs package also. After that you can open
Main Menu/Places/Connect to Server, select SSH for server type, put in the sever name (other info is optional) and hit "Connect."

With the sshfs package, you can mount a remote system to a local mountpoint just like a disk, and view files on the remote system as if they were in a local directory or disk.

---

### Post by warped0ne on 2008-11-04
EKS and LSWB,

Thank you very much.  For a newbie like me, very simple, direct instructions are the way to go.  I will try this ASAP.

---

### Post by warped0ne on 2008-11-05
I tried to use Samba through Webmin, and couldn't figure it out.  Then I set up SSH in about 5 minutes (the time it took to install openssh-server and sshfs through synaptic on both machines) and started watching movie files from my desktop on my laptop.

Thanks again.

P.S. For any Ubuntu developers out there, this is something I would probably try to make a little simpler if you want more users to switch from Windows.  I can set up a Windows network in about 5 minutes as well, and all I need is the installation CD/DVD or a USB flash drive to do it.  For this Ubuntu set up, I spent at least 6 hours between searching online and trying different things before EKS and LSWB let me know about SSH.

---

### Post by rfarmer on 2008-11-05
Thanks lswb and I agree with warped0ne. All I needed was the ability to share files, but finding these steps took some real looking.

---

