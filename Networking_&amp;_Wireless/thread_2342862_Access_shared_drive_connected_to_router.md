---
title: "Access shared drive connected to router"
date: 2016-11-10
forum: Networking &amp; Wireless
---

### Post by edstevens on 2016-11-10
Just took delivery on a new System 76 Gazelle w/ Ubuntu 16.04 LTS and and working through my setup task list. Am running with the default Unity desktop.

Current item is connecting to a network drive shared through my wifi router.  

Router is TP-Link Archer 7.  Drive is an older WD, usb connected to the router.  I am able to get an 'on demand' connection by right-clicking 'the files' icon and selecting 'connect to server', but the connection does not persist.  If I close it, then come back to 'files' I have to go back through 'connect to a server' to re-connect.  So the question is, how can I make this network drive connection permanent?

--
Personal background just to set expectation levels  ;-) - 35+ years in IT, mostly as an Oracle DBA on multiple platforms.  Very familiar with Oracle Linux (derived from Red Hat) but very new to Ubuntu.

---

### Post by TheFu on 2016-11-10
[https://www.youtube.com/watch?v=aQLs5cPfqGc](https://www.youtube.com/watch?v=aQLs5cPfqGc)

Generally speaking, it is a bad idea to connect any storage to a consumer router.
[https://www.cnet.com/news/top-wi-fi-routers-easy-to-hack-says-study/](https://www.cnet.com/news/top-wi-fi-routers-easy-to-hack-says-study/)

I have a TP-Link (expensive one) and removed it from the WAN connection. Hacked. It is now a WAP only, internally.

So ... if all that doesn't make you want to rethink this ... and security of the storage isn't a primary consideration, then you should **mount** it.  Chances are the router is providing a stripped-down CIFS server, so install samba and mount it with a guest connection where you want it on the Linux machine.  *mount -t cifs .... *  Using the /etc/fstab can work.  Lots of guides for this and the Ubuntu way isn't any different from rpm-based systems to my knowledge.  Once mounted, it will show up as local storage, I believe.  CIFS storage should only be used for data, not programs. With your experience, you already know that, but for lurkers ...

---

### Post by slickymaster on 2016-11-10
*Thread moved to **Networking & Wireless**.*

---

### Post by edstevens on 2016-11-15
Sorry for the delayed response.  A lot on my plate.

I understand the concerns about security, but fail to see how connecting the storage directory to the router is any less secure that connecting it to any other device on the network.  I'm open to other methods of making that drive available to all computers on my home network.  I have taken all the precuations one can with the router ... changed the router's admin username and password.changed passwords for all wii-fi access -- all passwords meet US military standards for complexity.

---

### Post by TheFu on 2016-11-15
We are way off topic now.  Did you get the mount working?

Passwords are not sufficient when security is desired.

---

### Post by Morbius1 on 2016-11-16
If you are otherwise happy with the way "Connect to Server" works and mounts and only want to automate this process you can use Gigolo:

Install gigolo:
```
sudo apt install gigolo
```
Use it's Connect to Server option to mount the share - don't forget to mark "Remember Forever" for the password.

[COLOR=#0000cd]*Note: If this is a samba ( smb ) share that does not require credentials it will not remember "Connect anonymously" so choose "Connect as user" instead with username = guest and password = xxx.*[/COLOR]

When the share displays within gigolo right click it and select "Create Bookmark" and select the "Auto-Connect" option.

Now have gigolo start minimized when invoked:
[ATTACH=CONFIG]272167[/ATTACH]
And have gigolo start at login:
Startup Applications > Add > Name = gigolo, Command = gigolo

Logoff and logon again and your share should auto mount.

---

### Post by edstevens on 2016-11-17
> **TheFu said:**
> We are way off topic now.  Did you get the mount working?

Passwords are not sufficient when security is desired.

Yes, I just now got the mount working, adding the necessary entry to /etc/fstab

---

