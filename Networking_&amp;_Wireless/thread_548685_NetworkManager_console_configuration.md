---
title: "NetworkManager console configuration"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by patsissons on 2007-09-11
I am currently using feisty on a very scaled down X setup (runs on an IBM thinkpad 390e with a p2 @ 300MHz and 64M ram).  I run a customized window manager that uses only 1M of resident memory (and not much more non-resident memory).  Running a WM like gnome, kde, or even xfce is out of the question, the laptop would simply be unresponsive.

Anyways, I was thinking of writing my own script for auto network configuration based on the available wifi AP's and a configuration file, then I stumbled upon NetworkManager.  From what I can tell, NetworkManager does just this, however, it only seems to be useable from kde or gnome.  I can't find any documentation on how to set it up without the kde or gnome applets.

So now I am curious, does there exist a program that allows configuration of NetworkManager from the console.  If not, is this something that is possible to create?  Can you configure NetworkManager simply by editing configuration files?  If a program must be created, can NetworkManager be controlled by a script (or scripts)?

Thanks to anyone who can shed some light on these questions.

---

### Post by reckless2k2 on 2007-09-11
ahhhh...everything in linux is a script. haha..you can create a bash script to do just about anything. you'll have to look into it a little because i'm a little out of date on the correct script language you'd need but you'll be using:

ifup, ipdown, iwscan or lwlist (can't remember which one) and setting the iwconfig based on the network found in the scan. i use to do this with 5.10 on kde and it's been some time since i had to have to do that. bash script can be done easy yourself with the parameter's and if statements. i grabbed a sxript like this and modded it for me then. i think it's a debian script out there.

sorry...just pointing in directions.

---

### Post by patsissons on 2007-09-12
Actually, I was looking for a way to confure the DBus system, but after some research I discovered that kdenetworkmanager and the gnome network manager applet handle their own configuration and then just send the appropriate messages over the DBus.

Originally I was going to just write a script that would invoke ifconfig, route, and edit the resolv.conf file.  Then once i started to look into DBus i found that you can send DBus messages with the dbus-send command.  Unfortunately, you can only send messages, not listen for signals (which would be very important for an auto network configuration tool).  So a script that just invoked dbus-send was out of the question.

I have since decided to take it upon myself to spear head the development of the first console based library for accessing NM over the DBus.  The library is written in Ruby and has progressed rather well so far (still tons of code left to write).  I will be updating [http://dhx.ath.cx/wordpress/ruby-networkmanager/](http://dhx.ath.cx/wordpress/ruby-networkmanager/) as I continue along.

Even if you aren't interested in the library I am creating, you may be interested in the work I have done to decypher the NM DBus specs.  Everything I discover is documented in a comment block in the code.

---

