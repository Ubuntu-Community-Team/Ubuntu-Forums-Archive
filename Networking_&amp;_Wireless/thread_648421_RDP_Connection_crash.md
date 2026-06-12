---
title: "RDP Connection crash"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by elicoten on 2007-12-23
I can't connect from Ubuntu 7.10 to my Windows RDP host. I have tried the Terminal Server client, 
and a program called Remotedesktop Client and both of them cause Ubuntu to either reboot, or just X server to reboot or else the screen goes black and the machine locks. 

Other windows machines are able to connect to this RDP host.

Thanks in advance for any assistance

---

### Post by elicoten on 2007-12-26
Bump

---

### Post by dannyboy79 on 2007-12-26
is there anything in any log files?
/var/log/sys.log (forgot exactly what the name of the system log file is)
or similar log files? what about the X log file?

---

### Post by elicoten on 2007-12-26
No can't find anything useful in the log files. The system only crashes in full-screen mode. And it seems to just die, without even recording the fact that it crashed.

---

### Post by dannyboy79 on 2007-12-27
are you entering the IP address or a hostname? also, you're chosing RDP as the protocol correct? To see what's occuring behind the scenes try to issue the command from the command and pipe the output to a file, that way if it crashes I would think it would save the output from starting the TSClient. So try this:

tsclient > tsclient.log

it should save the file called tsclient.log within the directory that you were in when you issued the command BUT make sure it's in a location that your current user can write to, like your home directory. Also, are you sure that RDP is setup properly on your windows machine? Just checking.

Also, I found a bug regarding this but it's old so I would think that it's fixed by now.

[https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/109139](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/109139)

---

### Post by elicoten on 2007-12-27
I've tried both Ip address and hostname, though usually I enter a hostname.

Interestingly enough I searched google for tsweb and connected to a random server that google found and it worked fine, both with RDP and RDPv5. The connection was to a Windows 2003 Server and it seemed to be fine, but when I do it to my own computer (which is Windows XP), it crashes when its in full-screen mode, and also when its using RDPv5 protocol. I have found that if I use the RDP protocol and don't set it to full-screen mode it connects ok, but what's wrong with full-screen mode and why does it only crash with my computer and not with the Windows Server I found randomly on the internet?

Tsclient > tsclient.log generates an empty file in my home directory. There are no messages in that file at all.

Windows clients can connect reliably to my XP RDP machine with no problem.

When I had dapper I experienced that problem as well, but I managed to get around that by using a different front-end. Now I've tried a couple of front-ends and the same problem.

Once when it froze, the CAPS LOCK + SCROLL LOCK lights flashed (not continously - but just once)

Thanks for your help.

---

### Post by dannyboy79 on 2007-12-27
are you saying that the computer crashes or only X? sounds like it may be an error with your X-server not working with the Full screen mode. What do these log files show?

/var/log/Xorg.log or similar?

also, what resolution are you using on the windows machine and what resolution are you using on the Ubuntu machine? I just tried to tsclient from my Ubuntu machine that's running 1280x1024 on a  x11vnc server which is running on my Gutsy machine which is running 1024x768 and it wouldn't let me do Full Screen mode for whatever reason. THe tsclient box came up saying it couldn't connect, when I looked at the details, it made it sound like it wasn't using proper options when starting the vncviewer (tsclient) but when I just leave it at default screen size, it works fine. Not sure what else to tell you.

---

### Post by elicoten on 2007-12-27
I think the whole computer freezes - like it would if you removed the RAM or CPU or something - completely frozen up. As I said once the caps lock and scroll lock flash but then even they stopped flashing (I think I saw somewhere that the flashing means kernel panic or something). Not just X otherwise I'd be able to press CTRL + ALT + F1 to change to tty1 and login to the console. But that doesn't work.

I can use full-screen mode for the other server I found on the internet, and I can also play videos and DVDs in full screen mode.

On the Windows machine I'm running at 1280 x 1024, and on the Ubuntu machine 1024 x 768. It starts connecting and then suddenly freezes without an error. With a Windows client this isn't an issue, the Remote Desktop server changes resolution upon connection, and then again upon disconnection.

It could be something to do with the screen resolutions being different, but that really shouldn't cause the whole computer to crash.

---

### Post by dannyboy79 on 2007-12-27
you are right, it shouldn't lock up the whole computer. If you can use full screen on the other computer than I would assume the problem is not with your computer. It's with the RDP windows computer you're trying to connect to that's on your lan. I wish I could help more but I am out of ideas.

---

### Post by elicoten on 2008-01-10
I have some more information. I finally managed to get some error message from it.
WARNING: Remote desktop does not support colour depth 24; falling back to 16
X Error of failed request:  BadAtom (invalid Atom parameter)
  Major opcode of failed request:  23 (X_GetSelectionOwner)
  Atom id in failed request:  0x0
  Serial number of failed request:  1374
  Current serial number in output stream:  1374
but when this error message comes, it doesn't lockup the whole computer - it connects anyway. Previously the whole computer was freezing up.

Any more ideas? (By the way the remote computer's console is set to colour depth 32bit I think.

---

### Post by dannyboy79 on 2008-01-10
no I am sorry, I have no more ideas. is there a way to set the screen res and color depth within TSC? can you change the res and color depth temporarily on the windows box to see if that would solve it? have you tried other rdp clients?

---

