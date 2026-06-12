---
title: "Automounted sshfs directories no longer work properly after intrepid upgrade"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Gizmonty on 2008-11-04
Hi all,

Wow, the networking and wireless forum sure is busy since the intrepid release - are you listening Canonical?

Anyhoo, I have a server which was running Hardy and has a 2TB raid drive that was mounted as /mnt/raid and was being shared by sshfs. I am accessing this from 2 computers (a laptop and a desktop which were both running Hardy) which have been set up to automatically mount this directory via sshfs whenever the network connects (and unmount on disconnect). I did this via a couple of scripts that I got from some how-to that I can no longer find. This was a *very* nice setup and worked flawlessly until I got too enthusiastic and upgraded them all to intrepid.

Now, they still both automount the directory and I can browse and read the files. However, I can no longer write to the raid drive. The file browser used to report free space on the drive as 1000GB (regardless of actual available space) but it now reports free space as 0 bytes and when I try to write anything to the drive I get the error message **"Error while copying to "raid". There is not enough space on the destination. Try to remove files to make space."** If I work directly on the server, there is no problem.

I suspect that there will be a simple solution to this and that someone else will be having the same problem but am unsure how to go about investigating the source of the problem for myself.

Any ideas?

---

### Post by dmizer on 2008-11-05
Please post the mount commands. I assume you're using sshfs in tandem with fuse and autofs?

---

### Post by icedfusion on 2008-11-05
Hi,
I have the same issue, my mounting cmd is:

sshfs -p 443 some_ip_address:/ /media/bio &

connection states it as 0 bytes so I can no longer write files....

ice.

---

### Post by IMSargon on 2008-11-07
I see the same issue with a simple setup.

Two computers are running fresh installs of Intrepid Ibex with all the latest updates. Root one computer1 mounts computer2 as auser. 

#df -h
Filesystem            Size  Used  Avail Use% Mounted on
auser@computer2:      0.0K -0.0K  0.0K  231% /mnt/test

#sshfs -V
SSHFS version 2.0
FUSE library version: 2.7.3
fusermount version: 2.7.3
using FUSE kernel interface version 7.8

# ssh -V
OpenSSH_5.1p1-hpn13v5, OpenSSL 0.9.8g 19 Oct 2007

# dpkg -l | grep openssh
ii  openssh-client                            1:5.1p1-3ubuntu1  

Is anybody NOT experiencing this problem with these versions?
Is anyone experiencing this problem with OTHER versions?

Edit: 
After a little searching, I found that this bug has been reported
[https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/100116](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/100116)

So maybe we just wait and hope?

---

### Post by Alexqw on 2008-11-09
I am having the same issue with SSHFS in Intrepid.  I'll post if I find anything.

---Alex

---

### Post by icedfusion on 2008-11-09
Cheers for the updates. Bit of a pain that this is broken. Will watch the tracking of the bug. 

Please report here if an answer is found.

Cheers

ice.

---

### Post by IMSargon on 2008-11-10
I found a computer that does not display this problem. It displays 1TB free which is incorrect but usable. 

# sshfs -V
SSHFS version 2.0
FUSE library version: 2.7.3
fusermount version: 2.7.3
using FUSE kernel interface version 7.8

# dpkg -l | grep openssh
ii  openssh-client                            1:5.1p1-3ubuntu1

# ssh -V
OpenSSH_4.3p2 Debian-9etch3, OpenSSL 0.9.8c 05 Sep 2006

Could anyone having this problem post their version info?

Edit:
I've completely removed and reinstalled openssh-client. Now the computer is showing the 0.0K free problem

# ssh -V
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007

So anyone who needs to circumvent this problem can downgrade to 4.3p2, at least

---

### Post by IMSargon on 2008-11-10
SOLUTION FOUND:

One possible solution is to upgrade SSHFS to 2.1, which can be found here: [http://packages.ubuntu.com/jaunty/sshfs](http://packages.ubuntu.com/jaunty/sshfs)

With this package version, the sizes appear correctly.
# sshfs -V
SSHFS version 2.1
FUSE library version: 2.7.3
fusermount version: 2.7.3

---

### Post by Gizmonty on 2008-11-13
Thankyou thankyou thankyou IMSargon!

This was such a quick easy solution. I hope it gets rolled out as an autoupdate for all to enjoy soon.

---

### Post by Miata-MS on 2008-11-17
Thank you very much IMSargon. That solution worked perfectly for me, I was having the same issue of the sshfs mount showing 0.0kb free.

For anyone else having this issue with Intrepid, Installing the sshfs 2.1 deb linked above works great.

---

### Post by Lusse on 2008-11-17
> **Miata-MS said:**
> Thank you very much IMSargon. That solution worked perfectly for me, I was having the same issue of the sshfs mount showing 0.0kb free.

For anyone else having this issue with Intrepid, Installing the sshfs 2.1 deb linked above works great.

Confirmed! Works great for me to. Thanks.

//Linus

---

### Post by devveloper on 2008-12-03
i tried both methods mentioned in this thread, and i still am experienceing problems with sshfs dismounting by itself.

the methods i tried were 

using sshfs 2.1:

SSHFS version 2.1
FUSE library version: 2.7.3
fusermount version: 2.7.3
using FUSE kernel interface version 7.8

and using the older version of the openssh-client 4.x
actually, when i used this for a while, i had problems with openssh-server complaining about the version, and i upped it back to v5 although it still did not solve the problem.

anyone other suggestions?

---

### Post by IMSargon on 2008-12-04
> i tried both methods mentioned in this thread, and i still am experienceing problems with sshfs dismounting by itself.

That's not a bug, it's a FEATURE! :-p

If you don't use an SSHFS mount for a while, it will automatically log you out. Here's the solution from the Ubuntu SSHFS page:

> Your ssh session will automatically log out if it is idle. To keep the connection active (alive) add this to ~/.ssh/config or to /etc/ssh/ssh_config on the client.

ServerAliveInterval 5

This will send a "keep alive" signal to the server every 5 seconds. You can usually increase this interval, and I use 120. 
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

If you try this and still have trouble, you may need to start a new thread. This thread seems to be specific to the free space problem.

---

### Post by Squeggee on 2008-12-30
Updating the sshfs to V 2.1 solved my 0 bytes problem.  Thanks for the help.  Always appreciated!!!!:D

---

