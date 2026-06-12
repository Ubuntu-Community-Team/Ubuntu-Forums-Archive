---
title: "[SOLVED] Removed network-manager... now can't connect..."
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by shakma on 2007-06-19
I know, that may be a perfectly logical result to what I did, but here's the story:

I was trying to install wicd for ease of wireless WPA use.  I had done this once before, and I swear that that's how I did it... However, as soon as I removed network-manager this time, I lost all internet connectivity.  I did install the wicd package (v1.2.7), but I still can't connect.  BTW, at this point, I am only trying to connect WIRED.  But still, no love :(   Fortunately, I have two machines to work from, but I need to get that one back up and running by morning to take it back to work. 

1) Did I do something wrong?
2) Can I re-install network-manager (and network-manager-gnome and fiesty-desktop(?)) from the CD?
3) Don't you HAVE to uninstall network-manager to get wicd to work?
4) Is there a better way to get WPA working (<-- LAF!  I have searched the forums extensively on this issue, and I've tried a little bit of everything.  I know it's a whole seperate topic.  I don't expect answers here on this one.)

Thanks in advance.  Peace.
shakma

Long live the ubuntuforums!

---

### Post by ugm6hr on 2007-06-19
> **shakma said:**
> 1) Did I do something wrong?
2) Can I re-install network-manager (and network-manager-gnome and fiesty-desktop(?)) from the CD?
3) Don't you HAVE to uninstall network-manager to get wicd to work?
4) Is there a better way to get WPA working (<-- LAF!  I have searched the forums extensively on this issue, and I've tried a little bit of everything.  I know it's a whole seperate topic.  I don't expect answers here on this one.)

1) Don't think so. You should be able to get wired working again if you turn off the roaming mode in the basic Network settings, and then restart with the cable plugged in (hopefully).  To get Wicd to work - try a different WPA supplicant driver or network interface than the default settings (e.g. *wext* instead of *madwifi*, *ath0* instead of *wlan0* - ifconfig/iwconfig will tell you your interface, and googling your wifi chipset with wpa supplicant will tell you your supplicant driver - or trial and error)
2) Network-manager will probably still be in your /var/cache/apt/archives, so you should be able to re-install without a CD or internet (just try Synaptic/apt-get - without reloading package information).
3) Yes
4) Maybe? I would actually recommend Wicd 1.2.9 (I found 1.2.7 unstable on my Feisty installation!).  I have found Wicd to be the best way to get my Atheros5005G (and another PCMCIA Realtek card) to work with WPA **with roaming**.  Only downside is that you can't choose to disconnect from a network (you can only connect to a different network) - and it seems to mess up the connection when I suspend.

---

### Post by shakma on 2007-06-20
Thanks, ugm6hr!  I'll get on the other machine and try these solutions.  I also have Wicd 1.2.9, but was hesitant to try a non "stable" version... worried it would cause more trouble than it fixed. :)

I'll post an update when I have one.

Peace.
shakma

---

### Post by shakma on 2007-06-20
Update number 1: 
I'm back on! (wired)  Funny thing - turns out there was a DSL service outtage in my area at just about the _EXACT MOMENT_ I was removing network-manager and installing Wicd!!!  When I rebooted then and got nothing, it was probably just a coincidence!:roll:

So, several hours later it's all back on and I can connect fine from this machine (again, wired).

I actually don't have wireless here at home, but I'll be taking this machine back to work within two days, and I'll test it out there.  In the meantime, I did upgrade to Wicd 1.2.9 (thanks for the tip).  I shouldn't have to disconnect from the network ever... the whole reason I got onto this twisted path was that I took on the task of securing our previously unsecured wireless network at work (which is a school, btw).  I wanted to use WPA, and of course the Windoze laptops had no problems, but this linux box (which sits all of 6 feet from the wireless router - just not practical to run a wire right across the middle of the walkway!) gave me unending headaches when trying to use WPA with network-manager.  

Thanks again, and I'll post the second and (hopefully) final update later this week.

Peace.
shakma

---

### Post by walkerk on 2007-06-20
If you're having problems with Network Manager use Wifi-Radar w/ WPA.. check out my thread.. It'll work with any laptop w/ a working driver.. not just broadcom 1390..

