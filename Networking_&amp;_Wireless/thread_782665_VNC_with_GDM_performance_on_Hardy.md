---
title: "VNC with GDM performance on Hardy"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by GrantParnell on 2008-05-05
We have an application server that will be accessed by a bunch of VNC clients from a LAN. We do not want persistent logins so we're using GDM.

In a nutshell, performance has gone backwards when we migrated from dapper to hardy.

I have installed several fresh hardy desktops and added xinetd, vnc4viewer and xvnc4server packages and added the following in /etc/xinetd.d/vnc

```

service vnc 
{
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd -query 127.0.0.1 -once -securitytypes=none -geometry 1008x700 -depth 16 -extension XFIXES
	disable = no
        
}

```

I have added an appropriate line in /etc/services for vnc for port 5952 such that I can now do
```

vncviewer hostname:52 

```
and it up comes the GDM login screen. All good so far.

However in comparison with the same thing we had running on dapper screen throughput is much slower even before we've started the user's desktop. It does appear to be related to xinetd and Xvnc because I have changed gdm to wdm and xdm with no difference. Also the desktop by comparison performs better with straight vncserver rather than through xinetd and gdm. For instance if I do this:-
```

vncserver :1 -name parngr -geometry 1008x700 -depth 16

```
The performance of a gnome-terminal for instance is quite acceptable using the latter method.

For comparison here's the xinetd config from dapper..
```

service vnc
{
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd -query 127.0.0.1 -once -securitytypes=none -geometry 1008x700 -depth 16 -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/75dpi,/usr/share/X11/fonts/100dpi
        disable = no
}

```

Firstly, does anybody else have this problem. Secondly where can I find ALL the command line options to Xvnc (vnc4 server). Thirdly has anyone solved it?

Also acceptable solutions are OTHER ways to have non-persistent VNC sessions and what I need to add to /etc/apt/sources to get freenx working. This will be for sites with a couple of hundred seats so no home/hobbled versions acceptable - except for proof of concept.

I'm going to try experimenting with Centos 5 and Fedora 8 at home to see if there's similar issues.

---

