---
title: "Question on remote into Ubuntu from Windows (Ubuntu 18.04.03)"
date: 2019-10-26
forum: Networking &amp; Wireless
---

### Post by mstrozier on 2019-10-26
Hello all.  I have put together an old rig of mine (FX-8350 on a MSI FX970 gaming motherboard) that I will be using downstairs in my hobby room. (restore and sale antiques / vintage items).  There are times when I want to remote into this machine from another area of the home however that is my current issue.  Originally I was running the latest version of Linux Mint and had it setup where using windows 10 I could remote desktop, select XVNC as my connection and able to control the machine via a desktop.  However wanted to come back to Ubuntu.   I know there are ways to do SSH but I don't want a command line access.  But rather able to control the system remotely.  I've tried various methods of setting up xrdp, xorg, [COLOR=#333333][FONT=Consolas]xserver-xorg-core and [/FONT][/COLOR]xorgxrdp.  

The last attempt was last night following the instructions from this youtuber: [https://www.youtube.com/watch?v=a0p0y1bN8Tw&t=625s](https://www.youtube.com/watch?v=a0p0y1bN8Tw&t=625s)

His method worked.  I was originally excited as yes, finally I can remote into the machine.  However then the problem occurred when I was down trying to log in local.  Nothing would happen.  I rebooted the machine, it'll come up to the login screen but my keyboard and mouse is locked out.  Can't move the mouse and none of the keys do anything.

So this morning I have scraped and reloaded a fresh install of Ubuntu 18.04.03 again and now, not doing anything for remote access until I get some solid help :)  As I don't really want to have to reinstall yet again and again.  As I am just spinning circles.

Thanks

---

### Post by TheFu on 2019-10-26
x2go worked very well for any of the lighter DEs.  
[https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)
[LIST=1]
[*]Setup ssh with fail2ban access on the remote system
[*]Add the x2go PPA on both the remote and local systems
[*]Install the x2go-server on the remote system
[*]Install the x2go-client on the local system
[*]If Windows is the local system, install the font package.
[*]Ensure a light DE is available on the remote system. XFCE, Mate, LXDE or openbox are good choices
[*]Run the x2go-client, setup the connection, be careful to pick a light DE in the settings
[/LIST]
Be happy.

x2go is an implementation of the NX protocol. This uses ssh tunnels for all traffic, which is better than the alternatives for security.  By controlling the connection settings for bandwidth, compression type and size, we can get excellent performance.  I use LAN settings on the LAN and ISDN settings for over the internet.

Because ssh handles the authentication, ssh-keys are honored.  So will the ~/.ssh/config settings for any connections, like non-standard ports for ssh.

---

### Post by mstrozier on 2019-10-26
Thanks TheFu, I'll give that a try.  :)  Appreciate the help.

---

