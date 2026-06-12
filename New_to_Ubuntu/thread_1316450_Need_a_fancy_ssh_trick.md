---
title: "Need a fancy ssh trick"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by noorez on 2009-11-06
So here is my situation:

I live in a university residence where the connection speed is questionable at times.

However, I am a student of computing science and when I 'ssh' into my account I can  'wget' things pretty fast. (mostly going for other linux distro's). But space on this account is limited so downloading an entire 'iso' would max out my quota.

So, is there a trick to using 'wget' on my university account but pipping the download to my home computer?

The connection speed between my home computer and the computing science network is quite good.

---

### Post by dvlchd3 on 2009-11-06
Look into SSH tunneling.  This will allow you to "tunnel" your downloads through your SSH account at the university:

[http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Tunneling_Explained.html](http://www.ssh.com/support/documentation/online/ssh/winhelp/32/Tunneling_Explained.html)

---

### Post by noorez on 2009-11-06
I've looked into that but I'm not really getting a straight answer. Is there a simple/known procedure that I could follow?

Or a script to set it up?

I've never worked with a proxy server before so I'm not exactly sure how work my way around one for this case.

---

### Post by dvlchd3 on 2009-11-06
If you are running Ubuntu/Linux on your home computer:

[http://www.ubuntugeek.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html](http://www.ubuntugeek.com/manage-ssh-tunnels-with-gnome-ssh-tunnel-manager.html)

---

### Post by jbrown96 on 2009-11-06
SSH tunneling is the way to go. 

I'm also at a university. Gotta love Internet2. I use wget to get iso's as well. I downloaded a CentOS DVD from another university in less than 5 minutes once; I think the download was actually disk-bound.

---

### Post by Defrector on 2009-12-01
The only situation where I could see this working to your benefit is if you activated compression on your SSH connection using the -C flag. Even in this case, you probably would only see a few percent improvement. The idea would be that you mounted your home computer's destination directory onto your university account using sshfs, then used wget to download to the mounted directory.

The issue is that regardless as to whether you wget from your home connection or your university's connection and forward to your home connection, you're still going through your slower home connection at the end of it all: it is going to be bottlenecked by that. 

The only way around that would be compression and web-based files are usually compressed pretty far to begin with. (think tar.gz)

---

### Post by sandyd on 2009-12-01
you can simply do this. setup a SSH server on the computer with fast internet
then install putty on the computer with slow internet.
start putty. go to ssh -> Tunnels
in source port, enter in 1010.
flip the destination to dynamic.
connect and login.
set the firefox SOCKS proxy to 1010.
done.
your firefox now surfs the internet through the computer lab.

---

