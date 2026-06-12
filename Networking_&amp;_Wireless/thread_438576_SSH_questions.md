---
title: "SSH questions"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2007-05-09
Hi, all. I've got some questions about SSH. I'm pretty new to Linux, but I'm learning at a respectable pace. I am rather ashamed to admit that I am quite ignorant as to the ways of networking, and this may be the source of some of my problems.

I have Feisty installed on a desktop machine that I use daily. Today I went and picked up a new Toshiba notebook. It came pre-installed with Vista, but I partitioned it off and installed Feisty as a dual-boot. It took some doing, but I got the wireless adapter working and can go online and all that jazz..

What I'm working towards here is being able to log into and control either machine from either machine. Ideally, I will then re-create my desktop environment on my new laptop. so it's like carrying my familiar desktop with me, and being able to acces my files and info, wherever I go. For now it's easy, because I'm sitting with my laptop right next to my desktop and the router is within arms reach; i.e., everything I need is right here and easily accessible. If I run into a problem and need to change a setting or something, I spin my chair and switch keyboards...

I have SSH server and client installed on both computers. I can acces either machine from either machine from the command line

```
$ ssh myname-desktop
```or
```
$ ssh myname-laptop
```I then have free access, through the command line, to anything anywhere in either computer. That works, but doing the things I want to do from the command line is quite tedious. 

I can't get the GUI to work at all. I keep getting "connection refused" messages from either side.

I have firestarter configured to allow SSH on port 22, and even specified the home network IP addresses, but I can't establish a connection through the GUI, only in a terminal window. I've read some how-to's and various posts in the forums, but I haven't been able to find any relevant info; most concern security and tweaking and whatnot.. which is fine, and will come in handy down the road, but I'd rather not start tweaking and fine tuning before I get the thing working right.

Like I said, I'm trying to replicate my desktop environment on my laptop, and would like to be able to access and control either computer from either computer in a remote-desktop kind of fashion.

So.. anybody have some ideas or know of a webpage that can point me in the direction I'm trying to go?

I'm not sure what info to include here, so if you need anything just give a shout and I'll be on it ASAP.

---

### Post by Epica on 2007-05-10
Hi detroit/zero
You can run GUI apps over SSH by typing their command names. Just make sure that the line

```
X11Forwarding yes
```

is in your sshd config file usually located at /etc/ssh/sshd_config and use the command

```
ssh -X yourusername@remotecomputershostname
```

-X enables X11 forwarding allowing you to run gui programs

If you want to have a complete desktop enviroment remotly controlled check out VNC or XDMCP.
Be sure to open ports 177, 6000-6015 and 16001 for XDMCP in firestarter and that should save you a few headaches :) 

Hope this helps.

---

### Post by detroit/zero on 2007-05-11
Well,  I've been messing with VNC, but I'm still unable to make a connection. I've cleared the specified ports and set all the passwords but for some reason I can't get authorization to make a connection.

SSH still works from a command line in either direction. VNC doesn't work at all. From Nautilus' Network Panel, the desktop will see the laptop and can acces any file anywhere in the computer (even if Vista is running...), so I know I have something right. But my notebook can't gain acces to my desktop except through an SSH command line.

I guess I need to read up on networking and permissions and whatnot.

Is there a program or a package available that I can use to sync my notebook to my desktop, or do I have to do it the old fashioned way?

---

### Post by detroit/zero on 2007-05-11
OK. With the help of a random type-o, I've discovered the error of my ways and am now able to use a remote desktop through VNC viewer. I was entering the command
```
$ vncviewer myname-desktop
```when I should have been entering
```
$ vncviewer myname-desktop:1
```I've been reading up on this, and clearly when following the instructions, this is the way to go. Before it would work, however, I had to set up separate user accounts on each computer named myname-laptop and myname-desktop, respectively. (the desktop account was on the laptop comp allowing me to control it from my desktop and vice versa.. you get the idea..) Oddly enough, I didn't have to whitelist any ports in Firestarter; traffic is flowing freely between the two computers. This seems a little dangerous for right now, but I'm reading up on how to secure everything and I'll get to it in due time.

