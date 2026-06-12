---
title: "Installing FreeNX"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by scribbles on 2009-02-07
Following [this guide]("https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server"), I initially had gpg key issues but resolved them by using the Launchpad PPA FAQ on keys. 

After getting the right repo's into sources.list, I ran ```
sudo apt-get install freenx
``` and got this ```
sudo apt-get install freenx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  expect freenx-media freenx-rdp freenx-server freenx-session-launcher freenx-vnc libxcomp3 libxcompext3 libxcompshad3 nxagent nxlibs smbfs x11vnc xvnc4viewer
Suggested packages:
  expectk libarts1c2 libarts1 xdm vnc4-common vnc-common
The following NEW packages will be installed:
  expect freenx freenx-media freenx-rdp freenx-server freenx-session-launcher freenx-vnc libxcomp3 libxcompext3 libxcompshad3 nxagent nxlibs smbfs x11vnc xvnc4viewer
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 5596kB of archives.
After this operation, 14.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net intrepid/main libxcomp3 3.3.0-3-0freenxteam2 [384kB]
Get:2 http://archive.ubuntu.com intrepid/main expect 5.43.0-16 [317kB]
Get:3 http://archive.ubuntu.com intrepid-updates/main smbfs 2:3.2.3-1ubuntu3.4 [1376kB]
Get:4 http://ppa.launchpad.net intrepid/main libxcompext3 1:3.3.0-3-0freenxteam1~intrepid1 [35.2kB]
Get:5 http://ppa.launchpad.net intrepid/main libxcompshad3 3.3.0-2-0freenxteam1 [25.3kB]
Get:6 http://ppa.launchpad.net intrepid/main nxlibs 3.3.0-4-9-0freenxteam1~intrepid1 [561kB]
Get:7 http://ppa.launchpad.net intrepid/main nxagent 3.3.0-4-9-0freenxteam1~intrepid1 [1772kB]
Get:8 http://archive.ubuntu.com intrepid/universe x11vnc 0.9.3.dfsg.1-1ubuntu1 [765kB]
Get:9 http://ppa.launchpad.net intrepid/main freenx-rdp 0.7.3+svn612-0freenxteam11~intrepid1 [20.8kB]
Get:10 http://ppa.launchpad.net intrepid/main freenx-vnc 0.7.3+svn612-0freenxteam11~intrepid1 [20.8kB]
Get:11 http://ppa.launchpad.net intrepid/main freenx-server 0.7.3+svn612-0freenxteam11~intrepid1 [105kB]
Get:12 http://ppa.launchpad.net intrepid/main freenx-media 0.7.3+svn612-0freenxteam11~intrepid1 [24.9kB]
Get:13 http://ppa.launchpad.net intrepid/main freenx-session-launcher 0.7.3+svn612-0freenxteam11~intrepid1 [24.3kB]
Get:14 http://ppa.launchpad.net intrepid/main freenx 0.7.3+svn612-0freenxteam11~intrepid1 [20.8kB]
Get:15 http://archive.ubuntu.com intrepid/universe xvnc4viewer 4.1.1+xorg1.0.2-0ubuntu7 [143kB]
Fetched 5596kB in 4s (1301kB/s)
Preconfiguring packages ...
Selecting previously deselected package expect.
(Reading database ... 175673 files and directories currently installed.)
Unpacking expect (from .../expect_5.43.0-16_i386.deb) ...
Selecting previously deselected package libxcomp3.
Unpacking libxcomp3 (from .../libxcomp3_3.3.0-3-0freenxteam2_i386.deb) ...
Selecting previously deselected package libxcompext3.
Unpacking libxcompext3 (from .../libxcompext3_1%3a3.3.0-3-0freenxteam1~intrepid1_i386.deb) ...
Selecting previously deselected package smbfs.
Unpacking smbfs (from .../smbfs_2%3a3.2.3-1ubuntu3.4_i386.deb) ...
Selecting previously deselected package x11vnc.
Unpacking x11vnc (from .../x11vnc_0.9.3.dfsg.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package xvnc4viewer.
Unpacking xvnc4viewer (from .../xvnc4viewer_4.1.1+xorg1.0.2-0ubuntu7_i386.deb) ...
Selecting previously deselected package libxcompshad3.
Unpacking libxcompshad3 (from .../libxcompshad3_3.3.0-2-0freenxteam1_i386.deb) ...
Selecting previously deselected package nxlibs.
Unpacking nxlibs (from .../nxlibs_3.3.0-4-9-0freenxteam1~intrepid1_i386.deb) ...
Selecting previously deselected package nxagent.
Unpacking nxagent (from .../nxagent_3.3.0-4-9-0freenxteam1~intrepid1_i386.deb) ...
Selecting previously deselected package freenx-rdp.
Unpacking freenx-rdp (from .../freenx-rdp_0.7.3+svn612-0freenxteam11~intrepid1_all.deb) ...
Selecting previously deselected package freenx-vnc.
Unpacking freenx-vnc (from .../freenx-vnc_0.7.3+svn612-0freenxteam11~intrepid1_all.deb) ...
Selecting previously deselected package freenx-server.
Unpacking freenx-server (from .../freenx-server_0.7.3+svn612-0freenxteam11~intrepid1_i386.deb) ...
Selecting previously deselected package freenx-media.
Unpacking freenx-media (from .../freenx-media_0.7.3+svn612-0freenxteam11~intrepid1_i386.deb) ...
Selecting previously deselected package freenx-session-launcher.
Unpacking freenx-session-launcher (from .../freenx-session-launcher_0.7.3+svn612-0freenxteam11~intrepid1_i386.deb) ...
Selecting previously deselected package freenx.
Unpacking freenx (from .../freenx_0.7.3+svn612-0freenxteam11~intrepid1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up expect (5.43.0-16) ...

Setting up libxcomp3 (3.3.0-3-0freenxteam2) ...

Setting up libxcompext3 (1:3.3.0-3-0freenxteam1~intrepid1) ...

Setting up smbfs (2:3.2.3-1ubuntu3.4) ...
Setting up x11vnc (0.9.3.dfsg.1-1ubuntu1) ...
Setting up xvnc4viewer (4.1.1+xorg1.0.2-0ubuntu7) ...

Setting up libxcompshad3 (3.3.0-2-0freenxteam1) ...

Setting up nxlibs (3.3.0-4-9-0freenxteam1~intrepid1) ...

Setting up nxagent (3.3.0-4-9-0freenxteam1~intrepid1) ...
Setting up freenx-server (0.7.3+svn612-0freenxteam11~intrepid1) ...
/etc/init.d/freenx-server: line 17: /nxserver: No such file or directory
/etc/init.d/freenx-server: line 18: /nxserver: No such file or directory

Setting up freenx-rdp (0.7.3+svn612-0freenxteam11~intrepid1) ...
Setting up freenx-media (0.7.3+svn612-0freenxteam11~intrepid1) ...

Setting up freenx-session-launcher (0.7.3+svn612-0freenxteam11~intrepid1) ...
 * Reloading system message bus config...                                                                                                                                                                                                [ OK ]

Setting up freenx-vnc (0.7.3+svn612-0freenxteam11~intrepid1) ...
Setting up freenx (0.7.3+svn612-0freenxteam11~intrepid1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for menu ...

``` You'll notice a few lines up it shows the init.d line saying that /nxserver does not exist. I tried to stop/restart freenx via init.d and it said /etc/init.d/freenx command not found. What went wrong?

---

### Post by scribbles on 2009-02-07
bump

---

### Post by dougie173 on 2009-02-07
I've just installed freenx myself and have just got my head around how I *think* it works.

When you start an nx session the nx client logs onto your machine using ssh as user nx. 

looking at my /etc/passwd:

nx:x:122:135:FreeNX Server,,,:/var/lib/nxserver/home/:/usr/bin/nxserver

you can see that as soon as that the nx user logs in it spawns the nxserver which the nx client then uses to tunnel the traffic through. So the startup script in the /etc/init.d is a bit of a red herring.


Now if I could just get VNC working over it grrrr!!!! #-o#-o#-o


Hope this helps

---

### Post by scribbles on 2009-02-07
But shouldn't freenx-server be up and running awaiting a client interaction then login as user nx? Should I not be able to restart the server whether or not its in use?

---

### Post by dougie173 on 2009-02-07
No it only starts nxserver when a nx client starts a session and closes it when the session closes.

When I run 'ps -ef|grep nx' normally there's nothing. When I've got a nx client connected running 'ps -ef|grep nx' shows that nxserver is running.

The nxserver doesn't need to be running all the time. Only sshd needs to be running. The nxserver process will start only when it's needed.

---

### Post by scribbles on 2009-02-07
```
NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
``` This is as far as I've gotten. I have sshd setup with no password auth so the keys have to be preloaded. When I use putty I have to load my rsa key into pageant and then connect via putty and just enter my username. I tried importing the key I use into nx client and then connecting and it wouldn't work. I just tried entering the default DSA key which looks like the paragraph style block into my .sshd authorized_keys file and it just closed the remote connection. 

I don't get it.

---

### Post by dougie173 on 2009-02-07
Hmmm sshd with no password auth. That's not how I've got mine set up. So I may be shooting in the dark but hey I'll give it a go!! Two heads and all that ;)

Have you installed the freenx key from the server in the nx client. You need to copy it from /var/lib/nxserver/home/custom_keys/client.id_dsa.key

Also do you have 'AllowedUsers' in /etc/ssh/sshd_config? 
If so then you need to add the nx user to this.

I spent a couple of hours last night pulling my hair out as I was getting this error.

---

### Post by scribbles on 2009-02-07
I added user 'nx' to AllowedUsers and still got the same error.
```

:/var/lib/nxserver$ cd /var/lib/nxserver
:/var/lib/nxserver$ ls
db  home
:/var/lib/nxserver$ cd home
-bash: cd: home: Permission denied
:/var/lib/nxserver$ sudo cd home
sudo: cd: command not found
:/var/lib/nxserver$

``` Could this be a result of me using PuTTy to do remote terminal commands? I can't get to client.id_dsa.key.

---

### Post by kevdog on 2009-02-07
Log in as root:

sudo su

Then you can change to that directory.

---

### Post by scribbles on 2009-02-07
Thanks kevdog!

The key in the file is the same 'default key' that the freenx client shows in vista. I added that to my authorized_keys file but ti is the --------BEGIN DSA PRIVATE KEY--------- paragraph style key while the other ssh-rsa key I have is listed in the one line style, does SSH differentiate between these listing types?

Note that I did try pasting the paragraph style private key and it failed. There is a ssh-dss private key one line style in /var/lib/nxserver/home/authorized_keys2....

---

### Post by scribbles on 2009-02-08
The keyblock in /var/lib/nxserver/home/client.id_dsa.key is the DSA PRIVATE KEY, the key that goes into ~/.ssh/authorized_keys is the public key. 

I can see in auth.log it shows the client wasn't previously allowed to connect because it wasn't in AllowedUsers but subsquent connections after user 'nx' was added just show refused.

Which key from freenx do I use and how does it fit in with the client?

Does freenx support NoPasswordAuth?

---

### Post by scribbles on 2009-02-08
My local ip showed up in denyhosts which shows why it was being refused, but I still get this msg...
```

NX> 203 NXSSH running with pid: 2376
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.*.* on port: 22
NX> 202 Authenticating user: nx
Ubuntu 8.10 \n \l

NX> 208 Using auth method: publickey
NX> 204 Authentication failed.
```

---

### Post by scribbles on 2009-02-08
bump

---

### Post by andser on 2009-02-15
> **scribbles said:**
> bump

Start script is looking for nxserver executable. In my working install is located in /usr/lib/nx

In my case I had to edit:

/etc/init.d/**freenx-server**

add:

**PATH_BIN=/usr/lib/nx**

just before:

case "$1" in
        start)


Simple restart:

sudo /etc/init.d/freenx-server restart

---

