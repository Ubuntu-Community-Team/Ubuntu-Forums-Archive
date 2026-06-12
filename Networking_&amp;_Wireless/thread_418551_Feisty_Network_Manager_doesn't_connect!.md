---
title: "Feisty: Network Manager doesn't connect!"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Der Doktor on 2007-04-22
Hi!

Yesterday, I installed Feisty on my system! Now, I have the problem, that it doesn't connect to my WEP-WLAN (which worked fine under Edgy!).
If I write the SSID and the key directly into my /etc/network/interfaces, Ubuntu connects to my WLAN!
So, whats wrong with the Networkmanager? :confused: 

So long
Doc.

---

### Post by Sunflower1970 on 2007-04-22
Sadly, some people have trouble with network manager(I'm one of them). On my laptop, in Edgy, everything worked fine (I was using wifi radar). When upgrading to Feisty, my wireless stopped working. I uninstalled network manager and went back to wifi radar. Everything's working great again. Wifi radar is in the repos, or it can be found here: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/).  Some people are using wicid as well. I think it's on sourceforge.net somewhere.

---

### Post by Ichijin on 2007-04-22
how do u remove the network manager?

---

### Post by luisromangz on 2007-04-22
It works very well, but you have to remove the wireless interface from /etc/network/interfaces so KNetworkManager is able to manage the interface. No sure if NetworkManager behaves in the same way...

Hope you get it working, it's such a great app.

---

### Post by Der Doktor on 2007-04-22
@Sunflower1970: I used the Network Manager under Edgy and it worked perfectly!

@uisromangz: I tried to comment out the ath0 interface in my /etc/network/interfaces but this didn't work, too.

---

### Post by danieltellez on 2007-04-22
> **Sunflower1970 said:**
> Sadly, some people have trouble with network manager(I'm one of them). On my laptop, in Edgy, everything worked fine (I was using wifi radar). When upgrading to Feisty, my wireless stopped working. I uninstalled network manager and went back to wifi radar. Everything's working great again. Wifi radar is in the repos, or it can be found here: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/).  Some people are using wicid as well. I think it's on sourceforge.net somewhere.

... i've tried with wicd, network manager, and directly editing interfaces file... but nothing. I'm using a dlink dwl 122 adapter and the system thinks it's a wired lan adapter instead of a wireless adapter.
Both, wicd and network manager, show me the networks but don't let me connect them... 

Buaaa !!!

---

### Post by Ichijin on 2007-04-22
with wicd and wifi radar i can now connect to unsecure networks.  but stil can't access my WEP network

---

### Post by Tigera on 2007-04-22
I don't know if this will help you or not, but I found out that I had to delete the line that said "wpa-conf managed" in my /etc/network/interfaces file.  (Please see [http://lists.alioth.debian.org/pipermail/pkg-wpa-devel/2006-December/000896.html]("http://lists.alioth.debian.org/pipermail/pkg-wpa-devel/2006-December/000896.html") for more info).  I've been manually hacking my interfaces file since Dapper, so if you have inherited that file from Edgy, this might work for you.
If it doesn't, maybe post the output of the 
```
sudo /etc/init.d/networking restart 
```
command so that others can help.  Good luck.

---

### Post by jonocorp on 2007-04-23
I know that wifi in Edgy was buggy.  It always listed my wifi signals as 90%+, and I could connect network anywhere in the house.

Now, with Feisty, I can barely connect in my room.  My signal in my room now is at 20-30%.  When I go to another room where the signal is at least 40%+, I can SOMETIMES connect.  In Edgy, I can connect with my network almost all of the time, but in Feisty, it's almost a crapshoot.

First of all, I shouldn't be getting a weak signal like that when the router is only in the next room.  How is it detecting such a weak signal where it shouldn't be?

I would really like to see this fixed.

I've/am using Network Manager.

---

### Post by Der Doktor on 2007-04-23
Hi!

I don't have a "wpa-conf managed" line in my /etc/network/infertaces! (I think this ist because I WEP and not WAP ;) ) I also tried to delete the lines with ath0, but this didn't word, too!
So, whats to da?

