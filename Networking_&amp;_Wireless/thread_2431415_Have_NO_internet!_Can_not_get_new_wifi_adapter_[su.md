---
title: "Have NO internet! Can not get new wifi adapter [supposedly Linux-friendly] to work"
date: 2019-11-16
forum: Networking &amp; Wireless
---

### Post by crazybear on 2019-11-16
I have installed an ASUS PCE-AC51. It uses a Realtek RTL8812AE chip. I found the newest linux driver for it and thought I built it correctly....but when I do an analysis on it [or more bluntly try to connect to the internet], I find I'm far, far from where I need to be. I'm NO expert in networking nor in building complex drivers [and this is complex!]. I see other threads somewhat related, but I do not find the answers I need on them. Would some kind person 'out there in Linux land' PLEASE help me through this. I need internet and am only contacting you now by using  Windows which I detest and never use - with good reason. My very mean landlord cut off my LAN internet cable, as we are in Court over many issues. There is a strong enough wifi signal coming through my window from somewhere else, but I can NOT get this wifi adapter to work. HELP! Please! Thanks in advance.

I will try to post the last diagnostic information I have, if it tells you anything....I only get a few hints that the computer knows what I know....it is not working [but WHY, I don't know - nor what I would have to do to make it work].



   
  [http://paste.ubuntu.com/p/4Nf7fzbgbd/](http://paste.ubuntu.com/p/4Nf7fzbgbd/)      my diagnostic information!!!!

---

### Post by jetsam on 2019-11-16
Is it a viable option to buy a usb wifi dongle just to add some flexibility?  There's a sticky thread at the top of the forum with buying advice.  I think I'd put one on order (they're about $15.00) if I were in your shoes just to give myself options.  Unfortunately, there's no guarantees that things will go swimmingly even if you do throw new hardware at your hardware problem.

I think that's all I can add right now.  There are champs at troubleshooting these interface issues in the forum, but I'm not one of them...

Cheers,
jetsam

---

### Post by crazybear on 2019-11-16
> **jetsam said:**
> Is it a viable option to buy a usb wifi dongle just to add some flexibility?  There's a sticky thread at the top of the forum with buying advice.  I think I'd put one on order (they're about $15.00) if I were in your shoes just to give myself options.  Unfortunately, there's no guarantees that things will go swimmingly even if you do throw new hardware at your hardware problem.

I think that's all I can add right now.  There are champs at troubleshooting these interface issues in the forum, but I'm not one of them...

Cheers,
jetsam

I'd be very hesitant to get another one. I have one from a phone provider, but its program ONLY works with Mac and Windoz...typical. I spent a LOT of money on this that is now in my machine, and I'm poor.....so hoping someone can help out and I don't have to keep buying things that don't work...I've already gone through three...each more expensive than the one before - each claiming more to be 'Linux-compatible'....and I'm sure it is if one is a genius at building drivers and networking complexities. Since I started to mess around with this, the desktop which once did get wifi with the provided windows drivers [on CD] NOW doesn't get any internet by wifi. The lousy USB dongle here in an East European country where all the providers are cheats [in more than one way], costs me a fortune for lousy and slow internet. No thanks. SOMEONE, please help!

---

### Post by chili555 on 2019-11-16
We see these interesting points in your diagnostics:

> ##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
[COLOR="#FF0000"]WirelessEnabled=false[/COLOR]
WWANEnabled=false
WimaxEnabled=trueAs well as:

> 0: phy0: Wireless LAN
	[COLOR="#FF0000"]Soft blocked: yes[/COLOR]
	Hard blocked: noAnd finally:

> ##### network managers ##################

Installed:

	NetworkManager
	WicdAs far as I know, given 109 years of experience in Linux wireless, Wicd does nothing whatever better than the default Network Manager. It is typically installed as a guess as to what might fix the as yet undiagnosed wireless issue. It almost never does.

I suggest that you remove it:

```
sudo apt -get purge wicd*
```Reboot.

Click the Network Manager icon and select 'Enable Wi-Fi`. Your wireless should now be working.

[IMG]https://i.stack.imgur.com/XmE1R.png[/IMG]

The correct driver appears to be installed and working properly.

---

### Post by crazybear on 2019-11-16
I did remove wicd*, but hope you know what you are suggesting. There was a message I didn't get fully that said ' X will no longer work until you reinstall wicd]. However, I still have NO internet! Also, I have NO IDEA how to 'Enable Wifi" and a command line command might be best. I have NO Network Manager symbol nor can I find it listed in programs.....thus, I do NOT know how to 'enable wifi'

---

### Post by uRock on 2019-11-16
Check out this thread. I haven't read it all the way through, but the user was having issues with the Realtek 8812 and got it working. [https://ubuntuforums.org/showthread.php?t=2431438](https://ubuntuforums.org/showthread.php?t=2431438)

---

### Post by jeremy31 on 2019-11-16
Try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo sed -i 's/WirelessEnabled=false/WirelessEnabled=true/' /var/lib/NetworkManager/NetworkManager.state
sudo rfkill unblock all
systemctl enable network-manager.service
systemctl start network-manager.service
```

---

### Post by crazybear on 2019-11-16
This is very frustrating.....and network structure is a nightmare and complex beyond what it should be!
Also, I have to turn off my computer; remove the Ubuntu disk; put in the Windows disk; start the computer and come here......
what did wicd do and was removing really a correct move?
I see MANY different suggestions that seem mutually exclusive on the internet and I'm very confused. 
I see a nmcli wifi on command and others and sometimes nmcli with r or -g after a space
I tried sudo ifconfig [device logical name] up and it says [I think] it is 'up', but I get no wifi and no packets go up nor down - zip.

Someone please help....

```

 :~$ iwconfig
  wlp4s0    IEEE 802.11  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
            Retry short limit:7   RTS thr=2347 B   Fragment thr:off
            Power Management:on
            
  wwx001e101f0000  no wireless extensions.
   
  eth0      no wireless extensions.
   
  virbr0-nic  no wireless extensions.
   
  eth1      no wireless extensions.
   
  virbr0    no wireless extensions.
   
  lo        no wireless extensions.
   
  $ sudo ifconfig wlp4s0 up
   
  SIOCSIFFLAGS: Operation not possible due to RF-kill
  $ nmcli r all on
  ~$ sudo ifconfig wlp4s0 up
  ~$ iwconfig
  wlp4s0    IEEE 802.11  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
            Retry short limit:7   RTS thr=2347 B   Fragment thr:off
            Power Management:on
            
  wwx001e101f0000  no wireless extensions.
   
  eth0      no wireless extensions.
   
  virbr0-nic  no wireless extensions.
   
  eth1      no wireless extensions.
   
  virbr0    no wireless extensions.
   
  lo        no wireless extensions.
   
  ~$ sudo lshw -C network; lsb_release -a; uname -a; sudo rfkill list; sudo iwlist scan | egrep 'chan|sid'
    *-network               
         description: Wireless interface
         product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:04:00.0
         logical name: wlp4s0
         version: 01
         serial: 04:d4:c4:13:c1:51
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-55-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
         resources: irq:40 ioport:ee00(size=256) memory:fbefc000-fbefffff
    *-network
         description: Ethernet interface
         product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:07:00.0
         logical name: eth1
         version: 03
         serial: 00:24:1d:ce:b6:64
         size: 10Mbit/s
         capacity: 1Gbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:16 ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
    *-network
         description: Ethernet interface
         product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:08:00.0
         logical name: eth0
         version: 03
         serial: 00:24:1d:ce:b6:66
         size: 10Mbit/s
         capacity: 1Gbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:17 ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
    *-network:0 DISABLED
         description: Ethernet interface
         physical id: 1
         logical name: wwx001e101f0000
         serial: 00:1e:10:1f:00:00
         capabilities: ethernet physical
         configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=no multicast=yes
    *-network:1 DISABLED
         description: Ethernet interface
         physical id: 2
         logical name: virbr0-nic
         serial: 52:54:00:2b:2f:a7
         size: 10Mbit/s
         capabilities: ethernet physical
         configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  LSB Version:   core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
  Distributor ID: Ubuntu
  Description:     Ubuntu 16.04.6 LTS
  Release:           16.04
  Codename:      xenial
  Linux 4.15.0-55-generic #60~16.04.2-Ubuntu SMP Thu Jul 4 09:03:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
  0: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  wwx001e101f0000  Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  virbr0-nic  Interface doesn't support scanning.
   
  eth1      Interface doesn't support scanning.
   
  virbr0    Interface doesn't support scanning.
   
  lo        Interface doesn't support scanning.

```

---

### Post by jetsam on 2019-11-16
Let folks here help...  Try to follow their instructions closely, and hopefully you'll get a good result.  The internet has contradictory advice about everything, not just troublesome wifi issues...

Reducing frustration in the thick of things is tough.  Breaks help, even long ones if need be.  The pacing of forum advice can frustrate efforts to help, so it's best to pick a few experienced posters and stick with them.  You have four experts at different aspects of networking in your thread, so have no fear ;)  We're usually pretty good at not jumping into a working kitchen and confusing the cooks.

---

### Post by chili555 on 2019-11-16
> network structure is a nightmare and complex beyond what it should be!

I disagree entirely. Ordinarily, if a driver is present, Network Manager shows a little pop-up that indicates that there are wireless networks available and invites you to connect. The fact that you see no NM icon is not an issue with networking in Ubuntu; it is a rare case where there is an issue with your specific installation.

> I have NO Network Manager symbol nor can I find it listed in programs..

Let's see if we can get it to appear; from the terminal:

```
nm-applet &
```

Any luck?

```
I get no wifi and no packets go up nor down - zip.

```
Network Manager isn't going to decide, without input from you, which of the perhaps dozens of networks to connect to, nor is it going to conjure up the WPA2 password.

If you now see the NM icon, click it and try to connect. If not, try:

```
nmcli device wifi rescan
nmcli device wifi list
nmcli device wifi connect SSID-Name password wireless-password
```

Did you connect?

After you connect, we shall try to solve the mystery of the missing NM icon.

---

### Post by crazybear on 2019-11-17
> **uRock said:**
> Check out this thread. I haven't read it all the way through, but the user was having issues with the Realtek 8812 and got it working. [https://ubuntuforums.org/showthread.php?t=2431438](https://ubuntuforums.org/showthread.php?t=2431438)

That thread has almost zero connection with my system or devices...different in almost all ways.

> **chili555 said:**
> I disagree entirely. Ordinarily, if a driver is present, Network Manager shows a little pop-up that indicates that there are wireless networks available and invites you to connect. The fact that you see no NM icon is not an issue with networking in Ubuntu; it is a rare case where there is an issue with your specific installation.


Let's see if we can get it to appear; from the terminal:

```
nm-applet &
```

Any luck?

```
I get no wifi and no packets go up nor down - zip.

```
Network Manager isn't going to decide, without input from you, which of the perhaps dozens of networks to connect to, nor is it going to conjure up the WPA2 password.

If you now see the NM icon, click it and try to connect. If not, try:

```
nmcli device wifi rescan
nmcli device wifi list
nmcli device wifi connect SSID-Name password wireless-password
```

Did you connect?

After you connect, we shall try to solve the mystery of the missing NM icon.

OK, good news and bad news.... I was able to see the list of available wifi signals and connect to one... the bad news is still no NM icon and the signal apparently is too weak [57dB] to do anything....I can't even get emails. :mad: I had had a HUGE dish antenna here, but now it is far away....wish I had it now.)

To the person who gave me the powersave command. I ran it and then realized you likely thought I had a laptop. I do NOT have a laptop - it is a HUGE desktop with a HUGE powersupply - so I hope I'm not throttling the wifi adapter. Is there a command to undo the powersave command you gave?

So, I guess in theory now I can connect, but the signal while not to my memory so weak as to work, is not 'working'....even though it is connecting.

Sigh.

I moved the computer as close to the window as possible in winter. Now I get 54-56 dB. As I remember from the distant past when I also had to use wifi, that should be sufficient if not spectacular; yet NO program gets any packets of information. Could something be interfering between the wifi adapter and the programs?! Anyway to find out? Maybe this is just an expensive and bad wifi adapter - but others who bought it for Linux said it worked for them.... I note that is also does NOT work in Windoz which which it came with drivers on CD..but I'm NOT going to even bother with that, just wanted to note that here. In Windoz I have the very expensive and very poor quality internet via a mobile providers USB dongle...but it ONLY works with Windoz and is priced at an insane price for service. I don't want to pay so much NOR use Windoz.

Found this on the internet: So it DOES seem something is blocking the incoming wifi signal from getting to my programs. ANY IDEAS what it is and how to get rid of it?!?!?
[TABLE]
[TR]
[TH]Signal Strength[/TH]
[TH]Expected Quality[/TH]
[TH]Required For[/TH]
[/TR]
[TR]
[TD]-30 dBm[/TD]
[TD]Maximum signal strength, you are probably standing right next to the access point.[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]-50 dBm
[/TD]
[TD]Anything down to this level can be considered excellent signal strength.


[/TD]
[/TR]
[/TABLE]
-60 dBm Good, reliable signal strength.

---

### Post by jetsam on 2019-11-17
> In Windoz I have the very expensive and very poor quality internet via a mobile providers USB dongle...but it ONLY works with Windoz and is priced at an insane price for service. I don't want to pay so much NOR use Windoz.

...Are you on Android and do you have a reasonable data cap?  We might be able to work on an alternative way for you to tether to your mobile phone.  If so, see this thread at the end:
[Re: Options for maintaining connectivity when the power is cut? ]("https://ubuntuforums.org/showthread.php?t=2430835&p=13906016#post13906016")

Back to the original question.  The electronics internal to your adapter have an impact on the signal strength and how well that signal is interpreted into bits.  It's difficult to quantify, involves signal to noise ratios and noise floors and a lot of engineering we have no means of knowing specifically, so it isn't very relevant.  You should be able to improve the situation practically by getting a better antenna, moving to a better reception spot, and (possibly) reducing high frequency noise nearby.  One way to do this is to completely unplug any switching power supplies that you don't need: turn off all the led light bulbs in the area. Also, all the "wall wart" power supplies you aren't using are producing high frequencies.  They're supposed to keep this stuff to a minimum, but it can't hurt to pull the plug just as a test.  Basically any modern AC to DC converter could very well be interfering at least somewhat with your weak signal.

Cheers,
jetsam

Edited to add:  [Line of sight]("http://www.fab-corp.com/pages.php?pageid=2") is relevant at wifi frequencies as well.  It may be worth thinking about if you know at least vaguely where the signal is coming from.

---

### Post by crazybear on 2019-11-17
> **jetsam said:**
> ...Are you on Android and do you have a reasonable data cap?  We might be able to work on an alternative way for you to tether to your mobile phone.  If so, see this thread at the end:
[Re: Options for maintaining connectivity when the power is cut? ]("https://ubuntuforums.org/showthread.php?t=2430835&p=13906016#post13906016")

Back to the original question.  The electronics internal to your adapter have an impact on the signal strength and how well that signal is interpreted into bits.  It's difficult to quantify, involves signal to noise ratios and noise floors and a lot of engineering we have no means of knowing specifically, so it isn't very relevant.  You should be able to improve the situation practically by getting a better antenna, moving to a better reception spot, and (possibly) reducing high frequency noise nearby.  One way to do this is to completely unplug any switching power supplies that you don't need: turn off all the led light bulbs in the area. Also, all the "wall wart" power supplies you aren't using are producing high frequencies.  They're supposed to keep this stuff to a minimum, but it can't hurt to pull the plug just as a test.  Basically any modern AC to DC converter could very well be interfering at least somewhat with your weak signal. 
Cheers,
jetsam

Yes, there is one AC/DC converter about two meters away and the usual cables into the back of a desktop computer. Strangely, my tablet which is only a few cm closer to the source of the wifi signal than the two antennas on this ASUS internal gets good reception from the same wifi source...the ASUS doesn't get anything usable, but a rating of -54 to -56 dB. I don't get it. No, I can not use my tablet and don't have a smartphone for what you were thinking of....sorry. For security reasons I don't have a sim in the tablet and it is only getting this wifi signal. I have special security needs I can't discuss.

---

### Post by jetsam on 2019-11-17
> I don't get it.

I don't think anybody does, to be honest.  I have never adjusted an antenna without finding the whole thing mysterious and ending up with the antenna at some strange angle not at all where it ought to be by rights.  I think even the Ham radio guys, who spend years on antennas, essentially budget and design them, then put them as high as they can get them, and finally, futz around with position and orientation, swearing at them all the while...  just like the rest of us ;)

---

### Post by crazybear on 2019-11-17
There were two AC/DC converters, but unplugged there was NO difference - so that is not it. Unplugging various wires [all necessary] in the back panel of the computer also had no effect. I have tried to move around the antennas, but it only very slightly changes the dB level, but NOT the seemingly total lack of connectivity to ANY program that uses internet. I remember many years ago using a wifi signal of this strength without problem.
I suspect, but am NO expert on this, that something is blocking the signal to ALL programs. What could it be? Again, the tablet is on foot closer to the window outside of which some meters away is the AP - and it gets reasonable wifi reception..I can watch streaming video, etc. Any ideas appreciated. I have lightning fast cable internet, but my landlords cut it [we are in Court against each other on 'issues']....and I need internet for 'normal things' and to find a new place to live and am unable to do either much at all...relying on the tablet for news and a little [very little] of the above.....

---

### Post by jetsam on 2019-11-17
> I suspect, but am NO expert on this, that something is blocking the signal to ALL programs.

...that would be something else entirely, a configuration problem or some such...   Chili is probably your best bet if such is the case.

Yeah...  the AC/DC adapter stuff is a bit of  a stretch.  Most computer power supplies are pretty well shielded, and anything certified shouldn't be releasing so much radio energy that it makes much difference.  Stuff to look out for would be things like dodgy usb wall chargers from anonymous manufacturers, possibly cheap led light bulbs which contain a dc adapter hidden in their bases.  They may not be making any effort to shield the world from their noise, because it would cost money to do so.

I guess I might suggest using your feet at this point.  If you could find a temporary office somewhere, even if it's in a friend's closet or the basement of a university library or in your car parked outside a local cafe...  It would be nice to see whether your set-up is working or not in the presence of a stronger signal.

---

### Post by praseodym on 2019-11-17
dmesg output shows a firewall blocking. Lets try

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by crazybear on 2019-11-17
> **jetsam said:**
> ...that would be something else entirely, a configuration problem or some such...   Chili is probably your best bet if such is the case.

Yeah...  the AC/DC adapter stuff is a bit of  a stretch.  Most computer power supplies are pretty well shielded, and anything certified shouldn't be releasing so much radio energy that it makes much difference.  Stuff to look out for would be things like dodgy usb wall chargers from anonymous manufacturers, possibly cheap led light bulbs which contain a dc adapter hidden in their bases.  They may not be making any effort to shield the world from their noise, because it would cost money to do so.

I guess I might suggest using your feet at this point.  If you could find a temporary office somewhere, even if it's in a friend's closet or the basement of a university library or in your car parked outside a local cafe...  It would be nice to see whether your set-up is working or not in the presence of a stronger signal.

What is Chili? [and please remember without internet, I can not download anything not already in my system]. This DESKTOP computer is NOT going to be moved anywhere - and if I could [and I can't], there would be no point. I have one place [this window] that has a wifi signal I can use. I am home [also my office] and there is no other place, nor is this giant possible to move. It aint' gonna happen..... I think we can discount any interference; it would be effecting the tablet getting its signal and it is not. The tablet and the back of the computer are now 30 cm away from one another. One works on the wifi signal just fine, the other doesn't work on the wifi signal at all. I'm guessing that the ASUS [which cost about $150] and its two large 14cm antenna have better wifi 'gathering' ability than my Samsung tablet.

---

### Post by jetsam on 2019-11-17
Did you try the firewall removal commands posted by praseodym?  If you have your firewall configured to block all your traffic, it would give the symptoms you've described.  

All the other suggestions I've made are just suggestions.  Sometimes there's an easier way to work around a problem than directly assaulting it.  Not always, and it's sometimes better to find the root cause of an issue anyway.  Anyways, we're making progress...  slowly.

I think you should try the firewall commands and report back.

By Chili I meant Chili555, the forum user who helped a few posts above.  He's one of the champs at troubleshooting network interfaces I mentioned earlier.

---

### Post by crazybear on 2019-11-17
> **praseodym said:**
> dmesg output shows a firewall blocking. Lets try

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

Just tried that.....no improvement...but what did I do? I wish such things would be explained, so I can reverse things if needed.
Only a trickle of packets coming in our out - as before - not enough to get email or run any webbrowser. Even skype which needs very little doesn't work.

Ideas?

This computer worked for seven years just fine on a high-speed LAN line, until my horrible landlords I'm in Court with cut the line....leaving me struggling the past three months to get internet!....this is a long long struggle and not there yet. In fact with windoz I can only barely get it at very high cost here; with Ubuntu can't get it at all - and in the past I never touched Windoz, this is an OLD disk I had around from before I discovered Linux about 15 years ago.

```

 $ sudo lshw -C network; lsb_release -a; uname -a; sudo rfkill list; sudo iwlist scan | egrep 'chan|sid'
    *-network               
         description: Wireless interface
         product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:04:00.0
         logical name: wlp4s0
         version: 01
         serial: 04:d4:c4:13:c1:51
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-55-generic firmware=N/A ip=192.168.1.29 latency=0 link=yes multicast=yes wireless=IEEE 802.11
         resources: irq:40 ioport:ee00(size=256) memory:fbefc000-fbefffff
    *-network
         description: Ethernet interface
         product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:07:00.0
         logical name: eth1
         version: 03
         serial: 00:24:1d:ce:b6:64
         size: 10Mbit/s
         capacity: 1Gbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:16 ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
    *-network
         description: Ethernet interface
         product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:08:00.0
         logical name: eth0
         version: 03
         serial: 00:24:1d:ce:b6:66
         size: 10Mbit/s
         capacity: 1Gbit/s
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
         resources: irq:17 ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
    *-network DISABLED
         description: Ethernet interface
         physical id: 1
         logical name: virbr0-nic
         serial: 52:54:00:2b:2f:a7
         size: 10Mbit/s
         capabilities: ethernet physical
         configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  LSB Version:   core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
  Distributor ID: Ubuntu
  Description:     Ubuntu 16.04.6 LTS
  Release:           16.04
  Codename:      xenial
  Linux  4.15.0-55-generic #60~16.04.2-Ubuntu SMP Thu Jul 4 09:03:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
  0: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  eth1      Interface doesn't support scanning.
   
  virbr0-nic  Interface doesn't support scanning.
   
  lo        Interface doesn't support scanning.
   
  virbr0    Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
  

```

---

### Post by jetsam on 2019-11-17
Everything coming out of your wifi adapter is bits-- streams of 0's and 1's, so there's just no possibility of signal loss being an issue between the wifi adapter and any desktop application.  Probably what's happening is some high percentage of the traffic you're receiving is being detected as having errors, forcing the adapter to ask for the packet to be re-sent.  I *think* the major problem is, basically, bad reception.  

Looking into antenna options is probably worthwhile.  Wasn't there a 'potato chip can antenna' for wifi that worked well?  I think that may have gone away a few generations ago; antennas have been getting smaller as the frequencies have risen.

The first apt command gets rid of some default Ubuntu firewall stuff.  The iptables commands more or less would have listed any filters that were set up as well as deleted any firewall rules blocking traffic.  Basically, we want to just get rid of any and all firewalls until we've gotten the network working and your machine receiving traffic.  You can google "man iptables" or type "man iptables" into a terminal to get the documentation that allows you to decipher these things.

---

### Post by jeremy31 on 2019-11-17
Can we see new wireless script results?
```
./wireless-info
```

---

### Post by chili555 on 2019-11-17
The intent of the powersave change was not, literally, to save power; it is to keep Network Manager from putting your wireless to sleep and then not always being able to properly awaken it. Many wireless devices come back to life properly upon resume from power saving; many others do not. 

Speaking of antennas, are you quite certain that both antennae are firmly attached?

[IMG]https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fimages-na.ssl-images-amazon.com%2Fimages%2FI%2F51v-R2AOclL._AC_SS350_.jpg&f=1&nofb=1[/IMG]

---

### Post by praseodym on 2019-11-17
Haven't read through anything, but your LAN-NIC is Realtek 8168. Download this file and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.047.02-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.047.02-1_all.deb)

Installation

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Wired connection should work now. Try updating the wlan drivers via
```

sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot

---

### Post by crazybear on 2019-11-18
> **praseodym said:**
> Haven't read through anything, but your LAN-NIC is Realtek 8168. Download this file and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.047.02-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.047.02-1_all.deb)

Installation

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Wired connection should work now. Try updating the wlan drivers via
```

sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot

Kindly remember that BECAUSE I have NO internet I can NOT download ANYTHING in Ubuntu! Period....unless you know a way to download it in Windoz and transfer it. I do not. However, there was a LOT of ancillary data that came with the Linux driver [unbuilt] on the original CD and there were a few items to be blacklisted. I think I did so in the place they suggested. There is SO much other material [and I am SURE not all of it is to be used], it is hard to know which of it needs to be used - if any. I struggled for WEEKS just to properly build the driver - as the one on the CD was not the latest and was very difficult to build. What all the other items are for, or if needed, I do not know. I don't think this website would even allow me to upload it all.

I ran 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf

, but noticed nothing different. I'm back here 'windoz', but the lower commands surely need an internet connection and I tried and still have none in Ubuntu.

---

### Post by jetsam on 2019-11-18
There must be dozens of ways to make this easier on yourself if you'd be willing to accept local help and/or move the silly computer for a few hours.  No sympathetic user's group or gaming buddy or library IT department or even just an ethernet port in the lobby of a local hotel?  

No wireless repeater you could pick up to boost the horrid signal?  The right one would provide an ethernet jack for you.  You'll probably be wanting to do this anyway no matter how good you get the adapter running...

No temporary hotspot you could order from your cell phone provider while you work on a better budget option?

Well, if none of the above...  it seems you need to download things into Windows or your tablet and transfer them to Linux and compile them from there...

---

### Post by crazybear on 2019-11-18
> **jetsam said:**
> There must be dozens of ways to make this easier on yourself if you'd be willing to accept local help and/or move the silly computer for a few hours.  No sympathetic user's group or gaming buddy or library IT department or even just an ethernet port in the lobby of a local hotel?  

No wireless repeater you could pick up to boost the horrid signal?  The right one would provide an ethernet jack for you.  You'll probably be wanting to do this anyway no matter how good you get the adapter running...

No temporary hotspot you could order from your cell phone provider while you work on a better budget option?

Well, if none of the above...  it seems you need to download things into Windows or your tablet and transfer them to Linux and compile them from there...

Trust me, what you suggest is dangerous for me and impossible - both. I do not have a cellphone provider either. For security I have no cellphone. I am a whistleblower who is hunted. More I will not say.  I am NOT taking my computer OUT. Sorry, rant over...

---

### Post by jetsam on 2019-11-18
Ok...

There's a whole class of devices called wireless range extenders.  Like I said above, it seems like something you will want even if you get your wireless adapter working well.  But, the good ones come with ethernet ports, so you could bypass the problem either temporarily or permanently.

Here's a link to a $30.00 one.  It's not that I think you should buy that one (you need a EU source surely, anyway), but just to clarify what sort of thing we're talking about.  This one only has one ethernet port, but that's enough I think for your situation:
[TP-Link | AC750 WiFi Range Extender]("https://www.amazon.com/TP-Link-AC750-WiFi-Range-Extender/dp/B07N1WW638/")

---

### Post by crazybear on 2019-11-18
> **jetsam said:**
> Ok...

There's a whole class of devices called wireless range extenders.  Like I said above, it seems like something you will want even if you get your wireless adapter working well.  But, the good ones come with ethernet ports, so you could bypass the problem either temporarily or permanently.

Here's a link to a $30.00 one.  It's not that I think you should buy that one (you need a EU source surely, anyway), but just to clarify what sort of thing we're talking about.  This one only has one ethernet port, but that's enough I think for your situation:
[TP-Link | AC750 WiFi Range Extender]("https://www.amazon.com/TP-Link-AC750-WiFi-Range-Extender/dp/B07N1WW638/")

If I understand, it would only allow me to be further from the window. Being close to the window is NO problem. The two antenna on the back of the computer are about 40cm from the window. As I said, my tablet [without any sim] is getting the exact same wifi signal well enough to stream video. The computer is getting zip. This is what I don't 'get'. While I can afford a little money, money it not something I am looking to spend at this time. I have none coming in and unusual and many demands for it going out. I must get a new place and get out of here - fast; yet without good reliable internet on the desktop can not even search for a new place to be [in a city with virtually a zero vacancy rate is not easy!]. What would the range extender do for me - I fail to see. I still think it is not the less than strong signal, as evidenced by the tablet. Sadly, I can't effectively seek new places to live nor do any word processing on the tablet and both are essential now. I also need access to data and programs on the HDDs....more so on Ubuntu which was current. The Windoz computer I last used over ten years ago.

---

### Post by jetsam on 2019-11-18
You would be able to connect a short ethernet cable between your computer and the Wireless Range Extender, which has an ethernet port.  After configuring the range extender, which I believe can be done either with your computer or a mobile phone or your tablet, you would immediately have access to the internet on your desktop computer. 

...At that point, you could decide to expend further effort getting the sub-standard wifi adapter on your computer to function under Linux.  If you did not, you would still have a 100 Mbps wired connection to the network.  You could use this indefinitely until you move to a better situation.

The choices are yours...  And all of this is provisional on things going well, as our support suggestions always are.

Cheers,
jetsam

---

### Post by crazybear on 2019-11-18
> **jeremy31 said:**
> Can we see new wireless script results?
```
./wireless-info
```

I forgot to mention [it gets confusing going back and forth between HDDs] that this in terminal gave NO response. Terminal only said something to the effect that 'this is a folder' and said nothing more. Is that the correct command?

---

### Post by crazybear on 2019-11-18
> **jetsam said:**
> You would be able to connect a short ethernet cable between your computer and the Wireless Range Extender, which has an ethernet port.  After configuring the range extender, which I believe can be done either with your computer or a mobile phone or your tablet, you would immediately have access to the internet on your desktop computer. 

...At that point, you could decide to expend further effort getting the sub-standard wifi adapter on your computer to function under Linux.  If you did not, you would still have a 100 Mbps wired connection to the network.  You could use this indefinitely until you move to a better situation.

The choices are yours...  And all of this is provisional on things going well, as our support suggestions always are.

Cheers,
jetsam

Jetsam, I appreciate the help and suggestions, but if I understand this device gets plugged into an electrical outlet. How it then 'extends' the wireless range I'm not sure...perhaps through the electrical wiring or ? But, the nearest electrical outlet [220 volt 50 cycle here] is NOT close to the window at all - and thus far away from any wifi signal. This building is 650 years old, is made of stone and the walls are 1 m [1 yd] thick - and I'm sure NO wifi signal passes thought the walls at all. Only through the window. Am I missing something? It seems to not be something for me, but something that might work in the houses built in the USA, maybe. I'm overstretched financially and only will spend on something I'm fairly sure will work now and help me in the future as well. I do get (some poor) internet on the Windoz disk, but it costs a small fortune to a mobile cheat company - the other 3 mobile providers being even worse. My tablet gets free wifi and is only 30cm closer to the window than the computer. I could in fact put the computer on the window sill [with difficulty and two hours work], but I think the signal is sufficiently strong and something else is the problem. Maybe ASUS just makes crud wifi adapters and I'm wasting my time.....there are many, many threads on the internet with people having problems with this chip and driver - but most find a way...I have not (and all indications are that the driver is set up OK...but perhaps not or not completely...I just don't know...I find network architecture the most complex of all computer-related things....and the least understandable when I read about them.

---

### Post by jetsam on 2019-11-18
I'd still really recommend trying one.  Just buy from a place that offers easy returns.  If you can't get it working, return it and no worries.

It's impossible to predict signal strength in detail, and these things are designed to make the most of what they can get.  You can get enough signal under Windows to make your wireless work, so there must be, at least sometimes, enough signal available at your location.

I *think* it could work for you.  No guarantees, of course, but I really think it could save you another three days or a week of grief wrestling with wrappers and drivers for your wireless card.  You've better things to do with your time.

Edited to add: there are also free standing variants, and ones with bigger antennas...  some have 5 switched ethernet ports.  I just linked to an inexpensive option that seemed like it could do the job.  You'd want to comparison shop some.

---

### Post by praseodym on 2019-11-18
Download it via Windows and transfer it via USB (somehow)

---

### Post by crazybear on 2019-11-19
> **praseodym said:**
> Download it via Windows and transfer it via USB (somehow)

I would not know how to do such a thing - either the download nor the transfer.

---

### Post by jetsam on 2019-11-19
You can PM me, crazybear, if you want to.  We could maybe work out an equipment loan.  I'd need some way to mail you things, though...

---

### Post by crazybear on 2019-11-21
I'm TOTALLY frustrated. I hesitated and now wish I had NOT purchased a wifi extender. It comes with horrible instructions - without words; only with images that I can NOT understand after a full day trying. I can not get it to work [I think] and if I got it to work, it is doing nothing. This is how I usually find any device related to networking. The instructions are written for people who don't need instructions. I do. I'll fight a few more hours, but then return it......and even that will be a battle. It also nowhere said if it would be Linux compatible, but I can't even get it to work on the Windoz disk/OS. I'm very frustrated. I think devices are NOT what I need. the signal strength is good enough to get the wifi signal my tablet is using as I type and in nearly the exact same position as the ASUS device for the desktop. Something is wrong with the configuration of the ASUS. Can anyone help?! I'm going broke paying this corrupt phone provider for 5Gb sims [which last only days if I use them very sparingly]. I can't get a contract service and can't go into why. 

Again, the suggestion I get a read out of 
./wireless-info

was not defined as to what I was to do. Look in the file? Run it in terminal? {I would assume the former, as the later doesn't work]

---

### Post by jetsam on 2019-11-21
Darn.  It's possible you're being stymied by the other side of the network that you're connecting to.  Some public/private networks in apartment buildings are locked down pretty tight.  You could be hitting firewalls after connecting and being identified as an unusual user.  

If you could somehow pretend to be a gamer... that could get complicated unfortunately...

I'm sure the wifi extender can do some good for you, can you link to the model and manufacturer?  I'd like to see its user manual.

---

### Post by crazybear on 2019-11-21
I have a STRONG Dual Band Repeater 750 and the insructions [such as they are] are available on the internet.

---

### Post by jetsam on 2019-11-21
This one?
[Dual Band Repeater 750]("https://www.strong.tv/en/products/repeater/repeater750")

Ok. I will have a look.  Let me know if you make any progress on your own initiative.

---

### Post by crazybear on 2019-11-22
Yes, that one exactly.

---

### Post by crazybear on 2019-11-22
[URL="https://www.strong.tv/en/products/repeater/repeater750"]```

https://www.strong.tv/en/products/repeater/repeater750

```

[/URL]But, no one seems to focus on what is MOST obvious to me: My Samsung tablet which is only 1 ft [30 cm] closer to the window than the antenna of the Asus in the desktop gets streaming video from this wifi signal without problem....signal strength is NOT the problem. The problem is some configuration problem or block in the software in the computer, IMHO.

---

### Post by jetsam on 2019-11-22
> The problem is some configuration problem or block in the software in the computer, IMHO. 

Yes.  The drivers for your computer's wifi adapter are functional, but only barely functional.  praseodym was attempting to walk you through the process of changing them, but progress stalled there...  We would need to transfer a lot of source files to your computer via manual usb drive transfers, then get your computer to compile new replacement drivers for your wifi card...

But in the meantime, you've aquired the Strong repeater.  If we can make that work, we can forget about the problematic wifi adapter entirely.

Please hook an ethernet cable between your computer and the repeater.  The cable should be attached to the port marked LAN on the repeater, and to the ethernet port on the back of your computer.
There is a switch on the side of the repeater labeled "access point/repeater/router."  Set it to the "repeater" position for now.
Plug in the repeater somewhere you think it should get a decent signal.
Turn on your computer, open a browser and type the following into the browser address bar:
> [http://192.168.10.1](http://192.168.10.1)
This should bring you to the admin sign on page of the repeater.
Use 'admin' for the username and 'admin' for the password, and push the 'logon' button.

Does it show you a web page for configuring the repeater with an option for connecting to a wifi network?

---

### Post by crazybear on 2019-11-22
> **jetsam said:**
> Yes.  The drivers for your computer's wifi adapter are functional, but only barely functional.  praseodym was attempting to walk you through the process of changing them, but progress stalled there...  We would need to transfer a lot of source files to your computer via manual usb drive transfers, then get your computer to compile new replacement drivers for your wifi card...

But in the meantime, you've aquired the Strong repeater.  If we can make that work, we can forget about the problematic wifi adapter entirely.

Please hook an ethernet cable between your computer and the repeater.  The cable should be attached to the port marked LAN on the repeater, and to the ethernet port on the back of your computer.
There is a switch on the side of the repeater labeled "access point/repeater/router."  Set it to the "repeater" position for now.
Plug in the repeater somewhere you think it should get a decent signal.
Turn on your computer, open a browser and type the following into the browser address bar:

This should bring you to the admin sign on page of the repeater.
Use 'admin' for the username and 'admin' for the password, and push the 'logon' button.

Does it show you a web page for configuring the repeater with an option for connecting to a wifi network?

Already tried that before your suggestion. Have spent perhaps ten of the most frustrating hours yesterday and today fighting with this - which I will return soon. I can't take the frustration! Sometimes [and I'd say only about 10% of the time] I can with great difficulty get the page for configuring - usually it times out and magically appears on the browser if I leave it alone for 30 min or so...and it often freezes or times out after making a change. I've tried many combinations of things, but nothing works. Less so in Ubuntu than in Windows - but nothing works in either. I'm exhausted and going insane from this. Their 'diagram' shows pressing of a button on the device for ten seconds many times - what it is and why they do not say. I can't figure out what to try to connect to...but I've tried everything that shows and no change....no internet. Nothing I see makes sense. In Ubuntu I can monitor the number of bytes up and down and it shows an increase, but NO internet connection. The interface seems like it was written in China by someone who did not know English and used google-translate. Some instructions make no sense. I try to figure out what they mean and usually everything just freezes up. There is one place where after a bar moving shows 'loading' it says 'if you are connected by LAN unplug the lan for 7 sec and plug back in and go back'. It doesn't say whether to do that when the loading is happening, before, or after - nor if one is to the the 'back' button [which never works] or use the back arrow on the browser - which also doesn't work. I think everytime it has frozen up at that point and I start all over again trying for 30-45 min to get to the log in page. AAAAAHHHHHH!

---

### Post by jetsam on 2019-11-22
Right.  Take a break from it for a while, crazybear.  Your frustration doesn't need to be so frustrating...

Consider calling a local IT guy in.  Somebody else needs to help you jump these hoops, and any professional would likely have you online in minutes, or at least be able to identify a better approach to your problems.  Wherever you bought the repeater from may offer cheap tech support.  If they don't, surely someone else does.  Check craigslist for a computer fixit guy. 

This is now probably the longest thread I've ever followed on the forums, and I've been in a few marathon threads before.  It's an achievement of a sort that you're still trying and haven't given up.  

The goal is to not let the frustrations get so severe that you feel you have to give up.  Networking tends to present troubles early on during set-up and configuration.  Once it gets going, though, it just goes and goes and goes.  At least it ought to.

Cheers,
jetsam

---

### Post by crazybear on 2019-11-22
No local IT guy. Negative. Now, in Win it shows that it is feeding something into the LAN port, but only when I turn off the LAN port and use the expensive and slow phone provider USB thing can I get on the internet. I don't know if I can call that progress. Somehow the two together conflict...but I tried just the extender and that didn't work. By the way, the extender is really a Winstars with another name on it.

---

### Post by jetsam on 2019-11-22
> By the way, the extender is really a Winstars with another name on it. 

Winstars sales page:
[http://www.win-star.com/en_us/product/WS_WN575A2.html]("http://www.win-star.com/en_us/product/WS_WN575A2.html")

There's no manual downloads at the moment.  Web site in progress :(

Where do you find this equipment?  Go to the most common electronics store locally and buy the thing they sell the most of.  You'll save yourself all kinds of grief staying on the beaten path in this instance.

---

### Post by crazybear on 2019-11-22
> **jetsam said:**
> Winstars sales page:
[http://www.win-star.com/en_us/product/WS_WN575A2.html](http://www.win-star.com/en_us/product/WS_WN575A2.html)

There's no manual downloads at the moment.  Web site in progress :(

Where do you find this equipment?  Go to the most common electronics store locally and buy the thing they sell the most of.  You'll save yourself all kinds of grief staying on the beaten path in this instance.

It comes with a photo only 'manual'...but that is very confusing and I have a PhD in the sciences. I'm already beyond budget. I have no income and lots of money going out. My situation is totally NON-STANDARD. It was one of two of the more popular sellers at the big computer store...but unless and until I return it and get my money back, I'm not buying anything else. I can't explain my situation - just accept it as non-standard. I'm not in my country. I do not speak the local language more than a little. Why will no one address the fact the tablet gets this wifi signal no problem, and the computer will not - at least not the ASUS device and I'm struggling with this Strong. I don't see it pictured in the win-star page, but that is what shows up when I ask wifi devices to be listed in Ubuntu....don't know why...maybe  some part or partnership or one company making for another.  At the Strong website you can download the same sheet of 'set up instructions' I have. [https://www.strong.tv/downloads/manuals/Dual_Band_Repeater_750_QG.pdf](https://www.strong.tv/downloads/manuals/Dual_Band_Repeater_750_QG.pdf) Very lame, as is the interface to set up the device. I have things I MUST do to not perish, and have limited time to mess around with this - although good internet is very important. I don't think I can devote more than some time this weekend. I MUST find another place fast - and without internet that is all but impossible. If I could explain my situation [which I can not], folks would understand better. It is late here and maybe until morning [I get up about 3:30 or 4:00 lately], I may try to forget this frustration and deal with the all too many other ones I have, unrelated to the computer. Thanks for the help. What made anyone think that the driver needed an upgrade? I thought I have built the latest one available. If there is some way to download things in Windows and they are not too large, I have movable drives to move the data to Ubuntu. I hate using Windoz and this back and forth along with all else I'm having to deal with [and can not discuss] is driving me to the edge. Back in the morning here....

---

### Post by jetsam on 2019-11-22
OK.  Tomorrow morning, then.

Ubuntu can't distribute the drivers we were trying to compile because they are closed source and proprietary...  They're taken from Windows installations, then "wrapped" by special code that lets them communicate with Linux...

Talk to you later,
--jetsam

---

### Post by crazybear on 2019-11-23
> **jetsam said:**
> This one?
[Dual Band Repeater 750]("https://www.strong.tv/en/products/repeater/repeater750")

Ok. I will have a look.  Let me know if you make any progress on your own initiative.
As a matter of fact, at this time, the extender is BLOCKING my getting anything - such as from the USB device [expensive and slow]. I  just had to shut off the extender in order to get on line with the USB device. This is obviously a conflict in how the extender is set up, I think...but setting up the extender is a nightmare and clear as mud. I have not the faintest idea of how I should do it; what the architecture should be, etc.

Again, as I have said repeatedly and no one hears me on - if the router is blocking my computer, why is it not blocking my tablet? To me this says it has no active system to identify me or any of my devices.

---

### Post by crazybear on 2019-11-23
> **jetsam said:**
> OK.  Tomorrow morning, then.

Ubuntu can't distribute the drivers we were trying to compile because they are closed source and proprietary...  They're taken from Windows installations, then "wrapped" by special code that lets them communicate with Linux...

Talk to you later,
--jetsam

I'm here off and on today and likely tomorrow, but woke up frustrated - see the above comment to see why. In setting up the repeater, I have made things worse, not better. logging on to the repeater is an hour long nightmare. Once in it, it is NOT clear what needs to be done and what will cause more problems. Usually after making changes the entire screen locks up and I just say *** it and give up for some hours.

I don't understand what makes you think the Ubuntu drivers I built are not the most recent or incorrectly built. I don't want to do needless activity [which is all I have been doing up to now].

---

### Post by jetsam on 2019-11-23
Two architectures:  

This is the one I was hoping would work:
```
PC--->ethernet cable---->repeater---->wifi---->wifi router---->internet
```

This is the one you started this thread trying to make work:
```
PC--->wifi adapter--->wifi--->wifi router--->internet
```

Architecture #1 means giving the repeater your network wifi credentials through its admin page.  Apparently something is going wrong at that point, but it's hard for me to add anything helpful...  I don't understand where the configuration is going wrong.

Architecture #2 I believe means going back to post #24 and #34 of this thread and picking up where you left off.  Post #34 by praseodym:
> Download it via Windows and transfer it via USB (somehow) 

refers to #24:
> Haven't read through anything, but your LAN-NIC is Realtek 8168. Download this file and save it in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/...7.02-1_all.deb](http://de.archive.ubuntu.com/ubuntu/...7.02-1_all.deb)

Installation

... and it continues on from there.

That's where we are.  



--------


Is there anything on FAQ page of the Strong support site for your repeater that helps at all?
[https://www.strong.tv/en/products/repeater/repeater750]("https://www.strong.tv/en/products/repeater/repeater750")

One complication that may be confusing you:
> Before the installation, the default IP address of Dual Band Repeater 750 is 192.168.10.1.After the installation, Dual Band Repeater 750 obtains its IP address from your router. Please login to the management interface of your router and check the IP address that is assigned to your Dual Band Repeater 750. 

But after the repeater is connected to wifi, you should be able to connect to the web admin interface most easily through: 
> [http://strong.ap750](http://strong.ap750)

---

### Post by crazybear on 2019-11-23
> **jetsam said:**
> Two architectures:  

This is the one I was hoping would work:
```
PC--->ethernet cable---->repeater---->wifi---->wifi router---->internet
```

This is the one you started this thread trying to make work:
```
PC--->wifi adapter--->wifi--->wifi router--->internet
```

Architecture #1 means giving the repeater your network wifi credentials through its admin page.  Apparently something is going wrong at that point, but it's hard for me to add anything helpful...  I don't understand where the configuration is going wrong.

Architecture #2 I believe means going back to post #24 and #34 of this thread and picking up where you left off.  Post #34 by praseodym:
 

refers to #24:

... and it continues on from there.

That's where we are.
No, not exactly so. I believe I turned off the wifi adapter, but nothing changed. I can try that again. There are just so many variables and likely the repeater is not set up correctly [the page was as clear as mud as to how to set it up and kept freezing up anyway]. I can't keep switching back and forth from one project to the other and back and then back again. I'm running out of time. I need to pick one and make it work or....I don't know what. I'm not doing this to watch the news or play games or any such. Let me try again turning off the wifi adapter.... too many variables [two OS; three+ ways to access internet; many configurations; many problems with each of these named, so not too easy to find the problem[s]......

---

### Post by crazybear on 2019-11-23
Stranger than strange! I [thought] I finally got it connected - first on  the Windoz disk and then on the Ubuntu disk. The Ubuntu disk had not  been updated in a LOOONG time and I updated it with several things...and  now, without touching/changing anything [as far as I'm aware], I'm only  able to get on the internet with the USB device, as before.
While  the speed when it was connected was not blinding fast, it was OK....but  now..... what the hell is going on here? I don't get it. I had found how  to reset the wifi device and struggled again to get to the setup page  and tried some new combination of what is not explained well [ha!] in  the pictures only 'manual'. It worked for a while....and  now....????!??!!!

If I get on again in the Ubuntu disk, what should I update? I could have before.....now, I can't but will try again in the morning. It was all working for many hours....now not.

---

### Post by jeremy31 on 2019-11-24
See the wireless script link in my signature so that we can see current results

---

### Post by crazybear on 2019-11-25
Can anyone download the [horrible] 'photo-instructions' and help  me.....I have tried perhaps 30+ times many different ways - taking up 20  hours of time, with only about 2 hours of success, which spontaneously  ended and I don't remember the formula of things I did to get there.  Also, If I ever get back online in Ubuntu, what can I do to get the ASUS  driver to work. I have spent money and all too much time and  frustration...and have made no progress, sadly. I'm exhausted and will  soon give up - as I have urgent things I must do and this is taking away  from those tasks. I'll give it another day or two....then give up.  Please help...

---

### Post by crazybear on 2019-11-25
> **jeremy31 said:**
> See the wireless script link in my signature so that we can see current results

That takes having internet. I do NOT! Only in Windoz - NOT in Ubuntu. Sorry.

---

### Post by uRock on 2019-11-25
You'll have to download the script using Windows, then save to a drive accessible by both OSes, then run it in ubuntu, then save to that same drive, then use Windows to upload the output. 

Notice I spell Windows properly?

---

### Post by wildmanne39 on 2019-11-25
If you still have the wireless script on your computer and it is in your home folder like it should be then just run this command:
```
./wireless-info
```
it will create the text file in your home folder.

---

### Post by jeremy31 on 2019-11-25
Some commands to check ```
lspci -nnk | grep -iA3 net
```
Does the wifi device show a kernel driver in use?
```
rfkill list
```
Does it show a hard or soft block on wifi?
```
cat /var/lib/NetworkManager/NetworkManager.state
```
Does it show ```
[main]
NetworkingEnabled=true
WirelessEnabled=true
```
Or does it show false?

---

### Post by crazybear on 2019-11-26
> **uRock said:**
> You'll have to download the script using Windows, then save to a drive accessible by both OSes, then run it in ubuntu, then save to that same drive, then use Windows to upload the output. 

Notice I spell Windows properly?

.......that assumes I know how to download a Linux script in Windows. I do not. Please explain. Thanks.

---

### Post by crazybear on 2019-11-26
FINALLY, making some progress!...[I hope it lasts!]....I'm online in Ubuntu...the connection is rather slow..but there IS a connection! I will give some of the diagnositics, below. Please tell me if there is anything I should do to make it work better and/or faster. I can see the repeater is not doing anything. It is broadcasting an empty signal....but I seem to be getting my weak signal through the PCIe ASUS device.

```

:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2019-11-26 07:49:27--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 140.82.118.3
Connecting to github.com (github.com)|140.82.118.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2019-11-26 07:49:27--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 199.232.16.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|199.232.16.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info               100%[==========================================>]  17.04K  --.-KB/s    in 0.1s    

Last-modified header missing -- time-stamps turned off.
2019-11-26 07:49:28 (139 KB/s) - &#8216;wireless-info&#8217; saved [17452/17452]


Results saved in "/home/xxxxx/wireless-info.txt".


~$ sudo lshw -C network; lsb_release -a; uname -a; sudo rfkill list; sudo iwlist scan | egrep 'chan|sid'
  *-network               
       description: Wireless interface
       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: 04:d4:c4:13:c1:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-55-generic firmware=N/A ip=192.168.1.33 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:40 ioport:ee00(size=256) memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 03
       serial: 00:24:1d:ce:b6:64
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:ce:b6:66
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.54 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:17 ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwx001e101f0000
       serial: 00:1e:10:1f:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=no multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: 52:54:00:2b:2f:a7
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial
Linux xx 4.15.0-55-generic #60~16.04.2-Ubuntu SMP Thu Jul 4 09:03:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
virbr0    Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wwx001e101f0000  Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.


```

```

##### NetworkManager info ###############

GENERAL.DEVICE:                         virbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0
GENERAL.IP-IFACE:                       virbr0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     virbr0
GENERAL.CON-UUID:                       559ec3d2-32d5-4a44-acc4-163eef7a649b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{28}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   559ec3d2-32d5-4a44-acc4-163eef7a649b | virbr0
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         00:24:1D:CE:B6:66
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:08:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Internet
GENERAL.CON-UUID:                       a1e88d07-fe54-42c3-9bc8-cc863731c639
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{12}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a1e88d07-fe54-42c3-9bc8-cc863731c639 | Internet
IP4.ADDRESS[1]:                         192.168.1.54/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1574839713
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.54
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::224:1dff:fece:b666/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = fe80::1/128, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_info_refresh_time = 14400
DHCP6.OPTION[2]:                        dhcp6_client_id = 0:4:93:ae:0:c8:7b:fd:6b:cf:b0:ca:aa:74:f7:6f:ab:48
DHCP6.OPTION[3]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        dhcp6_unknown_16 = 0:0:d:e9:0:c:64:73:6c:66:6f:72:75:6d:2e:6f:72:67
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:10:7b:ef:c3:1c:98

GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8812AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.15.0-55-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         04:D4:C4:13:C1:51
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:04:00.0/net/wlp4s0
GENERAL.IP-IFACE:                       wlp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     AP-HotelH-2G 19
GENERAL.CON-UUID:                       e08a3c3a-f97c-4b73-b6f5-b8fe07011115
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     144 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{25,14,23,18,22,24,27,21,19,3,2,15,0,4,6,5,1,20,10,9,7,17}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1e3de76d-c391-4946-aae6-7c5e3a317440 | AP-HotelHenrici-2G 15
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   3943fc77-fdc9-410e-a93a-c74e3c89698f | AP-HotelHenrici-2G 3
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   95d6ea90-3912-4ea2-a15d-b8966704eec2 | AP-HotelHenrici-2G 18
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   990dbb89-90c7-4292-8a57-221030287363 | AP-HotelHenrici-2G 12
CONNECTIONS.AVAILABLE-CONNECTIONS[5]:   59b6581a-c334-4ee6-8c54-f079d63bd14f | AP-HotelHenrici-2G 9
CONNECTIONS.AVAILABLE-CONNECTIONS[6]:   0080479c-14fb-4f59-9b31-87761aafff4d | AP-HotelHenrici-2G 4
CONNECTIONS.AVAILABLE-CONNECTIONS[7]:   e08a3c3a-f97c-4b73-b6f5-b8fe07011115 | AP-HotelHenrici-2G 19
CONNECTIONS.AVAILABLE-CONNECTIONS[8]:   d3e4ed26-ffbe-44bf-875f-4a11fb63c65c | AP-HotelHenrici-2G 13
CONNECTIONS.AVAILABLE-CONNECTIONS[9]:   0372012b-8dfa-48d2-8570-b9e057d47233 | AP-HotelHenrici-2G 5
CONNECTIONS.AVAILABLE-CONNECTIONS[10]:  6ffa7051-583e-4485-95d6-032c0c6ce6eb | AP-HotelHenrici-2G-STRONG 1
CONNECTIONS.AVAILABLE-CONNECTIONS[11]:  83b8c273-ed7c-47dd-8985-6053ba44d001 | AP-HotelHenrici-2G 10
CONNECTIONS.AVAILABLE-CONNECTIONS[12]:  5b6df40d-2a66-4752-aaa3-0a7d6a30cf0b | AP-HotelHenrici-2G 1
CONNECTIONS.AVAILABLE-CONNECTIONS[13]:  7e74b91f-dbf3-4941-a3b6-edc1494781d2 | AP-HotelHenrici-2G
CONNECTIONS.AVAILABLE-CONNECTIONS[14]:  5338e773-3a65-4f53-8a76-df8488edb5ff | AP-HotelHenrici-2G 14
CONNECTIONS.AVAILABLE-CONNECTIONS[15]:  63644978-4906-4081-bae0-afeb0e68eaed | AP-HotelHenrici-2G 16
CONNECTIONS.AVAILABLE-CONNECTIONS[16]:  e2eb3b7c-25f6-4bc9-b9f4-91a3c13bc4ef | AP-HotelHenrici-2G 6
CONNECTIONS.AVAILABLE-CONNECTIONS[17]:  70037219-d88a-4388-83ce-4652e16425e6 | AP-HotelHenrici-2G 7
CONNECTIONS.AVAILABLE-CONNECTIONS[18]:  530fd6fa-dd01-4532-843c-55b29d82aa10 | AP-HotelHenrici-2G 2
CONNECTIONS.AVAILABLE-CONNECTIONS[19]:  90c0a398-9754-4ef0-bf83-b0889913bc54 | AP-HotelHenrici-2G-STRONG
CONNECTIONS.AVAILABLE-CONNECTIONS[20]:  0c8c76e9-5578-4b6f-9161-029c349d5e32 | AP-HotelHenrici-2G 17
CONNECTIONS.AVAILABLE-CONNECTIONS[21]:  b4b2e21f-9d9a-4a4e-a8bf-9a7b05061f81 | AP-HotelHenrici-2G 11
CONNECTIONS.AVAILABLE-CONNECTIONS[22]:  322fcd13-ccd0-4031-be45-b6dfc557ce62 | AP-HotelHenrici-2G 8
IP4.ADDRESS[1]:                         192.168.1.33/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1574839707
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.33
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::1a44:c900:45a7:384d/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = fe80::1/128, nh = ::, mt = 600
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        dhcp6_info_refresh_time = 14400
DHCP6.OPTION[2]:                        dhcp6_client_id = 0:4:93:ae:0:c8:7b:fd:6b:cf:b0:ca:aa:74:f7:6f:ab:48
DHCP6.OPTION[3]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        dhcp6_unknown_16 = 0:0:d:e9:0:c:64:73:6c:66:6f:72:75:6d:2e:6f:72:67
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:10:7b:ef:c3:1c:98

GENERAL.DEVICE:                         ttyUSB0
GENERAL.TYPE:                           gsm
GENERAL.NM-TYPE:                        NMDeviceModem
GENERAL.VENDOR:                         HUAWEI_MOBILE
GENERAL.PRODUCT:                        HUAWEI_MOBILE
GENERAL.DRIVER:                         option1, huawei_cdc_ncm
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         58 (Modem now ready and available)
GENERAL.UDI:                            /org/freedesktop/ModemManager1/Modem/0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         eth1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         00:24:1D:CE:B6:64
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:07:00.0/net/eth1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         virbr0-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         52:54:00:2B:2F:A7
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         41 (The device's existing connection was assumed)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0-nic
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
AP-2G-STRONG  80:3F:5D:A1:85:49  Infra  3     2422 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
AP-2G-5G      80:3F:5D:A1:85:4A  Infra  40    5200 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  --         no        
AP-Hot            C8:3A:35:47:54:78  Infra  7     2442 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
AP-Hot-2G         B4:75:0E:17:5E:A2  Infra  3     2422 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  --         yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 2

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
no-auto-default=00:24:1D:CE:B6:66,00:24:1D:CE:B6:64,
[ifupdown]
managed=true


##### NetworkManager profiles ###########

```

---

### Post by crazybear on 2019-11-26
As with last time.....after a good [if not great] initial ability to get on the internet, with time of about an hour, it slowly slowed down to a stop/ How is that possible. Is something else in  my system causing this. Is the repeater - which is NOT set up properly and defies being set up properly? Is something else? I'm sending this from Windoz and using the overly expensive USB device. I'm exhausted. I'm confused. Help appreciated. It seems, at minimum. I can for about an hour get on with a low-level connection in Ubuntu...if that allows a window to do something to fix all this.

---

### Post by jeremy31 on 2019-11-26
Can you copy the wireless-info.txt file from your home directory in Ubuntu to a thumb drive so you can post the contents from Windows

---

### Post by crazybear on 2019-11-27
Can anyone find any problem with my set up? Again later yesterday and this morning I could NOT AT ALL connect to the internet thought the ASUS PCIe device! I don't understand. The two times I was able to, the signal was weak and got weaker within an hour and then stopped. All the while my tablet, which was getting the exact same wifi signal stayed steady. What is going on?! The wifi extender I purchased seems useless and impossible to configure. I have wasted about 20 hours fighting with it and give up. It goes back to the store today. It comes with the worst 'instructions' ever, written by a non-English speaker for the English version and totally unclear. With it I NEVER got connected and it never boosted the wifi - or even carried it. Maybe I'll try another - or just give up....haven't decided yet. Here, returning a device means an hour wait after a half hour each way drive. The TP devices at least have robust instruction manuals. But the ASUS device should work without the extender and it is not. In an effort once to cloak my computer behind another, a techie type once assigned some IP addresses to the LAN ports. Could that be in part causing the problem? I don't know how to undo that in Windows. I do, but have not in Ubuntu. I'm just confused. Anything 'network' is just confusing to me. Help please.....I can't emphasize how urgent and important a good internet signal is now. It is literally a matter of life and death and I have few alternatives due to my special circumstances.

---

### Post by crazybear on 2019-11-27
> **jeremy31 said:**
> Can you copy the wireless-info.txt file from your home directory in Ubuntu to a thumb drive so you can post the contents from Windows

I believe it is the lower window of post 62 above. I'll double check, but I'm sure I copied and pasted it in one of those windows.

The extender diversion never worked out. I returned the first and have a second - I can connect to neither. Besides, I'm a scientist and the fact my tablet can get a fairly good signal and is only a VERY, VERY short distance closer to the source of the wifi than the computer was always a clue that the signal didn't need boosting [it can't hurt - but I can't get it boosted anyway]...and that the problem lies in the configuration of the computer software.

What is powersave and why would I want it? This is not a laptop, this is a huge desktop with 1200 Watts of power.

---

### Post by uRock on 2019-11-27
> **crazybear said:**
> I believe it is the lower window of post 62 above. I'll double check, but I'm sure I copied and pasted it in one of those windows.

The extender diversion never worked out. I returned the first and have a second - I can connect to neither. Besides, I'm a scientist and the fact my tablet can get a fairly good signal and is only a VERY, VERY short distance closer to the source of the wifi than the computer was always a clue that the signal didn't need boosting [it can't hurt - but I can't get it boosted anyway]...and that the problem lies in the configuration of the computer software.

What is powersave and why would I want it? This is not a laptop, this is a huge desktop with 1200 Watts of power.

This shows powersave is turned off.
```
##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
**wifi.powersave = 2**

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
no-auto-default=00:24:1D:CE:B6:66,00:24:1D:CE:B6:64,
[ifupdown]
managed=true
```[https://gist.github.com/jcberthon/ea8cfe278998968ba7c5a95344bc8b55](https://gist.github.com/jcberthon/ea8cfe278998968ba7c5a95344bc8b55)

The network extender idea was unnecessary. I am sorry you were taken down that rabbit hole.

I did see mention of the antenna wire possibly being loose. My Netbook has that issue and it is very obvious as it had a hard time connecting to an AP that was only 20 feet away without any obstructions.

I'm not very good at troubleshooting wireless, so I can't offer much more information on what's being seen in the script information you've posted. Hopefully someone else is able to take a look at that and spot the issue.

---

### Post by wildmanne39 on 2019-11-27
You want powersave mode off that allows your wifi device to operate more efficiently. The info from the script you posted is very incomplete that is why we need to see all the text file information so someone can help you.

---

### Post by crazybear on 2019-11-28
It is too large to post here......never did a pastebin upload....trying...

---

### Post by wildmanne39 on 2019-11-28
Here is the link to Ubuntu pastebin:

[https://paste.ubuntu.com/](https://paste.ubuntu.com/)

it is easy to paste the information from the file into Ubuntu pastebin, I am currently having trouble loading the page for pastebin for some reason but the link I provided works great.

Just paste the content of the file created by the script into the window on Ubuntu pastebin site then click paste afterwards copy the link to the information back here so we can see it.

---

### Post by crazybear on 2019-11-28
-snip- will replace with new one shortly

The strangest things are happening...sometimes I will get good internet connection, other times there is none!

---

### Post by jeremy31 on 2019-11-28
I might have found something
```
cd /lib/firmware/rtlwifi
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/rtlwifi/rtl8812aefw.bin
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/rtlwifi/rtl8812aefw_wowlan.bin
```

Reboot, you can also try disabling the kernel module power management with
```
echo "options rtl8821ae ips=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf
```

This firmware has been released about 6 weeks ago [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/rtlwifi?id=c1ce20e56e81bffa48209793754001fc7afff7a5](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/rtlwifi?id=c1ce20e56e81bffa48209793754001fc7afff7a5)

---

### Post by crazybear on 2019-11-28
Right now, sometimes I get internet [and it is good]; other times I get zero - and never know nor can I see what causes the change. It is driving me insane - and still having to go back to the Windoz disk to even type this.
I will run another analytical on the system..... 

The new firmware I downloaded - but haven't the faintest idea of what or how to deal with it and wouldn't without specific step-by-step instructions. Besides, I use the [COLOR=#000000]rtl8821ae driver. Isn't this for the other?[/COLOR]

---

### Post by crazybear on 2019-11-29
to your suggested command all got in response was 
```

[COLOR=#000000][FONT=&amp]rtl8821ae ips=N

```
 - nothing more to 
```

[/FONT][/COLOR]echo "options rtl8821ae ips=N" | sudo tee /etc/modprobe.d/rtl8821ae.conf

```

---

### Post by crazybear on 2019-11-29
[https://paste.ubuntu.com/p/4cpjhCXPnn/](https://paste.ubuntu.com/p/4cpjhCXPnn/)

Is the latest. At the moment, for reasons unknown, I again have internet in Ubuntu.

Oh, by the way, each time I have to go into terminal and tell it to connect to the preferred AP. There must be a way to have it do that automatically, but how I don't know. Would be appreciated.

---

### Post by jeremy31 on 2019-11-29
> **crazybear said:**
> Right now, sometimes I get internet [and it is good]; other times I get zero - and never know nor can I see what causes the change. It is driving me insane - and still having to go back to the Windoz disk to even type this.
I will run another analytical on the system..... 

The new firmware I downloaded - but haven't the faintest idea of what or how to deal with it and wouldn't without specific step-by-step instructions. Besides, I use the [COLOR=#000000]rtl8821ae driver. Isn't this for the other?[/COLOR]

Your device just uses the rtl8821ae driver but it is a rtl8812ae chipset and that is why it needs that firmware.  To auto connect to wifi, go into Network Manager connections and set one to automatically connect when in range

---

### Post by crazybear on 2019-11-29
OK, thanks, now I understand why I would need the firmware update - but looking in the package I have no idea how to install the firmware - guidance gladly appreciated. It contains a long list of devices, but not mine and even if ASUS was listed, I wouldn't know what to do. 

Way back at the start of this long thread I mentioned I have no Network Manager that is supposed to be 'there', so there is no setting for connect automatically...... How to re-install Network Manager? I think long ago there was one. All I have is something called Netspeed preferences which is not very good. Addendum....stranger still, in Synaptic it shows several files installed when I put 'Network Manager' in the search box....but I can't find it nor can I launch it from terminal.

---

### Post by jeremy31 on 2019-11-29
Do you have an icon in the notification area/taskbar for wifi/ethernet?  That normally can be left/right clicked for options such as editing network connections

---

### Post by crazybear on 2019-11-30
> **jeremy31 said:**
> Do you have an icon in the notification area/taskbar for wifi/ethernet?  That normally can be left/right clicked for options such as editing network connections

No. I remember there was one in my earlier versions of Ubuntu, but think not in 16.04 for me. There is just an area of up and down arrows and I can have it show the number of bytes or bits up and down. No other setting other than what it monitors [LAN 1, LAN 2, this wifi device it is now set on, etc.] I always connected before by LAN, so it was never an issue. Now it is. Another thing that is happening strangely - when I do get internet in Ubuntu it is quite good; but it sometimes just stops [even though the netspeed monitor - which I have to right click where those arrows are to make appear] shows a LOT of bytes going up and down as before.....and the connection is not reported as lost - but something is blocking somewhere. It can happen without opening any new program or window or doing anything. Other times it does seem [maybe] connected to opening a new program/browser - but often not.

_How do I apply this new firmware that I downloaded_? - and do you think it will make any difference? I'm NO expert at all, but I don't think it would explain the on sometimes off sometimes connection to the internet while the packets are still flowing - but who knows......

---

### Post by jeremy31 on 2019-11-30
The new firmware should be in use as the driver will load it if it is found in /lib/firmware/rtlwifi
The last script result you posted shows that the wifi switched between the router and the extender device, it might be worth shutting the extender off
See if network-manager-gnome is installed

---

### Post by crazybear on 2019-11-30
> **jeremy31 said:**
> The new firmware should be in use as the driver will load it if it is found in /lib/firmware/rtlwifi 

Move the entire folder [with all the various things in it] to /lib/firmware/rtlwifi?

> **jeremy31 said:**
> 
The last script result you posted shows that the wifi switched between the router and the extender device, it might be worth shutting the extender off
See if network-manager-gnome is installed

Will do/try (but if memory serves me network-manager-gnome is installed, but will check again). But the extender is really boosting the signal....the problem as mentioned now is I see LOTS of bytes coming and going - but all programs claim they can not find the server!?!?!?!? - so I get no internet connection.

.....but as I was trying various things, something strange happened: eth0 and eth1 are now listed as 'unclaimed' and don't show up......how do I 'claim' them again? Thanks.
```

 [FONT=&amp]sudo lshw -C network; lsb_release -a; uname -a; sudo rfkill list; sudo iwlist scan | egrep 'chan|sid'[/FONT]

[FONT=&amp]  *-network               [/FONT]
  [FONT=&amp]       description: Wireless interface[/FONT]
  [FONT=&amp]       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter[/FONT]
  [FONT=&amp]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
  [FONT=&amp]       physical id: 0[/FONT]
  [FONT=&amp]       bus info: pci@0000:04:00.0[/FONT]
  [FONT=&amp]       logical name: wlp4s0[/FONT]
  [FONT=&amp]       version: 01[/FONT]
  [FONT=&amp]       serial: 04:d4:c4:13:c1:51[/FONT]
  [FONT=&amp]       width: 64 bits[/FONT]
  [FONT=&amp]       clock: 33MHz[/FONT]
  [FONT=&amp]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
  [FONT=&amp]       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-70-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11[/FONT]
  [FONT=&amp]       resources: irq:38 ioport:ee00(size=256) memory:fbefc000-fbefffff[/FONT]
  [FONT=&amp]  *-network **_UNCLAIMED_**[/FONT]
  [FONT=&amp]       description: Ethernet controller[/FONT]
  [FONT=&amp]       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT]
  [FONT=&amp]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
  [FONT=&amp]       physical id: 0[/FONT]
  [FONT=&amp]       bus info: pci@0000:07:00.0[/FONT]
  [FONT=&amp]       version: 03[/FONT]
  [FONT=&amp]       width: 64 bits[/FONT]
  [FONT=&amp]       clock: 33MHz[/FONT]
  [FONT=&amp]       capabilities: pm msi pciexpress msix vpd bus_master cap_list[/FONT]
  [FONT=&amp]       configuration: latency=0[/FONT]
  [FONT=&amp]       resources: ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff[/FONT]
  [FONT=&amp]  *-network **_UNCLAIMED_**[/FONT]
  [FONT=&amp]       description: Ethernet controller[/FONT]
  [FONT=&amp]       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller[/FONT]
  [FONT=&amp]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
  [FONT=&amp]       physical id: 0[/FONT]
  [FONT=&amp]       bus info: pci@0000:08:00.0[/FONT]
  [FONT=&amp]       version: 03[/FONT]
  [FONT=&amp]       width: 64 bits[/FONT]
  [FONT=&amp]       clock: 33MHz[/FONT]
  [FONT=&amp]       capabilities: pm msi pciexpress msix vpd bus_master cap_list[/FONT]
  [FONT=&amp]       configuration: latency=0[/FONT]
  [FONT=&amp]       resources: ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff[/FONT]
  [FONT=&amp]  *-network:0 DISABLED[/FONT]
  [FONT=&amp]       description: Ethernet interface[/FONT]
  [FONT=&amp]       physical id: 1[/FONT]
  [FONT=&amp]       logical name: virbr0-nic[/FONT]
  [FONT=&amp]       serial: 52:54:00:2b:2f:a7[/FONT]
  [FONT=&amp]       size: 10Mbit/s[/FONT]
  [FONT=&amp]       capabilities: ethernet physical[/FONT]
  [FONT=&amp]       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s[/FONT]
  [FONT=&amp]  *-network:1 DISABLED[/FONT]
  [FONT=&amp]       description: Ethernet interface[/FONT]
  [FONT=&amp]       physical id: 2[/FONT]
  [FONT=&amp]       logical name: wwx001e101f0000[/FONT]
  [FONT=&amp]       serial: 00:1e:10:1f:00:00[/FONT]
  [FONT=&amp]       capabilities: ethernet physical[/FONT]
  [FONT=&amp]       configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=no multicast=yes[/FONT]
  [FONT=&amp]LSB Version:   core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch[/FONT]
  [FONT=&amp]Distributor ID: Ubuntu[/FONT]
  [FONT=&amp]Description:   Ubuntu 16.04.6 LTS[/FONT]
  [FONT=&amp]Release:       16.04[/FONT]
  [FONT=&amp]Codename:      xenial[/FONT]
  [FONT=&amp]Linux-GA-X58A-UD7 4.15.0-70-generic #79~16.04.1-Ubuntu SMP Tue Nov 12 14:01:10 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux[/FONT]

  [FONT=&amp]0: phy0: Wireless LAN[/FONT]
  [FONT=&amp]        Soft blocked: no[/FONT]
  [FONT=&amp]        Hard blocked: no[/FONT]
  [FONT=&amp]virbr0-nic  Interface doesn't support scanning.[/FONT]
  
  [FONT=&amp]virbr0    Interface doesn't support scanning.[/FONT]
  
  [FONT=&amp]wwx001e101f0000  Interface doesn't support scanning.[/FONT]
  
  [FONT=&amp]lo        Interface doesn't support scanning.[/FONT]
  

```

---

### Post by crazybear on 2019-11-30
network-manager-gnome is installed. Still need to know what to move to [COLOR=#000000]/lib/firmware/rtlwifi.[/COLOR]

Latest: [https://paste.ubuntu.com/p/DmRzDjsSYg/](https://paste.ubuntu.com/p/DmRzDjsSYg/)

---

### Post by crazybear on 2019-12-01
I'm in Ubuntu now, and today the internet has been stable. So, maybe the lack of a visible/usable network manager IS (part of?) the problem. Just my hunch. In terminal I typed NetworkManager and was told I had to be root; but when I added sudo at the front it did nothing and said NetworkManager not found....but it shows in Synaptic as installed in the form you suggested, above.

However, I have eth0 and eth1 listed as unclaimed and without any MAC addresses! How did that happen?! And how do I correct it? I use LAN connection to the internet much more than wifi and will need them for other purposes, as well!

```

 $ ip addr show
1: lo:<LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWNgroup default qlen 1000
    link/loopback00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8scope host lo
       valid_lftforever preferred_lft forever
    inet6 ::1/128scope host 
       valid_lftforever preferred_lft forever
2: wlp4s0:<BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UPgroup default qlen 1000
    link/ether04:d4:c4:13:c1:51 brd ff:ff:ff:ff:ff:ff
    inet192.168.1.37/24 brd 192.168.1.255 scope global dynamic wlp4s0
       valid_lft74311sec preferred_lft 74311sec
    inet6fe80::ece0:7976:b160:de97/64 scope link 
       valid_lftforever preferred_lft forever
3: wwx001e101f0000:<BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN groupdefault qlen 1000
    link/ether00:1e:10:1f:00:00 brd ff:ff:ff:ff:ff:ff
4: virbr0:<NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueuestate DOWN group default qlen 1000
    link/ether00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lftforever preferred_lft forever
5: virbr0-nic:<BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWNgroup default qlen 1000
    link/ether52:54:00:2b:2f:a7 brd ff:ff:ff:ff:ff:ff


$ sudo lshw -Cnetwork
[sudo] password for : 
  *-network              
       description:Wireless interface
       product:RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor:Realtek Semiconductor Co., Ltd.
       physical id:0
       bus info:pci@0000:04:00.0
       logical name:wlp4s0
       version: 01
       serial:04:d4:c4:13:c1:51
       width: 64bits
       clock: 33MHz
       capabilities:pm msi pciexpress bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=rtl8821aedriverversion=4.15.0-70-generic firmware=N/A ip=192.168.1.37latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources:irq:36 ioport:ee00(size=256) memory:fbefc000-fbefffff
  *-networkUNCLAIMED
       description:Ethernet controller
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor:Realtek Semiconductor Co., Ltd.
       physical id:0
       bus info:pci@0000:07:00.0
       version: 03
       width: 64bits
       clock: 33MHz
       capabilities:pm msi pciexpress msix vpd bus_master cap_list
      configuration: latency=0
       resources:ioport:be00(size=256) memory:fbaff000-fbafffffmemory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
 *-network UNCLAIMED
       description:Ethernet controller
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor:Realtek Semiconductor Co., Ltd.
       physical id:0
       bus info:pci@0000:08:00.0
       version: 03
       width: 64bits
       clock: 33MHz
       capabilities:pm msi pciexpress msix vpd bus_master cap_list
      configuration: latency=0
       resources:ioport:ae00(size=256) memory:fb8ff000-fb8fffffmemory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
  *-network:0DISABLED
       description:Ethernet interface
       physical id:1
       logical name:wwx001e101f0000
       serial:00:1e:10:1f:00:00
       capabilities:ethernet physical
      configuration: broadcast=yes driver=huawei_cdc_ncmdriverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=nomulticast=yes
  *-network:1DISABLED
       description:Ethernet interface
       physical id:2
       logical name:virbr0-nic
       serial:52:54:00:2b:2f:a7
       size:10Mbit/s
       capabilities:ethernet physical
      configuration: autonegotiation=off broadcast=yes driver=tundriverversion=1.6 duplex=full link=no multicast=yes port=twisted pairspeed=10Mbit/s

```

---

### Post by crazybear on 2019-12-02
Please all....the wifi is now working well - thanks...but somehow I made eth0 and eth1 disappear!....they are listed as UNCLAIMED. Please, how do I fix this. I need them!! the MAC address they had can be found in the second window.

```

 $ ip addr show
1: lo:<LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWNgroup default qlen 1000
    link/loopback00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8scope host lo
       valid_lftforever preferred_lft forever
    inet6 ::1/128scope host 
       valid_lftforever preferred_lft forever
2: wlp4s0:<BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UPgroup default qlen 1000
    link/ether04:d4:c4:13:c1:51 brd ff:ff:ff:ff:ff:ff
    inet192.168.1.37/24 brd 192.168.1.255 scope global dynamic wlp4s0
       valid_lft74311sec preferred_lft 74311sec
    inet6fe80::ece0:7976:b160:de97/64 scope link 
       valid_lftforever preferred_lft forever
3: wwx001e101f0000:<BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN groupdefault qlen 1000
    link/ether00:1e:10:1f:00:00 brd ff:ff:ff:ff:ff:ff
4: virbr0:<NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueuestate DOWN group default qlen 1000
    link/ether00:00:00:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lftforever preferred_lft forever
5: virbr0-nic:<BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWNgroup default qlen 1000
    link/ether52:54:00:2b:2f:a7 brd ff:ff:ff:ff:ff:ff


$ sudo lshw -Cnetwork
[sudo] password for : 
  *-network              
       description:Wireless interface
       product:RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor:Realtek Semiconductor Co., Ltd.
       physical id:0
       bus info:pci@0000:04:00.0
       logical name:wlp4s0
       version: 01
       serial:04:d4:c4:13:c1:51
       width: 64bits
       clock: 33MHz
       capabilities:pm msi pciexpress bus_master cap_list ethernet physical wireless
      configuration: broadcast=yes driver=rtl8821aedriverversion=4.15.0-70-generic firmware=N/A ip=192.168.1.37latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources:irq:36 ioport:ee00(size=256) memory:fbefc000-fbefffff
  *-networkUNCLAIMED
       description:Ethernet controller
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor:Realtek Semiconductor Co., Ltd.
       physical id:0
       bus info:pci@0000:07:00.0
       version: 03
       width: 64bits
       clock: 33MHz
       capabilities:pm msi pciexpress msix vpd bus_master cap_list
      configuration: latency=0
       resources:ioport:be00(size=256) memory:fbaff000-fbafffffmemory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
 *-network UNCLAIMED
       description:Ethernet controller
       product:RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor:Realtek Semiconductor Co., Ltd.
       physical id:0
       bus info:pci@0000:08:00.0
       version: 03
       width: 64bits
       clock: 33MHz
       capabilities:pm msi pciexpress msix vpd bus_master cap_list
      configuration: latency=0
       resources:ioport:ae00(size=256) memory:fb8ff000-fb8fffffmemory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
  *-network:0DISABLED
       description:Ethernet interface
       physical id:1
       logical name:wwx001e101f0000
       serial:00:1e:10:1f:00:00
       capabilities:ethernet physical
      configuration: broadcast=yes driver=huawei_cdc_ncmdriverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=nomulticast=yes
  *-network:1DISABLED
       description:Ethernet interface
       physical id:2
       logical name:virbr0-nic
       serial:52:54:00:2b:2f:a7
       size:10Mbit/s
       capabilities:ethernet physical
      configuration: autonegotiation=off broadcast=yes driver=tundriverversion=1.6 duplex=full link=no multicast=yes port=twisted pairspeed=10Mbit/s

[SIZE=5][U][B]
how they were...[/B][/U][/SIZE]

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 03
       serial: 00:24:1d:ce:b6:64
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:ce:b6:66
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:17 ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff

```

---

### Post by jeremy31 on 2019-12-02
Post results for ```
dkms status; modinfo r8168; grep r8169 /etc/modprobe.d/*; ls /lib/firmware/rtlwifi
```

---

### Post by crazybear on 2019-12-03
```

$ dkms status; modinfo r8168; grep r8169 /etc/modprobe.d/*; ls /lib/firmware/rtlwifi
oem-audio-hda-daily-lts-xenial, 0.201904020820~ubuntu16.04.1: added
modinfo: ERROR: Module r8168 not found.
/etc/modprobe.d/blacklist.conf:blacklist r8169
rtl8188efw.bin           rtl8192eu_wowlan.bin     rtl8723bu_nic.bin
rtl8188eufw.bin          rtl8192sefw.bin          rtl8723bu_wowlan.bin
rtl8192cfw.bin           rtl8712u.bin             rtl8723defw.bin
rtl8192cfwU_B.bin        rtl8723aufw_A.bin        rtl8723fw_B.bin
rtl8192cfwU.bin          rtl8723aufw_B.bin        rtl8723fw.bin
rtl8192cufw_A.bin        rtl8723aufw_B_NoBT.bin   rtl8812aefw.bin
rtl8192cufw_B.bin        rtl8723befw_36.bin       rtl8812aefw_wowlan.bin
rtl8192cufw.bin          rtl8723befw.bin          rtl8821aefw_29.bin
rtl8192cufw_TMSC.bin     rtl8723bs_ap_wowlan.bin  rtl8821aefw.bin
rtl8192defw.bin          rtl8723bs_bt.bin         rtl8821aefw_wowlan.bin
rtl8192eefw.bin          rtl8723bs_nic.bin        rtl8822befw.bin
rtl8192eu_ap_wowlan.bin  rtl8723bs_wowlan.bin
rtl8192eu_nic.bin        rtl8723bu_ap_wowlan.bin

```

---

### Post by jeremy31 on 2019-12-03
```
sudo sed -i 's/blacklist r8169/#blacklist r8169/' /etc/modprobe.d/blacklist.conf
```
Reboot, the firmware you downloaded is in the correct spot for the wireless driver to use it

---

### Post by crazybear on 2019-12-04
Great! Thanks! Almost done, I think....now I only need to rename the logical name back to what they were and is standard.... How does one do that? Now they have names like enp7s0 and enp8s0

```

 *-network               
       description: Wireless interface
       product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlp4s0
       version: 01
       serial: 04:d4:c4:13:c1:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.15.0-72-generic firmware=N/A ip=192.168.1.24 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:40 ioport:ee00(size=256) memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 03
       serial: 00:24:1d:ce:b6:64
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.047.02-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:33 ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 03
       serial: 00:24:1d:ce:b6:66
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.047.02-NAPI duplex=full ip=192.168.1.88 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:34 ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:2b:2f:a7
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s


```

---

### Post by CatKiller on 2019-12-04
[Predictable Network Interface Names]("https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/")

> 
**Why?**

  The classic naming scheme for network interfaces applied by the  kernel is to simply assign names beginning with "eth0", "eth1", ... to  all interfaces as they are probed by the drivers. As the driver probing  is generally not predictable for modern technology this means that as  soon as multiple network interfaces are available the assignment of the  names "eth0", "eth1" and so on is generally not fixed anymore and it  might very well happen that "eth0" on one boot ends up being "eth1" on  the next. This can have serious security implications, for example in  firewall rules which are coded for certain naming schemes, and which are  hence very sensitive to unpredictable changing names.  

  
To fix this problem multiple solutions have been proposed and  implemented. For a longer time udev shipped support for assigning  permanent "ethX" names to certain interfaces based on their MAC  addresses. This turned out to have a multitude of problems, among them:  this required a writable root directory which is generally not  available; the statelessness of the system is lost as booting an OS  image on a system will result in changed configuration of the image; on  many systems MAC addresses are not actually fixed, such as on a lot of  embedded hardware and particularly on all kinds of virtualization  solutions.  The biggest of all however is that the userspace components  trying to assign the interface name raced against the kernel assigning  new names from the same "ethX" namespace, a race condition with all  kinds of weird effects, among them that assignment of names sometimes  failed. As a result support for this has been removed from systemd/udev a  while back. 

  
Another solution that has been implemented is "biosdevname" which  tries to find fixed slot topology information in certain firmware  interfaces and uses them to assign fixed names to interfaces which  incorporate their physical location on the mainboard. In a way this  naming scheme is similar to what is already done natively in udev for  various device nodes via /dev/*/by-path/ symlinks. In many cases,  biosdevname departs from the low-level kernel device identification  schemes that udev generally uses for these symlinks, and instead invents  its own enumeration schemes. 

  
Finally, many distributions support renaming interfaces to  user-chosen names (think: "internet0", "dmz0", ...) keyed off their MAC  addresses or physical locations as part of their networking scripts.  This is a very good choice but does have the problem that it implies  that the user is willing and capable of choosing and assigning these  names. 

  
We believe it is a good default choice to generalize the scheme  pioneered by "biosdevname". Assigning fixed names based on  firmware/topology/location information has the big advantage that the  names are fully automatic, fully predictable, that they stay fixed even  if hardware is added or removed (i.e. no reenumeration takes place) and  that broken hardware can be replaced seamlessly. That said, they  admittedly are sometimes harder to read than the "eth0" or "wlan0"  everybody is used to. Example: "enp5s0"

---

### Post by chili555 on 2019-12-04
> now I only need to rename the logical name back to what they were and is standard.... How does one do that? Now they have names like enp7s0 and enp8s0
Why? The standard today is predictable interface naming. The standard a few years ago, when I had only a few white hairs, was eth0, eth1, etc.

Is there any reason you can name, other than 'that's the way we've always done it', that eth0 is better than enp7s0?

There is only one thing that you can absolutely count on in computer science: change. The Linux kernel and its wrapper, Ubuntu, are changing every day. I recommend that you embrace it.

---

### Post by crazybear on 2019-12-06
I'm sorry to have to report a BIG NEW problem. Everything was working well for several days. Today it was working and on all day....I took a nap and then came back to the computer  [not having been turned off] and noticed there was NO internet. I ran some of the diagnostics and some of the 'fixes' and 'repair' methods listed in this thread. Nothing worked. The computer said my wifi device was down. I rebooted and remembered that a new kernel was installed this morning, so I tried two older kernels. Nothing helped. Now all of my hardware-based network devices are UNCLAIMED. Please help! I'm really confused at how it went from just fine to all messed up again. Today, I was doing mostly word-processing while also sometimes doing internet searches and connecting to various sites.....somewhere in the later part of the day, something went terribly wrong. I was NOT using terminal until AFTER I noticed my wifi device was down.

```

 $ sudo lshw -C network; lsb_release -a; uname -a; sudo iwlist scan | egrep 'chan | sid'
    *-network UNCLAIMED     
         description: Network controller
         product: RTL8812AE 802.11ac PCIe Wireless Network Adapter
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:04:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: ioport:ee00(size=256) memory:fbefc000-fbefffff
    *-network UNCLAIMED
         description: Ethernet controller
         product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:07:00.0
         version: 03
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list
         configuration: latency=0
         resources: ioport:be00(size=256) memory:fbaff000-fbafffff memory:fbaf8000-fbafbfff memory:fbb00000-fbb1ffff
    *-network UNCLAIMED
         description: Ethernet controller
         product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:08:00.0
         version: 03
         width: 64 bits
         clock: 33MHz
         capabilities: pm msi pciexpress msix vpd bus_master cap_list
         configuration: latency=0
         resources: ioport:ae00(size=256) memory:fb8ff000-fb8fffff memory:fb8f8000-fb8fbfff memory:fb900000-fb91ffff
    *-network DISABLED
         description: Ethernet interface
         physical id: 1
         logical name: virbr0-nic
         serial: 52:54:00:2b:2f:a7
         size: 10Mbit/s
         capabilities: ethernet physical
         configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  LSB Version:   core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
  Distributor ID: Ubuntu
  Description:     Ubuntu 16.04.6 LTS
  Release:           16.04
  Codename:      xenial
  Linux GA-X58A-UD7 4.13.0-45-generic #50~16.04.1-Ubuntu SMP Wed May 30 11:18:27 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
  lo        Interface doesn't support scanning.
   
  virbr0-nic  Interface doesn't support scanning.
   
  virbr0    Interface doesn't support scanning.
  
```

---

### Post by crazybear on 2019-12-07
OK, I ran 

```

sudo sed -i 's/blacklist r8169/#blacklist r8169/' /etc/modprobe.d/blacklist.conf


``` again, rebooted [had forgotten that was necessary when I panicked], and all are claimed again and I have internet again.
My question, however, is why did that happen and if it was the addition of a new kernel? They come regularly. Will I have to do this each time I get and install a new one?...and I still have to go to terminal each time
and tell the computer to look for the repeater's SSID to connect [sometimes more than just at the beginning of a session] - as I have NO network manager. It is shown as installed, but I can not find it nor get it to open using terminal..... So, I have a 'solution', but not a good nor easy one. Thanks.

---

### Post by jeremy31 on 2019-12-08
I am not familiar with that DE you are using so I cannot help much with network manager.  The blacklist was the result of commands you ran back early in this topic and somehow the replacement driver disappeared and the kernel module was still blacklisted resulting in unclaimed status

---

