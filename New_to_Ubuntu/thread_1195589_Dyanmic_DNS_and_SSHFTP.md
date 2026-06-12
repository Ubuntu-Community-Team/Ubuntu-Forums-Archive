---
title: "Dyanmic DNS and SSH/FTP"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Tyrsius on 2009-06-24
I am having a number of problems, and its hard for me to even understand there relation to each other because of my inexperience in this area. I will try to be as thorough as possible. Feel free to point out there areas where I am wrong, as I am sure I do not fully understand everything (of even 50%) of whats involved.

First, the goal: some type of FTP accessible outside my local network. Preferably a secure one (SSH/SFTP) that I can access through filezilla or (if it's even possible) a browser.

I am using Ubuntu 9.04. I have already installed and configured (though probably not correctly) SSH and Samba. I am able to SSH into the machine inside the local network, and the file sharing through the windows workgroup to windows computers on the local network is working.

I am behind a router. I have configured it to forward ports 22 and 443 (because one of the guides I found suggested using this instead of 22). I have (again, maybe incorrectly) opened the same ports in the ssh.conf file. That section uses a line break, like this:

Port 22
Port 443

If it should use a comma instead, please let me know.

I have also set up a Dynamic DNS through dyndns.org. I am unable to ping the hostname I set up from outside the network, I get a timeout. This may be due to the router. When I check what ismyip.com I get the same ip for multiple computers on my network, which tells me the IP it sees is the router, and not the computer. If this is the case, how do I get the ip that goes to dyndns to point to the computer (I feel really stupid asking this, it seems like I should know the answer)?

I am also unable to get filezilla to connect, even inside the network. I can ssh on the other linux computer on the network, but I don't know how to ssh with windows. I know this might seem pointless since the workgroup filesharing is working, but I was trying to troubleshoot filezilla since its what (i think) I will need to access the files across the internet. Is there another method I should use, or is filezilla failing related to the problem above?

I have looked around quite a lot through these and other forums trying to get this working, or even to get a more complete understanding of how it all works. I am by no means computer illiterate, but I feel out of my league for the first time in a while here. Help would very much be appreciated.

---

### Post by prshah on 2009-06-24
> **Tyrsius said:**
> 
First, the goal: some type of FTP accessible outside my local network. Preferably a secure one (SSH/SFTP) that I can access through filezilla or (if it's even possible) a browser.

I am able to SSH into the machine inside the local network

I am behind a router. I have configured it to forward ports 22 and 443 

I have (again, maybe incorrectly) opened the same ports in the ssh.conf 

Port 22
Port 443

I am unable to ping the hostname I set up from outside the network

I will need to access the files across the internet. Is there another method I should use, or is filezilla failing related to the problem above?


If you are able to use SSH within the network, then SSH is setup correctly and all you need to do is port forwarding on the router to allow SSH from the Internet. Since you say you have done this as well, then I suspect that:
[indent]a) Either you have done the port-forwarding wrongly
b) Your router is not forwarding IP address updates to dyndns.org correctly.[/indent]

The fact that you are unable to ping your dyndns.org hostname might point to (b). 

Can you ssh from outside the network using your external IP address instead of your dyndns hostname. An important point; you have to be on a separate Internet connection (not the same Internet connection as the one where your SSH server is). Eg, if your SSH server is on the corporate network, then you must connect through another dialup or another Internet account (NOT the corporate network) to be able to check if you can SSH to external IP of your SSH server.

The ports have to be opened in /etc/ssh/ssh**d**.conf, not ssh.conf. Also you should not open Port 443 in this; this has nothing to do with ssh.

Once you have ssh setup properly, you can use SSHFS/scp from any linux machine, or puttyscp from any Windows machine to transfer files back and forth securely (among a whole host of other options.)

Exposing your Windows Shares to the outside world is a terrible idea and I cannot urge you enough **not** to do this,

I have no idea what filezilla is or what is does so I cannot advise in this regard.

Do post back in this thread if you have further troubles.

---

### Post by Bucky Ball on 2009-06-24
prshah, Filezilla is really handy. I use it for working on web site and moving things to, from and around on the server and my machine. Cool.

