---
title: "True combat elite not working"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by wilbuzz2 on 2010-10-13
when running tce i get this in the treminal 

Sys_LoadDll(/home/will/enemy-territory/tcetest/ui.mp.i386.so)... 
Sys_LoadDll(/home/will/enemy-territory/tcetest/ui.mp.i386.so) failed:
"libstdc++.so.5: cannot open shared object file: No such file or directory"
Sys_LoadDll(ui) failed dlopen() completely!
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: VM_Create on UI failed
anyone know what i can do

---

### Post by NightwishFan on 2010-10-13
Run this command or click  here: [_**[COLOR="Blue"]apt://libstdc++5[/COLOR]**_]("apt://libstdc++5")

```
sudo apt-get install libstdc++5
```

---

### Post by Soulcage on 2010-10-13
```
sudo apt-get install libstdc++5
```

If there's no version then you need to download it [http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libstdc%2B%2B5]("http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=libstdc%2B%2B5") on Lucid ubuntu I use jaunty's version.

---

### Post by NightwishFan on 2010-10-13
Might not be a libstdc++5 on ubuntu 10.04. Here is an alternate way:

```
sudo apt-get install libstdc++6
```
Then:
```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```

---

### Post by wilbuzz2 on 2010-10-13
Worked but i only get 3 servers for some reason but thanks for getting it to work.Once again THANK YOU!

---

