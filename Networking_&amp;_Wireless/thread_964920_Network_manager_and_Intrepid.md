---
title: "Network manager and Intrepid"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by mavo on 2008-10-31
Since upgrading, Network Manager no longer connects to my wifi network.  

The network is detected then Network Manager requests a network address from the wireless network.  After a while, the dialogue box appears asking tor network authentication.  Then the process repeats itself without ever successfully connecting.

I'm using a Dell Inspiron 1525 and was previously using Network Manager 0.7 successfully under Hardy to access wifi and mobile broadband.  Mobile broadband still works but wifi doesn't.

Any advice please?

---

### Post by JGrubbs on 2008-10-31
I am having the same problem!! If I reboot it will connect, but if I close my laptop it disconnects, and won't reconnect unless I reboot again. I even tried removing the network-manager, **[COLOR="Red"]WHICH I DON'T RECOMMEND!![/COLOR]**

This made my laptop unable to connect at all, I had to find the packages for network-manager and network-manager-gnome and transfer them to my laptop from disc and then reinstall them.

I am now able to connect after rebooting, but if I close my laptop, the connection is lost and requires a reboot to reconnect.

---

### Post by superprash2003 on 2008-10-31
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by JGrubbs on 2008-10-31
The link you posted is for an old distribution of Ubuntu, it even states, "I'm getting mixed feedback from Hardy Heron (version 8.04) beta testers. There is a bug with (ssb) module loading (bug 1 bug 2) that prevents ndiswrapper from working properly for some users."

It doesn't say anything about 8.10 Intrepid. Everything was working okay in Hardy, and it stopped working after upgrading to Intrepid, so their must be a bug in the updated Ubuntu. Hopefully they will fix it soon!

---

### Post by ChrisBieda on 2008-10-31
We are not alone, by all appearances.  Scanning the threads here indicates that wireless cards are detecting encrypted signals (both WEP and WPA) but Network Manager will not connect to them when supplied with the appropriate key or passphrase.

With wireless now down, I guess I'll have to run a temporary 50' Ethernet so I can get the inevitable update that fixes this.  (Sigh.)  

And the 7.10->8.04 update went SO smoothly.:sad:

---

### Post by JGrubbs on 2008-11-01
It's not just with WEP and WPA, I tested today with a wireless signal with all security turned off, when I connect to the hidden wireless signal it works until I close my laptop, then it stops working until I reboot.

---

### Post by MockY on 2008-11-01
The following is only true for my laptop. Skip to the end if you don't like to read.

I strongly suggest that you don't use Network Manager at all. It is extremely unreliable and slow. It has not worked for me since Feisty. And the fact that it worked flawlessly on Feisty and not ANY Ubuntu release after that is not just odd, it's down right horrible.

Feisty has worked for me just fine so I haven't bothered installing any later release until now when the support is obsolete for it, and I assume the updates stops coming along with that. So I installed Linux Mint 5 and was over all very happy with it. Network manager actually worked, but it did not connect automatically to my network on reboot until the computer had been on for about 8 minutes. Sometimes even longer than that. So I installed Wicd and holy crap!!!! This software worked beyond flawless in Mint and life went on. 
But due to minor bugs (not being able to switch keyboard setting is one of them) I now installed Intrepid. And just like I expected, Network Manager did not work like it should. I am able to connect at first, but it keeps asking me for password over and over again. It finally stops asking me after 20 times and I can manually enter my wifi information in order to connect. I gave it another try and rebooted. But it was the same story after that. I did not waste much time and installed wicd instantly.

To my surprise, it did not work as good as I wanted. I have a SmoothWall setup with wireless on it's own NIC, completely excluded from the green LAN, and on top of that, I do not broadcast my ssid. This however does not work in Ibex (I bet it will in future Mint releases since it works perfectly in the current). If I broadcast my SSID however, then it works just as flawlessly as I remembered it. I'm not specifically worried since I run WPA and on a specific wifi network protected by my smoothwall, so I'm just going to continue to broadcast it.

Loooong story short, do yourself a favor and completely dump Network Manager and replace it with Wicd.

Get it from [HERE]("http://wicd.sourceforge.net/download.php"). Upon install, it will automatically remove Network Manager. Very smooth install method.

---

### Post by jokker on 2008-11-01
Not only for laptops ! I struggle since yesterday night to get my server to have a static IP addresses on both gigabit NICs. There is no way to get it to work. NO matter what I try, it goes back to dhcp after reboot ! What's wrong with with this ubuntu ??????? Why is there not an update fixing this issue ALREADY ???
I am more than upset right now. My website is down, my ssh server is down, print server is down, ftp is down, samba is down... Unfortunately everything has to be setup with static IP at home

---

### Post by guycross on 2008-11-01
I am running a Dell inspiron 1520 - and I am brand new to ubuntu/linux - I cannot find wireless at all on that laptop- so i am on my old P600 vaio!

