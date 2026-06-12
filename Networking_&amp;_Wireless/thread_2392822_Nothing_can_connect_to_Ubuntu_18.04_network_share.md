---
title: "Nothing can connect to Ubuntu 18.04 network share"
date: 2018-05-25
forum: Networking &amp; Wireless
---

### Post by herqulees on 2018-05-25
This is a true nightmare of something that used to just work and should just work yet for no obvious reason isn't working at all. It's probably real simple but I've been digging through so many web pages that I'm on information overload.
I have a freshly installed Ubuntu 18.04 64bit acting as a Plex server. All of the Plex stuff is running fine, there's about 4TB of movies on an external drive and neither Ubuntu nor Plex have any issues using this drive.
Through the GUI I set Ubuntu to share the external drive and it installed a few samba things then was all finished. Going to my Windows 10 computer it doesn't see the Ubuntu computer but by typing in the IP address I can see the external drive share and clicking on it I enter my Ubuntu username and password only to be told access is denied. I changed the access to allow anyone and instead of being asked for a user name and password Windows tells me access is denied without even trying, so I turned off open access since that was even worse. I rebooted my Windows 10 computer to an Ubuntu 18.04 LiveUSB and immediately saw the other Ubuntu computer on the network so I clicked it and entered my login info for the share and it just tells me the file already exists. So I gave up on Ubuntu even being able to connect to Ubuntu and went back to Windows.
What is wrong with this fresh install of Ubuntu 18.04 that makes it to where it is impossible to simply connect to its network share? And what more information can I provide to help troubleshoot this?

---

### Post by TheFu on 2018-05-25
I vaguely remember the 18.04 release notes saying something about Samba changing default settings.  Did you see that?

For the external HDD, which file system is it running?

For Samba access, did you setup the new samba user with smbpasswd?

---

### Post by herqulees on 2018-05-26
> **TheFu said:**
> I vaguely remember the 18.04 release notes saying something about Samba changing default settings.  Did you see that?

For the external HDD, which file system is it running?

For Samba access, did you setup the new samba user with smbpasswd?

The external drive is ext4. I haven't heard anything till now about setting up a samba user. I assumed it was like Windows where the network share user/password would be my user account on the computer that's sharing. A quick search doesn't give me much information after 2010, could you give an explanation on what I would need to do?

---

### Post by mkn.dev.linux on 2018-05-30
There seems to be an issue with Ubuntu 18.04 or I'm missing something. System is complete up to date, all the necessary packages are installed, however, nothing can connect in or out. Another interesting thing is the "Sharing" tab in settings. If toggled on, it will toggle itself off upon exiting or selecting another settings menu.

I have never had an issue with connecting to other home network computers 16.04 and if I remember right the process was automatic. What happened?

OS: Ubuntu 18.04
CPU: i7 6700K
MEM: 32gb DDR4 G.Skill
GPU: GTX 1080 (396.24)

---

### Post by herqulees on 2018-06-02
> **mkn.dev.linux said:**
> There seems to be an issue with Ubuntu 18.04 or I'm missing something. System is complete up to date, all the necessary packages are installed, however, nothing can connect in or out. Another interesting thing is the "Sharing" tab in settings. If toggled on, it will toggle itself off upon exiting or selecting another settings menu.

I have never had an issue with connecting to other home network computers 16.04 and if I remember right the process was automatic. What happened?

OS: Ubuntu 18.04
CPU: i7 6700K
MEM: 32gb DDR4 G.Skill
GPU: GTX 1080 (396.24)

Unfortunately it does not look like this website is widely used anymore. I made this thread a week ago and only four people have looked at it. Of those four only two people posted anything. A fresh install of Ubuntu 18.04 on my "server" and a fresh install of Windows 10 on another computer didn't fix the issue for me and they still wouldn't connect. So I ended up going back to Windows 7 on the server after having no success searching for an answer on Google. Windows and Ubuntu just weren't meant to work together I guess.

---

