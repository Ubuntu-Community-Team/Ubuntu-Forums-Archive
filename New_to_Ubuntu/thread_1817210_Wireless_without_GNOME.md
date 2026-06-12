---
title: "Wireless without GNOME?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by pmooney78 on 2011-08-03
I've been playing with switching window managers. I really like OpenBox, especially for the speed boost, but there's a deal-breaker: I only have wireless internet service, and I can't figure out how to connect to my own wireless router without the GNOME network manager applet. I've tried just starting gnome-panel from a terminal, and it runs, but the network manager applet doesn't appear. I can't figure out any other way to connect.

I've tried running nm-tool from a terminal, and it reports on available networks, but doesn't seem to give me any options for connecting to anything. I'm currently dual-booting Ubuntu 10.04 and Linux Mint Julia (based on Ubuntu 10.10), and having the exact same problem with both.

Not being able to use wireless networking is a deal-breaker on a window manager for me. I've googled this, but can't find anything that makes sense to me. There's a lot of results, but they all seem to assume that I know a lot more than I do about how wireless works. 

My preference would be to have something that replicates the functionality of the GNOME panel as much as possible, but I'll take what I can get. Any help is much appreciated.

---

### Post by josephmills on 2011-08-03
Hi there don't know if this will help but have you looked into wicd or wifi radar ? Like I said I dont know if that will help or not.

---

### Post by sadaruwan12 on 2011-08-03
Well, as far as I know the network manager applet is a small peace of software what you get when you install a complete WM like GNOME which is more of a beast compared to OB.

So even in GNOME if you don't like the Network Manager applet you can replace it with something you like.

For me the first thing pop's into my mind is WICD which is little bit more advanced than the GNOME one and you can configure it to do what you want.

You can follow this to install and configure WICD [Click Here]("http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html") To go there.

---

### Post by Gone fishing on 2011-08-03
Or possibly you could do it the way it used to be done before the manager applet by modifying the /etc/network/interfaces file?

---

### Post by Wim Sturkenboom on 2011-08-03
Maybe [http://ubuntuforums.org/showpost.php?p=10930324&postcount=7](http://ubuntuforums.org/showpost.php?p=10930324&postcount=7) helps; connect using command line. You can wrap it in a script that accepts a *start* and a *stop* argument and add it to some menu

---

### Post by pmooney78 on 2011-08-03
Thanks! Wicd looks like it'll do what I need. Next time I reboot, I'll try it under OpenBox.

---

