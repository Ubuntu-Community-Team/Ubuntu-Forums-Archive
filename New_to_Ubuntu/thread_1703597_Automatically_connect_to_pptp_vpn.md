---
title: "Automatically connect to pptp vpn"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by binHEX on 2011-03-09
I have configured a pptp session to a windows vpn server, and when I call the vpn manually with this command:
pppd call winvpn

it works just fine.  I get a ppp0 adapter, I can access the vpn network, etc.

My problem is trying to figure out how to get this connection started automatically on bootup, without user interaction.
I have tried adding it to the interfaces file, I have tried settign up and creating a rc.local file (I added a echo xxx >> filename command after it to see if the file was running and it is) - but nothing I can figure out will get it to connect on startup.
Please help!  This is running on a console-only server, no GUI.

---

### Post by binHEX on 2011-03-09
Ok, this is how I finally got it to work.

I created a script
```
/scripts/vpnconnect
```

pasted the following into the script

```
#!/bin/bash
sleep 15
pppd call winvpn
```

I then set it to be executable

```
chmod 755 /scripts/vpnconnect
```

Then I added the following to my rc.local

```
/scripts/vpnconnect&
```

Now, the pptp tunnel gets created and connects every time the machine boots.  The key was the 15 second pause.  It gave the OS time to initialize whatever was not getting initialized before.

---

### Post by foxy123 on 2012-08-07
> **binHEX said:**
> I have configured a pptp session to a windows vpn server, and when I call the vpn manually with this command:
pppd call winvpn

How did you do that? I need pretty much the same thing, a simple pptp connection, which starts automatically on boot.

---

