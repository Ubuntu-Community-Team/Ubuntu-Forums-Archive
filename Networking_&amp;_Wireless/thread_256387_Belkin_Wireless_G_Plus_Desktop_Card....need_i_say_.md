---
title: "Belkin Wireless G Plus Desktop Card....need i say more?"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by linuxnoob20 on 2006-09-12
ok. ive tried with other versions of linux alittle here and there and now im tryin ubuntu. ive been jumpin around versions cuz i cant get this thing to work at all. i cant even install ndiswrapper cuz the 'make' command doesnt work...even as root. ive been readin up on this a lot and i saw somethin bout an update i need to get or somethin...good luck to me tryin to get it without an internet connection in ubuntu. i also downloaded wine but i saw that it doesnt really do anything with driver installs,and it prob wont install itself without the make command. all i want is internet when i boot into linux...thats all. it would make it seem so much better to me if i could look things up there instead of having to restart and go into windows first. anyways,any suggestions?

---

### Post by majesticturkey on 2006-09-13
You can add the CD as a repository, and install build-essentials through Synaptic. That will let you use the make command. Then you can build ndiswrapper and all will be fine.

---

### Post by linuxnoob20 on 2006-09-13
thx. i did it alittle differently but i got make and ndiswrapper installed. but now i have no idea what to do as far as installing the .inf file. i did what the instructions said and it came out with an error. it said it was installed but i didnt notice any change anywhere. it said it couldnt do anything with inf files or somethin. i know im bein vague...cant remember what it said exactly.

---

### Post by mckooiker on 2007-10-21
First of all I advise you this tutorial/Documentation: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")
If that did not work try this......

This is how I got my Belkin Wireless G Plus Desktopcard (G+ 802.11g) working. For me it worked on Ubuntu 6.10, 7.04 and 7.10.

If you do not have exactly the same card it might be wiser to find some other "tutorial". Also other Linux-distributions might not work like this and I do not guarantee good results. However since this wireless card drove me mad when I first tried it, I would be happy if this ''tutorial could help some of you (even one would be fantastic!!).

**1)** The first thing to do is to get ndiswrapper on your computer. This is present on the cd from which you installed Ubuntu. In my case I installed ndiswrapper-common and ndiswrapper-utils-1.9.
I installed it with the synaptic package manager(system-->administration-->synaptic package manager), but you can also install it from within the terminal using sudo apt-get install [package-name].
**2)** Second: insert your Belkin cd and copy the three driver files on your desktop (Files-->Drivers-->WINXP2K). (files are BCM43XX.CAT, BCMWL5.INF and BCMWL5.SYS).

**3)** Now lets check some settings, go to the terminal and type the following line:

[COLOR="Red"]**iwconfig**[/COLOR]

this should return something like: 
lo	no wireless extentions
eth0	no wireless extensions
eth1	IEEE 802.11g *******
	*****etc.
You could also lack the eth0 or have it inverted. Anyways, remember the one that says IEEE 802.11g (in this case I remember eth1)

**4)** Next, check the pci-bus the wireless card is using, go to system-->preferences--> Hardware information
search your wireless card BCM4318[AirForce..]....
Click on the submenu WLAN Interface.
In my case I see a few times pci_14e4_4318 somewhere in the right panel, but in your case it could be another number.
Just write down the number following pci_ substituting the underscore with ':'. In my case: 14e4:4318

Now we can start:

**5)** Ubuntu comes pre-installed with a driver that does not work, therefore you will have to blacklist this driver sooner or later in the protocol (will prevent the driver from loading on the next start-up). I start with it right away, type the following in the terminal (Applications-->Accessories-->terminal):

[COLOR="Red"]**sudo gedit /etc/modprobe.d/blacklist**[/COLOR]

after entering your root password a text-file will open. Add the folowing at the bottom of the file:

[COLOR="Red"]**blacklist bcm43xx**[/COLOR]

save and close file.

**6)** Now load driver in ndiswrapper:
type in the terminal:
[COLOR="Red"]**ndiswrapper -i /home/[username]/Desktop/BCMWL5.INF**[/COLOR]

(take care, the folder name Desktop is not the same as the folder name desktop, so take care of lowercase/uppercase letters!).

[COLOR="Red"][B]ndiswrapper -d 14e4:4318
ndiswrapper -m[/B][/COLOR]

**7)** unload the preinstalled driver that is not working

[COLOR="Red"]**sudo rmmod bcm43xx**[/COLOR]

**8)** Turn on the wireless card (a LED on the wireless card should turn on right after you press Enter!!)

[COLOR="Red"]**sudo modprobe ndiswrapper**[/COLOR]

**9)** Add ndiswrapper in the modules that will be loaded on start-up:

[COLOR="Red"]**sudo gedit /etc/modules**[/COLOR] (a text file should open)

write "**[COLOR="Red"]ndiswrapper[/COLOR]**" at the bottom of the file, save and close.

