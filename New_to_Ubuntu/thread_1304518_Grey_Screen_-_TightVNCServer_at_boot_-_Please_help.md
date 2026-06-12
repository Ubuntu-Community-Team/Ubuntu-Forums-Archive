---
title: "Grey Screen - TightVNCServer at boot - Please help"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Marble68 on 2009-10-29
Sorry if this is the wrong forum - 

I've gone through numerous posts and almost have tightvncserver working at boot time.

When my Ubuntu Jaunty workstation (UBU001) boots, TightVNCServer starts and I can connect.

However, I get the dreaded grey screen.

I've been editing my **/home/(user)/.vnc/xstartup** file and testing various results.

I can get a terminal window to come up, etc.

However, It seems like I can't get gnome to start.

This blog post seemed very helpful:
[http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot]("http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot")

I followed instructions there first, and have wallowed around the intertubes looking for an answer ever since.

I've added **gnome-session** & to the xstartup file to no avail.

If I login and sudo I get better results.  It's almost as if once I sudo to root and restart /etc/inet.d/vncserver it works.  To me, this implies some sort of security issue?  Perhaps I have the wrong permissions somewhere?

I've examined the logs and don't see anything that jumps out at me.  Perhaps more experienced eyes will spot an obvious mistake I'm making.

The only error I see is this line in the logs:
**Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'**

On a side note, do I need to remove Vivo?

Thanks in advance for any guidance or help; I'd really appreciate it.

Here are my files.

*START ***********************  /home/(username)/.vnc/xstartup*

#!/bin/sh
#unset SESSION_MANAGER
#exec sh /etc/X11/xinit/xinitrc

#xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc
exec gnome-session &

#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#gnome-session &

#unset SESSION_MANAGER
#sh /etc/X11/xinit/xinitrc

#unset SESSION_MANAGER
#gnome-session &


*END   ***********************  /home/(username)/.vnc/xstartup*




[I]
START ***********************  /etc/init.d/vncserver[/I]
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          vncserver
# Required-Start:    networking
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

PATH="$PATH:/usr/X11R6/bin/"

# The Username:Group that will run VNC
export USER="(username removed)"
#${RUNAS}

# The display that VNC will use
DISPLAY="1"

# Color depth (between 8 and 32)
DEPTH="16"

# The Desktop geometry to use.
#GEOMETRY="<WIDTH>x<HEIGHT>"
#GEOMETRY="800x600"
GEOMETRY="1024x768"
#GEOMETRY="1280x1024"

# The name that the VNC Desktop will have.
NAME="UBU001"

OPTIONS="-name ${NAME} -depth ${DEPTH} -geometry ${GEOMETRY} :${DISPLAY}"

. /lib/lsb/init-functions

case "$1" in
start)
log_action_begin_msg "Starting vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/tightvncserver ${OPTIONS}"
;;

stop)
log_action_begin_msg "Stoping vncserver for user '${USER}' on localhost:${DISPLAY}"
su ${USER} -c "/usr/bin/tightvncserver -kill :${DISPLAY}"
;;

restart)
$0 stop
$0 start
;;
esac

exit 0


*END   ***********************  /etc/init.d/vncserver*


*END   ***********************  /home/(username)/.vnc/ubu001:1.log*


Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
29/10/09 05:10:09 Xvnc version TightVNC-1.3.9
29/10/09 05:10:09 Copyright (C) 2000-2007 TightVNC Group
29/10/09 05:10:09 Copyright (C) 1999 AT&T Laboratories Cambridge
29/10/09 05:10:09 All Rights Reserved.
29/10/09 05:10:09 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
29/10/09 05:10:09 Desktop name 'UBU001' (ubu001:1)
29/10/09 05:10:09 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
29/10/09 05:10:09 Listening for VNC connections on TCP port 5901
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
29/10/09 05:10:38 Xvnc version TightVNC-1.3.9
29/10/09 05:10:38 Copyright (C) 2000-2007 TightVNC Group
29/10/09 05:10:38 Copyright (C) 1999 AT&T Laboratories Cambridge
29/10/09 05:10:38 All Rights Reserved.
29/10/09 05:10:38 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
29/10/09 05:10:38 Desktop name 'UBU001' (ubu001:1)
29/10/09 05:10:38 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t

29/10/09 10:13:08 Got connection from client XXX.XXX.XXX.XXX
29/10/09 10:13:08 Non-standard protocol version 3.4, using 3.3 instead
29/10/09 10:13:13 Full-control authentication passed by XXX.XXX.XXX.XXX
29/10/09 10:13:13 Pixel format for client XXX.XXX.XXX.XXX:
29/10/09 10:13:13   8 bpp, depth 8
29/10/09 10:13:13   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding 16
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding 17
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding 9
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding 8
29/10/09 10:13:13 Using tight encoding for client XXX.XXX.XXX.XXX
29/10/09 10:13:13 Using compression level 6 for client XXX.XXX.XXX.XXX
29/10/09 10:13:13 Enabling X-style cursor updates for client XXX.XXX.XXX.XXX
29/10/09 10:13:13 Enabling cursor position updates for client XXX.XXX.XXX.XXX
29/10/09 10:13:13 Using image quality level 6 for client XXX.XXX.XXX.XXX
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding -65530
29/10/09 10:13:13 Enabling LastRect protocol extension for client XXX.XXX.XXX.XXX
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding -223
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding -65535
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding -32768
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding -32767
29/10/09 10:13:13 rfbProcessClientNormalMessage: ignoring unknown encoding -32766
29/10/09 10:13:14 Pixel format for client XXX.XXX.XXX.XXX:
29/10/09 10:13:14   16 bpp, depth 16, little endian
29/10/09 10:13:14   true colour: max r 31 g 63 b 31, shift r 11 g 5 b 0
29/10/09 10:13:14   no translation needed
29/10/09 10:13:14 Using hextile encoding for client XXX.XXX.XXX.XXX
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding 17
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding 16
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding 9
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding 8
29/10/09 10:13:14 Using compression level 6 for client XXX.XXX.XXX.XXX
29/10/09 10:13:14 Enabling X-style cursor updates for client XXX.XXX.XXX.XXX
29/10/09 10:13:14 Enabling cursor position updates for client XXX.XXX.XXX.XXX
29/10/09 10:13:14 Using image quality level 6 for client XXX.XXX.XXX.XXX
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding -65530
29/10/09 10:13:14 Enabling LastRect protocol extension for client XXX.XXX.XXX.XXX
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding -223
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding -32768
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding -32767
29/10/09 10:13:14 rfbProcessClientNormalMessage: ignoring unknown encoding -32766
29/10/09 10:13:47 Client XXX.XXX.XXX.XXX gone
29/10/09 10:13:47 Statistics:
29/10/09 10:13:47   key events received 0, pointer events 701
29/10/09 10:13:47   framebuffer updates 4, rectangles 20, bytes 1199242
29/10/09 10:13:47     LastRect markers 1, bytes 12
29/10/09 10:13:47     cursor shape updates 2, bytes 164
29/10/09 10:13:47     cursor position updates 2, bytes 24
29/10/09 10:13:47     hextile rectangles 3, bytes 1198128
29/10/09 10:13:47     tight rectangles 12, bytes 914
29/10/09 10:13:47   raw bytes equivalent 5505072, compression ratio 4.591225







*END   ***********************  /home/(username)/.vnc/ubu001:1.log*

---

