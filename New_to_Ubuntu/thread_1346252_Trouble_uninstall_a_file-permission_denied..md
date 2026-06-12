---
title: "Trouble uninstall a file-permission denied."
date: 2009-12-04
forum: New to Ubuntu
---

### Post by username22 on 2009-12-04
I've been tryin to delete the bottom 3 files all day, but i get permission denied, im tryin to install a fresh version of gfire for pidgin but it can not install because it cant over write the bottom 3 files. I tried loggin in as fakeroot but still denied, im the admin on my comp, positive of this but it still says permissions denied to deleting the files, i also tried loggin in as root but says incorrect password but im the only admin on this comp. Any way to delete the files another way that overrides root? i use ubuntu 9.10

libxfire.a
libxfire.la
libxfire.so

su
Password: 
su: Authentication failure

---

### Post by sandyd on 2009-12-04
> **username22 said:**
> I've been tryin to delete the bottom 3 files all day, but i get permission denied, im tryin to install a fresh version of gfire for pidgin but it can not install because it cant over write the bottom 3 files. I tried loggin in as fakeroot but still denied, im the admin on my comp, positive of this but it still says permissions denied to deleting the files, i also tried loggin in as root but says incorrect password but im the only admin on this comp. Any way to delete the files another way that overrides root? i use ubuntu 9.10

libxfire.a
libxfire.la
libxfire.so

su
Password: 
su: Authentication failure
type "sudo" in front of the command.
for example
```

sudo rm [I]filename

```
[/I]

---

### Post by username22 on 2009-12-04
Thanks Carlee

---

### Post by username22 on 2009-12-04
New problem but similar. I try installin gfire from synaptic package manager but it's givin me the same error sayin it can not over write the same 3 files i listed in my first post. I checked the directory /usr/lib/purple-2 but all of the 3 files are not present. Any idea on what is happenin and why its sayin it can not overwrite the files when they dont even exist anymore?

---

### Post by username22 on 2009-12-04
bump

---

### Post by MelDJ on 2009-12-04
are the three in synaptic? if there are, mark them for complete removal

or there might be residue form the uninstall, so try sudo apt-get autoremove in terminal

---

### Post by username22 on 2009-12-04
> **MelDJ said:**
> are the three in synaptic? if there are, mark them for complete removal

or there might be residue form the uninstall, so try sudo apt-get autoremove in terminal


Neither of them are in synaptic unless im searchin incorrectly, im just searchin for 'libxfire.so and the other 2. The command you listed didnt affect it.

---