[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by Tyrsius on 2009-06-24
First off, thank you prshah.

I removed the port 443 from the sshd.conf.
You warned against opening up the Windows Shares to the internet: is there same way that this process would do that? If so, how do I block access that is not authorized? I though this was the whole point of SSH?

I was finally able to SSH in from outside the network by setting an additional port forwarding rule on my router, but why this worked confuses me. I have a Dlink 4300, and while the port forwarding interface is not as straighforward as a Linksys WRT, there was a section that explicitly said it was for FTP connections from the internet to a computer inside the network.

You are probably not familiar with the router menu, but screenshots are easy to come by so I am hoping someone can explain this to me.

In the router menu Advanced > Virtual Server, you can specify port forwarding (or so it seems) to an Ip inside the network. When I did this, it did not allow SSH. When I set a rule from Advanced > Gaming, however, it did work. Can anyone explain the difference in what these two sections are doing? If Gaming is actually the port forwarding section I needed, what the hell does the Virtual Server section do?

I did not remove the port forwarding rule I had entered in Virtual Server, so it and the one from Gaming are both present, but its working and I am afraid to mess with it. I will have to test filezilla tomorrow, as I do not have access to a machine outside the network with it installed right now.

What I am hoping to eventually be able to do is get an ftp set up that can be accessed through a browser (with read only permissions). Can anyone point me in the right direction for that?

---

### Post by prshah on 2009-06-24
> **Tyrsius said:**
> how do I block access that is not authorized? I though this was the whole point of SSH?

When I set a rule from Advanced > Gaming, however, it did work. 

What I am hoping to eventually be able to do is get an ftp set up that can be accessed through a browser (with read only permissions). 

SSH is only a "transport" layer; it encrypts data that is being transmitted between the client and the server so that intervening computers/devices cannot "snoop" the data.

SSH cannot be used to "block" arbitrary unauthorized access. For example, even with a secure SSH setup, a machine can still be compromised via http (80), ftp (21), samba (Windows sharing, 135-139, 443), telnet (23), etc; these are all irrelevant to SSH.

There are a number of services that can run "over" SSH, such as rsync, scp (secure copy), sshfs (ssh file system), etc; but you cannot "push" existing services such as samba or ftp to run through ssh without considerable effort.

To block arbitrary accesses, you need to use a firewall, such as the iptables/ufw combo in Ubuntu.

As for the issue with the router; each router has their own terminology and (il)logic behind the setup interface. As long as it's working, don't bother too much about it; trying the same thing in another router will turn out to be a whole new experience, every time.

btw, for FTP, you need to use port 21, and an ftp server such as vsftpd.

The fact that browsers can be used to access FTP sites is a purely browser-side technology and does not require you to do any additional setup aside from setting up an ordinary FTP server.

---

### Post by Tyrsius on 2009-06-24
Once again prshah you have been extremely helpful.
 
I managed to get vsftpd set up and I can access it from outside the network with read only permissions. The only problem I have left is in regards to the configuration of vsftpd, which apparently (as far as i know) can only be done through gedit of the vsftpd.conf file.
 
I've disabled anon-users and allowed local users, as well as restricted vsftpd to a user I set up specifically for the ftp. The only problem is that after logging in you are presented with the entire filesystem (/) instead of the /home directory of the user specified. How can I configrue vsftpd to only look in (or mount, w/e the term here is) a specific directory?

I also have side question for anyone who might know more about FileZilla. I am able to connect to the computer through FileZilla using port 21 and the ftp account, but not through port 22 using any of the accounts. I should probably ask this on the filezilla forums, and I would head there next, but is there a way to setup scp (or another SSH method, it says its using sftp) for filezilla, or is it only possible to connect to the FTP server?

---

### Post by prshah on 2009-06-24
> **Tyrsius said:**
> How can I configrue vsftpd to only look in (or mount, w/e the term here is) a specific directory?


It's been a while since I have setup a (vs)ftp server, so I can't quite remember; however, I do recall adding ```
chroot_local_user=YES
``` (or something similar) to the vsftpd.conf file will restrict users to their home directories. Yes, the config is purely though text file.

sftp = sshfs(/scp). Quite the same.

---

