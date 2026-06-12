---
title: "Please could someone tell me the relationship of these"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2006-09-13
Im going crazy with the whole wireless fiasco with ubuntu. Ive had loads of challenges getting hardware to work on it, most have been a fun challenge and great when sussed.

But.

Wireless is just depressing as there appears to be no standard and is a total minefield of terms and 'do this but dont do that' 'this doesnt work with this' 'this breaks that' etc.

Ive got a wireless belkin G 7010 **which i can successfully use from the default gnome network setings with either none or wep.** This works great and detects either wired or wireless

But... i need wpa-psk, as my annoying windows machine doesnt like wep.

Ive read a million guides and they all seem to use terms but never explain what they are or how they relate to each other.

so far im up to my eyes in the following terms and have no idea how they effect each other:
[B]
heres what ive managed to figure out (i think):[/B]
1) Standard /etc/network/interfaces  (accessable from the gnome admin menu) this is the standard ubuntu network card setup with everything but WPA-PSK

2) Network manager, im assuming is a total replacement for the above? and only works if no 1 is disabled. (if so, where are the WPA options otherwise whats the point?) 

3) Ndiswrapper, sussed this out, its wrapper 4 windows driver and effects all

**now it gets real confusing:**
4) WPAsupplicant Im guessing this tells something else to use a different protocol but which one? 1,2 or 3?!? (why this cant be an option when connecting in network manager is beyond me!)

4) Madwifi keeps cropping up in guides but havent a clue what this is

5) wifiradar same as above, do these effect 1 or 2 or are they separate again?

etc.etc.etc.

It seems incredible to me that Ubuntu powerful as it is, seems a real mission to set up something as simple as telling a card to use a protocol

---

### Post by wieman01 on 2006-09-13
I try to answer some of your questions... Feel free to challenge me.

A. "/etc/network/interfaces" indeed controls your network (unless you are using a tool called "NetworkManager" and even handles WPA-PSK if you have "wpa_supplicant" installed. But most people decide to outsource the service and handle WPA-PSK in a separate file. But in principle it is possible:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

B. NDiswrapper is not your driver but a Linux container for your native Windows driver. That's different, but we are on the same page.

C. "wpa_suppliant" is only required if you need WPA(2).

D. Madwifi is a Linux driver for Madwifi wireless adapters. In contrast to a NDiswrapper solution you don't employ your native Windows driver. There are other Linux driver next to this one (e.g. Atheros). Simply depends on what adapter you are using.

E. Wifiradar can be used for for various network protocols. I am not very familiar with it, but it does have an impact (or makes use of) 1. I remember you cannot use it together with NetworkManager.

F. NetworkManager has certain constraints: It can handle DHCP only (no assignment of static IPs), you need to broadcast your ESSID (does not work with hidden ones), and I think it does not connect to unsecured networks after the latest update.

What other questions are there? Happy to discuss! And I agree: Wireless support under Linux sucks quite a bit. Very immature.

---

### Post by dgrafix on 2006-09-13
Ok, thx for the informative response :)

Sounds like all i need to do then is to configure the standard interface bit to accept wpa-psk, and dump network manager altogether.

Question is, how. Your guide seems to mention requirements i dont understand if i have.

Is wpa2 the same thing as wpa-psk as my router has only 3 options:
None, wep(64&128), wpa-psk (AES & TKIP)

I would use wep, no problem but i cant find out how to enter the key under windows properly(it says you need to specify the type and length as well as cose), or my card no longer supports wep, either way it doesnt work on my windows pc.

---

### Post by dgrafix on 2006-09-13
One more question:

If i simply turn off SSID broadcasts, do i even need encryption as no one will 'see' me unless they know the network name.

Or am i dangerously mistaken

---

### Post by wieman01 on 2006-09-13
My Windows PC's network adapter stopped working after I had installed Linux. So I dropped Windows altogether (good excuse).

WPA2 is the same as WPA with AES. So if you choose WPA-PSK with AES, then my guide will help you. Forget about the mentioned requirements, this solution should work for you as well. WPA2 (AES) is the safest option for wireless network that's avalable at the moment.

My guide also mentions a documentation on wireless security. You will understand the whole concept behind it after reading it.

If you use WEP, you should choose a 128-bit key in a Hexadecimal format, not plain-text (that being the type). Linux supports WEP out of the box, you can use Gnomes standard (wireless) networking tool for it.

If you want to give WPA a go using my posted solution, let me know. Just use either my or your own thread so that I can lead you through the process.

---

### Post by wieman01 on 2006-09-13
> **dgrafix said:**
> One more question:

If i simply turn off SSID broadcasts, do i even need encryption as no one will 'see' me unless they know the network name.

Or am i dangerously mistaken
Yes, not necessarily dangerously mistaken, but mistaken. :-) I would not need the ESSID of your network to break into it. Just the right software/patch to do so (airsnort, aircrack, you name it). Your router is broadcasting its MAC address, that more than sufficient.

