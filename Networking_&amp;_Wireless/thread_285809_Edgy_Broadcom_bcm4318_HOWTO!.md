---
title: "Edgy Broadcom bcm4318 HOWTO!"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by nbound on 2006-10-27
*Unknown whether this or similar works with the AMD64 and other versions of ubuntu, if you have success please post it in this thread.*

**Download ndiswrapper from Synaptic**
[LIST]
[*]System -> Administration -> Synaptic Package Manager
[*]Search for ndiswrapper
[*]Download "ndiswrapper-utils-1.9" and "ndiswrapper-common" (Edgy Users may only have 1.8, this is fine for the howto - *someone tell me if edgy ndiswrapper has or has not been updated*)
[/LIST]

**Blacklist native bcm43xx drivers**
[LIST]
[*]Type:
```
sudo gedit /etc/modprobe.d/blacklist
```
[*]Add the line:
```
blacklist bcm43xx
```
[*]After saving type at the terminal:
```
sudo rmmod bcm43xx
```
[/LIST]

**Get windows drivers and install them**
[LIST]
[*] A) Download and extract windows drivers to a folder of your choice. Drivers can be found [here]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip")
[*] B) Drivers from original disk are also fine, the previous link is just a newer version

[*]Install them in ndiswrapper:
```
sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf
```
[*]Check to see if hardware found
```
sudo ndiswrapper -l
```
[*]If hardware not found and you are sure you followed the howto you have a different card and this howto will not work.
[/LIST]


**Setup ndiswrapper to load driver (and itself) at startup**
[LIST]
[*]Edit the following file:
```
sudo gedit /etc/modules
```
[*]Add a line which says:
```
ndiswrapper
```
[*]Restart
[/LIST]

**During restart the "Wireless On" light for your laptop should turn on or flash depending on your setup (Well it did for me: your results may vary)**
[LIST]
[*]If light does not show try pressing wireless button (incase left in off mode)
[/LIST]

**Setup Wireless Card in Networking** (Manual setup is also fine)
[LIST]
[*]System -> Administration -> Networking
[*]Enable wireless connection and configure all the settings
[*]Disable wired connection (wireless and wired connections may not work simultaneously - your mileage may vary in this regard, if it doesnt work, it should after extra tinkering that isnt covered here)
[*]Use the internet/LAN!
[/LIST]

This was posted from my laptop which used the above method.
Kudos to lolcese for driver link (moved since previous revision of this howto)

***Hope it helped!***

---

### Post by krazyd on 2006-10-27
It took me hours of trawling these forums to figure out that procedure.. ](*,)

Thanks for the nice, clear explanation! This should definitely be added to the wiki! :)

---

### Post by Erik. on 2006-10-27
Hi,
Thanks i will try it,
i don't understand one thing:
Setup Wireless Card in Networking

    * System -> Administration -> Networking
    * Enable wireless connection and configure all the settings
    * Disable wired connection
    * Use the internet/LAN!
I need to activate my wireless and turn off my wired but how to use lan?

my wireless is eth0 and wired is eth1

EDIT:
I have done the step installing ndsiwrapper and sudo gedit /etc/modules already done...

---

### Post by nbound on 2006-10-27
You want to have both connections active?

That doesnt seem to work from experience.

You must run one at time

---

### Post by scrubadub on 2006-10-27
some notes i think should be added
where to get the drivers
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

no need to reboot
sudo modprobe ndiswrapper
(make sure you press any hardware buttons to turn on wifi)
sudo ifconfig eth1 up

this should be all you need to do, for some reason it didnt show up in ifconfig -a until i manually brought it up. it also shows up in the gui network config. Then I do this to pull an ip addy
sudo iwconfig eth1 essid SSIDNAME;sudo dhclient eth1

btw using a compaq v2000z with
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
along with
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

both work at the same time for me with no problems, remember to check your route table if the traffic isn't going to the iface you want

---

### Post by nbound on 2006-10-27
> **scrubadub said:**
> some notes i think should be added
where to get the drivers
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

Will add :) 

> **scrubadub said:**
> no need to reboot
sudo modprobe ndiswrapper
(make sure you press any hardware buttons to turn on wifi)
Didnt work on mine... i HAD to reboot (yep strange as it is)


> **scrubadub said:**
> 
sudo ifconfig eth1 up

this should be all you need to do, for some reason it didnt show up in ifconfig -a until i manually brought it up. it also shows up in the gui network config. Then I do this to pull an ip addy
sudo iwconfig eth1 essid SSIDNAME;sudo dhclient eth1

btw using a compaq v2000z with
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
along with
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
The manual way will be confusing for most people, the gui way does work, so i left it with that, if someone is more advanced then yeah they are free to do it that way.

> **scrubadub said:**
> both work at the same time for me with no problems, remember to check your route table if the traffic isn't going to the iface you want
hmmmm cheers, ill have to give that a look :)

im using basically the same laptop as you :cool:

---

### Post by ilushkin on 2006-10-27
thank you. really worked for me. This topic summarized can be seen here:
[http://www.networkadministrationblog.com/dell-1390-wireless-problems-on-linux-setup/](http://www.networkadministrationblog.com/dell-1390-wireless-problems-on-linux-setup/)

---

### Post by Brookranger on 2006-10-27
Have used Ubuntu before but quit because of wireless problems. So trying again.....and again and again....Using Broadcom 4318 Air Force One. When I sudo modprobe ndiswrapper I get the following:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
Of course, this is a binary file and I can't really read it but I checked and it does exist.
ndiswrapper is in /etc/modules
lsmod does not show ndiswrapper. 
ndiswrapper -l shows bcmwl5 driver present, hardware present
/etc/ndiswrapper shows bcmwl5 directory and modules.ndiswrapper so it seems to be installed.
My wireless does not show up at all in /system/administration/networking.
Wired connection shows up as eth0 when I use ifconfig but shows nothing for wireless. iwconfig shows no wireless. Have rebooted twice, once with only wireless, once with wired attached. Still nothing.
Sigh....
Anyone, please?????

---

### Post by nbound on 2006-10-27
are you sure bcm43xx is blacklisted?

also are you sure u got the right ndiswrapper package (theres two) get the one stated at the beginning of the howto

---

### Post by nickj6282 on 2006-10-27
This was a no-go for me. Made my wifi card disappear altogether. I've got an HP Pavilion dv8000 with the Broadcom 4318 card and an AMD64 CPU running the AMD64 Edgy (and yes, I used the AMD64 version of the .inf drivers).

Can anyone point me in the right direction?


Thanks,
-Nick

---

### Post by rogerdean on 2006-10-28
hello nbound and everyone
many thanks for the walkthrough. however i have no ethernet connection, or any connection other than wireless, so i can't download ndiswrapper in my ubuntu session. is there any other way to do this?
cheers
roger

---

### Post by nbound on 2006-10-28
use someone elses computer to get the deb files :)

---

### Post by rogerdean on 2006-10-28
yup, i can switch back to windows for that. sorry though, not the foggiest where to start... have half a brain but definitely still a newbie! 
many thanks again

---

### Post by nbound on 2006-10-28
its kinda hard to explain in a single post but the guys on the ubuntu irc channel could probably talk you through it

---

### Post by rogerdean on 2006-10-28
ok, i'll have a go. wish me luck...
cheers

---

### Post by rogerdean on 2006-10-28
ok folks, here's what worked for me...

i downloaded the windows drivers from nbound's link on the previous page

i also downloaded the following five deb packages:
ndiswrapper-common_1.18-1ubuntu2_all.deb
ndiswrapper-source_1.18-1ubuntu2_all.deb
ndiswrapper-utils-1.1_1.1-5_i386.deb
ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb
ndiswrapper-utils_1.1-5_all.deb

...from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=edgy&release=all)

i double-clicked each deb package to install them (some i think were present before, but not all)

then from the system-applications menu i opened 'windows wireless drivers' or whatever it's called, and told it to install bcmwl5.inf from nbound's drivers

...and that was it! i didn't even need a restart (although you may)

thanks to all for the help
Roger

---

### Post by Erik. on 2006-10-28
Hi,
I have done everything you say here into this HOW TO but when i rebooted my pc my wireless option into networking was gone.
How to get it back?

---

### Post by gustavo24 on 2006-10-28
This was EXTREMELY helpful.
Got a refurbished laptop with a Broadcom 4318 Air Force One a few days ago, drove myself crazy because I had seen ndiswrapper work flawlessly before, then saw your posting.

Worked great. Thanks!

---

### Post by nbound on 2006-10-28
> **Erik. said:**
> Hi,
I have done everything you say here into this HOW TO but when i rebooted my pc my wireless option into networking was gone.
How to get it back?

strange... are u sure you blacklisted bcm43xx

---

### Post by doug.barrett on 2006-10-28
> **nbound said:**
> strange... are u sure you blacklisted bcm43xx

I've done it too.  The only way I got it to work is to download ndiswrapper from source, and even then, it worked poorly because it wouldn't find the ESSID's, I would have to manually enter them (It's a pain when I have to connect to multiple wireless connections in a day).

Maybe I'll just go back to Dapper and do things that way.

---

### Post by trubblemaker on 2006-10-28
if your wifi disappeared all together odds are you might not have blacklisted bcm43xx.  check ```
dmesg 
```for any issues like ndiswrapper not loading, missing firmware blah blah blah, 

don't for get another easy way to have ndiswrapper load on boot is
```
sudo ndiswrapper -m  
``` 

PS the red howto in my sig has zipped debs if anyone is needing an all in one solution

---

### Post by Brookranger on 2006-10-29
Thanks so much to this forum, I finally got my BCM4318 working fine on Dell laptop. You guys are great!

---

