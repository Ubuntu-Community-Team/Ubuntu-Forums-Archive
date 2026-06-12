---
title: "Wireless not working - Need help"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by Eax.exe on 2008-01-19
Sorry for the crappy title :)

I'm using this guide: [http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros](http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros)
To try and set up my WiFi again.
I formatted this morning. Last time it worked a 100%, but now it won't compile ndiswrapper :S

I am at step 5 where it says I need to write this in the terminal:
```

pushd ndiswrapper-*/
sudo make uninstall
make
sudo make install
popd

```

When I copy+paste it, I get these errors:
```

eax@shodan:~$ pushd ndiswrapper-*/
~/ndiswrapper-1.5 ~
eax@shodan:~/ndiswrapper-1.5$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper': Is a directory
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
eax@shodan:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/eax/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/eax/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/eax/ndiswrapper-1.5/driver/built-in.o
  CC [M]  /home/eax/ndiswrapper-1.5/driver/hal.o
  CC [M]  /home/eax/ndiswrapper-1.5/driver/iw_ndis.o
  CC [M]  /home/eax/ndiswrapper-1.5/driver/loader.o
/home/eax/ndiswrapper-1.5/driver/loader.c: In function &#8216;register_devices&#8217;:
/home/eax/ndiswrapper-1.5/driver/loader.c:930: error: &#8216;struct usb_driver&#8217; has no member named &#8216;owner&#8217;
make[3]: *** [/home/eax/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/eax/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/eax/ndiswrapper-1.5/driver'
make: *** [all] Error 2
eax@shodan:~/ndiswrapper-1.5$ sudo make install
make -C driver install
make[1]: Entering directory `/home/eax/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/eax/ndiswrapper-1.5/driver \
                DRIVER_VERSION=1.5
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/eax/ndiswrapper-1.5/driver/loader.o
/home/eax/ndiswrapper-1.5/driver/loader.c: In function &#8216;register_devices&#8217;:
/home/eax/ndiswrapper-1.5/driver/loader.c:930: error: &#8216;struct usb_driver&#8217; has no member named &#8216;owner&#8217;
make[3]: *** [/home/eax/ndiswrapper-1.5/driver/loader.o] Error 1
make[2]: *** [_module_/home/eax/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/eax/ndiswrapper-1.5/driver'
make: *** [install] Error 2

```

What am I doing wrong?

Thanks In Advance :)

---

### Post by janarene on 2008-01-19
As far as I can read, right after you pasted your code you got this error message:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper

So I'd suggest running 'sudo make uninstall' until it doesn't tell you Not all installed files are removed.

Also, by the way your message was worded, it sounded like you marked the entire 5 lines of code and pasted into your terminal at one time.  If you had pasted one line at a time instead, you might have caught the error.

---

### Post by Eax.exe on 2008-01-19
> **janarene said:**
> As far as I can read, right after you pasted your code you got this error message:

NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper

So I'd suggest running 'sudo make uninstall' until it doesn't tell you Not all installed files are removed.

Also, by the way your message was worded, it sounded like you marked the entire 5 lines of code and pasted into your terminal at one time.  If you had pasted one line at a time instead, you might have caught the error.

Thanks :) I've tried running "sudo make uninstall" about 25+ times now. Didn't change a thing.

Thanks :) Still doesn't work though :( Any suggestions?

---

### Post by Eax.exe on 2008-01-19
Okay, I tried something very desperate.
I simple went to: /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper
and deleted the directort ndiswrapper myself.
I still says:

```

eax@shodan:~/ndiswrapper-1.51$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

```

What can I do?

---

