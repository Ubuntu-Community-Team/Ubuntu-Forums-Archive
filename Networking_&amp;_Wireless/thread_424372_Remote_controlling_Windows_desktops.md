---
title: "Remote controlling Windows desktops"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by zolodon on 2007-04-26
As a system administrator in a primarily Windows domain, I'm struggling to convert to a Linux desktop at work due to the lack of one key piece of software (and I don't have as much time at home to learn all I want to know about Linux)...

Is there any application out there that will allow a Linux machine to remote control Windows clients without pre-installing software on the Windows client PCs (like VNC) simply by knowing an admin login for the remote computer?  We use Dameware as our primary remote administration tool and love how it installs itself as needed when an admin connects to new machines.  Is this possible from a Linux client?

I don't really mind what the Linux software has to load on these Windows clients as long as it's lightweight, fast, secure, allows for interaction between the user and the session (both can grab the mouse to show the other how to do things), and will provide some way to stop any running services/processes created by the sessions.  This software much also allow connections to Windows 2000, XP, and 2003 machines.

I know this is a tall order for a native Linux application, but it would be much more efficient than running virtual Windows machines from a Linux desktop (which I will do if absolutely necessary).

Thanks in advance for any help or suggestions you can offer.

---

### Post by MikeDX on 2007-04-26
YES! there is

Applications -> Internet -> Terminal Server client

put in the IP of the machine and then choose RDPV5

welcome to linux

---

### Post by zolodon on 2007-04-26
Wouldn't I have to be connecting to a terminal server/app to use this, though??

I'm talking about connecting to desktop PCs for remote administration, not our Citrix/terminal servers.

---

### Post by eentonig on 2007-04-26
As long as they are XP Pro installs, you can enable rdp on the windows stations. The service is installed by default. It just needs to be activated. 

Personally, I always use rdp if I get the chance. VNC is so much slower.

---

### Post by zolodon on 2007-04-26
RDP can certainly work for Windows XP clients, but what about the Windows 2000 ones (yes we still have many of those)?

I can modify GPO settings to turn on RDP for XP PCs, but I will get negative feedback if I change too many settings just to enable Linux support for administration (since management does not support Linux usage at this time).  We're talking about hostile territory in a mostly Windows shop here...I need to find ways to get the job done without making network-wide changes for others to concern themselves with (some fellow admins are very paranoid about what they don't know...Linux).

Has anyone else here used DameWare?  The ability to install the necessary client/service upon connection to a remote PC with DameWare is the main feature I'm looking for...since client/network changes are not needed as long as you know the client or admin passwords.

---

### Post by Wicca on 2007-04-27
> **zolodon said:**
> RDP can certainly work for Windows XP clients, but what about the Windows 2000 ones (yes we still have many of those)?

RDP is not exaclty what you want, it just starts a new session on a Windows box. Besides on Windows Terminal Server, AFAIK you can't take over the session the user is in, or peek over their shoulders to have a look what's going on. The only native solution for Linux seems to be VNC which require changes on the client boxes, and that's something you don't want.
Just as you I 'm a sysadmin in a Windows world. Luckily I'm on my own so no fearfull and ignorant fellow admin can bother me \\:D/. I use Remote Admin for the job, which is, just as Dameware, a Windows program. I didn't want to install VNC on every client, although nobody will stop me from doing that, it's slow and the capabilities of Remote Admin are much better.

As an alternative I have the client part of Remote Admin placed on one of the W2003 servers. From my Ubuntu box I have a RDP session to that server, which sits there permanentely, with Remote Admin opened. I use Beryl as well so I put this session on one of the sides of the cube. If someone calls and need assistance I just turn the cube and.... have a look.
The client part of Remote Admin is just a simple .exe so there's no need to install. I'm not sure about Dameware about that.

You can also try to install Dameware on Ubuntu with Wine. With Wine you can use Windows programs on Linux. Not all programs will work, but you might give it a try. I never used Wine so I can't tell you anything more about that, search these wonderfull forums for more information.

---

### Post by zolodon on 2007-04-27
Thank you for the response, Wicca...  You've given me some good ideas about how to work around the situation (RDP to a server with the DameWare client installed/running).  Alos, applying that to a side of the Beryl cube (something I use as well) certainly sounds like an efficient approach.

I still wish there was something native I could use for this task, but a work-around will do until I can help support a project like the one I desire.  :) 

BTW, I did try to install DameWare with Wine before, but ran into a slight problem of the installer being in MSI format.  Does anyone have a suggestion for how to install such apps through Wine?

---

### Post by breaking on 2008-01-25
> **zolodon said:**
> BTW, I did try to install DameWare with Wine before, but ran into a slight problem of the installer being in MSI format.  Does anyone have a suggestion for how to install such apps through Wine?

Well i just saw this thread, cause i have the same problem. I found the solution to this part of the problem by a quick google:
[http://wiki.jswindle.com/index.php/Wine_MSI](http://wiki.jswindle.com/index.php/Wine_MSI)

The short answer is just run:
```
wine msiexec /i program.msi
```

The problem is that even though dameware installed properly and shows up in applications -> wine (after a quick killall gnome-panel), it won't open the actual program. I got a divide by zero in the terminal, if i run it from there. Anybody got this working?

---

