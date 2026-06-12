---
title: "Intel 3945 wireless in edgy"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by sarsparilla on 2006-10-27
I recently installed Ubuntu 6.10 Edgy on my laptop (Dell Inspiron E1750) and really like the os, except that I can not fot the life of me get my wireless internet connection (Intel PRO/Wireless 3945ABG) working. I've tried to follow the various threads that have been made regarding this subject but keep getting lost when it gets to the important stuff. I'm a real nub when it comes to linux so I am hoping that this is able to be a somewhat easy fix. Any help is truly appreciated. 

iwconfig eth1 gives me this:
```

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0

```

Right now I am not worrying about encryption or anything like that, I just want to start small and be able to connect to my home wireless network and my school's as well. Neither have any passwords or anything like that.

in device manager it recognizes my card and is able to give information, and in System->Administration->Networking it shows a wireless connection but says that it is not configured, even after I check the "enable this connection" box.

I hope you guys can help.
If you need more information I will do my best to get it to you.

---

### Post by Roybotnik on 2006-10-27
Bump.. I just installed a I was able to connect to my WEP'd home network once, but after a reboot I can't do anything.  I've got the same card and laptop.

---

### Post by gotgenes on 2006-10-27
I'm having the same issues here. ipw3945 used to work beautifully in Dapper but does not work right out of an Edgy install. Did someone forget to put in the linux-restricted-modules?
```

chris@feathers:~$ dmesg | grep eth1
[17179628.892000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```
Something's not right. I may have to re-install Dapper.

---

### Post by featherking on 2006-10-27
i have the same card and it works fine, if you dont need a static ip i would suggest using Network-Manager for your wireless, it works fine and so does this card in edgy btw. To install network-manager

```
sudo apt-get install network-manager-gnome network-manager
```

This will place an icon by the clock and you can click on it to see available networks. then you can connect with your password

---

### Post by featherking on 2006-10-27
By the way,

If you are having problems with network manager, check your System>Administration>Networking and hit properties for all your network connections listed there and make sure they are NOT enabled. sudo apt-get install network-manager-gnome network-manager.

The reason is, Network-manager likes to take control of setting up the connections for these devices (you can use NM to easily switch between wired/wireless), but this is also the reason you cant use Static IP's, because as of yet NM doesnt allow you to set an ip anywhere and if you do it throught the Networking menu, you break NM.

---

### Post by gotgenes on 2006-10-27
> **featherking said:**
> i have the same card and it works fine, if you dont need a static ip i would suggest using Network-Manager for your wireless, it works fine and so does this card in edgy btw. To install network-manager

```
sudo apt-get install network-manager-gnome network-manager
```

This will place an icon by the clock and you can click on it to see available networks. then you can connect with your password

It's a little hard to get network-manager without access to a network...

The problem appears to be based in Network Settings. I can "sudo iwlist scanning eth1" just fine. Hopefully I can manually connect to a network and get moving.

---

### Post by featherking on 2006-10-27
> **gotgenes said:**
> It's a little hard to get network-manager without access to a network...

How about an install disc? or another computer to download the .deb package from? or a jump drive? or physically plug in to your router and download from your wired connection?

Here are the two packages inside this archive that you need to install network-manager, obviously you both are on the internet viewing these posts somehow. Just d/l this and install on your ubuntu pc

---

### Post by gotgenes on 2006-10-27
> **featherking said:**
> How about an install disc? or another computer to download the .deb package from? or a jump drive? or physically plug in to your router and download from your wired connection?

Here are the two packages inside this archive that you need to install network-manager, obviously you both are on the internet viewing these posts somehow. Just d/l this and install on your ubuntu pc

Thanks for posting those files, however, there are several other dependancies for those packages. I will collect them and post them here. So now we are reduced to Red Hat levels of manually collecting packages and their dependencies if you can kindly tell me where to go to manually download debs. I feel like such a Neanderthal.

In the meantime, I spew filth in direction of Network Settings. I can't even get my wired connection working through it. "sudo ifup eth1" just results in DHCP timeouts. What's going on here? What happened to networking since Dapper? How could it have gotten *worse*?

---

### Post by sarsparilla on 2006-10-27
I'm posting this from my lappy now... without wires!

Thanks a lot featherking, I really appreciate your help.

---

### Post by featherking on 2006-10-27
No problem sarsparilla,

@gotgenes
-What other dependencies could you need? i didnt think much else was required beside standard stuff, like gtk and gnome keyring access. Unfortunately i dont know of a spot to manually download the .deb's i just pulled those two out of my apt cache

