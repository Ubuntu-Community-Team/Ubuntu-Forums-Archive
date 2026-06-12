---
title: "Help for Intel PRO/Wireless 3945ABG"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by nlooie on 2007-04-04
Hi

I have installed Ubuntu on my new laptop, but i'm having trouble with my wireless internet. I know that Intel PRO/Wireless 3945ABG is supported, but i just cant get it to work. Can anyone please guide me? What should i do?

Thank.

---

### Post by handaxe on 2007-04-04
First of all check that you have the linux-restricted-modules-common package installed in synaptic.

Most common problem.

Lets take it from there.

HA

---

### Post by nlooie on 2007-04-04
Thaks for the reply.

I can see that it is installed in the Synaptic Package Manager. The istalled virsion is 2.6.17.5-11

Then what?

---

### Post by handaxe on 2007-04-04
Ok, There are some kernel security updates to come then, but they should not affect the card.

Issue a

```
sudo depmod -a
sudo modprobe ipw3945
```then:

```
lsmod | grep ipw
```This should produce output with ipw3945 in it, meaning the drivers are loaded.

If nothing, then we must investigate that separately.

Assuming the above is ok.  Please type:

```
sudo lshw -C network

sudo ifconfig

sudo iwconfig
```These should show you, among others eth1, which is the network card and outputs related to the presence of a signal from the wireless AP.

lets see...

HA

---

### Post by handaxe on 2007-04-04
Sorry, [I]I was inattentive;  you need :

linux-restricted-modules-2.6.17-11-generic

the 2.6.17-11 bit must match your current kernel.

Find that by
:
[/I]```
uname -r
```[I]

HA
[/I]

---

### Post by nlooie on 2007-04-04
Mine 2.6.17-10

And when i type the commands i get a lot of information. 

My Eth1 says: unassociated ESSID: off/any, and some other stuff.

You have any idea?

Im at work now so im not replyind right now. But later today. Thanks.

---

### Post by nlooie on 2007-04-04
And what should i do with my kernel, when it is 2.6.17-10 and not 2.6.17-11?

---

### Post by handaxe on 2007-04-04
In Synaptic, the reload button should provide a list of updates.  Install those.  That should get you up to date.

HA

PS Will write some basic instructions on connecting if you need.

What are you connecting to in terms of encryption type - wpa, wep etc.

Also post if you can the outputs of those commands ifconfig etc, just so we can be sure that you are ok.

---

### Post by handaxe on 2007-04-04
Ok, seeing the output would have been good, but I assume that your card is up and running.

Now to the connection part:  

You can configure the card by using menu System -> Administration -> Networking, selecting your wireless card, then properties and checking the tick box "Enable this connection"

This will set up entries in a file /etc/network/interfaces. Go and check this in gedit if you will. You should see the following:
```
 auto eth1
iface eth1 inet dhcp
```You should be good to go for an open AP or a wep encrypted one, using the networking administrator. The following link is good on wep in the event of trouble [http://www.ubuntuforums.org/showthread.php?t=172810&page=2](http://www.ubuntuforums.org/showthread.php?t=172810&page=2)

Should you want wpa and other encryption under network administration, the following link refers:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

There are some network manager applications that considerably ease the use of wpa encryption and roaming between APs and handle wep as well.

There is **Network-Manager** (check in Synaptic for Gnome and Kde versions). This is the official Ubuntu manager in effect, as it is pat of the standard install in the next version Feisty Fawn. One thing to remember about Network-Manager on Edgy (6.70) - you HAVE to comment out all references to your wireless interface in /etc/network/interfaces for N-M to work.  Also, do not try wireless in N-M whilst linked to a wired connection.

There is also **Wicd**, obtainable at 
[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

There is a deb install (gdebi should run when you click on the downloaded deb file). Also installs a tray icon BUT does not put an entry is startup. You do that by going to "System" "Preferences" "Sessions" "Startup Programs" and enter /opt/wicd/tray-edgy (if using Edgy) or /opt/wicd/tray-dapper (Dapper).

I use Wicd and have an ipw3945. That does not mean you should use Wicd in preference to N-M. Perhaps try both, see which you like best.  Best not to run both at the same time. Install, try, uninstall, install the other.

Hope this helps,

HA

---

### Post by nlooie on 2007-04-04
I got it working now, after i updated the kernel and installed network manager gnome. Thank you very much for helping :)

---

### Post by handaxe on 2007-04-04
Good news!!! - have fun and be productive or just have fun.....=D>

HA

---

