---
title: "Lubuntu/Remote Desktop Problems"
date: 2014-06-27
forum: Networking &amp; Wireless
---

### Post by awanpmjadb on 2014-06-27
I'm trying to set up remote desktop access to my server which is running the latest Lubuntu from my Lubuntu (same version) netbook.  Both installations are fresh installs save for the installation of wifi drivers.

I followed this guide: [https://wiki.ubuntu.com/Lubuntu/RemoteDesktop]("https://wiki.ubuntu.com/Lubuntu/RemoteDesktop")

I successfully installed openssh-server and vino.  

I configured vino with "vino-preferences" and set vino to run at startup and checked to make sure it was running and listening on port 5900.  It was.

I forwarded ports 5900 and 22 on my router.

I successfully ssh'd to my server.

Attemting to connect to the vino server with "vncviewer localhost:12345 &" (I inserted my local host) gives me the following error:

> vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server

I'm stumped.  Googling has failed me after two days of fussing.  I need the help of smart people.  What information is required for assistance?  

Thank you for any help.

---

### Post by TheFu on 2014-06-28
I've never use vino.
To run a GUI program on a remote linux system, there are a few different ways. If the internet isn't involved, it is relatively easy (like on a local LAN).
* X/Windows nominal forwarding
* VNC
* RDP
* NX
* or just plain old CLI connections via ssh.  ssh is what Linux/UNIX admins use 99.99999% of the time.

RDP and VNC and X/Windows are NOT secure. They do not encrypt traffic. Never open those ports to the internet - 5900-5950 are examples of those ports - do NOT open those on your router.

NX protocol is a little more efficient than RDP or VNC AND it includes ssh tunneling as part of the solution. It is not optional.  ssh tunnels have been used for 20 yrs to provide secure connections between systems around the world.

Ok  - so NX is the protocol to be used, but there is a problem.  With 13.10 and later releases, the FreeNX server hasn't been ported (I think the  project is dead). It seems, though I haven't tried it yet, that x2go is the newer NX-based solution.

Of course, we can just use a full-VPN and use RDP or VNC if we like. OpenVPN is the solution for that, but it is generally non-noob friendly. A good understanding of routing and firewalls and encryption is needed.

With all these solutions, only 1 port needs to be open on the firewall - the VPN or ssh port.

So, if you want to get vino working, then get ssh working from everywhere first. Then get vino working inside your HOME network and add the ssh tunnel in there. Finally, get both working from the internet. By breaking down the problem into smaller parts, reviewing the log files carefully (even if there isn't an error), you'll solve this. There are many tutorials for ssh - may want to check youtube too. [http://askubuntu.com/questions/4474/enable-remote-vnc-from-the-commandline](http://askubuntu.com/questions/4474/enable-remote-vnc-from-the-commandline) might help too.

I hope this all makes sense.

---

### Post by awanpmjadb on 2014-06-28
Fu - Thanks so much for your response.  That was very informative.  It confirms that I really need to educate myself a lot further.

i have ssh working both locally and from outside.  I'm not sure what I'm doing wrong as far as vino is concered.  I've tried other vpn servers too.  I'd already used the link you included to help me troubleshoot my problem, but to no avail.  I'll dig in again today.

My "server" is a busted up netbook with a broken screen/touchpad/etc that I bought cheap on ebay which is running deluge with webui and sharing my files for xbmc via samba.  Basically, I just want to be able to access it via vpn locally so that I don't ever need to touch the piece of junk again.  The computer I use is identical and fully working, so I just swapped hard drives to get things set up.  

Is there no simpler solution here?  Thanks again.

---

### Post by TheFu on 2014-06-28
x2go should be easier to setup.
Also - take a look at plex - it is the best DLNA server I've found, though not being F/LOSS does bother me a little.

With Linux, we trade "easy" for 10,000x more configurable. That's the trade-off.

Does Vino work locally without the ssh tunnel? Get that working first, then setup an ssh-tunnel when you want it remote. Think of ssh and vino as different problems - they are.  

Why use samba at all?  I'm curious. For Linux-to-Linux on the LAN, nfs is much faster and don't have the limited file permissions that samba forces.  Over the internet, use sftp - if ssh is working and you didn't disable sftp/scp, then it is already there - ready to be used.  Also - be certain you DO NOT allow password-based authentication for ssh.  This is not secure. Use keys.  It is easier AND more secure - how often does THAT happen?!  

If I load openssh-server, I load fail2ban too. Easy security if the server listens on port 22 (I let the router do the port translation) so the defaults are fine.

Don't know those other programs. I'm a CLI-guy.

---

### Post by awanpmjadb on 2014-06-28
> **TheFu said:**
> x2go should be easier to setup.
Also - take a look at plex - it is the best DLNA server I've found, though not being F/LOSS does bother me a little.

With Linux, we trade "easy" for 10,000x more configurable. That's the trade-off.

Does Vino work locally without the ssh tunnel? Get that working first, then setup an ssh-tunnel when you want it remote. Think of ssh and vino as different problems - they are.  

Why use samba at all?  I'm curious. For Linux-to-Linux on the LAN, nfs is much faster and don't have the limited file permissions that samba forces.  Over the internet, use sftp - if ssh is working and you didn't disable sftp/scp, then it is already there - ready to be used.  Also - be certain you DO NOT allow password-based authentication for ssh.  This is not secure. Use keys.  It is easier AND more secure - how often does THAT happen?!  

If I load openssh-server, I load fail2ban too. Easy security if the server listens on port 22 (I let the router do the port translation) so the defaults are fine.

Don't know those other programs. I'm a CLI-guy.

Thanks again!  You're clearly in a vastly different league than I am, linux-wise and likely otherwise.  I'm using samba to share with my Raspberry Pi running Xbian.  I'm using samba only because of the familiarity, and because it worked easily.  

As for using keys, I'm unfamiliar with the process, though I undestand the basic principle.  I'll read up on it.  

I'll see if I can get Vino to work without the ssh-tunnel and try your other suggestions and post my results later today.  

I really appreciate the help.

---

### Post by steeldriver on 2014-06-28
How did you set up the tunnel? what is your SSH connection string exactly?

Also what version of Ubuntu? You mention the versions are the same, but don't say what it is. Some of the default connection settings for vino-server have changed in 14.04, I think: see here --> [http://ubuntuforums.org/showthread.php?t=2218554](http://ubuntuforums.org/showthread.php?t=2218554)

---

### Post by awanpmjadb on 2014-06-28
So I'm trying to figure out how to use x2go.  Its gui appeals to me (and my noobness).  I followed the instructions on their site for installation of the server and did so via an ssh connection to my server computer.  I then installed the client on my netbook and am trying to figure it out.  Should I be using LXDE as the session type?  I assume yes, since I understand it to be what lubuntu uses (--> why it's "faster").  Also, when setting up my session it has a line that reads, "Use RSA/DSA key for ssh connection:" What do I need to do here?  To connect to my server computer via ssh currently, I have to type in my password.  I believe this is what you were talking about when you said not to use a password and to use a key instead.  How do I use a key instead?  If I leave the key field blank and attempt to connect it shows my login username and prompts me for my password.  When I enter it, it does its thing and then fails with the errror, "Unable to execute: startlxde".

---

### Post by awanpmjadb on 2014-06-28
> **steeldriver said:**
> How did you set up the tunnel? what is your SSH connection string exactly?

Also what version of Ubuntu? You mention the versions are the same, but don't say what it is. Some of the default connection settings for vino-server have changed in 14.04, I think: see here --> [http://ubuntuforums.org/showthread.php?t=2218554](http://ubuntuforums.org/showthread.php?t=2218554)

I'm using Lubuntu 14.04.  The SSH connection string I'm using is: > ssh -L 12345:192.168.0.1:5900 username@192.168.0.100 where username is replaced with my well, username.

---

### Post by awanpmjadb on 2014-06-28
Okay, so I was too quick to post a reply with more questions.  I read a tutorial on [how to setup ssh keys]("http://www.guyrutenberg.com/2007/10/05/ssh-keygen-tutorial-generating-rsa-and-dsa-keys/").  What I did:

> picard@herer:~$ ssh -L 12345:192.168.0.1:5900 USERNAME@192.168.0.100
USERNAME@192.168.0.100's password: 
Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

*** System restart required ***
Last login: Sat Jun 28 08:36:10 2014 from 192.168.0.105
USERNAME@server:~$ ssh-keygen -t rsa -b 2048
Generating public/private rsa key pair.
Enter file in which to save the key (/home/USERNAME/.ssh/id_rsa): mykey
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in mykey.
Your public key has been saved in mykey.pub.
The key fingerprint is:


I then copied mykey.pub to the network and moved it locally onto my netbook.  I then directed x2go to the file and attempted to connect.  It still prompted me for my password, and then afterward it asked for my passphrase.  It appeared to not work as it continually prompted me for my passphrase until it failed.  I'm confused.

---

### Post by TheFu on 2014-06-28
ssh-keygen
ssh-copy-id

ssh has to be picky about file permissions both locally and on the remote machine. Best to use **ssh-copy-id** to setup stuff on the remote machine.

The public key needs to be on the remote system BEFORE using ssh. Never share the private key - NEVER.

I haven't setup x2go here ... 14.04 is still a little too new to risk it for us. Maybe next month.  There was a clear how-to posted to these forums in the last 2 months - it was reasonably clear, to me anyway.

Don't worry about the learning curve. You'll get there, but it takes time and some struggle for all the subtle things to "click" in your brain. We all go through it.  It took me years to learn/notice some really great things - the **ssh-copy-id** tool is an example. Since learning that, setting up key-based ssh credentials has become trivial.  I also use ~/.ssh/config for everything now ... only took me 15 yrs to notice it. ;(  

There is always someone who knows more than me out there on any specific topic.  This week, I bumped into [Larry Wall]("https://en.wikipedia.org/wiki/Larry_Wall") and chatted a few minutes at YAPC:NA. Extremely humbling and a nice person too. He's still learning stuff about the language he invented. ;)

---

### Post by awanpmjadb on 2014-06-28
Well thank you again for your help and your wise words.  You seem like a professional educator.  Anyway, I figured out x2go and got the public key working.  There's lots I would like to learn still, but for now, problem solved.

---

### Post by TheFu on 2014-06-28
Please mark the thread as SOLVED to help others. My signature has a link for that.

How is x2go?  Fast? Does audio work?

---

