---
title: "NetworkManager with hidden ESSID"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by RikoW on 2006-11-01
Dear all,

I have a problem with NetworkManager at work, where the APs don't broadcast their ESSID. At home, where I don't hide the ESSID, there is no problem.

So, here it goes: I'm running NetworkManager on a Dell D600 and really like it, especially the dispatcher feature. However, when I'm at work, the internal wireless network does not show up in the list that the nm-applet provides. I can connect to it without problem using the 'Connect to other wireless networks'. Then it shows in the list. However, next time I reboot the machine and look into the applet, they internal network is gone again from the list. It's a WEP encrypted network, if that makes any difference.

in  *~/.gconf/system/networking/wireless/networks* I find a configuration for the network, but it never shows up. It kind of defeats the purpose of NetworkManager, if you need to configure the same network all the time again.

I googeled already, but didn't find any answer.

Am I completely optimistic to assume, that the network should show up, once it was configured correctly? Is there any solution for that? 
The way it is now, it's useless for me :(

Thanks and cheers,

                  a very frustrated Riko

---

### Post by Jan Hrbacek on 2006-11-01
I have the same problem. 

I am not 100 % sure about it, but I think I have read in some forum that NetworkManager is not there yet. It doesn't remember the setting, so every time you restart you have to go through the GUI and fill all the parameter such in Contact to other Wireless Network...

Another issue is that everytime you also have to fill the password for the keyring. 

All these steps make connection ho hidden ssid a time consuming and rather annoying process...

---

### Post by RikoW on 2006-11-01
> **Jan Hrbacek said:**
> 
I am not 100 % sure about it, but I think I have read in some forum that NetworkManager is not there yet. It doesn't remember the setting, so every time you restart you have to go through the GUI and fill all the parameter such in Contact to other Wireless Network...


I find that hard to believe, but maybe you are right. I would consider that one of THE fundamental functions you would need from an tool like network-manager. At least to your known network, connection should be a piece of cake..


> **Jan Hrbacek said:**
> 

Another issue is that everytime you also have to fill the password for the keyring. 

All these steps make connection ho hidden ssid a time consuming and rather annoying process...

Actually, the keyring password doesn't bother me that much, since it's one that I choose myself and typing it in works blindly.

Cheers,

              Riko

---

### Post by wieman01 on 2006-11-01
Let me confirm that. NetworkManager has 2 drawbacks:

1. No support for hidden ESSID.
2. DHCP only, no static IPs.

Believe or not.

_**EDIT:**_
That's why I dropped NetworkManager entirely & configured my WPA2 network manually.

---

### Post by Jan Hrbacek on 2006-11-01
It supports hidden ssid, it means it connects to hidden ssid, however, it doesn't save and remember the setting.

---

### Post by wieman01 on 2006-11-01
> **Jan Hrbacek said:**
> It supports hidden ssid, it means it connects to hidden ssid, however, it doesn't save and remember the setting.
That's a new one. You must be using Edgy then.

---

### Post by Jan Hrbacek on 2006-11-01
> **wieman01 said:**
> That's a new one. You must be using Edgy then.

Yes I am.
Do you have any idea how to extract from NetworkManager parameters which it calls wpa_supplicant with?

---

### Post by wieman01 on 2006-11-01
No, I don't know the parameters. But am I right in that you want to know how to configure your network outside NetworkManager?

---

### Post by Jan Hrbacek on 2006-11-01
Yes, my problem is that I have only wifi access. I have two linux boxes - FC5 and Ubuntu Edgy. Only FC5 is now sucessfuly connected to internet via NetworkManager.

In order to have access to repositories I need to get my Ubuntu on the net. I tried to install NetworkManager from debian packages that I have downloaded using my 2nd linux box. However, it I didn't make it to work.

Therefore I am trying to make Ubuntu work with wpa_supplicant, because it is included on install CD of Ubuntu 6.10.

So far I was not lucky... If interested, read this, please