### Post by etienne.navarro on 2006-10-29
The scripts found at this forum thread:
[http://www.ubuntuforums.org/showthread.php?p=1140976#poststop](http://www.ubuntuforums.org/showthread.php?p=1140976#poststop)
work fine if you replace the Dapper ndis-utils with the Edgy ones.

By the way, if your only connection is via wireless then be sure to get these ndiswrapper-utils debs  while you still have connectivity.
[https://launchpad.net/distros/ubuntu/edgy/i386/ndiswrapper-common/1.18-1ubuntu2](https://launchpad.net/distros/ubuntu/edgy/i386/ndiswrapper-common/1.18-1ubuntu2)
[https://launchpad.net/distros/ubuntu/edgy/i386/ndiswrapper-utils/1.1-5](https://launchpad.net/distros/ubuntu/edgy/i386/ndiswrapper-utils/1.1-5)

---

### Post by trubblemaker on 2006-10-29
actually the script that you point to and the red howto in my signature (same post) have been updated to edgy now.

---

### Post by nandasunu on 2006-10-31
Thanks, this is a lifesaver!

---

### Post by Bastanteroma on 2006-10-31
This method worked for me until I reinstalled edgy and tried it again (First install two days ago, then reinstall today).  The only difference I'm aware of is that during the first install, using the text installer, I chose the broadcom card as my primary interface, it scanned, then gave up.  This time I set the wired connection as primary.  Last time my wireless light lit up on reboot and worked, this time no dice.

Any ideas if this could have caused the problem and if it's fixable without reinstalling?

---

### Post by aroswald1977 on 2006-10-31
Amd Turion64, 64 bit edgy, bcm4318 shows up in lspci, got drivers, firmware, ndiswrapper configured, says hardware exists, bcm43xx blacklisted, = no dice.

any suggestions?

It worked perfectly under dapper, with ndiswrapper.

---

### Post by Das Goat on 2006-10-31
I did all of the steps, but when I get to editing /ect/modules, I only come up with an empty file that I can not save. I am sure that I need to edit the /ect/modules file tht already exisits, but I can not figure out how to do this. Sudo gedit /ect/modules just doesn't work.....

---

### Post by nbound on 2006-10-31
> **Das Goat said:**
> I did all of the steps, but when I get to editing /ect/modules, I only come up with an empty file that I can not save. I am sure that I need to edit the /ect/modules file tht already exisits, but I can not figure out how to do this. Sudo gedit /ect/modules just doesn't work.....
you've misspelt it.... etc as in etcetera, rather than ect

---

### Post by nbound on 2006-10-31
> **Bastanteroma said:**
> This method worked for me until I reinstalled edgy and tried it again (First install two days ago, then reinstall today).  The only difference I'm aware of is that during the first install, using the text installer, I chose the broadcom card as my primary interface, it scanned, then gave up.  This time I set the wired connection as primary.  Last time my wireless light lit up on reboot and worked, this time no dice.

Any ideas if this could have caused the problem and if it's fixable without reinstalling?

It should have worked that way... my card was set up that way :confused:

---

### Post by nbound on 2006-10-31
> **aroswald1977 said:**
> Amd Turion64, 64 bit edgy, bcm4318 shows up in lspci, got drivers, **firmware**, ndiswrapper configured, says hardware exists, bcm43xx blacklisted, = no dice.

any suggestions?

It worked perfectly under dapper, with ndiswrapper.

why do u need firmware for? this isnt like the other broadcom cards which need fwcutter... also i see ur running 64-bit... i honestly cant say with certainty this howto will work... but it should

---

### Post by naimarshad on 2006-10-31
hye guys i have same problem with my broadcom 4318 i installed the driver

when i do

sudo ndiswrapper -l

then i get this

Installed drivers:
bcmwl5          driver installed, hardware present 

but now connectivity any idea  or any idea what are the steps to get it up i can also see my both interface in network manager.

please help!

---

### Post by trubblemaker on 2006-10-31
> **aroswald1977 said:**
> Amd Turion64, 64 bit edgy, bcm4318 shows up in lspci, got drivers, firmware, ndiswrapper configured, says hardware exists, bcm43xx blacklisted, = no dice.

any suggestions?

It worked perfectly under dapper, with ndiswrapper.

yeah same issue here, I uninstalled and reinstalled from source, and everything is back to working.
I would advice  uninstalling ndiswrapper and installing ndis wrapper 1.8 (1.28 if you download from sourceforge), either from synaptic or from source it seems to be the most stable with edgy.  I can tell they've changed things, (not that this is everyones issues, but IPv6 had been blacklisted in my dapper on my computer before the upgrade and the same methods no longer worked after upgrade, I ended up blacklisting ipv6 to get rid of it this time.)  

*common mistake*

if you forget to uninstall the driver's and reinstall, you'll still have the same issues as before.
Really easy to do it from source

[http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.28.tar.gz?download go here to download ](http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.28.tar.gz?download go here to download ) 
```

mv ndiswrapper-1.28.tar.gz /some/location/of/your/choice
ndiswrapper -e bcmwl5
rmmod ndiswrapper
tar -zxvf ndiswrapper-1.28.tar.gz
cd ndiswrapper-1.28
sudo make uninstall
make 
sudo make install
ndiswrapper -i /path/to/drivers/bcmwl5.inf
modprobe ndiswrapper
sudo ndiswrapper -m

```
Your Done 


*note* > 
You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

if you don't have header files for your kernel,(`uname -r` will tell you your kernel) them use synaptic to fix you self up then run 'make' and 'sudo make install'  

if you don't have the drivers follow one of the howto's in my signature as they explain how to get drivers if you need them.


NOTE: you can try blacklisting ipv6 but this likely isn't the issue, i'm mearly pointing to a fact that **networking has changed since dapper** and the **most recent version of ndiswrapper should be installed in my experience**

unimportant to most people:
When I"m at school I had disable ip6v as it wasn't setup on my school network properly, this meant that I could get an ip but wouldn't let me surf.

---

### Post by nbound on 2006-10-31
> **naimarshad said:**
> hye guys i have same problem with my broadcom 4318 i installed the driver

when i do

sudo ndiswrapper -l

then i get this

Installed drivers:
bcmwl5          driver installed, hardware present 

but now connectivity any idea  or any idea what are the steps to get it up i can also see my both interface in network manager.

please help!
Set up the connection... (ie. SSID, any encryption you use, etc.)

---

### Post by fedleo on 2006-11-01
Broadcomm drive me crazy!
Sudo ndiswrapper -l command told me the driver is installed, but not a word about the hardware. I double checked the blacklist and the line "blacklist bcm43xx" is here. I rebooted twice. No way, also with ifconfig I cannnot see the wifi card.

On Dapper my 4309 worked like a charm... 
I wonder what is changed in less than a year.

---

### Post by nbound on 2006-11-01
Did u add ndiswrapper to your modules file? (else it wont load)... also if u used the driver linked here... they wont work... the are for the 4318 :)

---

### Post by fedleo on 2006-11-01
Yeah, I've set the module and no, I'm using the same driver used on dapper. So it's compatible with my card ;)

---

### Post by nbound on 2006-11-01
Hmmm thats pretty strange then... maybe an update will fix it soon :)

---

### Post by trubblemaker on 2006-11-01
totally sux but they changed some ground level stuff in the new networking, I know that they've atleast changed how they implmented ipv6 as my old method of turning it off stopped working.  So to get myself up and running I had to remove all traces of ndiswrapper and then re-install from late-est source and now I'm back up and running..... I also blacklisted ipv6 but I don't think the world needs to do that I'm just on a funky school network where ipv6 is badly implemented.

here's my fix for ya'll

this isn't necessary for all just people that have known ipv6 issues.
```
 echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist 
```

time to start of with a clean install from source 

and to be honest it totally sounds like I had the same issue, I think that you should uninstall everything, and build the 1.28 driver from scratch

that means removing all instances of ndiswrapper
```

sudo rmmod ndiswrapper
ndiswrapper -e bcmwl5
sudo apt-get remove ndis*

```
*stop* if you can think of anywhere else that their might be ndiswrapper parts lying around, now is the time to find and destroy them.

then get and install from source. 
*note* I won't tell you where to get new drivers for you card I assume you already have them and just need to get the card back up and running.  if you need them check one of the howto's in my signature after removing all instances of ndiswrapper.
```

cd ~
sudo apt-get install linux-headers-`uname -r`
wget http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz
tar -zxvf ndiswrapper-1.28.tar.gz
cd ndiswrapper-1.28
sudo make uninstall
make 
sudo make install
sudo modprobe ndiswrapper
ndiswrapper -i /path/to/drivers/bcmwl5.inf
sudo ndiswrapper -m

```
 just paste the commands and all should be well.  As a note, ndiswrapper will say that driver is present when ever the files are where there supposed to be means nothing in terms of working with the drivers....

hope this helps

---

### Post by Rudy507 on 2006-11-01
Hey guys,
I'm running into some problems.

First off: 
When I sudo modprobe ndiswrapper I get the following:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

I DO have bcm4xx (or whatever it is) blacklisted. 

Further...
I first tried using my windows driver of bcml5.inf. But somewhere along the way of blacklisting bcm4xx, installing this driver, and adding ndiswrapper to boot, ALL network connections aren't even showing up any more. 

I checked ndiswrapper -l, and it said that the driver bcml5 was invalid.

I uninstalled it, and tried installing the driver that is recommended (linked to in the first post on this thread). I got the same results on that driver when I ran ndiswrapper -l.

Any ideas?

---

### Post by trubblemaker on 2006-11-01
yeah I think it's a matter of not just 
```
ndiswrapper -e bcmwl5
```
I actually needed to remove ndiswrapper completely and starting from scratch.

you could try filing a bug and seeing if they issue a fix.

see my post above for quick instructions

---

### Post by naimarshad on 2006-11-01
Thanks alot nbound actually i got it up, i was missing the notification area, but some how when i configured the connection ssid it was up but i could not see the activity so I just added Add to Panel-> Network Monitor. But please can you guide me how can I discover my network automatically. Like autodiscovery for wirelss networks andy tool?

---

### Post by nbound on 2006-11-01
Once it set up the first time... it should detect other networks... at least... mine did under dapper. I havent been anywhere to test it since using edgy :)

---

### Post by aceracer195195 on 2006-11-05
i tried this hot-to and my card dissapeared all together.  I'm in the dark here and don't know what to do.  when i typed somhting in to check the drivers er somehting it told me that "bcmw15/inf is invalid" or somehting liek that.

Help please!

Ace

---

### Post by trubblemaker on 2006-11-05
you mistyped the driver and now it's not loading, hence you network card disapearing.
you typed:
```

ndiswrapper -i bcmw15[COLOR="Red"]/[/COLOR]inf

```
you needed to type
```

ndiswrapper -i bcmw15[COLOR="Red"].[/COLOR]inf

```
now I'm pretty sure you need to 
```

sudo rm -r /etc/ndiswrapper/bcmw15[COLOR="Red"]/[/COLOR]inf
ndiswrapper -i bcmw15[COLOR="Red"].[/COLOR]inf

```
and you should be back in business

---

### Post by aceracer195195 on 2006-11-05
the slash was a tyoo in my post, i didn't catch it.
i wll check that i didn't put a slash tough.

Ace

---

### Post by aceracer195195 on 2006-11-05
> **trubblemaker said:**
> you mistyped the driver and now it's not loading, hence you network card disapearing.
you typed:
```

ndiswrapper -i bcmw15[COLOR="Red"]/[/COLOR]inf

```
you needed to type
```

ndiswrapper -i bcmw15[COLOR="Red"].[/COLOR]inf

```
now I'm pretty sure you need to 
```

sudo rm -r /etc/ndiswrapper/bcmw15[COLOR="Red"]/[/COLOR]inf
ndiswrapper -i bcmw15[COLOR="Red"].[/COLOR]inf

```
and you should be back in business

I did what you instructed, i did type it correctly an got the same thing, nothing.

Any ideas? i really want this to work.

Ace

---

### Post by trubblemaker on 2006-11-05
the usual issues are these:

you didn't blacklist the native driver
check that with ```
cat /etc/modprobe.d/blacklist | grep bcm 
``` comes up blank,

you had a previous install of the driver, updated.  This has 'caused a lot of issues, it is my opinion that ndiswrapper doesn't upgrade well. (I suggest uninstalling, and [reinstalling from source]("http://ubuntuforums.org/showpost.php?p=1696835&postcount=33")) but if you're already 1/2 way through try this

you should remove the driver, before up grading, otherwise you have to do it again after, to do that:

```
 
sudo ifconfig wlan0 down
sudo rmmod ndiswrapper
ndiswrapper -e bcmwl5
ndiswrapper -l
ndiswrapper -i path/to/driver/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ifup wlan0

```

the ndiswrapper -l is to make sure it went away, if it didn't you can do wierd stuff like blacklist it and reboot, and then you ndiswrapper to remove the driver, but why get crazy, just clobber it with
```
 sudo rm -r /etc/ndiswrapper/bcmwl5 
```
and then carry on with 
```
 ndiswrapper -i path/to/driver/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ifup wlan0

```
anyways hope this helps

---

### Post by aceracer195195 on 2006-11-05
first when i 
"sudo modprobe ndiswrapper" i got a 
"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): invalid argument"

and when i tried to "sudo ifup wlan0" the device wasn't there.

So am i like totally messed up or what?

Ace

---

### Post by trubblemaker on 2006-11-05
nah just reboot and try it. failing that I would really suggest uninstalling and building from source, as I posted in my last link, it's really quick and *works* Give me a sec and I'll find a script that does it all for you so you don't even have to think....

---

### Post by trubblemaker on 2006-11-05
This script is designed to be simple and not for experience users, it works, all you need is to know where the driver for your card is.  

**Best practice:** you shouldn't run or create the script, but you should just run the commands from the script in a terminal manually one at a time.  You should stop doing any commands that have any strange or 'kinda-strange' output.  You should post that out put to this thread. And not continuing until you've corrected the error's or strangeness.  And as always you should ask questions.

**For people that just want a quick script, and don't want to paste each command to a command prompt:** that gets your ndiswrapper working again use the following instructions.

In a terminal:
change into the directory that contains your driver bcmwl5.sys/bcmwl5.inf file:
```
 cd /path/to/where/bcmwl5.inf-lives/ 
```
open a file to write to:
```
cat > file-name
```
Here's the code to paste:
```

#/bin/bash
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist # blacklist native driver
sudo rmmod ndiswrapper            # removes ndiswrapper from kernel
ndiswrapper -e bcmwl5             # removes old loaded driver, this a critical step
                                  
sudo apt-get remove ndiswrapper*   # removes any ndiswrapper packages installed 
                                  

cd ~                              # move to home directory

# following two instructions install necessary packages to build from source

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

# following two instructions download and unzip ndiswrapper
# you can get the source also by browsing to it : http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148
wget http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz
tar -zxvf ndiswrapper-1.28.tar.gz  # untars the file

cd ndiswrapper-1.28                # or whatever version you downloaded

# necessary to run twice, to show nothing left to remove, technically could get away with saying it once
sudo make uninstall
sudo make uninstall

# build and install steps
make 
sudo make install


sudo modprobe ndiswrapper         #load ndiswrapper into the kernel

ndiswrapper -i bcmwl5.inf         #load windows drivers into ndiswrapper
sudo ndiswrapper -m               # writes alias "wlan0" so it referred to as wlan0

# tries to connect to the net with default settings in /etc/interfaces/ndiswrapper
# it reports success or fail
sudo ifup wlan0 && echo "Succesfully connected to the INTERNET" && exit
echo "Failed to connect to the internet."

```
after you past the code then press <crtl> + 'd ' at the same time.
then change the permissions of the file so it can run
```
chmod u+x file-name
```
then run it
```
./file-name
```

seroiusly no thinking or experience involved, works like a charm, even tries to connect to the net for you.

[COLOR="Red"]edit[/COLOR] removed "yes |" from install/remove as safer is better.

---

### Post by aceracer195195 on 2006-11-05
so i just follow the instruction in that last link and i should be able to connect to the internet?

I'm still kinda lost on this.

Ace

---

### Post by trubblemaker on 2006-11-05
try going onto the web, if you can great! otherwise please give me output of the following commands.

yeah, you should what's the output of the following commands:

```

ifconfig
iwconfig
iwlist scan
dmesg | grep ndis
ndiswrapper -l

```

---

### Post by aceracer195195 on 2006-11-05
fist it wouldn't let me d the cd /path/to/bcm15.inf thing, said it wasn't a valid directory (even tho the folder was on my desktop).

then after making a new file inside the folder and running what you posted it gave me what i owuld call the linux blue screen of death.  something about uninstalling what i was already using and it'd make somhting unbootable.

no internet sucess.

i'll post the results of those commands in like 10 minutes.

Ace

---

### Post by trubblemaker on 2006-11-05
ok my bad I wanted you to change to the folder with bcmwl5.inf in it. I didn't mean change to the file.
This is a clearer way of saying it:
```
cd /path/to/where/bcmwl5.inf-lives/
```