On a side note maybe if you start all the way over with your networking. Look at your /etc/network/interfaces file and comment out everything except
```
auto lo
iface lo inet loopback
```

Now go back into your System>Admin>Network and try to just enable your wired connection. *If it doesnt appear in the list, close that window try

```
sudo ifconfig eth0 up
```

If it is in the list already doing the above step wont do anything. Now go try to see if it will accept your DHCP now. The /etc/Network/interfaces file shows all the configuration data you have stored. If you comment out the lines (with #) instead of deleting them, then you can reverse it if something goes wrong (but everything is wrong already..)

---

### Post by notebook_ftw on 2006-10-27
Well, this is pretty annoying.  I am also having the same trouble with my Dell Precision M90.  The Intel 3945 has worked fine with both SUSE 10.1 and Dapper, but for some reason Edgy is just... screwed.  And yes, the package does have dependencies.  So far, the only one I have seen is libnl1-pre6, but that doesn't mean there may not be more once I get into it a little more.

---

### Post by gotgenes on 2006-10-27
I have sent a HOWTO to the How To Forum but it has to be moderator approved. Thus, I'll try and replicate it here:

For those of you who need Network Manager to make wireless work, and who, for reasons like me, find the computer unable to access the net to get NM in the first place, here you go!
[LIST=1]
[*]Download the file [http://gotgenes.com.nyud.net:8080/nm-debs.tar.gz](http://gotgenes.com.nyud.net:8080/nm-debs.tar.gz) and save it to a thumbdrive or some removable media, then transfer it to the computer you need to install Network Manager on and put it in some place convenient. Here I assume you save it in /tmp/
(**NOTE:** if the above URL does not work for you, first try [switching to port 8090]("http://gotgenes.com.nyud.net:8090/nm-debs.tar.gz"), and failing that, try [getting it direct]("http://gotgenes.com/nm-debs.tar.gz"), but **please**, be nice to my server and stick to the Coral Cache whenever possible.)
[*]Extract the debs
```

tar -xzvf nm-debs.tar.gz

```
This should extract a folder called nm-debs.
[*]Add the "local repository" to /etc/apt/sources.list. Just add the following line
```

deb file:/tmp nm-debs/

```
It's very important that you use your respective paths here. This is for the case that your debs are in /tmp/nm-debs/ as mentioned above. (Also, please note that there is a space between /tmp and nm-debs/ per apt conventions. See the [Apt HOWTO]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages") for more information.)
[*]Update apt so it knows about the local repository
```

sudo apt-get update

```
[*]Install the debs
[LIST]
[*]For Ubuntu (GNOME) users:
```

sudo apt-get install network-manager-gnome

```
[*]For Kubuntu (KDE) users:
```

sudo apt-get install knetworkmanager

```
[/LIST]
[*]Comment/delete everything out of /etc/network/interfaces except the following two lines
```

auto lo
iface lo inet loopback

```
**If you skip the above step, Network Manager will not be able to detect your network cards!** This critical step has been posted numerous times in the forums and the wiki, so don't skip it, or we shall say "Ni!" to you.
[*]Launch Network Manager
[LIST]
[*]Ubuntu (GNOME): Alt+F2, enter in
```
nm-applet
```
[*]Kubuntu (KDE): Alt+F2, enter in
```
knetworkmanager
```
[/LIST]
[/LIST]

**NOTE:** If someone would care to test these instructions for Kubuntu, I would appreciate it. I don't know if all the dependency (i.e., required) packages for knetworkmanager are included in the current tar file. If they aren't please email and/or post on the forum what other packages are needed for knetworkmanager. Also, please verify the startup command for knetworkmanager. Thanks.

---

### Post by theBuggane on 2006-10-28
The important point here that immediately solved my problem (and may be lost in all the config file updates)...

*disable the network connections in System>Administration>Networking after installing network manager* (or better by commenting out all interfaces, apart from loopback, in /etc/network/interfaces), as mentioned by Dr. Featherking earlier on here.

Many thanks to Featherking!

...an additional point: wireless networking with Ubuntu and 3945 seems dependent on the access point. I have two d-link access points and only one works OK with Ubuntu, the other not at all. My router (d-link 624+) does not work. I also have a cheapo US Robotics router and this works all the time. All these work without complaint under Windows.

In other words, test with another wireless device too. Sorry if I am stating the obvious.

---

### Post by notebook_ftw on 2006-10-28
Well, my method was much more crude.  I simply booted from the Dapper LiveCD (in which the 3945 works perfectly) and started SPM, then selected to install Network Manager from there.  It told me the dependencies.  I went to packages.debian.net and downloaded the dependencies.  Then I rebooted into Edgy, installed the dependencies, then installed Network Manager.  Problem solved.  I'm typing this in Edgy right now.

---

### Post by Raoul Duke on 2006-10-28
I have the 3945, and it is a pain in the butt. The problem (i think) is not with Network Manager. When I change acces points, the available ESSID's do not show up, I have to scan for them with swscanner and then manually enter the one I want. Sometimes I have to unload/reload the driver to get it all going again. This is a new computer which has only run edgy, so I can't say if dapper is the same.

---

### Post by featherking on 2006-10-28
Glad someone else was helped,

@Raoul
-What are the contents of your /etc/network/interfaces file?

---

### Post by dr_d on 2006-10-29
So you guys have Network-Manager-Gnome working?

I can't for the life of me to get it to work.. Every time I boot up I get the message:

The NetworkManagerApplet cannot find some required resources. It cannot continue.

And the icon does not appear in my taskbar.. Networking itself works if I enable the connections in System|Admin|Networking.... I've tried disabling them and rebooting but same deal... 

If anyone knows how to fix this, pls help me out.

Thanks

---

### Post by dr_d on 2006-10-29
problem fixed. #1 diagnostic tool ever: search google for error message.

now i can enjoy edgy problem free.. btw isn't the new version of firefox nice

cheers

---

### Post by garethc on 2006-10-29
I've followed these instructions to the T (or I thought I did, I am an Ubuntu/Linux noob after all), and I run into a problem that nobody else seems to: when I add the 'deb file:/tmp/nm-debs/' line to sources.list, and update using 'sudo apt-get update', I get an error about the line I added being "malformed".

What did I do wrong?

Also, when I use 'gksudo gedit /etc/apt/sources.list' I get an error message relating to failed authentication procedures (would love to post the actual error message, but couldn't transfer it from Ubuntu to XP). It still lets me edit 'sources.list' and save it, however. Obviously I'm stumbling around in the dark here!

Gareth :confused: 

> **gotgenes said:**
> I have sent a HOWTO to the How To Forum but it has to be moderator approved. Thus, I'll try and replicate it here:

For those of you who need Network Manager to make wireless work, and who, for reasons like me, find the computer unable to access the net to get NM in the first place, here you go!
[LIST=1]
[*]Download the file [http://gotgenes.com.nyud.net:8080/network-manager-gnome_debs.tar.gz](http://gotgenes.com.nyud.net:8080/network-manager-gnome_debs.tar.gz) (if that URL does not work for you, remove the ".nyud.net:8080" part, but please, be nice to my server) and save it to a thumbdrive or some removable media, then transfer it to the computer you need to work on and put it in some place convenient. Here I assume you save it in /tmp/
[*]Extract the debs
```

tar -xzvf network-manager-gnome_debs.tar.gz

```
This should extract a folder called nm-debs.
[*]Add the "local repository" to /etc/apt/sources.list. Just add the following line
```

deb file:/tmp nm-debs/

```
It's very important that you use your respective paths here. This is for the case that your debs are in /tmp/nm-debs/ as mentioned above.
[*]Update apt so it knows about the local repository
```

sudo apt-get update

```
[*]Install the debs
```

sudo apt-get install network-manager-gnome

```
[/LIST]

---

### Post by featherking on 2006-10-29
> **garethc said:**
> when I add the 'deb file:/tmp/nm-debs/' line to sources.list

You appear to have added deb file:/tmp/nm-debs/ when it should have a space between /tmp and nm-debs/. So you should add this (you can copy/paste it)

```
deb file:/tmp nm-debs/
```

this is due to the way the lines are set up in the sources.list file. If you look at some of the other lines in that file you will notice they are usually -> deb space URL space directory(ubuntu version). it is the same here. When you add this line you are telling it to look for -> deb space URL(file:/tmp) space directory(nm-debs/) i believe that is your problem, if not - post back

---

### Post by garethc on 2006-10-29
Thanks,

Just goes to show I don't know command syntax in Linux, ha ha. That should do it, if not I'll repost.

> **featherking said:**
> You appear to have added deb file:/tmp/nm-debs/ when it should have a space between /tmp and nm-debs/. So you should add this (you can copy/paste it)

```
deb file:/tmp nm-debs/
```

this is due to the way the lines are set up in the sources.list file. If you look at some of the other lines in that file you will notice they are usually -> deb space URL space directory(ubuntu version). it is the same here. When you add this line you are telling it to look for -> deb space URL(file:/tmp) space directory(nm-debs/) i believe that is your problem, if not - post back

---

### Post by garethc on 2006-10-29
ok, after a few hiccups my wireless is now working. Now onto my graphics chip!

thanks so much for all the help, esp. featherking!:)

---

### Post by thenowherekid on 2006-10-29
I have the i3945 but i use kubuntu, im not sure if gnome-network manager will work for me. i can get my wireless to connect, take about 10 min. of messing around before it does connect though. any sugestions

---

### Post by featherking on 2006-10-29
havent used kubuntu, but dont they have a program similar to this network-manager that shows available networks and stores passwords in the keychain? I dont think network manager will work for because of the gnome dependencies. I think there is a program called Knetwork manager but other than that im clueless, sorry

---

### Post by gotgenes on 2006-10-29
> **thenowherekid said:**
> I have the i3945 but i use kubuntu, im not sure if gnome-network manager will work for me. i can get my wireless to connect, take about 10 min. of messing around before it does connect though. any sugestions

I just updated the packages in hopes of being more Kubuntu-friendly, [see my HOWTO post]("http://ubuntuforums.org/showthread.php?t=286188&page=2#12") and let me know if it works for you.

---

### Post by thenowherekid on 2006-10-30
Thanks very much gotgenes. It worked just fine for me. only think i dont like is that you have to use KDE wallet to store passwords. But this fix is doing wonderful. It speeds up boot time because it is not trying to configure the network. and before the only way i got the wireless to work was by disabling and then enabling it again. Awesome thanks.

---

### Post by janbockaert on 2006-10-30
> **gotgenes said:**
> I'm having the same issues here. ipw3945 used to work beautifully in Dapper but does not work right out of an Edgy install. Did someone forget to put in the linux-restricted-modules?
```

chris@feathers:~$ dmesg | grep eth1
[17179628.892000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```
Something's not right. I may have to re-install Dapper.

at this stage, i'm still playing around with the live-cd. Only to notice that there is no network, not wired and not wireless. ](*,)  I would like to install edgy tomorrow on my dell 9400 with intel pro 3945. But i got scared and a little confused.

So, could anyone confirm, that the problem with the 3945 chip is not the restricted modules (there are a lot of people posting about these restricted modules) and can you confirm, that the network problems can be solved with installing network-manager? Does anyone know what the problem with 3945 in edgy is? (it works perfect on dapper?):confused: 

Thanks

Jan

---

### Post by gotgenes on 2006-10-30
> **janbockaert said:**
> So, could anyone confirm, that the problem with the 3945 chip is not the restricted modules (there are a lot of people posting about these restricted modules) and can you confirm, that the network problems can be solved with installing network-manager? Does anyone know what the problem with 3945 in edgy is? (it works perfect on dapper?):confused: 

Thanks

Jan
Hi Jan,

That was my post with regards to restricted modules and it was bogus--the restricted modules **are** included in the Live-CD installation. I should have just done an "lsmod | grep ipw3945" to confirm this but I reacted hastily. So everything is loaded that you will need, and you could, by command-line, connect to a WAP. But who wants to do that, right? ;) (Actually, I haven't figured out how to do that yet, but if someone has a link to a HOWTO on that, please post!)

The main problem seems to be in the System -> Administration -> Networking applet (i.e., Network Settings). It fails to configure connections with the 3945 ABG wireless NIC. It also failed to work with my wired LAN NIC, too, until I manually typed in the DNS for my home router.

All these problems went away by installing Network Manager. It works great with the 3945 ABG. Don't be discouraged to install Edgy, just have those packages I've tar'd up ready when you do so you can install Network Manager and be on your merry net-surfing way. :)

P.S. Ninjai!? **YESSSS!!!!!**

---

### Post by gotgenes on 2006-10-30
> **thenowherekid said:**
> Thanks very much gotgenes. It worked just fine for me. only think i dont like is that you have to use KDE wallet to store passwords.
Yes, on the GNOME side it uses GNOME Keyring to manage passwords, which is a bit of a nuisance, but I can understand why they're used. Glad the HOWTO worked for you! :D

---

### Post by janbockaert on 2006-10-30
thanks, this is the answer i was hoping for. 

There are a lot of people on the forum, claiming missing restricted-modules were to blaim for no network with intel 3945. I'm glad this is not the case. 

As soon as i'm back home from work, i'll start the upgrade, i'll let you know how it worked out.

---

### Post by featherking on 2006-10-30
Restricted-Modules makes no sense as intel has released the source code for all there wifi chipsets (2100,2200,3945, etc) Why would they be restricted at all when we can freely view the source? This chipset ran fine in dapper and works great now, even with kismet if thats what people want. Network-Manager, for me, just always worked and was simple so i used it. period

I bet if you look on the live cd it may even have network-manager already on it. I installed dapper from a dvd a while back and network-manager was already there

P.s. I bet it uses the keyring for when you have a whole bunch of wifi spots to connect to and cant remember the passwords to all of them. Myself i have like 20 and its nice to just put in my login password and have access to all those wifi spots that i cant remember JMHO..

---

### Post by KGB on 2006-10-30
Sadly, these suggestions do not work for me, as KNetworkManager works as far as detecting my Intel 3945 Wireless and detecting my network(and some other networks in the area..). It even goes so far to ask me for the wpa2 passphrase, which I happily enter. But the activation hangs at 28% while "configuring device" and after a while it just reverts back to disconnected. If I check iwconfig eth1 while it hangs there it sometimes shows eth1 as associated to my ap and mostly not associated.
Any ideas about what is happening there?

---

### Post by gotgenes on 2006-10-31
> **featherking said:**
> This chipset ran fine in dapper and works great now, even with kismet if thats what people want. Network-Manager, for me, just always worked and was simple so i used it. period
Agreed, it all worked great in Dapper, but we now have a situation in Edgy that it doesn't work out-of-the-box. Period.

> **featherking said:**
> I bet if you look on the live cd it may even have network-manager already on it. I installed dapper from a dvd a while back and network-manager was already there
You bet all you want, but I actually *did* a fresh install from the Edgy i386 Desktop CD and it's not there. This is why I'm providing the packages in a downloadable fashion. If you just dist-upgrade from Dapper, NM will automatically update, too. This thread pertains to those doing fresh installs of Edgy. We're not posting about these problems because we're ignorant, we're posting because this is a genuine problem.

> **featherking said:**
> P.s. I bet it uses the keyring for when you have a whole bunch of wifi spots to connect to and cant remember the passwords to all of them. Myself i have like 20 and its nice to just put in my login password and have access to all those wifi spots that i cant remember JMHO..
The purpose of the keyring is to store passwords, for anything, not just WiFi, and access them with just one password, the keyring password. It's a convenience, as you said, for getting around having to remember many passwords. Enter it once in the keyring and that's the last time.

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

---

### Post by janbockaert on 2006-10-31
> **-Chi.0 said:**
> Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

Thanks, but the reason i did buy a centrino laptop was because te 3945 chipset has a opensource driver, and didn't need ndiswrapper :)

i'm backing up my dapper folders right now, i'll start installing in some hours. :)

---

### Post by gotgenes on 2006-10-31
There's no need for NdisWrapper with the Intel Pro Wireless 3945 ABG NIC. It's fully supported by the current Ubuntu kernels.

---

### Post by janbockaert on 2006-10-31
Typing in Edgy without wires. network manager working like a charm! 

Installation of Edgy was not without problems. Installation crashed twice at 94%. ](*,)  So i did a clean install of dapper, and then a painless dist-upgrade. A waist of time, i know, it took almost as long as installing windows xp :-D 

After the upgrade, i did had a wireless network, but the applet did not see any other network, than the one i was connected to in dapper.

Network Manager start working after commenting out some lines in /etc/network/interfaces. (see the howto)

thanks a lot for the support, the ubuntu community is what separates this distro from the others.

Jan

---

### Post by featherking on 2006-10-31
> **gotgenes said:**
> Agreed, it all worked great in Dapper, but we now have a situation in Edgy that it doesn't work out-of-the-box. Period.


You bet all you want, but I actually *did* a fresh install from the Edgy i386 Desktop CD and it's not there. This is why I'm providing the packages in a downloadable fashion. If you just dist-upgrade from Dapper, NM will automatically update, too. This thread pertains to those doing fresh installs of Edgy. We're not posting about these problems because we're ignorant, we're posting because this is a genuine problem.


The purpose of the keyring is to store passwords, for anything, not just WiFi, and access them with just one password, the keyring password. It's a convenience, as you said, for getting around having to remember many passwords. Enter it once in the keyring and that's the last time.

What the hell is your problem? You act as the resident expert on the topic, im pretty sure a quick read through this thread will show that youve taken everything IVE said and conveniently turned it into your own howto. And i see youve managed to give only yourself credit. No need to come looking for trouble i was just making a statement about my experience having run with few problems in the past few months

---

### Post by janbockaert on 2006-10-31
ubuntuguide.org has a different solution for the problem:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_get_ipw3945_and_wep.2Fwpa_to_work)