help... where do i start

---

### Post by JGrubbs on 2008-11-01
I got this working today, but checking something I should have thought to check before. For some reason my WEP security key was changed to something totally different than what it was before the upgrade. I changed it back today, and now my wireless disconnects when the laptop goes to sleep, but I am able to reconnect by clicking on the icon and selecting the wireless connection again, without having to reboot.

---

### Post by guycross on 2008-11-01
mine key is fine, i am connected through the same router on my old laptop... thats how i am typing here!

my dell just hasnt found my wifi "chip" or whatever is in the laptop

---

### Post by guycross on 2008-11-01
i got the broadcomm wifi card - wud appreciate sum help gettin it wurkin

---

### Post by guycross on 2008-11-01
> **guycross said:**
> i got the broadcomm wifi card - wud appreciate sum help gettin it wurkin

please.... i really want to get going with linux/ubuntu - but unless i can get my wifi working ia m going to have to delete it.

---

### Post by mavo on 2008-11-02
Thanks for the above comments.  Does anyone else agree that switching to Wicd is the way forward?  Looking at its website, I'm not sure it would handle 3G mobile broadband.

---

### Post by penC on 2008-11-02
MockY,

Great many thanks! I've been struggling with lousy signal level & slow connectivity with my Acer 5102 (with AR2413 chip) + several versions of Ubuntu, while a b****y old Apple G4 connects just like a snap. Wicd seems to have solved this problem (so far, knock-knock) :-)

  pen

---

### Post by eks on 2008-11-02
I do also strongly recommend wicd. I use on both laptops, a Pavilion and a Acer Aspire One. It's much more full featured and with a cleaner interface, excellent when you are on the road.

On the desktop I've left the normal network manager because never had any problem.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by waffen on 2008-11-02
Yeess!!! Its working! I just installed it.. and I can connect with my static ip (I check that with ifconfig command!) I can see a pair o wireless networks then I can not see before :D ... on monday I can try to connect to another wifi network.. today is impossible for me.. or another wifi user to confirm then Wicd work with Wifi??

Thanks!

---

### Post by mavo on 2008-11-02
OK.  I added this to my third party repositories:

deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

Then ran this command:

wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

But Wicd is not showing up in Synaptic when I run a search for it.  How did others manage to install it?

---

### Post by waffen on 2008-11-02
aja.. I have the same issue.. try downloading the deb package from sourceforge repo directly.

---

### Post by crussia on 2008-11-03
> **mavo said:**
> Thanks for the above comments.  Does anyone else agree that switching to Wicd is the way forward?  Looking at its website, I'm not sure it would handle 3G mobile broadband.

Switching to wicd made no difference. It scanned my networks just like NM and refused to connect to them after cycling through connection a few times. I have a broadcom BCM4306, by the way, running with ndiswrapper.

NM worked with Feisty. Could not work with Hardy and I had to upgrade because of compatibility problems with updates to applications. I had hoped that problems with networking had been fixed in Ibex.

> **mavo said:**
> OK.  I added this to my third party repositories:

deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

Then ran this command:

wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

But Wicd is not showing up in Synaptic when I run a search for it.  How did others manage to install it?

'sudo apt-get install wicd'   did the trick for me, but it did not help with my connection problems.

---

### Post by inkrypted on 2008-11-03
I was having alot of the same problems both on mine and my wifes notebook. I finally got fed up and this worked beautifully even better than the new manager.

