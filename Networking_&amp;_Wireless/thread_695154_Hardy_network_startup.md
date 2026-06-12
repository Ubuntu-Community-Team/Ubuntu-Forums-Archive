---
title: "Hardy network startup"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by drdabbles on 2008-02-12
I have installed Hardy on my work PC, and configured it to authenticate against our Windows AD. This works fantastically, so long as the network starts BEFORE samba and winbind. As it is now, I have a manually specified IP address, but the network interface does not become active until after I log into an X session. Obviously, because the username and password are from a network source, I can't successfully do this.

My workaround for now is to log in as the user I created at install time, start the network, restart samba and winbind, log out, switch back to my GDM login, and finally log into the machine as my network user. Is there a way to make my network interfaces come up before X, so I can actually authenticate? I suspect this is a problem for anyone else attempting to log in this way, unless I can cache the credentials on my PC until a login is successful, but then you risk having an incorrect password.

Any help would be greatly appreciated!

---

### Post by drdabbles on 2008-02-12
Ah, right. So, I thought I had added "auto eth0" in my network/interfaces file. Turns out I'm that jerk today. Sorry, all!

---

### Post by drdabbles on 2008-02-14
Okay, so, now that I've added auth eth0 to my network/interfaces file, I still have the problem. My interface does not auto start, it waits for me to log into X, at which point NetworkManager brings it up.

I'm not sure this is the best behavior. Don't get me wrong, I LOVE NM, and I use it everywhere. It does a FANTASTIC job with my WiFi connections and just works straight out of the box for me. But, in this particular configuration, it's falling down flat.

Winbind needs to start AFTER networking is brought up. Looking at the init file, it does just this by depending on "networking". However, it's becoming clear to me that "networking" does not bring up all interfaces, even if specified as "auto". Does anybody have a suggestion moving forward on how to fix this in the final release?

---

