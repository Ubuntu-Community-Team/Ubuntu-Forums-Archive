---
title: "WIFI not working on Lenovo Yoga 900 (Ubuntu 16.04 LTS)"
date: 2018-01-14
forum: Networking &amp; Wireless
---

### Post by demaigos on 2018-01-14
Hi there,

I just installed Ubuntu 16.04 LTS on my Lenovo Yoga 900 13 ISK.

During the installation, I could select my local wifi and connect to it. However, once booting again, there is no Wifi connection and I also can not select any networks. Wifi seems to be disabled. rfkill gives me

```

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

According to [https://ubuntuforums.org/showthread.php?t=2308187](https://ubuntuforums.org/showthread.php?t=2308187), I followed these instructions:

[COLOR=#000000]> 
You have that issue, it is corrected in a newer 15.10 kernel[/COLOR]

[COLOR=#000000]Download [/COLOR][https://www.kernel.org/pub/linux/ker...0151120.tar.gz]("https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz")[COLOR=#000000] and transfer it to Ubuntu desktop, right click on the file and choose 'extract here'[/COLOR]
[COLOR=#000000]Then in terminal[/COLOR][COLOR=#000000]Code:
cd ~/Desktop/backports-20151120
make defconfig-iwlwifi
make
sudo make install[/COLOR]


However, when following these instructions, I get 
```

markus@markus_Lenovo-YOGA-900-13ISK:~/Schreibtisch/backports-20151120$ make deconfig-iwlwifi
make[2]: „conf" ist bereits aktuell.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
markus@markus-Lenovo-YOGA-900-13ISK:~/Schreibtisch/backports-20151120$ make
make[5]: „conf“ ist bereits aktuell.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/markus/Schreibtisch/backports-20151120/compat/main.o
In file included from /home/markus/Schreibtisch/backports-20151120/backport-include/backport/backport.h:7:0,
                 from <command-line>:0:
./include/asm-generic/qrwlock.h: In function ‘__qrwlock_write_byte’:
/home/markus/Schreibtisch/backports-20151120/backport-include/linux/kconfig.h:25:28: error: implicit declaration of function ‘config_enabled’ [-Werror=implicit-function-declaration]
 #define IS_BUILTIN(option) config_enabled(option)
                            ^
./include/asm-generic/qrwlock.h:156:26: note: in expansion of macro ‘IS_BUILTIN’
  return (u8 *)lock + 3 * IS_BUILTIN(CONFIG_CPU_BIG_ENDIAN);
                          ^
./include/asm-generic/qrwlock.h:156:37: error: ‘CONFIG_CPU_BIG_ENDIAN’ undeclared (first use in this function)
  return (u8 *)lock + 3 * IS_BUILTIN(CONFIG_CPU_BIG_ENDIAN);
                                     ^
/home/markus/Schreibtisch/backports-20151120/backport-include/linux/kconfig.h:25:43: note: in definition of macro ‘IS_BUILTIN’
 #define IS_BUILTIN(option) config_enabled(option)
                                           ^
./include/asm-generic/qrwlock.h:156:37: note: each undeclared identifier is reported only once for each function it appears in
  return (u8 *)lock + 3 * IS_BUILTIN(CONFIG_CPU_BIG_ENDIAN);
                                     ^
/home/markus/Schreibtisch/backports-20151120/backport-include/linux/kconfig.h:25:43: note: in definition of macro ‘IS_BUILTIN’
 #define IS_BUILTIN(option) config_enabled(option)
                                           ^
cc1: some warnings being treated as errors
scripts/Makefile.build:308: die Regel für Ziel „/home/markus/Schreibtisch/backports-20151120/compat/main.o“ scheiterte
make[6]: *** [/home/markus/Schreibtisch/backports-20151120/compat/main.o] Fehler 1
scripts/Makefile.build:581: die Regel für Ziel „/home/markus/Schreibtisch/backports-20151120/compat“ scheiterte
make[5]: *** [/home/markus/Schreibtisch/backports-20151120/compat] Fehler 2
Makefile:1550: die Regel für Ziel „_module_/home/markus/Schreibtisch/backports-20151120“ scheiterte
make[4]: *** [_module_/home/markus/Schreibtisch/backports-20151120] Fehler 2
Makefile.build:6: die Regel für Ziel „modules“ scheiterte
make[3]: *** [modules] Fehler 2
Makefile.real:88: die Regel für Ziel „modules“ scheiterte
make[2]: *** [modules] Fehler 2
Makefile:40: die Regel für Ziel „modules“ scheiterte
make[1]: *** [modules] Fehler 2
Makefile:30: die Regel für Ziel „default“ scheiterte
make: *** [default] Fehler 2
markus@markus-Lenovo-YOGA-900-13ISK:~/Schreibtisch/backports-20151120$ 
markus@markus-Lenovo-YOGA-900-13ISK:~/Schreibtisch/backports-20151120$ sudo make isntall
[sudo] Passwort für markus: 
make[1]: *** Keine Regel, um „isntall“ zu erstellen.  Schluss.
Makefile:40: die Regel für Ziel „isntall“ scheiterte
make: *** [isntall] Fehler 2
markus@markus-Lenovo-YOGA-900-13ISK:~/Schreibtisch/backports-20151120$ sudo make install
  CC [M]  /home/markus/Schreibtisch/backports-20151120/compat/main.o
