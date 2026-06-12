---
title: "&quot;Unblacklist&quot; wireless driver"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by roundhead on 2010-04-17
I tried to blacklist my wireless driver to see if karma had another driver to install since the one I initially installed did not work. now nothing works. does anyone know how to "unblacklist" the driver?

---

### Post by lkraemer on 2010-04-17
To Blacklist a driver you had to edit the file at:
/etc/modprobe.d/blacklist.conf

In that file you added some filename for the driver that needed to be
blacklisted, or you removed the "#" at the beginning of the line.

Just go back and edit the file with gedit or nano and reverse what
you previously did.  

You can see a list of the previous history commands with the
following command in a terminal window:  (cut and paste to prevent typos)
```

history

```
If you want to pipe those commands to a file use......
```

history > histfile.txt

```

```

cd /
pwd
ls -alt
sudo nano /etc/modprobe.d/blacklist.conf       ........For >=9.04 otherwise blacklist
exit

```

To remove any modules you previously loaded to test use:.....(just as an example)
```

modprobe -r b44
modprobe -r b43

```

Then you will need to reboot for the changes to take effect or try:
```

sudo /etc/init.d/networking restart

```

This way things will be as they were before you made any edits.

But, this did not tell you anything about your problem of non working
Wifi.  So, open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 and above use:
                                  cat /etc/modprobe.d/blacklist.conf
iwconfig
cd /
ls -alt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

It will be your decision on what to use.......Ndiswrapper or provided Driver
for your version.

If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below, if you want to do it manually:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

lk

---