**10)** Setup your network by going to System-->Administration-->Network
Click on "Wireless Connection" and then "properties"
Disable roaming mode and enter the right network name, encryption and password. (if your wireless network is encrypted)
configuration is probably automatic (DHCP).

If you can not connect to the internet at this moment try to restart the system, if it does not work check the wireless settings (step10).
If it still does not work you're probably as frustrated as I was!! let me know and I will try to help you!

Some troubleshooting (from the terminal):
[COLOR="Red"]**ndiswrapper -l**[/COLOR]

This should return something like this:
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
If not, ndiswrapper did not load and/or install properly
In this case try removing driver from ndsiwrapper: [COLOR="Red"]**ndiswrapper-r bcmwl5**[/COLOR] and restart from step 6. If you encounter any errors before arriving at the end try to resolve these errors and do not continue before you resolved the problems!

---

### Post by AtomBombCalamari on 2007-10-23
ok Im really new at Linux and Ubuntu... I didnt want to register and post a  reply, but i just cant figure this out, so here i am. 

Ive gone through quite a few tuts on how to make this work and im at that frustrated level you're talking about. 

I blacklisted bcm43xx. I've got the bcmwl5.inf installed. it's set to the 14e4:4318 card in ndisrapper. however in the wireless driver manager it shows that the hardware is not present for that driver in there. then in ndis wrapper -l i get the normal output. bcmwl5 : driver installed
device (14E4:4318 ) present (alternate driver: bcm43xx) 

...and everything else(modprobe, rmmod, etc.) in your tutorial and everyone else's. the only thing that doesn't look right is the hardware not showing up in that gui. do you know what's wrong here?

Edit:
ok so I switch back into ubuntu to disable the bcm43xx-fwcutter firmware that comes with gutsy. I forgot to mention that i tried that too. well it doesn't work and i disabled it. still no connection. However I looked at the Windows wireless drivers again and it says the hardware is present. So actually nothing looks like it is wrong, but still no connection. I moved my computer closer to the router for a while yesterday to download some things on the wired and it works fine. I really have no idea what is going on.

---

### Post by mckooiker on 2007-10-30
Ok, since I went through the same trouble I will not rest before you managed to get that d*md*d wireless card working.
I am not a guru, but I hope that I will be able to help you.

Good thing you tested the card on windows, So we know it is inserted in the right way, and it should be functional. Double check: your wireless card is present in the list you can find at System-->preferences-->hardware Information ?

If I remember well, I firstly got the connection after having removed my Lan-card. ubuntu was searching for a wireless card in eth0, whereas my wirless card was on eth1 (or something like that).

Ok, can you post the contents of "[COLOR="Red"]iwconfig[/COLOR]" (typed in the terminal)?
and can you also post the contents of the file /etc/network/interfaces [in terminal type:[COLOR="Red"]gedit /etc/network/interfaces[/COLOR]]

---

### Post by AtomBombCalamari on 2007-11-03
iwconfig:
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:32 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ifconfig:
eth0 Link encap:Ethernet HWaddr 00:11:5B:63:85:81
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:16 Base address:0xa000

eth1 Link encap:Ethernet HWaddr 00:11:50:62:3B:44
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:21 Memory:fa000000-fa002000

eth1:avah Link encap:Ethernet HWaddr 00:11:50:62:3B:44
inet addr:169.254.4.24 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:21 Memory:fa000000-fa002000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1789 errors:0 dropped:0 overruns:0 frame:0
TX packets:1789 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:173629 (169.5 KB) TX bytes:173629 (169.5 KB)

ndiswrapper -l
bcmwl5 : driver installed
device (14E4:4318 ) present (alternate driver: bcm43xx)

So it looks like it should be working to me. The System>Admin>Network gui has the wireless checked, no other connection checked, and the properties for the wireless are not roaming(i have my network and password punched in.) if i try to do roaming no networks can be seen.(there are at least 5 at all times in windows) The gui in the DNS tab shows two dns severs that look like the right ones, and i didnt enter those, it retrieved them itself. When I try to open a browser it doesnt give the page couldnt be loaded. It just says looking for [www.google.com](www.google.com) or whatever address i enter. and never loads or eventually times out.

---

### Post by mckooiker on 2007-11-05
try this: make a copy of your interfaces file:
[COLOR="Red"]**cp /etc/network/interfaces /etc/network/interfacesbackup**[/COLOR]

change file: [COLOR="Red"]**sudo gedit /etc/network/interfaces**[/COLOR]
and paste the following into your file (changing *** into your password and network name into the name of your network: 

[I]auto lo
iface lo inet loopback

iface eth1 inet dhcp
-essid **network name**
- key ***************************
wireless-key ***************************
wireless-essid **network name**
auto eth1[/I]

safe and exit
After this you might need to restart......Hope this will work!

---

