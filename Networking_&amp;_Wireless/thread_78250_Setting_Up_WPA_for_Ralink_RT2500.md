---
title: "Setting Up WPA for Ralink RT2500"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by MeijUbuntu on 2005-10-18
Hello,

I have installed a clean breezy and it looks like it detected my RT2500 (Linksys) wireless device. It is available in the device database and under network it shows the the device although it's not activated.

I did not try anything yet, because i hope someone can tell me what the best way is to set this RT2500 up for use with WPA (i am using WPA-PSK).

Do i need wpa_supplicant to set up WPA?
If so, which driver i will select?
Do i need to activate the RT2500 from network settings (gnome) ?

Please help me.

---

### Post by MeijUbuntu on 2005-10-20
Please, has someone a working rt2500 wireless device with WPA?

Please submit your howto so we all can benefit from it.

Thnx

---

### Post by firecat53 on 2005-10-20
I can't speak to your specific card, but.....
  1. Get the card working without WPA first (WEP and/or unencryped). If you can't change the network from WPA, go find one somewhere(library, coffee shop) to test on. It's hard enough to get wireless working sometimes without adding the wpa in the mix!!

  2. Using wpa_supplicant does require some command line work. No gui yet, that I'm aware of. There are numerous tutorials floating around on these forums and elsewhere that cover the basics of setting up wpa. Once you're card is working, there's really nothing that's specific to your wireless card when you set up wpa_supplicant, except perhaps some tweaks to the configuration file.

Good luck!

Scott

---

### Post by jhong on 2005-10-20
My linksys card works perfectly with WPA-PSK using the rt2500 driver, i'm at work now, will post my config tonight.

Q: Do i need wpa_supplicant to set up WPA?
A: No, the rt2500 driver itself supports WPA
Q: Do i need to activate the RT2500 from network settings (gnome) ?
A: Yes, but you need to make some changes to /etc/network/interfaces first

---

### Post by MeijUbuntu on 2005-10-20
It's working !!!!! Yeah it's working.

Somehow there is a default rt2500 installed (which comes along with Breezy) which is not very good. According to the howto (wiki ubuntu) you copy the file to the directory wireless directory. 

But that's wrong. You have to copy it to the directory rt2500 within the wireless directory. (overwriting the breezy default) !!

And bang, Raconfig2500 is working and now after a reboot everytjing is well.

Thnx a lot all. Now i really don't need Windows anymore.

---

### Post by jhong on 2005-10-20
[QUOTE=MeijUbuntu]It's working !!!!! Yeah it's working.

Somehow there is a default rt2500 installed (which comes along with Breezy) which is not very good. According to the howto (wiki ubuntu) you copy the file to the directory wireless directory. 

But that's wrong. You have to copy it to the directory rt2500 within the wireless directory. (overwriting the breezy default) !!

And bang, Raconfig2500 is working and now after a reboot everytjing is well.

Thnx a lot all. Now i really don't need Windows anymore.[/QUOTE]

Congratulations!  RaConfig never worked for me, I tried changing the /etc/Wireless/...  config file manually... not working either, i deleted RaConfig (as well as QT) and ran a few commands randomly, all of a sudden it worked!  I then got all the commands from bash_history and put them in the interfaces script, rebooted my box, my WMP54G started working with WPA!! :D  Here's what i have in /etc/network/interfaces

iface ra0 inet dhcp
    pre-up iwconfig ra0 essid ***YOUR-SSID***
    pre-up iwconfig ra0 mode managed
    pre-up iwpriv ra0 set Channel=11
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=AES
    pre-up iwpriv ra0 set WPAPSK="***YOUR-WPA-PSK***"
    pre-up iwpriv ra0 set TxRate=0

---

### Post by Quirky on 2005-10-21
[QUOTE=jhong]Here's what i have in /etc/network/interfaces

```
iface ra0 inet dhcp
    pre-up iwconfig ra0 essid ***YOUR-SSID***
    pre-up iwconfig ra0 mode managed
    pre-up iwpriv ra0 set Channel=11
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwpriv ra0 set EncrypType=AES
    pre-up iwpriv ra0 set WPAPSK="***YOUR-WPA-PSK***"
    pre-up iwpriv ra0 set TxRate=0
```
[/QUOTE]

THANK YOU! This finally did the trick for me :) With TKIP instead of AES.

I have been trying to get WPA working for a week or so now, and this did it. Excellent stuff. The difference seems to be to use pre-up for everything, not set encryption with iwconfig and perhaps TxRate set to 0 (?). If only it was in the wiki... RaConfig and Gnome Network Manager just didn't work for me and seemed to mess each other up as well.

Woo hoo. Now the neighbours can get their own WLAN ;)

---

