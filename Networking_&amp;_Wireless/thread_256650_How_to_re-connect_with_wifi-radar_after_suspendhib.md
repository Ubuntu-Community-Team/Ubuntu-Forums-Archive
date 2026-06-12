---
title: "How to re-connect with wifi-radar after suspend/hibernate?"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by rosslaird on 2006-09-13
I am using wifi-radar (the gnome network app does not work on my system). Every time after I suspend or hibernate the system, the wireless connection is broken. So I have to start wifi-radar, wait for a few seconds, select the proper connection, wait for the connection to be made, then close wifi-radar.

Is there a way to automate this?

Thanks.
Ross

---

### Post by awaldram on 2006-09-13
put a script in /etc/acpi/resume.d

give it a name '97-wifistart.sh'

eg

#!/bin/bash

if [ -x /usr/sbin/wifi-radar ]; then
        /etc/init.d/wifi-radar restart;
        ifconfig eth1 up
        /usr/sbin/wifi-radar  -d

adjust the interface name to match yours
(ifconfig will tell you what it is)

---

### Post by rosslaird on 2006-09-16
Thanks for the help. Unfortunately, the script did not work. Using "sudo wifi-radar -d" works from a terminal after resume, so I wonder where the problem might be.

And I wonder if I could just have one line in the script:

wifi-radar -d

Ross

---

### Post by awaldram on 2006-09-20
Strange all the script does is

check wifiradar is installed
restart wifiradar (wpaconfig busted after restart so restart it all(for me)
bring up wifi interface this is because on my system after resume its down
run 'wifiradar -d'

yes if you inerface is up after resume then 

wifiradar -d on its own should work

---

### Post by awaldram on 2006-09-20
you could try manualy running the script from a terminal to see whats happening

---

### Post by rosslaird on 2006-09-20
Hang on -- I haven't tested it yet, but I think the problem may be that the script was not executable! So I did chmod +x and chmod 775 on it, and I'll test it this afternoon.

Also -- do the spaces matter in the first line?

Does this (spaces before "-x" and after "radar"; the way it was in your post above):

```
if [ -x /usr/sbin/wifi-radar ]; then
```

work the same as this (no spaces before and after):

```
if [-x /usr/sbin/wifi-radar]; then
```

Thanks again.

Ross

---

### Post by rosslaird on 2006-09-20
OK, I tried it. Not quite there yet. Here's the script:

#!/bin/bash
```

if [ -x /usr/sbin/wifi-radar ]; then
        /etc/init.d/wifi-radar restart;
        ifconfig eth1 up
        /usr/sbin/wifi-radar -d

```

And here's what I get when I run it from a terminal:

```
./97-wifistart.sh: line 7: syntax error: unexpected end of file

```

---

### Post by rosslaird on 2006-09-20
Noodled around a bit, got it:

```
#!/bin/bash

if [ -x /usr/sbin/wifi-radar ]; then
        /etc/init.d/wifi-radar restart;
        ifconfig eth1 up
        /usr/sbin/wifi-radar -d
fi
```

The fi seems to be required, and the spaces DO matter.
Works now (at least from the terminal -- acid test next).

Cheers.

Ross

---

