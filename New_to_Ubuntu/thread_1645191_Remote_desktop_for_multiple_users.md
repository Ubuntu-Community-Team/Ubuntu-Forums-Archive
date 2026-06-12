---
title: "Remote desktop for multiple users"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by RussellEngland on 2010-12-14
Is there something like remote desktop but have multiple users logging into their own desktop?

---

### Post by lukeiamyourfather on 2010-12-14
I was going to say VNC, but I think that works only if a single user is already logged in. Never tried it with multiple sessions and desktops.

---

### Post by CharlesA on 2010-12-14
IIRC, you can use something like tightvnc and each user will have their own session.

There's also FreeNX (from nomachines.com) but the free version can only support 2 sessions.

---

### Post by HermanAB on 2010-12-14
Howdy,

SSH of course.

Create user accounts for multiple users, dumkopf, tom and harry, then log in with ssh like this:
$ ssh -X -C -c blowfish dumkopf@serveripaddress gnome-panel

and ditto for tom and harry.  As many as you want really, then go click happy.

That also works from Windoze if you install Cygwin with OpenSSH and whatever else you want to run.

---

### Post by Artif on 2012-03-29
I'm looking for subject. A way to use over LAN _all_ resources of a   remote computer. For example - I have laptop with week Atom processor   and no 3D, but I want to use it for editing of my video on my powerful  remote desktop.

**[SIZE=2]Hey! Anyone have good software review or a &quot;how to&quot;?[/SIZE]**


> **RussellEngland said:**
> Is there something like remote desktop   but have multiple users logging into their own desktop?

Programs to be launched via SSH '-X' will be stopped on your disconnect.   I do not know a way to &quot;launch and forget&quot; a task on server. 3D   applications will use your client's local graphics processor, or no 3D   acceleration will be used at all, or you'll fail to use 3D application.

With VNC it's possible to &quot;launch and forget&quot;. You may connect to your   desktop from several places and to continue working with applications   already launched earlier. Several users can use a same computer locally   and remotely simultaneously. You need to use polkit to prevent   unexpected shutdowns. Launch of 3D applications is not possible, or you   need additional complex installation of VirtualGL, or else. You may  need  to protect your VNC server with SSH, for example.

I do not use FreeNX. It is GPL implementation of NoMachine. I have read in mailing lists FreeNX seems to have   issues with 3D - it will use your client's 3D, or nothing, or complex  setup (a  kind of an agent).

LTSP project is something special, it is for diskless stations or smth. similar. It is much more boot manager.

** A workaround could be:**
1) Setup SSH tunnel to server, 2) setup VNC on server for localhost, 3) setup VirtualGL.

The first two steps are widely described. There are a lof of VNC servers. Some of them are already protected with TLS, or SSH, or else. The third is mentioned rarely, and in connection with attempts of 3D applications launch.

VirtualGL have **security issues** - access to X-Server and possible sniff of keystrokes and similar. But it can provide a way to launch 3D application on remote server, using a 3D hardware and drivers of remote server.

It seems the software is smart enough. You must install it, stop all GUI software, do configure with the help of it's internal script, relaunch your GUI and you can simply launch 'vglrun your.application.bin'. See documentation:
[http://www.virtualgl.org/Documentation/Documentation](http://www.virtualgl.org/Documentation/Documentation)

Setup may be smth. like the following. Setup TightVNC connection to your server, may be secured with SSH tunnel.
Login on your server via TightVNC and separately via SSH, on your server do in terminal (commands are for my system):
```
$ sudo dpkg -i VirtualGL_2.3_amd64.deb
$ sudo /etc/init.d/gdm stop
# /opt/VirtualGL/bin/vglserver_config
# reboot
$ xauth merge /etc/opt/VirtualGL/vgl_xauth_key
$ xdpyinfo -display :0
$ /opt/VirtualGL/bin/glxinfo -display :0 -c

$ /opt/VirtualGL/bin/vglrun /opt/sweetHome3D/SweetHome3D
$ /opt/VirtualGL/bin/vglrun hugin

```0) hugin and SweetHome3D are 3D programs, there is launch example. You may modify shortcuts for software.
1) GDM is not used now AFAIR. As for me - I'm using LXDM. Choose your own...
2) Mentioned commands were used on my system, for you they may differ. This is not step by step howto.
3) Pay attention, there is 'reboot' command for remote computer. Will it be accessible after reboot?
4) The workaround will allow simultaneous usage of the server by several remote users, at the same time one local user can login and work at physical console.
5) After GUI stop you'll need SSH access to server.

---

