---
title: "SSH Oddity"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2007-09-03
Here's an odd one I can't seem to figure out this time around. I did it once by accident, but it was sometime ago and I don't remember exactly how.

I have two computers, a desktop and a laptop. Both are connected to a home network through a DSL wireless router. (One wired, one not..)
[I]
From the desktop,[/I] I can VNC and/or SSH into the laptop. I can control the computer using VNCViewer or XDCMP. I can copy files to and from using the scp command or regular commands once an SSH connection has been established. No problems here.
[I]
From the laptop[/I], I can VNC into the desktop, and control that computer remotely by using VNCViewer or logging in using XDCMP (I'm writing this now through VNCViewer from the laptop to the desktop). But, I can't use SSH or SCP from the laptop to get into the desktop computer.

I used Firestarter to set "myname-desktop" as an allowed host in the laptop. I did the same on the desktop comp, whitelisting connections from "myname-laptop", however, the connections are still refused. I even whitelisted  SSH and VNC connections from the "myname-laptop" host, but the connection on Port 22 gets refused every time. (But not VNC Port 5900..)

I know this is a simple fix, but it's managing to elude me.

Anyone see an error I've made?

---

### Post by noob12 on 2007-09-03
Can you post the result of these when run on your desktop host
```

netstat -tnl

sudo iptables -nL

```

---

### Post by detroit/zero on 2007-09-03
I'm sorry.. I haven't had time to update until now.

Someone sent me a message last night (that I can't seem to find now) that pointed out I may want to make sure that both the server and client SSH applications are installed on both machines, as it seems the problem could be that the server-side app might not be installed on the desktop.

Indeed this was the case. Now my error message has gone from "connection refused on port 22" to this:

```
myname@myname-laptop:~$ ssh myname-desktop
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
**:**:**:**:**:**:**:**:**:**:**:35:86:4f:9d:ac.
Please contact your system administrator.
Add correct host key in /home/myname/.ssh/known_hosts to get rid of this message.
Offending key in /home/myname/.ssh/known_hosts:2
RSA host key for zero-desktop has changed and you have requested strict checking.
Host key verification failed.
myname@myname-laptop:~$ 

```

I don't remember "requesting strict validation".. I used Firestarter (as I mentioned) to allow connections only from one of my computers to the other; not even other computers on my home network can use SSH or VNC to get into either of these machines.

I've found the file it points out easy enough, but I'm not at all sure how to go about changing the key it specifies.

I'm doing this in preparation for a system wipe and re-install on the laptop after a snafu of unparalleled proportions left  it all but unusable. The desktop was just yesterday reformatted and re-installed after some crippling NVidia  BS left it unusable back in May or June.

I found the SSH page in the community docs  site, but it's a big page to sift through in between flipping steaks, and I hope someone can point me in the right direction?

---

### Post by noob12 on 2007-09-03
On the laptop, edit the file under your home directory in ~/.ssh/known_hosts

Remove the line entries myname-desktop and any of its ips. They are stale.

A new entry will be created when you next ssh to myname-desktop.

---

### Post by detroit/zero on 2007-09-03
The file you mention is mainly made of (what looks to me to be) gibberish.

I just deleted the file, and all went as it should.

Thanks a million!

---

