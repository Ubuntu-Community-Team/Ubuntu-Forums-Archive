---
title: "Location of Wireless Information Files"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by CharmCityCrab on 2008-05-03
Where are the files where saved network information like wireless passwords are stored in file editor?  I'm going to try to use gedit to try to get some changes to save that I can't seem to make save through the normal interface on the uppernav bar, presuming this last attempt I made didn't do the trick.

---

### Post by Aearenda on 2008-05-03
They are saved in the keyring, if you are using Network Manager - it would be terribly unsafe to have them in a text file, unencrypted!

---

### Post by CharmCityCrab on 2008-05-04
> **Aearenda said:**
> They are saved in the keyring, if you are using Network Manager - it would be terribly unsafe to have them in a text file, unencrypted!

Is there some way to get at the keyring directly?  The network administration tool seems to keep resetting my password randomly.  Obviously, when it then goes to connect to my wifi router, it doesn't connect.  I've gone in and changed the automatic config settings, but that never worked anyway even previous to this problem -- it's only ever worked in roaming mode, and I've gone in and changed those saved settings, only to find my password goes to something strange and random where it won't connect.

---

### Post by CharmCityCrab on 2008-05-04
In case anyone had the same question I had -- I discovered the answer.  You can access the keyring graphically through Applications>Accessories>Passwords and Encryption Keys.

---