---

### Post by beerorkid on 2007-04-23
I had some strange probs this weekend as well.

I installed feisty and using a "works out of the box" belking wifi card I got connected to my network no prob.  Borked the system and reloaded it, and now I cannot get it to connect to my network with the card.

Will mess around with it tonight and see if I can figure it out.

---

### Post by Der Doktor on 2007-04-24
Hi!

Now, I tried to use the NetworkManager under Edgy (Live CD) and there, it worked pertectly with the same configuratin!
So, there's a fault in Feisty! :confused:

---

### Post by macabro22 on 2007-04-26
I've got the same problem! Kwifi lists the available networks but wont connect. Dammit!

---

### Post by bedake on 2007-04-26
I am having a similar problem, when using network manager it will show the available networks but I cannot connect to any at all.  The only exception seems to be my home network which network always times out on during the first boot and makes me manually select that network to connect to.  Thats not so much a problem for me as it is an inconveniance.


However at my college it is a different story, I try to connect to one of the several available networks and each one I fail to connect to.  When I first boot up and select a network, network manager will show one of those little glowing orbs for beginning the connection and then time out a minute or so later, after I try to connect again one of those orbs wont even show up.  This seems to happen to every network but my home one for some reason.


So any ideas why I can connect to my home network via wireless fine but not anywhere else?


I havent tried wifi radar yet because im worried that if I uninstall network manager I wont even be able to connect at home anymore.



The output my iwconfig after unsuccesfully attempting to connect to my school's network.

IEEE 802.11b/g  ESSID:"Library2"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:15:F9:38:80:20   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by kyle_fransham on 2007-04-26
> **bedake said:**
> I am having a similar problem, when using network manager it will show the available networks but I cannot connect to any at all.  The only exception seems to be my home network which network always times out on during the first boot and makes me manually select that network to connect to.  Thats not so much a problem for me as it is an inconveniance.

However at my college it is a different story, I try to connect to one of the several available networks and each one I fail to connect to. When I first boot up and select a network, network manager will show one of those little glowing orbs for beginning the connection and then time out a minute or so later, after I try to connect again one of those orbs wont even show up. This seems to happen to every network but my home one for some reason.


I have the exact same issue.  I configured my wireless at work yesterday (finally....) and I could connect here, but when I got home I couldn't connect to my network (or any of my neighbours' unencrypted networks ;) )

I got back into work today and found that I could still connect to the wireless network here.

There's nothing except auto lo stuff in my /etc/network/interfaces file.