just to let you know.

---

### Post by kanchata on 2006-10-31
> **gotgenes said:**
> I have sent a HOWTO to the How To Forum but it has to be moderator approved. Thus, I'll try and replicate it here:

For those of you who need Network Manager to make wireless work, and who, for reasons like me, find the computer unable to access the net to get NM in the first place, here you go!
[LIST=1]
[*]Download the file [http://gotgenes.com.nyud.net:8080/nm-debs.tar.gz](http://gotgenes.com.nyud.net:8080/nm-debs.tar.gz) and save it to a thumbdrive or some removable media, then transfer it to the computer you need to install Network Manager on and put it in some place convenient. Here I assume you save it in /tmp/
(**NOTE:** if the above URL does not work for you, first try [switching to port 8090]("http://gotgenes.com.nyud.net:8090/nm-debs.tar.gz"), and failing that, try [getting it direct]("http://gotgenes.com/nm-debs.tar.gz"), but **please**, be nice to my server and stick to the Coral Cache whenever possible.)
[*]Extract the debs
```

tar -xzvf nm-debs.tar.gz

```
This should extract a folder called nm-debs.
[*]Add the "local repository" to /etc/apt/sources.list. Just add the following line
```

deb file:/tmp nm-debs/

```
It's very important that you use your respective paths here. This is for the case that your debs are in /tmp/nm-debs/ as mentioned above. (Also, please note that there is a space between /tmp and nm-debs/ per apt conventions. See the [Apt HOWTO]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages") for more information.)
[*]Update apt so it knows about the local repository
```

sudo apt-get update

```
[*]Install the debs
[LIST]
[*]For Ubuntu (GNOME) users:
```

sudo apt-get install network-manager-gnome

```
[*]For Kubuntu (KDE) users:
```

sudo apt-get install knetworkmanager

```
[/LIST]
[*]Comment/delete everything out of /etc/network/interfaces except the following two lines
```

auto lo
iface lo inet loopback

```
**If you skip the above step, Network Manager will not be able to detect your network cards!** This critical step has been posted numerous times in the forums and the wiki, so don't skip it, or we shall say "Ni!" to you.
[*]Launch Network Manager
[LIST]
[*]Ubuntu (GNOME): Alt+F2, enter in
```
nm-applet
```
[*]Kubuntu (KDE): Alt+F2, enter in
```
knetworkmanager
```
[/LIST]
[/LIST]

**NOTE:** If someone would care to test these instructions for Kubuntu, I would appreciate it. I don't know if all the dependency (i.e., required) packages for knetworkmanager are included in the current tar file. If they aren't please email and/or post on the forum what other packages are needed for knetworkmanager. Also, please verify the startup command for knetworkmanager. Thanks.

HEI, Hello now I'write on Kubuntu "on the Net", I're passed/followed alls your step, have recently installed Kubuntu 6.10 and my wifi with chip Ralink working in the install process, configuring the net by hand on installer (fail to dhcpc, back to reconfigure by hand and work, only on this step) when ends the install and boot d'nt have a connection, follow step by hand, change static ip to dhcp, back, check files, nothing.
Back to boot on windows ( have wireless connection working fine, same) going to search support and look your work, great work, open knetwokmanager, nice step, fill and GÓ.
For th people with Ralink Chipset in this case RT61PCI and Companions drivers, solved.
Many thank&#347;
Kanchata

---

### Post by featherking on 2006-11-01
while we are on the topic of compatible hardware with Network Manager, see this [link]("http://live.gnome.org/NetworkManagerHardware") to find out if your card is supported

---

### Post by solasaurus on 2006-11-02
Wah! My wireless still don't work. :(

I've read all through this thread, plus read through [this useful howto]("http://www.digitalvampire.org/blog/articles/2006/09/29/ubuntu-edgy-eft-on-a-thinkpad-x60s-how-to-make-ipw3945-work") and [this  bug report]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62452"). I've installed the linux-restricted-modules and network-manager + network-manager-gnome. My wired connection is working fine now using DHCP over NetworkManager as eth0, but there is no eth1. lsmod says ipw3945 is there and top tells me its running, but it just won't show up. It doesn't even show up in the System|Admin|Networking anymore.

The only instruction I've yet to follow is to "reload the ipw3945 module". To be honest, I don't know how. I tried to "rmmod ipw3945" but it wouldn't let me. :(

I'm desperate to get this working as I'm headed to an Educational Computing Conference in a couple of days and I really wanted to show off Ubuntu (and use the wireless like everyone else) but I'm really stuck after 2 hours trying to figure this out. :(

If anyone knows what I've got wrong I'd appreciate their advice. I've got a Dell Inspiron 6400 with Intel wireless....

---

### Post by mikael_b on 2006-11-02
Hi,

I followed the how-to and I can start NM and it finds my network.
But when i try to connect to it just keeps trying until till fails,
the network is not even encrypted. Anyone know what this could depend on?

---

### Post by alingex on 2006-11-02
I have exactly the same problem as solasaurus.
I tried everything you suggested, but eth1 still won't show up.
It's an Acer Aspire 5550 with Intel Wireless in my case.

---

### Post by featherking on 2006-11-02
@mikael_b
 I once had this issue, and it ended up being a problem with my router, it didnt have enough free DHCP slots free to give one to my laptop? Could this also be your issue?

@solasaurus,alingex
 is your wireless switch turned to ON in your BIOS? It cant be off or adjustable in my experience. If it is not set to ON or ALWAYS ON or something like that, it will not work but may appear to be there

---

### Post by mikael_b on 2006-11-02
> **featherking said:**
> @mikael_b
 I once had this issue, and it ended up being a problem with my router, it didnt have enough free DHCP slots free to give one to my laptop? Could this also be your issue?


So I looked at my router but it can handle up to 99 computers. As there are only 5 connected that shouldn't be a problem. Furthermore I tried to reinstall ubuntu and the first thing i did was to do the how to again, posted abov... But still the same problem. My computer finds the network, i select it so it should connect, and it try to connect for 2 min and then fails.. 

Maybe there is a log file for NM?

---

### Post by mikael_b on 2006-11-02
Ok, this is strange, I tried with another wlan and it works. Isn't it possible to use åöä for the name of wirless network?

I tried to changed the sid from "test" to "töst" and it stoped working.. so people one new thing to learn, do NOT use any special chars in the ssid!

---

### Post by gotgenes on 2006-11-02
> **mikael_b said:**
> Maybe there is a log file for NM?
Try killing NetworkManager and starting it as no-daemon:
```

sudo killall NetworkManager
sudo NetworkManager --no-daemon

```
Should print a lot of info to STDOUT. Watch it to see what it does when it attempts to connect to your network.

---

### Post by TorchlightJay on 2006-11-03
I have done everything as well. My eth1 works.... if I am about 3 feet away from the router. If I am going to have to hang out that close, I might as well be connected with eth0. Anyone have any idea why my computer would need to be that close in order to connect? As for the ones whom say the network manager doesn't work, go ahead and get right by your router and see if it works then.

---

### Post by solasaurus on 2006-11-03
Thankyou Featherking and gotgenes for your help (from the very beginning!) I finally did get NetworkManager and nm-applet working. After rebooting the wired connection is flawless and the wireless worked for a short while before crashing. :confused: This had me locked out of the internet for the past day or so. :-#

I've now diagnosed two problems, only one of which is strictly to do with wireless, and I think more of a hardware issue:

1. wireless crashes and causes momentary hanging of computer -> I looked into this and found these messages in /var/log/syslog
> Nov  4 08:29:31 tesla kernel: [17183505.964000] ipw3945: uCode verification failed at addr 0x00003800+0 (of 900)
Nov  4 08:29:31 tesla kernel: [17183505.964000] ipw3945: Unable to load firmware: -5
Nov  4 08:29:31 tesla kernel: [17183505.988000] ipw3945: uCode verification failed at addr 0x00003800+0 (of 900)
Nov  4 08:29:31 tesla kernel: [17183505.992000] ipw3945: Unable to load firmware: -5
Nov  4 08:29:31 tesla kernel: [17183506.016000] ipw3945: uCode verification failed at addr 0x00003800+0 (of 900)
Nov  4 08:29:31 tesla kernel: [17183506.016000] ipw3945: Unable to load firmware: -5
Nov  4 08:29:34 tesla kernel: [17183509.012000] ipw3945: Unable to initialize device after 5 attempts.
Nov  4 08:29:34 tesla kernel: [17183509.056000] ipw3945: Microcode HW error detected.  Restarting.
Nov  4 08:29:34 tesla kernel: [17183509.080000] ipw3945: uCode verification failed at addr 0x00003800+0 (of 900)
Nov  4 08:29:34 tesla kernel: [17183509.084000] ipw3945: Unable to load firmware: -5
Nov  4 08:29:34 tesla kernel: [17183509.108000] ipw3945: uCode verification failed at addr 0x00003800+0 (of 900)
Nov  4 08:29:34 tesla kernel: [17183509.108000] ipw3945: Unable to load firmware: -5

ad infinitum... Looks like something is wrong with the Intel Wireless Pro driver. :confused: 

2. networking can't see past gateway -> back when I was a Suse user (all of 1 month ago) I would always type my gateway address into the network config. Ubuntu doesn't ask for this. So I can now see my router (192.168.1.2), all the pcs on the network (192.168.1.*) and the gateway/modem (192.168.1.254). But I cannot even ping IPs on the net, so I know it's not DNS related. Which file do I edit to point it to the gateway address???

---

### Post by kikos on 2006-11-04
I too did a fresh install of Edgy and couldn't get the 3945 to work.  After doing some research I found that while /etc/modprobe.d/ipw3945 exists in Edgy fresh install, /sbin/ipw3945d-2.6.17-10-generic does not.  The ipw3945 modules needs ipw3945d to make the network interface work.

ipw3945d exists in the restricted-modules, but I could not use it because it would mess up my beryl install.  So what I did is (1) apt-get install the restricted-modules; (2) copy the /sbin/ipw3945d-2.6.17-10 into my home directory; (3) apt-get purge restricted-modules; (4) copy the ipw3945d file back into /sbin

ifconfig eth1 up, and ubuntu recognized the ipw3945 wireless interface.  Next, i installed network-manager as instructed in this thread, and my wifi seems to work flawlessly.

---

### Post by LordYama on 2006-11-04
I had some trouble connecting, but everything worked flawlessly after I rebooted my wireless router. The wireless on my other laptop was working with it without dramas, so restarting the router didn't cross my mind.

So my advice to everyone is to restart your router before looking at the software settings on the laptop.

---

### Post by elektronaut on 2006-11-09
> **kikos said:**
> I too did a fresh install of Edgy and couldn't get the 3945 to work.  After doing some research I found that while /etc/modprobe.d/ipw3945 exists in Edgy fresh install, /sbin/ipw3945d-2.6.17-10-generic does not.  The ipw3945 modules needs ipw3945d to make the network interface work.

ipw3945d exists in the restricted-modules, but I could not use it because it would mess up my beryl install.  So what I did is (1) apt-get install the restricted-modules; (2) copy the /sbin/ipw3945d-2.6.17-10 into my home directory; (3) apt-get purge restricted-modules; (4) copy the ipw3945d file back into /sbin

ifconfig eth1 up, and ubuntu recognized the ipw3945 wireless interface.  Next, i installed network-manager as instructed in this thread, and my wifi seems to work flawlessly.
I followed your advice, but one point was missing (at least for a newbie like me ;) ): ipw3945d has to be called, it won't automatically be loaded after a reboot. Now everything is O.K. :) 
If you need more information, you can find it in [my thread]("http://ubuntuforums.org/showthread.php?p=1735521").

