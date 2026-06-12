---
title: "Ubuntuzilla public key error?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by Alex De Duck on 2010-01-23
W: GPG error: http/downloads.sourceforge.net all Release: The following signatures could not be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29

Long story short, borrowed out my laptop and the smart alec thought he'd upgrade Mozilla for me. *sigh* Can anyone give me a hand? The package from ubuntuzilla (APT repository) is apparently installed, but I keep getting this error, and Mozilla is the same old.

---

### Post by Ant59 on 2010-01-23
Add the key for the repository:

[http://ubuntuforums.org/showpost.php?p=1653773&postcount=3](http://ubuntuforums.org/showpost.php?p=1653773&postcount=3)

---

### Post by Alex De Duck on 2010-01-23
Did that, strangely enough still getting the error despite it looking like it had been successful.

---

### Post by lovinglinux on 2010-01-23
> **Alex De Duck said:**
> Did that, strangely enough still getting the error despite it looking like it had been successful.

Check your firewall. That error on Ubuntuzilla was happening to me because my firewall was blocking the connection to the server. I didn't bother to check the connection logs, but I presume it uses a different port than http.

---

### Post by nanotube on 2010-01-23
> **Alex De Duck said:**
> W: GPG error: http/downloads.sourceforge.net all Release: The following signatures could not be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29

Long story short, borrowed out my laptop and the smart alec thought he'd upgrade Mozilla for me. *sigh* Can anyone give me a hand? The package from ubuntuzilla (APT repository) is apparently installed, but I keep getting this error, and Mozilla is the same old.

you can add the ubuntuzilla signing key with this command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29

```

also, the firefox package from ubuntuzilla is called 'firefox-mozilla-build', so if you want to use the latest mozilla release, install that package, and restart the browser. 

see more detailed instructions on everything at the ubuntuzilla website: [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

### Post by Alex De Duck on 2010-01-24
That did it, thanks!

---

### Post by nanotube on 2010-01-24
> **Alex De Duck said:**
> That did it, thanks!

great :)

---

### Post by EnlistedSquire on 2010-06-28
Trying to import the key times out. Trying to browse to it in FF also times out. Browsing to [http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/) works OK ("it works") so it looks like the Ubuntuzilla key specifically is missing.

Any ideas why?

[EDIT]Working now. Very strange.

---

