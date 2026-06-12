---
title: "avm WLAN USB-Stick (Ubuntu 6.10)"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by annuzzer on 2006-10-29
Hi,

finally found the appropriate forum, I hope.

After the in other respects smooth installation of Ubuntu 6.10 on my laptop I'd like to establish a connection to the WWW via [my WLAN USB-stick](http://www.avm.de/en/Produkte/FRITZBox/FRITZ_WLAN_USB_Stick/index.html). The only installation instruction I found was [this German one](http://wiki.ubuntuusers.de/FRITZ%21WLAN_USB_Stick).

Unfortunately after entering
```
cd fritz/src
sudo make
```

(changing to the unpacked directory and starting the installation) I got this error messages ('Fehler' is the German word for error as you may know):
```
ann@ubuntubox:~/fritz/src$ sudo make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/ann/fritz/src modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/ann/fritz/src/main.o
In file included from /home/ann/fritz/src/main.c:31:
/home/ann/fritz/src/tools.h:75: error: expected identifier or ‘(’ before ‘typeof’
/home/ann/fritz/src/tools.h:75: error: expected ‘)’ before ‘__xchg’
/home/ann/fritz/src/main.c:65: error: unknown field ‘owner’ specified in initializer
/home/ann/fritz/src/main.c:65: warning: initialization from incompatible pointer type
make[2]: *** [/home/ann/fritz/src/main.o] Fehler 1
make[1]: *** [_module_/home/ann/fritz/src] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.17-10-generic'
make: *** [fwlanusb.o] Fehler 2
```
'Betrete Verzeichnis' means 'entering directory' and 'Verlasse Verzeichnis' at the end of the error message means 'leaving directory'.

Any ideas how to get ahead? If you need additional information please let me know.

Thanks in advance...

Ann

---

### Post by justplayin on 2006-10-30
I got the stick to work under Ubuntu Dapper with this [Kubuntu  Howto]("http://www.kubuntu.de/forum/forum.php?req=thread&id=4639&page=-1")
They have a detailed description of compiling ndiswrapper and the necessary packages. Although it's for Kubuntu it worked under Ubuntu for me.
I guess for Edgy it's the same process as for Dapper.

---

