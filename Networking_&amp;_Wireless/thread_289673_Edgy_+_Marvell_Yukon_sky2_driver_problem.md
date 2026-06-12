---
title: "Edgy + Marvell Yukon sky2 driver problem"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by koepi on 2006-10-31
I have browsed trough forum for this problem and none of the threads helped me.

The thing is that I have Marvell Yukon network card and sky2 driver loaded, which is randomly disconnecting. Then I have to manually connect it back trough network settings. This is really frustrating me.

In dapper I had the same problem and I solved it with sk98lin driver, which worked for me perfectly.

This driver I wanted than to use also in Edgy, but without luck.

Thing just doesn't want to install. It gives me following error:

sudo sh ./install.sh

./install.sh: 69: Syntax error: "(" unexpected

Can anybody help me on this, cause I didn't found any forum on developers site to post this issue there?

Thanks!

If you need more info on my system I will gladly post it.

---

### Post by koepi on 2006-11-01
Anyone!?!??! :confused: 

Come guys, there is surely someone who has/had the same problem. I don't believe that I'm only one.

Thanks!

---

### Post by amo-ej1 on 2006-11-01
this might be a long shot ;-)

but when you open install.sh if it starts with #!/bin/sh or #!/bin/bash could you change this line ?

If it says #!/bin/bash make it #!/bin/sh and vice versa, i've seen some issues with this and it might even be something ugly like that ;)

---

### Post by koepi on 2006-11-02
I did what you have proposed but it didn't solved the problem. The error is still the same.

Maybe it would help info on how I try to change driver. I use following procedure:

sudo apt-get install build-essential linux-headers-$(uname -r)

sudo ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux

sudo modprobe -r sky2

sudo ./install.sh

This worked in dapper.

Thanks!

---

### Post by koepi on 2006-11-04
This is getting anoying!!! ](*,) 

Do some of you have any solution to this nightmare!?!?!

All I want is to just install sk98lin driver instead of buggy sky2. I did it before in dapper with no problem, why can't I do the same in edgy!?!? :evil:

If someone knows where to point me, please do!!!

Thanks!

---

### Post by koepi on 2006-11-05
Anybody!?!?!?! :confused:

---

### Post by FrodoB on 2006-11-05
Maybe if you posted a link to the driver that is causing you this issue?

---

### Post by 23meg on 2006-11-05
Why don't you attach a copy of that install.sh?

---

### Post by koepi on 2006-11-05
Ok, here is the file which is causing troubles. :(

---

### Post by FrodoB on 2006-11-06
Open the install.sh file in "Text Editor" or vi and then change the first line from:

#!/bin/sh

to

#!/bin/bash

/bin/sh is a link to /bin/dash and dash does not seem to be happy with the script.

Then try it again, it will likely work.

---

### Post by albox on 2006-11-11
Hi  koepi,
I have the same problem and I'd like to know if you managed to install sk98lin driver instead of sky2 ?

THanks

---

### Post by albox on 2006-11-18
Hi, I didn't manage to replace sk2 by sk98lin.

Here is what I tried :

> sudo rmmod sky2
sudo modprobe sk98lin
sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ ok ]

What I don't really understand is that sometimes, after booting, I can't use the network and sometimes, it works. If I try to remove and reinsert sky2, it doesn't work too :
> 
$ lsmod | grep sk
sk98lin               218900  0

sudo modprobe -r sk98lin
sudo modprobe sky2
sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ ok ]


---

### Post by rykel on 2006-12-09
Hi,

Is there a simpler, GUI way to solve the connection problem?

I am running Ubuntu Edgy on a Toshiba laptop with a Marvell Yukon Gigabyte controller too, and it only connects on a fresh bootup. Alas, it stays connected only for about 5 minutes, and then it takes a reboot to reconnect to the internet.

I am not confident running the script etc. but if you could give me a step-by-step guide which has been proven to work, I will be most happy to do it.

Thank you for your help!

---

### Post by rykel on 2006-12-10
Hi people,