Having said all that - By creating these user accounts, a new home folder has been set up in each system for access from the other computer. These users are "fresh" - default ubuntu human theme,  default settings, things like that.

Can anybody tell me how I might go about syncing up all these accounts across two different computers so it's like having one computer? Or, am I dreaming?

Thanks in advance for any help....

---

### Post by henrik_schmidt on 2007-05-12
> **detroit/zero said:**
> OK. With the help of a random type-o, I've discovered the error of my ways and am now able to use a remote desktop through VNC viewer. I was entering the command
```
$ vncviewer myname-desktop
```when I should have been entering
```
$ vncviewer myname-desktop:1
```I've been reading up on this, and clearly when following the instructions, this is the way to go. Before it would work, however, I had to set up separate user accounts on each computer named myname-laptop and myname-desktop, respectively. (the desktop account was on the laptop comp allowing me to control it from my desktop and vice versa.. you get the idea..) Oddly enough, I didn't have to whitelist any ports in Firestarter; traffic is flowing freely between the two computers. This seems a little dangerous for right now, but I'm reading up on how to secure everything and I'll get to it in due time.


I don't understand, why you had to do that. Anyway, there's another way... The below will allow you access to your desktop computer's display from your laptop, as if you were sitting in front of it (which apparently you are, but you get the idea ;) ). First of all, security is an issue here. Thats why you should check to see, whether the ports VNC uses are closed by the firewall. For this you need nmap. Install nmap on your laptop ```
sudo apt-get install nmap
``` From your laptop run the following command ```
nmap -P0 myname-desktop -p 5900
``` nmap should tell you that this port is closed or filtered depending on your firewall configuration, which makes sense since you don't have vncserver running. Try running the vncserver command on your desktop and run ```
nmap -P0 myname-desktop -p 5901
``` (note the portnumber is 5901 instead of 5900). nmap should still tell you the port is filtered or closed. If it's open, your firewall probably isn't running. This needs to be fixed before you continue. The below is assuming you have the firewall up and running or that you are on a secure local network. Go ahead and kill vncserver. ```
vncserver -kill :1
```

All right, let's install vncserver on your desktop if you haven't already. ```
sudo apt-get install vnc4server
``` Now we need to do some configuration. type ```
sudo gedit /etx/X11/xorg.conf
``` Edit the Module section first. Put ```
Load  "vnc"
``` at the bottom, so it looks similar to this:
```

Section "Module"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
        Load  "vnc"
EndSection

```

Now edit the Screen section. Put ```
Option  "SecurityTypes"  "None"
``` at the bottom like you did with the load command in the Module section. This will tell the vnc-module, that you dont want vnc to prompt you for a password when you connect. We'll let ssh and your firewall deal with security. Right then, time to restart myname-desktop. When your desktop machine comes back up, verify that port 5900 is still closed by running the nmap command from your laptop. If it's not, you've just given your entire LAN access to your desktop on mymane-desktop. If you're not behind a firewall or a NAT router, you've just given the entire internet access as well. That's sorta problematic. If this is the case remove the Load "vnc" line in xorg.conf and restart. Fix the security problems and try again.

Once you've verified, that your firewall is working and is blocking the port,  you're set to go. On your laptop run ```
 ssh -L5900:localhost:5900 myname-desktop
``` Open another terminal and type ```
vncviewer localhost
``` You should now connect to your desktop. If your firewall isn't running you can just type ```
vncviewer myname-desktop
``` and you will be connected directly, without using ssh. Note that you aren't prompted for a password. If that makes you uneasy (if you trust your firewall it shouldn't), have a look at this page: [http://www.realvnc.com/products/free/4.1/x0.html](http://www.realvnc.com/products/free/4.1/x0.html)

---

### Post by detroit/zero on 2007-05-12
I was with you right up until this point:

> When your desktop machine comes back up, verify that port 5900 is still closed by running the nmap command from your laptop. If it's not, you've just given your entire LAN access to your desktop on mymane-desktop. If you're not behind a firewall or a NAT router, you've just given the entire internet access as well. That's sorta problematic. If this is the case remove the Load "vnc" line in xorg.conf and restart. Fix the security problems and try again.

Once you've verified, that your firewall is working and is blocking the port,  you're set to go. On your laptop run ```
 ssh -L5900:localhost:5900 myname-desktop
