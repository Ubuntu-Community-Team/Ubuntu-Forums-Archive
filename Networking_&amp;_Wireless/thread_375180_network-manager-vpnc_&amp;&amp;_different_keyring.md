---
title: "network-manager-vpnc &amp;&amp; different keyring"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by SgtPepperKSU on 2007-03-03
I've set up network manager to connect to my work VPN and it works great.  The only thing I'd like to change is what keyring it stores the password and group password in.  I haven't been able to find a way to do this.  Is there some .conf file I need to change?

---

### Post by teaker1s on 2007-03-03
gnome-keyring is installed you need to terminal
```
apt-get install gnome-keyring-manager
```
when installed
```
 killall gnome-panel
```

system>administration>keyring manager

---

### Post by SgtPepperKSU on 2007-03-03
I guess I didn't give enough details.  I have gnome-keyring-manager installed, and I have created the keyring I'd like to use.  But how can I get network manager to use it?

---

### Post by teaker1s on 2007-03-03
I miss understood, I don't know the answer but keyring manager appears to allow asociation  with application
s or in terminal have you tried for a manual
```
man gnome-keyring-manager
man-keyring-manager
```

---

### Post by SgtPepperKSU on 2007-03-03
> **teaker1s said:**
> have you tried for a manual

All the man entry says is 
> home-keyring-manager is a graphical key management tool for GNOME. GNOME keyring manager allows the user to create, delete, and otherwise manipulate keys and keyrings which can be used to store passwords.
Then under the options section, it says "These aren't right, yet" and has options that look like they belong with a packaging tool.
Not overly useful.

I have tried clicking, right-clicking, and every menu item (not many) everything thing I can see, but all I can manage to do is create a new keyring, and modify/delete existing keys.

---

### Post by teaker1s on 2007-03-03
forgive me if i'm wrong but here is my debian gnome keyring manager

---

### Post by SgtPepperKSU on 2007-03-04
Yes, that's what mine looks like, too.  If you goto View->Keyrings, you can see all of your keyrings, and File->New Keyring, you can create new ones.  And, like I said, I can modify existing keys.  But, I can't create new keys there (or I could create a key in my new keyring and add nm-vpnc-auth-dialog to the applications) or move existing keys between keyrings.  Even if I could, I'm not sure Network Manager would look in the new keyring.

After some more research, I've noticed other programs have a --keyring command line option (or similar) to direct them to a different keyring.  But, that didn't work with nm-applet, and the there is not meaningful documentation that I can find to check for a different option.

---

