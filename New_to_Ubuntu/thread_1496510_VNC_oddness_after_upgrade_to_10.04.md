---
title: "VNC oddness after upgrade to 10.04"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by garethrevo on 2010-05-29
Hi

Need some help please.

I had 9.10 netbook remix running on an aspire revo nettop. Mostly used for running squeezebox server. It is running headless, as I'm not using it for anything much else.

I was using vnc (x11vnc) over ssh from a Win XP PC to get desktop access when I needed it  - e.g. for updates etc as I'm no command line expert.

Today I upgraded to 10.04 and everything's working OK except when I try to use VNC. It takes several seconds to come up with a login prompt, then when I've logged in, every application I open stays visible for a couple of seconds and then disappears. They're all on the task bar at the top of the window - it still looks like the netbook remix desktop.

Any ideas how I can stop this happening ?

Thanks in advance

Gareth

---

### Post by johnatyandoit on 2010-06-08
> **garethrevo said:**
> Hi

Need some help please.

I had 9.10 netbook remix running on an aspire revo nettop. Mostly used for running squeezebox server. It is running headless, as I'm not using it for anything much else.

I was using vnc (x11vnc) over ssh from a Win XP PC to get desktop access when I needed it  - e.g. for updates etc as I'm no command line expert.

Today I upgraded to 10.04 and everything's working OK except when I try to use VNC. It takes several seconds to come up with a login prompt, then when I've logged in, every application I open stays visible for a couple of seconds and then disappears. They're all on the task bar at the top of the window - it still looks like the netbook remix desktop.

Any ideas how I can stop this happening ?

Thanks in advance

Gareth

My vnc/ssh remote access failed after upgrade to 10.04 too. Looking at your definition of the vnc service in the /etc/xinetd.d if directory, if you have 

-extension XFIXES

in the server_args line, remove it. Then do:

service xinetd restart

That fixed it for me.
Here is the full service definition (server_args is one line):

service vnc1024 
   {
    type = UNLISTED 
        disable = no 
        socket_type = stream 
        protocol = tcp 
        wait = no
        user = nobody
        server = /usr/bin/Xvnc 
        server_args = -inetd :1 -query 127.0.0.1 -geometry 1024x600 -depth 16 -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared -once -SecurityTypes none 
        port = 5901    
    }

---