So wireless security is crucial. I would not worry about somebody else being able to decrypt your traffic, it's rather somebody taking advantage of your access point and doing nasty stuff through your internet gateway. It's eventually you who is liable.

---

### Post by dgrafix on 2006-09-13
thanks

Ill see how i go with this.

Unfortunately i need my windows pc. 
Im a games designer & graphics person and require DirectX. I keep all my files on a ubuntu server & access from windows via samba.

I use ubuntu for everything officey/webby/emailie though, thats why i want it on my other laptop :)

---

### Post by wieman01 on 2006-09-13
Alright... So wireless security should play an even more important role to protect your files, etc. ;-) Let us know how it goes.

---

### Post by dgrafix on 2006-09-13
I dont think its working yet. Here is my conf but im not sure how i configure this for TKIP or AES

auto lo
iface lo inet loopback
auto ra1
iface ra1 inet static
wpa-driver wext
wpa-conf managed
wpa-ssid DanAirNet
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 1d553b91e7761de6fb80e05fe077accb56161fa05a489f311b6ca877b2f75005
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by wieman01 on 2006-09-13
What's your adapter again? Atheros? You may have to replace "wext":

hostap = Host AP driver (Intersil Prism2/2.5/3)
madwifi = MADWIFI 802.11 support (Atheros, etc.)
atmel = ATMEL AT76C5XXx (USB, PCMCIA)
wext = Linux wireless extensions (generic)
ndiswrapper = Linux ndiswrapper
ipw = Intel ipw2100/2200 driver
wired = wpa_supplicant wired Ethernet driver
test = wpa_supplicant test driver

Have you configured your router accordingly? Also you need to restart your network twice... That's a known bug. Please also post the command you are using to restart the network plus the resulting terminal output.

---

### Post by wieman01 on 2006-09-13
"ra0"... Isn't that Ralink? Forgot... Then "wext" should be fine I guess.

---

### Post by dgrafix on 2006-09-13
mines a ndiswrapped belkin 7010 v3.000DE using bcmwl5a driver. Works fine for wep and none.

---

### Post by wieman01 on 2006-09-13
Ok, then it should be "wext"... Sorry, you have mentioned that. But then "ra0" is not the right interface. NDiswrapper is "wlan0". Could that be your problem?

Outa here for a few hours. I'll continue later today.

---

### Post by tturrisi on 2006-09-13
FYI, there is no such thing as a mad-wifi chipset or a mad-wifi adapter.  Mad-wifi is a linux wlan driver for adapters w/ Atheros based chipsets only.  The interface name will be athX and it also creates a virtual device called wifi0.

Disabling ssid broadcast won't help security too much.  It means that the AP does not broadcast the ssid.  An AP usually sends out the ssid X # of times/second.  But if a client is connected to an AP, the client sends the ssid in each packet, thus the ssid can easily be captured.  The advantage is that if no one is using the wifi then no one else will see the AP UNTIL someone connects to the AP.  Thus the only security is that neighbors w/ wifi cards won't see your AP.

WPA and WEP are both easily crackable, wep easier than wpa.  But less than 2% of Internet users have a clue as to how to crack these encryptions, and less than that will try.

iface ra1 = an adapter w/ a Ralink chipset.

net-admin is the built in networking applet in gnome.
Network-manager is a 3rd party network applet.
As is wifi-radar.

None are capable of using WPA by themselves.

wpa-supplicant is an additional linux package that enable the use of wpa, either with network-manager or manual config.  Net-admin & wifi-radar cannot use wpa at present.

---

### Post by wieman01 on 2006-09-13
Thanks for it, tturrisi. One statement is worth taking a second glance at: WPA is crackable. That is true, however, WPA2 is not by today's means. You're right in that WPA is using TKIP which is a very weak algorithm but since its revision (WPA2) uses AES it is considered safe (quoting):

*"The design and strength of all key lengths of the AES algorithm (i.e., 128, 192 and 256) are sufficient to protect classified information up to the SECRET level. TOP SECRET information will require use of either the 192 or 256 key lengths. The implementation of AES in products intended to protect national security systems and/or information must be reviewed and certified by NSA prior to their acquisition and use."*

---

### Post by dgrafix on 2006-09-13
to wieman
> 
Have you configured your router accordingly? Also you need to restart your network twice... That's a known bug. Please also post the command you are using to restart the network plus the resulting terminal output.

Didnt know there was one ´, i use sudo reboot



to tturrsi
ok now im really confused. :-? 

I tried using network manager and my network appears on the list. when i try to connect though it asks for a WEP128 or WEP64asc or WEP64h. Theres no mention of wpa-psk anywhere

](*,) ](*,)

---

### Post by wieman01 on 2006-09-13
Ah... dgrafix... I am not sure we talk about the same thing to be honest. NetworkManager is a tool that does not come with Gnome/Ubuntu by default, you need to install it separately.

