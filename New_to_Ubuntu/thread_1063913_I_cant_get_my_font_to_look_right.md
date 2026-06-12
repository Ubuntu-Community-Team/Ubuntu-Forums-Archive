---
title: "I cant get my font to look right"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Luehrs1 on 2009-02-08
My font looks funny and I dont know why

[ATTACH]102654[/ATTACH]

---

### Post by Idaho Dan on 2009-02-08
luehrs,
can you go to System, Preferences, Appearance and then Fonts?

Dan.

---

### Post by Luehrs1 on 2009-02-08
Yea, its all set to sans

---

### Post by photon_man62 on 2009-02-08
Try typing this into a terminal:
```

sudo apt-get reinstall defoma
```

---

### Post by Luehrs1 on 2009-02-08
patrick@patrick:~$ sudo apt-get reinstall defoma
[sudo] password for patrick: 
E: Invalid operation reinstall
patrick@patrick:~$ 

This is what it gives me

So i did install

patrick@patrick:~$ sudo apt-get reinstall defoma
[sudo] password for patrick: 
E: Invalid operation reinstall
patrick@patrick:~$ sudo apt-get install defoma
Reading package lists... Done
Building dependency tree       
Reading state information... Done
defoma is already the newest version.
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
patrick@patrick:~$ 

But it still looks the same

---