In file included from /home/markus/Schreibtisch/backports-20151120/backport-include/backport/backport.h:7:0,
                 from <command-line>:0:
./include/asm-generic/qrwlock.h: In function ‘__qrwlock_write_byte’:
/home/markus/Schreibtisch/backports-20151120/backport-include/linux/kconfig.h:25:28: error: implicit declaration of function ‘config_enabled’ [-Werror=implicit-function-declaration]
 #define IS_BUILTIN(option) config_enabled(option)
                            ^
./include/asm-generic/qrwlock.h:156:26: note: in expansion of macro ‘IS_BUILTIN’
  return (u8 *)lock + 3 * IS_BUILTIN(CONFIG_CPU_BIG_ENDIAN);
                          ^
./include/asm-generic/qrwlock.h:156:37: error: ‘CONFIG_CPU_BIG_ENDIAN’ undeclared (first use in this function)
  return (u8 *)lock + 3 * IS_BUILTIN(CONFIG_CPU_BIG_ENDIAN);
                                     ^
/home/markus/Schreibtisch/backports-20151120/backport-include/linux/kconfig.h:25:43: note: in definition of macro ‘IS_BUILTIN’
 #define IS_BUILTIN(option) config_enabled(option)
                                           ^
./include/asm-generic/qrwlock.h:156:37: note: each undeclared identifier is reported only once for each function it appears in
  return (u8 *)lock + 3 * IS_BUILTIN(CONFIG_CPU_BIG_ENDIAN);
                                     ^
/home/markus/Schreibtisch/backports-20151120/backport-include/linux/kconfig.h:25:43: note: in definition of macro ‘IS_BUILTIN’
 #define IS_BUILTIN(option) config_enabled(option)
                                           ^
cc1: some warnings being treated as errors
scripts/Makefile.build:308: die Regel für Ziel „/home/markus/Schreibtisch/backports-20151120/compat/main.o“ scheiterte
make[5]: *** [/home/markus/Schreibtisch/backports-20151120/compat/main.o] Fehler 1
scripts/Makefile.build:581: die Regel für Ziel „/home/markus/Schreibtisch/backports-20151120/compat“ scheiterte
make[4]: *** [/home/markus/Schreibtisch/backports-20151120/compat] Fehler 2
Makefile:1550: die Regel für Ziel „_module_/home/markus/Schreibtisch/backports-20151120“ scheiterte
make[3]: *** [_module_/home/markus/Schreibtisch/backports-20151120] Fehler 2
Makefile.build:6: die Regel für Ziel „modules“ scheiterte
make[2]: *** [modules] Fehler 2
Makefile.real:88: die Regel für Ziel „modules“ scheiterte
make[1]: *** [modules] Fehler 2
Makefile:40: die Regel für Ziel „install“ scheiterte
make: *** [install] Fehler 2

```

Can't really help myself with these errors (let me know what exactly you want to have translated... Don't know why it's in German :-( )

Errors may due to the fact that this fix was intended for a different Ubuntu version?

Thanks for your help!!!

---

### Post by jeremy31 on 2018-01-14
Try in terminal ```
echo "blacklist ideapad-laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
```
Reboot and welcome to the forums

---

### Post by demaigos on 2018-01-14
Hi Jeremy,

thanks for the warm welcome.

I'm sorry for not mentioning this in my initial post: I tried blacklisting it according to the thread as well, before I came to your last suggestion from that thread

Whereas 
```

echo "blacklist ideapad-laptop"

```
gives me a result ("blacklist ideapad-laptop"), the sudo tee command thereafter does not deliver any results, a reboot therefore also did not change anything :-/

Thanks,
Markus

---

### Post by jeremy31 on 2018-01-14
See the wireless script link in my signature and post results

---

