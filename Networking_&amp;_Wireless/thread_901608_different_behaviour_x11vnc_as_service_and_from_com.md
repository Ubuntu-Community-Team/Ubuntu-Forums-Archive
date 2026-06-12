---
title: "different behaviour x11vnc as service and from command line"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by Ray-ubunter on 2008-08-26
Hi,

I seem to be experiencing a strange difference when running x11vnc as a service and from the command line.

When I run x11vnc as a service:

service x11vnc
{
        port            = 5900
        type            = UNLISTED
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        server          = /usr/bin/x11vnc
        server_args     = -inetd -avahi -o /var/log/x11vnc.log -auth /var/lib/gdm/:0.Xauth -bg -display :0
        disable         = no
}

one of my viewers (default ¨screen sharing.app¨) on my mac is not able to open a connection properly (continues connecting but nothing happens).

x11vnc server log says:

26/08/2008 21:39:30   other clients:
26/08/2008 21:39:30 Disabled X server key autorepeat.
26/08/2008 21:39:30   to force back on run: 'xset r on' (3 times)
26/08/2008 21:39:30 Client Protocol Version 3.889
26/08/2008 21:39:30 Protocol version sent 3.889, using 3.889
26/08/2008 21:39:30 created xdamage object: 0xa00024
26/08/2008 21:39:30 rfbProcessClientSecurityType: executing handler for type 1
26/08/2008 21:39:30 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
26/08/2008 21:39:46 cutbuffer_send: no send: uninitialized clients


However when I run x11vnc from the command line

x11vnc -shared -forever -rfbauth -o ~/x11vnc.succes /home/remi/.vnc/passwd -display :0

there there is no problem connecting using this client


26/08/2008 21:02:05 Got connection from client 192.168.0.104
26/08/2008 21:02:05   other clients:
26/08/2008 21:02:05 Disabled X server key autorepeat.
26/08/2008 21:02:05   to force back on run: 'xset r on' (3 times)
26/08/2008 21:02:05 created xdamage object: 0x800024
26/08/2008 21:02:05 Client Protocol Version 3.889
26/08/2008 21:02:05 Protocol version sent 3.889, using 3.889
26/08/2008 21:02:05 rfbProcessClientSecurityType: executing handler for type 2
26/08/2008 21:02:06 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x000003F3)
26/08/2008 21:02:06 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x000003EA)
26/08/2008 21:02:06 Enabling full-color cursor updates for client 192.168.0.104


When using other clients there is no problem in either case however I would much prefer to use the default (allows server side scaling), and am slightly annoyed by the fact I don seem to be able to get it to work.

Any ideas?

Thanks
Remi

---

### Post by krunge on 2008-08-26
> **Ray-ubunter said:**
> 
        server_args     = -inetd -avahi -o /var/log/x11vnc.log -auth /var/lib/gdm/:0.Xauth -bg -display :0
 
You might want to edit your post and remove the "-avahi" and "-bg" options from server_args. They don't make sense for inetd mode.  Under inetd stdio is used, so it can't go into the background (I believe x11vnc ignores "-bg" in this case).

For "-avahi" it also doesn't make much sense:  under inetd x11vnc isn't running until the connection is made; so how could it advertise itself to the local network?

If you edit these out of your post you can help limit the spread of confusion.

It is also possible the "-avahi" is causing your problem, but you say other viewers can connect via the inetd method so I guess it is probably not the cause...
> 
one of my viewers (default ¨screen sharing.app¨) on my mac is not able to open a connection properly (continues connecting but nothing happens).

x11vnc server log says:

26/08/2008 21:39:30   other clients:
26/08/2008 21:39:30 Disabled X server key autorepeat.
26/08/2008 21:39:30   to force back on run: 'xset r on' (3 times)
26/08/2008 21:39:30 Client Protocol Version 3.889
26/08/2008 21:39:30 Protocol version sent 3.889, using 3.889
26/08/2008 21:39:30 created xdamage object: 0xa00024
26/08/2008 21:39:30 rfbProcessClientSecurityType: executing handler for type 1
26/08/2008 21:39:30 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
26/08/2008 21:39:46 cutbuffer_send: no send: uninitialized clients


I'm confused why it works for the command line case.  But an issue here is that Apple violates the VNC/RFB protocol to some degree by "cleverly" cooking up their own special protocol version "3.889".  For compatibility with other VNC software they aren't supposed to do that.

For RFB protocol 3.8 and higher there is an extra step in the handshaking.  I think that is causing the problem.  Why it works for you sometimes is unclear to me...

I tested with my macbook and a workaround seems to be to add the option "-rfbversion 3.3" to the x11vnc cmd line.  Then it pretends to be an older server and that seems to trick the mac screen_sharing.app into using 3.3 too.

Let me know if it works or not.

BTW, the mac screen sharing viewer seems quirky and sluggish to me.  Do you see this too?

---

### Post by mhoydis on 2008-11-01
I confirm that adding "-rfbversion 3.3" to the command line allows the Screen Sharing client in OS X (Leopard) to connect to x11vnc (Ubuntu Intrepid).

But the Screen Sharing client is then very unstable and effectively unusable :(
It keeps prompting to ignore the lack of encryption at the server (even after it seems to be successfully connected and working), then eventually crashes.  The x11vnc.log spits out this...

01/11/2008 10:55:11 Client Protocol Version 3.3
01/11/2008 10:55:11 Protocol version sent 3.3, using 3.3
01/11/2008 10:55:11 created xdamage object: 0x2c0002c
01/11/2008 10:55:11 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x000003F3)
01/11/2008 10:55:11 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x000003EA)
01/11/2008 10:55:11 Enabling full-color cursor updates for client 192.168.1.3
01/11/2008 10:55:11 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x00000450)
01/11/2008 10:55:11 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x0000044C)
01/11/2008 10:55:11 Enabling NewFBSize protocol extension for client 192.168.1.3
01/11/2008 10:55:11 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x0000044D)
01/11/2008 10:55:11 Using zlib encoding for client 192.168.1.3
01/11/2008 10:55:11 Pixel format for client 192.168.1.3:
01/11/2008 10:55:11   32 bpp, depth 32, little endian
01/11/2008 10:55:11   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
01/11/2008 10:55:27 client_count: 0
01/11/2008 10:55:27 inetd viewer exited.
01/11/2008 10:55:27 deleted 40 tile_row polling images.

---

### Post by mhoydis on 2008-11-01
I'm having good luck using JollyFastVNC as a client.
[http://www.jinx.de/JollysFastVNC.html](http://www.jinx.de/JollysFastVNC.html)

---

