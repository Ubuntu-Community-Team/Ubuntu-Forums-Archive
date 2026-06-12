---
title: "X over SSH?"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by linuxpenguin on 2007-01-26
I've got a remote server running Ubuntu Server and OpenSSH.

I understand that there's some way to set up X on this server and make it tunnel through OpenSSH so that I can control a GUI application remotely?  How can I set this up?

---

### Post by guysmiley25 on 2007-01-26
Are you meaning X forwarding.

```

ssh username@ip -X

```

I'm not sure if you need to have X installed on the remote machine or not! I might give it ago now though.

---

### Post by chili555 on 2007-01-26
ssh -X -l user 192.168.0.101 (or wherever)

-X simply means...well, gimme some X!

Probably a more elegant way to do this, but old folks have old ways.

"I'm not sure if you need to have X installed on the remote machine or not!" Installed? Probably. Running, i.e. runlevel 5? No.

---

### Post by linuxpenguin on 2007-01-26
I'm on a Windows PC right now though, with PuTTY, which supposedly can handle this.  Are you saying that I have to SSH from my remote machine back to my desktop machine?

---

### Post by guysmiley25 on 2007-01-26
Ok so I logged into my remote ubuntu server, that is headless. I install a app called mousepad. A text editor for xfce.

sshed into the box

```
ssh username@ip -X
```

ran mousepad

```
mousepad
```

and got

```
(mousepad:16343): Gtk-WARNING **: cannot open display:  
```

So I do not think this can be done. If so not that easily and I do not know how.

---

### Post by guysmiley25 on 2007-01-26
Not with putty. You need something called Cygwin/X.

---

