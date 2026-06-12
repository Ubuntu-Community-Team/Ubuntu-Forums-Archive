---
title: "Accessing Files Outside of Network"
date: 2016-04-20
forum: Networking &amp; Wireless
---

### Post by falstad007 on 2016-04-20
I'm pretty new to Ubuntu and I've installed and been playing with Ubuntu Server on a spare machine.

What I'm looking for is a way to access files outside of my network.

I've set up Samba and VSFTPD, but Samba only works in-network and FTP would have me download any programs or files that I'd like to modify (i.e. I can't open a picture, stream a video, or open modify and save a document).

I've heard about open-source cloud utilities, but I just want to be able to access my files through Explorer rather than going through a web interface.

Is there a way to essentially set up my own NAS on Ubuntu Server or have a program like Samba that points outward?

---

### Post by TheFu on 2016-04-20
FTP and Samba are not secure enough to be used of the internet.  Use **SFTP** instead - built-into the openssh-server package.  Of course, if you like you can setup a full VPN using something like openvpn to be able to use samba/anything else over the internet.  But sftp is 1000x easier and provided you don't use passwords, much more secure.

There are sftp clients for every OS that has a network stack.  On Windows, WinSCP is reasonable, but there are other clients.
If you have sshfs on the client OS, then you can "mount" the remote storage, securely and make it appear to be local to the machine. Then you can do almost anything on it - there are some limitations, of course.

Watch out for those "cloud" things. Most are completely dependent on HTTPS for security. There are a number of reasons why that might not be sufficient, but it depends on your use cases.

I'm always confused when someone says they want plain FTP.  That protocol should have been killed off around '95 - you know - when telnet was basically killed in favor of ssh.

So - just to be clear - load openssh-server and fail2ban on the "server" and load any ssh client/scp client/sftp client on the client machine.  You'll need to open a port on the edge router and forward the port to a static IP for the server and the normal port for ssh (22/tcp).  ssh, scp, sftp all share this port.   I use port translation on the router    WAN ---> 63022/tcp --->  ROUTER ---> 22/tcp ---> Server

Fail2ban will block brute force attacks and the default config does ssh on port 22 already.

Every Linux file browser has ssh/scp/sftp built-in.  ssh://WAN-IP:63022 ... will get you to the files, if you've setup everything correctly.  You'll want to prevent password logins from the WAN for security reasons. That just means you need to create ssh-keys for each client and place the public key on the "server" in the ~/.ssh/authorized_keys file.   On Linux, the easy way to do that is with the **ssh-copy-id** command.  check the manpage for details.

ssh is one of those few tools that is both more secure AND more convenient.  By using 4K keys, the connection is basically unhackable (brute force) and secure (except for SW bugs).  After you get this working, you'll probably want to secure it a little more, monitor all the hacking attempts, and keep the system patched at least weekly.  There have been serious bugs found in ssh, but those are corrected extremely quickly becuase the world manages all servers over ssh.  scp and sftp get those benefits for free.

Forget about a "NAS" for remote access, if you care at all about security.  There are so many flaws in almost every one of those implementations, it is scary.  I laugh reading about WD and their internet access to files - it is like they don't have any clue about security based on the implementation.  They aren't alone.  People who connect storage to their routers and actually believe that storage is only available to them?  Really?    I've got a bridge to sell these nice people who believe all marketing material.

Use ssh. Be happy.

---

### Post by May_Masters on 2016-04-25
Well, another option might be to setup a VPN Tunnel and you could use all your services as you'de inside your home net ;)

---

### Post by TheFu on 2016-04-25
> **May_Masters said:**
> Well, another option might be to setup a VPN Tunnel and you could use all your services as you'de inside your home net ;)

True. If you go the VPN way, be certain to use openvpn in IPSec mode, never use pptp, which was hacked almost 15 yrs ago and never fixed. 

ssh is relatively easy for nerds to use. ssh is the 'swiss-army-knife' of secure network connectivity. Most folks don't know all the features it has.  For example, I run a remote desktop thru ssh-tunnels with about 2-3x faster performance than VNC.  It is pretty easy to remotely edit files using rsync and almost any Linux editor ... which happens automatically through ssh tunnels.  Lots of things like that sorta "just-work" through ssh.

openvpn is hard to setup, but easy for normal people to use. If access to more than just files and linux systems is desired, definitely setup openVPN. Plus, ssh works fine through openvpn tunnels, though it will be slower, there isn't any harm.

---