### Post by jhong on 2005-10-21
[QUOTE=Quirky]THANK YOU! This finally did the trick for me :) With TKIP instead of AES.

I have been trying to get WPA working for a week or so now, and this did it. Excellent stuff. The difference seems to be to use pre-up for everything, not set encryption with iwconfig and perhaps TxRate set to 0 (?). If only it was in the wiki... RaConfig and Gnome Network Manager just didn't work for me and seemed to mess each other up as well.

Woo hoo. Now the neighbours can get their own WLAN ;)[/QUOTE]

Congratulations, i'm now seriously thinking that i should make a HOWTO for configuring WMP54G+WPA on Breezy...  shall i?

---

### Post by bionnaki on 2005-10-21
yes!

---

### Post by bionnaki on 2005-10-22
would your method work with a static IP?

---

### Post by Carbon Copy Man on 2005-11-18
I wouldn't mind another how-to... I'm still having weird problems with my wireless...

I followed the Wiki tutorial, but once I got into RaConfig, I found that the connection would just come and go... Kind of like it was connecting but not logging in.

Is this a normal problem with RaConfig?

I just tried going to /etc/network/interfaces and editing it like you say, but it didn't seem to have any effect whatsoever on anything.

---

### Post by eMiles on 2005-11-21
Hello everybodies.

i am new on Ubuntu and i have a problem to connect my WPA with my card RT2500!

@MeijUbuntu OR OTHERS

could you explain exactly the best way to configure ??? (if we need Raconfig or not, need nsdiswrapper or not,.... etc)

thanks in advance for your help

PS:  i can see my pci card and i can connect it with only WEP, not Wpa!

---

### Post by polo_step on 2005-11-24
Interesting thread!

I just got a notebook with an internal RaLink rt2500 wireless thingy and have AES/WPA2 wireless here.  I'm having troubles with 5.10 Live, but if I ever install Ubuntu on this box, the above info should certainly come in handy!

---

### Post by eMiles on 2005-11-26
Up ???

---

### Post by devj on 2005-11-28
Xiexie ni jhong! 

I had been wrestling with this a few days before I came across this thread, your information and solution was spot on.  I am using a Linksys wireless card to connect to a Linksys wireless router WRT54G using WPA-PSK.

---

### Post by MeijUbuntu on 2005-12-01
[QUOTE=eMiles]Hello everybodies.

i am new on Ubuntu and i have a problem to connect my WPA with my card RT2500!

@MeijUbuntu OR OTHERS

could you explain exactly the best way to configure ??? (if we need Raconfig or not, need nsdiswrapper or not,.... etc)

thanks in advance for your help

PS:  i can see my pci card and i can connect it with only WEP, not Wpa![/QUOTE]

Hello Emiles,

Sorry for the late messages.
For me the Raconfig is working fine, but i will try the other solution also.
I noticed there is another solution suggested in the Howto.

SO please wait a few days and i will report my howto.

---

### Post by eMiles on 2005-12-04
[QUOTE=MeijUbuntu]Hello Emiles,

Sorry for the late messages.
For me the Raconfig is working fine, but i will try the other solution also.
I noticed there is another solution suggested in the Howto.

SO please wait a few days and i will report my howto.[/QUOTE]


Hi

oh thank you very much if you can help me and us!!
i'm waiting for your comments and solution!!!
no problem

---

### Post by eMiles on 2005-12-11
@MeijUbuntu

Up please..

---

### Post by law1213 on 2005-12-20
Hey guys,

You say the rt2500 works almost out of the box. I would like to know whether the same is true for the 64bit version of ubuntu, since that seems to have fewer packages do you still get the rt2500 module. If anyone has an experience I'd he glad to here it.

Cheers.

---

### Post by jago25_98 on 2006-01-15
What package is the rt2500 kernel module in? 

It's supposed to be included with Breezy but it's not in my 2.6.10-k7 kernel. It's not in 2.6.15 from kernel.org and I can't get it to compile from source.

Worst still the rt2500 source has overwritten my /etc/modules.conf!

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo/)

---

### Post by geek.de.nz on 2006-07-28
Hi, I would like to setup WPA under Linux using a CA (Certificate Authority) to connect to my university wlan.

The wlan has the following properties:

Network Authentication: WPA
Data encryption:        TKIP

EAP type select Protected EAP (PEAP)

Secured password (EAP-MSCHAP v2)

select Thawte Server CA from the list of Trusted Root Certification Authority

