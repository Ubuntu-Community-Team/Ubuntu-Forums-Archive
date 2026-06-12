---
title: "FreeNx"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Tabu.it on 2011-02-28
Hi,
I have freenx working very well, untill i decided to boot my ubuntu server without keyboard, mouse and monitor.

My auth.log

> 
Feb 28 22:07:02 Ubuntu sshd[2212]: Connection from 192.168.1.10 port 57062
Feb 28 22:07:02 Ubuntu sshd[2212]: Failed none for nx from 192.168.1.10 port 57062 ssh2
Feb 28 22:07:02 Ubuntu sshd[2212]: Found matching DSA key: <<<DSA KEY>>>
Feb 28 22:07:02 Ubuntu sshd[2212]: Accepted publickey for nx from 192.168.1.10 port 57062 ssh2
Feb 28 22:07:02 Ubuntu sshd[2212]: pam_unix(sshd:session): session opened for user nx by (uid=0)
Feb 28 22:07:02 Ubuntu sshd[2212]: User child is on pid 2286
Feb 28 22:07:15 Ubuntu nxserver[2452]: (nx) Failed login for user=tech from IP=192.168.1.10
Feb 28 22:07:15 Ubuntu sshd[2286]: Connection closed by 192.168.1.10
Feb 28 22:07:15 Ubuntu sshd[2286]: Transferred: sent 2792, received 1968 bytes
Feb 28 22:07:15 Ubuntu sshd[2286]: Closing connection to 192.168.1.10 port 57062


After that i restart ubuntu with keyboard mouse and monitor plug and freenx works.

So is there a way to a use freenx without keyboard mouse and monitor plug to ubuntu 10.04?

---

### Post by Tabu.it on 2011-02-28
Anyone with an idea about the problem?

---

### Post by pricetech on 2011-02-28
Don't bump so quick.

I don't use FreeNX, but something that comes to mind is that maybe to computer is not booting without keyboard connected.  Check your BIOS to make sure it's not stalling during post due to lack of a keyboard.

---

### Post by Tabu.it on 2011-02-28
ok sorry, it could boot with no keyboard or mouse (i tested it because i could connect and login to server with putty)

---

### Post by Tabu.it on 2011-03-01
*bump*

---

### Post by wizard10000 on 2011-03-01
FreeNX isn't an X client, it's a remote control application.  If X isn't running on the host FreeNX won't work.

If you want to run the host headless you'll need to run an X client instead of a remote control application like FreeNX or VNC.

Hope this helps -

---

### Post by Tabu.it on 2011-03-01
> **wizard10000 said:**
> FreeNX isn't an X client, it's a remote control application.  If X isn't running on the host FreeNX won't work.

If you want to run the host headless you'll need to run an X client instead of a remote control application like FreeNX or VNC.

Hope this helps -

So if i boot without keyboard mouse and monitor the Ubuntu X client won't start?

---

### Post by pricetech on 2011-03-01
Depends on your runlevel.  If you're in front of the computer when you boot it, do you get a graphical login screen or a command line ???

---

### Post by wizard10000 on 2011-03-01
> **Tabu.it said:**
> So if i boot without keyboard mouse and monitor the Ubuntu X client won't start?

Unless you've got the hardware hard-coded into xorg.conf X will fail to start if the hardware's not installed.

---

### Post by Tabu.it on 2011-03-01
> **wizard10000 said:**
> Unless you've got the hardware hard-coded into xorg.conf X will fail to start if the hardware's not installed.

is there a guide to do it?

---

### Post by wizard10000 on 2011-03-01
> **Tabu.it said:**
> is there a guide to do it?

Why not just enable remote X connections and run the X client on the remote machine?  Much simpler.

---

### Post by Tabu.it on 2011-03-01
> **wizard10000 said:**
> Why not just enable remote X connections and run the X client on the remote machine?  Much simpler.

I'm confuse, so i could use freenx with no keyboard - monitor with a x client on the remote machine?

---

### Post by wizard10000 on 2011-03-01
> **Tabu.it said:**
> I'm confuse, so i could use freenx with no keyboard - monitor with a x client on the remote machine?

You wouldn't use FreeNX at all.

Look here -

[http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/](http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/)

---

### Post by Tabu.it on 2011-03-01
> **wizard10000 said:**
> You wouldn't use FreeNX at all.

Look here -

[http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/](http://www.craigryder.com/linux-ubuntudebetc/x11-forwarding-and-ssh-for-remote-linux-ubuntu-desktop/)

ok read and done.

I have install xming on windows and i'm using putty for ssh
I could login and type gnome-session, i could see the ubuntu desktop but not the top and bottom bar (maybe because ubuntu resolution is 1280x1024 and windows pc 1920x1080?). And also i have multiple windows of ubuntu desktop (some of them are all black).

The only way to "escape" to all of that windows is to close xming (it tells me :There are 23clients connected, is it normal?)
Also i use jdownloader to download files from different hosters, and it require a GUI to run. is it possible to run it without log in to ubuntu with ssh + x11?.

Thank you

---

### Post by wizard10000 on 2011-03-01
Not sure, but the problem might be xming.  I have no experience with that application, sorry  :(

---

### Post by Tabu.it on 2011-03-01
> **pricetech said:**
> Depends on your runlevel.  If you're in front of the computer when you boot it, do you get a graphical login screen or a command line ???

With monitor keyboard and mouse yes. Without it i could login only with putty

---

### Post by pricetech on 2011-03-14
Strange.  Mine boots to a graphical login whether I have a keyboard / mouse plugged in or not.  Once X is running, then freenx or NX from nomachine should work just fine.  I honestly can't say why your X is not starting.

---

### Post by Tabu.it on 2011-03-16
Yes, it's very strange. Could be the integrated VGA?

---

### Post by pricetech on 2011-03-17
I wouldn't think so as mine is integrated as well.

---

### Post by Tabu.it on 2011-03-17
My hardware is: 
RAM DDR3 Corsair XMS3 TW3X4G1333C9A 1333Mhz 4GB (2x2GB) CL9	
CPU AMD Phenom II X2 555 3.2GHz Socket AM3 80W Callisto Black Edition Boxed HDZ555WFGMBO
MB Gigabyte GA-880GA-UD3H (880G,AM3,ATX,DDR3,VGA,AMD,EuP)	9
2 X Hard Disk Interno Western Digital Caviar Blue 1TB 3.5" 7200rpm 32MB SATA3 WD10EALX <<<this hd are in Raid 1 (ubuntu software raid).

I should try to install the vga driver and then reinstall freenx.

---

### Post by AndrewX192 on 2011-03-19
FreeNX does not require X11 to be running, and will work fine on Ubuntu 10.04 without a keyboard or mouse.

---

### Post by wizard10000 on 2011-03-19
> **AndrewX192 said:**
> FreeNX does not require X11 to be running, and will work fine on Ubuntu 10.04 without a keyboard or mouse.

This.  I thought FreeNX was an RDP application - it isn't.  It's an X solution.  My apologies for shooting my mouth off without knowing what I was talking about  ;)

---