[http://ubuntuforums.org/showthread.php?t=478612](http://ubuntuforums.org/showthread.php?t=478612)

I was having similar problems with net-manager so I removed it.

---

### Post by shakma on 2007-06-21
Update #2:
No love from Wicd. :(  I get all the way up to the "Obtaining IP address" stage, then nothing 'til it decides to give up.  I've tried the "wext" and "madwifi" supplicants.  PSK is definitely correct.  3 Windoze laptops all connect fine everytime (right now, in fact...)  My wireless card, btw, is a D-Link DWL-G510 (rev. B1).  It is an Atheros chipset... which I think means madwifi should work?

I tried "ndiswrapper" and it totally froze up...

All would be well if I could just get this thing connected!  Please help, anyone! ](*,)

Thanks in advance.  Peace.
shakma

---

### Post by walkerk on 2007-06-21
> **shakma said:**
> I know, that may be a perfectly logical result to what I did, but here's the story:

I was trying to install wicd for ease of wireless WPA use.  I had done this once before, and I swear that that's how I did it... However, as soon as I removed network-manager this time, I lost all internet connectivity.  I did install the wicd package (v1.2.7), but I still can't connect.  BTW, at this point, I am only trying to connect WIRED.  But still, no love :(   Fortunately, I have two machines to work from, but I need to get that one back up and running by morning to take it back to work. 

1) Did I do something wrong?
2) Can I re-install network-manager (and network-manager-gnome and fiesty-desktop(?)) from the CD?
3) Don't you HAVE to uninstall network-manager to get wicd to work?
4) Is there a better way to get WPA working (<-- LAF!  I have searched the forums extensively on this issue, and I've tried a little bit of everything.  I know it's a whole seperate topic.  I don't expect answers here on this one.)

Thanks in advance.  Peace.
shakma

Long live the ubuntuforums!

give netapplet a try

```
sudo apt-get install netapplet
```

you should be able to connect to a wired interface this way..

---

### Post by walkerk on 2007-06-21
> **shakma said:**
> Update #2:
No love from Wicd. :(  I get all the way up to the "Obtaining IP address" stage, then nothing 'til it decides to give up.  I've tried the "wext" and "madwifi" supplicants.  PSK is definitely correct.  3 Windoze laptops all connect fine everytime (right now, in fact...)  My wireless card, btw, is a D-Link DWL-G510 (rev. B1).  It is an Atheros chipset... which I think means madwifi should work?

I tried "ndiswrapper" and it totally froze up...

All would be well if I could just get this thing connected!  Please help, anyone! ](*,)

Thanks in advance.  Peace.
shakma

Did you try wifi-radar?

---

### Post by shakma on 2007-06-21
> **walkerk said:**
> Did you try wifi-radar?

Well, I just tried wifi-radar and I got the *exact* same result... :(

Still nothing past "Acquiring IP Address".  It sees the SSID and all.  I tried wext and madwifi supplicants.  Really the exact same situation as with Wicd... :confused:

Any other ideas?

Peace.
shakma

---

### Post by ugm6hr on 2007-06-21
Bizarre....  just to check - can you post the output from *lspci* just to be certain - but I think your card has the Atheros 5005G chipset.

So it should work with the Restricted Drivers enabled and Wicd (my laptop has built-in Atheros5005G).  My Wicd preferencs are ath0 / wext (although it would make more sense for it to be madwifi).

This also suggests it should work with Feisty:
[http://ubuntuforums.org/showthread.php?p=2629337](http://ubuntuforums.org/showthread.php?p=2629337)

You certain there's no issue with the 64-digit code?

---

### Post by tturrisi on 2007-06-21
you need to use wext with atheros now:
[http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice](http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice)

---

### Post by ugm6hr on 2007-06-22
> **tturrisi said:**
> you need to use wext with atheros now:
[http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice](http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice)
Found that out by trial and error!

---

### Post by walkerk on 2007-06-22
right. but he said wext did not work..

w/out wpa enabled are you able to pull a dhcp address from your router? lets try to crawl first.

---

### Post by ugm6hr on 2007-06-23
> **shakma said:**
> Update #2:
No love from Wicd. :(  I get all the way up to the "Obtaining IP address" stage, then nothing 'til it decides to give up.  I've tried the "wext" and "madwifi" supplicants.  PSK is definitely correct.  3 Windoze laptops all connect fine everytime (right now, in fact...)  My wireless card, btw, is a D-Link DWL-G510 (rev. B1).  It is an Atheros chipset... which I think means madwifi should work?
Just had a thought...

When you click on the arrow beside your SSID in Wicd Manager - and then again on the arrow beside Advanced Settings - what is entered in all the boxes?

If your router has DHCP (which the "obtaining IP..." suggests) - you should untick the boxes "Use static IPs" and "Use static DNS", then tick the "Use encryption" and select WPA1/2 and enter (or copy and paste) the 64-digit key into the box below.

I am currently on a WEP network - but have attached a screenshot of what I mean (with the arrowhead circled).

---

### Post by shakma on 2007-06-24
> **ugm6hr said:**
> Just had a thought...

If your router has DHCP (which the "obtaining IP..." suggests) - you should untick the boxes "Use static IPs" and "Use static DNS", then tick the "Use encryption" and select WPA1/2 and enter (or copy and paste) the 64-digit key into the box below.



Just had an observation...

You are referring to a 64-digit key.  Now, I am using WPA with a Pre-Shared Key (WPA-PSK).  It is my understanding that the router (and Wicd, presumably) convert a text-based "passkey" into some 64-bit (or whatever) algorythm so that I don't have to.  I can use a passkey like "shakmarox" and tell the router to only accept that passkey.  Then, only wireless clients who know that exact passkey can gain access to the wireless network.  Your mention of an actual 64-**digit** key only applies to those using WEP, right?

I won't be back at work to try anything else 'til Monday morning, but I really appreciate all of the ideas and suggestions.  In response to some of the other questions:

1) I was able to connect just fine before securing the network (with network-manager in fact!)

2) I have no info in the IP, DNS, etc boxes as I am using the router as a DHCP server.

*) I used to have a static IP on this machine... maybe I'll try that again Monday.

More updates when I have some.  Keep the good ideas coming!  Peace.
shakma

P.S.  My WPA-PSK is *not* "shakmarox" :D

---

### Post by ugm6hr on 2007-06-24
> **shakma said:**
>  Your mention of an actual 64-**digit** key only applies to those using WEP, right?
Errrmmm.  Yes - sorry to mislead.  I'm no security expert :oops:

WPA uses 8-63 digit passkeys, doesn't it?  I think the security increases with increasing passkey length.

So that can't be the problem...

The reason I thought of that possibility is that when I first installed Wicd and tried to click connect without completing the advanced settings, it tried to acquire IP indefintely (it didn't ask for password etc).

---

### Post by ugm6hr on 2007-07-08
If you're still trying with this - just wanted to say it's worth trying entering the passkey both with and without "" surrounding it (i.e. *"passkey"* and  *passkey*).

I have found that one of my infrequently used networks (Linksys WAG54G) insists on putting "" on either side of the passkey.

---

### Post by shakma on 2007-07-13
Greetings, all.  Here's the latest.

As of the newest "stable" Wicd (1.3.1), I am now able to connect w/WPA to my home network!!!

:guitar:

Now, I'll be taking this machine *back* to work on Monday morning to see if it will connect to that network.  

FYI: I did try *"passkey"* and *passkey*.  Without quotes ended up working this time.

I found a thread that mentioned turning the PSK into it's 64-letter hex version:
(Code: wpa_passphrase *ssid* *passkey*)

While this command does work, it wasn't the solution.  The regular, ascii PSK ended up working just fine.

Further (final?!) update on Monday...

Peace.
shakma

---

### Post by shakma on 2007-07-16
Hallelujah!  :KS

All's well in the wonderful world of wireless.  Much thanks to all in this thread (and the "How do I make WPA work?!?!" Community).  Much thanks to the people behind Wicd.

Wicd 1.3.1 seems to have been the majority of the solution.  I am now on the wireless network at work, protected by WPA(ascii-PSK).

I really didn't do anything much differently throughout this processes.  It works the way you'd think it should.  And with Wicd 1.3.1 _it works the way it *should*!_

Much love to the ubuntuforums.  This community never ceases it amaze me.  All those who continue to struggle - fight on!  ;-)

Peace.
shakma

P.S.  Anyone who needs help getting a wireless router to work *through* a primary router (basically as just a wireless access point), ask me.

---

### Post by shakma on 2007-07-31
Just a quickie... if anyone but me is still reading this...

After one glorious day, the wireless refused to connect ever again!  I was beside myself, to say the least.  I tried everything.  I removed Wicd and went back to network-manager... which worked for about 10 minutes.  After a couple of trial reboots, though, that stopped connecting.:confused:

The moral of the story is: I replaced the wireless router with a different one (originally a netgear, replaced with a slightly older linksys) and all of my problems were gone!  I don't know what happened with the netgear... maybe it got dropped one too many times... but all's well now.

That's all.:neutral:

Peace.
shakma

---

### Post by ugm6hr on 2007-07-31
Before you through the Netgear away....  

Very occasionally, changing the wifi broadcast frequency channel (I think 1,6 or 11 are recommended - thought this might just be made up!) can make a big difference in this scenario... 

Just a thought...

---

