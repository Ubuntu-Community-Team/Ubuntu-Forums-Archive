---
title: "Unable to use remote x11vnc on a ssh tunnel"
date: 2019-07-31
forum: Networking &amp; Wireless
---

### Post by jaro2019 on 2019-07-31
I want to connect to my desktop at work via vnc. Here how I did:  
[LIST]
[*]On the remote machine I ran:
  ```
autossh -M 8081 -NR  2222:localhost:22 -p3082 [email]censor@censor.sytes.net[/email]


```
[*]On local machine I ran:
  ```
ssh -vvv -NL 5900:localhost:5900 work
```

[/LIST]
  define work in .ssh/config
  ```
Host work
    Hostname localhost
    User censor
    Port 2222

```  And start x11vnc server
  ```
export DISPLAY=:0
x11vnc

```  When use remmina connect to address localhost:5900 it just flash then disappear.
  The log of the x11vnc
  ```
24/07/2019 16:23:40 Got connection from client 127.0.0.1
24/07/2019 16:23:40   other clients:
24/07/2019 16:23:40 Normal socket connection
24/07/2019 16:23:40 Disabled X server key autorepeat.
24/07/2019 16:23:40   to force back on run: 'xset r on' (3 times)
24/07/2019 16:23:40 incr accepted_client=1 for 127.0.0.1:33082  sock=11
24/07/2019 16:23:40 Client Protocol Version 3.8
24/07/2019 16:23:40 Protocol version sent 3.8, using 3.8
24/07/2019 16:23:40 rfbProcessClientSecurityType: executing handler for type 1
24/07/2019 16:23:40 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
24/07/2019 16:23:41 Pixel format for client 127.0.0.1:
24/07/2019 16:23:41   8 bpp, depth 8
24/07/2019 16:23:41   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
24/07/2019 16:23:41 copy_tiles: allocating first_line at size 61
24/07/2019 16:23:41 rfbProcessClientNormalMessage: ignoring unsupported encoding type ultraZip
24/07/2019 16:23:41 Using compression level 9 for client 127.0.0.1
24/07/2019 16:23:41 Using image quality level 0 for client 127.0.0.1
24/07/2019 16:23:41 Using JPEG subsampling 1, Q15 for client 127.0.0.1
24/07/2019 16:23:41 Enabling X-style cursor updates for client 127.0.0.1
24/07/2019 16:23:41 Enabling full-color cursor updates for client 127.0.0.1
24/07/2019 16:23:41 Enabling cursor position updates for client 127.0.0.1
24/07/2019 16:23:41 Enabling KeyboardLedState protocol extension for client 127.0.0.1
24/07/2019 16:23:41 Enabling NewFBSize protocol extension for client 127.0.0.1
24/07/2019 16:23:41 Enabling LastRect protocol extension for client 127.0.0.1
24/07/2019 16:23:41 Enabling SupportedMessages protocol extension for client 127.0.0.1
24/07/2019 16:23:41 Enabling SupportedEncodings protocol extension for client 127.0.0.1
24/07/2019 16:23:41 Enabling ServerIdentity protocol extension for client 127.0.0.1
24/07/2019 16:23:41 Using tight encoding for client 127.0.0.1
24/07/2019 16:23:41 client_count: 0
24/07/2019 16:23:41 Restored X server key autorepeat to: 1
24/07/2019 16:23:41 viewer exited.
24/07/2019 16:23:41 deleted 60 tile_row polling images.

```  Log of ssh -vvv:
  ```
debug1: Connection to port 5900 forwarding to localhost port 5900 requested.
debug2: fd 9 setting TCP_NODELAY
debug2: fd 9 setting O_NONBLOCK
debug3: fd 9 is O_NONBLOCK
debug1: channel 5: new [direct-tcpip]
debug3: send packet: type 90
debug3: receive packet: type 91
debug2: channel 5: open confirm rwindow 2097152 rmax 32768
debug2: channel 5: window 1992972 sent adjust 104180
debug2: channel 5: read<=0 rfd 9 len -1
debug2: channel 5: read failed
debug2: channel 5: close_read
debug2: channel 5: input open -> drain
debug2: channel 5: ibuf empty
debug2: channel 5: send eof
debug3: send packet: type 96
debug2: channel 5: input drain -> closed
debug3: receive packet: type 96
debug2: channel 5: rcvd eof
debug2: channel 5: output open -> drain
debug2: channel 5: obuf empty
debug2: channel 5: close_write
debug2: channel 5: chan_shutdown_write: shutdown() failed for fd 9: Transport endpoint is not connected
debug2: channel 5: output drain -> closed
debug3: receive packet: type 97
debug2: channel 5: rcvd close
debug3: channel 5: will not send data after close
debug2: channel 5: send close
debug3: send packet: type 97
debug2: channel 5: is dead
debug2: channel 5: garbage collecting
debug1: channel 5: free: direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36686 to 127.0.0.1 port 5900, nchannels 6
debug3: channel 5: status: The following connections are open:
  #2 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36662 to 127.0.0.1 port 5900 (t4 r0 i0/0 o3/0 fd 6/6 cc -1)
  #3 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36664 to 127.0.0.1 port 5900 (t4 r1 i0/0 o3/0 fd 7/7 cc -1)
  #4 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36666 to 127.0.0.1 port 5900 (t4 r2 i0/0 o3/0 fd 8/8 cc -1)
  #5 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36686 to 127.0.0.1 port 5900 (t4 r3 i3/0 o3/0 fd 9/9 cc -1)

debug1: Connection to port 5900 forwarding to localhost port 5900 requested.
debug2: fd 9 setting TCP_NODELAY
debug2: fd 9 setting O_NONBLOCK
debug3: fd 9 is O_NONBLOCK
debug1: channel 5: new [direct-tcpip]
debug3: send packet: type 90
debug3: receive packet: type 92
channel 5: open failed: connect failed: Connection refused
debug2: channel 5: zombie
debug2: channel 5: garbage collecting
debug1: channel 5: free: direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36688 to 127.0.0.1 port 5900, nchannels 6
debug3: channel 5: status: The following connections are open:
  #2 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36662 to 127.0.0.1 port 5900 (t4 r0 i0/0 o3/0 fd 6/6 cc -1)
  #3 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36664 to 127.0.0.1 port 5900 (t4 r1 i0/0 o3/0 fd 7/7 cc -1)
  #4 direct-tcpip: listening port 5900 for localhost port 5900, connect from 127.0.0.1 port 36666 to 127.0.0.1 port 5900 (t4 r2 i0/0 o3/0 fd 8/8 cc -1)

```  What did I do wrong?

