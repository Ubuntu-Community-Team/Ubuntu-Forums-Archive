---
title: "[SOLVED] Router connection"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by miki85 on 2007-09-25
first i want to open by saying, i looked at previous threads and wasn't able to find a solution to my problem :(

i installed ubuntu and as an xp user i'm used that windows automatically recognize the Network adapter and the connection brought by the router(wired).

been trying for a week now and i just dont seem to get in to the internet that easilly...

i saw in some previous questions that one asked for IFCONFIG output so maybe it will be of any help:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D3:CE:F8:6D  
          inet6 addr: fe80::213:d3ff:fece:f86d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D3:CE:F8:6D  
          inet addr:169.254.10.37  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2664 (2.6 KiB)  TX bytes:2664 (2.6 KiB)

---

### Post by SpiritIsReality on 2007-09-25
howdy
could you click on System > Administration > Network
(or do you have System > Administration > Networking)
click on the Wired Connection so it's highlighted.
then click on properties...and tell us what you've got there.
also info from the tabs General, DNS, and Hosts.  
info from
cat /etc/network/interfaces
is important too.
well I'm into this with not much understanding of what avahi is, but
> chili555
June 26th, 2007, 07:01 PM
Avahi assigns a 169.254.x.x IP address when a DHCP server can't be found or doesn't respond. Please try:sudo ifdown eth0 && sudo ifup eth0Let us know if you get an actual IP address and we'll troubleshoot a bit more.
from here
[http://ubuntuforums.org/archive/index.php/t-484904.html](http://ubuntuforums.org/archive/index.php/t-484904.html)

[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)
hardware not being recognized maybe?


trails

---

### Post by SpiritIsReality on 2007-09-25
howdy
I got this for commands on finding hardware, if it's recognized and all
[http://www.google.ca/search?hl=en&q=linux+ethernet+lspci+dmesg+grep&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+ethernet+lspci+dmesg+grep&btnG=Google+Search&meta=)
so it's
lspci
dmesg | grep eth0
dmesg | grep Ethernet

what else? There's something to get the product numbers of the device, have to look that
up..... later.


route -n
to view the current default route,
to see if the gateway is listed.
could try
sudo dhclient eth0
to see if we get a dhcp address from the gateway
ifconfig -a
shows UP and Running. supposed to be working.
but the avah says eth0 is not getting a proper address assigned.
could try setting a static ip address thru the System > Administration > Network
or with
ifconfig eth0 address netmask mask
route add default gw gw-address

can't find that command for the vendor and product numbers of hardware.
ahha!
[http://jbakshi.50webs.com/Linux_tutorial/Hardware_detection/Hardware_Detection.html](http://jbakshi.50webs.com/Linux_tutorial/Hardware_detection/Hardware_Detection.html)
lspci
lspci -b
lspci -n
lspci -d
lspci -s

---

### Post by miki85 on 2007-09-26
i think i got all you asked:
[http://img406.imageshack.us/my.php?image=screenshotcb8.png](http://img406.imageshack.us/my.php?image=screenshotcb8.png)
[http://img210.imageshack.us/my.php?image=screenshot1qj8.png](http://img210.imageshack.us/my.php?image=screenshot1qj8.png)
[http://img485.imageshack.us/my.php?image=screenshot2gr7.png](http://img485.imageshack.us/my.php?image=screenshot2gr7.png)
[http://img210.imageshack.us/my.php?image=screenshot3ru0.png](http://img210.imageshack.us/my.php?image=screenshot3ru0.png)

hope there's findings in it :confused:

---

### Post by SpiritIsReality on 2007-09-26
howdy
screenshots, way to go. ok, everything there looks fine.
doesn't hurt to check.
there be better round here, but let's see what we can come up with.
now we should look at
```
lspci
```
and
```
dmesg | grep eth
```
the | is, hold down the shift key, and type the \ key

if you post the info from those two commands, we can see if we
can find your NIC card chip manufacturer.
and see where we get to from there.

thanks

oh, I just found this yesterday.
when you're at the post reply page, typing a post, I scrolled down the page to the
heading additional options. there's a manage attachment button there. try that for screenshots.

sorry, connectin to ubuntuforums.org got dropped about half an hour ago and couldn't
reconnect to ubuntu.com or here till now.

---

### Post by miki85 on 2007-09-26
i brought back the results but one is txt coz' the output was longer then ScreenShot ... anything suspicious ?

---

### Post by SpiritIsReality on 2007-09-26
howdy
here's my lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
00:09.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

the Ethernet controller ...same as yours.

here's my dmesg | grep eth
[   53.714676] eth0: RealTek RTL8139 at 0xd8848000, 00:40:f4:85:ff:65, IRQ 11
[   53.714744] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   23.656000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   35.180000] eth0: no IPv6 routers present

I don't get the 
[   13.951512] eth0: RealTek RTL8139 at 0xf88d8000, 00:13:d3:ce:f8:6d, IRQ 16

[   13.951516] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

[   69.696119] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

[   99.610810] NETDEV WATCHDOG: eth0: transmit timed out

[  102.602015] eth0: Transmit timeout, status 0d 0000 c07f media 10.
of yours.

maybe we could disble the eth1 and eth2. I'll have to check how to do that in 
[http://help.ubuntu.com/community/WifiDocs](http://help.ubuntu.com/community/WifiDocs) I think that's where it is.
we're onto something I reckon.
the dhcp server can't be found. now why not. I don't think your ethernet card is at
fault because it checks out in lspci.

could you try, at the terminal
```
sudo dhclient eth0
```
to see if we get a connection?
til I get back

trails

---

### Post by miki85 on 2007-09-26
well it seems bad, but i dunno take a look ...

---

### Post by SpiritIsReality on 2007-09-26
howdy
that's definitely the problem.
not bad, just not workin' yet...haha!
I'm sorry you're having this trouble.
please don't get discouraged. I'm just not the guru that's needed here.
please don't give up on this gnu/linux. the problem is solvable!
just how.
I haven't found where to disable the other eht's yet, and I'm not sure if that's the fix.
is this computer a dual boot with microsoft?
if so, what does the ipconfig say in the terminal.
it's probably not the cable, or connections, but it could be.
or
can you try the ubuntu live cd on a different computer that you know connects to the internet?
it won't hurt the other pc to try it, and if it works, then we can look at the lspci,
ifconfig -a
route -n 
or
route -r 
have a look at what you can find.
could look at this to see others with the same problem and see what they did.
[http://www.google.ca/search?hl=en&q=avah+169.*&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=avah+169.*&btnG=Search&meta=)

could click on search, advanced search, keyword avah 169 , then search and see if
there's any with a [solved] mark on them.
I'll be back.....(it's not as bad as when MacArthur said that(paraphrase))

it's a blessing in disguise. we're not in the dark anymore, but sometimes the light seems like it's
at the end of a tunnel? seek and we will find. haha!
take her cool. this too shall pass.
trails

---

### Post by miki85 on 2007-09-26
hi, did what you said... i'm talking from another computer in the house that is connected to the internet through wireless connection to the router wired to my computer...

anyway here it worked great except one problem, it's my mom's comp' :(

hmmmmm.... well after we got that strait i'm going back to my computer to try the last few commands you gave me hoping it will unreveal the cause  (and affect) hopefully

---

### Post by miki85 on 2007-09-26
well now i think i know it's not from the network adapter but from somewhere else ...

while being in my moms comp' i got to remember that i had two other netcard in my closet...

tried them both... non of them worked... tried everything i can think of and no connection :(

is there a possibility that i need to do something in order to connect to the router?

even though it's the most unsecure one and no accounts or passwords... anything... but still
maybe there's a config of some sort i need to enter ?!

BTW it's: TP-LINK TL-WR541G

:confused:   :confused:   :confused:   :confused:   :confused:   :confused:   :confused:

---

### Post by SpiritIsReality on 2007-09-26
howdy
ok. hopefully you've got the same nic card in your computer now as we started with. if not could
you do that? we don't want to have too many unknowns here. we've got enough now. haha!
I got the default ip address of your router from here with the info you gave me. thanks.
[http://www.tp-link.com/support/showfaq.asp?id=20](http://www.tp-link.com/support/showfaq.asp?id=20)
8.     Open a web browser, type the default IP address 192.168.1.1 in the address bar and the default username admin, password admin to log in the web-based utility to configure your wireless router.

so that's good to know. because that's your default gateway address (router address)

this talks about the /etc/network/interfaces file
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

did this search
[http://www.google.ca/search?hl=en&q=disable+eth*+%2Fetc%2Fnetwork%2Finterfaces&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=disable+eth*+%2Fetc%2Fnetwork%2Finterfaces&btnG=Google+Search&meta=)
found this
[http://ubuntuforums.org/archive/index.php/t-174809.html](http://ubuntuforums.org/archive/index.php/t-174809.html)
mpvano has a good explanation of what we're working on.
and medya says to make sure the auto eth0 line is first in the file....hayyy!!

look at your /etc/network/interfaces file....auto eth0 isn't the first line...!

ok. we'll try to fix that.


so, at the top of the screen, click on Applications > Accessories > Terminal
to get a terminal.
in the terminal, type, or copy and paste. If you don't know how to copy and paste, ask me.
```
gksu gedit /etc/network/interfaces
```
and press enter.
(enter your password in the window that asks for it, and press enter, or click OK.)
on live cd, no password is asked for.
now you should see your /etc/network/interfaces file in the gedit(text editor) window.
(the eth0 is a eth(zero) , you can tell because of the dot in it.)

make your /etc/network/interfaces file in the window look like this
> 

auto eth0
iface eth0 inet dhcp

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

you can copy and paste this into your file if you like.
we put a # sign in front of the lines we want ubuntu to ignore.

then click the Save icon at the top of the window.
then click File, then click quit.

are you using the ubuntu live cd?
if so, then in the terminal, type
```
sudo /etc/init.d/networking restart
```
press enter
and see if you can get out to the internet with firefox.
if firefox can't connect , try this in the terminal
```
sudo ifdown -v eth0
```
press enter
```
sudo ifup -v eth0
```
press enter
```
dhclient eth0
```
press enter and
try firefox again.

if you have ubuntu installed on your hard drive, then maybe you
could restart your computer, just for good measure, and see if you
can get to the internet with firefox.

maybe you could print this post out so you can take it with you to your 
computer

if it doesn't work, don't get disappointed, we'll try giving your computer
a static ip address then, and see if that works.

edit :good advice from Pumalite on this forum, is to get a Knoppix live cd.
[http://www.knoppix.org/](http://www.knoppix.org/)
click on your language flag
click on download
click on bittorrent if you know how to do that. or
click on http like here for instance
ftp.uni-kl.de	[rsync][rsync dvd]	[ftp]	[color=red][http][/color]	Technische Universität Kaiserslautern 
read paragraph, click on accept
the two files we're after are
  
[   ] KNOPPIX_V5.1.0CD-2006-12-30-EN.iso          30-Dec-2006 23:28  698M  
[   ] KNOPPIX_V5.1.0CD-2006-12-30-EN.iso.md5      30-Dec-2006 23:30   69   

click on the first one to download the iso.
click save to disk. save where you want.
click on the second to download the md5sum.
save to disk.
once the file has finished downloading, the directions here can be used to
burn the image to disk.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

try this knoppix live cd on your pc. See if you can get to the internet with it
with firefox.
does your computer have windows xp installed?
can you get to the internet when running it?
there's good screencasts (videos) about ubuntu at
[http://screencasts.ubuntu.com](http://screencasts.ubuntu.com)
try scrolling down the page to installing ubuntu part 1.
click on the video picture, right click on file, click on save link as..., then
right click the icon, open (play)
and dual-boot install with windows
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

catch you on the rebound, pard.

trails

---

### Post by miki85 on 2007-09-27
i removed all the other network adapters and gone back to the one we started with!

i was running on live cd, did the "interfaces" file changes, did all the
commands after it and nothing changed.. so i took one step forward and installed ubuntu successfully... then changed the file again this time as you said i got promped with the password... but after save and restart still nothing :(

i got the knopix STD Live CD so i placed it in the tray and booted... no luck there too...

only thing i keep seeing is that the damn LED on the back of the network card is off and get turned on only when windows starts... hmm but why is that ?!... btw the ip you've got 192.168.1.1 is the routers IP and  i tried calling it from FireFox but no response... probably i'm stuck from software to hardware because the net card led is off and i even cant reach the router :confused:

i just want to say thank you for the patience so far and that i'm willing to try anything just that it will get me connected through ubuntu ...](*,)

waiting for more suggestions ..

---

### Post by SpiritIsReality on 2007-09-27
howdy

> only thing i keep seeing is that the damn LED on the back of the network card is off and get turned on only when windows starts... hmm but why is that ?!... btw the ip you've got 192.168.1.1 is the routers IP and i tried calling it from FireFox but no response... probably i'm stuck from software to hardware because the net card led is off and i even cant reach the router
good observation. I'm with you on that one. 
I haven't had any trouble with nic cards so I don't even know if there's an led on it.
yep, just checked and it's on. 
and you can get to the internet with windows.
and I don't get all those eth's in /etc/network/interfaces, just the one eth0 and the lo loopback.
one thing I noticed is that on I think it's...I'll check...and post back...
that your nic was on irq 16 and the nic here said irq 11.
I'm wondering if there's a conflict of bus's or whatever's.
gonna have to check on that too.

catch you in ten.

---

### Post by SpiritIsReality on 2007-09-27
ok
here's yours
> ubuntu@ubuntu:~$ dmesg | grep eth

[   13.951512] eth0: RealTek RTL8139 at 0xf88d8000, 00:13:d3:ce:f8:6d, IRQ 16

[   13.951516] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

[   69.696119] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

[   99.610810] NETDEV WATCHDOG: eth0: transmit timed out

[  102.602015] eth0: Transmit timeout, status 0d 0000 c07f media 10.

[  102.602022] eth0: Tx queue start entry 4  dirty entry 0.

[  102.602029] eth0:  Tx descriptor 0 is 00082156. (queue head)

[  102.602033] eth0:  Tx descriptor 1 is 00082156.

IRQ 16

my dmesg | grep eth says:
[    7.960000] eth0: RealTek RTL8139 at 0xd8850000, 00:40:f4:85:ff:65, IRQ 11
[    7.960000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   23.460000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.240000] eth0: no IPv6 routers present

IRQ 11

but...more importantly I think we should have a look at these searches and see what we
can find. from your dmesg,
if you right click on these links, and click on open in new tab. then you can get back here easier.
if you happen to close a tab and wish that you could have it back. click History, top of firefox,
scroll pointer down to Recently Closed Tabs. What a saver that is sometimes..

 a search for:
 NETDEV WATCHDOG: eth0: transmit timed out
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+NETDEV+WATCHDOG%3A+eth0%3A+transmit+timed+out&as_q=rtl&btnG=Search%C2%A0within%C2%A0results](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+NETDEV+WATCHDOG%3A+eth0%3A+transmit+timed+out&as_q=rtl&btnG=Search%C2%A0within%C2%A0results)
Transmit timeout, status 0d 0000 c07f media 10
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Transmit+timeout%2C+status+0d+0000+c07f+media+10&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+Transmit+timeout%2C+status+0d+0000+c07f+media+10&btnG=Google+Search&meta=)
haha! recognize those hombres?! so I opened that up to linux
[http://www.google.ca/search?hl=en&q=linux+%22Transmit+timeout%2C+status+0d+0000+c07f+media+10%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+%22Transmit+timeout%2C+status+0d+0000+c07f+media+10%22&btnG=Google+Search&meta=)

let's have a look around and see what we can find out.
fire three shots...I mean post back here if you find anything we should look at.
if you get to a site we should look at. then highlight the address in the address bar at the top
of firefox, hold your mouse pointer at just to the left side of the http:// , until it turns into an
I looking  pointer, then hold down the left button, drag it to the right until the scrolling quits or
you reach the end of the address. 
the address should be highlighted now. then let up on the left button. the address should
still be highlighted. right click on the highlighted address, click on copy.
click on the tab for this page, click on post reply, then left click in the window, to get a I looking
cursor. right click the cursor, click copy, and bang. then hit enter key to get to the left side of
the window again. 

trails

---

### Post by SpiritIsReality on 2007-09-27
BLAM ! ....BLAM ! ....BLAM !

check this out pard.
[http://www.google.ca/search?as_q=NETDEV+WATCHDOG+eth0+transmit+timed+out+rtl&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=NETDEV+WATCHDOG+eth0+transmit+timed+out+rtl&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
I'm goin' back to have a closer look.

edit : got to here on the link that noob12 gives in post #11
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
then the link to gentoo
[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)
have a look see. 
Kernel installation > Troubleshooting.
> 
Troubleshooting

As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)

Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.

Third edit: 2.6.22.4 still cannot power up the NIC. 

****try that second edit :Second edit: Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.
****what do you think? worth a try?

edit : quote of noob12 from here
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
>  Re: HOWTO FIX no link detected Realtek 8168/8169 cards
This fix will only work for the specific problem whose symptoms are described here; everything will look right (you'll see the interface in ifconfig -a) but ethtool will show that you don't have a link detected, and the shutdown/unplug test will solve the problem. If the shutdown/unplug test didn't work for you, you probably have a different problem. If you post a new thread with the details and PM me, I'll try to help you.

trails.

---

### Post by noob12 on 2007-09-27
Sorry to butt in.  

Consider booting with the option **pci=noacpi**  .  See if that helps.  I've attached instructions.

**Instructions for one-time boot flag entry**

When booting you'll normally see grub flash a menu of boot options up for a little while.  While it is up  with the default selection highlighted, press **e**, then use arrow keys to navigate to the line that starts with **kernel** and hit **e** again to edit it.  Put the flags at the end of the line, separated from each other and from prior material on that line by space or spaces.  Hit Enter to accept, then b to boot.

To confirm you got the flags entered properly, you should see them if you type
```

dmesg | grep 'Kernel command line'

```
after you boot.

The flags will only apply to that one boot.  If this helps, I'll tell you how you can make it permanent.

---

### Post by miki85 on 2007-09-27
noob12 , i'm sorry but i havent understood what to do :(
if you can explain bit slower.. sorry complete noob...
and i dont have a boot menu i insert the cd and choose boot from second hard drive or something like that (the last option) and then click on ubuntu to run it..

..fmat , one of the links you sent said that i should try to turn off the comp and unplug the net cable...wait 15 sec' and boot stright to ubuntu... going to try it, maybe it is a bug in the net-card ... even though we tried other cards, it still worth a try

---

### Post by miki85 on 2007-09-27
oops, now that i read the end of the post that's exactly what you told me todo...
but anyway i'm off to try it :)

---

### Post by SpiritIsReality on 2007-09-27
noob12 ... please do by all means...thankyou...ps. was planning on asking miki85 to contact you
and possibly vote on your post

miki85 ...no oops necessary, that's me messin' around with the edit. I didn't think anybody else
was around....my bad.

waiting and a watching.

---

### Post by miki85 on 2007-09-27
well i came back from the shutdown\unplag... not even a sign of life...
on the way i tried pressing e' on serval places and i found the menu with the kernel and pressing e again opens a command line of some sort or that is the edit ? idunno but no metter where i got i still dont understand what you said about the flags (what are they?) and what to change there so there was little i could have done there ... if you could explain a little bit more i'm sure i'll be able to execute it properly...

---

### Post by SpiritIsReality on 2007-09-27
howdy
I can try to help til/if noob12 gets back.
I've not done that boot from hard drive using the live cd, but I've seen it mentioned on the screencast.
if you can get back to where you see a menu, that mentions kernel by pressing the e,
leave it like that and post back here.

trails

---

### Post by miki85 on 2007-09-27
well it's kind of a problem because it's on the same computer so if i'm there i cant post...

i'm sorry but i have to go to sleep but i'll be here tomarrow hopeing you will too and if you have any ideas please leave them here and i'll do each one first thing in the morning ... nighty night, Zzz...

---

### Post by SpiritIsReality on 2007-09-27
ok

[COLOR=red]edit : please go to post #27 now[/COLOR] 
edit : then #26.
if no go, come back here and try this?

you could print this post so you can follow this when you reboot.

I used the live cd.
chose boot from the first hard drive.
pressed enter key.
when black screen with white lettering flashes on the screen,
it says something like a count down 3..2..
and says to see the menu,  press the Esc key in so many seconds. yours may be different.
once the Esc key is pressed, the menu shows.

No hurry any more, we can take our time now. the menu shows :
root (hd_,_)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=BigLongNumber888 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

or something similar, then...

use the arrow keys to get the line that starts with the word kernel, highlighted, lit up.

now when the kernel line is lit up, press the e key.

when you've pressed the e key, you get a screen that says something like
grub edit> kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=BigNumer888 ro quiet splash
I had a <-number ro quiet splash

the cursor should be blinking in just the right place to type
pci=noacpi 

type that at the end of the line with a single space between the word splash
and the pci=noacpi so it looks like this
<-number ro quiet splash pci=noacpi

press the enter key
press the b key
the pc should boot.

once you've booted, check if you can get on the internet with firefox.
also, if you could open the terminal and type:
```
dmesg | less
```now you can use your up and down arrow keys to scroll thru this.
and when you've had all you can stand of it, press the q key, for quit.
you can type
```
man dmesg
```press enter
if you're in the gnome-terminal, you can use the
mouse scroll wheel to scroll thru the page, or
use your pg up,pg dn, or arrow keys.
read the first paragraph or so.
then q to quit.
so you could run (type into terminal and press enter key)
```
cd
```to make sure your in your home directory (folder)
then run
```
dmesg > boot.messages
```then click Places > Home Folder and the boot.messages
file should be in there.

we're looking for anything recommending something more for boot flags like
the pci=noacpi one. 
it'll look quite odd, but try taking your time and look for something like
Bios blah blah, or something  couldn't do something....try pci=xxxx or acpi=force
stuff, or I guess I should say flags, like that.
the xxx=xxxx is the stuff, flags we're looking for.


booting the live cd, and choosing the boot from first hard drive option, was different...
once it finishes booting, I got this window telling me there's a volume detected 
containing packages. would you like to open. ok or close or cancel. I closed., then right
clicked the cd icon on the desktop and clicked eject. live cd  disk is ejected
and I was running the hard drive installed ubuntu. cool.

edit : could see first couple of paragraphs here about acpi
[http://en.wikipedia.org/wiki/Acpi](http://en.wikipedia.org/wiki/Acpi)

trails

---

### Post by SpiritIsReality on 2007-09-28
howdy
could we look into doing this?
> As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.
from here
[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

we can check in linux:
man ethtool
I think just run
ethtool eth0
no,  have to run
sudo ethtool eth0
have to run as  root (administrator) SuperUserDO

trails

---

### Post by SpiritIsReality on 2007-09-28
howdy
setting "Wake-on-lan after shutdown." in xp.

xp "wake on lan after shutdown" search
[http://www.google.ca/search?hl=en&q=xp+%22wake+on+lan+after+shutdown%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=xp+%22wake+on+lan+after+shutdown%22&btnG=Google+Search&meta=)
>  Lone_Wolf
LQ Newbie
 
Registered: Jul 2007
Location: Netherlands
Distribution: Archlinux
Posts: 6
	
The official Realtek drivers for Windows dated post May 2007 have a "feature" .
Default they are set to disable Wake On Lan, and this results in DISABLING the card whenever Windows shuts down.
It can only be started by Windows.
You will notice this because the Link light will only be on when Windows is loaded. The normal status of the Link light should be always on while the system is on (after or during POST) on these NICs.

solution :
In Windows XP (example)
Right click my computer --> Hardware tab --> Device Manager --> Network Adapters --> "double click" Realtek ... --> Advanced tab --> Wake-On-Lan After Shutdown --> Enable.from 
[http://www.linuxquestions.org/questions/showthread.php?p=2895586](http://www.linuxquestions.org/questions/showthread.php?p=2895586)
can you follow the path in this quote. I don't have advanced tab > wake on lan after shutdown > enable. If you can follow that path and enable it,
it's probably a good thing.

trails

---

### Post by SpiritIsReality on 2007-09-28
howdy

miki85 ...your post #11
> 
..fmat , one of the links you sent said that i should try to turn off the comp and unplug the net cable...wait 15 sec' and boot stright to ubuntu... going to try it, maybe it is a bug in the net-card ... even though we tried other cards, it still worth a try
sorry I missed that about the cable.

the quote I gave in post #16 >Powering off and unplugging the machine for a few seconds (around 10 usually does it) seems to reset the card, so it will work in Linux again until you boot Windows again.
that was not a good quote to give on it's own... my bad... about unplugging the cable. I saw somewhere they were talking about
the power cord.
quote from bollix47 post #6 here
[http://ubuntuforums.org/showthread.php?t=500978](http://ubuntuforums.org/showthread.php?t=500978)
> I had a similar problem recently and found a solution that worked for me.
Basically, shutdown your computer and remove the power cord for 30 seconds.
As soon as I booted back up the connectivity light came back on.
Prior to that I had rebooted numerous times, changed cables and ports on the router, but the problem would not go away until all power was removed from the computer.
Good luck.
you could try that. see if it works.

[color=blue]if this works, > please go to post # 26.
if this does not work, > please return to post # 24[/color]

my apologies for the confusion. 
trails

---

### Post by miki85 on 2007-09-28
O.M.G !!!

i cant believe this is really happening ...
i am talking to you from Ubuntu !
finally... and i owe it all to you  **fmat** !!!

you are the greatest !!!

you know what solve it all ?!

no matter what, at least as far as i can see it...  no matter what we would have done in Ubuntu would have made things right... 

it that post that say :
"Right click my computer --> Hardware tab --> Device Manager --> Network Adapters --> "double click" Realtek ... --> Advanced tab --> Wake-On-Lan After Shutdown --> Enable."

that made the led on the back of the network card stay up... :)
i cant tell you how happy i am and how grateful i am to you and how much you helped me !!!
keep on being such a friend... you are the BEST mate... 

T H A N K    Y O U  !!!

---

### Post by SpiritIsReality on 2007-09-28
YEEEEHAAAA !!!!
howdy pard

thank goodness

>"Right click my computer --> Hardware tab --> Device Manager --> Network Adapters --> "double click" Realtek ... --> Advanced tab --> Wake-On-Lan After Shutdown --> Enable."

yup, I think you're right, no matter what we did in ubuntu, the micsoft had us locked out.

this is the dawning of the age of .....open source ... a gnu age ...

we're all here helpin' one another learn how to run this linux mustang.
if it wasn't for the others helping us, it'd be a rough ride.
it's a great spirit around here, pard. we're in grand company.

happy trails

---

### Post by SpiritIsReality on 2007-09-28
ok

if you go to the Thread Tools, at the top of the page, maybe page 1. click and choose 
Mark Thread Solved, then when others search for router connection, to find an answer
to their trouble they'll see this thread marked [Solved] if they search router, or connection. good keywords don't you think.
click on search, right click advanced search, click open link in new tab, click on the new tab, at the
top of firefox.
 in User Name , type, fmat
under Search Options, Find Posts From, click the arrow and choose Yesterday.
at the bottom of the page, click Search Now.
those are the threads that I've posted in. I can catch you on the trail the same way.

about keepin' track of what threads you post in. what helped me, and I'm sorry to say I didn't keep
track of who it was that said this to someone else who was askin'...but thanks just the same...
if you click on forum help, forum FAQ (frequently asked questions), at the bottom of that
page it mentions choosing "default thread subscription mode".

what I was told to do, 
at the top of any page, click on User CP, click on Edit Options,
 on that page, scroll down and find under the heading Messaging and Notification
the box titled Default Thread Subscription Mode
click on the expansion arrow, and choose No Email Notification
down at the bottom of the page, click on Save Changes

from now on, when you post in a thread, that thread will show up when you log in 
and at the top of the page, click on User CP and click on Subscribed Threads.
the threads will be in bold print if someone posts after you have viewed the thread.

there's ways of managing that Control Panel, Subscribed Threads Folder page
which I'm just starting to figure out.
you can make folders called different names and move threads around just like files in
your Home Folder.

YouAreInTheSaddle. Way to go. Headin' for ...
all the best
trails
the legend goes, that on billy the kids gravestone, a while after they did or supposedly buried him there, found on the tombstone was a scratched
PALS
 I had to edit out buds, I was mistaken if I'm not mistaken
pals is what they said to one another often so the story goes. we're pals. or (buds would work). I've gotta look that up. I love searchin
I was gone for a minute, then I got to thinkin bout when I gnu how much I love teamwork. like gnow, you gno.
[http://www.google.ca/search?hl=en&q=%22billy+the+kid%22+%22william+bonnie%22+%28buds+%7C+pals%29&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%22billy+the+kid%22+%22william+bonnie%22+%28buds+%7C+pals%29&btnG=Search&meta=)
buds

---

### Post by dilidon on 2007-09-29
> **fmat said:**
> howdy
setting "Wake-on-lan after shutdown." in xp.

xp "wake on lan after shutdown" search
[http://www.google.ca/search?hl=en&q=xp+%22wake+on+lan+after+shutdown%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=xp+%22wake+on+lan+after+shutdown%22&btnG=Google+Search&meta=)
from 
[http://www.linuxquestions.org/questions/showthread.php?p=2895586](http://www.linuxquestions.org/questions/showthread.php?p=2895586)
can you follow the path in this quote. I don't have advanced tab > wake on lan after shutdown > enable. If you can follow that path and enable it,
it's probably a good thing.

trails

I confirm - setting this to "wake on lan after shutdown" -> "enable" under XP works.
(I had to install XP the other day to run a specific program, and after that I ran into network problems under Ubuntu - your research helped me out.)
thanks.

---

### Post by SpiritIsReality on 2007-09-29
dilidon ...I messed up badly, I've got to put reference to noob12 and others at gentoo and all the 
buds,,you know what I mean. I'm gettin a bit turned around in the forums.. keeping track..
but I messed up there..please help me fix that. could you.? please..any advice...greatly appreciated
I'm gonna have a look around. I thought for sure I posted noob12 post # in a link. I messed up. sorry
What I was thinking about when I pointed out post#26 was the proper directions. I forgot about mentioning
credits. I remembered one other place, I'll see if I can find it. oh well, I guress you'd have to check the backups and time
log files to prove that this said that at then....you know what I mean. I messed up. I'll see if I can find that place I 
said to check posts #26,234,3,23 I don't remember the numbers so I figured I might as well list the wrong ones for sure.
see I just did it again. mention 26, not guess at the others ...
[http://ubuntuforums.org/showthread.php?t=562479](http://ubuntuforums.org/showthread.php?t=562479) post #2
...thanks
buds

---

### Post by noob12 on 2007-09-29
I think you had multiple issues including the one in this other thread: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Sorry I couldn't stick around through the whole thing.  Glad you got it solved!

---

### Post by SpiritIsReality on 2007-09-29
noob12 ...thankyou sooooo much pard. how IIIIIIIIIIIIIIIIIIIIIII solved it was searching for an answer and
found yours. please read post #33 this thread. please help me straighten out this mess. any advice greatly appreciated. please
...thanks
buds

---

### Post by SpiritIsReality on 2007-09-29
howdy
miki85 ... what posts should we mention as having solved this thing, could you help me figure out
what posts we used. you already did didn't you you said you followed that post where Wolf was telling how to set Wake-on lan after shutdown. right? how the hell are you anyway. first thing, I do
when I see your light on is start asking for help. well right after the howdy and your name.
2 out of 3 aint bad... well 3 out of 3 is better
buds

---

### Post by SpiritIsReality on 2007-09-29
howdy
noob12 ...no apologies necessary
buds

---

### Post by miki85 on 2007-09-29
hi, it's the Wolf's thread that did the magic :)

and me?, everything's great, from the moment i connected i didnt leave ubuntu and now learning python through "Dive into python"... it's really neat :) ... i have a background in visual basic but.. heh that doesnt help in linux so i have to learn something new...

---

### Post by SpiritIsReality on 2007-09-29
howdy
miki85 ... good to hear from you pard. thanks for that link pointer.
I don't quite know what to say.
Tell you what. meett you on the community chat and we'll ...chat.
could you please...there I go again asking you for stuff... could you go to the top of the page and 
click Thread Tools, and click on Mark This Thread Solved. Then people who are looking for 
Solved ones will find them, and the people who figure they should help know they don't have to?
Like they say in the movies, you got sand. I'll give you that.
I reckon that in the long run it will be all good.
buds

edit :where did the community chat go?
edit :I thought there was one.
edit :community cafe and backyard?
edit : > 
            [IMG]http://ubuntuforums.org/clear.gif[/IMG]                              [**Community Cafe**]("http://ubuntuforums.org/forumdisplay.php?f=11")                               (20,169 Threads) (376,297 Posts)             Community Chat area for general discussion.


---

### Post by SpiritIsReality on 2007-09-29
WOW
our first one miki85. thanks pard.
what a ride!
buds

---

