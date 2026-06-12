---
title: "No luck compiling network-manager"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by evil_elman on 2006-07-17
Hello everybody...

I just tried SUSELinux 10.1 and was quite impressed by the network-manager app it had. The most stable of its kind I've seen so far... So, back to Ubuntu to try it out.

I found the sources and thought I might give compiling it a shot. By following the excellent instructions provided I ran the following command 
```
./configure
```
and I get the following output (amongst other things that are OK):
```
configure: error: wireless-tools >= 28pre9 not installed or not functional 
```

When looking in Synaptics I can find the following package installed: 
```
wireless-tools version 27+28pre13-1ubuntu2
```

Why is this package not doing the trick? Do I need to replace it with some other generic package not specifically made for Ubuntu?

Maybe one of these will work? [http://packages.debian.org/changelogs/pool/main/w/wireless-tools/wireless-tools_28-1/changelog](http://packages.debian.org/changelogs/pool/main/w/wireless-tools/wireless-tools_28-1/changelog)

---

### Post by Fass on 2006-07-17
[http://packages.ubuntu.com/dapper/net/network-manager-gnome](http://packages.ubuntu.com/dapper/net/network-manager-gnome)

You don't need to compile network-manager. It's in the repositories.

---

### Post by evil_elman on 2006-07-17
Damn... Totally missed that one...

*Opening Synaptics*

Thanks!

---

### Post by Fass on 2006-07-17
[http://www.ubuntuforums.org/showthread.php?t=179643](http://www.ubuntuforums.org/showthread.php?t=179643)

That thread may help you get it running if you haven't before, or it doesn't work for you out of the box.

---

### Post by evil_elman on 2006-07-17
Worked right 'out-of-the-box'. Just needed a reboot and some settings in the regular Networking app. Done in two minutes.

I think I'm the happiest Ubuntu user ever now! :D 

Now... If I could only get decent 2D performance in Gnome as well... :-k

---

