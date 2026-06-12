---
title: "Vinagre: &quot;connection to host was closed&quot;"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by rvs070 on 2008-09-23
I've set up x-win32 on my laptop to run programs from my ubuntu box in windows (XP). However, I'm finding that for some things having my entire ubuntu desktop available in windows would be most useful. Since I already have remote x set up, I thought I'd run a remote desktop within that framework.

I've enabled remote desktop for my ubuntu user, opened a remote terminal window on my laptop, and entered:

```
vinagre *ubuntu_machine_name*:0 
```

A vinagre window pops up, but it immediately gives me the message

```
connection to host *ubuntu_machine_name*:0 was closed
```

I've tried the same thing with 'localhost' instead of *ubuntu_machine_name*, but I get the same message.

Any idea what the problem is? If I'm using Vinagre incorrectly to start out with, can anyone recommend a different way to get my desktop with the setup I already have?

---

### Post by silvagroup on 2008-10-17
I too am having a similar problem except I get the error while trying to access a Ubuntu box from another Ubuntu box.

Have you been able to resolve your problem?

In searching the web all I have been able to find is something about a bug, but does not aoffer any solutions.

This is a real bummer because when I used KDE I had no problem with this it worked very well. But for some reason when I switched to Gnome I have been unable to get rdp to work.

---

### Post by olskar on 2008-10-19
I have got this problem too recently..

---

### Post by NHaGa on 2008-11-01
Same here using two intrepid machines. Any clues?

---

### Post by silvagroup on 2008-11-01
WOW same thing in Intrepid, that doesn't sound good.
I'll check some of the other distro forums and see if it's Ubuntu based or not.

---

### Post by 448191 on 2008-11-04
I had this same problem. Unchecking "Only allow local connections" 'fixed' it.

I assume access will be limited by the settings in hosts.allow and hosts.deny anyway?

Edit: just thought about something obvious: my router isn't letting port 5900 through anyway, so I'm pretty much safe on this one :P

---

### Post by silvagroup on 2008-11-04
Thanks 448191 that did the trick !!!!!!!

---

### Post by nickski on 2008-12-07
this did not help me...:confused:

EDIT: Nevermind, just realized you have to log out after the change...now it works yay

---

### Post by pizpot on 2008-12-17
Question, can I use vinagre to connect to my neighbor's computer when he takes it home? Right now it is sitting on the same router as me, and when I try to connect to 192.168.1.101 it says Connection to host "IP:5900" was closed.

What do I need to do to connect:
a) while on the same router
b) while in a different house (they don't have a router, and I know about IPs anyways)

PS: I find no "Only allow local connections" checkbox anywhere.

---

### Post by stefanadelbert on 2008-12-20
I was also getting the "Connection to host <hostname on port> was closed" error, but after logging out of and back into the host machine, everything worked as expected.
Very nice.

---

### Post by Weidbrewer on 2009-02-07
Unchecking the local connection box did not help me.  Still getting the connection closed message.   I can log in via the command line, but cannot connect to the desktop.  Both machines are running 8.10.

---

### Post by Sooty on 2009-02-11
sorry still cannot find the local connections only checkbox. Where is it?

Windows vista seems almost attractive sometimes! Hush my mouth!

---

### Post by Weidbrewer on 2009-02-11
You can get to the remote desktop admin, right?   (System => preferences => remote desktop.)

From there, click the advanced tab, and then select where the pointer is below.

[IMG]http://i166.photobucket.com/albums/u105/Weidbrewer/Screenshot.png[/IMG]

---

### Post by Weidbrewer on 2009-02-14
Now I'm having a new problem.  I've got the remote desktop working, but I noticed something when I logged in to the server directly (not remote) tonight:  My wallpaper is gone.  I can go in to the appearance settings and select different wallpapers, but none of them will display.

Again, this is not when logging in remotely (though, when I did, I had "disable the wallpaper" selected.)

---

### Post by DonMGard on 2009-03-08
I'm also having this problem.  Somehow I can't connect to my desktop remotely, even though I have set the DMZ on my router to pass all connections and have disabled the firewall in Ubuntu.  I've locked my PC and unchecked the "only local" box.  Does anyone have any idea what my problem could be.

The only thing I can think of is that I am in a different place trying to access my desktop.

Thanks, all.

---

### Post by zob on 2009-03-18
Hi.

I have a problem with Vinagre and VNC as well. I have a netbook (running cruncheee, based on ubuntu 8.10) and a desktop running ubuntu 8.10). I have installed vinagre, xtightvncviewer, tightvncserver, and more on both computers. I'm not using firewalls.

