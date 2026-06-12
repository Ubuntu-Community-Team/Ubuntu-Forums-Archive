---
title: "flash plugin broken"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Falc7 on 2009-11-28
I think my flash plugin is broken, synaptic gives me this message:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

What should i do?

---

### Post by dream_coder on 2009-11-28
Try changing your download mirror in the system-->admin--> software sources should sort the problem out for you :)

---

### Post by dream_coder on 2009-11-28
or if you like remove the flash plugn completely then download the flash from adobe create a folder in .mozilla called plugins and extract the flash.so into that folder restart firefox now you have flash installed :)

---

### Post by Falc7 on 2009-11-29
I changed my download location, and i get this:
```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

W: Duplicate sources.list entry http://gb.archive.ubuntu.com karmic/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com karmic/universe Translation-en_GB (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_universe_i18n_Translation-en%5fGB)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com karmic/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://gb.archive.ubuntu.com karmic/universe Translation-en_GB (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_universe_i18n_Translation-en%5fGB)

```

I am unable to remove flash plugin, when i open synamptic, i get this message : ```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

I click ok, then synaptic closes, so i don't get the chance to remove the package.

Update manager tells me the software index is broken

---

### Post by dream_coder on 2009-11-29
try this sudo apt-get install -f in a terminal

---

### Post by [A]madeus on 2009-11-29
i got the same problem here.

Here is the result from terminal. (Please click to enlarge)
[[IMG]http://www.uppic.net/ts/19screenshot1.png[/IMG]]("http://www.uppic.net/show/c4515e3a4aa0a58f89a7ad298cbcebe3")

Please help.

---

### Post by [A]madeus on 2009-11-29
i got a solution from this thread.
[http://ubuntuforums.org/showthread.php?p=8408135#post8408135](http://ubuntuforums.org/showthread.php?p=8408135#post8408135)

Follow the fourth replied, Wojox's.
It works :)

---

### Post by Falc7 on 2009-11-29
thanks :D

---

