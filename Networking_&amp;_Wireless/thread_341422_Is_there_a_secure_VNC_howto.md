---
title: "Is there a secure VNC howto?"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by josesanders on 2007-01-18
I want to access the desktop on my Edgy machine at home through my Windows machine at work.  I use ssh now, but I want to see the whole desktop, not just the command line.  I tried to set up vnc, but the only guide I could find seems to be for an older version of Ubuntu, and some of the instructions are not applicable.  I've read that vnc itself is not secure, but it can be if you use it with ssh somehow.

Is there a vnc howto for edgy, and if so, is there a howto to use it securely with ssh?

Thanks

---

### Post by chipdip on 2007-01-18
Thats a good idea, I wanted to do something like that also.

---

### Post by josesanders on 2007-01-20
bump

---

### Post by grumpymole on 2007-01-21
I'll write up a proper how-to in a few hours.

Howevere, if you already have an existing remote desktop working and you want to scure it, it's quite easy using putty.  The principle behind this is to create an SSH tunnel between the two machines.  Then, instead of connecting to the remote machine directly, you "connect" to the endpoint of the tunnel on your local machine.  

For  example, if you are connecting to qwerty.com:5901 for a remote desktop:
1.  In putty, specify a SSH connection to qwery.com  (leave port 22).
2.  Go  to the Tunnels section under SSH (lower down the tree on the left-hand-side).
3.  Source port: 5901, Destination: localhost:5901, click Add.  It should add an entry that says "L5901     localhost:5901".  This means that the  tunnel will be between the local (Windows) port 5901 and port 5901 on the remote machine.
4.  Go back to Session and select Open to connect.
5.  You get a window to sign in  as usual.
6.  To check that the tunnel is up, right-click on the titlebar and choose Event Log.  Look through the window content and you should see som information about the tunnel.

Now, connect to your Ubuntu box using tightvnc (or whichever viewer you choose), but instead of connecting to qwerty.com:5901, now connect to localhost:1.  This will connect to port 5901 on the Windows machine (the machine you are connecting from), which is being listened to by putty and forwarded through the tunnel to the remote machine.  

As I  said, I'll right up  a proper how-to with some screen shots in a few hours.  There is a how-to for remote desktop without the secure bit on my blog.  I use this every day to connect to my home PC from the  corporate LAN.

If you want to pm me, I use a gmail account with the name grumpymole.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by morphet on 2007-01-21
This might not be exactly what you are lloking for, but it might offer some insight.

[http://lifehacker.com/software/vnc/geek-to-live--secure-vnc-with-hamachi-228862.php](http://lifehacker.com/software/vnc/geek-to-live--secure-vnc-with-hamachi-228862.php)

---

### Post by josesanders on 2007-01-22
GrumpyMole - thanks, that's pretty much what I'm looking for.  I haven't yet figured out how to get the VNC server installed properly because the only howto that I found wasn't for Edgy, so a lot of the instructions didn't make sense.  I can probably figure that out eventually, but of course, I would very much appreciate a howto if you are up to it.

Thanks

---

### Post by josesanders on 2007-01-23
I fixed my problems, so to summarize, here are the steps (I'm just repeating from several different threads):

following the initial Howto:

```
$ sudo apt-get install vnc4server xinetd
```

NOTE:
I've seen that there is a bug in the latest version, so if you run into problems, you might want to try using the older version of vnc4server.  Instead of the previous command, run

```
$ sudo apt-get install vnc4server/edgy xinetd

```
Then:
```
$ sudo vncpasswd /root/.vncpasswd
$ sudo gedit /etc/xinetd.d/Xvnc
```

Add the following text to the new file
```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd
        port = 5901
}
```

Then restart xinetd
```
$ sudo /etc/init.d/xinetd stop
$ sudo killall Xvnc
$ sudo /etc/init.d/xinetd start
```

This is where my setup differs from the howto:
Fix the font problem:
```
$ cd /usr/share/X11
$ sudo ln -s /usr/share/fonts/X11 fonts
```

Login locally to the server and change the settings under:
Administration->Login Window
Under the remote tab, set it to be the same as local

Then on the remote Windows machine, download Putty and tightVNC.  Start the ssh session as described above by GrumpyMole, and then open tightVNC viewer and connect to the local host.

I know this is just repeating what is already out there, but I had to sift through 25 pages in the original thread to get it to work, so I thought it would be nice to have a concise summary for future reference.

---

### Post by merker19 on 2007-01-30
Hi-
It works which is great, but vnc server on my Ubuntu box is listening on 0 instead of 1, even though I have the correct line in my Xvnc file:

port = 5901

Any suggestions?
Thanks,
merker19

---

### Post by darkcyber on 2007-02-05
Thanks for this thread...working on getting vnc viewer working on my ubuntu pc and this is great information. :KS

---

