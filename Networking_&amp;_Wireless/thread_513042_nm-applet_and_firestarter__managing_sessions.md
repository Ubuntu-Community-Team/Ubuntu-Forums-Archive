---
title: "nm-applet and firestarter / managing sessions"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by nimajiman on 2007-07-30
I am running Ubuntu Feisty and have network manager set up to connect to my wireless router automatically on login. I have also added firestarter to my list of startup programs. The problem is that Firestarter is loaded before network manager has a chance to connect to my router, so i get the  "device eth0 is not ready" error message each time i log in. I then have to click ok, go to firestarter once network manager does its thing, and tell it to start. Not a big deal i know, but i would like Firestarter to wait until nm-applet has loaded and connected to my router before it loads.

I went into sessions and tried changing the order of nm-applet to 40 (from 50) and/or firestarter to 60 (from 50), but all that happens is my splash screen hangs for ages when i log in - it eventually disappears and all is normal, but not sure what i'm doing wrong or how to make it start network manager first before firestarter loads.

Any ideas?

---

### Post by vmlinuz on 2007-08-05
Hi. I had almost the same problem as you; if you want firestarter to set up your firewall (iptables) at computer startup, edit the file /etc/firestarter/firestarter.sh. 

Find these lines:
[FONT="Courier New"]
if [ "$MASK" = "" -a "$1" != "stop" ]; then
       echo "External network device $IF is not ready. Aborting.."
       exit 2
fi

if [ "$NAT" = "on" ]; then
       if [ "$INMASK" = "" -a "$1" != "stop" ]; then
               echo "Internal network device $INIF is not ready. Aborting.."
               exit 3
       fi
fi[/FONT]

Now, comment them out (by adding a "#" in front of each line), like so:
[FONT="Courier New"]
#if [ "$MASK" = "" -a "$1" != "stop" ]; then
#       echo "External network device $IF is not ready. Aborting.."
#       exit 2
#fi
#
#if [ "$NAT" = "on" ]; then
#       if [ "$INMASK" = "" -a "$1" != "stop" ]; then
#               echo "Internal network device $INIF is not ready. Aborting.."
#               exit 3
#       fi
#fi[/FONT]


It worked just fine for my desktop computer, as it takes some time to set up a connection with the modem. Iptables doesn't seem to care whether a network interface (like eth0) is actually connected to something, so why would firestarter do? I'll submit a bug report about this as soon as I'll have the time to. (Sorry for my english)

---

### Post by nimajiman on 2007-08-20
Thanks, I finally got around to trying this out, and it worked great. Now firestarter starts by itself when I boot, which is exactly what I wanted to save the annoying-ness of pressing start everytime.

Thanks again!

---