as for the other error message and the blue screen of death, wish I could see what you meant, I didn't know linux had an equivalent.  I have seen bcm43xx and ndiswrapper, freeze my screen, but that's when I hadn't black listed the driver,

this will fix that.
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by aceracer195195 on 2006-11-05
wel here's te codes you asked for, 2 were invalid (typo?).  i'll try the new stuff

Ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

dmesg | gred ndis
bash: gred: command not found

ndiswrapper &#8211;l
bash: ndiswrapper: command not found


Ace

---

### Post by trubblemaker on 2006-11-05
I meant:
```
dmesg | gre[COLOR="Red"]p[/COLOR] ndiswrapper
```


can you post the output of running the script from the directory?
or do you know where the script fails, or lists an error?
you can run each step one after another and then post all the input, I'm sure we can find the error and get you up and running.  and it should only take another 3-4 posts.  Minus spelling errors, on both our parts.  Sometimes, I don't read what I post before posting, ouch. I can't believe some people listen to me!

---

### Post by aceracer195195 on 2006-11-05
this is the blue screen i was talking about.  it appears like 1/2 way though the running.  still no connct plus my card still isn't under networking.

You are running a kernel (version 2.6.17-10-generic) and attempting to    &#9474;  
 &#9474; remove the same version. This is a potentially disastrous action. Not     &#9474;  
 &#9474; only will /boot/vmlinuz-2.6.17-10-generic be removed, making it           &#9474;  
 &#9474; impossible to boot it, (you will have to take action to change your boot  &#9474;  
 &#9474; loader to boot a new kernel), it will also remove all modules under the   &#9474;  
 &#9474; directory /lib/modules/2.6.17-10-generic. Just having a copy of the       &#9474;  
 &#9474; kernel image is not enough, you will have to replace the modules too.     &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; I repeat, this is very dangerous. If at all in doubt, answer Yes. If you  &#9474;  
 &#9474; know exactly what you are doing, and are prepared to hose your system,    &#9474;  
 &#9474; then answer No.                                                           &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;  Do you want to abort removal now?


Ace

---

### Post by trubblemaker on 2006-11-05
found it, apparently sometimes the regex can get a little crazy
I found the error and have changed it, you need to change this line in the files:

[COLOR="Red"]yes | sudo apt-get remove ndis*[/COLOR]
to 

yes |  sudo apt-get remove ndiswrapper*

then re-run the file and all should be well. I'm sorry, I didn't get the same results on my server, but it's just a server so didn't have many packages on it, when I ran it on my desktop box I got the issue that you ran into with ndis*.

---

### Post by aceracer195195 on 2006-11-05
output of "dmseg | grep ndis"

[17179595.344000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)

Ace

---

### Post by aceracer195195 on 2006-11-05
ok, this is what i get when i run the fixed code.

./file-name: line 3: ndiswrapper: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: Command line option 'r' [from -r] is not known.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
tar: w: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: ndiswrapper-1.28.tar.gz: Not found in archive
tar: Error exit delayed from previous errors
./file-name: line 10: cd: ndiswrapper-1.28: No such file or directory
make: *** No rule to make target `uninstall'.  Stop.
make: *** No rule to make target `uninstall'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
./file-name: line 16: ndiswrapper: command not found
sudo: ndiswrapper: command not found
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.


Ace

---

### Post by trubblemaker on 2006-11-05
please run in a terminal then try running the script again if they succeed.
```

sudo apt-get install linux-headers-2.6.17-10-generic
wget http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz

```

---

### Post by aceracer195195 on 2006-11-05
i got the same thing as before.

my card still isn't recognised unde networking, does that help at all?

Ace

---

### Post by trubblemaker on 2006-11-05
well I need you to run the commands starting with the "wget ....", commands as your still failing one of the steps,.  likely the wget,  as I saw the error you had last time.  from now on if the output of a command say anything that looks even remotely not normal or could maybe be bad, but you don't know you need to post the output to the forum so I can take it into account when I tell you to try some steps.... it's all about communicatoin.

so what is the out put of the wget command I told you to do last time?

---

### Post by pwlodarczak on 2006-11-06
I always hat to get the latest ndiswrapper from here:
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
to get the bcm4318 working, worked on dapper and edgy. The one I installed through synaptic pm never worked.

---

### Post by Harry the Spider on 2006-11-06
Fantastic! This worked first time after several fruitless hours spent trying out other threads! In case it helps anyone my wireless adapter is a Belkin G+ Notebook card Belkin part number F5D7011 - obviously it has the BCM4318 in its innermost depths, hence all the trouble.
Thank you nbound for a superbly clear (and correct) set of instructions!

Edit:
The above only worked for me after the first re-boot.
Next time I tried the power light on the card lit up but nothing else happened!
Am going to do a clean install of Edgy then try my luck with fwcutter....

---

### Post by aceracer195195 on 2006-11-06
output of wget command

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

Then i re-ran the earler edited scrpit as instructed and got the same output as i had posted earler.

Ace

---

### Post by weematt on 2006-11-06
I have a HP DV8000, and in the process of upgrading to Edgy, my broadcom 4318  stopped working.

dmesg talked about "windows driver unable to initialize device" or something similar.  I thought maybe it was IRQ problems, tried noapic acpi=off and irqpoll etc., none of which worked, but I did find a solution (thanks to this list here).

SOLUTION: Installing ndiswrapper from source.  My guess as to why this works is because the link on this list (several pages back) is for 1.22 whereas edgy comes with 1.8.  I hazard that for some reason, the combination of this card, and ndiswrapper 1.8 is not good?  Just a guess -- but I thought I'd throw this out there.

Good luck everyone.  I've been so frustrated in trying to get linux up and running, but this is a HUGE step forward.  (Only stupid f-ing ati radeon 200m dri to go :/)

Good luck!

-Matt

---

### Post by mssever on 2006-11-07
> **trubblemaker said:**
> ```

#/bin/bash
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist # blacklist native driver
sudo rmmod ndiswrapper            # removes ndiswrapper from kernel
ndiswrapper -e bcmwl5             # removes old loaded driver, this a critical step
yes |  sudo apt-get remove ndiswrapper*   # removes any ndiswrapper packages installed 
cd ~                              # move to home directory

# following two instructions install necessary packages to build from source
yes | sudo apt-get install build-essential
yes | sudo apt-get install linux-headers-`uname -r`

```
Running ```
yes | sudo apt-get foo
``` is dangerous unless you know what you're doing. Who knows what you could be automatically saying yes to? Better to run apt-get by itself--especially in a portable script. Apt-get asks questions for good reasons.

---

### Post by trubblemaker on 2006-11-07
in this case we're talking about installing build-essentails and linux headers and installing. I completely agree that it's good to not blindly say yes to apt-get.  I will alter my post to make specific mention of your well founded, warning.
*update*  script and post have been changed to include best practices and warnings.

---

### Post by etienne.navarro on 2006-11-08
> **trubblemaker said:**
> actually the script that you point to and the red howto in my signature (same post) have been updated to edgy now.

Thanks. I'll add this to the [http://ubuntuguide.org]("http://ubuntuguide.org/") wiki

---

### Post by trubblemaker on 2006-11-09
> **etienne.navarro said:**
> Thanks. I'll add this to the [http://ubuntuguide.org]("http://ubuntuguide.org/") wiki
here's another link worthy of looking over that builds ndiswrapper from source.