---

### Post by SeijiSensei on 2019-07-31
Are you authenticating with keys? I didn't see anything about authentication in the output above.

---

### Post by jaro2019 on 2019-07-31
> **SeijiSensei said:**
> Are you authenticating with keys? I didn't see anything about authentication in the output above.

Yes, I use ```
ssh-copy-id
``` to simplify the process. Do you have any ideas?

---

### Post by SeijiSensei on 2019-08-01
Sorry, but I can't be more help because I don't use SSH for this task. All my connections are via OpenVPN [static tunnels]("https://openvpn.net/community-resources/static-key-mini-howto/"). In cases like yours, I would configure the office machine as a client. On your end you'd need to enable your router to do port forwarding for the selected port back to the local machine.  Then you can pass any type of traffic between the machines, not just x11vnc.

---

### Post by jaro2019 on 2019-08-02
> **SeijiSensei said:**
> Sorry, but I can't be more help because I don't use SSH for this task. All my connections are via OpenVPN [static tunnels]("https://openvpn.net/community-resources/static-key-mini-howto/"). In cases like yours, I would configure the office machine as a client. On your end you'd need to enable your router to do port forwarding for the selected port back to the local machine.  Then you can pass any type of traffic between the machines, not just x11vnc.

Thank you for the suggestion, I will try and reply back later

