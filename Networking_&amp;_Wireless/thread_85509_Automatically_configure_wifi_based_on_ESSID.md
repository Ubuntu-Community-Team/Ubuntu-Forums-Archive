---
title: "Automatically configure wifi based on ESSID"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by BlueNoteMKVI on 2005-11-02
My laptop goes with me to lots of places where I have wifi access, and most of the time I want to just let DHCP assign my IP address and I'll go from there.  When I'm home, however, I want to assign a static IP address so that my backup scripts can run each night.  I have an idea of how to do this, and I think I could program it in PHP...but I'm not much good with shell scripts.  Hopefully someone can help me out.

Here's the basic idea, in psuedo-code:

```
//get list of available APs
$available_aps=iwlist eth1 scan
//look for my home AP
if somewhere_in_list('$available_aps, 'myessid'){
  //configure static IP
}else{
  //proceed with DHCP
}
```

Is this doable?  I don't mind putting all of that into a script by hand once, but I don't want to mess with the command line every time I boot my computer in a new place.

---

### Post by redactech on 2005-11-02
I have similar case

almost everywhere I go I have dynamic IP but at one place so I'm using

[http://sourceforge.net/projects/gtkwifi](http://sourceforge.net/projects/gtkwifi)

Basically my laptop is configure on static IP and wherever else I go I run gtkwifi it will remember the wep keys and so on... it is pretty good.. you can also run it not as an applet but in a separate window (in case you're not using gnome or kde) by 

```
gtkwifi run-in-window
```

---

### Post by BlueNoteMKVI on 2005-11-02
I saw that, and a similar utility called "netgo" for KDE.  I installed netgo, but unless I run the program as root it can't do anything because it needs access to the iwconfig commands.  Can gtkwifi handle changing configurations on the fly without entering a password?

---

### Post by redactech on 2005-11-03
never try roaming per se but since I'm using it I forgot all the passphrases...

so yes it does automagically connect ...

---

