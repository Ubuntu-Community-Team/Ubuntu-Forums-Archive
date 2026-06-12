---
title: "Ubuntu server"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by il pepe on 2010-11-06
I have an old computer standing in my office, and i had the idea to make it a small office server (mainly file server). I would like to acces the 'server' with two laptop's (one ubuntu, one windows)

So i started out installing ubuntu server.

But now i'm pretty much stuck.
I thought samba would be the main solution for my requirements. so i started to change the data in the smb.conf file, like in [https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")
but i'm not able to restart samba...

Any solutions?

---

### Post by HermanAB on 2010-11-06
Howdy,

If it is a regular machine with screen, keyboard and mouse, then you should install regular Ubuntu on it.  Working without a GUI is just a pain in the derrier.

Unlike the older Linux distros (Fedora, Suse and Mandriva) which have wizards for everything, Ubuntu doesn't have many wizards yet.  So if you want to install Samba, then your best best is to install Webmin and configure things via a web browser.

---

### Post by ikt on 2010-11-06
> **HermanAB said:**
> Working without a GUI is just a pain in the derrier.

If you're new to linux then working with a GUI initially may help speed things along, however learning to use the cli is best for working with the server long term, however if all your going to do is basic file sharing I don't see why ubuntu desktop edition couldn't be used, there'd just be slightly more updates than the server version.

---

### Post by sikander3786 on 2010-11-06
> but i'm not able to restart samba...

What was the error returned?

Which version of Ubuntu did you install?

The link you referrer to is pretty old. Samba now runs as service in Ubuntu so try

```
sudo service smbd start
```

&

```
sudo service nmbd start
```

As already suggested in above posts, if you are new to Linux, it would be better to install Ubuntu Desktop as Ubuntu Server is actually Ubuntu Desktop just without a GUI. You'll be able to run all your server apps just like the Server Edition on Ubuntu Desktop as well.

---

### Post by il pepe on 2010-11-06
i'm not that new to linux, but i'm a noob in setting up a server.

The pc now has a screen, keyboard and stuff, but i would like to remove those in the long term.
Second, we're talking about a older pc, which can run a gui, but i would rather not, to keep enough resources free for just the file sharing/printer sharing.

Anyway, you guys would recommend installing regular ubuntu, setting the whole thing up, and then remove the gui?

btw: i installed ubuntu server 10.04 LTS. installed as lamp and samba server.

---

### Post by sikander3786 on 2010-11-07
> Anyway, you guys would recommend installing regular ubuntu, setting the whole thing up, and then remove the gui?

I don't think if that will be of much help. If you want a headless server, webmin is the way to go.

[http://www.webmin.com/](http://www.webmin.com/)

> i installed ubuntu server 10.04 LTS. installed as lamp and samba server.

The link you posted had the instruction for init.d script. Did you try starting samba as a service as mentioned in my previous post?

---

### Post by Gone fishing on 2010-11-07
If you want a gui for the server you could install one sudo ```
apt-get install xubuntu-desktop
``` (bit lighter than gnome) handy for using the browser to look at howtos and copy and pasting from the browser.

Once you've got the server as you want you don't need to run the gui.

A second for Webmin [http://www.webmin.com/download.html](http://www.webmin.com/download.html) you can now install using a deb.

---

### Post by v1ad on 2010-11-07
hmm i prefer the CLI way. don't need an extra screen keyboard mouse or anything. just ssh into it.

also i used webmin b4 also, it's pretty neat.

---

### Post by il pepe on 2010-11-07
> **v1ad said:**
> hmm i prefer the CLI way. don't need an extra screen keyboard mouse or anything. just ssh into it.

also i used webmin b4 also, it's pretty neat.

Seems i'm too rookie for ssh. Couldn't get it working :s

---

### Post by il pepe on 2010-11-07
i installed webmin.
Now how do i get in? tried with w3m [https://server-ip:10000/](https://server-ip:10000/)
but replies: can't load https....

?

---

### Post by CharlesA on 2010-11-07
Is it listening on port 10000 ?

Are you have any firewall in place?

Run these please:

```
netstat -ln
```

```
sudo iptables -L
```

---

### Post by il pepe on 2010-11-07
Good remark! :D

I tried netstat:
the server doesn't seem to be listening to port 10000

iptables are all set to accept (so no firewall active, is supose).

So the server isn't listening... How can i resolve this?
Or should i just take a port which the server is listening to?

---

### Post by CharlesA on 2010-11-07
Try doing a reboot, unless webmin threw up errors during install it should have started automatically.

If it's still not listening after a reboot, how did you try to install webmin?

---

### Post by il pepe on 2010-11-07
still the same.

I downloaded .deb file and just ran it...

---

### Post by CharlesA on 2010-11-07
If you just downloaded the deb and tried to install it with dpkg, it would have unresolved dependencies.

Run this:

```
sudo apt-get install -f
```

After that's done, webmin should be listening.

---

### Post by il pepe on 2010-11-07
yup that did the trick.
The only problem now is that w3m isn't really the best browser to show webmin... So i'm now looking to install a browser, without installing to much...

---

### Post by CharlesA on 2010-11-07
Use another machine on the same network to access the webmin interface.

That's the whole point of using a web interface.

---

### Post by il pepe on 2010-11-07
Okay that worked. so i can start configurating the whole server.

The only question i have, is a very dumb one: if i share files and i use the ip adress, will the system automatically use the LAN or will transfer go over the internet? is suppose the first, but is there a way to check this?

The configuration now is a hub connected to the server. to this hub there is wireless router connected, on which the laptop is wireless connected...

---

### Post by CharlesA on 2010-11-07
It'll only share to the local network.

---

### Post by HermanAB on 2010-11-07
Note that you need not uninstall the GUI to conserve resources.  Just stop and start X manually as needed.  Having Gnome and other GUI apps installed, allows you to SSH into the box and run for example gedit to remotely edit a file with a nice editor, without actually running X on the server:

$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or even
$ ssh -X -C -c blowfish user@server gnome-panel
and go click happy.

---

