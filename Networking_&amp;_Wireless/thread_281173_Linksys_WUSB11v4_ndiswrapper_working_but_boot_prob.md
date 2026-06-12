---
title: "Linksys WUSB11v4 ndiswrapper working but boot problem"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by MightyMouse on 2006-10-20
Hi,
I have just configured my Linksys WUSB11v4 USB wireless adapter with ndiswrapper and evrything is working fine, except that I have to run the entire iwconfig, modprobe ndiswrapper dmesg |grep wlan routine + deactivating, then reactivating my wlan0 device in System/Networks every time at start up. 
I did runs sudo ndiswrapper -m when I had set up everything and I do have the wlan listed in my /etc/network/interfaces file
--------------------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet dhcp
wireless-essid xxxxxxx
wireless-key xxxxxxxxx

auto wlan0
--------------------------------------------------
I also have a file ndiswrapper in /etc/modprobe.d which looks like this:
--------------------------------------------------
alias wlan0 ndiswrapper
--------------------------------------------------
And I have added a line to /etc/modules:
--------------------------------------------------
# /etc/modules: kernel modules to load at boot time.

#This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper

----------------------------------------------------
So why on earth doesn't it work? I must be missing something. I really hope someone can point out the flaw in my approach. It is rather annoying to have to type all this stuff every time I start Ubuntu. And even if I would make an excecutable I still would have to deactivate/activate the wlan every time?!:confused: 

Thanks for any help.

Anja:confused:

---

### Post by wieman01 on 2006-10-20
I assume you had done a..,.
> sudo depmod -a
...before modprobing "ndiswrapper"?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Please tell us what you have done step by step so that I can figure out what step you have been missing.

---

### Post by MightyMouse on 2006-10-21
Ok, 
I definetly did a sudo depmod -a at one point, but after that I have changed the channel on my AP and run ndisrapper -m several times without depmod -a before I got the network up.
I did the following just now but after shuting down I still have the same problem.](*,) 

anja@Maus2:~$ sudo ndiswrapper -l
Installed ndis drivers:
wusb11v4                driver present, hardware present
anja@Maus2:~$ sudo depmod -a
anja@Maus2:~$ sudo modprobe ndiswrapper
anja@Maus2:~$ sudo iwconfig wlan0 mode managed
anja@Maus2:~$ sudo iwconfig wlan0 key restricted xxxxxxxxxx
anja@Maus2:~$ sudo iwconfig wlan0 essid XXXXXX
anja@Maus2:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

Is there any way I can "clean" up everything and start from scratch? I guess I do know now how to do it correctly but get the impression that I cannot change the excisting settings any more.
So if I could start from installing my driver in a clean ndiswrapper I should be ok. Any suggestions how I could do this? Or can I still "rescue" the installation as it is now?

Thanks for your help, 
Anja
:-k

---

### Post by wieman01 on 2006-10-21
Hi, 

You can fire up Synaptic, then right-click on the package, and choose "Mark for Complete Removal". This will eliminate all config files as well.

I recommend you to follow the guide I posted step by step. Have used on a number of occasions & it has seldom failed me so far. Let us know how that goes.

---

