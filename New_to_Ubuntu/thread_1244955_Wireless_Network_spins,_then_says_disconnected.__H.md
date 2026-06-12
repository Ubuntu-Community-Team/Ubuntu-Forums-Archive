---
title: "Wireless Network spins, then says disconnected.  Help please..."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by ankillito on 2009-08-20
Hello,

I'm running Jaunty on a Dell XPS M1530, and I read the tests saying everything worked great for it.  The first time I ran ubuntu on it, I successfully connected to my home wireless network.  The next few times, it would intermittently disconnect.  Now, I can't connect at all. Because it worked before, I don't see how it could be driver problems, which is what most of the posts I've seen have been talking about.

When connecting to a network, it spins for a long time, and then gives the message Wireless Network - Disconnected.  After the first few days of it working great, it has done this consistently.

I tried reading through this:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
and ran lshw and saw
*-pci:2
  description: PCI bridge
  <stuff>
  configuration: driver=pciport-driver
 *-network
    description: Wireless interface
    <stuff>
    configuration: broadcast=yes driver=wl0 <that's WL#0> diverversion=5.10.91.9 module=wl multicast=yes

So then I ran lsmod, and wl does show up.  So I would think that this means my drivers are all set up right, especially because I was once able to connect.  However:

Ping'ing the router gives:
connect: Network is unreachable

iwconfig shows for eth1:
IEEE 802.11 Nickname:""
Access Point: Not-Associated
Link Quality: 5 Signal level: 218 Noise level: 165
<and all 0s for invalid counts>

I'm not really sure what I should be looking for.  I would like to start using Ubuntu for most of my stuff, but I can't until I get this sorted out.  Any help would be greatly appreciated, thanks!

---

### Post by swoody on 2009-08-20
Hi ankillito, and welcome to the forums ):P

This sounds like it may be an issue with your router. I know with my wireless router, the farther I get away from it, the less stable it becomes. Have you tried verifying that everything's working as it should with your router? Can you connect to it with other wireless devices? Have you tried moving closer to the router? Do you find signal strength lacking where you're trying to use your router? Also, try changing your wireless channel to a different one - you may be getting interfereance on your current channel. It may sound strange, but everytime I would use my cordless phone, it would interfere with my wireless signal, and disconnect all wireless devices. This should be pretty easy to test out from your router setup interface.

Also, just for your informaion, the reason your ping wouldn't go through is because you need to have some kind of network connection to be able to ping other devices - LAN for other computers in your home, WAN (internet) for servers/other computers.

---

### Post by mapes12 on 2009-08-20
Hi ankillito

When you installed Ubu did you also install an application called "ndiswrapper" to get your wifi up and running? I've experienced the same problem when using ndidwrapper i.e. at first no problems then after a few days the wifi can't connect.

If your wifi adapter is built into your machine then in Terminal ```
lspci
``` and post the output back here.

Could also be worth rebooting your router as well.

---

