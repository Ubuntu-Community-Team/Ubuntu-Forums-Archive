---
title: "[SOLVED] Wireless slow to re-connect after resume"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by th89 on 2008-11-01
When I resume my laptop from standby, my wireless is always slow to connect. It takes between 15 and 30 seconds after the laptop is totally resumed before it will connect. Im running Intrepid Ibex. Any ideas?

---

### Post by rhcm123 on 2008-11-01
In all honesty, wait. It takes several moments for the system to bring back up the network interfaces, broadcast for an ip, reccive an ip, configure it, etc.:popcorn:

---

### Post by th89 on 2008-11-01
I can accept a little wait. But it wont start to broadcast for 15-30 seconds. It will show up as wireless disconnected. After 30 seconds I can see it starting to broadcast for an IP. From standby to connected time is closer to probably 45 seconds or more.

---

### Post by rhcm123 on 2008-11-01
thats because it has yet to reinitiate the dameon process
meaning it has to close the old one from before the hold
then restart it and reconnect.

---

### Post by rhcm123 on 2008-11-01
If it's really a problem, then setup a static ip connection.

First, right click on the icon and hit "connection information."
Write down the following settings:
IP address (typically 192.168.X.XXX if you are on a home network)
Subnet Mask (typically 255.255.255.0)
Default Route (typically 192.168.X.X if you are on a home network)

Now,
Go to System -> Administration -> Network
Click on unlock and type your password to activate the console.

The list of interfaces should all say something like "Roaming mode enabled."
Now, hit the floppy disk icon in the corner and save the current configuration as "Away" (you don't have to, use whatever you want. Roaming mode is for if you are traveling)

Then, click on wireless connection. Select your network from the list, type the passkey, then set static ip config.

It should look somthing like this.

NETWORK: essid for your network.
Encryption: chose your encryption.
Passkey: set the passkey.
Network configuration: static ip
IP address: use the one you recorded earlier
Subnet mask: use the old one
Default gateway: called default route in the connection information tab.

Hit apply. wait for the "changing interface configuration" dioluge box to go away on it's own, then hit the floppy icon again. Save this configuration as home, then hit the green check mark. (the green check mark sets the selected configureation as the one used).

Now, this might not even increase the speed by a lot, and you may have connection issues. It's 45 seconds. It won't kill you. It's just the way the script works.:KS

---

### Post by th89 on 2008-11-01
Yeah, static is much faster, but for my network, its not feasible. It seemed very slow, compared to Hardy.

---

### Post by rhcm123 on 2008-11-01
It must be a bug. Perhaps you should report it to launchpad?

---

### Post by th89 on 2008-11-03
I ended up reformatting my laptop due to another issue, and it seems to connect in about 1/2 the time or less now. Not sure what was causing the slow connecting before.

---