---

### Post by pgilmon on 2006-11-28
I think that if you follow the instructions in [1] and [2] it will be executed automatically at startup. I did that because I had to remove the restricted modules in order to install the nvidia proprietary drivers.

[1]: [http://www.ubuntuforums.org/showpost.php?p=1722490&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1722490&postcount=2)
[2]: [http://www.ubuntuforums.org/showpost.php?p=1722497&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1722497&postcount=3)

---

### Post by mikewhatever on 2006-12-17
nice

---

### Post by morpheus01 on 2007-02-27
FINALLY;

The solution for those with broken Intel wireless devices after the Kernel update (for people as thick and fresh as I am).

1. PLUG IN AN ETHERNET CABLE FROM YOUR PC TO YOUR MODEM.
2. GO TO SYSTEM-ADMINISTRATION-SYNAPTIC PACKET MANAGER.
3. SEARCH FOR "LINUX-RESTRICTED-MODULES 2.6.17".
4. MARK FOR INSTALLATION, APPLY AND RESTART PC.
CONGRATULATIONS.

Ethernet cable = standard wired Internet cables come with modems to link to PCs.

---

### Post by maku777 on 2007-05-04
thank you SO MUCH to the original poster for this tutorial.  I've worked 2 days as a newb trying to get the network manager working....with this and another great tutorial to enable WPA

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

.I'm on the internet with my desktop, ubuntu 6.10, and wireless usb linksys adapter.

thanks again.
-maku

---