---

### Post by jaro2019 on 2019-08-12
Hi

I would like to share my work around, install nomachine nx and do the same port forwarding, it works :)

---

### Post by TheFu on 2019-08-13
> **jaro2019 said:**
> Hi

I would like to share my work around, install nomachine nx and do the same port forwarding, it works :)

NX uses ssh tunnels as part of the protocol. If you prefer F/LOSS, there is x2go which is also an NX implementation.  They have active development for both the server and the client.

I don't use VNC, but aren't the DISPLAY environments something like :10, not :0?  It uses a different X/Server than the normal desktop would (:0).

I don't use autossh, so didn't feel comfortable responding earlier.

---

### Post by jaro2019 on 2019-08-13
> **TheFu said:**
> NX uses ssh tunnels as part of the protocol. If  you prefer F/LOSS, there is x2go which is also an NX implementation.   They have active development for both the server and the client.

I don't use VNC, but aren't the DISPLAY environments something like :10,  not :0?  It uses a different X/Server than the normal desktop would  (:0).

I don't use autossh, so didn't feel comfortable responding earlier.

Thank you for the suggestion. I would like to use the different DISPLAY  due to I remote from my tablet and another desktop, and it scale to the  native client resolution. The server maximum is stuck at 1366x768 which is too small for me.

---

### Post by TheFu on 2019-08-13
In **x2go**, the resolution is controlled just like on a physical machine, using any of the xrandr tools.  I like **lxrandr** because it is a simple little GUI that isn't too complex.  Setting the initial resolution in the x2go client is also possible.  I run x2go at 1920x1200p all day long.  I have no idea if it supports higher resolutions.

x2go doesn't have a tablet client that I'm aware and I don't remember seeing any ARM linux clients either. That could be an issue, but I honestly haven't looked for either in about 3 yrs.  

In 2008, I did a Central + South America trip with just a Nokia N800 wifi tablet.  At the time, it was freakin' amazing running a version of Debian and did everything I needed.  But it would eat batteries.  Then Microsoft sent in a corporate killer and he killed Nokia and their tablet/phone lines.  

Around 2011, I wanted to travel with just a 10 inch tablet. Did a trip to Europe and ran into all sorts of issues, mostly connectivity.  I never tried travel with just a tablet again.  Turns out that I need just a little more OS.

Since then I've been travelling with a small Ubuntu laptop - 10 inch, then 11 inch, then 13 inch, all sub-3 lbs.  This year, my travel has slowed, so my current laptop is a little bigger and a little heavier, but also more capable, while still being cheap ($305).  On the home LAN, I'll use x2go or vinagre to connect to the different types of clients - spice, NX, rdp, vnc. NX is what I use for Linux, VNC through an ssh tunnel into a Windows virtual machine and RDP into a Windows physical box.  Whenever I'm outside the home LAN, if ssh isn't sufficient (which it is 99% of the time), I'll connect to my desktop running x2go and from there hop onto any other system needed. 

The required DISPLAY should be in the vncserver config or on the command line, right?  Assuming you still want to fight with VNC.

---

### Post by jaro2019 on 2019-08-14
Hope I can travel many countries like you.

I travel with my ipad 6 and an external keyboard. Before that, I have a HP 2570P which is small and "kinda" light, but It can't fit into my sling bag. Now it becomes the linux box, stay at home. The ipad can handle well the documents things, and when I need some heavy coding, I remote to the linux box by Ericom AccessToGo and now NomachineNX. Work without mouse is a bit clumsy, but I feel fine consider how much mobility I got. 

At home I have a windows box for gaming, and it's a remote client when I need to work. With LAN, xrdp and xvnc is enough.

I used to open rdp to windows via Internet, but I got Dharma Ransomware. Somehow latest avast and windows 10 don't save me.

My config is xrdp + lxde at linux box. Any rdp client (Ericom for example) is used to init the remote session. Then I use nomachine to connect to that session.

At work, I just use nomachine and ssh tunnel.

---