### Post by GrantParnell on 2008-05-05
I have now reported this as Bug #227146 
Essentially manually copying binaries from Fedora 8 (because it's a later version of vnc4server) solved the problem for me.

---

### Post by cocjh1 on 2008-06-02
Also seeing this!

Was previously running Ubuntu 7.10 and had problems with multiple parallel logins (couldn't connect more than two people).  Anyway, upgraded OS to 8.04 which solved that problem but hit this new one.

Just downloaded a "try before buy" version of RealVNC from their website, 4.4.1 (r12183), which appears to fix the problem also.

Thanks,
Chris

---

### Post by cocjh1 on 2008-06-24
Now using Ubuntu server 8.04 and problem is back.  Slow response under VNC.  Have tried latest version of RealVNC 4.4.2 but no improvement.

As a test ran the Nibbles game and the worms are very slow in moving, however noticed if the mouse pointer is kept with the window, and moved constantly, the worms speed up to normal.

It's like the system will only respond if the mouse is moved..

Any ideas?

Thanks,
Chris

---

### Post by d-_-b.za on 2008-06-24
> **GrantParnell said:**
> I have now reported this as Bug #227146 
Essentially manually copying binaries from Fedora 8 (because it's a later version of vnc4server) solved the problem for me.

Had the same problem, thanks for the tip. 

But I did not have access to a Fedora Distro so I googled and found this website: [VNC Server 4.1.2 packaged for Ubuntu Hardy 8.04]("http://www.francescosantini.com/index.php?page=linux&lang=en")

It contains two Debian packages:

    * fs-vnc4-common_4.1.2_i386.deb
    * fs-vnc4server_4.1.2_i386.deb

you can download and install it with the following commands in the terminal:

```

wget http://www.francescosantini.com/files/vnc/fs-vnc4-common_4.1.2_i386.deb
wget http://www.francescosantini.com/files/vnc/fs-vnc4server_4.1.2_i386.deb
sudo dpkg -i fs-vnc4-common_4.1.2_i386.deb
sudo dpkg -i fs-vnc4server_4.1.2_i386.deb

```

and after the install restart your machine and the vnc4server would run at a acceptable speed.

Regards,

---

### Post by cocjh1 on 2008-06-26
Hey, thanks d-_-b.za!  That has fixed the problem for me also.

Any ideas where the problem lies?

---

### Post by Neutrino Sunset on 2008-08-10
Thanks from me too d-_-b.za that tip got my VNC to Ubuntu going about 10 times faster than it previously was and it was driving me nuts.

---

### Post by kermiac on 2008-08-11
> **d-_-b.za said:**
> Had the same problem, thanks for the tip. 

But I did not have access to a Fedora Distro so I googled....

SNIP



That sounds like just what the doctor ordered!! Any chance of someone making a 64 BIT .deb for us 64BIT users as I do not have access to the required files from fedora & TBH I'm still a bit of a linux n00b, lol.

---

### Post by bawilson2 on 2008-08-12
> **kermiac said:**
> That sounds like just what the doctor ordered!! Any chance of someone making a 64 BIT .deb for us 64BIT users as I do not have access to the required files from fedora & TBH I'm still a bit of a linux n00b, lol.

I'd also be interested in this.  I tried downloading the Fedora files but was having problems when I copied them over.  Any help with this would be great.

---

### Post by kermiac on 2008-08-12
Just an update on my version of the 64 bit situation - I found the fedora .rpm's on "RPM Search" & used "alien" to convert them to .deb packages. There were no errors & everything installed fine, all dependencies were met, etc. After a quick reboot I noted the newer version has installed correctly, but there has been NO IMPROVEMENT in speed.
So in a nutshell, I do not believe there is a current solution for us 64 bit users (REMINDER: I'm still a linux n00b, so PLEASE feel free to prove me wrong, lol). If anyone has any suggestions please leave them here so we can try & find a solution to this.

Also, let me know if anyone wants the 64bit .debs uploaded to try them, although it definately didn't fix it for me.

---

### Post by vof on 2008-11-13
Thanks from me too to d-_-b.za - his link to the 4.1.2 versions helped me solve both the gnome-settings-daemon crashes and the slow vnc speed.

---

### Post by tomcheng76 on 2008-12-10
> **cocjh1 said:**
> Now using Ubuntu server 8.04 and problem is back.  Slow response under VNC.  Have tried latest version of RealVNC 4.4.2 but no improvement.

As a test ran the Nibbles game and the worms are very slow in moving, however noticed if the mouse pointer is kept with the window, and moved constantly, the worms speed up to normal.

It's like the system will only respond if the mouse is moved..

Any ideas?

Thanks,
Chris
Sorry for bumping. I am having the exact nibble problem in Ubuntu 8.10 AMD64 with latest vnc4server in the repository. Everything is drawn line by line, I have already turned off desktop effects. Does anyone have a fix for Intrepid? Thank you.

---

### Post by tomcheng76 on 2008-12-11
anyone? please help. it is slow even on LAN connection :P

---

### Post by rjmoerland on 2009-01-03
I'm using Hardy server with the default vnc4server package (4.1.1.+xorg1.0.2-ubuntu7) and whatever Linux vnc viewer I use, the connection is slow. Weird thing is that when I use UltraVNC from a Windows machine, I do get a decent connection speed. :confused: What could UltraVNC possibly do that xtightvncviewer and krdc can't?

---

### Post by rescdsk on 2009-04-28
Hi,
For those of you whose slowness is not fixed by upgrading VNC, another possible source of VNC (and general X) slowness is this bug: [https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815](https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815)

The fix is to downgrade your libX11-6 packages, as in this reply: [https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815/comments/39](https://bugs.launchpad.net/ubuntu/+source/xcb/+bug/88815/comments/39)

-T

---

### Post by rescdsk on 2009-04-29
Oops, if you install those packages you might also have to install the matching libx11-dev:
[http://launchpadlibrarian.net/5509179/libx11-dev_1.0.3-4ubuntu1_i386.deb](http://launchpadlibrarian.net/5509179/libx11-dev_1.0.3-4ubuntu1_i386.deb)

And then pin the versions:

/etc/apt/preferences:
```
Package: libx11-6
Pin: version 1.0.3*
Pin-Priority: 1001

Package: libx11-data
Pin: version 1.0.3*
Pin-Priority: 1001
```

---

### Post by Skinner_au on 2009-06-20
I had been dreading my upgrade from Gutsy for some time as I didn't really have the hours to put into it when things broke from the upgrade, but I finally made the plunge about a week ago as my feeling of insecurity had gone on long enough without updates, and I didn't fancy doing a cleanup if I got hacked (is there a prize for the last person standing who hasn't upgraded?).

The upgrade wasn't smooth and soaked up much of a weekend, but one of the niggles remaining was odd VNC behaviour.

I use the xinetd/inetd VNC setup described in other threads which worked perfectly for me with it's resumability. When I upgraded to Hardy it began behaving badly, but I didn't know how to describe the problem, so it was difficult to search on. The fix described above solved my problem, but I'll try and describe it in case anyone else has the same issue.

When I logged in through VNC, the session 'skin' seemed  to frequently flicker between a plain/naked window and the gnome settings. The best way I can describe it is that, if you've ever run a remote Xwindows app over ssh before, you'll notice the window is very plain and square... well that's what it looked like. Each time the screen would do a redraw (which was quite slow in itself compared to the previous operation under Gutsy) it would change back to the plain skin, then redraw again with the gnome skin. Performance was slow over LAN, and painful (but still usable) over internet. It was quite bizarre, and I'm sure my linux-vocabulary isn't strong enough to describe the problem accurately. I hope there's enough there that anyone else with the same problem recognises it.

Anyway the links above fixed the problem, so I'm happy (this was the last thread I was reading before starting a new one).

Thanks again to the ubuntuforums community for solving yet another problem.


Sk

---

