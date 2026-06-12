---
title: "VNC and GDM - GDM greeter not running for remote connections. ie grey screen"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by arch4nge1 on 2008-01-04
Hi All,

Version: 7.10 Gutsy Gibbon 32 bit Desktop
Platform: Intel

I've been following Tichondrius'  HOWTO: Set up VNC server with resumable sessions tutorial to set up remote login but I've been having troubles getting GDM to show up on the remote connections.

All I see is a grey screen with a X cursor. Running vncviewer :1 displays this as well as running it from remote workstation. I'm guessing the GDM greeter isn't running for the second display.

I have XDMCP running as the log shows a lot of XDCMP stuff.

My /etc/gdm.conf-custom is as follows:-
[daemon]

[security]

AllowRoot=true

[xdmcp]

Enable=true
HonorIndirect=false

[gui]

[greeter]
RemoteGreeter=/usr/lib/gdm/gdmlogin
GlobalFaceDir=/usr/

[chooser]

[debug]

[servers]


If it's any help I'm also getting these strange errors in syslog:-
gdm_xdmcp_handle_manage: Failed to look up session id <large negative value>

And:-
 DEBUG: gdm_xdmcp-handle_manage: Got display=1, SessionID=878173317 Class=MIT-unspecified from MIT-unspecified1
Jan  5 14:10:49 host1 gdm[14801]: WARNING: gdm_xdmcp_handle_manage: Failed to look up session id 878173317
Jan  5 14:10:49 host1 gdm[14801]: DEBUG: XDMCP: Sending REFUSE to 878173317
Jan  5 14:10:50 host1 gdm[14801]: DEBUG: gdm_forward_query_lookup: Host ::ffff:127.0.0.1 not found


Any help would be much appreciated.

---

### Post by HermanAB on 2008-01-05
Hmm, in my experience, VNC is at best a pain in the derrier.  I use SSH with X forwarding for everything - much less hassle and secure.

You don't really need a remote desktop - you already have one on your local machine, so just connect with ssh and run the program you want directly:

$ ssh -c blowfish -X user@server programname

$ ssh -c blowfish -X joesoap@142.59.19.115 "gedit /etc/fstab"

$ ssh -c blowfish -X joesoap@142.59.19.115 kicker

and so on.

Cheers,

Herman

---

### Post by cyb0rg_ on 2008-02-06
I am seeing similar issues:

gdm[10574]: WARNING: gdm_xdmcp_handle_manage: Failed to look up session id 1143689123

When i turn on gdm debugging i see:

gdm[5462]: DEBUG: XDMCP: Sending WILLING to ::ffff:127.0.0.1
gdm[5462]: DEBUG: gdm_peek_local_address_list: Could not get address from hostname!

My xinetd.d Xvnc file is:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 800x600 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared -securitytypes=none -extension XFIXES
        port = 5901
}

```

I did some playing around and discovered if you change [FONT="Courier New"]-query localhost[/FONT] to [FONT="Courier New"]-query ::1[/FONT] things start working.

For example:
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query ::1 -geometry 800x600 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared -securitytypes=none -extension XFIXES
        port = 5901
}

```

---

### Post by lousy.ratbag on 2008-02-24
this (XDM and GDM) isn't working for me - all i see is a grey window with an X

system is a new gutsy build with everything up to date

i've been reading the forums for two days and trying all the various "fixes" and none have made any difference.  i've created the /etc/xinetd.d/ file (and edited /etc/services), edited /etc/gdm/gdm.conf (to Enable and set Greeter), rebooted - and tried all the "fixes" and rebooted - no improvement

if i run vncserver :1 and vncviewer :1 then i get stuff in the window (which i could configure in ~/.vnc/xstartup) but i want a *login* approach per XDM/GDM

ps -ef shows Xvnc running, while i have my sad grey window with X in it.
i moved /usr/lib/gdm/gdmlogin (and gdmgreeter, just in case) to one side and put a script in its place that logged when it was run - this is never run, so Xvnc never starts gdmlogin

help!

---

