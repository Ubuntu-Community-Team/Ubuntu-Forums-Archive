---
title: "Upgrade to 8.10 disabled my wireless"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by mikex on 2008-11-13
Well, I had a perfectly good working wireless setup on my hp laptop with the previous version of Ubuntu, but I just upgraded to 8.10 and it rendered my wireless setup broken - no connection can be made. Very unhappy at the moment...

I see it's using a restricted driver now called wl - don't know what that is. Also, when I try to run the hardware tester it pops up a box at the bottom of the screen which promptly goes away and nothing happens. The same thing happens when I try to run the Windows Wireless drivers tab under Administration - nothing ever opens up.

When I try to enter a WPA password under the network Connections panel, I get this message -

Updating connection failed: nm-ifupdown-connection.c.82-connection update not supported (read-only)

Riiiiight...

So, What am I to do about this? As I said, the laptop was connecting to the internet just fine before I upgraded. I am totally lost as to what went wrong or how to fix it.

---

### Post by xadder on 2008-11-13
Similar problems here. My Thinkpad T43 worked very well in Hardy (and Gutsy and ....), but now network-manager just shows me a list of the wireless networks I connected to in the past, but no way to see or use the wireless around me. Very frustrating.

In case it helps, I have:

 description: Wireless interface
                product: PRO/Wireless 2915ABG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:04:02.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:e0:ec:d7
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

---

### Post by strikeback03 on 2008-11-13
My T43 with 2915ABG did not show me any networks to connect to when I first rebooted after upgrading, I had to go to the configuration for my router and add my WPA2 password again, then restart X, and my connection came up.

However it does not stay up, it randomly disconnects and sometimes asks to confirm the password.  So now I'm looking for a solution for that.

---

### Post by xadder on 2008-11-14
Hi,

I don't have a router, and in general need wireless to work when I travel. As it is now I don't see any hint that there are wireless networks anywhere, so issues like WPA (I'm not sure what that is I must admit, but I have used it with passwords when needed from my Hardy system).
Something broke with intrepid, so I hope there is a solution :(

---

### Post by mikex on 2008-11-14
OK, so no hints?

Well I restored my laptop to an image of the previous (working) version of Ubuntu with wireless - I really don't need these headaches.

Venting Mode - Why oh why doesn't wireless support get any better with upgrades, *especially* when the user has a setup that is *working* before an upgrade? This is what causes my love/hate relationship with this OS!](*,)

Let's try this question then:

BEFORE I allow the upgrade to 8.10 to take over, what could I do BEFORE clicking the upgrade button to make sure my perfectly good wireless setup isn't trashed by 8.10?

---

### Post by mirror2m on 2008-11-14
Try to check it here.
I got the same problem when I upgraded it to ver 8.10. Now it seems to be fine. Good luck ;)

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by mirror2m on 2008-11-14
In short:

sudo apt-get install wpasupplicant
sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces
  Comment out everything other than “lo” entries in that file and save the file
sudo gedit /etc/default/wpasupplicant
  Add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

  Reboot your system or use the following command

[source]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

---

### Post by mikex on 2008-11-14
> **mirror2m said:**
> In short:

sudo apt-get install wpasupplicant
sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces
  Comment out everything other than “lo” entries in that file and save the file
sudo gedit /etc/default/wpasupplicant
  Add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

  Reboot your system or use the following command

[source]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

OK thanks, but are you telling me to do this BEFORE or AFTER I upgrade. You didn't specify.

---

### Post by mikex on 2008-11-15
Wait a minute... how can I get anything (sudo apt-get install) if the network won't function after I upgrade!

When I do the first command

sudo apt-get

nothing at all happens...

when I try to configure the wireless password I get this message

Updating connection failed: nm-ifupdown-connection.c.82-connection update not supported (read-only)

When I try to run the hardware tester it pops up a box at the bottom of the screen which promptly goes away and nothing happens. The same thing happens when I try to run the Windows Wireless drivers tab under Administration - nothing ever opens up.

Something about my networking is foobarred after I do the upgrade!

---

### Post by xadder on 2008-11-16
Wireless working, Phew!!

I started trying some of the ideas mentioned here and elsewhere, but wpasupplicant was already installed, and I couldn't get module-assistant to install ipw2200 (a suggested driver for intel). I almost gave up, but tried one very simple thing:

edit /etc/network/interfaces and remove all lines except those including lo.
Now I just have:

auto lo
iface lo inet loopback

Instead of:
iface eth1 inet dhcp
wireless-essid YYY XXXX

Suddenly I can "see" al the neworks around me again, and connecting has become as simple as it used to be :-)

---

