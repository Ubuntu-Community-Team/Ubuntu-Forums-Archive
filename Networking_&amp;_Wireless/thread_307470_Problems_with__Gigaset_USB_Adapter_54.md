---
title: "Problems with  Gigaset USB Adapter 54"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Bero Nizic on 2006-11-26
I saw that there are many threads about problems with wireless card in Ubuntu, and I would like also to give my contribution :???: 
Exactly, I have a problem with my Gigaset USB Adapter 54 on my Ubuntu 6.0.6

I am Linux newbie, but there are more than one tutorial which explain what to do - I was following that suggestions but I am at the moment stucked,and I need your help. It is big obstacle for a linux wannabe (as me) to transiton from XP to Ubunutu. I hope you can help, if you do and if you ever come to Croatia I would like to drink beer or coffee with you ;) 
Any other information which you think is important and not provided in this post I would gladly give. Please read and give me some (smart) advice.

It seems that for my adapter there are 2 possibilites:
zd1211 driver and ndiswrapper.

What I did:
step 0
I have installed linux headers, essential build, wireless tools

step 1:zd1211
I removed existing zd1211 driver (modprobe -r zd1211)

- I have download zd1211 firmware and copied it to /lib/firmware/zd1211
- I download [http://zd1211.ath.cx/download/zd1211-driver-r77.tgz](http://zd1211.ath.cx/download/zd1211-driver-r77.tgz)
- sudo -s
- I compiled it with make clean, make, make install
- modprobe -v zd1211
- echo zd1211 >> /etc/modules
- iwconfig produce this:
[I]lo        no wireless extensions.
sit0      no wireless extensions.
eth1      IEEE 802.11b  ESSID off/any
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/I]
ifconfig wlan0 up produce 
"*wlan0: ERROR while getting interface flags: No such device*"
- I unplugged adapter and reconnected it, but same thing...
- after that I tried driver versions: 83, 39, 80 (with first unloading old version)

I did restart, but same thing. 
BTW, adapter is working fine in Windows XP Home.

After that, I tried step 2:ndiswrapper
- ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
- download ndiswrapper ver. 1.29
- make distclean, make, make install
- I have copied drivers from orignal installation disk for Gigaset Adapter 54 in ndiswrapper directory (this driver is suggested by [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List))
- ndiswrapper -i se4501d.inf
- ndiswrapper -l produces: 
"Installed drivers:
se4501d driver installed, hardware present"
- depmod -a (no error)
- modprobe ndiswrapper (no error)

ifconfig wlan0 up produce 
"*wlan0: ERROR while getting interface flags: No such device*"
In system log there isn't 
 "[I]ndiswrapper: driver ''driver1'' loaded" for that driver, 
and neither "wlan0: ndiswrapper ethernet device xx xx xx xx xx xx[/I]"

After that I have found newer version of ndiswrapper 1.9, and download it.
- ndiswrapper -e se4501d
- same procedure for 1.9, but also same result ](*,) 

dmesg produce list which is in attachment *list.txt*.

Thank you for your help.
Bero

---

### Post by FrodoB on 2006-11-26
Go to your ndiswrapper directory and run:

sudo make uninstall

This will remove it.

Then go and follow these instructions for the Belkin F5D7050 ver 4000 that uses the same drivers:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Be sure to use:

make both

As this will get the drivers for the zd1211 and the zd1211b and one of them will work for you.

---

### Post by Bero Nizic on 2006-11-26
It isn't functioning :(

1. I uninstalled ndiswrapper

2. sudo modprobe -r zd1211

3. installed with make both for 83 driver

4. ls /lib/modules/`uname -r`/net  -> showing to files: zd1211b.ko and zd1211.ko

5. lsusb
Bus 006 Device 007: ID 083a:4521 Accton Technology Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

6. iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b  ESSID off/any
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

7. After that I did:
- modprobe -v zd1211
- modprobe -v zd1211b
- iwconfig -> result was the same ](*,) 

I tried to connect adapter with different USB slots, but nothing. I am using USB 2.0 hub; hub is working properly - I can put in USB memory stick and it is working automatically. I tried also USB 1.1 slots, but same thing.

Results of dmesg is in list2.txt file. If there is need for any other information I would gladly provide it.

Bero

---

### Post by FrodoB on 2006-11-26
Well all of the posts I am seeing seem to indicate that this is not a zd1211 or zd1211b. Take a look at these:

[http://www.google.com/search?hl=en&q=083a%3A4521++Linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=083a%3A4521++Linux&btnG=Google+Search)

Am I missing something?

---

### Post by Bero Nizic on 2006-11-26
> **FrodoB said:**
> Well all of the posts I am seeing seem to indicate that this is not a zd1211 or zd1211b. Take a look at these:

[http://www.google.com/search?hl=en&q=083a%3A4521++Linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=083a%3A4521++Linux&btnG=Google+Search)

Am I missing something?

Results are very interesting: to bad that they are all in German! ;) I did understand just one thing: other people are also having problems with it. Even if it isn't zd1211 driver, why ndiswrapper isn't functioning? :-? I saw there is prism54 project but it looks suspiuocus to me, and there is company called Linuxant which is produceing wlan drivers - it must be paid, and it isn't   my adapter in supported list, probably also this doesn't function. And even if it does it is cheaper/simplier to buy other adapter. :-k

---

### Post by blackmh on 2006-11-26
That adapter is piece of *beep* anyway and its not working even on windows as it should...

---

### Post by FrodoB on 2006-11-27
When I go to that search it has a link to the far right of each article that says "[SIZE=-1][ [Translate this page]("http://translate.google.com/translate?hl=en&sl=de&u=http://www.unixboard.de/vb3/showthread.php%3Ft%3D12290%26page%3D2&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D083a:4521%2B%2BLinux%26hl%3Den%26lr%3D%26sa%3DG") ]" and when I click on it the article is translated into fairly readable English.

[/SIZE]

---

### Post by Bero Nizic on 2006-11-27
FrodoB,
yes it is funny that I didn't see it :o 
Translation is funny, but readable. Seems that my first conclusion was correct - that thing doesn't function in linux. I have spent too much time on this, and even if exists a solution, I don't have time for more searching. I will buy other adapter which have better support. 
Thank you for your suggestions.

Bero

---

### Post by bjd on 2006-11-27
Also note that your wireless device appears to be called eth1 instead of wlan0, hence the 'No such device' errors when trying to up the wlan0 device.
So try same again but with eth1, where you used wlan0 before.

---