Does anyone know where the configuration file for NetworkManager resides?  Perhaps there's something there that records the first network you successfully connect to, and then doesn't let you connect to any others?  (I'm grasping at straws here...)

bedake:  strange that your iwconfig output shows you as connected to the library network and registers the mac address of the access point, but no quality to the connection.  I don't actually know what that means.  I'll see what my iwconfig output says when I unsuccessfully attemt to connect to my home network.

---

### Post by Melcar on 2007-04-26
I had a similar problem.  Networkmanager would simply not connect.  Turned out to be a problem with ndiswrapper, so I just compiled it from source.  Everything works perfectly now.

---

### Post by Der Doktor on 2007-04-26
@Melcar: I don't use the Ndiswrapper, because my WLAN-Card is supported "out-of-the box"!

@macabro22: Can you connect to your WLAN, if you add the SSID and the WEP key (if you WLAN is WEP) to you /etc/network/interfaces?

**I see, that I'm not alone with my problem!**

---

### Post by wersdaluv on 2007-04-27
I think I have the same problem. See [this thread]("http://ubuntuforums.org/showthread.php?p=2543968#post2543968").

Have you already found a solution to connect with Feisty?

---

### Post by holscher on 2007-04-27
i've got the same problem... if i close network manager with the sytem monitor i can connect to by using iwlist and iwconfig in a terminal. 
:confused:

---

### Post by bedake on 2007-04-27
> **kyle_fransham said:**
> 
bedake:  strange that your iwconfig output shows you as connected to the library network and registers the mac address of the access point, but no quality to the connection.  I don't actually know what that means.  I'll see what my iwconfig output says when I unsuccessfully attemt to connect to my home network.

Yeah, I was wondering about that myself,

It is also probably worth mentioning, that I have had this problem in both edgy and feisty.



Obligatory bump for attention.

---

### Post by marcelop on 2007-04-27
Unfortunately (I think) you are not alone:
[http://ubuntuforums.org/showthread.php?t=414793](http://ubuntuforums.org/showthread.php?t=414793)

It seems the Ubuntu developers may need to spend sometime working on the NetworkManager.

---

### Post by Der Doktor on 2007-04-28
> **wersdaluv said:**
> Have you already found a solution to connect with Feisty?
Yes! I disabled the network manager and added the SSID and the WEP-key to my /etc/network/interfaces manually!

---

### Post by jackn on 2007-04-28
> **Sunflower1970 said:**
> Sadly, some people have trouble with network manager(I'm one of them). On my laptop, in Edgy, everything worked fine (I was using wifi radar). When upgrading to Feisty, my wireless stopped working. I uninstalled network manager and went back to wifi radar. Everything's working great again. Wifi radar is in the repos, or it can be found here: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/).  Some people are using wicid as well. I think it's on sourceforge.net somewhere.

I've followed Sunflower1970's advice. No honey.

Network-manager can be removed with 
```
sudo aptitude remove network-manager-gnome
```

and then

```
sudo aptitude remove network-manager
```

The site quoted by Sunflower above allows you to download a version of wifi-radar for Feisty. This I had to do on my desktop as, obviously, my laptop has no connection to the net. I then burnt it onto a CD (a floppy will do) and copied it onto the laptop. After installation, it could show me all the local wifi networks, but i wasn't connected.

Some relevant facts: First, In my case, as in the case of others on the thread, the same laptop worked like a charm with Edgy. Then, I've also tried to connect off of the CD, and that doesn't work either.

Help?

Jackn

---

### Post by jackn on 2007-04-28
Issue solved, thanks to the following [post]("http://ubuntuforums.org/showthread.php?t=413594&page=4") by adotB:

> I was having the same problem: Network Manager could see wireless networks but never connect to them. The ethernet on my laptop doesn't work, so you see how this was a big problem. I downloaded the earlier version using my Windows partition from the repos:

network-manager:
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.3-2ubuntu6_i386.deb)

and the applet:
[http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.3-2ubuntu6_i386.deb)

I uninstalled the network-manager packages and installed the older versions and now i happily browse the internet. The update manager always shows the updates of course, but if you don't mind that, this might be a good solution until this bug is fixed.

This did the job for me. I used my desktop to burn the files onto a CD and then copied them to the laptop.

Once installed, you only need to click the network-manager on your icon, and provide the necessary data to your connection.

Jackn

---

### Post by jerrylamos on 2007-04-28
On this system, looking at /var/log/syslog, during boot Network Mangler disables my network card.  When Fiesty boots up, there's a little red mark on the Nework Mangler icon, I click on it, says there is no network connection (of course, Network Manager just disabled it!) I click on wired connection, and it comes up.  I have to remember to do this on every boot.

It doesn't do any good to remove the Network Mangler package because it removes the desktop icon but does NOT remove Network Mangler's disabling of my network card.  Now with no icon to click, I have to bring up a terminal and do sudo dhclient, enter password.

To me it seems as if Feisty started out as Network Mangler and they added Ubuntu to it.  There is some myth that if you have multiple internet connections (who has that?) Network Mangler will automagically switch to the better connection.  There's another myth that Network Mangler is supposed to manage wireless access and switch to the stronger signal.  What I see mostly on the forums is their wireless card stopped working with Feisty.

Wonder what Gutsy Gibbon will do...

Cheers, Jerry:confused:

---

### Post by Der Doktor on 2007-04-29
> **hroit said:**
> Issue solved, thanks to the following [post]("http://ubuntuforums.org/showthread.php?t=413594&page=4") by adotB:



This did the job for me. I used my desktop to burn the files onto a CD and then copied them to the laptop.

Once installed, you only need to click the network-manager on your icon, and provide the necessary data to your connection.

Jackn
I installed the version from the Edgy reposity and now, it works! :)