What I CAN do:
- On a local network I can log in with vinagre from my netbook to my desktop.
- From WAN (or crossing my router from the other end of town), I can log in to my desktop with vinagre (I havn't tried to log in to my netbook that way).

What I CANNOT do:
- On a local network I cannot log in with vinagre from my desktop to netbook (as I just mentioned, it works fine the other way).
- I have cannot access a friends computer (but I think it's his routers firewall, but I would like to be more sure, which I would be if it worked 100% on my local network, so actually trying to make it work locally is part of my troubleshooting).

It's really strange that it doesn't work on LAN (it doesn't even have to cross my router).

I get the same kind of error as people in this thread. Something like connection refused or closed - depending on the client I'm trying to use (they all fail).

I CAN however make ssh work - both ways, on LAN at least (still havn't been able to pass by my friends router). That ssh works, even running a whole x-session logging in from ubuntu/cruncheee's login screens, actually just make it even more weird that non of the VNC-based client/servers will work.

If anybody can help, I would appreciate it very much.

Thanks.

---

### Post by natrixnatrix89 on 2009-03-20
ehh :( I'm having the same problem between two intrepid ubuntu pc's. Restarting or unchecking anything doesn't help.. So it might be the fault of the router? is there an alternate port to use?

---

### Post by whatshisname on 2009-05-16
I, too, experienced many of the problems mentioned in this thread.

FWIW.  Logging out and back in didn't do it for me.  But restarting the computer did.

Either I was careless or didn't remember correctly but you should review your settings for setting up remote desktop when you boot back up.  It *seems* some of the settings had changed, notably "ask for confirmation" but I could be wrong.  I have changed a lot of settings this morning trying to get this puppy to work.  Happily it does now.

---

### Post by silvagroup on 2009-05-16
You can set up any port you want to use by assigning it in assign alternate port, check earlier screen shot posted to see where.

I had it all working great in Intrepid now that I am in Jaunty I can log in fine on my laptop and see my desktop pc and control it, except laptop doesn't refresh so I have no clue what is happing on the desktop pc.

Tried messing with all the settings on my Remote Desktop Settings on the desktop and doesn't make ant difference.
must be something local to the laptop.
But interesting just tried accessing my wifes desktop from the same laptop and it works fine, so must be something on my desktop settings.

Back to being a mushroom again.

---

### Post by johnaaronrose on 2009-07-08
On Jaunty, there is no 'Local Connections Only' checkbox and there is no Advanced tab. I want to 'remote' from a laptop to a netbook. Remote Desktop Viewer works OK when both laptop & netbook are connected to the same router. However, no success when the laptop is connected to a router linked to one ISP and netbook is connected to another router linked to another ISP i.e. true remote connection.

I've allowed port 5900 in both Ubuntu firewalls. First router is UPNP enabled and has Service on port 5900 with firewall rule for laptop LAN ip address. Second router is UPNP enabled. In Firewall Configuration (i.e. gui for gufw), I've allowed port 5900 incoming on laptop.

I've tried ipaddress::5900 with ipaddress as first router address & as second router address: both give window stating connection was closed..

Is it a problem with jaunty or what should I be using for Host in Remote Desktop Viewer?

---

### Post by sdaau on 2009-10-08
> **johnaaronrose said:**
> On Jaunty, there is no 'Local Connections Only' checkbox and there is no Advanced tab.

I experienced the same problem. Interestingly, I cannot connect with vinaigre even to another Ubuntu on the local network; however, I can connect from the same computer using xvncviewer (or tsclient) using the PC is 192.XX.XX.XX IP adress ?! Vinaigre fails with "connection closed" even if I use this very same IP address?

> **johnaaronrose said:**
> However, no success when the laptop is connected to a router linked to one ISP and netbook is connected to another router linked to another ISP i.e. true remote connection.

I've allowed port 5900 in both Ubuntu firewalls....

I've tried ipaddress::5900 with ipaddress as first router address & as second router address: both give window stating connection was closed..

Is it a problem with jaunty or what should I be using for Host in Remote Desktop Viewer?

Looks like you need to set up the receiving router, to forward port 5900 to the computer which runs the VNC server.

Cheers!

---

### Post by kingpioneer on 2012-01-18
Logging out and logging back in solved the problem for me.

---

