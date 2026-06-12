---
title: "Ubuntu 7.04 ralink wireless problems"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by jklarsen on 2007-04-14
Hi All,


I am real newbie to ubuntu, so this might be an obvious answer, so please dont bash me!


I have installed 7.04 and it works fine, but the wireless is not.

I can get a list of all the wireless networks, so my guess is that ubuntu can use the wireless card, so i am not shure what goes wrong, because when i choose my network, and enters the passwd it just keeps on trying to connect.
It is a WPA Pre-shared key network, and i can only select WEP in ubuntu, so this might be the problem.

As far as i can see it is an Ralink 6521 network adapter, so any if you have any hints/tricks/solutions etc. i would really appreciate this, because i really want to use Ubuntu.
Also when you reply please consider that i am a Windows guy, so terminals etc. are new to me;-)


Thanks in advance

Best...Jan

---

### Post by nuttiplutt on 2007-04-14
Hi!

I'm also having problems getting connected with my ralink rt2500 wireless card and also being a newbie to Ubuntu, I've had to do some searching for solutions. First I can tell you that in the GUI in 7.04, you can only use WEP. To use WPA, you will have to do changes in the settings through a terminal, so I'd advice you to learn a bit about how to use the terminal as it is essential to use WPA. If you do want to use WPA, there's a good guide here: [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

Some hints which I had to discover the hard way: 

1. 
When getting error messages in install commands, it might be useful to have the installation cd in your cd drive.

2.
There might be a good solution to uninstall network manager in 7.04 if you decide to use WPA.
This is mentioned in the post I've written here: [http://ubuntuforums.org/showthread.php?t=408403]("http://ubuntuforums.org/showthread.php?t=408403")


I hope that some experts can help you further as I'm discovering things as I go along and still feel very much like a newbie in Ubuntu.

---

### Post by huygens on 2007-04-14
Hello,

Your card (RT6521) was called also in the past RT61. That's the one I have ;-)

So to answer your question first, Network Manager which comes default with Ubuntu Feisty [does support properly the RT chipset]("http://live.gnome.org/NetworkManagerHardware") (check the rt2x00 in the unsupported section). There is only WEP encryption possible, WPA is not possible. Actually it is not really NetworkManager fault as the RT driver does not provide the expected interface for NM to use WPA.
So you have the solution to modify your network to use WEP (but it is not that secure, but might be enough already for you) or you should deactivate NM (like nuttiplut sugested, just remove it) and you will have to fiddle with some files.
For your specific card, there are two good guides out there:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)
[*][http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)[/LIST]

---

### Post by jklarsen on 2007-04-15
Hi guys,

And thank you for your swift replies.


I have looked at the guides you recomended and then started to follow them.

I uninstalled the network manager.


I get a lot of errors when trying the following:

jan@jan-laptop:~/rt61/Module$ sudo make all
make -C /lib/modules/2.6.20-14-generic/build SUBDIRS=/home/jan/rt61/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  CC [M]  /home/jan/rt61/Module/rtmp_main.o
/home/jan/rt61/Module/rtmp_main.c: In function â&#128;&#152;RT61_probeâ&#128;&#153;:
/home/jan/rt61/Module/rtmp_main.c:197: error: â&#128;&#152;struct net_deviceâ&#128;&#153; has no member named â&#128;&#152;get_wireless_statsâ&#128;&#153;
/home/jan/rt61/Module/rtmp_main.c: In function â&#128;&#152;RT61_openâ&#128;&#153;:
/home/jan/rt61/Module/rtmp_main.c:326: warning: passing argument 2 of â&#128;&#152;request_irqâ&#128;&#153; from incompatible pointer type
make[2]: *** [/home/jan/rt61/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/jan/rt61/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make: *** [all] Error 2


Also when i try to try the - [http://ubuntuforums.org/showpost.php?p=1310334&postcount=117](http://ubuntuforums.org/showpost.php?p=1310334&postcount=117)

i get an error when typing - sudo iwpriv ra0 set NetworkType=Infra
it says that i do not have an ra0 interface, so how do i see what it is called?


Hope this makes sence


Best...Jan

---

### Post by jklarsen on 2007-04-15
Also this also goes wrong.............

jan@jan-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r

btw, i changes encryption to WEP to avoid the WPA problems.

Best...Jan

---

### Post by nuttiplutt on 2007-04-15
> **jklarsen said:**
> Also this also goes wrong.............

jan@jan-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r

btw, i changes encryption to WEP to avoid the WPA problems.

Best...Jan

I got the same error when I did the command of build-essentials until I tried the command with the installation cd in the cd drive. If I remember correctly, I also needed to start up the Synaptic Package Manager (under system tools) when the installation cd is put in. Then the program asks if I want to add the repositories on the cd and I answered yes. Then the command went fine.

Can't help you with your other problem, though...

---

### Post by navsx on 2007-04-15
You should not use single quotes there, but the one to the left of key 1 on your keyboard. Better, yet, just copy this over:

sudo apt-get install linux-headers-`uname -r`

---

### Post by smo0th on 2007-04-18
Hi guys, I successfully configured the rt2500, be sure you don't have duplicate DNS, this is how it worked for me:

[http://ubuntuforums.org/showthread.php?p=2472174#post2472174](http://ubuntuforums.org/showthread.php?p=2472174#post2472174)

\\:D/

---

### Post by huygens on 2007-04-18
> **jklarsen said:**
> btw, i changes encryption to WEP to avoid the WPA problems.

If you feel that you do not need the increase security of WPA, this is fine :-) as the counter part is a gain in ease of use.
But if you would have sensitive data transferring on your local network and you are living in a neighbourhood where people could easily receive your Wi-Fi signal, using WEP would not be recommended. A good hacker, with a powerful computer and a bit of luck could crack a [104 bit WEP key in a matter of minutes]("http://eprint.iacr.org/2007/120"). But usually, it would take hours to do so for "kiddies".

---

### Post by wilderness wanderer on 2007-04-20
My 2 cents:

rt2500 pci card worked fine under Edgy. Upgraded via alt CD and no network. Numerous attempts at getting network manager to sort it out failed. I uninstalled network manager and it still will not connect via the Gnome network GUI. Note that this is with WEP encryption.

I _am_ able to connect via the command line:

sudo ifconfig ra0 down
sudo iwconfig ra0 essid blahblahblah key hexblahblah
sudo dhclient ra0

I found this at [https://bugs.launchpad.net/ubuntu/+s....20/+bug/37120](https://bugs.launchpad.net/ubuntu/+s....20/+bug/37120)

Syntax to manually configure in /etc/network/interfaces

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "MyRouterName"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="MySecretPassword
pre-up ifconfig ra0 up
auto ra0

Since I am only using WEP, modified to:

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "MyRouterName"
pre-up iwconfig ra0 key "MyKeyInHex"
pre-up iwconfig ra0 mode Managed
pre-up ifconfig ra0 up
auto ra0

Now I have wireless connectivity which survives a reboot.

---

### Post by Kelli on 2007-04-21
Just wanted to say THANK YOU!!! to wilderness wanderer.  My rt2500 wireless card worked great under Edgy, but stopped working as soon as I upgraded to Feisty.  A search yielded the fix that was posted here, and now my wireless works after reboot as well.  Thought I should officially jump in and say thanks so much!!!

---

### Post by wilderness wanderer on 2007-04-21
I'm glad you got it working Kelli.  Losing your network connection is one of the more frustrating problems.  I certainly wasn't looking forward to explaining to my mom that I upgraded her computer right out of its internet connection!

---

### Post by lukaszJarochowski on 2007-04-22
I had rt61 (ralink) driver installed in Edgy, and wanted to work with that driver in Feisty, so I've made this howto:
[http://ubuntuforums.org/showthread.php?t=415693]("http://ubuntuforums.org/showthread.php?t=415693")

hope that helps, it is really easy to get rt61 working as it was in edgy, with WPA, and everything.

---

### Post by elehayyme on 2007-05-25
Wow there is so much information here regarding this series.  Thank you so much for posting the details.  

I have a problem with my ralink (ra73).  Despite configuring everything (well, my husband did) and removing the network manager. my wireless connection will hold only for about 10 minutes. After that point, I have to sudo ifup, ifdown, etc.  You can imagine how frustrating this is! 

when I did a dmesg (I can't remember the exact line), I did find this message occurring over and over again:

net device supplies mac, activating this one

I'm not too sure what it means but it's correlating to each time I lose my internet connection. I'm not too sure why it's doing it either.

I'm sorry for being a little vague on the details as I am still learning.  

Should I just reinstall the drivers, etc? 

I'm using the Feisty version of ubuntu.

Thanks so much for your insight!

---

