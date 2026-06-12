---
title: "Network manager slow to load after boot"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by gagne.marc on 2010-10-11
I recently did a clean install of Maverick. Now, when I boot my computer, the network manager takes about 10-15 seconds to load before it finally connects to my network. Why? When I log out and log back in it's normal...
I have noticed one thing, though. Before, my "login" keyring had a password on it, and I had to enter it before being able to do anything - including starting the Network Manager. The moment I removed my password, the box no longer appeared as expected... but it was still as if it took the system a while to activate the Network Manager.

---

### Post by JustinR on 2010-10-11
> **gagne.marc said:**
> I recently did a clean install of Maverick. Now, when I boot my computer, the network manager takes about 10-15 seconds to load before it finally connects to my network. Why? When I log out and log back in it's normal...
I have noticed one thing, though. Before, my "login" keyring had a password on it, and I had to enter it before being able to do anything - including starting the Network Manager. The moment I removed my password, the box no longer appeared as expected... but it was still as if it took the system a while to activate the Network Manager.

This is normal - it takes a while for it to initialize network devices and set them up - and it also takes a few seconds to scan things like wireless networks, get an IP address etc.

The reason it's working after logging out and back in is because your just filling up the 15 seconds it takes to connect to a network.

I wish it was faster - with Ubuntu 10.10 it seems to take around 10 seconds to connect to a network. It seems to defeat the purpose of being able to boot straight to the desktop and launch Opera in 2 seconds and then have to wait 10 seconds for the Internet to connect.

---

### Post by beew on 2010-10-12
> **JustinR said:**
> This is normal - it takes a while for it to initialize network devices and set them up - and it also takes a few seconds to scan things like wireless networks, get an IP address etc.

The reason it's working after logging out and back in is because your just filling up the 15 seconds it takes to connect to a network.

I wish it was faster - with Ubuntu 10.10 it seems to take around 10 seconds to connect to a network. It seems to defeat the purpose of being able to boot straight to the desktop and launch Opera in 2 seconds and then have to wait 10 seconds for the Internet to connect.

I am not sure that it is normal. In my case it connects almost immediately (Lucid on both my machines with totally different wifi cards. I have tested Maverick on only one machine and it connects almost immediately as well) The only times when it takes 10 seconds or more to connect are when the signal is very weak (which has nothing to do with Ubuntu as Windows cannot connect either)

---

### Post by beew on 2010-10-12
> **gagne.marc said:**
> The moment I removed my password, the box no longer appeared as expected... but it was still as if it took the system a while to activate the Network Manager.

How did you remove your password?

---

### Post by gagne.marc on 2010-10-12
@beew: Passwords and Encryption Keys.
@JustinR: No, no, I've always had that. I mean the network manager appears, but no networks are displayed. Then it starts connecting, takes another five seconds, and it's ready.
EDIT: Whoa. It works normally now. Huh. Maybe a much needed update?
Anyway, thanks for your help everyone!

---

### Post by gagne.marc on 2010-10-13
Hold on! It's still there!
Come on, can anyone help me? This is really annoying. My Ubuntu is so fast otherwise, just this one, crucial thing...

---

### Post by gagne.marc on 2010-10-15
Oh, and it's the same for the battery indicator.

---