``` Open another terminal and type ```
vncviewer localhost
``` You should now connect to your desktop. If your firewall isn't running you can just type ```
vncviewer myname-desktop
``` and you will be connected directly, without using ssh. Note that you aren't prompted for a password. If that makes you uneasy (if you trust your firewall it shouldn't), have a look at this page: [http://www.realvnc.com/products/free/4.1/x0.html](http://www.realvnc.com/products/free/4.1/x0.html)

[/QUOTE]

I made all the mods to both computers, as I'm going for a either/or situation. After restarting both computers, I verified that port 5900 was closed to the outside world. I had to whitelist the SSH connection (port 22) on both machines fof the following command

```
ssh -L5900:localhost:5900 myname-desktop
```

Fine so far....

```
vncviewer localhost
```

Holy crap! I ended up with a mirror-in-a-mirror situation... Check out the screenshot. Like I said.. I was with you right up until those last couple commands. I'm not sure what went wrong. 

I'll keep tinkering. Thanks for the help!

---

### Post by henrik_schmidt on 2007-05-12
> **detroit/zero said:**
> 
I made all the mods to both computers, as I'm going for a either/or situation. After restarting both computers, I verified that port 5900 was closed to the outside world. I had to whitelist the SSH connection (port 22) on both machines fof the following command

```
ssh -L5900:localhost:5900 myname-desktop
```

Fine so far....

```
vncviewer localhost
```

Holy crap! I ended up with a mirror-in-a-mirror situation... Check out the screenshot. Like I said.. I was with you right up until those last couple commands. I'm not sure what went wrong. 

I'll keep tinkering. Thanks for the help!

OK, I didn't see that coming, but it is easily fixed. I'm guessing you got some error messages, such as "bind: Address already in use" when you ran the ssh command. What you're doing here is creating a tunnel. It's an (fairly) easy way of going through a firewall for one port only. "ssh -L1234:myprotectedhost:5678 otherhostinsidefirewall" means: connect me to otherhostinsidefirewall and direct all traffic going to port 1234 of my laptop to port 5678 of myprotectedhost. Direct all traffic coming back from port 5678 of myprotected host to port 1234 of my laptop. You are essentially creating a tunnel between two ports - one inside a firewall and one on your local machine. The problem here is, that youi've installed VNCserver on both machines and both of them uses port 5900 to communicate. When you try to create a tunnel, the local port is already in use, and the tunnel is not created. When you start vncviewer it doesn't connect to your desktop but to your own laptop which results in the feedback image. What you need to do instead is to run ```
ssh -L5901:localhost:5900 myname-desktop
``` and to run ```
vncviewer localhost:1
``` Don't do this on both computers at once, though, or you'll create another feedback. OK, maybe just once for fun ;)

---

### Post by detroit/zero on 2007-05-13
Hi again. Actually, no - I didn't get any error messages when that feedback window came up, but I'm getting them after following your latest steps. I think I've got the jist of it all now, I'll just keep playing with the settings and it'll work out.

Now I'm off to work on some sound issues I'm having with the laptop..

Thanks for the help!

---

### Post by ryanVickers on 2007-05-23
I have a working ssh network that's quite nice.  It works, and it has a password, and that, but I was wondering if there is a way to choose which folders are allowed to be write to, read, or even if they show up?
Just to clarify, I don't really care about which users are allowed, everyone I guess, but it IS important that they (everyone) can only read/write/view certain files/folders.

I have been looking for an answer to this conundrum for quite some time now and have found nothing.  I guess most people just want full access with a password, but individual permissions is really important in my situation.

---