(more info under [http://wireless.massey.ac.nz]("http://wireless.massey.ac.nz/") )

I looked into setting up WPA and could find quite some information, but I'm stuck on how to use a CA to connect to a network providing my Student credentials. If anyone has any ideas, it would really be appreciated because my wireless seems to be working more reliable with linux (kubuntu 6.06).

My kernel: 2.6.17.3-pcmcia-h (suspend2 support). Wireless works like a breeze without encryption. For my home network I'm happy without encryption (MAC address filter), but my university requires more security unfortunately.

Thanks in advance.

---

### Post by bleachlizard on 2006-08-08
Man, wish I could figure out this frickin rt2500... I've been trying to setup my wireless and my Radeon for Breezy for months now.  Wish I could help, I got another thread about this issue.  I'll keep everyone posted if someone gives me some useful info.

Oh yeah, and did I mention my college doesn't give anyone the encryption type... so I had to email all over the place in Information Services to flippin get an answer from someone because no one knew apparently.

---

### Post by sagarhshah on 2006-11-19
mr jhong,

you are the man,countless hours spent trying howtos and downloading raconfigs etc and all I could have done was seen your post and made the little edit about the txrate :)


now I can get rid of windows on my hard drive and just run it in vmware :) (unfortunately my university requires us to use a windows based application development environment [visual studio] so I can't get rid of it completely but atleast I can be assured that windows can only messup inside vmware and not break my machine)

:D
thanks man

Did I mention downloads seem so much faster using wireless on linux then on windows :)

---

### Post by Pollywoggy on 2007-01-14
> **jhong said:**
> Congratulations, i'm now seriously thinking that i should make a HOWTO for configuring WMP54G+WPA on Breezy...  shall i?

Nothing worked for me until I found this thread.  I have it working on Edgy now.

I would like to be able to use WEP too but have not been able to get it to work.
Any good howto's?

thanks


BTW I knew this card had to work in Ubuntu because I used it in Linspire right 'out of the box'.

---

### Post by Rich43 on 2007-04-15
PLEASE help me get this fix into network-manager.. I dont want to have to do this.. I want network manager to do it for me.. this is bad for Ubunu's user friendly image!

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/106874](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/106874)

---

### Post by smo0th on 2007-04-16
Hi everyone, this is the first time I am running on linux and ubuntu rox :D 

I had the same common problem with the rt2500 chipset and tried everything in this post and some others and finally after 2 days I realized that** the problem was in duplicate dns** so be careful not to duplicate your dns, how can you be sure?

1. ping 192.168.1.1 [COLOR="Blue"][if it replies it's good news][/COLOR]

2. sudo gedit /etc/network/interfaces
[COLOR="Blue"]Here you should have something like this:[/COLOR]

 auto ra0
iface ra0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "yournetwork" [COLOR="Blue"][don't miss the ""][/COLOR]
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="hex code of your network key" [COLOR="Blue"][don't miss the ""][/COLOR]
pre-up ifconfig ra0 up

[COLOR="Blue"]Be sure that you are not declaring any dns in this code[/COLOR]

3. sudo nano /etc/resolv.conf [[COLOR="Blue"]here you must have the IP addresses from your DNS servers][/COLOR]

[COLOR="Blue"]You should have your primary and secondary DNS servers here:[/COLOR]

111.222.111.222
222.111.222.111

[COLOR="Blue"]If you don't have your DNS servers here, type them, save and close.[/COLOR]

4. sudo /etc/init.d/networking restart [COLOR="Blue"][restart network connections][/COLOR]

Hope this helps :wink: 

:guitar:

---

### Post by narvus on 2007-04-16
Hi, by doing all this you say... won't I get in bigger troubles? I mean, will I have any problem with my wired connection?

When I edit /etc/network/interfaces... all I have to do is to add the lines refering to the wireless connection, the rest of the lines stay the same, no?

Thank you in advance:D

---

### Post by smo0th on 2007-04-18
Of course the rest of your configuration remains the same, you just have to add those lines to configure your wireless connection.

:popcorn:

---

### Post by wilderness wanderer on 2007-04-20
My 2 cents:

rt2500 pci card worked fine under Edgy. Upgraded via alt CD and no network. Numerous attempts at getting network manager to sort it out failed. I uninstalled network manager and it still will not connect via the Gnome network GUI. Note that this is with WEP encryption.

I _am_ able to connect via the command line:

sudo ifconfig ra0 down
sudo iwconfig ra0 essid blahblahblah key hexblahblah
sudo dhclient ra0

I found this at [https://bugs.launchpad.net/ubuntu/+s....20/+bug/37120](https://bugs.launchpad.net/ubuntu/+s....20/+bug/37120)

Syntax to manually configure in /etc/network/interfaces

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "MyRouterName"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="MySecretPassword
pre-up ifconfig ra0 up
auto ra0

Since I am only using WEP, modified to:

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "MyRouterName"
pre-up iwconfig ra0 key "MyKeyInHex"
pre-up iwconfig ra0 mode Managed
pre-up ifconfig ra0 up
auto ra0

Now I have wireless connectivity which survives a reboot.

---

