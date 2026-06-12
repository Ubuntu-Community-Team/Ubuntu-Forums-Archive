---
title: "Problem connecting to internet.  Can't find solution."
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by bobbert68 on 2008-08-02
I have been searching for a solution to my problem and cannot locate one.  I apologize if I overlooked one, but here is my dilemma:

I have running Ubuntu 8.04 and have no problem connecting to most wireless networks.  However, when I connect to a pay service that usually asks for your credit card information when you attempt to view any web page, I get an error that Firefox cannot locate server.

I have tried a couple solutions that included modifying the sysctl.conf file to turn off TCP Window Scaling and the etc/modprobe.d/aliases file to comment the ipv6 line.  Neither one worked.

Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-08-02
Have you tried multiple services (in different hotels, airports, et cetera) and get the same results each time?

The problem may have to do with your /etc/resolv.conf file, which Ubuntu looks at to figure out how to resolve domain names.  What are the contents of that file after you connect to the network?  It should mention a "nameserver"; if it doesn't, try adding in these lines:
```

nameserver 4.2.2.1
nameserver 151.197.0.38
nameserver 192.76.85.133
```

(actually sometimes that's all it takes to get Internet access from these services without registering or paying, if they're configured poorly and rely only on DNS redirection to force you to pay...although most of them now also filter MAC addresses, which is also pretty easy to get around, but we're not supposed to talk about overtly illegal things here :))

Also, are you sure that you're getting an IP address after you connect?  I've had these kinds of services do weird things; I've had times where it appears that I'm connected (according to Network Manager), but I don't really have an IP (according to ifconfig), and need to run:
```

sudo dhclient wlan0
```

to get an IP.  If you have the service available to test on, try these things and let us know if any of them seems to help.

---

### Post by cnich23 on 2008-08-03
Hey bobbert,  I am working with czee also and it has been a headache for me! I tried a few diffrent things and never was able to get it to work

[http://ubuntuforums.org/showthread.php?t=856508](http://ubuntuforums.org/showthread.php?t=856508)

tried a few different distros also with no luck, so i was forced to keep using windows,  but i am only stationed here for another month  so Ill be able to start using a wired connection then

---

### Post by bobbert68 on 2008-08-03
Thank you both.  I am assigned an IP and the resolv.conf file is working.  However, still no luck.

Cnich, I believe it is just a problem with CZee.  Let me know if you ever get anything working.  I'll do the same.

---

### Post by pytheas22 on 2008-08-03
I read through your thread cnich and am also thinking that maybe this has to do with the router rejecting you if it detects a non-Windows machine.  A way to trick it would be to install the[ Windows version of Firefox]("http://download.mozilla.org/?product=firefox-3.0.1&os=win&lang=en-US") and run it in wine (it works great)...that way, as far as the router can tell, you will appear to be running Windows.

Installing IE via ies4linux, as someone else in cnich's thread suggested, is the same idea, but it's harder to get IE installed offline because you have to hack a lot of stuff.  Firefox should "just work," though, and you can easily download the installer on another machine and transfer to Ubuntu if necessary.  You can also download the installer for wine from [http://packages.ubuntu.com](http://packages.ubuntu.com) if you don't have wine installed.

Another way to see how stuff is working would be to use some command-line tools.  First, see what happens when you try to resolve a website:
```

host google.com
```

Is it able to resolve?  It will probably just give you the IP of the router, but if it says anything, that's a good sign.

Also, what happens if you try to wget a site:
```

wget google.com
```

Is it able to download anything?

Finally, if you really wanted to get in on this, you could install Wireshark to figure out where exactly your packets are going.

By the way, what is CZee?  I sense that the military owns it but I'm not sure.  Is there anyone you could contact and ask about Linux support?

---

### Post by bobbert68 on 2008-08-07
I tried installing the windows version of FireFox through Wine and still had no luck with the connection.  Haven't tried contacting CZee yet.

---

