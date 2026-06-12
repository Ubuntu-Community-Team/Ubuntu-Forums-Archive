---
title: "sshfs will not connect"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by tropdoug on 2008-08-02
Hi guys

I had a working file sharing setup which broke after I thought I might try nfs rather than sshfs. (bad move) 

I have uninstalled nfs and unedited all the changes in various files. I have followed the step by steps to installing sshfs from this forum and also [COLOR=Blue]http://firmit.wordpress.com/2008/07/07/mount-remote-filesystem-over-ssh-with-sshfs/[/COLOR]
plus a couple of others. I have been meticulous and yet when I try to connect either from my laptop or from my desktop this is what I get

douglas@desktop:~$ sshfs douglas@10.1.1.4:/media/share
read: Connection reset by peer

and I cannot do anything. What does "connection reset by peer" mean?

Hope someone can help.





</div></div>

---

### Post by tropdoug on 2008-08-09
Bump!

---

### Post by Iowan on 2008-08-09
I haven't used sshfs (yet), but the [link]("http://firmit.wordpress.com/2008/07/07/mount-remote-filesystem-over-ssh-with-sshfs/") you mentioned uses the example > sshfs remote_username@remote_ip: /media/ext_sys
Notice the space after the colon.

---

### Post by jimv on 2008-08-09
Do you have OpenSSH server setup on the other machine?  If so, does "ssh douglas@10.1.1.4" work?

---

### Post by tropdoug on 2008-08-09
Thanks for the help guys.

Ok Lets go right back to the beginning, cos I must be doing something dumb.

I have a desktop machine static IP address 10.1.1.5 (see screenshot 1)

This machine connects to my router which is IP address 10.1.1.1 by ethernet cable

My wife has a laptop static IP address 10.1.1.4  - wireless connection gateway address 10.1.1.1

I can Ping both machines both ways (laptop to desktop and vice versa) 

I have added myself (Douglas) as a user on Kims laptop (screenshot 2) and as a member of the 'fuse group (screenshot 3) I have done sudo mkdir /home/douglas on the laptop and the directory does exist. 

The laptop has host name 'laptop'. The desktop has host name 'desktop'

sshfs is set on both machines. Modprobe fuse has been run on both machines and /etc/modules lists 'fuse' on the first line on both machines. 

Below are the commands and their results I have tried from the desktop to the laptop. I also tried from mthe laptop to the desktop and got exactly the same results.

```
douglas@desktop:~$ sshfs douglas@10.1.1.4: /home/douglas
read: Connection reset by peer
``````
douglas@desktop:~$ ssh douglas@10.1.1.4: /home/douglas
ssh: 10.1.1.4:: Name or service not known

``````
douglas@desktop:~$ ssh douglas@10.1.1.4
ssh: connect to host 10.1.1.4 port 22: Connection refused

```I have tried using the 'conect to server' command from the Places menu and entering in details inclduing port 22 as per the article previously mentioned -- nada!

I am getting really frustrated as everyone else is up and running in 2 minutes and I am blocked after two weeks. 

The only other thing I was wondering is maybe the firewall on the router is denying the request? although if I can ping 100% succesfully then surely that shouldnt be so. 

AAARRRGH!

Thanks for looking at this fellas, please help if at all possible.

---

### Post by jimv on 2008-08-10
You don't appear to have the SSH server installed on the machines.  Do this on the machine(s) that you want to be able to serve files from:

sudo apt-get install openssh-server

Once you so that, sshfs will work.  Also, you can use the SSH command to log into the other machine and run commands if you want.

---

### Post by tropdoug on 2008-08-12
You were right Jimv not sure how but synaptic did not install everything I needed, I probably selected the wrong thing. Doh!

Ok so I installed the openssh server and then in a terminal did 

```
douglas@desktop:~$ ssh douglas@10.1.1.4: /home/douglas
ssh: 10.1.1.4:: Name or service not known

```

It took a while to come back so obviously they are talking. A thought:- On Kims laptop I set it up with two partitions - one for the system and one for /home. When I use Places>Computer I have to click "26.9GB Disk" and then put in the admin password to access the /home files. 

When I click the home icon in the panel bar I go straight there. So I am thinking the path is wrong. But when I look at the top of the nautilus window using either method, all I see is /home/douglas. I think my understanding of paths in Linux may be a bit off. 

What would you suggest?

---

### Post by kdorf on 2008-08-12
The correct format for the sshfs command is this:

sshfs username@your_server:/remote/path/to/mount /local/mount/point

In the commands you've tried thus far you've omitted either the local mount point or the remote one. Also, SSH doesn't take a path. You need to remove the colon and folder from the ssh command like so:

ssh douglas@10.1.1.4

If that command works, your SSH server is installed and you can proceed.

---

### Post by tropdoug on 2008-08-13
Thanks for that Kdorf, I must admit the format for teaching newbies the correct commands confuses me, which is why I use the actual wors like my name. Anyway I will get used to it, I am sure. 

I will not be able to try this for a couple of days so I will post back here as soon as I have done so. 

Once again all the assisters, thank you.

Douglas

---

### Post by ZyZxx on 2008-08-23
Your format is incorrect try this on both machines. kdork made note of this. 

-- completely remove openssh-server to reset your keys
sudo aptitude purge openssh-server

-- reboot
sudo reboot

--re-install openssh-sever on each machine
sudo aptitude install openssh-server

-- make sure you have sshfs installed
sudo aptitude install sshfs

-- add local user in your case replace <local user> with douglas
sudo adduser <local user> fuse

-- create a mounting point. looks like you've done this /media/share
sudo mkdir <mount point>

-- add to fuse replace <mount point> with /media/share
sudo chgrp fuse <mount point>

-- change owner replace <mount point> with /media/share
sudo chmod 775 <mount point>

-- reboot
sudo reboot

-- now mount in this form -- sshfs douglas@10.1.1.4:/home/<user name> /media/share replace <user name> with correct user. this give you full access to the home folder. you can edit, modify, create, and delete files(read use with care).
sshfs [<user>@]<host>:[<path>] <mount point>

-- to unmount replace <mount point> with /media/share
fusermount -u <mount point>


Hope this helps. You can also read this

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by tropdoug on 2008-08-26
well ZyZxx and others. I have done my best but to no avail. I have followed each step in the last post and all went perfectly no errors and re set the keys etc. 

But when it comes time to mount -- it doesn't work. no matter what I do there is simply no way it will connect. 

I finally in despair, purged everything off both computers and loaded nfs. I followed a thread here 

[http://www.howtoforge.com/perfect-nfs-on-ubuntu-8.04-amd64](http://www.howtoforge.com/perfect-nfs-on-ubuntu-8.04-amd64)

and noticed at the bottom the information regarding firewall ports. In the past when I did get a one way connection from the laptop to the desktop via sshfs I did not do anything with the ports. But now I wonder if I actually should have. 

Anyway for now nfs is connecting fine. I still want sshfs, but I need to move on as my productivity on building a web page has come to a stop. 

So guys, thanks very much for your help. I will leave this one open for now, and in a week or so try again, and see what happens. If anyone has further thoughts, I would love to hear them. 

Douglas

---

