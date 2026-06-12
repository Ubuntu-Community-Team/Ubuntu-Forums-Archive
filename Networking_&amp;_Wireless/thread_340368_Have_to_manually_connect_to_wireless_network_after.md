---
title: "Have to manually connect to wireless network after reboot"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by andreb on 2007-01-17
Ah, the sweet pain associated with free software.. ;)

I struggled for hours yesterday trying to get my newly installed Ubuntu 6.10 up and running with a D-Link USB Wireless network dongle (G-122). After 3-4 hours it finally worked thanks to posts on forums like this. I guess it was really straight-forward really. But it sure was a big pain trying to find out which "how-to" to follow. 

On to my problem, but first a list of what's working / my config:
iwlist scan #shows my AP

Output from /etc/network/interfaces:
iface rausb0 inet static
adress ip.add.re.ss #my ipaddress
netmask ne.t.ma.sk #the netmask
gateway ga.te.w.ay #my gateway
wireless-essid xxx #my ssid
wireless-key xxx #my key, 13 digits
wireless-channel x  #my channel
auto rausb0

In addition I've specified DNS addresses manually.

If I launch terminal and enter:
sudo iwconfig rausb0 essid AP key s:1234567891234

-all works flawlessly. However if I reboot, I have to launch terminal and write this command again. In other words Ubuntu doesn't seem to connect to my AP automatically. What should I do ?

---

### Post by dmizer on 2007-01-17
lol ... hum, maybe a little dirty, but it'll work.

just edit /etc/rc.local like so:
```
sudo nano /etc/rc.local
```
and you should get a file that looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```
just add your network command above the "exit 0" like so:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig rausb0 essid AP key s:1234567891234
exit 0
```
*sudo is not necessary.

save the file and exit.  then, reboot and you should be connected.

---

### Post by andreb on 2007-01-17
Thanks for the help, dmizer!

---

### Post by deejaylinux on 2007-01-17
Hi, I think writing a script like this (called wireless-settings for example):

#!/bin/sh
# Set additional parameters for wireless configuration.
[ "$IFACE" = "rausb0" ] || exit 0

test -f /sbin/iwconfig || exit 0

if [ "$VERBOSITY" = 1 ]; then
        echo "Setting the Wireless adapter..."
        /sbin/iwconfig $IFACE essid AP key s:1234567891234 || true
else
        /sbin/iwconfig $IFACE essid AP key s:1234567891234 >/dev/null 2>&1 || true
fi

in /etc/network/if-up.d is a better solution. When your system is going to update, maybe the rc.local is updated also. But if you create this script, never will be delete on updates.

Hope this helps you.

Regards

---

### Post by andreb on 2007-01-17
Thanks for your input there, deejaylinux :)

I have however run into another problem, that might result in me just setting aside that Ubuntu box for awhile.. I was hoping to set up this machine I got from work as a file- /backup server at home (running Ubuntu), using wireless networking. 

I use an iMac in my daily work, running AirPort (Extreme) and an AirPort Express basestation. I was thinking that 54Mbps (even divided by two) should be enough for incremental backups, but I keep ending up with poor transmission even though the signal strength is ok. One hour to backup 4-500MB is too much.. 

So if none of you guys have any bright ideas conserning this as well, I'm afraid I've "wasted" some of your time as well on this project of mine.. Thanks though ;)

---

### Post by deejaylinux on 2007-01-17
How do you transfer files between both boxes?

That is, are you using FTP, SMB, NFS,...?

If you are sharing resources through SMB, there is a post talking about this... just wait to somebody solve the question.

Bye bye

---

