---
title: "DVDs won't play in any players"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by jonpon on 2011-01-14
I've just installed Ubuntu 10.10  on a new computer but can't get it to play DVDs. Here's what the terminal says when I start VLC from there.
```
fynn@fynns-computer:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9f6a914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb75aa0d4, 0xb75aa048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1295819303)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1990): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
^C[0xa01a164] signals interface error: Caught Interrupt signal, exiting...
fynn@fynns-computer:~$ 


```
Anyone have any ideas?
Thanks

---

### Post by ronnielsen1 on 2011-01-14
sudo apt-get install ubuntu-restricted-extras

---

### Post by jonpon on 2011-01-14
Thanks for responding
Vlc now works!! I downloaded the css things and It WORK!!!

 but I still have a problem!
Movieplayer asked to search for appropriate plugin but then I get this

```
No packages with the requested packages found
The requested plugins are:

```X-NAUTILUS-DESKTOP protocol source

Its not the end of the world 'cos I can now watch DVDs with VLC but still,
Any Ideas?

---

### Post by jonpon on 2011-01-14
Thanks. It did the trick,
 I downloaded the css things too and then rebooted 
Now I can watch in the player of my choice!
Brilliant!!!

---

### Post by ronnielsen1 on 2011-01-14
Where are you at in Germany? I was stationed at Kitzingen from 1980 - 1983 loved it

---

