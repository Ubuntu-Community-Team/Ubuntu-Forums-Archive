---
title: "Send magic packet at startup?"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by mikkel3 on 2014-02-08
Hello Users

I have searched , google'd , etc. but can not find the help I need when I " never " have touched ubuntu / linux before. so I need a step by step guide on this one.

I installed xubuntu , installed XBMC and got it to start up automatically so far so good .

I have my server set up ( FreeNAS ) and it is ready for WOL ( I can  start it with magic packet from my windows machine, so IPs mac etc , I  have this . )

So what I need now is when I start my xubuntu / xbmc machine, that  also sends a magic packet to my FreeNAS server.

I  have looked at " wakeuplan " " ethtool " "power wake " " etherwake "  but cant find the guide i need , having found and understand some part  about the local startup file , but there are Soooooo many post and  threads out there , so it is more confusing than helpful, for a beginner like me ....

hope  there is someone who can help me with this "simple " command : D what I  said, I need a little step by step , the terminal is ready , what's the  next step? Sudo get ......

Big thx .

---

### Post by tgalati4 on 2014-02-08
Put:

```
wakeonlan 00:00:00:00:00:00
```

in a startup file, like /etc/rc.local.  Put it before the *exit 0* line.

Make sure you have the correct MAC address for your freenas machine and substitute it for the 00:00:00:00:00:00 above.

---

### Post by TheFu on 2014-02-08
I use a [perl script]("http://www.han.de/~gero/netboot/archive/msg02524.html") - **wake.pl**  I've put this script in /usr/local/bin/ and changed the permissions to be *executable*. Perl is already installed on almost every Linux system.

Then I've written a tiny shell script for every system on the LAN that I'd like to send WOL packets at. Here is that script with the MAC address for a box here. The script filename is "xbmc-wol.sh" - so I don't have to think too much.
```
#!/bin/sh
/usr/local/bin/wake.pl 00:99:8c:51:d8:e6
```
You could put this into the xbmc startup script with a 5 second sleep.
```
#!/bin/sh
/usr/local/bin/wake.pl 00:99:8c:51:d8:e6
sleep 5
/usr/bin/xbmc &
```

Simple.

---

### Post by tgalati4 on 2014-02-09
My wake scripts are cheesy:

```
#!/bin/sh
# Super cheesy script to wake my server and put up a notification to that effect
#
/usr/bin/wakeonlan 00:19:d1:fa:0b:90
sleep 3
/usr/bin/wakeonlan 00:19:d1:fa:0b:90
sleep 3
/usr/bin/wakeonlan 00:19:d1:fa:0b:90 
sleep 2
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "Zalman PC is waking up"  "You'll be up in a few seconds."
sleep 10
notify-send --icon=/home/tgalati4/Projects/scripts/server.svg "Zalman PC is alive." "It's services are now available."
echo "The current time is:"
DISPLAY=:0.0; notify-send -i clock "$(date +"%H:%M")"
exit 0

```

But they get the job done.  I have a desktop launcher on each machine that calls this script.

---

### Post by TheFu on 2014-02-09
> **tgalati4 said:**
> My wake scripts are cheesy:

But they get the job done.  I have a desktop launcher on each machine that calls this script.

I'm convinced!  Plan to switch over soon, though I'll probably leave out the notify.

---

### Post by tgalati4 on 2014-02-09
I adjust the notify time since I have several machines and some of them take much longer to wake than others.  I use a triple wake command because sometimes the wake packets are not caught when going through several switches with heavy streaming traffic.  Like I said, cheesy.

---

### Post by Lars Noodén on 2014-02-09
If the machines take a while you could look with a ping to keep checking until the machine is up.

---