I think you are referring to the normal networking applet which indeed has only WEP as option.

---

### Post by dgrafix on 2006-09-13
where is the text file to manually tell network manager what to do as theres no options on the icon.

---

### Post by wieman01 on 2006-09-13
Here is the restart command for your network:
> sudo /etc/init.d/networking restart
Whenever you restart please do it twice...

---

### Post by bensexson on 2006-09-13
dgrafix if you are using ndiswrapper you should replace wext with ndiswrapper.

---

### Post by dgrafix on 2006-09-13
but that bit before was in the /etc/network/interfaces 
which i thought was for the normal network setup not network manager.

Trouble is, to use network manager, i need DHCP. ive done a test with all cards disabled in /etc/network/interfaces (ex.lo) and turned off all security on router.  Lights on card come on and i can see the network from the dropdown menu in network manager. BUT. when i try and connect it spins for ages then goes back to a ! with no error message or anything. When i check the ip address in network tools its not 192.168.. i dont know what it is as ipv4 not there only ipv6

I dont get this at all, my windows machine gets an ip no probs, and when i want a static one with the normal networking it works fine (but as you say no damn wpa so.. no good).

The problem seems to be with network manager and the need for DHCP.

---

### Post by wieman01 on 2006-09-13
> **bensexson said:**
> dgrafix if you are using ndiswrapper you should replace wext with ndiswrapper.
No, not anymore. Used to be ndiswrapper but this is obsolete. "wext" is the correct one, have been using it for a while. :-)

---

### Post by wieman01 on 2006-09-13
> **dgrafix said:**
> but that bit before was in the /etc/network/interfaces 
which i thought was for the normal network setup not network manager.

Trouble is, to use network manager, i need DHCP. ive done a test with all cards disabled in /etc/network/interfaces (ex.lo) and turned off all security on router.  Lights on card come on and i can see the network from the dropdown menu in network manager. BUT. when i try and connect it spins for ages then goes back to a ! with no error message or anything. When i check the ip address in network tools its not 192.168.. i dont know what it is as ipv4 not there only ipv6

I dont get this at all, my windows machine gets an ip no probs, and when i want a static one with the normal networking it works fine (but as you say no damn wpa so.. no good).

The problem seems to be with network manager and the need for DHCP.
Ok, we are talking about the same thing NetworkManager is supposed to do WPA but I cannot tell you from here what's wrong. But as you have pointed out, it's DHCP only.

So in order to enable your PC to do static IPs, we need to set up your WPA networking using the interfaces file. As you have just tried.

I now wireless networking under Linux is a frustrating business, but don't give up. Give it go... once you have set it up it won't turn you down like Windows does from time to time.

---

### Post by dgrafix on 2006-09-13
Ok, ive just noticed DHCP works ok with this:

auto ra1
iface ra1 inet dhcp

but to use network manager i need to remove this line correct?

where then do i configure network manager to do the same? as it doesnt work at all.

If i can get this working with network manager with no security, at least thats step 1 to getting the wpa working.

---

### Post by wieman01 on 2006-09-13
Ok, if you want to use NetworkManager then remove these two lines. That should do. But make sure you have "wpa_supplicant" installed. Then NetworkManager should give you the WPA(2) option.

If that does not work, then you can always try the other approach we have discussed (interfaces file).

---

### Post by dgrafix on 2006-09-13
> Then NetworkManager should give you the WPA(2) option

I still only have the wep options in network manager.

I cant seem to find any relationship between wpasupplicant and network manager. Dont i need to include it somewhere and configure it with my key etc.

BTW ssid broadcasts are on because if its off, the network doesnt appear in network manager

---

### Post by dgrafix on 2006-09-13
so..  wpa_supplicant effects both 
/etc/network/interfaces and network manager?

---

### Post by dgrafix on 2006-09-13
finally got it working, thanks everyone.

The fault was with network-manager and my ralink card. I was getting confused when many people said you could not use WPA without network manager. This is a very missleading statement.

I eventually got WPA-PSK working (when broadcasting ssid) simply with the following in interfaces file:

auto ra1
iface ra1 inet dhcp
pre-up ifconfig ra1 up
pre-up ifconfig ra1 down
pre-up ifconfig ra1 up
pre-up ifconfig ra1 down
pre-up iwconfig ra1 essid "danswireless"
pre-up iwconfig ra1 mode Managed
pre-up iwpriv ra1 set AuthMode=WPAPSK
pre-up iwpriv ra1 set EncrypType=TKIP
pre-up iwpriv ra1 set WPAPSK="my psk in hex"
pre-up ifconfig ra1 up


Happy man now :)
Thanks to all who helped me today ;)

---

### Post by wieman01 on 2006-09-13
Hello DGrafix, 

Good job. Try to replace TKIP with AES and see how it goes. Will make your network security even better.

---