[http://ubuntuforums.org/showthread.php?t=969061](http://ubuntuforums.org/showthread.php?t=969061)

---

### Post by mavo on 2008-11-03
Wicd has sorted the problem, and seems to remember my encryption key which is more than NM ever did.

Unfortunately, it seems not to support my 3G wireless broadband device.  But that's another problem.

Thanks to Mocky for the steer.

---

### Post by waffen on 2008-11-03
> **mavo said:**
> Wicd has sorted the problem, and seems to remember my encryption key which is more than NM ever did.

Unfortunately, it seems not to support my 3G wireless broadband device.  But that's another problem.

Thanks to Mocky for the steer.

Check this [Bug 291902] in PPA, is possible the people found the solution there for NM.... if any try this with success comment please here...

---

### Post by MockY on 2008-11-05
> **mavo said:**
> OK.  I added this to my third party repositories:

deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

But Wicd is not showing up in Synaptic when I run a search for it.  How did others manage to install it?

I added hardy instead of intrepid in Synaptic
```
deb http://apt.wicd.net hardy extras
``` 

then did a reload. Close Synaptic (it will not show up there for whatever reason.) Fire up the terminal and type
```
sudo aptitude install wicd
```
and it will install just fine. You have to manually start Wicd after install (it's located undet the Internet menu, or simply restart your computer.

---

### Post by mavo on 2008-11-07
Thanks.  I got it installed eventually using

sudo apt-get install wicd

---

### Post by arilds on 2008-11-07
> **jokker said:**
> Not only for laptops ! I struggle since yesterday night to get my server to have a static IP addresses on both gigabit NICs. There is no way to get it to work. NO matter what I try, it goes back to dhcp after reboot ! What's wrong with with this ubuntu ??????? Why is there not an update fixing this issue ALREADY ???
I am more than upset right now. My website is down, my ssh server is down, print server is down, ftp is down, samba is down... Unfortunately everything has to be setup with static IP at home
I had similar problem, and the solution to my issue was surprisingly easy.

Added the nameservers manually in /etc/resolver.conf and things started working again.

---

### Post by FreewheelinFrank on 2008-11-23
> **mavo said:**
> Thanks.  I got it installed eventually using

sudo apt-get install wicd

This worked for me too, thanks.

Add me to the list of people who couldn't find Wicd in Synaptic after adding the repository and key and updating.

---

### Post by mtalexan on 2008-11-26
Assuming I use the hardy version of the repository ```
deb http://apt.wicd.net hardy extras
```
instead of intrepid, ```
deb http://apt.wicd.net intrepid extras
``` and manually trigger the install from the command-line ```
sudo apt-get install wicd
``` since the package never shows up in Synaptic, everything seems to work fine.

Thanks to everyone for all the help, my connection is now faster and more consistent than it was with the Network Manager.  Hopefully the Ubuntu developers will realize everyone's getting sick of this Network Manager crap after every upgrade and just pull in wicd as part of the standard package instead.

The only downside to using wicd, is the lack of an icon in the system tray to indicate the current connection state.  I ended up just throwing the app launcher to my launcher panel so I can check it whenever I feel like.

---

### Post by jemvyc on 2008-11-27
I just changed to wicd. It works as advertised,  BUT!  It will only recognize my installed Atheros wifi and the wired network.  It will not recognize either my rtl8187 dongle or my DWL 120+   Otherwise, it's great.

Does anybody have an idea what is wrong or if I can fix it?

Jim

---

### Post by waffen on 2008-11-27
> **jemvyc said:**
> I just changed to wicd. It works as advertised,  BUT!  It will only recognize my installed Atheros wifi and the wired network.  It will not recognize either my rtl8187 dongle or my DWL 120+   Otherwise, it's great.

Does anybody have an idea what is wrong or if I can fix it?

Jim

are you try to put the same question in the wicd bug report section?

---

### Post by mtalexan on 2008-11-30
It seems I was a little hasty in my previous praise of wicd.

> **mtalexan said:**
> Assuming I use the hardy version of the repository ```
deb http://apt.wicd.net hardy extras
```
instead of intrepid, ```
deb http://apt.wicd.net intrepid extras
``` and manually trigger the install from the command-line ```
sudo apt-get install wicd
``` since the package never shows up in Synaptic, everything seems to work fine.

Thanks to everyone for all the help, my connection is now faster and more consistent than it was with the Network Manager.  Hopefully the Ubuntu developers will realize everyone's getting sick of this Network Manager crap after every upgrade and just pull in wicd as part of the standard package instead.

The only downside to using wicd, is the lack of an icon in the system tray to indicate the current connection state.  I ended up just throwing the app launcher to my launcher panel so I can check it whenever I feel like.

I stand by my previous statements that wicd is faster and more consistent, but it seems to have a problem after reboot.  Immediately after install everything's great, and after the first reboot it sill works fine, but after the second reboot, encryption seems to fail.

For some reason, when I'm running my network with any encryption, 40-bit WEP, 128-bit WEP, WPA, or WPA2, wicd fails to get further than "bringing down the interface" for my connection.  It no only doesn't auto-connect as it's told to, but won't connect even when manually told to do so.  

wicd did show the correct information for the network after each click of the refresh button as I changed the settings on my network to try different things, and did save the Passphrases or Hex codes for the encryption correctly, but it won't connect.

I checked my /etc/network/interfaces file and the only lines were ```
auto lo
iface lo inet loopback
``` as indicated at [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php").  I also deleted all my keys for my network from my keyring.  It connects correctly to unencrypted networks, ie. my neighbor's, but refuses to get any further than to bring down the interface when I tell it to connect.

On a side note, clicking the connect button associated with the wireless network you want to connect to occasionally causes it to try to connect to a completely different network on your list of available networks.

Also, it seems the intrepid version of the wicd repository is available and working, but may require a reboot for Synaptics to pick it up.  It doesn't give you the absolute latest stable version, but does give you the latest version released for general use.

SOLUTION:  I noticed someone else was having a similar problem in a different post, and got everything working by switching from network-manager to wicd, then back again.  The same worked for me.  Strangely enough, the only change made while trying to get wicd working was to delete all my previous keys from my keyring (System->Administration->Keyring Manager) for my wireless network.

---