---

### Post by jubilee33 on 2007-04-29
I have two different laptops and the network-manager behaves differently.  Both laptops have a clean installation of Feisty.  On the Dell Inspiron 600m, the network manager is merely a decoration.  No connection info whatsoever!  But miraculously, the wireless connection works right after the CD installation.  On the other laptop, I am permanently stuck with a grayed-out wired connection that doesn't exist.  [I seem to have a connected wireless network but I cannot access the Internet at all]("http://ubuntuforums.org/showpost.php?p=2558237&postcount=8").  Very weird!

It's such a pity that I waited from Dapper to Edgy and finally Feisty for my buggy soundcard to work.  Now I'm stuck with a faulty wireless network all of a sudden.  I'm totally lost.

---

### Post by zshift on 2007-05-02
I'm not sure how many of you this will help, but I noticed a small detail i kept messing up with. 

when network manager asks you for the wep passkey, there are several options that you can choose: WEP passphrase, HEX, and ASCII. 

passphrase is the word that you chose on the router, like "bob" or "thisisthepasskey".
the Hex is the long hexadecimal encrypted version of the passphrase, like "9283640fe932a..."

My mistake was that i kept putting in the Hexc value while having selected the passphrase option. 
I hope this helps some people that overlook things often.

---

### Post by bedake on 2007-05-03
I uninstalled network manager and installed wifi manager and I still have the same problems connecting to any network but my own.  Its giving me the message, failed to acquire IP address

---

### Post by jackn on 2007-05-03
Bedake, have you tried the older 'network managrer'?

Like yourself, I wasn't able to get another networking app to work, but the older Ubuntu version did the trick. 

It's worth a shot. Please see post #24.

Jackn

---

### Post by robin.w on 2007-05-03
I had exactly the same problem with my network-manager after upgrade Ubuntu 6.10 Edgy to 7.04 Feisty. Before my wifi card worked perfectly (***Broadcom bcm4318, driver by ndiswrapper***) but after I just could make a connection using iwconfig without WPA. Network-manager didn't work at all. 
If you want to have your network-manager (*knetworkmanager or network-manager-gnome*) just remove it and install older version.

```
sudo apt-get remove network-manager
```
Next download older network-manager package from Edgy 6.10 (*viz attached files*) and install.
```
sudo dpkg -i network-manager_0.6.3-2ubuntu6_i386.deb 
```
and also install knetworkmanager or network-manager-gnome (*depends on your GUI, I have KDE:KS *).
```
sudo apt-get install knetworkmanager
```

Now it should be ok. Just run knetworkmanager and check available wifi networks.

But pay attention during upgrade your system. If you upgrade network-manager you'll be back and your network-manager won't work like before. Let's hope that the bug will be fixed soon.

---

### Post by Der Doktor on 2007-05-05
> Let's hope that the bug will be fixed soon.

Has the bug been reported at Launchpad?

---

### Post by sean on 2007-05-06
I use Ubuntu Fesity on my Dell D620 with a BCM4310 chipset.  I use ndiswrapper and have to connect manually because NetworkManager is completely useless for me with Feisty.  It would be nice if NetworkManager would play nice with Ndiswrapper.

Sean

---

### Post by tompravi on 2007-05-22
Thank you very much, **_robin.w_**
I was looking for it. 
Thank you

After appling your solution **I have upgraded to the current pkg of network-manager and the connection to internet continued to be ok.**

So, I tried a new installation of ubuntu. This time I tried and succeded to configure my dlink/dwl-g650 wireless card of my laptop before of the installation. 
After this  I had a working internet connection. Then I continued with installation.
After the rebooting and entrance to my new ubuntu/linux system I realized that the wireless card was configured and operated very well.

I don't think that the problem is with network-manager only.

PS. Sorry about my english

---

