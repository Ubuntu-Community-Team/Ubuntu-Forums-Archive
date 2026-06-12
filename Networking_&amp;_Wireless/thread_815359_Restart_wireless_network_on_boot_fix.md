---
title: "Restart wireless network on boot fix"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by humina on 2008-06-01
Every time I start my computer, the wireless connection does not load properly.  I have a static IP address and I'm using WPA.  It works if I run the command:
```
sudo /etc/init.d/networking restart
```
Of course this is a pain to have to run every time.  Most people add this line to their rc.local but this is not a real fix.  This is a band aid solution and the real fix is to make the wireless card load properly when the machine boots.  Can this get fixed?  Has anyone been able to REALLY fix the problem and not have a band aid solution?

---

### Post by chili555 on 2008-06-01
> Has anyone been able to REALLY fix the problem and not have a band aid solution?Certainly!

Since you want to connect automatically, I assume this si a desktop machine that will stay at home and will therefor not need Network Manager. The answer is to *sudo gedit /etc/network/interfaces* to make it look like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.168.40
gateway 192.168.168.230
dns-nameservers 192.168.168.230
netmask 255.255.255.0
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>
```The key is 'auto wlan0.'

The details of how to set this up are here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Now, having said that, some cards will *still* not start without a band-aid. I would not be afraid to use it if you need it.

---

### Post by kevdog on 2008-06-02
Running anything in the init.d folder brings up the concept of run levels.  The default runlevel for ubuntu is 2. You can confirm this by simply typing runlevel at the command line.  There are 7 runlevels total and only usually are 2,3,4,5 used for booting.  Run level 6 is for shutdown (ie sudo init 6 will actually shut down your machine).  I borrowed this off the wiki:

Debian Linux

Debian, as well as most of the distributions based on it, like early Ubuntu, does not make any distinction between runlevels 2 to 5. See also the Debian FAQ on booting.

    * 0 - Halt
    * 1 - Single
    * 2 through to 5 - Full multi-user with console logins and display manager if installed
    * 6 - Reboot

Ubuntu

Ubuntu 6.10 (Edgy Eft) and later contain Upstart as a replacement for the traditional init-process but they still use the traditional init scripts and Upstart's SysV-rc compatibility tools to start most services and emulate runlevels.


Assuming you are using run level two, the actual programs that are started within run level 2 are contained within /etc/rc2.d

Within this program, you will see a bunch of symbolic links such as S20-<program_name>.  S=Start K=Kill.  The actual number (20 in this example) can range from 0-99.  The number actually controls the order they are started within the boot process.  Basically in the order they are specified in the file, these symbolic links call the actual startup scripts located in the init.d folder.  Again the links are in the rc2.d folder are actual symbolic links to the programs in the /etc/init.d folder.

Sometimes when you need to restarting the networking service, it is because it is being started either too early in the boot sequence, or when it is brought up, it was dependent on another service that hasn't been started or was in the process of starting.  The solution to this problem may be to start networking services later in the boot sequence, or simply have the networking services pause for a while (sleep 20), after being initiated. 

The quickest way you can determine if this theory is accurate, would be to manually edit the /etc/init./networking startup file, and under the start block would be to put a line like: sleep 20.  This would test the theory.  If this theory in fact solves your problem, you could leave the sleep statement in place, or actually change the boot order of the networking service using the program update-rc.d.  Here is a link: [http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

Basically you would remove the networking services (remove symbolic link from rc2.d using the update-rc.d program) and then 
reinstall the link (using update-rc.d) to the networking service however specifying a higher boot level order than it was previously so the service brought up later in the boot sequence.

Make sense?

---