### Post by Daz_S on 2009-08-21
I have the same problem with this.  I am using a pci card (according to lspci it's a RALINK RT2561/RT61).  It worked fine until I rebooted my wireless router to factory settings when I moved from NZ to Aus.

Now my Windows laptops can connect to the router but the ubuntu box can't.  It just comes up, the icon spins, then says I'm disconnected.

I am using the wireless router as a router only, not a modem (it gets its feed from the new modem they sent me).  Incidentally I can't get the wireless router to connect to the internet through the modem either, but that's another story.

---

### Post by ankillito on 2009-08-26
Sorry for the delay - my last post didn't get submitted.  I would like to blame Vista, but it had to have been operator error.

@Swoody - Other computers are connected to the same router, and I have brought my laptop right next to it.  I should have mentioned these things, but I think they mean I can rule out the router.  I tried changing the channel, but that didn't fix it.  (I went from channel 11 to 1)  Thanks for the suggestions though, and for correcting my ping misunderstanding!

@mapes12 - I am not running ndiswrapper.  I believe the relevant line from lspci is:
0b:00.0 Network controller: Broadcom Corporation BCM4310 802.11b/g (rev 01)

I tried googling that, but none of the results I saw helped.  Unfortunately, I lost the record of exactly what I tried because my first reply didn't post.

I wasn't using ndiswrapper because of this page, which  suggested my laptop shouldn't need anything:
[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1530](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1530)

I'm going to continue to google around, but I would appreciate any suggestions.  Thanks your your pointers so far!

---

### Post by stalkier on 2009-08-26
Sorry if I missed this in a previous post but do you have a password (WAP/WEP/ETC) on the connection?? I know I had this issue on mine. I was inserting the old password and was like wtf! Then I felt like an idiot when I realized what I was doing. Just a thought.

---

### Post by ankillito on 2009-08-26
yeah, there is WEP.  I'm sure I'm using the right one though.  I double checked it by using the key on my iPod touch, and triple checking what I typed in.  Not only that, but the WEP key didn't change since the first time I turned on Ubuntu.  I entered the key back then, and it connected fine.  Using the same key, it later stopped working.  I retyped the key that I triple checked, and is still isn't working.  Meh...

---

### Post by ankillito on 2009-08-27
This guy has the same computer, and was able to make the wifi work simply from an apt-get update and an apt-get upgrade.
[URL="http://symbiotix.net/articles/dell-xps-m1530-and-ubuntu-first-impressions"]
http://symbiotix.net/articles/dell-xps-m1530-and-ubuntu-first-impressions[/URL]

I'm beginning to think I should just reinstall.  I don't have anything on here yet to loose...

---

### Post by Hygaphunkik on 2009-08-27
This might sound wierd but I had a similar looking problem when connecting to another network which used a key.
Having checked that everything was typed in correctly by clicking the show key box I would try and connect. The icon would spin for a while, as you say and then I would get the disconnected message. When I went to re-enter the password I saw that it had been filled in with gibberish. This happened on more than one occasion. In the end I deleted the connection profile and started again.

Don't know if that is of any use at all, but I thought I would let you know.

---

### Post by swoody on 2009-08-27
I don't think you mentioned it, but is your ESSID hidden, or does your router broadcast it? I have read where some people were having problems with the wl0 driver in Jaunty when their ESSID's were set to be hidden. Even if your's isnt' hidden, you may want to give this thread a read, and see if you can manage to get that patch to work for your issues. I'm not sure exactly what the patch fixes, but if it works for your problem, then great :)

[http://ubuntuforums.org/showthread.php?t=1187656](http://ubuntuforums.org/showthread.php?t=1187656)

On the subject of drivers - in your "Hardware Drivers" window, what wireless drivers does it list? Is there only STA?

---

### Post by ankillito on 2009-08-27
@Hygaphunkik - that is odd indeed.  Not happening in my case though...

@swoody - reading through article now, but yes, apart from my graphics driver, the only one listed is Broadcom STA wireless driver.  Is this not as it should be?

EDIT: ESSID - Is the router hiding it?  No.  Though I think I ran some command sometime where my card might be connecting as is the ESSID="".  Not sure what I was looking at though.  I don't know the general infrastructure of the wireless card, drivers, and pci bridges.  Great chance to learn though!

EDIT: I was thinking back to how my wifi worked so well in the beginning, so I decided to delete any new files and try again.  I right clicked on the spinner, edit connections, over to wireless tab, selected the connection, and hit delete.  Naturally, it prompted me for the password.  I obliged.  It spun, and then it came back, asking for the password again.  Am I using the wrong credentials?  It worked on other devices...

---

### Post by swoody on 2009-08-28
No, that's perfectly fine, I was just curious if it showed anything else. Have you tried disabling the WEP encryption temporarily, and connecting without it? This may be able to help us narrow down the problem a bit more.

---

### Post by ankillito on 2009-08-29
I was avoiding doing that because my cousin, who's graciously letting me spend the summer at his house, has other computers connected to the wireless.  I'll try and find a convenient time to reset the router.

This is my first post from Jaunty!  I'm successfully connected to wifi, but at a different house with a different network.  This network is using something other then WEP, I think.  I'll look into more when I'm not visiting my parents.  Thanks for all your help, and I'll be sure to post what I find.

---

### Post by izziere on 2009-08-29
Wifi and Ubuntu seem to be mortal enemies.  One thing that affects both Windows and Ubuntu is the router maybe setting WEP encryption to Shared rather than Open or vice versa.  Getting the key right is only the first step.

I really suggest you go back to earlier suggestion which is to temporarily stop using WEP encryption (hardly worth it anyway given cracking tools available) and try it unsecured.  That will either prove or disprove the theory about it being encryption-related.

If it works In /etc/network/interfaces or your network manager programme you can then change the wep key entry by maybe adding restricted in front of the key (eg "wireless-key restricted xxxxx...") if your router settings say it is shared key authentication.

Also check the router settings for DHCP server, etc.  Does it work on an ethernet connection?

---

### Post by swoody on 2009-08-29
No, no, no. I'm not suggesting running without encryption permanently. That was only to check to see if there was an issue with it. I just meant turning off the encryption, then attempting to connect, and then re-enabling the encryption. That's all. It's very dangerous to run your wireless without any sort of encryption, and I would never recommended doing it. Not everyone out there has the ability or knowhow to crack even a WEP network, but just about everyone knows how to connect to a wireless signal that's unguarded - hence you'd be putting yourself at a much greater risk.

Ankillito - Changing encryptions should be a simple matter of changing the option in your router control program. There shouldn't be a reason to have to reset it, and the time the network would be running encrypted would be very minimal - just a minute or two at most to check if you are able to connect. When you do this, please keep up updated on your results :)

---