[http://ubuntuforums.org/showpost.php?p=1699287&postcount=451](http://ubuntuforums.org/showpost.php?p=1699287&postcount=451)

---

### Post by mrhonne on 2006-11-10
I've a hp nx8220 with this ill-supported bcm4318. I tried many different howtos using bcm43xx or ndiswrapper, but none of them worked.
I've also tried this howto vainly for the first ti[SIZE="5"][/SIZE]me, because I made a mistake:

To get the bcmwl5.inf and bcmwl5.sys file I downloaded the *newest* driver of hp.com, but ndiswrapper didn't work with them ](*,) 
Following a sudden inspiration I downloaded the *oldest* driver for bcm4318 (version 4.00 B instead of 6.00 A) from
[http://h18007.www1.hp.com/support/files/hpcpqnk/us/revision/9083.html](http://h18007.www1.hp.com/support/files/hpcpqnk/us/revision/9083.html)
and Hooray! it works! :-D 

[SIZE="3"]
So if this ndiswrapper howto doesn't work for you, try an older windows driver.[/SIZE]

---

### Post by pratik5705 on 2006-11-10
Thanks for the great post. It worked. Thanks again!!!


> **scrubadub said:**
> some notes i think should be added
where to get the drivers
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

no need to reboot
sudo modprobe ndiswrapper
(make sure you press any hardware buttons to turn on wifi)
sudo ifconfig eth1 up

this should be all you need to do, for some reason it didnt show up in ifconfig -a until i manually brought it up. it also shows up in the gui network config. Then I do this to pull an ip addy
sudo iwconfig eth1 essid SSIDNAME;sudo dhclient eth1

btw using a compaq v2000z with
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
along with
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

both work at the same time for me with no problems, remember to check your route table if the traffic isn't going to the iface you want

---

### Post by pastorjay on 2006-11-10
Guys, I am putting this in as many threads about the broadcomm as I can.  The new nvidia drivers cause some kind of conflict with the broadcomm wireless cards.  Not sure what happens, but as soon as I unloaded the nvidia drivers, and went with the default drivers the wireless function all of a sudden is working perfectly, and not dropping out anymore.  Just a heads up!  And here is hoping that nvidia can fix this real quick, as you cannot use any 3d functions of the card, which means no Beryl and the sorts.

---

### Post by trubblemaker on 2006-11-10
pastorjay does that new driver come with edgy? or is it something you installed, it would explain, some things, but there might be a fix for it.

---

### Post by pastorjay on 2006-11-10
It is the new driver from nvidia itself.  From what I can tell, the ndsiwrapper uses (at least on my machine) IRQ #177.  It seems that for some reason or another, the nvidia driver shuts that IRQ down.  Look at my posts here to see more of this.  [http://ubuntuforums.org/showthread.php?t=295787]("http://ubuntuforums.org/showthread.php?t=295787")

If I remember right, I ran dmseg in the console.  About half way down it told me that ndiswrapper was using IRQ #177.  At the very end of the output, it told me that IRQ #177 was disabled.  If you are having these issues and using the new nvidia driver, you may want to look at this.

If there is a work around, that would be great.  As of now, I am actually looking for a replacement mini WiFi card for my laptop.  I do not want to have to go through this every time I install any version of linux, and it seems the Intel chipped cards are better to work with.

---

### Post by trubblemaker on 2006-11-10
k after installing the new driver use the [from source link]("http://ubuntuforums.org/showpost.php?p=1699287&postcount=451") in my signature and tell me if that fixes you up.

---

### Post by DavidTangye on 2006-11-12
I find I can run both OK.

---

### Post by j o e l on 2006-11-12
Worked great, nbound!  Thanks!

Took me weeks to get wireless sorted out on Dapper, and using you guide, I had it done in 15 minutes!

---

### Post by xiownthisplacex on 2006-11-15
Ok, i did the first command and when i do sudo rmmod bcm43xx i get this:
$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules


ANY HELP PLEASE?

---

### Post by trubblemaker on 2006-11-15
no worries you don't have ndiswrapper loaded. you can continue with the steps and ignore errors that you get for ndiswrapper commands until you install it from source. 

ps  always willing to help, no need to shout.

---

### Post by dragonlor20 on 2006-11-17
> **nbound said:**
> why do u need firmware for? this isnt like the other broadcom cards which need fwcutter... also i see ur running 64-bit... i honestly cant say with certainty this howto will work... but it should

The driver you sent us to though seems to be the 32-bit driver, which after installed and upon running
```
dmesg
```

gives the message

> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

I am looking for the 64-bit driver now, after I find it I will post whether or not this helped...

...

It seems that a bcmwl564.inf doesn't exist, and edgy wants this file for the 64-bit version.

---

### Post by trubblemaker on 2006-11-17
check the red howto in my signature, it claims a 64bit package for you to use ndiswrapper.

ok I checked it was still there here's a [link to the driver]("http://www.box.net/public/oy219x8mlz")

still the red howto might be helpfull....

---

### Post by Sir_Yaro on 2006-11-18
works for me with one exception. i had to add
```
modprobe ndiswrapper
```
to /etc/rc.local
instead of 
```
ndiswrapper
```
in /etc/modules

---

### Post by bourne- on 2006-11-23
> **nbound said:**
> **Download ndiswrapper from Synaptic**
[LIST]
[*]System -> Administration -> Synaptic Package Manager
[*]Search for ndiswrapper
[*]Download "ndiswrapper-utils-1.8" and "ndiswrapper-common"
[/LIST]

**Blacklist native bcm43xx drivers**
[LIST]
[*]Type:
```
sudo gedit /etc/modprobe.d/blacklist
```
[*]Add the line:
```
blacklist bcm43xx
```
[*]After saving type at the terminal:
```
sudo rmmod bcm43xx
```
[/LIST]

**Get windows drivers and install them**
[LIST]
[*]Download and extract windows drivers to a folder of your choice (drivers can be found here: [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip))
[*]Install them in ndiswrapper:
```
sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf
```
[*]Check to see if hardware found
```
sudo ndiswrapper -l
```
[/LIST]

**Setup ndiswrapper to load driver (and itself) at startup**
[LIST]
[*]Edit the following file:
```
sudo gedit /etc/modules
```
[*]Add a line which says:
```
ndiswrapper
```
[*]Restart
[/LIST]

**During restart the "Wireless On" light for your laptop should turn on (Well it did for me: your results may vary)**
[LIST]
[*]If light does not show try pressing wireless button (incase left in off mode)
[/LIST]

**Setup Wireless Card in Networking** (Manual setup is also fine)
[LIST]
[*]System -> Administration -> Networking
[*]Enable wireless connection and configure all the settings
[*]Disable wired connection (wireless and wired connections do not seem to work simultaneously)
[*]Use the internet/LAN!
[/LIST]

***Hope it helped!***


K I tried to blacklist 43xx in the blacklist file but I am being denied access to it. And I do not get prompted to login in as admin. So how can I edit it? I have tried changing the permissions on it using 'chmod' but that doesn't work. I also tried edited it in VI but that didn't work either, I was denied access. So what can I do?

thanks
todd

---

### Post by trubblemaker on 2006-11-23
really should work with


```
sudo vi /etc/modprobe.d/blacklist
```

or onliner

```
sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
```

---

### Post by bourne- on 2006-11-23
> **trubblemaker said:**
> really should work with


```
sudo vi /etc/modprobe.d/blacklist
```

or onliner

```
sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
```

yeah crap I forgot to us sudo
so i did this: I navigated to /etc/mobprobe.d/
one I was there I put in:
```
sudo gedit blacklist
```
and it modified the file no problem
could I of used?
```
sudo vi blacklist
```

---

### Post by trubblemaker on 2006-11-23
yup

---

### Post by bourne- on 2006-11-23
K well this tutorial did not work for me. I followed it exactly and all I was successful at was making my wireless connection disappear all together. System/Administration/Networking , all that is listed there is ethernet connection and modem connection.

Thanks for another tutorial
will have to keep looking till i find one that works for me

---

### Post by trubblemaker on 2006-11-23
check my signature for a couple different ones, the last one the [ndis from source]("http://ubuntuforums.org/showpost.php?p=1699287&postcount=451") is currently my favorite for ease of use and "just works"  to be honest alot of people have had issues with installing from packages recently.  I don't know why but they have so I hope you find one of the ones in my signature help full

|
|
|
V

---

### Post by nitricacid on 2006-11-25
Hello everyone.
I had just gotten an Compaq Persario (C303NR)(brand new) and I have to say that after I installed Kubuntu everything worked rite out of the box.
The only 
problem I have (as if you couldn't guess) is my Broadcom Wireless card (as listed in the tutorial).

Below is the following code that I got after folling this 'How-to' to a T.
Sadly to say that my wireless still doesn't not work.

Any help would be greatly apreaciated. 
also, if anyone could recommend a good COMPATIBLE wireless PCcard (In case I cant get this onboard to work.

Code:
null@ubuntu:~$ sudo pico /etc/modprobe.d/blacklist
Password:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
blacklist bcm43xx

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

null@ubuntu:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

null@ubuntu:~$ sudo ndiswrapper -i /home/null/stuph/driver/80211g/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it

null@ubuntu:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

null@ubuntu:~$ sudo pico /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper


Thanks In Advance.

---

### Post by trubblemaker on 2006-11-27
you can "manually" delete the driver by deleting the folder in /etc/ndiswrapper, so it would look like
```
sudo rm -r /etc/ndiswrapper/bcmwl5
```

then try reinstalling the driver.

*note* sometimes this howto **doesn't work for people that upgraded from dapper** and you might want to check out some of the howto's in my signature.  Try a different method though, try the "ndis from soure" or the native driver as the packages are an issue not the instructions.

---

### Post by 4martin1 on 2006-12-01
Big thanx to you nbound!!! Thanks to your instructions, I managed to install my asus 138g V2 wireless card.

---

### Post by shartke on 2006-12-01
None of them worked for me.  I rebooted and the light came on but I cannot see any wireless networks.  I tried sudo iwconfig wlan0 essid SSID key KEY and then dhclient after that.  Did not work.  iwconfig shows that the device is there. Any suggestions

---

### Post by zspada15 on 2006-12-01
It didn't work for me. In dapper it worked, but now it works natively with bcm43xx in edgy

---

### Post by trubblemaker on 2006-12-01
> **shartke said:**
> None of them worked for me.  I rebooted and the light came on but I cannot see any wireless networks.  I tried sudo iwconfig wlan0 essid SSID key KEY and then dhclient after that.  Did not work.  iwconfig shows that the device is there. Any suggestions
what's your output for:
```

sudo iwlist scan
ndiswrapper -l
dmesg | grep ndis
iwconfig 
ifconfig
cat /etc/network/interfaces

```

don't for get K.I.S.S., get the wireless set up on an un-encrypted network first, once that works then turn on the encryption, otherwise it's hard to tell if it's the encryption or the wirlesss card that's giving you issues.

---

### Post by hush on 2006-12-02
[QUOTE=trubblemaker;1719106]
open a file to write to:
```
cat > file-name
```

heres where I'm stuck :(
```
adam@adam-laptop:~/drivers/80211g$ cat > driverfile
bash: driverfile: Permission denied
```

---

### Post by trubblemaker on 2006-12-02
you don't have permissions to write to that folder, either create it in another folder, like "/home/my-slick-user-name" or create it with sudo.

ie

```
sudo cat > file-name
```

---

### Post by woopud on 2006-12-02
Okay, i'm trying to get my BCM 4306 to work in Edgy and got this far:

```
woopud@woopud-laptop:~$ sudo ndiswrapper -i /woopud/80211g/bcmwl5.inf
Password:
bcmwl5 is already installed. Use -e to remove it
woopud@woopud-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
woopud@woopud-laptop:~$ 

```

What's wrong with this ?
Bert

---

### Post by woopud on 2006-12-03
Pretty sure I did but somehow I get the following now:

woopud@woopud-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
bcmwl5a invalid driver!
bcmwl5.sys      invalid driver!
woopud@woopud-laptop:~$ 

Bert

---

### Post by woopud on 2006-12-03
Okay, so I removed all three drivers and started over.  Got the drivers from the first post and put them in a folder named "wifi" and put that in my 'home' folder named "woopud" then i did this: 

woopud@woopud-laptop:~$ sudo rm -r /etc/ndiswrapper/bcmwl5
woopud@woopud-laptop:~$ sudo ndiswrapper -i ~/woopud/wifi/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/woopud/woopud/wifi/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
woopud@woopud-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
woopud@woopud-laptop:~$

---

### Post by trubblemaker on 2006-12-03
> **woopud said:**
> Okay, so I removed all three drivers and started over.  Got the drivers from the first post and put them in a folder named "wifi" and put that in my 'home' folder named "woopud" then i did this: 

woopud@woopud-laptop:~$ sudo rm -r /etc/ndiswrapper/bcmwl5
woopud@woopud-laptop:~$ sudo ndiswrapper -i ~/woopud/wifi/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/woopud/woopud/wifi/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
woopud@woopud-laptop:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
woopud@woopud-laptop:~$

I think your path was off try removing all the drivers again and then use this command:

```
sudo ndiswrapper -i ~/wifi/bcmwl5.inf
```

alternatively you can just move to the folder containing the driver and run ndiswrapper:

```

cd /home/woopud/wifi/
sudo ndiswrapper -i bcmwl5.inf
```

---

### Post by woopud on 2006-12-03
Okay, I figured out what I did wrong, got rid of the drivers and installed the right one.  But wireless still doesn't show up in Network, just the wired ethernet and the modem.

Bert

---

### Post by trubblemaker on 2006-12-03
ok so can you please post the output of the following
```

ifconfig
iwlist scan
iwconfig
lspci | grep roadcom
cat /etc/network/interfaces
ndiswrapper -l
dmesg | ndis
sudo dhclient wlan0

```

it will help me to determine where your at and how you're doing

---

### Post by LostShootingStar on 2006-12-03
just want to say thanks for posting this, it helped me greatly.

---

### Post by woopud on 2006-12-03
> **trubblemaker said:**
> ok so can you please post the output of the following
```

ifconfig
iwlist scan
iwconfig
lspci | grep roadcom
cat /etc/network/interfaces
ndiswrapper -l
dmesg | ndis
sudo dhclient wlan0

```

it will help me to determine where your at and how you're doing

Okay, here goes:

```
woopud@woopud-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:47:92:2E  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe47:922e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2707299 (2.5 MiB)  TX bytes:806149 (787.2 KiB)
          Interrupt:185 Base address:0x2800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

woopud@woopud-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

woopud@woopud-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

woopud@woopud-laptop:~$ lspci | grep broadcom
woopud@woopud-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

woopud@woopud-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
woopud@woopud-laptop:~$ dmesg | ndis
bash: ndis: command not found
woopud@woopud-laptop:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
woopud@woopud-laptop:~$ 




```

Bert

---

### Post by trubblemaker on 2006-12-03
One spelling error on my part and one on yours:
```
lspci | grep [COLOR="Magenta"]roadcom[/COLOR]
dmesg | [COLOR="Magenta"]grep[/COLOR] ndis
```
also need this too:

```

cat /etc/modprobe.d/blacklist

```
it looks like you haven't modprobed ndiswrapper yet:
```

modprobe ndiswrapper
iwlist scan

```

---

### Post by woopud on 2006-12-04
I really appreciate you taking the time to help me !

Bert

```
woopud@woopud-laptop:~$ lspci | grep roadcom
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
woopud@woopud-laptop:~$ dmesg | grep ndis
[   57.904755] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   58.006424] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   58.006436] ndiswrapper (load_sys_files:215): couldn't prepare driver 'bcmwl5'
[   58.007174] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'
woopud@woopud-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist bcm43xx
woopud@woopud-laptop:~$ modprobe ndiswrapper
woopud@woopud-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

woopud@woopud-laptop:~$ 


```

---

### Post by trubblemaker on 2006-12-04
so as dmesg says:

> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B

you need to find the correct 64 bit driver.  check the read howto in my signature, it has a 64 bit method in it

---

### Post by woopud on 2006-12-04
There are four different links in your signature ?
Does that mean I have to get rid of ndiswrapper and use fwcutter ?

Bert

---

### Post by woopud on 2006-12-04
Okay, uninstalled the bcmwl5 driver and installed the 64 bit driver and get the following now :

```
woopud@woopud-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:47:92:2E  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe47:922e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:879651 (859.0 KiB)  TX bytes:84257 (82.2 KiB)
          Interrupt:185 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

woopud@woopud-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

woopud@woopud-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

woopud@woopud-laptop:~$ lspci |grep roadcom
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
woopud@woopud-laptop:~$ cat /etc/netwrk/interfaces
cat: /etc/netwrk/interfaces: No such file or directory
woopud@woopud-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

woopud@woopud-laptop:~$ ndiswrapper -l
Installed drivers:
netbc564                driver installed, hardware present 
woopud@woopud-laptop:~$ dmesg | grep ndis
[   52.578243] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   52.719947] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[   52.722552] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[   52.728592] Modules linked in: ndiswrapper sbp2 lp 8139cp pcmcia 8139too mii yenta_socket rsrc_nonstatic pcmcia_core joydev snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device tsdev parport_pc parport snd i2c_nforce2 i2c_core shpchp pci_hotplug evdev psmouse serio_raw pcspkr soundcore snd_page_alloc ext3 jbd ehci_hcd ohci_hcd usbcore ohci1394 ieee1394 ide_generic ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[   52.728678] Pid: 3142, comm: loadndisdriver- Tainted: P      2.6.17-10-generic #2
[   52.728785] Process loadndisdriver- (pid: 3142, threadinfo ffff81001a174000, task ffff81001fc0d710)
[   52.728832] Call Trace: <ffffffff8832a06e>{:ndiswrapper:win2lin5+25}
[   52.728977]        <ffffffff8833307d>{:ndiswrapper:NdisAllocateMemoryWithTag+13}
[   52.729048]        <ffffffff8832a03b>{:ndiswrapper:win2lin3+17} <ffffffff8832a03b>{:ndiswrapper:win2lin3+17}
[   52.729190]        <ffffffff88332ca7>{:ndiswrapper:NdisMAllocateSharedMemory+71}
[   52.729265]        <ffffffff8832a06e>{:ndiswrapper:win2lin5+25} <ffffffff802cbbfe>{alternate_node_alloc+126}
[   52.729383]        <ffffffff88344407>{:ndiswrapper:miniport_init+167} <ffffffff8833efb0>{:ndiswrapper:IoSyncForwardIrp+144}
[   52.729515]        <ffffffff88344560>{:ndiswrapper:NdisDispatchPnp+144}
[   52.729574]        <ffffffff8833daed>{:ndiswrapper:IoInitializeIrp+45}
[   52.729638]        <ffffffff8833dbc6>{:ndiswrapper:IoAllocateIrp+134} <ffffffff8832a027>{:ndiswrapper:win2lin2+14}
[   52.729766]        <ffffffff8833d1de>{:ndiswrapper:IofCallDriver+62} <ffffffff8833e56f>{:ndiswrapper:IoBuildSynchronousFsdRequest+47}
[   52.729891]        <ffffffff883428dc>{:ndiswrapper:IoSendIrpTopDev+172}
[   52.729959]        <ffffffff8833d5c5>{:ndiswrapper:IoGetAttachedDevice+293}
[   52.730029]        <ffffffff88342b4c>{:ndiswrapper:pnp_start_device+76}
[   52.730103]        <ffffffff88342dba>{:ndiswrapper:wrap_pnp_start_device+538}
[   52.730267]        <ffffffff8033ed07>{__pci_register_driver+87} <ffffffff8832ea23>{:ndiswrapper:wrapper_ioctl+1155}
[   52.730522]  <3>ndiswrapper (wrapper_init:129): loadndiswrapper failed (35072); check system log for messages from 'loadndisdriver'
[   52.737588] Modules linked in: ndiswrapper sbp2 lp 8139cp pcmcia 8139too mii yenta_socket rsrc_nonstatic pcmcia_core joydev snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device tsdev parport_pc parport snd i2c_nforce2 i2c_core shpchp pci_hotplug evdev psmouse serio_raw pcspkr soundcore snd_page_alloc ext3 jbd ehci_hcd ohci_hcd usbcore ohci1394 ieee1394 ide_generic ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan vesafb capability commoncap vga16fb cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit softcursor
[   52.737850]        <ffffffff8033eb28>{pci_unregister_driver+24} <ffffffff8832e4a6>{:ndiswrapper:loader_exit+134}
[   52.737956]        <ffffffff88342289>{:ndiswrapper:module_cleanup+9} <ffffffff8815d0fc>{:ndiswrapper:wrapper_init+252}
woopud@woopud-laptop:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
```

Am I going in the right direction now ?

---

### Post by trubblemaker on 2006-12-04
in my post:
read = red + typo.

I was trying to say the [COLOR="Red"]red[/COLOR] howto in my signature, and I have to say that I don't think that you installed the correct 64bit driver for the bcm4318. as you can see it's still having issues loading.  if you still boot into windows with that machine you can use windows to grab the actual files it uses. (the ones we want.)

to do this Start>Control Panel>Network Connections
then right click on Local Area Connections 
         select 'Properties'
    
Click on 'Configure'

Click on 'Drivers' tab

Click on 'Driver Details'

There is the exact location of the driver that windows uses and the one that you want to use for your linux.

Then do the install for ndiswrapper, you should be good to go.  If you can no longer boot into windows, use the red howto to get yourself up and running.

---

### Post by woopud on 2006-12-04
Well the driver that shows up there is the bcmwl5 which I allready installed before.

Bert

---

### Post by trubblemaker on 2006-12-05
well I'm at a cross roads then I don't know what to tell you as I saw your dmesg that said definately that it didn't like it, I say that you use the [COLOR="Red"]red[/COLOR] howto to install a 64bit bit driver

---

### Post by Benitez on 2006-12-05
Thank you *so* much! I have Wireless on my laptop again; I am actually writing this in thanks wirelessly on my computer.

Please, PLEASE make this a sticky so that others don't have to search for hours on end!

--Benitez :twisted:

---

### Post by trubblemaker on 2006-12-05
Benitez: fyi check out the [ubuntu wiki]("https://wiki.ubuntu.com/") for more great howto's if you ever get stuck on something.

---

### Post by woopud on 2006-12-06
Somehow everything got messed up, now I installed Edgy i386 on my laptop, went thru all the steps installing ndiswrapper, networkmanager and the right driver but then after reboot the wireless doesn't show up under System > Administration > Networking

```
woopud@woopud-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:47:92:2E  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe47:922e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:712134 (695.4 KiB)  TX bytes:85480 (83.4 KiB)
          Interrupt:185 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

woopud@woopud-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

woopud@woopud-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

woopud@woopud-laptop:~$ lspci | grep roadcom
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
woopud@woopud-laptop:~$ cat/etc/network/interfaces
bash: cat/etc/network/interfaces: No such file or directory
woopud@woopud-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
woopud@woopud-laptop:~$ dmesg | grep ndis
[17179611.704000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179611.812000] ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) loaded
[17179611.816000] ndiswrapper (NdisWriteErrorLogEntry:241): log: C000138D, count: 1, return_address: e0bafbe3
[17179611.816000] ndiswrapper (NdisWriteErrorLogEntry:244): code: 259
[17179611.816000] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[17179611.816000] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[17179611.816000] ndiswrapper (miniport_halt:327): device da237400 is not initialized - not halting
[17179611.816000] ndiswrapper: device eth%d removed
[17179611.816000] ndiswrapper: probe of 0000:02:02.0 failed with error -22
woopud@woopud-laptop:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
woopud@woopud-laptop:~$ 


```

---

### Post by trubblemaker on 2006-12-06
you might need to re-blacklist the driver.  I'm thinking that yuo are having a driver conflict with the native driver.

---

### Post by woopud on 2006-12-06
Well, I went back to the first post in this thread and checked to see if it was still black listed and it is.  

Bert

```
woopud@woopud-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
woopud@woopud-laptop:~$ 

```

---

### Post by trubblemaker on 2006-12-06
gotta love google:

quick search on "ndiswrapper error 22" turns [sourceforge ndiswrapper page ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ") with this:
> If you get "probe of XXXX:YY.ZZ.A failed with error -22", you may have IRQ problems or it might be a USB driver problem. If you have problems with IRQ assignment the kernel couldn't assign IRQ for the wireless card, you can find out which IRQ ndiswrapper is trying to use and release that IRQ find out which other device is using it with cat /proc/interrupts. You may want touse ACPI and configure BIOS to assign IRQs using ACPI. If it's a USB driver problem there are known issues with high speed USB and ndiswrapper, module under 2.6 is called ehci_hcd, try modprobe --remove ehci_hcd and then reload the ndiswrapper module, that's worked for some people.

hope it helps

---

### Post by styven on 2006-12-07
Hi there,

I can't seem to get any further than this......

styven@styvens:~$ sudo ndiswrapper -i/styven/80211g/bcmwl5.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
styven@styvens:~$ 

As I understand i have ndis wrapper installed as per this how-to, I have blacklisted the bcm43xx driver, it looks to me that i cannot get the bcmwlf5.inf to install.

Steve

---

### Post by styven on 2006-12-07
Hang on there.......needed a space somewhere in the command.

Still got problems though....

styven@styvens:~$ sudo ndiswrapper -i /styven/80211g/bcmwl5.inf
Installing bcmwl5
couldn't copy /styven/80211g/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
styven@styvens:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!
styven@styvens:~$ 

steve

---

### Post by styven on 2006-12-07
Sorry, me again.............

the previous wireless connection in network settings has dissapeared!

The hardware is as detailed.....

Installed drivers:
bcmwl5  invalid driver!
styven@styvens:~$ lspci | grep Broadcom\ Corporation
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
styven@styvens:~$ 

As I understand, this is the right driver for my card, any ideas.

Steve.

---

### Post by trubblemaker on 2006-12-07
yeah it would with the blacklisting, 

you haven't installed the correct driver or,more likely you didn't point to the correct path of the driver. you need to 
```

ndiswrapper -e bcmwl5
[code]
then I"m going on a limb that you forgot your home directory in the path so :
[code]
sudo ndiswrapper -i [COLOR="Red"]/home[/COLOR]/styven/80211g/bcmwl5.inf

```
then to check it's installed use:
```
ndiswrapper -l
```
it should reply:
```
Installed drivers:
bcmwl5          driver installed, hardware present 
```

post if you have more questions

---

### Post by styven on 2006-12-07
thanks for your feedback......here how it went....

styven@styvens:~$ ndiswrapper -e bcmwl5
styven@styvens:~$ sudo ndiswrapper -i /home/styven/80211g/bcmwl5.inf
Password:
bcmwl5 is already installed. Use -e to remove it
styven@styvens:~$ ndiswrapper -e bcmwl5
styven@styvens:~$ ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

Steve

---

### Post by trubblemaker on 2006-12-07
you can manually remove the driver:
```
sudo rm -r /etc/ndiswrapper/bcmwl5
```
consider that replacement for the "ndiswrapper -e " instruction and repeat the above steps

---

### Post by TheGilmanator on 2006-12-07
Here's a fun one.

My laptop requires a keycombo of [FN] + F2 to turn on the wireless adapter.

I've followed all the above instructions and I'm able to see the device, it's got a driver... but it's powered off.

Anyone have any ideas of how to get the darn thing to power on? The FN + F2 keycombo isn't working for me and I don't have any hardware one-touch buttons...

---

### Post by trubblemaker on 2006-12-08
If you have a dual boot, boot into windows and turn it on. Great. 

If you're on a toshiba, there is a package in synaptic that will turn I believe will enable those keys.  

YOu also might have the option to turn it on in you BIOS.

Hope this helps.

---

### Post by xpan on 2006-12-09
no can do!

I did exactly what the howto suggested. I even installed ndisgtk and installed the driver with the help of it. 

I downloaded the driver from acer-support ftp server and it is the same I use for my windows environment. 

although the ndiswrapper -l gives me this:

> bcmwl5          driver installed, hardware present

the radio led does not blink. I can't even connect to the router (192.168.1.1). The radio does not want to start... 

any other work around?

---

### Post by TheGilmanator on 2006-12-11
I gave up and just bought a dlink PCMCIA that has been documented to work.

10 minutes later I had wireless. Installed wifi-radar and my life has been happy since!

---

### Post by mags73 on 2006-12-12
This how-to worked like a charm, after I rebooted with my cabled LAN unplugged.  For what ever reason, when I am cabled up my wifi will not initialize, even if the LAN interface is disabled in the network manager.

Maybe if someone happens to be looking at this and has some time, shed some light on this?  

Thanks for the great post, I am glad this is finally working.


-- Mags73

Dell Latitude D510 (BCM4401-B0 100Base-TX Ethernet Controller, BCM4318 AirForce One 54g)

---

### Post by trubblemaker on 2006-12-12
so with the cable unplugged you get wifi, but when it's plugged in you get nothing?

post these commands please:

```

cat /etc/network/interfaces
iwconfig
ifconfig
dmesg | grep ndis

```
you should also I guess tell me if you are using a network manager. and if you booted with the cable in this time.

---

### Post by warkro on 2006-12-29
> **TheGilmanator said:**
> Here's a fun one.

My laptop requires a keycombo of [FN] + F2 to turn on the wireless adapter.

I've followed all the above instructions and I'm able to see the device, it's got a driver... but it's powered off.

Anyone have any ideas of how to get the darn thing to power on? The FN + F2 keycombo isn't working for me and I don't have any hardware one-touch buttons...

I have the same problem.  I have the Fn + F2 key combo to turn on/off the wirless light.  I followed the howto but I still can't get wireless light to work hence no wireless.  It turns on when booting windows but it doesn't turn on with Ubuntu.  Anyone get this to work?

---

### Post by trubblemaker on 2006-12-29
so as you may have read, you might be able to turn this on in your bios, if your on a toshiba I've heard their is a package that will enable the function buttons so it works again.

The most common reason it doesn't work however is having the incorrect driver installed, to check this use the following command to make sure that ndiswrapper is loading correctly.
```

dmesg | grep ndis

```

---

### Post by warkro on 2007-01-04
> **trubblemaker said:**
> so as you may have read, you might be able to turn this on in your bios, if your on a toshiba I've heard their is a package that will enable the function buttons so it works again.

The most common reason it doesn't work however is having the incorrect driver installed, to check this use the following command to make sure that ndiswrapper is loading correctly.
```

dmesg | grep ndis

```

I finally got it working....thanks.

---

### Post by trubblemaker on 2007-01-04
what was the fix?

---

### Post by davy-mobil on 2007-01-09
hi 
I am an absolute newbie to linux, and I am having trouble getting my wireless to work,
So I did everything that you said to do I think, and what it says is,

davy@dav-mobil:~$ sudo ndiswrapper -l
Installing bcmwl5
couldn't copy /home/davy/Desktop/wireless_card/80211g/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.

then when I check it like you said to it says

davy@dav-mobil:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5  invalid driver!

does anybody know what the next step is?

---

### Post by trubblemaker on 2007-01-09
the incorrect driver got installed you need to 
```

sudo ndiswrapper -e bcmwl5

```
if that doesn't remove the driver (you can check by using "ndiswrapper -l") then do
```

sudo rm -r /etc/ndiswrapper/bcmwl5

```
then you need to install the correct driver
```

sudo ndiswrapper -i /path/to/the/bcmwl5.inf

```
I should say that you also need the bcmwl5.sys file in the same directory as bcmwl5.inf, their kinda married and need to go everywhere together,
then test again with 
```

ndiswrapper -l

```
**if **it says that the driver is installed and hardware present run
```
 ndiswrapper -m 
```
if will make ndiswrapper start on boot.

---

### Post by davy-mobil on 2007-01-11
Hi
Thank you very much for your help,
It says the drivers are installed.  This also made the wireless appear in my networking window, but I cannot connect yet.  So I rebooted thinking maybe that would make ndiswrapper start or something, But it still does not show any networks on the wireless assistant,  I know that there is a wireless connection as I was just using Windows XP and that works with the wireless,  

Thanks again for your help I am sure I must be doing something obvious wrong...

---

### Post by warkro on 2007-01-11
> **trubblemaker said:**
> what was the fix?

sorry for replying too late...

I had the right driver but my light doesn't turn on unless it actually connects. the wireless indicator light only lights up when I have activity but when it's idle it doesn't work. 
 Doesn't really bother me that much.

How I got my wireless to work:
Followed the Howto
then I played around with wpa_supplicant like only having this 
```

auto lo
iface lo inet loopback

pre-up wpa_supplicant -B -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
in my /etc/network/interfaces

and adding 

```

sudo ifdown eth1
sudo ifup eth0
sudo dhclient
``` to my /etc/rc.local

and adding this to /etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="myessid"
        psk=whateverigot

}
network={
ssid="other"
key_mgmt=None
}
```

that would let me connect my wireless instantly everytime I bootup. however, I found that that to choose between networks I would have to add it to the wpa_supplicant.conf.  so with the connection that I had...i installed network manager and I undid all the things that I changed in /etc/network/interfaces and /etc/rc.local.

thanks again.

Note:  I never touched my System > Admin > networking configuration.  I have my connections not configured but I still get wireless anyone know why?

---

### Post by maxamillion on 2007-01-11
I recently was issued a Dell Latitude 110L from work and I decided it was destined to run Xubuntu like the rest of my computer fleet. I have followed many tutorials, including this one and even one that gets the bcm43xx drivers functioning, but no matter what tutorial I follow I always get the same result.

```
max@xDell:/etc/X11$ lspci | grep Broadcom
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
max@xDell:/etc/X11$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 
max@xDell:/etc/X11$ 

```

This appears that everything is set where it should be but then we attempt to configure a few things....

```
max@xDell:/etc/X11$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

max@xDell:/etc/X11$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:EE:1C:EB  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:feee:1ceb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:539435 (526.7 KiB)  TX bytes:104708 (102.2 KiB)

eth1      Link encap:Ethernet  HWaddr 00:14:A5:0E:51:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Memory:dfdfe000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84 (84.0 b)  TX bytes:84 (84.0 b)

max@xDell:/etc/X11$ iwlist eth1 scan
eth1      No scan results
max@xDell:/etc/X11$ 

```

The scan results should pick up 4 access points including the one I am sitting next to (my iBookG4 running Xubuntu Edgy with bcm43xx for the AirportExtreme does, so I know this one should as well).

Any thoughts?

---

### Post by trubblemaker on 2007-01-11
> **warkro said:**
> s
Note:  I never touched my System > Admin > networking configuration.  I have my connections not configured but I still get wireless anyone know why?

GUI isn't all that.  it's pretty lame, mine says the same thing.  Be aware that the gui will add entries into /etc/network/interfaces if you play with it.  So i suggest not using it.

---

### Post by trubblemaker on 2007-01-11
maxamillion  got a couple things for you to check out.

```

sudo iwlist scan eth1
dmesg | grep ndis
dmesg | tail
cat /etc/modprobe.d/blacklist

```
I'm thinking off the bat that it's the incorrect driver but can't say for sure, if your on dual boot  still you can make windows tell you the files, needed or you can grab them from the nic install disc.

I have to say that "iwlist scan" really is the test if your wireless card is working or not.

Thanks for all the output in you post that really helped to narrow down the issue.

---

### Post by maxamillion on 2007-01-11
Thanks for the reply. I'm at work now and will post the output of those commands when I get home.

I don't dual boot and I think I will put Feisty Heard 2 on there and see if I can get it working. I have to test Feisty anyways, might as well test it with this :)

---

### Post by trubblemaker on 2007-01-11
no worries that was another suggestion I was going to make (re-install) but I figured that the ndiswrapper from source would be quicker

---

### Post by mudflapz on 2007-01-24
(edit) OH never mind, Problem solved.  Thnx

---

### Post by frreje on 2007-01-27
Hi,
I just installed ubuntu and don't understand something.
The command:
```
sudo rmmod bcm43xx
```
Returns:
> Module bcm43xx does not exist in /proc/modules

---

### Post by kosson on 2007-02-03
I drive a beautifull Aspire 5101 ANWLMi which responds to the  lspci with:

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I had a succesfull installation using ndiswrapper 1.8 in combination with bcm4318.all.tar.gz

The only problem is that every time I reboot I have to disable the lan connection, disable wireless connection and enable wireless again. Only after these operations my system is up 'n ready for wifi.
How may I solve this cumbersome situation ?

Thank you guys for your time and patience

---

### Post by tekron on 2007-02-03
I just installed the wireless drivers correctly for my HP Dv5000z, bcm4318, and upon reboot I went to networking and there is no option for a wireless network, just wired. In terminal, it says hardware present for the driver and my wireless light is on, what happened?

---

### Post by kosson on 2007-02-03
Blacklist it !
See how in upper threads

---

### Post by kosson on 2007-02-03
It happend to me to, this situation but before getting ndiswrapper 1.8 which works like a miracle with bcm4318xx.all.tar.gz.

Update ndiswrapper, uninstall the older bcm4318xx and try again but with that special tar.gz...

The only problem is that I have to turn it on manually which could become a pester soon

---

### Post by valke on 2007-02-10
ok my wireless card is not showing up, i did blacklist, and i checked it with

```
dmesg
```

and then this is what i got, scrolling down a bit...

```
[17179588.172000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:14:22:93:ef:0a
[17179588.364000] lp: driver loaded but no devices found
[17179588.408000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179588.472000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17179588.472000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed

```

please do help me! i don't know what i did wrong. followed the directions to the letter. have been logging what i do as well. i'm available for chat in gmail, [email]stormy.valke@gmail.com[/email]

:evil:

---

### Post by kosson on 2007-02-10
update ndiswrapper to 1.8 :KS

---

### Post by valke on 2007-02-10
ummm, i thought i did, how do i update? sorry, under a lot of stress, brain not working...:confused:

---

### Post by kosson on 2007-02-10
sudo apt-get update ndiswrapper

or

update with Adept Manager (System)

---

### Post by valke on 2007-02-10
this is what i get

```
E: The update command takes no arguments
```

what does this mean?

---

### Post by kosson on 2007-02-10
I'm sorry it is my mistake. It's upgrade, not update..
Sorry !
try again ! should be fine now

---

### Post by valke on 2007-02-10
i did something stupid and need some help.

```
valke@millimeter-laptop:~$ Sudo gedit /etc/modprobe.d/blacklist
bash: Sudo: command not found
valke@millimeter-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
Password:
valke@millimeter-laptop:~$ sudo rmmod bcm43xx
valke@millimeter-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
valke@millimeter-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf
Installing bcmwl5
couldn't copy /location_of_your_wireless_driver/bcmwl5.inf at /usr/sbin/ndiswrapper-1.8 line 144.
valke@millimeter-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.infbcmwl5 is already installed. Use -e to remove it
valke@millimeter-laptop:~$ sudo ndiswrapper -i /home/valke/wireless/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
valke@millimeter-laptop:~$ -e
bash: -e: command not found
valke@millimeter-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf -e
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
valke@millimeter-laptop:~$ -e
bash: -e: command not found
valke@millimeter-laptop:~$ sudo ndiswrapper -i /home/valke/wireless/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
valke@millimeter-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf -e
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
valke@millimeter-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf -e
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
valke@millimeter-laptop:~$ -e driver
bash: -e: command not found
valke@millimeter-laptop:~$ sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf -e driver
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
valke@millimeter-laptop:~$ 


```

---

### Post by valke on 2007-02-11
thanks, i figured it out! works great!

---

### Post by EverySam on 2007-02-11
I don't understand, why haven't they fixed this by default yet? It's been broken forever. This is way too annoying to do every time I install a new distro.

---

### Post by valke on 2007-02-13
i concur, they should add this to the live cd and detect automatically, because if and when i upgrade to fiesty, i do not want to do this again. although i just may become an expert on this and adjusting my resolution from now on.

---

### Post by tpb on 2007-02-23
Hi Nick !
I have the same problem - and still no solution. 
When i type sudo [COLOR="Red"]ndiswrapper -l[/COLOR] i get a repply, that the driver is loaded. 
But if I type [COLOR="Red"]sudo ifup eth1[/COLOR], I get an error message (No such device).

Thorkild

---

### Post by kosson on 2007-02-23
1. Make sure is hardware is ON ! (no disrespect... happens)
2. Make sure is blacklisted
3. Aaa... hmmm... try it now...

---

### Post by kosson on 2007-02-24
I'm the happiest man ever !
WiFi works like a charm on my new installed Feisty Fawn Hurd 4

---

### Post by nickj6282 on 2007-02-24
Fantastic! So when is Feisty scheduled to be released? I never got around to upgrading to 6.10 when I heard about so many others having problems with it.

-Nick

---

### Post by kosson on 2007-02-24
Is due to 1 of April !
I'm so happy to see my Acer 5100 buzzin' n hummin'... I tell you my friends is quite a show amd64 power plant fitted with Feisty Fawn Hurd 4.

The new realease of KDE implemented is verry fast and slick.

---

### Post by nbound on 2007-02-27
My first time back on here in a few months, its great to hear so many of you got it working using my HOWTO:-D .... It caused me no end of headaches when i first tried setting up my wireless again ](*,)

---

### Post by lolcese on 2007-03-22
Thanks for the guide. The updated link for the driver is [URL="ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip"]ftp://ftp.support.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip
[/URL]

---

### Post by nbound on 2007-04-11
Updated for Feisty, cheers for new link lolcese :)

---

### Post by chipyoung on 2007-04-11
Thank you nbound.  Your "Feisty" Broadcom bcm4318 HOWTO worked great on my Dell Inspiron 8100 laptop with a Linksys card.  I tried the fwcutter routine and became very frustrated.

Thanks again.
Chip

---

### Post by wipeout140 on 2007-04-13
Will this give me 54mb wireless instead off 11mb i mostly get on the .deb from here - featured in HOW TO:
[http://ubuntu.cafuego.net/dists/edgy-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/edgy-cafuego/bcm43xx/)

---

### Post by nbound on 2007-04-14
Yes this will give you 54mb, as long as you have a BCM4318 (aka airforce one)

---

### Post by wipeout140 on 2007-04-14
> **nbound said:**
> Yes this will give you 54mb, as long as you have a BCM4318 (aka airforce one)

Yes i do, One more question will need to delete/un-install them drivers first

---

### Post by nbound on 2007-04-14
> **wipeout140 said:**
> Yes i do, One more question will need to delete/un-install them drivers first

yes, but that is included in the howto :)

---

### Post by wipeout140 on 2007-04-15
> **nbound said:**
> yes, but that is included in the howto :)

Thanks i try it out when 7.04 comes out as final

---

### Post by darkhacker902 on 2007-04-15
Ok So I followed this tutorial when i installed ubuntu Dapper Drake from my CD.

Finally it worked. Awesome.

I thought, well i'm a little outdated, I think I will go and update to Edgy.

Crap.

Because Now my wireless connection is not working again.

Everything in this tutorial is correct, i re-followed it And Ndiswrapper -l tells me that the device, and hardware is present. iwconfig tells me there are no wireless extensions though, and in the networking gui, there is no Wlan0 Just eth1 which is my wired extension, which I disabled.

What do I do now?


Ryan

---

### Post by nbound on 2007-04-15
double check that youve disabled bcm43xx and that youve set ndiswrapper to load in the modules file, they are the two most likely problems

---

### Post by M4v3r1ck on 2007-04-18
Ok, performing "sudo rmmod bcmxx" gets me-
ERROR: Module bcm43xx does not exist in /proc/modules
I'm using Edgy and a total Linux newb. And I doin' something wrong there or is that important?
~M4v

---

### Post by pauldude000 on 2007-04-18
What can I say?.......THANK YOU THANK YOU THANK->Y O U!

After following a different post elsewhere, which also caused a re-installation of Kubuntu Edgy...... I found this thread through Yahoo. I am writing this post without the blue cord, using my otherwise paperweight broadcom 4318 airforce1 wifi card, on my Acer Aspire 5050 notebook! :guitar: YES


Now all I need for a completely functioning unit is to get the sound working right... 

For any Acer users with the bcm4318 broadcom airforce card... USE THIS ADVICE ... 

I have just recently switched to Linux (1 week linux user), and if I can follow this advice, you can. I am using 32bit Kubuntu Edgy.(64 bit dapper wont even load).

Good Luck!

Paul

---

### Post by Tha-Fox on 2007-04-18
I have blacklisted the native driver and ndiswrapper starts automatically. Still my Acer 5024 won't connect via Broadcom. As I followed this guide, it gave me error that said something like "permission denied". I know it doesnät tell too much but I give more information as soon as I get back to my computer. But what kind of information should I give to you for getiing some help? And yes, I am a total newbie when it comes t Linux :D

---

### Post by pauldude000 on 2007-04-18
Which step did you get the error from?

---

### Post by M4v3r1ck on 2007-04-19
Ok, performing "sudo rmmod bcmxx" gets me-
ERROR: Module bcm43xx does not exist in /proc/modules
I'm a total Linux newbie here and any help would be appreciated. This is prolly one of the best communities I have ever seen online anywhere.
~M4v

---

### Post by pauldude000 on 2007-04-19
"Ok, performing "sudo rmmod bcmxx" gets me-
ERROR: Module bcm43xx does not exist in /proc/modules
I'm a total Linux newbie here and any help would be appreciated. This is prolly one of the best communities I have ever seen online anywhere.
~M4v"

I am a newbie here too, but I agree. However, I have been a programmer for a long, long, time. 

The next question is did you complete the process? 

(downloading and installing the windows drivers - check ndiswrapper to see if hardware found - etc.?) 

If not, then do so, as the drivers are necessary for ndiswrapper to run. 

I have managed to kill Kubuntu three times in a row, messing around with my user account settings, and have done this procedure three times in a row successfully. :) (experimentation can be fun, especially when you cannot log in)

I did notice that one of the three, the card was found by ndiswrapper, and the light was on, but  no internet. In the system manager I noticed that the card was enabled, but no tcp address was assigned. I manually assigned my wired tcp to the wifi, and presto, everything was working again. (I am using a belkin wireless router for internet sharing) 

Check your settings, and let us know what you come up with.

Paul

---

### Post by M4v3r1ck on 2007-04-19
Firstly, thanx for the help.
When I go to finish the install, this is what I get in terminal-

```

m4v3r1ck@M4vt0p:~$ sudo ndiswrapper -i bcmwl5.inf
Password:
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
m4v3r1ck@M4vt0p:~$ sudo ndiswrapper -l
Installed drivers:
bcmwl5   invalid driver!
m4v3r1ck@M4vt0p:~$

```

I did manage to blacklist the original fine, and I added ndiswrapper to the /etc/modules ok as well.
~M4v

---

### Post by Tha-Fox on 2007-04-19
I've tried to install the drivers this way:

First I've removed all former installations like it's told in here: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683) (that HOWTO gave me the same "permission denied" as all the other HOWTOs I've tried)

Then I start to follow this HOWTO. I search Synaptic for "ndiswrapper" and it finds ndisgtk, ndiswrapper-source and ndiswrapper-utils 1.8. I install only ndiswrapper-utils. Should I find also that "ndiswrapper-common"? 

Next I blacklist the native drivers and put the 


```
sudo rmmod bcm43xx
```

and it gives me: ERROR: Module bcm43xx does not exist in /proc/modules

I downloaded the latest drivers for my card in Windows and put them on the Ubuntu's desktop. Then I install them with
```

sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

```
and the response is: Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2

Next step:
```

sudo ndiswrapper -l
```

Installed ndis drivers:
bcmwl5          driver present, hardware present

Next:

```
sudo gedit /etc/modules 
```

and I add the row "ndiswrapper"

Then the restart and nothing happens. I have A-Link Roadrunner 44C as a router and Buffalo Airstation is attached to it? I have only one network cabel so when I restart, should I attach Airstation to A-link or laptop directly to A-link?

Edit: Now I tried to restart so that I removed the cable from laptop and attached it to Airstation. Lamp stayed off. I pressed it and nothing changed. I'm not even sure whether my connection settings are right or not. I copied the settings from Windows as well as I could. Is ESSID the same as SSID in the Windows? Something like 1452423AE5? In networks settings there are devices called wlan0 and eth0 which are both active. I changed eth0 to idle and no change. WEP-key is there and DHCP is on.

I put the eth0 as idle in the network settings. Then command "dmesg" gave me this kind of information:

[17179590.136000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179590.136000] eth0: RTL8169 at 0xf89a0400, 00:0a:e4:e4:79:98, IRQ 66

[17179591.788000] r8169: eth0: link down
[17179592.808000] lp: driver loaded but no devices found

[17179592.936000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179593.000000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded

[17179593.008000] ndiswrapper: using irq 177
[17179594.012000] wlan0: vendor: ''
[17179594.012000] wlan0: ndiswrapper ethernet device 00:14:a4:28:44:65 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
[17179594.012000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

[17179670.432000] IPv6 over IPv4 tunneling driver
[17179680.928000] wlan0: no IPv6 routers present

[17179726.688000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179743.172000] eth0: no IPv6 routers present


[17182012.348000] ndiswrapper (add_wep_key:848): adding encryption key 1 failed(C0010015)
[17182394.860000] r8169: eth0: link down

```
ifconfig
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:A4:28:44:65
          inet6 addr: fe80::214:a4ff:fe28:4465/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:c0204000-c0206000

```
iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```
iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
sit0      Interface doesn't support scanning.

```
dmesg | grep ndis
```

[17179592.936000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179593.000000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179593.008000] ndiswrapper: using irq 177
[17179594.012000] wlan0: ndiswrapper ethernet device 00:14:a4:28:44:65 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
[17182012.348000] ndiswrapper (add_wep_key:848): adding encryption key 1 failed (C0010015)

```
ndiswrapper -l
```

Installed ndis drivers:
bcmwl5          driver present, hardware present

Summa summarum: This time I didn't get the "permission denied" but it still won't work.

---

### Post by pauldude000 on 2007-04-20
"[B]Installed ndis drivers:
bcmwl5 driver present, hardware present[/B]"

This is good, since it demonstrates that ndiswrapper has the drivers, is detecting the hardware, and is stating that you have the right driver for the hardware.
---------------------------

"**Then the restart and nothing happens.**"

Does the light come on during boot, then shut off again? If so, then ndiswrapper is working, but there is a software settings error somewhere.
-----------------------------

"**I have A-Link Roadrunner 44C as a router and Buffalo Airstation is attached to it?**" 

I am not sure, as I am not a home networking guru on all device interaction, but I looked up the products, abd you are linking a secure router (buffalo airstation" to a router (A-Link). The Airstation supports Wep, WPA, and DHCP, while the A-Link supports DCHP (no mention of wep or wpa support) this might well be a problem. 
----------------------------

"**I have only one network cabel so when I restart, should I attach Airstation to A-link or laptop directly to A-link?**"

Try attaching that Airstation directly to your DSL/ADSL connection from your ISP, leaving the A-Link out of the picture. (You only need one router). If hooking up multiple computers, then you can buy wireless cards for them to connect to the Airstation as well. If the Airstation version you have has multiple RJ45 ports (DSL cable type connector), then your other pc's can hook through a wired connection, while your laptop(s) uses the wireless connection.

Your Airstation, like the A-link, is a router, able to connect multiple computers to a single ISP, except it is a better router from what I found researching the two.
---------------------------

"**Now I tried to restart so that I removed the cable from laptop and attached it to Airstation. Lamp stayed off. I pressed it and nothing changed. I'm not even sure whether my connection settings are right or not.**"

I have my doubts because of this:

"[B][17179591.788000] r8169: eth0: link down
[17179592.808000] lp: driver loaded but no devices found[/B]" 

As it should be, your wired ethernet device is disabled.

"[B][17179593.008000] ndiswrapper: using irq 177
[17179594.012000] wlan0: vendor: ''
[17179594.012000] wlan0: ndiswrapper ethernet device 00:14:a4:28:44:65 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
[17179594.012000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179670.432000] IPv6 over IPv4 tunneling driver[/B]"  

As it should be. It is saying that the drivers are functioning, and that the card has sent back supported mode info.

"[B]17179680.928000] wlan0: no IPv6 routers present
[17179726.688000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17179743.172000] eth0: no IPv6 routers present[/B]"

Bingo! Here is the problem! The card is not detecting your router. This is either due to:

1. Incorrect router connection to ISP cable (such as I mentioned earlier with router going through another mismatched router)
2. Incorrect ethernet software settings (Incorrect protocol , IP Address, Mask, etc..)

The failure of the connection key is due to the fact that no IPv6 routers were found.

In systems settings, check your ISP address, gateway, protocall, and domain name servers. DO NOT POST THE INFO HERE!!!!!! (information hackers could use, and I don't need to know.)

The Router should assign you an IP address, which should be something like 192.168.x.x. (pretty standard format) This is your routers gateway address for your machine. This number should be both your IP Address, and your route/gateway. 

Try this:

1. Connect just the Airstation router (no cables to your notebook, just wifi, leaving the A-link disconnected and out of the picture.)
2. In your network settings, set the TCP/IP to Automatic and DHCP, leaving the ESSID and Wep empty.
3. Apply the settings.

If you still show no IP address, copy your eth0 gateway settings, and paste them into your Wlan0 gateway editbox, and apply the settings. (Cheaters trick I use if my wired computer steals my wireless gateway, as I automatically get a new reassignment of a new gateway this way.)

Let me know if this works.

Paul

---

### Post by M4v3r1ck on 2007-04-20
Ok, I got my wireless going.

What I did is I followed the uninstall [http://ubuntuforums.org/showthread.php?t=25683]("http://ubuntuforums.org/showthread.php?t=25683") as Tha-Fox did, then, I followed the instructions @ [http://fedoranews.org/mediawiki/index.php/How_To_Install_Your_Broadcom_BCM4318_Using_Ndiswrapper]("http://fedoranews.org/mediawiki/index.php/How_To_Install_Your_Broadcom_BCM4318_Using_Ndiswrapper").

I ran a ```
sudo apt-get install ndiswrapper-utils-1.8
```

Then I switched to the folder where all my extracted driver files were-
I made sure I left the original driver blacklisted.

Then I ran-
```
sudo ndiswrapper -i bcmwl5.inf
```
Which brought up-
```
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
m4v3r1ck@M4vt0p:~$
```

When I display the installed ndiswrapper driver it shows-
```
Installed ndis drivers:
bcmwl5                driver present,  hardware present
```

Then I followed up with
```
sudo apt-get ndiswrapper -m
```

And as the guide stated it went into-
```
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.conf
```

The only thing the guide didn't cover was the fact that it was turned off, which I was able to turn on using-
```
sudo ifup wlan0
```

After that everything appeared, I just turned on the wireless switch and took me awhile to figure out how to use the interface effectively, but I'm connected right now.

My wireless light blinks as it's turned on but not connected and solid blue when it's connected.
I'm sure this is noob stuff to everyone else here but my post was more for other stray noob for something else to try.

Thank you for all your help and suggestions.
~M4v

---

### Post by reeth on 2007-04-21
Thanks very much, it works perfectly on my Acer Aspire 5000. This howto is great (i've searched about 5 hours till find it and make my wireless card works)! Still thank you for your great job!

---

### Post by Chuklz on 2007-04-21
thanks man :)
i am a total noobie who switched back and forth between ubuntu and windows for about a year now but I'd test ubuntu for a weekend or so but could never get wireless to work---
   now i can finally use my laptop with ubuntu and linux is finally my only OS!

one thing i noticed though during ndiswrapper:
   when i did the sudo ndiswrapper -i /location_of_your_wireless_driver/bcmwl5.inf step,  i could never get it to           work for some reason because the folder name was really long when I did the extract here thing.
  then i changed the folder name to one word, "wireless", and it worked.
  just a suggestion if someone has the same problem :)

---

### Post by Splendor78 on 2007-04-23
I just got done installing Ubuntu Feisty Fawn for the first time.  I've installed it on a Compaq Presario v2575US notebook with the BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.  I found this thread and was unable to get the steps listed to work.  The bcmwl5.inf driver would never take (even though it would tell me occasionally that it was already installed).

But I found this site

[http://designedfor.wordpress.com/2007/03/20/finally-wireless-broadcom-43xx-solution/#comment-380](http://designedfor.wordpress.com/2007/03/20/finally-wireless-broadcom-43xx-solution/#comment-380)

And the four easy steps worked on the first try and now I'm up and running.  The only things I had to do other than what's listed on that site were to run the updates before I started and disable my wired connection after the 4 steps (the wireless won't work with the ethernet enabled I guess).

Just thought I'd add my experience to the list here.

---

### Post by nbound on 2007-04-25
Strange, fwcutter isnt meant to work on 4318s properly

---

### Post by pauldude000 on 2007-04-26
I haven't posted any replies since my last advice as I have upgraded to from Kubuntu Edgy to Kubuntu Feisty myself.  I have noticed some problems (bugs?) in Feisty not present in Edgy.

Let me explain.

**_Edgy:_**

Advice provided at the start of this post thread worked perfectly. My laptops wired lan worked perfectly with my broadcom wifi.  Consistency was good, as my Lan only rarely tried to "steal" the wifi's TCP address. (Both being enabled at the same time.)

------------------------------

**_Feisty:_**

As soon as I upgraded to Feisty, I started encountering problems with the technique. at the console prompt, using ndiswrapper -l, I found both driver and hardware present, with additions.

**Previously I was given the message:**

bcmwl5:
Hardware present, driver installed.

**Now I get:**

bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

I didn't think )much of it, until I re-booted, and my wifi didn't work. The light was on, and ndiswrapper was still properly finding the device, but I had no internet. I suspected the Network Settings, and was **partially** right. If the light is on (hardware sending the ready status) and ndiswrapper is detecting the hardware and loading the proper driver (detected and bcmwl5) then everything is ready to go hardware and driver wise, the problem is elsewhere.

I stated "partially" right, as the problem was two part.

1. Problem in Network Settings (no TCP assigned to EITHER wired LAN or wifi with wifi enabled)
2. Wifi absolutely refused to work with network manager installed.

--------------------------------------------------------------


**_Solution: (a royal pain)_**

1. in package manager, uninstall package **networkmanager**

Now, modifications to your Network Settings will actually DO something!

2. In your Network Settings, disable ***_BOTH_*** your wired LAN and wifi. 
3. Now, enable ***_ONLY_*** your wifi.

You should now (if using DHCP connection protocall) see an assigned TCP on your wifi, and if so, then you have internet.

***_MAJOR PAIN IN KEASTER:_***

Get used to steps 2 & 3. Every time you re-boot, you may have the same problem I have in Feisty, in that you will loose your network settings, and have to re-disable LAN and re-setup wifi. Didn't happen in Edgy, but does in Feisty. I think it is a major bug.

If anyone knows a cure for this prob, let ME know!

---

### Post by JC Denton on 2007-04-26
Followed all the steps in the first post and still having problems. This is after making this post: [http://ubuntuforums.org/showthread.php?p=2526311#post2526311](http://ubuntuforums.org/showthread.php?p=2526311#post2526311)

when trying to use wpa_supplicant the following errors appear:

ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Segmentation fault (core dumped)

 lspci | grep Broadcom\ Corporation returns:

00:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

this is after installing the drivers from the link. Btw this is an Asus Z92 laptop but I figured the wifi cards would be the same..

iwconfig:
eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Managemer nt:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks... desperate by now after trying all the inf files on my cd /cab/exe files

---

### Post by pauldude000 on 2007-04-26
"this is after installing the drivers from the link. Btw this is an Asus Z92 laptop but I figured the wifi cards would be the same.."

I read your other post. You now have alot of drivers loaded, and they need to be unloaded. The easiest way I know is to remove and then  re-install ndiswrapper using a package manager such as synaptic or adept manager. 

After re-installing ndiswrapper, follow the information in the first post again. 

Lastly, at the console type ndiswrapper -l and reply with a cut/paste of the results.

Pauldude000

---

### Post by JC Denton on 2007-04-26
I did this before installing the drivers from the link.

results:

bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)

---

### Post by seismicmike on 2007-04-27
Here's some fun! I have a Gateway M320 Notebook (PLEASE NOBODY MOCK ME FOR MY NON COMPATIBLE HARDWARE) that had a built in wireless card that was working fine until I lost the drivers in an OS reinstall (the gateway support website no longer has the right version of the driver) so I bought a card... Belkin Wireless G+, part number F5D7011 in case anyone is interested... I downloaded the correct driver from Belkin's website (b/c I don't know where the CD is right now)....

it's not bcmwl5.inf... it's bcmwl6.inf... don't know if that makes any difference, but....

I follow every single step in this how to and even some other hints from [http://ubuntuforums.org/showthread.php?t=422596&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=422596&highlight=ndiswrapper)

and get absolutely NOTHING from my card.  ndiswrapper -l tells me that the driver is installed and the hardware is present, but the networking gui, ifup and ifdown and iwconfig tell me it isn't there... there are no lights on the card... but the driver is installed and is present...

YES I have done modprobe ndiswrapper. Any suggestions?

In a perfect world I would have a Mac with OSX Tiger and Ubuntu on a dual boot, but I don't have the kind of money necessary to make this happen.

---

### Post by pauldude000 on 2007-04-27
"I did this before installing the drivers from the link.

results:

bcmwl5 : driver installed
device (14E4:431 present (alternate driver: bcm43xx)
Reply With Quote"

Then your hardware and driver are loaded and running. Good. (you are also running feisty, due to the system response.)

Your problem is then with the ubuntu network system, and not with ndis or driver.

Let me guess, in the network settings, it shows both enabled and possibly the wired lan eth0 with a tcp address, but not the eth1 or wlan1 (wifi)? :) 
[B]
If so, then disable both, and re-enable ONLY the wifi.[/B] 

Check for TCP assignment. 

**Yes?** Without re-booting, try firefox, you should be online.

**Still no assignment?** the problem is elsewhere.

In the Network Settings, highlight wifi then click configure.

Is your ISP autoconfiguring? (assigns you TCP address such as dsl, wifi broadband, a router installed, etc.)

**Yes** Set your protocall to dhcp, then click apply. Re-disable wifi and then re-enable and check for TCP again.

**NO** 

1. If secure router or ISP access. Set your (e)ssid name / pass being carefull to make sure you are using the right case (as in upper and lower case. These are case sensitive) Redisable etc..

2. If ISP uses configuration script. Provide location of script. Redisable, etc.

If still no TCP, then you may have an installed program interfering with ndiswrapper. My guess would be the package networkmanager. (will not work with broadcom) Also try getting rid of the ndiswrapper gui interface.

Other than this, I can't say much more than that it is a software -bug/conflict error- you are experiencing, and you may want to do a search in synaptic for "TCP", and examine the packages installed, removing any non-necessary packages to possibly remove the conflict. This can break your system though, if you are not carefull.

Let me know what you come up with.

Pauldude000

---

### Post by MiLoX on 2007-04-27
Hi I think I've read all the post and couldn't found this error I got " [ 1276.350364] ADDRCONF(NETDEV_UP): wlan0: link is not ready  " everything seems to be working but when I try to connect to essid it stops at 28% and nothing happens 

Any ideas please??

---

### Post by piggy_knowles on 2007-05-03
Finally, something that worked for me. The only thing keeping me from putting ubuntu on my Acer Travelmate 2480 was the issue with the Broadcom wireless card. Even as a newbie I got this working. Thanks!

---

### Post by JC Denton on 2007-05-07
> **pauldude000 said:**
> "I did this before installing the drivers from the link.

results:

bcmwl5 : driver installed
device (14E4:431 present (alternate driver: bcm43xx)
Reply With Quote"

Then your hardware and driver are loaded and running. Good. (you are also running feisty, due to the system response.)

Your problem is then with the ubuntu network system, and not with ndis or driver.

Pauldude000

Thanks for your help Paul. Downing eth0 solved my problems.

---

### Post by turnovg on 2007-05-19
Ubuntu 7.04, fresh install.

I figured out the problem - it was wrong driver I was using. ...Or the driver could not be wrong (bcmwl5, bcmwl5a), but using this driver I always get the kernel bcm43xx driver active (alternate). Cannot remove it, cannot blacklist it. It's always their. So I took the original driver from the CD - NET2G54L.inf. Works like a charm!
(Using this driver the system does not add the kernel bcm43xx driver as alternate.)

Here's the procedure in short:

-----------------------------
0. wireless card not plugged in.
1. bcm43xx-fwcutter.deb - install
2. bcm43xx-fwcutter -w /lib/firmware/2.6.20-15-generic/ wl_apsta.o
3. dpkg -i ndiswrapper-common ndiswrapper-utils
4. ndiswrapper -i NET2G54L.inf
5. plugging wireless card...
8. ndiswrapper -m, ndiswrapper -mi, ndiswrapper -ma

Good luck everyone!


P.S.
Ubuntu 7.04 was fresh installed. (If you do many tries of installing the procedure described above could not work.)
(Or use the liveCD for trying. If successful - install Ubuntu and your wi-fi card :)

P.S.2
No need of any special actions like noapic at boot, blacklisting or rebooting...

---

### Post by MatBeharrell on 2007-05-19
The driver link seems to be down at the moment. An alternative is _**[here]("ftp://ftp.work.acer-euro.com/notebook/aspire_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip")**_

Thanks for the HowTo !

---

### Post by jimbob on 2007-05-22
Many thanks for this post nbound.  At first I got wireless working by using bcm43xx-fwcutter but it absolutely refused to go any higher than 11Mb/s as it did for many others.

I decided to go the ndiswrapper route and followed your post #1 here and now I'm happily chugging along at 54Mb/s as shown by iwconfig.

I borrowed the bcml5.inf and bcml5a.inf from my ex pee installation.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by motin on 2007-05-25
THANK YOU! Worked flawlessly!

I hope this routine is planned for semiautomatic or automatic implementation in Gutsy...

Is this yet on UDSF? It should be...

---

### Post by tahuya_rat on 2007-05-28
Hey, fantastic howto!  Thought I'd report my results / hardware for anyone in a similar situation.

I have had this card working before, using ndiswrapper from Synaptic, and from source, but had no roaming mode, and no ability to see available networks (had to enter the ESSID manually whenever I moved to another network).

I am using a Gateway MX6450.

1) - Fresh install of Feisty
2) - Run all updates right out of the gate.
3) - Install ndiswrapper from Automatix2.
4) - Follow the howto at the beginning of this thread, verbatim.

Restart and voila!  I now see all available networks under wireless networks, and I get the nifty connection meter icon instead of just the same "wired network" icon at the top of the screen.

Thanks again for the great howto, and hope this post helps anyone else with a Gateway MX6450.

-tahuya_rat

---

### Post by Major Pen0r on 2007-05-31
this made my wireless disappear actually....i have an Acer Aspire 3000 with a Acer InviLink 802.11b/g wireless card and i dunno if i used the right version of the walkthrough or not

and my processor is a AMD Mobile Sempron 3000

---

### Post by tahuya_rat on 2007-06-09
> **Major Pen0r said:**
> this made my wireless disappear actually....i have an Acer Aspire 3000 with a Acer InviLink 802.11b/g wireless card and i dunno if i used the right version of the walkthrough or not

and my processor is a AMD Mobile Sempron 3000


Really?  I think I actually used your drivers for my install.  Did you follow the steps I put forward in the last post?

---

### Post by DjDarkman on 2007-06-18
This howto is the best it works on feisty 32 bit edition too!!Many thanks.

---

### Post by frosty865 on 2007-07-10
Thank you! I'm a complete and utter newbie and you saved my bacon!

---

### Post by kennethb on 2007-07-23
These instructions worked for me. I have a Gateway laptop (MX6442) with a AMD 64-bit processor with the BCM4318. I'm using Feisty. Thanks!

---

### Post by JC Denton on 2007-09-07
I used to be able to use my bcm4318 wifi card but after downing both eth0/1 upping eth1 gives scioflags no such device. using ndiswrapper . The driver is installed.

previously I have been able to get it to work by downing eth0 first.

---

### Post by Ikslewap on 2007-10-07
***Sidenote:


For those of you receiving the "invalid driver: bcmwl5.inf" response when asking ndiswrapper to check for the driver, trying running the same procedure on bcmwl5a.inf.  For whatever reason it didn't like my first attempt but after I used the latter, it worked like a charm with a little configuration on the desktop

Hope this helps,

Paws

---

### Post by jnorthr on 2007-10-07
my kit only worked by using NDISWRAPPER testing 1.49-rc3 version NOT the stable version. Dunno why...

---

### Post by alex69 on 2007-12-12
thanks nbound  I've tried to follow your prescriptions but with no success:...

first I've blacklisted bcm43xx, then I made the follow steps
sudo ndiswrapper -i /home/alex/desktop/bcmwl5a.inf
and to be sure also...
sudo ndiswrapper -i /home/alex/desktop/bcmwl5.inf

but each time the sysm replayed:

bcmwl5 driver already installed
and:
bcmwl5a driver already installed

then I've tried to verify my job with:

sudo ndiswrapper -l

and the orrific result was:

bcmwl5: invalid driver!

and, obviously

bcmwl5a: invalid driver!

any suggestion? I'm very disoriented...

---

### Post by Lorac1949 on 2007-12-12
> **alex69 said:**
> thanks nbound  I've tried to follow your prescriptions but with no success:...

then I've tried to verify my job with:

sudo ndiswrapper -l

and the orrific result was:

bcmwl5: invalid driver!

and, obviously

bcmwl5a: invalid driver!

any suggestion? I'm very disoriented...

You may want to uninstall the driver and try this.  Worked for some folks.  It got me a little closer to a connection:

[https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/7.10/internet/C/ndiswrapper.html)

---

### Post by alex69 on 2007-12-12
thank you Lorac1949,

how should I uninstall the drivers?

do you mind both the drivers the bcmwl5 and bcmwl5a?

---

### Post by Lorac1949 on 2007-12-12
> **alex69 said:**
> thank you Lorac1949,

how should I uninstall the drivers?

do you mind both the drivers the bcmwl5 and bcmwl5a?

They can be uninstalled at System > Admininstration > Windows Wireless Drivers.  That is the same location where you'll reinstall them.  Sometimes an uninstall, followed by a reinstall helps.  Good luck.

---

### Post by din on 2007-12-12
Hi
I have problem

 sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

sudo ndiswrapper -i 80211g/bcmwl5.inf
driver bcmwl5 is already installed

sudo ndiswrapper -i 80211g/bcmwl5a.inf
installing bcmwl5a ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

 sudo ndiswrapper -l
bcmwl5 : driver installed
bcmwl5a : driver installed

Whats wrong?

Also,before all this in network settings it was wireless there, but now, after restart, its not listed.
also in restricted drivers manager i have option: Enable the Firmware Broadcom 43xx chipset family. but its not work:
The software source for the package
   bcm43xx-fwcutter
 is not enabled.

---

### Post by nickdbliss on 2008-04-15
You rock dude. :guitar: I just wanted to thank you for this excellent step by step guide. I was having lots of trouble with my wireless on laptop lately.. Now my headache is over lol. Posting this message via wireless on ubuntu. hehe.

---

### Post by Erik. on 2008-04-27
Does it also works for ubuntu 8.04 ?

---

### Post by jimbob on 2008-04-27
Can't really say since I no longer have my laptop with a bcm4318 chip inside, however if I were you I would try 8.04 "out of the box" first.  They may have it working as is by now.

---

### Post by sifon187 on 2008-05-12
> **Erik. said:**
> Does it also works for ubuntu 8.04 ?

Yes it works for 8.04, I just did it....works great.

---

### Post by nickdbliss on 2008-06-08
Leaving the blacklist step and after some tricks i am able to run finally my wireless in ubuntu 8.04

---

