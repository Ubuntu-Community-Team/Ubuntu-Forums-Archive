---
title: "Network manager Openconnect plugin doesn't work in 16.04LTS"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by oleg-secondary on 2016-04-21
Hi

After upgrade to 16.04 I have a little problem with openconnect plugin for NetworkManager: it doesn't work. NM just ignores it: no Openconnect in the new connection dialog.
And syslog contains this line: 
```

gnome-session[1897]: ** Message: vpn: (openconnect,/etc/NetworkManager/VPN/nm-openconnect-service.name) cannot load      legacy-only plugin
```

Any ideas?

---

### Post by daoswald on 2016-04-21
I can confirm. Cannot connect (same message), cannot add a new openconnect VPN entry (no openconnect in the add dropdown), and cannot edit existing: "Could not find VPN plugin service for 'org.freedesktop.NetworkManager.openconnect'."

I've run apt install --reinstall for all openconnect-related packages on my system, and rebooted without achieving further progress.

---

### Post by hdibani on 2016-04-22
same here, for now, using openconnect from the command line, no openconnect option under the VPN list.

---

### Post by oleg-secondary on 2016-04-22
Found this thread [https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/1571300](https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/1571300)

Short version: you can build newest network-manager-openconnect yourself as a temporary workaround

---

### Post by couloir0072 on 2016-04-28
I can log in via command line, but not network manager. I did the temporary workaround, got it installed, openconnect shows up, but I'm getting "no valid vpn secrets". Any suggestions would be great.

Thanks!

---

### Post by felgro on 2016-04-28
> **couloir0072 said:**
> I can log in via command line, but not network manager. I did the temporary workaround, got it installed, openconnect shows up, but I'm getting "no valid vpn secrets". Any suggestions would be great.

Thanks!

Who is your VPN provider?

---

### Post by erikspencerwilliams on 2016-04-28
FWIW: If you have access to a saved OpenConnect NetworkManager profile from before 16.04 (I had one on a 14.04 box) you can drop it in to /etc/NetworkManager/system-connections and use it as before.

You won't be able to edit it or create new OpenConnect profiles via the plugin but for anyone (like me) that just wants a cheap workaround this worked well.

---

### Post by sun0s on 2016-08-01
> **couloir0072 said:**
> I can log in via command line, but not network manager. I did the temporary workaround, got it installed, openconnect shows up, but I'm getting "no valid vpn secrets". Any suggestions would be great.

Thanks!

Got the same on fresh 16.4 connecting to corporate Cisco Anyconnect VPN via openconnect - works from cli, fails from network-manager applet with same. The connection involves CSD script run, then RSA SecurID dialog pops up. When connecting from applet, it fails right during entering credentials. 
In the NM logs:
Failed to request VPN secrets #3: No agents were available for this request.

---

