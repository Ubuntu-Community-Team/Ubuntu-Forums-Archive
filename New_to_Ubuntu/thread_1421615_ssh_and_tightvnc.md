---
title: "ssh and tightvnc"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-03-04
I have ssh and xtightvncviewer and tightvncsever installed on 2 ubuntu boxes. I have a windows xp computer with tightvnc installed on it too. How do i use ssh so that the 3 computers will talk to one another?

---

### Post by Bachstelze on 2010-03-04
Not enough information... How is your network set up? What do you mean by "talk to ona another"?

---

### Post by lance bermudez on 2010-03-04
well by talk i mean how to i connect to the different computers. it is a home network.

---

### Post by bodhi.zazen on 2010-03-04
First you do not need VNC, use ssh -X. On windows this involves putty + Xming, both of which are availabe as portable apps (run from a usb device if needed).

With ssh you get a command line, you can start X applications or an entire desktop

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948") 

From Windows :

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Or you can use cygwin (Putty is easier, but cygwin also has an X server).

[http://erikjheels.com/?p=470](http://erikjheels.com/?p=470)

From Linux use the -via option:

[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

or use the -L option with ssh  (see man ssh)

If you want to connect to the windows machines, you need to install an ssh server on windows, see cygwin.

---

### Post by lance bermudez on 2010-03-04
i use ubuntu 9.10 has my os my mother uses windows xp. I need to be able to connect from my ubuntu to her windows xp using tightvnc. I want to use ssh to keep the connection secured. The command line does not bother me to much for the ubuntu to ubuntu connection using ssh with the -C -X but i need a full remote gui view for the windows. any ideas?

---

### Post by bodhi.zazen on 2010-03-04
The windows computer is the server and Ubuntu the client ?

In that case, if you want to use ssh, you need to install an ssh server on Windows.

Personally I advise Cygwin:

[http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)

There are other ssh servers for windows, but I have not used them.

---

### Post by lance bermudez on 2010-03-04
The windows computer is the server and Ubuntu the client ?

this is a hard question because the answer is both. if I'm working on my mother and need to look at mine then the ubuntu is the server but however for most of the time the widows is the server and the ubuntu is the client connection to it.

---

### Post by bodhi.zazen on 2010-03-04
You are starting to go in circles.

If you want to connect to a machine, the machine you connect to is termed the server and the machine you connect from is the client.

If you want to connect to Ubuntu via VNC tunneled over ssh you need to:

1. Install openssh-server on Ubuntu.
2. you can use the default VNC server (vino or desktop sharing).
3. forward port 22 from your router to your Ubuntu box.
4. Use putty + a VNC viewer on windows.

I gave you the links on how to do this, are you having problems ?

If you want to connect to Windows via VNC tunneled over ssh you need to:

1. Install a ssh server on windows (see the cygwin link I gave you).
2. Install a vnc server (you may use tightvnc if you wish).
3. forward port 22 from your router to your windows box.
4. Connect from Ubuntu using ssh. If you wish you can install putty on ubuntu or use

ssh -L 5900:sever:5900 user@server

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Once you connect via ssh or putty you run a vncviewer and connect to localhost

What step are you having a problem with ?

---

### Post by Paddy Landau on 2010-03-04
Try [Yuuguu](http://www.yuuguu.com/)

---

### Post by lance bermudez on 2010-03-04
i was told that -via gateway
Automatically create encrypted TCP tunnel to the gateway machine
before  connection,  connect  to  the  host  through that tunnel
(TightVNC-specific). By default, this option invokes  SSH  local
port forwarding, assuming that SSH client binary can be accessed
as /usr/bin/ssh. Note that when using the -via option, the  host
machine  name  should  be  specified  as  known  to  the gateway
machine, e.g.  "localhost" denotes the gateway, not the  machine
where  vncviewer was launched. See the ENVIRONMENT section below
for the information on configuring the -via option.


lance@bermudezl:~$ xtightvncviewer -via 192.168.2.100
TightVNC Viewer version 1.3.9

Usage: xtightvncviewer [<OPTIONS>] [<HOST>][:<DISPLAY#>]
       xtightvncviewer [<OPTIONS>] [<HOST>][::<PORT#>]
       xtightvncviewer [<OPTIONS>] -listen [<DISPLAY#>]
       xtightvncviewer -help

<OPTIONS> are standard Xt options, or:
        -via <GATEWAY>
        -shared (set by default)
        -noshared
        -viewonly
        -fullscreen
        -noraiseonbeep
        -passwd <PASSWD-FILENAME> (standard VNC authentication)
        -encodings <ENCODING-LIST> (e.g. "tight copyrect")
        -bgr233
        -owncmap
        -truecolour
        -depth <DEPTH>
        -compresslevel <COMPRESS-VALUE> (0..9: 0-fast, 9-best)
        -quality <JPEG-QUALITY-VALUE> (0..9: 0-low, 9-high)
        -nojpeg
        -nocursorshape
        -x11cursor
        -autopass

Option names may be abbreviated, e.g. -bgr instead of -bgr233.
See the manual page for more information.

what am i doing wrong?

---

### Post by bodhi.zazen on 2010-03-04
xtightvncviewer -via 192.168.2.100 192.168.2.100

---

### Post by dominionize on 2010-03-04
Hello im New to ubuntu, i want to install PuTTy and open it like any other programm HELP

---

### Post by lance bermudez on 2010-03-04
lance@bermudezl:~$ xtightvncviewer -via 192.168.2.100 192.168.2.100
ssh: connect to host 192.168.2.100 port 22: Connection refused
xtightvncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:192.168.2.100:5900 192.168.2.100 sleep 20.

i have the windows set to use port 22. file wall is off

---

### Post by lance bermudez on 2010-03-04
dominionize are you trying to put PuTTy on ubuntu?
for ubuntu system>administration>synaptic
in synaptic use the search for putty 
check the box by putty
hit apply


from the ubuntu to windows i can get the program to work with
xtightvncviewer 192.168.2.100:22
but i would like the -via to know that the view is protected

---

### Post by lance bermudez on 2010-03-05
for the linux to linux
lance@bermudezl:~$ xtightvncviewer -via 192.168.2.103 -compresslevel 9 -x11cursor
lance@192.168.2.103's password: 
Permission denied, please try again.
lance@192.168.2.103's password: 
Permission denied, please try again.
lance@192.168.2.103's password: 
Permission denied (publickey,password).
xtightvncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:-x11cursor:5900 192.168.2.103 sleep 20.

i have the system>preferences>remote desktop password set and turned on
i have tired this password and also the ssh password key. i have moved the publickey password to both linux boxes

---

### Post by lance bermudez on 2010-03-06
xtightvncviewer -via "pete@192.168.2.103 -p 22" -compresslevel 9 -x11cursor localhost:0
the above works for linux i have another computer that i need to connect to from my linux box it is a windows xp computer with tightvnc on it set to accept port 22 how do i use the -via to connect to that computer also

---

