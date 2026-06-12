---
title: "installing USB wireless driver"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by bulb-xon on 2010-03-21
Greetings All...
as new convert to Linux (Ubuntu Studio 9.10) and dual booting with XP...
I've got my self on line in with  [COLOR=#0000ff]_[http://au.billion.com/product/wireless/bipac7300n.php](http://au.billion.com/product/wireless/bipac7300n.php)_[/COLOR]
and [COLOR=#0000ff]_[http://au.billion.com/product/wireless/bipac3011n.php](http://au.billion.com/product/wireless/bipac3011n.php)_[/COLOR].....

NOW...I managed to get this working in XP using the driver off the disc that came with the USB...when using with XP lights flash and everything....when plugged in and i've booted with Ubuntu no lights at all...

On the disc that came with the wireless USB adapter there is a LINUX DRIVER Folder but  unfortunately i don't know how to/where to  install it....(i really want  to get it working in Linux so i can piss littleflacid (microsoft) off  my computer)..it's a tar.gz file. 
here's a link (up for 7 days) if you're interested in seeing what inside and whaat i can do...[https://rcpt.yousendit.com/839744535/3c07d7dfdec07059b0ed0b854b6d1fa4](https://rcpt.yousendit.com/839744535/3c07d7dfdec07059b0ed0b854b6d1fa4)
i'm new at this linux game so you'll  have to be gentle..;)
 one thing i've noticed though, is when it's plugged in when i've  booted with Ubuntu the light isn't on....(it's on and flashes in XP )...
 any help in installing the linux driver would be appreciated and  repaid in thank you's
 Cheers

---

### Post by ikt on 2010-03-21
> **bulb-xon said:**
> Greetings All...
as new convert to Linux (Ubuntu Studio 9.10) and dual booting with XP...
I've got my self on line in with  [COLOR=#0000ff]_[http://au.billion.com/product/wireless/bipac7300n.php](http://au.billion.com/product/wireless/bipac7300n.php)_[/COLOR]
and [COLOR=#0000ff]_[http://au.billion.com/product/wireless/bipac3011n.php](http://au.billion.com/product/wireless/bipac3011n.php)_[/COLOR].....

NOW...I managed to get this working in XP using the driver off the disc that came with the USB...when using with XP lights flash and everything....when plugged in and i've booted with Ubuntu no lights at all...

On the disc that came with the wireless USB adapter there is a LINUX DRIVER Folder but  unfortunately i don't know how to/where to  install it....(i really want  to get it working in Linux so i can piss littleflacid (microsoft) off  my computer)..it's a tar.gz file. 
here's a link (up for 7 days) if you're interested in seeing what inside and whaat i can do...[https://rcpt.yousendit.com/839744535/3c07d7dfdec07059b0ed0b854b6d1fa4](https://rcpt.yousendit.com/839744535/3c07d7dfdec07059b0ed0b854b6d1fa4)
i'm new at this linux game so you'll  have to be gentle..;)
 one thing i've noticed though, is when it's plugged in when i've  booted with Ubuntu the light isn't on....(it's on and flashes in XP )...
 any help in installing the linux driver would be appreciated and  repaid in thank you's
 Cheers

Heya,

welcome to the land of linux, it's a little strange there's a linux driver provided but it isn't working out of the box as I would have thought they'd submit it to get included with the kernel, if you've got the windows driver there this may be of use:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by bkratz on 2010-03-21
Here is a pretty good page on installing stuff

[http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually](http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually)

---

### Post by 3rdalbum on 2010-03-21
The fact that the light doesn't come on does not necessarily mean that the device won't work for its main purpose. You've checked in the Network Manager applet on your top panel to see if the device is actually picking up networks and stuff?

Apparently this device's driver is not yet in the main tree of the kernel. If Network Manager doesn't show any wireless networks, then you'll need to compile the driver using the download you linked to. This actually isn't too hard.

First, get an internet connection by plugging your computer into an Ethernet port on your modem/router.

Secondly, use System > Administration > Synaptic Package Manager to install the 'linux-headers-generic' and 'build-essential' packages. If a new kernel gets installed in this step, then reboot after the installation is done (if unsure, reboot anyway).

Third, extract the .tar.gz (it's a compressed archive) to somewhere convenient, like your desktop.

Four, open the terminal (Applications > Accessories > Terminal). Type the word 'cd' (without the quotes), hit the space bar so there is a trailing space, and drag the decompressed folder to the terminal. You'll notice that its filepath has been filled in for you. Switch back to the terminal and hit Enter to run the command.

Now type:

```
make
sudo make install
```

You'll be asked for your password when you put in that second command - type it in and hit Enter, nothing will be shown while you type.

After the 'sudo make install' step is finished, reboot and you should have wireless connectivity. Congratulations, you've just compiled source code.

In Ubuntu 10.10 the driver should surely be available out-of-the-box.

---

### Post by bulb-xon on 2010-03-21
[COLOR=Olive][COLOR=Black]Thanks for all the replys.....[/COLOR]

 You've checked in the Network Manager applet on your top panel to see if the device is actually picking up networks and stuff?[/COLOR]

yes i have and NO nothing showing here only..'wired connection etho0'

F[COLOR=DarkGreen]irst, get an internet connection by plugging your computer into an Ethernet port on your modem/router.[/COLOR]  

[COLOR=Black]Done!![/COLOR]
[COLOR=Green]
Secondly, use System > Administration > Synaptic Package Manager to install the 'linux-headers-generic' and 'build-essential' packages. If a new kernel gets installed in this step, then reboot after the installation is done (if unsure, reboot anyway).[/COLOR]

[COLOR=Black]AND DONE!![/COLOR]

[COLOR=DarkGreen]Third, extract the .tar.gz (it's a compressed archive) to somewhere convenient, like your desktop.[/COLOR]

[COLOR=Black]and this tooo!![/COLOR]

[COLOR=SeaGreen]Four, open the terminal (Applications > Accessories > Terminal). Type the word 'cd' (without the quotes), hit the space bar so there is a trailing space, and drag the decompressed folder to the terminal. You'll notice that its filepath has been filled in for you. Switch back to the terminal and hit Enter to run the command.[/COLOR]

[COLOR=Black]OK thats fine...[/COLOR]

[COLOR=SeaGreen]Now type:

[/COLOR]       [COLOR=SeaGreen]Code:[/COLOR]
     [COLOR=SeaGreen]make
sudo make install[/COLOR] 
OK ive did the above and typed in 'make' (with no quotes) and the terminal came back with

[COLOR=Red]colum@mutlidge:~$ cd '/home/colum/rtl8192su_linux_2.6.0001.0320.2009' 
colum@mutlidge:~/rtl8192su_linux_2.6.0001.0320.2009$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_rx.o
  CC [M]  /home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_softmac.o
  CC [M]  /home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_tx.o
  CC [M]  /home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_wx.o
/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_wx.c: In function &#8216;ieee80211_wx_get_encode_ext_rsl&#8217;:
/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_wx.c:846: warning: suggest parentheses around operand of &#8216;!&#8217; or change &#8216;&&#8217; to &#8216;&&&#8217; or &#8216;!&#8217; to &#8216;~&#8217;
  CC [M]  /home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_module.o
/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_module.c: In function &#8216;alloc_ieee80211_rsl&#8217;:
/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_module.c:121: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
make[2]: *** [/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make: *** [all] Error 2
colum@mutlidge:~/rtl8192su_linux_2.6.0001.0320.2009$[/COLOR] 

[COLOR=Black]i then typed in 'sudo make install'[/COLOR] and there terminal said....
[COLOR=Red]
colum@mutlidge:~/rtl8192su_linux_2.6.0001.0320.2009$ sudo make install
[sudo] password for colum: 
make[1]: Entering directory `/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211'
make -C /lib/modules/2.6.31-9-rt/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/colum/rtl8192su_linux_2.6.0001.0320.2009/ieee80211'
make: *** [install] Error 2
colum@mutlidge:~/rtl8192su_linux_2.6.0001.0320.2009$ ^C
colum@mutlidge:~/rtl8192su_linux_2.6.0001.0320.200[/COLOR]

I noticed there was a few 'Errors' in these 2 terminal 'blurbs'...
i then did the old:

[COLOR=SeaGreen]After the 'sudo make install' step is finished, reboot and you should have wireless connectivity.[/COLOR]

but still no devices showing....
so i'm still at a loss....

i've had a go at this too from bkratz

[COLOR=SeaGreen]Here is a pretty good page on installing stuff

[http://amitech.50webs.com/installing...ckage_manually]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")[/COLOR]  

but you guessed it..nooooo

i want to get the linux driver working first so i don't want to have a go with ndiswrapper yet (that's a last resort...)

thanks for all the help and anymore (hopefully) coming my way..
cheers

---

### Post by bulb-xon on 2010-03-22
in addendum to my last post...the driver seems to be installed but that is about it...
attached are some screens from the "wireless network drivers" the first when i open wirless network drivers and the second when i click 'OK"



can anyone help me more???
chhers
;)

---

### Post by ikt on 2010-03-27
> **bulb-xon said:**
> in addendum to my last post...the driver seems to be installed but that is about it...
attached are some screens from the "wireless network drivers" the first when i open wirless network drivers and the second when i click 'OK"



can anyone help me more???
chhers
;)

if you type 'iwconfig' in terminal does anything show up?

---

