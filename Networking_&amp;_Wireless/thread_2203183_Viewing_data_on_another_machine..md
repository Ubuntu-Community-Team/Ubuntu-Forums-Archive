---
title: "Viewing data on another machine."
date: 2014-02-02
forum: Networking &amp; Wireless
---

### Post by oakridge on 2014-02-02
I have data which I wish to process on another machine on the network.  I can view this with Dolphin, Konqueror or Gwenview, but not with 'Home Folder'.  'Home Folder' is my preferred option because I am moving data between folders and this is better suited to the job.

Any ideas?

---

### Post by TheFu on 2014-02-02
There must be 30 different techniques to remotely process data. These will fall into 2 groups.
* Remote data access through something like NFS - google "ubuntu nfs"
* Remote tool access through [something like X/Windows or NX]("http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications"). 

Sorry, I don't use any of the tools that you've listed so I don't know what "Home Folder" means. Can you explain more. Sorry that I'm so ignorant.

Update:
If I were designing a solution for your needs, I'd determine how much data was involved, how much processing power was needed and determine if local data or remote data made the most sense for the processing needs.  If data processing is CPU bound, even with local data, then remote data is probably ok.  If data processing is IO-bound, then getting the processing as close to the data as possible would make more sense, even if the available CPU is slower.
If processing the data is using more than 1 physical computer, then some sort of "big data" cluster solution is likely best.  This opens 1,000s of different configuration options and solutions. It gets really complicated, really fast.

So ... more information about the specific processing and data amounts would help us help you. If this is video transcoding - I do that daily for my day job and have about a decade of experience. I have a little experience working with other very large data sets and processing those, but that was in very specialized fields and doubtful it applies to anyone else in the world. ;)

---

### Post by steeldriver on 2014-02-02
'Home Folder' is the tooltip that pops up for the Nautilus launcher - maybe that's what the OP is referring to? @oakridge can you confirm(e.g. by going to the 'Help' menu then selecting 'About')?

If so, that should support a variety of network protocols (Windows shares / SFTP / Webdav etc.)

---

### Post by oakridge on 2014-02-02
Thank you for the replies.

Yes, I do mean the icon below 'Dash Home' which calls itself 'Home Folder' but which is actually Nautilus.

The machine I want to access is dual boot Ubuntu 12.04/Windows 7.  I have tried both OSs without success.  The other machines on the network are all Windows and have no problems.  Samba, which I have used for years, is installed.

---

### Post by TheFu on 2014-02-02
We need a better description to help.
Be explicit - what have you setup on each machine and how are you trying to use it?

Does samba fit your needs and NOT work now?

---

### Post by oakridge on 2014-02-02
Three of us work from home and we have 7 computers between us.  Five are Windows 7, one dual boot and one and my Ubuntu which is also the file server.  I would prefer to use the recently built dual boot as file server because it has a 2TB HD.  All machines are happy to connect to my Ubuntu or the dual boot except mine which will connect to any machine except the dual boot in either Windows or Linux mode.  Connection is normal SMB using dotted quad protocol.  For maintenance I also use TeamViewer 9 which will connect to the Windows part of the dual boot (it has not been installed on Ubuntu).

I have used Samba for over 10 years, both here and before I retired.

I don't know quite what else to tell you - it is just a common-or-garden network.  Oh, the error message is: Could not display "smb://oakridge-dual/data".

---

### Post by TheFu on 2014-02-02
That DOES help.  

If people work from home and use the internet to communicate, then you really, really, really need a secure connection between everyone.  Using Samba over the internet is NOT secure - in the USA, every ISP I've been on blocks those ports too.  That leaves a VPN or using something based on ssh.  Getting ssh working is easy, VPNs take more effort.

Not sure I understand what you mean by "normal SMB using dotted quad protocol".  IPv4 addresses are xx.xx.xx.xx. IP is a layer 2 protocol.  SMB is a layer 7 protocol on top of TCP, a layer 3 protocol. Do you mean something else? I don't think this is important, unless you believe it matters.

I run IT servers for a few small companies that are also virtual, so I'm pretty familiar with this sort of setup architecture.

sftp is a secure way to connect all these machines to a central file server.  WinSCP or Filezilla are easy-to-use Windoz clients for sftp.  ssh/scp/sftp are secure and with ssh-keys, extremely convenient.  sftp:// URLs should work from any "home folder" (linux file manager)  and if DNS is setup to the public IP of the file server network, you are done. It works on the internal network too, but has more overhead than NFS or CIFS due to the data encryption.  If making ssh, scp and sftp available over the internet, please [add some simple security]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures") to prevent hackers free range.

If you need help with these things, ask. There are many how-to guides/links out there.  ssh-keys are much, much more secure than passwords.

---

### Post by oakridge on 2014-02-02
Thank you for your reply.  As I am now 71 it looks as though I may be a teeny bit out of date.

All the computers are in one building behind a secure firewall.  We have had not trouble viruses, trojans etc since the late 90s.

By dotted quad I mean addresses of the type 192.168.1.70.  I do not use a domain, just a workgroup.

---

### Post by TheFu on 2014-02-03
So ... if you have samba loaded on the file server, I'm confused. Can't you connect to that machine using any of the file managers?  On linux, just use a URL - smb://hostname or smb://ip-address/ to browse.  If "smb://" doesn't work - try "cifs://" .

If every machine IS on the same LAN and not "on" the internet (running a web service, email server, xyz-server), then using CIFS, which doesn't have any real encryption, is probably safe enough.  CIFS will be faster than sftp - no encryption.  sftp will work too, if you setup an ssh server on the "file server."  I use both.

---

### Post by oakridge on 2014-02-06
I think we have rather drifted away from my original question.  This was that I cannot connect to machines on the local network using 'Home Folder/Nautilus, but I have no trouble using Konqueror, Dolphin or Gwenview.

---

### Post by TheFu on 2014-02-06
> **oakridge said:**
> I think we have rather drifted away from my original question.  This was that I cannot connect to machines on the local network using 'Home Folder/Nautilus, but I have no trouble using Konqueror, Dolphin or Gwenview.


"I can't connect" isn't really much information to aid troubleshooting efforts. 
What have you tried?
What do the log files show on both the client AND the server?
What is the exact URL you are typing in?

---

### Post by SeijiSensei on 2014-02-06
Last I checked Nautilus supported smb:// URLs to access remote shares.  Did you try that?
```
smb://user@IP/sharename
```
should work.

---

