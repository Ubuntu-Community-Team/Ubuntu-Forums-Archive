---
title: "[SOLVED] Help with VNC over SSH Ubuntu to Ubuntu"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by No-Neck on 2008-07-22
I've been using the method described in a HowTo on these forums for a few months now. Set up openssh on my Ubuntu machine at home and control it using PortaPuTTy from a remote Windows machine. It works well.

I've now had enough of Windows and it's BSODs and have used Wubi to install Ubuntu on the remote machine, yay. I've installed PuTTy on the remote Ubuntu and can log in as normal, the same as I do with the Windows version of PuTTy. But I can't for the life of me work out how to get VNC working. PuTTy is set up exactly the same in Ubuntu as it is in Windows. I've tried using the inbuilt Remote Desktop Viewer, connecting to 127.0.0.1:50000, exactly the same as in Windows. It fails to make a connection. I've also installed vnc4viewer but can't get that working either. 

This has got to be something simple and stupid, any ideas please? :)

---

### Post by wiseguyxp on 2008-07-22
Did you tunnel port 50000 when you logged into the ssh session?

---

### Post by No-Neck on 2008-07-22
Yes, exactly the same configuration as is working within Windows. Remote Desktop Viewer instantly gives the error "Connection to host 127.0.0.1:50000 was closed".

I know PuTTy is only 'ported' to Linux, is there a better solution? 

Thanks for the reply BTW! :)

EDIT: All the syntax of terminal commands is something I'm very far away from learning being fairly new to Linux. Could someone tell me the proper 'vncviewer xxxxxxxxx' command to use in this situation? Maybe I'm just not doing it correctly.

---

### Post by wiseguyxp on 2008-07-22
I have been using PuTTY with OpenSSH with no issues...  until I reinstalled, but that's another story.  The way I had it set up was OpenSSH was installed on Ubuntu, and I usually connected through PuTTY on a Windows machine.  In the PuTTY options, I tunneled local source port "localhost:5900" to destination "5900" (I was using vnc4server I think).  I would open up RealVNC Viewer and type in "localhost" as the server, click okay, and it would pop up just fine.  Try a telnet to port 50000 from another machine (other than the server) using your external IP address.

As for the command, use "vncviewer xxx.xxx.xxx.xxx::50000"

---

### Post by No-Neck on 2008-07-22
Thanks for your replies mate. I've been doing the same thing. OpenSSH installed at home, PortaPuTTy on my USB drive to use on a Windows PC. It works fine from the Windows version of PuTTy, using tightvnc. PuTTy is set to tunnel 127.0.0.1:50000 to 5900 which is sent to my home PCs port 44444. I was under the impression that the port 50000 bit (in my case) was just used locally on this machine. i.e. vncviewer connects to port 50000 on the localhost, PuTTy intercepts and sends it out via 5900 to 44444 on the remote PC? Am I confusing myself here?

Telnetting port 50000 on the remote PC gives nothing, it's still waiting, but port 50000 isn't open at home anyway.

As for the vncviewer command, I've tried that one. Maybe I was being confused by the Ubuntu wiki which contains some complicated looking syntax for the command. o.O

---

### Post by wiseguyxp on 2008-07-22
I haven't gotten much sleep recently, so it might just be me.

Can you give me:

VNC listen port on server
Port you want the client to use

Also, can you connect to the vnc server from the server itself (localhost)?
If not, try telnetting to the port when you're on the server without any ports forwarded.

---

### Post by No-Neck on 2008-07-22
My home PCs SSH port is 44444. I have PuTTy set up to connnect to port 44444 on the remote PC.

In the tunnels section of PuTTy, I have it set to listen to port 50000, destination 127.0.0.1:5900. I tell the VNC viewer to connect to 127.0.0.1 port 50000.

VNC listen port was never set up on the remote/server PC. This set up works fine from within Windows. I followed this guide: [http://ubuntuforums.org/showthread.php?t=383053](http://ubuntuforums.org/showthread.php?t=383053)

I too need sleep, and I'm going to have to get some. Thanks for your help.

---

### Post by wiseguyxp on 2008-07-22
Oh wow, yeah.  I thought you were trying to access it from a Windows machine, I didn't realize they were both Ubuntu.  I thought when you said it worked fine on Windows, I thought you meant just the ssh part.  Command sequence should work as posted below.

SSH Connection
```
ssh -p 44444 -L localhost:50000:localhost:5900 [ssh server IP]
```
VNC Connection
```
vncviewer localhost::50000
```

i think...
but why not just use 5900 on the local machine instead of 50000?

---

### Post by No-Neck on 2008-07-23
Wooo, thanks. Using the first command with -l [myloginname] -i [mykeyfile] I was able to connect without PuTTy and using the second command worked perfectly this time.

Absolutely splendid, once again thank you.

EDIT: This seems like a far superior solution as well. The screen updates with a lot less lag.

---