### Post by MightyMouse on 2006-10-26
Just a short one. It seems I have to blacklist a driver (and if I remember correctly doing this was also the trick with my Labtop's wireless). How can I see which drivers are loaded during boot, or to be more precisely which driver is attempting to run the wirelss device?

Thanks

---

### Post by wieman01 on 2006-10-26
_**EDIT:**_
This one is Ralink based and should also be working out of the box. I found the Ralink Linux driver pretty lousy, in particular with regard to encryption, so I cannot recommend it. I am using "ndiswrapper" together with my WUSB54G & it works like a charm (WPA2 - AES).

To blacklist the driver, it's probably this one:
> echo 'blacklist **[COLOR="Red"]rt2570[/COLOR]**' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by az on 2006-10-26
> **wieman01 said:**
> Hi, 

I am not 100 sure but I believe it is the driver: [COLOR="Red"]**"at76c503"**[/COLOR]

_Blacklisting it:_

Reference: [http://at76c503a.berlios.de/]("http://at76c503a.berlios.de/")

That device works out-of-the-box.

To find out what chipset it is, boot, open a terminal and runà

tail -f /var/log/messages

and then plug in your device.  Post the output here.

---

### Post by wieman01 on 2006-10-26
> **azz said:**
> That device works out-of-the-box.

To find out what chipset it is, boot, open a terminal and runà

tail -f /var/log/messages

and then plug in your device.  Post the output here.
Made a mistake, wrong driver I mentioned... The version 4 does not work out of the box as far as I know. I know the previous versions did, but apparently NOT this one. Or am I mistaken?

_**EDIT:**_
Have edited the other post.

---

### Post by MightyMouse on 2006-10-27
Well it definetly didn't work out of the box!

I will try the tail -f /var/log/messages and put the output here (still at workso probably sometime this weekend)

Thanks

---

### Post by MightyMouse on 2006-10-29
Hmmm, very interresting

if unplugged then no driver is loaded, the var/log/messages looks like this

Oct 29 17:06:05 localhost gconfd (anja-4779): starting (version 2.14.0), pid 477 9 user 'anja'
Oct 29 17:06:05 localhost gconfd (anja-4779): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct 29 17:06:05 localhost gconfd (anja-4779): Resolved address "xml:readwrite:/h ome/anja/.gconf" to a writable configuration source at position 1
Oct 29 17:06:05 localhost gconfd (anja-4779): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct 29 17:06:05 localhost gconfd (anja-4779): Resolved address "xml:readonly:/va r/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct 29 17:06:05 localhost gconfd (anja-4779): Resolved address "xml:readonly:/va r/lib/gconf/defaults" to a read-only configuration source at position 4
Oct 29 17:06:07 localhost kernel: [17179610.872000] NET: Registered protocol fam ily 10
Oct 29 17:06:07 localhost kernel: [17179610.872000] lo: Disabled Privacy Extensi ons
Oct 29 17:06:07 localhost kernel: [17179610.872000] IPv6 over IPv4 tunneling dri ver
Oct 29 17:06:08 localhost gconfd (anja-4779): Resolved address "xml:readwrite:/h ome/anja/.gconf" to a writable configuration source at position 0

which is exactly the same as with the device plugged in with the exception of these lines

Oct 29 16:55:24 localhost kernel: [17179760.956000] usb 3-2: new full speed USB device using uhci_hcd and address 2
Oct 29 16:55:24 localhost kernel: [17179761.140000] ndiswrapper: driver wusb11v4 (Cisco-Linksys LLC.,05/13/2004, 3.110.0513.2004) loaded
Oct 29 16:55:26 localhost kernel: [17179762.724000] wlan0: vendor: 'M4301 NDIS Miniport Driver'
Oct 29 16:55:26 localhost kernel: [17179762.724000] wlan0: ndiswrapper ethernet device 00:0f:66:e9:1a:71 using driver wusb11v4, 13B1:000B.F.conf
Oct 29 16:55:26 localhost kernel: [17179762.724000] wlan0: encryption modes supported: WEP; TKIP with WPA

which suggests that ndiswrapper is properly loaded at start-up!!!!

Still I have to run the following in a terminal to be able to connect to the internet
sudo modprobe ndiswrapper
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key restricted xxxxxxxxxx
sudo iwconfig wlan0 essid NAMEESSID

(with xxxxxxxxxx obviously my hexadecimal code and NAMEESSID the name of my Ap)

I am a little confused, I would have expected to see some other driver being loaded and preventing the ndiswrapper driver to take over but this doesn't seem to be the case.

I get the impression that complete removal of ndiswrapper is not going to make this problem go away.
I also notice that when I open the Networking tool no device is chosen as default. But changing it to wlan0 wont start up the internet connection nor does deactivating/activating wlan0. Only running the commands above get me on the net.

Could I make a .sh from this? I am not so good at this kind of stuff, but if I am correct I could create a little executable form this, couldn't I?

Thanks, Anja

---

### Post by wieman01 on 2006-10-29
To load the module "ndiswrapper" at startup, do this:
> sudo ndiswrapper -m
This basically adds a line to "/etc/modules".

Second, you don't need to run the other commands for authentication/encryption manually. This file controls your network interfaces:
> sudo gedit /etc/network/interfaces
Please post the contents of this file & tell us a bit more about your network e.g. ESSID, WEP (encryption), DHCP vs. Static IP, etc. Then we'll edit the file accordingly so that your network gets configured at startup.

---

### Post by wieman01 on 2006-10-29
Last thing: I am not sure what "key restricted" means but if this is referring to WEP, please make sure that your router uses a 128-bit key because I know what 64-bit keys can be a problem sometimes.

And yes, "ndiswrapper" is probably the best option for your card. I have a WUSB54G V4 & the native Linux driver would not work at all.

---

### Post by MightyMouse on 2006-10-29
Hi

/etc/modules already looks like this
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper


/etc/network/interfaces looks like this

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet dhcp
wireless-essid Dierentuin
wireless-key xxxxxxxxxxxxxxxxxxxxx

auto wlan0

and I just switched to 128bit WEP, still no automatic start of my connection at start-up.

I have a Zyxel 660 modem, my ESSID is Dierentuin with radio on, I use DHCP, with 128bit WEP encryption, mixed mode 802.11 b+g, but this made no difference when I only used single mode b.

I am really curious what's wrong here. Especially since I got a prism card working with ndiswrapper on my Laptop and I can't find the difference in how I was setting it up because that one starts up automatically.

Cheers, Anja

---

### Post by wieman01 on 2006-10-29
This is a bit odd... If you don't mind let's write a little startup script & see if this does the trick. Of course that's just a temporary fix and workaround but at least you get rid of this annoying problem (hopefully) immediately.

1. Startup script:
> sudo kate /etc/init.d/networking_with_ndiswrapper
2. Paste this:
> sudo modprobe ndiswrapper
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key restricted [COLOR="Red"]xxxxxxxxxx[/COLOR]
sudo iwconfig wlan0 essid [COLOR="Red"]NAMEESSID[/COLOR]
3. Making the file executable:
> sudo chmod +x /etc/init.d/networking_with_ndiswrapper
4. Creating symbolic link:
> cd /etc/rcS.d/
sudo ln -s /etc/init.d/networking_with_ndiswrapper [COLOR="Red"]S40[/COLOR]networking_with_ndiswrapper
Then restart the computer. Please check that [COLOR="Red"]S40[/COLOR] is a number that comes after or is the same as "[COLOR="Red"]Sxx[/COLOR]networking" in folder "/etc/rcS.d/". The number determines the boot sequence & you don't want to run this script before the network has been brought up.

Let us know how you go... As said, this is a fix, no real solution... But it may do the job for now.

---

### Post by MightyMouse on 2006-11-02
Hi wieman01,
worked like a charm, and even if it is not the "real" solution at least now I have Internet without having to type in all the stuff by hand!

Thanks, a lot!

Cheers, Anja

---

### Post by wieman01 on 2006-11-02
You're welcome. I know this is not the most ideal solution but then again, it works. I guess we have other more important things to do. :-) And rest assured, you are not on your own.

See you next time...

---

### Post by wieman01 on 2006-11-02
There is another solution you could give a try... I have the same problem on my laptop PC (IPW2200 wireless) despite the fact that my desktop PC is fine. I need to restart my network every time I boot the PC otherwise the wireless adapter won't associate. 

The solution is to add a startup script that restarts my network while booting. The approach is the same but it looks slightly better:

_Create startup script:_
> cd /etc/init.d/
sudo gedit wireless-network.sh
_Add 1 line & save file:_
> /etc/init.d/networking restart
_Change permission (executable):_
> sudo chmod +x wireless-network.sh
_Create symbolic link:_
> cd /etc/rcS.d/
sudo ln -s /etc/init.d/wireless-network.sh **[COLOR="Red"]S40[/COLOR]**wireless-network
[Note: You may have to choose a boot sequence other than **[COLOR="Red"]S40[/COLOR]**.]

---

### Post by tbg58 on 2006-11-06
Thanks very much for posting the work-around script.  It worked like a charm on my old Dell notebook.

I understand there's a compatibility issue between the Edgy kernel and NDIS, and that DHCP sometimes gives problems as well.

My own experience was that as long as I took WEP off of my access point, the Edgy notebook would log in fine.  When I added WEP, no amount of finagling with the GUI tools or interfaces file would get it to hook up.

Even in Dapper my WEP key did not get picked up automatically and had to be re-entered with each reboot, but I suspect that adding a colon between each two characters of the key in /etc/networking/interfaces would probably have solved the problem.

In any case, thanks for the work-around script -- it worked fine, and I'm able to roam with my notebook once more, even if I'll have to manually edit the script when I travel.

Kindest regards & once more, thanks.

Dex

---