[http://www.ubuntuforums.org/showthread.php?t=290414](http://www.ubuntuforums.org/showthread.php?t=290414)

---

### Post by Nobber on 2006-11-01
> **Jan Hrbacek said:**
> Do you have any idea how to extract from NetworkManager parameters which it calls wpa_supplicant with?
You could just get connected via network manager, then do
```
ps ax | grep wpa
```
in a terminal. It should display the running wpa_supplicant process, with parameters (which might include a temporary config file).

---

### Post by BlaY0 on 2006-11-14
...but it doesnt. In NM case wpa_supplicant uses socket file which is filled with NM options/settings.

You can always tail your logs to actually see what's going on and what options/settings NM send to wpa_supplicant. Nearly every daemon or application like wpa_supplicant accept debug or verbose parameter, you just need to poke around where to set it.

---

### Post by LoSt180 on 2007-07-10
bumping this thread because this is my exact problem. Has a fix been figured out?
the threads I've found so far are mainly with troubles getting WPA to work in the first place, and one saying hidden SSID's are pointless :-?

Info: Acer Aspire 3000
Broadcom 4318 working with ndiswrapper/wpasupplicant/NetworkManager
6.10 Edgy


My home network, and 'secret' work connection have hidden SSID's. I see all networks in the same file as the original poster. But I still have to select 'Connect to Another Network' and enter everything manually.

Home and work use WPA2/WPA respectively. Network manager will auto connect to my parents WEP network that does broadcast SSID, as well as various hotel connections. Just not the hidden ones...

---

### Post by Frem on 2007-07-26
I also have this problem. I found a bug report [here,]("https://bugs.launchpad.net/network-manager/+bug/39707") but I don't think there's an official fix out yet.

---

### Post by zmjjmz on 2007-10-21
I can't even connect to the hidden network, much less have it remembered...
using Gutsy on a Macbook, 2nd gen...

---

### Post by Gfy on 2007-11-01
> **zmjjmz said:**
> I can't even connect to the hidden network, much less have it remembered...

I have the same problem. I can only get it to work when I enable the essid broadcasting on my router. (a Belkin F5D6231-4 router with 64bit WEP encryption)
When the essid broadcasting is disabled and I enter the configuration, nm-applet asks for the key, but it never connects.
Using Gutsy on a Medion MD 41300.

---

### Post by lmarr28 on 2007-11-01
> **Gfy said:**
> I have the same problem. I can only get it to work when I enable the essid broadcasting on my router. (a Belkin F5D6231-4 router with 64bit WEP encryption)
When the essid broadcasting is disabled and I enter the configuration, nm-applet asks for the key, but it never connects.
Using Gutsy on a Medion MD 41300.

Same problem here...  I have no problem connecting to wireless networks that broadcast their SSID, but if I try to manually connect to one with a hidden SSID, it will not work.

(IBM ThinkPad T42 w/ fresh Gutsy installed last night.)

---

### Post by Monsuco on 2007-11-01
I am unable to get network manager to connect to anything with a hidden ESSID. I am using Ubuntu 7.10 with all updates, a natively supported Ralink card, and Network Manager. Isn't there some command line way to connect to a hidden network if NM will not cooperate? I simply must be able to access this Wifi network. It seems to run fine on Windows, so the network works. On other Wifi tools it appeared to crash as soon as it tried to obtain an IP. Any way to connect would be splendid.

---

### Post by wieman01 on 2007-11-01
NetworkManager does connect to networks with SSID broadcast disabled. This has not been an issue at least since Feisty. But no idea why you guys cannot connect.

---

### Post by Monsuco on 2007-11-01
Well, if it does, then how do I do it?

---

### Post by kevdog on 2007-11-01
If you guys do 
iwlist scan
at command line, do the hidden essid's show up at all?

If they dont, can you connect manually to a hidden essid unencrypted network?? (If you dont know how to connect manually, instructions are in my signature).  Can you connected to a hidden essid with wpa?

---

### Post by wieman01 on 2007-11-02
You can to so by using the "Connect to other network" option. Just right-click on NM and select it. Then enter the network's name and key (for encryption).

---

### Post by Gfy on 2007-11-02
> **wieman01 said:**
> You can to so by using the "Connect to other network" option. Just right-click on NM and select it. Then enter the network's name and key (for encryption).

If I remember correctly, the signal strength showed 0% and it asked met to enter the key again, and again,...
After enabling the essid it worked just fine. I have no problems connecting a WPA protected AP. (with essid showing).

---

### Post by lmarr28 on 2007-11-02
> **Gfy said:**
> If I remember correctly, the signal strength showed 0% and it asked met to enter the key again, and again,...
After enabling the essid it worked just fine. I have no problems connecting a WPA protected AP. (with essid showing).

I tried this on my ThinkPad T42 again last night...

(1)  I am able to connect to my neighbor's un-hidden, unencrypted network with no problems.

(2)  If I try to switch to my own wireless network (which has the SSID hidden and uses WPA-PSK encryption) by manually typing the SSID and pass key into Network Manager's "manual configuration", it will not connect.  When I look in the system logs (I forget which section it was in), I see something about no DHCP addresses being offered and my wireless adapter has decided to use some strange IP address (I don't remember it off the top of my head, and I'm at work so I can't look for it at the moment, it wasn't on any network though).

(3)  If I change my router's settings to broadcast its SSID (and make no other changes), I can successfully connect to my home wireless network.  When I look in the system logs, I can see that my wireless adapter accepted a DHCP address of 192.168.1.110 from my router and it had updated my system time with the Ubuntu NTP server.

:confused:

---

### Post by zmjjmz on 2007-11-02
> **kevdog said:**
> If you guys do 
iwlist scan
at command line, do the hidden essid's show up at all?

If they dont, can you connect manually to a hidden essid unencrypted network?? (If you dont know how to connect manually, instructions are in my signature).  Can you connected to a hidden essid with wpa?
I get an ESSID " " after running 
iwlist scan
along with my others...
I'm assuming that this is the hidden one, as It's the only one NM doesn't pick up...

---

### Post by elVince on 2007-11-03
I'm having the same problem. I cant seem to connect to my wireless network if I hide its SSID. I can connect to it fine if I dont....


Anyone know a solution? I'll be reinstalling XP until I find a solution for this particular box

---

### Post by zackf on 2007-11-04
I can "manually set up a connection" but Network Mananger will not remember these settings upon reboot. It looks like this is still an issue, I will continue to look for a solution and let anyone know if it's out there

---

### Post by Uncle Mort on 2007-11-07
Just to confirm much the same.  Running 7.10 off Live CD having never got 6.10 or 7.04 to connect via wireless with WPA.  

Today's problem:  With ESSID Hidden and WPA-PSK set with TKIP, NM gets part the way through the process and seems to time out and fail.

Do the same with ESSID broadcasting but still with WPA-PSK, and it connects nicely.  Go to the router and change the ESSID to hidden and it all goes to rats - here's a bit of log if it's any help:

Nov  7 22:16:44 ubuntu NetworkManager: <info>  Disconnected. 
Nov  7 22:16:44 ubuntu NetworkManager: <info>  SUP: sending command 'DISABLE_NETWORK 0' 
Nov  7 22:16:44 ubuntu dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 8739
Nov  7 22:16:44 ubuntu dhclient: killed old client process, removed PID file
Nov  7 22:16:44 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov  7 22:16:44 ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 0' 
Nov  7 22:16:44 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov  7 22:16:44 ubuntu NetworkManager: <info>  SUP: sending command 'TERMINATE' 
Nov  7 22:16:44 ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Nov  7 22:16:44 ubuntu avahi-daemon[8266]: Interface wlan0.IPv4 no longer relevant for mDNS.
Nov  7 22:16:44 ubuntu avahi-daemon[8266]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Nov  7 22:16:44 ubuntu avahi-daemon[8266]: Withdrawing address record for [*address obfuscated*] on wlan0.
Nov  7 22:16:44 ubuntu avahi-daemon[8266]: Withdrawing address record for 192.168.1.101 on wlan0.
Nov  7 22:16:44 ubuntu dhclient: wmaster0: unknown hardware address type 801
Nov  7 22:16:44 ubuntu dhclient: wmaster0: unknown hardware address type 801
Nov  7 22:16:44 ubuntu dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Nov  7 22:16:44 ubuntu dhclient: send_packet: Network is unreachable
Nov  7 22:16:44 ubuntu dhclient: send_packet: please consult README file regarding broadcast address.

I went to the other room where there router is and set the ESSID back to Broadcast via XP m/c, and by the time I got back to the Ubuntu m/c it had picked up the network again unprompted.

I can do a more scientific capture of logs if anyone want them (but NB that I am a novice) but I'm off to bed now, so it'll have to wait until tomorrow!

---

### Post by zackf on 2007-11-08
I did get it working with WPA Supplicant with some help on the forums. In my case this is a really old laptop I was just putting together for my son to use at home, seems like a great solution for my needs, but it'd not work as well on a roaming laptop.

---

### Post by zmjjmz on 2007-11-08
zackf,
Could you point us the that thread(s)?
I'd really like to be able to get mine working...

---

### Post by Laervian on 2007-11-09
Hi everyone...I am having myself some problems with a wireless network having a hidden SSID. I have to connect to a WPA2 network, EAP method: PEAP, key type: Dynamic WEP, phase 2 type: MSCHAPV2, and specifying a certificate. I can do this finely both with nm-applet and knetworkmanager (after some experiments, as I had no support in this from the administrators sadly, they advise to use the cl with wpa-supplicant).

I now can connect fine. There is but one little problem: as the network is hidden, it does not show up automatically and nm-applet therefore does not see it - meaning that every time I have to reenter the required information. It is cumbersome and tiring to say the least as an approach. Windows Vista can connect without any problems, while I know that some Win XP machines have had problems (losing the configuration settings).

I have already tried to modify the /etc/wpa-supplicant/functions.sh file (changing the AP SCAN from 0 to 1 and 2) and to modify the configuration using gconf-editor or editing the ~/.kde/share/config/kentworkmanagerrc file (also needed in this case since the GUI is more stupid than that of GNOME and thinks there is no need for a certificate, so I have to specify the path manually in the config file). If someone had any idea on how to enable auto-detection and connection to this network I would be grateful...no hope I can get the administrators to have the SSID broadcast... (which would solve the problem in a second).

Thanks for the support.

---

### Post by dburnett77 on 2007-11-09
In your interface section of
/etc/...network/ 
you need to enable "radio_state=(1 or 2)", depending on your config.

Could also download WiCD.  Handles hidden networks well.

---

### Post by WhyWontThisWork on 2008-01-06
what is that radiostate value based on?

---

### Post by wieman01 on 2008-01-07
I used to be much in favor of wireless networks that do not broadcast the SSID although that does not add any extra security. Even worse, it is an extra risk. Read this for more:

> [http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx](http://blogs.technet.com/steriley/archive/2007/10/16/myth-vs-reality-wireless-ssids.aspx)

All in all, don't hide SSID's but have broadcast enabled.

_**EDIT:**_
Read this as well: [http://www.microsoft.com/technet/network/wifi/hiddennet.mspx]("http://www.microsoft.com/technet/network/wifi/hiddennet.mspx")

---

### Post by zackf on 2008-01-07
Although I agree with non-broadcasting as a security measure, sometimes not broadcasting has others roles. For instance we have a corporate network and provide free public wifi. In lobby areas I broacast the free SSID and hide the corprate to prevent confusion amoung guests. Again, at home I don't broadcast - not for security, but so neighbors stop asking to use it! (Imagine the nerve ;-). I figure if they're able to detect the hidden SSID they're smart enough to have their own wireless network.

That's not to say there aren't issues though, I would recommend doing this only for networks where people connect some of the time with laptops. Having things like wireless printers with a Hidden SSID has caused me problems in the past. And as we can see here, Linux has it's fair share of issues with Hidden SSID's as well.

---

### Post by wieman01 on 2008-01-07
> **zackf said:**
> And as we can see here, Linux has it's fair share of issues with Hidden SSID's as well.
Apparently for good reasons as I had to learn. :-)

---

### Post by WhyWontThisWork on 2008-01-12
so then theres no resolution?

---

### Post by wieman01 on 2008-01-13
> **WhyWontThisWork said:**
> so then theres no resolution?
Turn on broadcast, that's all. Don't hide your network's SSID. That's not a solution, but a conclusion.

---

### Post by Xsabre on 2008-01-14
Thanks for this insightful information. I did a clean installation of Xubuntu 7.10 over the weekend and I was pounding my head into the wall for 2 days trying to figure out why I was not able to connect to my router. 

I had forgot that my router was originally setup with Broadcasting off. Once I set it to broadcast things just seem to fall into place. 

Now on to how to get the keyring to automatically connect without having to enter the password every time.

Thanks again...

---

### Post by jpconard on 2008-01-30
Anything new on this front?  I'm a newbie using Freespire, which has KDE 3.5.6 and Knetworkmanager 0.1.  Is the 0.2 version any better?

I'd just as soon not broadcast my SSID (I know it isn't really security), but it will prevent most of my neighbors from knowing my network exists.

What I find strange is if I choose to not use Knetworkmanager and just configure the network in Control Center (is this directly in network manager I assume), then it can be setup to reconnect to the hidden SSID network on re-boot.  Even after suspend/resume (although I had to put "networking" in the stop services section of the acpi-support file).

So if it can work directly in network manager, why can't it work in knetworkmanager?  Isn't knetworkmanager just a front end for network manager?

Why do I want knetworkmanager to work?  Because it allows me to see multiple wireless networks easily and change between them (like windows).  The network manager in the control center is very basic (OK if you are always on one network only, I suppose.)

---