I managed to install the driver on Edgy!!

In case you come across a Kernel Header not found error message, go to /usr/src and see if you have the following folder:
**[INDENT]linux-headers-2.6.17-10-386[/INDENT]**

Your folder might be slightly different, but if you had installed linux-source, linux-headers etc. you should have something in there. (I am VERY confused by them all, so many files to download just to get a "header"!)   :confused: 

Once you have found the folder, create a symbolic link to it.

The **WRONG** command I did was:
[INDENT]**sudo ln -s /usr/src/2.6.17-10-386 /usr/src/linux**
(Folder "2.6.17-10-386" did NOT exist)[/INDENT]

If you did what I did wrongly, then you need to delete that link by:
[INDENT]**sudo rm /usr/src/linux**[/INDENT]

Then re-issue:
[INDENT]**sudo ln -s /usr/src/linux-headers-2.6.17-10-386 /usr/src/linux**[/INDENT]

After that, the installation of sk98lin should be successful.

And now, for me to find an ethernet modem and see if it works...   =)

Hope this helps!

P/S. The screenshot shows how my /usr/src folder looks like after I have created the correct symbolic link... look carefully at the top left icon called "linux" with the shortcut arrow... yeah, THAT is the link that needs to be created.

---

### Post by rykel on 2006-12-24
Hi all,

I have tried to see if the official sk98lin driver can give me a persistently good internet connection, but alas, even with the official driver, I had a disconnect after 20-30 mins or so... I will try to uninstall/remove sky2 completely and see if this helps, but anyway, what is your experience with the official driver? Does it work?

---

### Post by teomatto on 2007-01-11
i suggest to you to install new kernel follow this link
[http://www.ubuntuforums.org/showthread.php?t=326343](http://www.ubuntuforums.org/showthread.php?t=326343)

in this way i solved every my problems

teo

---

### Post by rykel on 2007-01-30
Hi all,

I am glad to inform you that with Dapper, the official sk98lin driver works for my Toshiba M40 Marvell/Yukon ethernet card, and I had it running continously without a single disconnect for more than 12 hours.

[INDENT]The steps to achieve this result are roughly these:
1.   Install the "headers" etc.
2.   Reboot.
3.   sudo modprobe sk98lin.
4.   Use Networking to Deactivate then Activate the eth1.
[/INDENT]
However, I am NOT sure if "sudo modprobe sk98lin" is even necessary, because I do not know if the official installer has set up the driver to load everytime Ubuntu boots up. Do you?

Thus, perhaps you might want to switch to Dapper Drake to ensure a trouble-free operation for the card.

Hope that helps!

---

### Post by stevecs on 2007-02-17
I'm also having serious problems w/ Ubuntu 6.10 & the sky2 driver (Asus P5W64WS Pro m/b)  Only the 2nd nic (which needs the sky2 driver) is having the problem where it will completely drop offline.   In order to fix it temporarily I have to remove the module (stop all services bound to that ip) reload the module and then restart the services.    A bloody pain in the a**.  

I've found references on google that there are numerous issues w/ the sky2 driver which is fixed in later 2.6.19/2.6.20 but have not seen anything back-ported to ubuntu 6.10 for this.   (yes, I could manually compile the driver but frankly I'd rather have it fixed in the main distribution as this is a problem to everyone).

---

### Post by sergioperr on 2008-07-14
Just for the record (maybe other people came here due to Google after time !):

I've tried this and other methods involving kernel recompiling, without success.
10 seconds before giving up, I found this solution from the user "Wanted". It worked for me ('me' is a Toshiba M305-S4826, and Ubuntu 8.04 -the Hardy Heron- released in April 2008.
(if the 'rmmod' command gives you and error, you can continue: disregard):
$ sudo su -
[type your password]
# rmmod sky2
# cd /lib/modules/`uname -r`/kernel/drivers/net
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko
# echo sky2 >> /etc/modules
# modprobe sky2

Good luck !
:guitar:

---

