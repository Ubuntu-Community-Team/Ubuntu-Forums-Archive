---
title: "Setting up a VPN"
date: 2016-03-27
forum: Networking &amp; Wireless
---

### Post by rosedale-services on 2016-03-27
I am relatively new to Linux. I have 15.10 Ubuntu desktop which I need to set as a server accessible to my employees. The info available from internet is daunting. There are only 4 employees who need access to database. When I try to run network manager I get this message. sudo start network-manager
[sudo] password for tom: 
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
Is there a laymans version to setting up a VPN available?

---

### Post by TheFu on 2016-03-28
Welcome to the forums.

Not that I am aware.
Also, anyone running a server should be on an LTS release - something like 14.04.  Support for 15.10 ends in a few months.  Newer isn't always better.  Release Support: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

OpenVPN is the normal VPN that people use. [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) There are clients for almost every OS made - if it has a network, there is an openvpn client.  OpenVPN is extremely capable with hundreds of features. That means it is flexible and can be used to meet almost any requirement.  It also means that deployment usually is NOT trivial.  For a trivial deployment, I suspect paying the openvpn guys for their nicely-packaged stuff is the easiest solution.

Running Network-Manager on a server usually isn't done.  Network-Manager is made for desktops, not servers. Servers often have more complicated networking than NM can handle well.

You didn't say how they need to access the DB.  I can think of 4 different methods, each would result in a different way for the DB access to be made.

If you really want to learn Linux, here is my best advice: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)
If you just want to solve this issue and move on, then paying someone to manage the Linux system is probably best.  

There are all-in-one distros which include a VPN and make stuff like this easier than using a stock, generic, Ubuntu system.  I can't speak about the overall security for those solutions, since I've never seen them in the wild.

If all you need is a VPN, there are tiny distros which do just that. If you also need a router upgrade, perhaps something like the highly respected pfSense would be a good choice? OpenVPN is an addon module for pfSense and relatively painless to get working.

---

### Post by kevdog on 2016-03-29
If you only have 4 employees -- possibly sftp, ssh would scale better.

---

### Post by TheFu on 2016-03-29
> **kevdog said:**
> If you only have 4 employees -- possibly sftp, ssh would scale better.

Good idea, except ...  ssh-tunneling works for technology people, but for normal end-users/DBAs, the simplicity (for the end-user) of a VPN is needed.  Had a small company.  Mostly hard-core programmers, but we had a few non-technical people who could never understand ssh. Don't know why. They just didn't care.  Had to deploy openvpn just for them. Everyone else still used ssh.  Heck, I still use ssh/scp/sftp for almost everything, thought I do use a VPN from Android because it is easier.

ssh is the swiss army knife of connectivity and file transfers.  It is amazing what can be done with ssh/scp/sftp, but it isn't intuitively obvious, like end-users need.

Deployed x2go with a remote desktop infra "inside" our production LAN.  x2go uses NX protocol, which is based on ssh-tunnels.  THAT the end-user-weenies could understand. The only downside was they didn't want to use Linux (Windows marketing/project managers), so they revolted.  Both quit our company. This wasn't the only reason, but I bet is was an important one.  People want to use skills that keep them employable both at the current job, but also in 5, 10, 20 yrs later.  Being able to use a simple remote desktop, securely, into our network, and run all the desktop tools that I installed for them wasn't good enough. They wanted MS-Project and MS-Access and MS-Word.  LibreOffice wasn't sufficient, in their minds.  I'd already forced them to use Zimbra for email (which Outlook can connect) and a web-based project management tool called Redmine (which everyone actually liked).  Deployed a DMS and Wiki for internal notes too - those didn't get used much - redmine became THE system of record for almost everything besides Zimbra.    For project-based work, I think Zimbra and Redmine are all that is needed - of course the accountants will use whatever tools they want and it isn't worth fighting with them at all.  We outsourced accounting - they used Quickbooks.

So - I re-read the OPs post and still don't know what she/he needs.  Are the employees on the same network or are they trying to access through the internet?  What is this "database"?  Is there a specific front-end that needs to be accessed or are they expected to run SQL commands directly?

We just can't help without more information. Too bad. Seems like a fun project for a day or so.

@kevdog - love the tagline. I was a newspaper boy.

---

### Post by slickymaster on 2016-03-29
*Moved to the **Networking & Wireless** sub-forum*

---

