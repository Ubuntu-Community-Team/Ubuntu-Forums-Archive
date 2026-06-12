---
title: "Connecting to Ubuntu over Internet from Windows machine"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Ducimus on 2007-01-16
With the occasional need to work from another location, i am trying to set up my Ubuntu machine with Samba on it to allow access to the files over the internet from Windows based machines. Though I am not really sure how? Please help

---

### Post by gilgongo on 2007-01-16
Samba is not for use over the public Internet. Well, you could use it, but you would be mad. Much better to use a VPN setup like FreeSWAN or PPTP (the latter is way simpler, but doesn't find favour with geeks for various reasons).

So the first question is, do you, or somebody you can contact, have control over a) the firewall, and b) somehting on the local network that can server a VPN?

---

### Post by robertpolson on 2007-01-16
If you were to do it the other way around, it would have been very easy

[www.logmein.com](www.logmein.com)

---

### Post by DerHesse on 2007-01-16
How about ftp to access your files?
You'd need dyndns and a router to forward Port21 to your box.
I would NOT use Samba, and NOT "Client for Microsoft Networks" on your Windows Notebook.

---

### Post by jtc on 2007-01-16
Yes, VPN is probably the way to go if you want to use samba outside a local network. Myself I'd like to mention [OpenVPN]("http://openvpn.net/").

Another option which would have worked really well if Windows hadn't been Windows would have be to tunnel Samba through SSH. The spoilsport in this case is that Windows won't allow you to choose of port of your own. Instead you'll first have to disable the machines own File sharing. If you want to try it out, take a look at this [tutorial]("http://www.cs.toronto.edu/support/remote_ssh_tunneling_windows_samba.html").

A diffrent approach is to use SFTP/SCP instead. The downside is that if you use the normal (and free) clients such as [WinSCP]("http://winscp.net/") and [FileZilla]("http://filezilla.sourceforge.net/") you won't really get your data naturally integrated into Windows.  If you want to use SFTP perhaps the commercial product [SftpDrive]("http://www.sftpdrive.com/") could be an option?

---

### Post by ehowell on 2007-01-16
I do the same thing, so I use SSH and [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").

My Ubuntu server at home runs an openssh server (set up using the [How-To Forge guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")) and at work on Windows I can use Putty to connect to the home computer. This way I can work directly on the files as if I was in terminal mode. If you need a GUI then I think you will need to go the Open VPN route (slower).

You have to have PuTTY connect to the IP address of your home computer, and remember to forward your port to that computer if you have a router installed. 

I also use Dynamic DNS ([www.dyndns.org](www.dyndns.org)) which is a free redirect from a subdomain (example.homelinux.com) to your IP address so if your IP is dynamic you don't get lost :)

Hope that helps, it is nice to be able to work on the home computer from work!

---

### Post by pod25 on 2007-01-16
If your happy to use command line, then use Putty (SSH) excellent little tool.

If you are not happy with command line, then install Webmin onto the ubuntu machine, then it doesn't matter where you are in the world so long as you have internet access, webmin is the perfect tool to admin your ubuntu.

---

### Post by Ducimus on 2007-01-16
Well this isnt me yet... ](*,) 
still trying to get it going thanks so far

---

### Post by Ducimus on 2007-01-16
ok got webmin, seems to be the key, now it's just a matter of figuring it out and setting it up so someone who is non command line friendly can access the system 
or myself for that matter

---

### Post by Ducimus on 2007-01-17
OK Perhaps I am dumber than i thought

---

