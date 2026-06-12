---
title: "Slow performance when connecting to Vista using rdesktop"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Ole_Brun on 2008-11-28
I am connecting to several different Windows machines from my Ubuntu laptop. I am using rdesktop, and it works great for XP and Win 2003 hosts.
However, when connecting to my new Dell Precision running Vista x64 Ultimate, the performance is really bad. The mouse movements are erratic, and everything is much slower than when working locally on the machine.
Both my laptop and the Vista machine is on the same LAN.

Anyone know of a fix to this issue?


-Ole_Brun

---

### Post by superprash2003 on 2008-11-29
is it a wired LAN?? do you have some other LAN activity going on in the background?? are you trying to remote control multiple machines at the same time?

---

### Post by Ole_Brun on 2008-11-29
Well, it is a 54Mb WLAN that I am using at the moment. But I used to connect to the same machine with Vista, and even over a few Mb ADSL line it worked just fine.

After reading some threads on the Net I could see that others have the same problem with rdesktop->Vista, but I haven't found a solution yet.

---

### Post by superprash2003 on 2008-12-01
you could use VNC as an alternative [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-windows-pc-from.html)

---

### Post by Ole_Brun on 2008-12-01
Thanks for your reply.
I do use VNC sometimes, but usually the performance is not very good compared to rdp. I would very much like to find a solution to the rdp problem before using other remote connection alternatives.

---

### Post by fstanchina on 2008-12-01
I got a new Vista box at the office and I, too, noticed that the mouse was unbearably slow when I connected from home with rdesktop. I'm using Debian, not Ubuntu, but the problem is likely distribution-agnostic.

Well, it turns out that the mouse pointer slowness is caused by fancy pointer schemes. Choose "none" for your pointer scheme and your mouse pointer will fly again!

Here's the explanation I came up with. As far as I know, RDP renders the mouse pointer on the client; the server sends the appropriate mouse pointer image when it changes. I guess rdesktop has some limitation on the pointer image depth (or maybe, if I know Microsoft, they just changed the spec about the colorfulness of the pointer image) and it doesn't accept fancy mouse pointers, so they get rendered on the server, killing interactivity.

Note that the "Windows Aero" scheme (the default in Vista) looks quite flat but is in fact delicately shaded, making it "colorful" for the purpose of this analysis.

With that out of the way, I don't see any appreciable differences in performance between my Vista and XP desktops. I wonder if the stuff about TCP window sizes was just a red herring, but I'll leave someone with more time on his hands to dig on that.

---

### Post by HermanAB on 2008-12-01
Another way to speed things up is with 'Cendio Seamless RDP'.

Cheers,

Herman

---

### Post by Ole_Brun on 2008-12-02
Thanks fstanchina!
Changing the mouse scheme really did the trick!
Now I can control the Vista machine as if I was sitting next to it :)

I will also look into Cendia Seamless RDP. Sounds like an interesting application.

---

### Post by NTolerance on 2008-12-29
The mouse pointer theme fix worked for me.  Just for clarification it must be done on the Vista PC.  No need to change the pointer theme on Ubuntu.

---

### Post by simd on 2009-04-18
> **fstanchina said:**
> 
Well, it turns out that the mouse pointer slowness is caused by fancy pointer schemes. Choose "none" for your pointer scheme and your mouse pointer will fly again!

I've been looking for a solution for quite a while. You are a genius! Thank you!

---

### Post by NTolerance on 2009-08-22
The fix of changing the Windows cursor scheme to "None" worked great for Vista, but not so much for Windows 7.  The laggy cursor can be fixed by changing to "None", but the cursor turns black instead of white and cannot be seen against a black background.  

Also, all other cursor schemes aside from the default "Aero" theme have nasty artifacts, rendering them useless also.

---

### Post by Ole_Brun on 2009-08-24
Thanks for letting us know!
I haven't tried with Windows 7 yet. Let's hope that a new version of Rdesktop is released that deals with these problems.
I think I might wait upgrading my Vista machine to 7 until I know that the RDP from my Ubuntu machine is working flawlessly.

---

### Post by NTolerance on 2009-08-24
Ok, so I found a fix that allows you to use the standard "Aero" cursor theme with good performance: use the -z option for rdesktop.  This option turns on compression.  I wouldn't expect compression to have an effect on the mouse cursor on a 100Mbit LAN, but it does.  So here's a working rdesktop command line:

```
rdesktop -z 192.168.0.5
```

To take this a step further and enable rendering of Cleartype fonts, look at this [blog post](http://katastrophos.net/andre/blog/2008/03/10/rdesktop-connect-to-windows-vista-with-cleartype-font-smoothing-enabled/).  So if I'm on a LAN, let's combine compression with the "LAN default" RDP experience switch:

```
rdesktop -z -x 0x80 192.168.0.5
```

Optionally, take this further again and install what is, in my opinion, the best VNC/RDP client available for GNOME, [GRDC](http://grdc.sourceforge.net/).  Version 0.6 works quite well, and has a GUI option for compression.  The -x switch can be added as well in the advanced options.  

:guitar:

---

### Post by ante.blaskovic on 2010-10-02
Better fix for black background over RDC to see mouse pointer is to change desktop color, go to  "Windows color and appearance" and change black color with any other from color palette.

---

### Post by loserbaby2 on 2011-05-20
I found that remmina works well for Windows 7 and Vista on Ubuntu.  It's a workaround, but still!

---

### Post by mailsub2000 on 2012-01-14
one more thought from me if you want.
The network speed from / to ubuntu box may also affecting rdp speed.
I tried solution from here and my rdp  works little faster.

[http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu](http://ubuntumanual.org/posts/10/how-to-increase-internet-speed-in-ubuntu)

add below to /etc/sysctl.conf  and 
sudo sysctl -p

## increase TCP max buffer size setable using setsockopt()
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216
## increase Linux autotuning TCP buffer limits
## min, default, and max number of bytes to use
## set max to at least 4MB, or higher if you use very high BDP paths
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216
## don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
## recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
## for 10 GigE, use this, uncomment below
## net.core.netdev_max_backlog = 30000
## Turn off timestamps if you're on a gigabit or very busy network
## Having it off is one less thing the IP stack needs to work on
## net.ipv4.tcp_timestamps = 0
## disable tcp selective acknowledgements.
net.ipv4.tcp_sack = 0
##enable window scaling
net.ipv4.tcp_window_scaling = 1
##disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

---