### Post by chili555 on 2007-01-26
[http://the.earth.li/~sgtatham/putty/0.59/htmldoc/Chapter3.html#using-x-forwarding](http://the.earth.li/~sgtatham/putty/0.59/htmldoc/Chapter3.html#using-x-forwarding)

Looks like you will need to have X running on your Windows machine.

> In order to use this feature, you will need an X display server for your Windows machine, such as Cygwin/X, X-Win32, or Exceed.

---

### Post by guysmiley25 on 2007-01-26
Ok got it to work in my case. If your server is headless you will need xauth

```
sudo apt-get install xauth
``` on the remote machine.

---

### Post by dbott67 on 2007-01-26
You can also use freenx (aka nomachine - [http://www.nomachine.com/)](http://www.nomachine.com/)).  NoMachine creates an SSH tunnel to connect to your remote machine & it's very fast.

Another user (darrenm) pointed it out to me & I am very impressed:
> **darrenm said:**
> I used to use VNC but found it a bit too bandwidth heavy. 

I just download the 3 packages from [www.nomachine.com](www.nomachine.com) - Free Linux server, NXNode and NXclient for Debian/Ubuntu and install.

From the NoMachine website:
>  NoMachine NX is a Terminal Server and Remote Access solution based on a comprising set of enterprise class open source technologies. Thanks to the outstanding compression, session resilience and resource management developed on top of the X-Window system, and the integration with the powerful audio, printing and resource sharing capabilities of the Unix world, NoMachine NX makes it possible to run any graphical application on any operating system across any network connection as if you were sitting in front of your computer.


Here's a couple of screenshots of me connecting from my XP computer and my Ubuntu desktop computer to the Ubuntu computer running NX server.

-Dave

---

### Post by zetsumei on 2007-02-07
i get the following error after downloading/insalling cgywin and running putty

Gdk=ERROR **; X connection to localhost:10.0 broken (explicit kill or server shutdown).

how do i fix this?

---

### Post by oldweasel on 2007-02-07
Dbott67: do you have SSHserver and nxserver running at the same time? I am getting a ssh connection refused and wonder if NXClient is trying to connect with the sshserver instead of the nxserver. Thoughts?

---

### Post by dbott67 on 2007-02-07
> **oldweasel said:**
> Dbott67: do you have SSHserver and nxserver running at the same time? I am getting a ssh connection refused and wonder if NXClient is trying to connect with the sshserver instead of the nxserver. Thoughts?

Yes, I'm running both.  I've just SSH'd into my home computer, and run the following commands.  This is what I get just before I login via NX:
```
dbott@thedrake:~$ ps aux | grep NX
dbott    24640  0.0  0.3   4584  3304 ?        S    Jan24   0:03 /usr/NX/bin/nxesd -tcp -nobeeps -port 6000 -bind 127.0.0.1
dbott     9063  0.0  0.0   2880   796 pts/3    R+   11:17   0:00 grep NX

dbott@thedrake:~$ ps aux | grep ssh
root      4586  0.0  0.1   4764   976 ?        Ss   Jan09   0:00 /usr/sbin/sshd
dbott     4885  0.0  0.0   4332   628 ?        Ss   Jan09   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
root      8991  0.0  0.2   7528  2368 ?        Ss   11:16   0:00 sshd: dbott [priv]
dbott     9001  0.0  0.1   7528  1544 ?        S    11:16   0:00 sshd: dbott@pts/3
dbott     9074  0.0  0.0   2876   792 pts/3    R+   11:17   0:00 grep ssh

```

Here is what I get just after logging in via NX:
```
dbott@thedrake:~$ ps aux | grep NX
dbott    24640  0.0  0.3   4584  3304 ?        S    Jan24   0:03 /usr/NX/bin/nxesd -tcp -nobeeps -port 6000 -bind 127.0.0.1
nx        9161  3.0  2.7  27240 25152 ?        Ss   11:19   0:00 nxserver -c /usr/NX/bin/nxserver --login
nx        9177  0.4  0.2   5004  2184 ?        S    11:19   0:00 /usr/NX/bin/nxssh -nxservermode -l nx_admin localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o PubkeyAuthentication yes -o RSAAuthentication yes -o RhostsAuthentication no -o PasswordAuthentication no -o RhostsRSAAuthentication no -o StrictHostKeyChecking no /usr/NX/bin/nxnode
nx_admin  9183 10.7  1.2  12724 11424 ?        Ss   11:19   0:01 /usr/NX/bin/nxnode
nx_admin  9198  5.0  1.7  28148 16288 ?        S    11:19   0:00 /usr/NX/bin/nxagent -D -options /home/nx_admin/.nx/C-thedrake-1032-B5555EA28D992F929E50D7FB3F263C69/options -name NX - nx_admin@thedrake:1032 - Ubuntu @ Home :1032
nx        9204  0.0  1.6  27224 14732 ?        S    11:19   0:00 nxserver -c /usr/NX/bin/nxserver --login
nx        9205  0.1  0.1   5004  1596 ?        S    11:19   0:00 /usr/NX/bin/nxssh -B -E
nx_admin  9207  1.8  0.7  12864  7180 ?        S    11:19   0:00 /usr/NX/bin/nxnode
nx_admin  9208  0.6  0.6  13220  5764 ?        SN   11:19   0:00 /usr/NX/bin/nxagent -D -options /home/nx_admin/.nx/C-thedrake-1032-B5555EA28D992F929E50D7FB3F263C69/options AD-name NX - nx_admin@thedrake:1032 - Ubuntu @ Home :1032
dbott     9238  0.0  0.0   2876   792 pts/3    R+   11:19   0:00 grep NX

```

So, both services are running (ssh & nxserver).

-Dave

---

### Post by dbott67 on 2007-02-07
As a further aside into this, these are the steps that I performed in setting up NX and SSH:

For SSH:

1. Installed openssh server via Synaptic.
2. Configured and running on port 22
3. No other modifications

For NX:

1. Dowloaded the .DEB versions of NXserver, NX Client and NX Node from [www.nomachine.com](www.nomachine.com).
2. Installed the .DEBs in this order:
    - NX Node
    - NX Client
    - NX Server
3. Installed the NX Server following these instructions:
    - [http://www.nomachine.com/documents/server/install.html](http://www.nomachine.com/documents/server/install.html)
4. Configured the Nodes & added users following this document:
    - [http://www.nomachine.com/documentation/admin-guide.php](http://www.nomachine.com/documentation/admin-guide.php)

The one thing that I noticed is that it is better to create a new user account for NX rather than using my regular account.

-Dave

---

### Post by dbott67 on 2007-02-07
> **zetsumei said:**
> i get the following error after downloading/insalling cgywin and running putty

Gdk=ERROR **; X connection to localhost:10.0 broken (explicit kill or server shutdown).

how do i fix this?

A few questions for you:

Why are you using Cygwin?  Did you install it on a Windows machine?  Do you need to run an SSH server on Windows?  If so, you can install **sshwindows** from here:
[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/).

Otherwise, if you just want to access your Ubuntu box from another computer (Windows or Linux)

Here's what I do for SSH access:

**Ubuntu (as SSH server):**

1. Download & install openssh-server if you only want to run it as an SSH server
2. Download & install openssh-client and/or PuTTY for the client if you also want to be able to connect to other SSH servers

**For Windows (as client):**

1. Download and install PuTTY from here:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

-Dave

---

### Post by shookone on 2007-02-16
For X Server for Windows use Xming. Small and efficient. enable X11 tunneling in putty.. you are all set.

---

### Post by sean talbert on 2007-06-06
I had a similar problem where I was getting the error messages:

Xlib: connection to "localhost:10.0" refused by server
Xlib: PuTTY X11 proxy: wrong authentication protocol attempted
Error: Can't open display: localhost:10.0

Setup:

Ubuntu Server 7.04 and a Windows XP on different networks.

Ubuntu LAMP Server 7.04
Added the desktop:
     sudo apt-get update
     sudo apt-get install ubuntu-desktop
Installed OpenSSH Server:
     sudo apt-get install ssh openssh-server

Windows XP
Installed Xming 6.9.0.23 (Xming-6-9-0-23-setup.exe) from [http://sourceforge.net/projects/xming/](http://sourceforge.net/projects/xming/) 
Installed PuTTY (putty.exe) from [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)


Start Xming

Open putty.exe
     Entered the IP address for the Ubuntu server
     In Connection->SSH->X11 enabled X11 forwarding, entered the Windows XP IP address for the X display 
          location, and selected XDM-Authorization-1 for the remote X11 authentication protocol.
     Select Open and login

In the PuTTY terminal, I get the message: /usr/bin/X11/xauth:  /home/[user name]/.Xauthority not writable, changes will be ignored

I get this message when I login using the original administrator account (not root) created during the server installation. 

If I type xeyes (use X) into the PuTTY terminal, I get the 3 lines of error messages first listed, but the regular PuTTY commands do work, just not the X11 forwarding.

However, after I created a new user and logged in as that user, the PuTTY terminal does not list the .Xauthority error message, and xeyes works.

Why does the X11 forwarding not work with the original administrator account?

---

### Post by sean talbert on 2007-06-06
Figured it out... root owned /home/[user name]/.Xauthority

Logged in as root: chown [user name] /home/[user name]/.Xauthority

---

