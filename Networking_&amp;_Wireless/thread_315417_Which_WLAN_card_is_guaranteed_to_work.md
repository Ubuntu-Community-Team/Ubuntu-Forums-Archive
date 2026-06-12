---
title: "Which WLAN card is guaranteed to work?"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by johann_p on 2006-12-09
After spending hours and hours trying to get my Netgear WG311V3 wireless lan card to work (which was a matter of three minutes under WindowsXP) and getting no success so far, I am frustrated enough to essentially throw away the card and replace it with one that is certain to work under Ubuntu.
(See my unsuccessful attempt, despite the help of kind and helpful users, here: [http://ubuntuforums.org/showthread.php?t=314854](http://ubuntuforums.org/showthread.php?t=314854))

So, I would like to know, which brands or products exist that are officially supported (by the vendor) to work under Edgy? Am really sick and tired of compiling ndiswrapper, trying contradicting recipes in countless howtos etc just the get rewarded with an error message. Maybe it works of you or for him, but, alas, for some strange reason it does not work for me.

I want some product which I place in my computer, boot Ubuntu, configure my WPA-PSK passphrase and just *USE*. 
Which hardware would work like this under Edgy?

---

### Post by FrodoB on 2006-12-09
I am not the person to answer the WPA-PSK issue, but the Atheros devices are supposed to do it. If you want to test any card, you should test it with no security or WEP, because WPA-PSK configuration is not a GUI driven affair in Ubuntu or any other Linux that I have used.

For PCI the best bet for, works out of the box, is an Atheros based card.

Usually something that says 108Mbps, or better yet contains the Atheros or Atheros Super-G name on it.

Here are some example Atheros devices:

DWL-G510: (Atheros)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368)

DWL-G520: (Atheros)
[http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869](http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869)


Netgear WG311T: (Atheros)
[http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx](http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx)
[http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=1-1/qid=1165670769/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics](http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=1-1/qid=1165670769/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics)
[http://www.newegg.com/Product/Product.asp?Item=N82E16833122134](http://www.newegg.com/Product/Product.asp?Item=N82E16833122134)


D-Link DWL-G650: (Atheros)
[http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6](http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367)


If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.

Warning! Atheros USB devices do not just work in Linux. For USB devices there are not a lot of works out of the box cards that I can recommend, but there are several good ones if you are willing to compile drivers. Here are devices that I have tested myself with good results:


USB Devices:

Zonet ZEW2500P works out of the box. This device is about $25 at NewEgg:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833130111](http://www.newegg.com/Product/Product.asp?Item=N82E16833130111)

It does have a slow startup, it takes about 12-15 seconds for the device to start working after a bootup or insertion of the device in Edgy. I suspose it is dowloading and starting firmware.

It uses a Ralink rt2570 series chipset and kernel module.

It works well with WEP, I cannot comment upon WPA as I have not yet tried it.

---

### Post by jmcwb on 2006-12-09
I have tried WPA-PSK passphrase for years with my Netgear WG511 without success.  Until linux truely supports WPA-PSK without all the trial and error it will never make it as a true desktop replacement.  Hence unless you are network hacker, no WLAN card can be guaranteed to work on any flavor of linux, and I've tried many - ubuntu, fedora, mandrake (-riva) knoppix, xandros, centos, redhat...)

---

### Post by K.B. on 2006-12-09
I'll second this question--  I've been trying to get a D-Link DWL-650 to work with Edgy ( [http://www.ubuntuforums.org/showthread.php?t=296179]("http://www.ubuntuforums.org/showthread.php?t=296179")) with no success and am about ready to just toss the card in the garbage.

What card works with Ubuntu and with WEP? Is there any?

---

### Post by FrodoB on 2006-12-09
I believe that there is a bug in Edgy with respect to the prism chipset. If you try a Dapper setup it may just work.  Run Dapper as a Live CD and see if you can configure the device.

If you really want to get a different card go with the D-Link PC Card, which is a DWL-G650 in my post above.

Let us know how Dapper goes, it may solve your issue.

If you are using an Atheros card as in my post above most wireless issues in Linux become a lot easier. For Linux, wireless is a matter of finding a device with a well supported chipset.

> **K.B. said:**
> I'll second this question--  I've been trying to get a D-Link DWL-650 to work with Edgy ( [http://www.ubuntuforums.org/showthread.php?t=296179](http://www.ubuntuforums.org/showthread.php?t=296179)) with no success and am about ready to just toss the card in the garbage.

What card works with Ubuntu and with WEP? Is there any?

---

### Post by johann_p on 2006-12-09
Hmm -- when I look at all these products, I either see "Windows XP" and sometimes "Windows 2000" listed in the system requirements (no other OS anywhere), or this is not mentioned, but from the other instructions or manuals, it is obvious that the only OS they are talking about is Windows.

Moreover, as I said, WPA-PSK is ABSOLUTELY essential to work. There is currently no alternative in secure Wlan communication and other computers on the network I want to use rely on it.

So, it essentially looks as if what I want does not really exist. Not a single vendor guarantees the card to work with Linux, in a way that it is guaranteed to work with Windows.

I do not want to rely on exemplary evidence from others that it *might* work. Others have said they got the NETGEAR WP311V4 card to work -- I didnt. 

I have to agree -- unless something changes with issues like this (or with using certain ink printers, printer/fax/copier stations etc), Linux will remain an OS for people who either do not need to operate that hardware or are enough of a technician and hacker to finally, somehow, get things to work.

That is quite sad and frustrating.

---

### Post by FrodoB on 2006-12-09
Well, it is an OS that has weak support from the device vendors, particularly in the Wireless area at the moment.  

Microsoft does not write drivers for the wireless chipset supplier's devices, the wireless suppliers do that for Microsoft in order to be able to sell their wares.  

These suppliers do not support Apple OS-X, or any other flavor of UNIX to the extent that they support Window, as the numbers do not justify the investment for them. The also want to have non-disclosure agreements with the device manufacturers and this is not compatible with a compile from source OS like Linux.

Wireless is an area in Linux that ebbs and flows with the release of new chipsets from the suppliers and the device suppliers like D-Link and Linksys keep changing the chipsets that they use in cards with the same model name.  

This is not going to change, so folks who want to use Linux on existing machines, have to do investigation before jumping out and buying a wireless device.  There was a time when this was true of other devices in the computers, but the market forces have eliminated the weak players so compatibility is not so much of an issue any longer.

also, this is in reality not just a Linux/UNIX problem, if you try to install Windows XP from scratch on new hardware, you will spend hours trying to get the correct drivers to make it work, unless you had the foresight to get them all and burn them to a CD in advance. I have a Dell that will barely work at all with WIndows XP without 1 to 2 hours of driver installs and tweaking. I have Linux machines that are ready to go with Debian or Ubuntu in 15 minutes including wireless.

I also have a Belkin F5D7050 ver 3000 that performs better out of the box on Linux than it does on Windows XP using the latest drivers from Microsoft or Ralink. But I don't run WPA-PSK even on Windows so my experience is not relevant to your goals.

There are of course a lot of devices out there that will do what you want, but you will have to do research before spending your money or you will be disappointed.

The Atheros devices do work well with wpasupplicant, so you should be able to research the Atheros devices and find good recipes  for  configuring then  with WPA-PSK. 

From my point of view the only thing that you are gaining with WPA-PSK is that it is less likely that someone can steal your bandwidth.  

Incidentally, you are no less secure using WEP when making a purchase on-line than your are in using wired ethernet as your browser is providing the secure link to the seller.  I just turn my access point off when I am not using it and make myself an unreliable supplier of bandwidth and besides, there are still people running with no encryption so why waste time breaking my WEP key.

If I lived in an apartment and people were using all of my bandwidth I would be more concerned I suppose.

---

### Post by FrodoB on 2006-12-09
I have never used this, but the instrucions look clear and the comments by visitors to the site would lead one to believe that this gentleman has a relatively  solid grasp of the WPA-PSK issue.  And the Atheros devices do work with wpasupplicant.

---

### Post by FrodoB on 2006-12-09
Johann_p;

Are you saying that you could get your WG311v3 to work with WEP, but not WPA-PSK? If so I believe that I can help you now.  I just got this working on my TRENDnet device using ndiswrapper and wpasupplicant.

FrodoB

---

### Post by FrodoB on 2006-12-09
Once you have a debugged ndiswrapper or mAdWiFi connection using no security or WEP you can then convert to WPA-PSK fairly easily. Just remember to change all references to wlan0 to ath0 for mAdWiFi.

Using WPA-PSK on Ubuntu 6.10 Edgy Eft, with wireless supplied by ndiswrapper:


1) Create a /etc/wpa_supplicant.conf file that contains the following: (make sure that your psk is the same as is in your access point router.)

===================== cut ==========================================================
ctrl_interface=/var/run/wpa_supplicant

ap_scan=2

network={
       ssid="H.M.S. Hood"
       key_mgmt=WPA-PSK
       proto=WPA
       pairwise=TKIP
       group=TKIP       
       psk="vjGRNMaOrREWXAVd1lnI2K2JN203K93TIwF55z99FF5OwkSM5c7i0BnVu7mqiDL"
}

===================== cut ==========================================================

You can make the WPA-PSK passphrases at Gibson Research's Perfect Passwords - GRC's Ultra High Security Password Generator:

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

You must use the same passphrase in your Access Point Router for this to work. Replace my example with your own.



2) Edit the /etc/network/interfaces file and add a record for your wireless device:

sudo gedit /etc/network/interfaces

Add a record similar to this one, replacing your existing wlan0 if any:

===================== cut ==========================================================
auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
wpa-ssid Your_SSID_Name
post-down killall -q wpa_supplicant

===================== cut ==========================================================



3) Reboot your system or use the following command:

sudo /etc/init.d/dbus restart

A complete system reboot can be helpful, so I recommend that.

---

### Post by johann_p on 2006-12-09
Dear FrodoB - thanks for all the support. I am not saying I got it to run with WEP because I cannot modify the router at the moment -- I have to use it as is, with a WPA-PSK.
The reason I think this might be an issue with WPA-PSK is that from the debuggin output of wpa-supplicant, I do get an association with the base station, I do see the correct ssid and mac address, but then there is failure with the key exchange. Since I have double, triple, n-tuple checked the validity of the key, there must be a problem with how that kind of encryption does (not) work in combination with the driver or something.

I might try this again, but somehow I do not have a good feeling anyways, experiencing those slowdowns etc when trying to activate the network.

I think if it really can be expected to work I buy the D-Link G520 card. I'd really spend a couple dozen euros than another couple of hours here :)

---

### Post by jckay on 2006-12-09
Hi all - I'm also trying to get my D-Link DWL-G630 card (atheros) working. Using Synaptic in Ubuntu v6.10 seemed to do the trick (as far as loading the madwifi modules), but yet I still cannot connect to my WLAN. It's an 11g wlan, and I use WPA-PSK for security, but can I get some guidance? Did I just read that WPA is not supported in Linux? Not at all? Never? No way? 

If true, that is a terrible setback to my using Ubuntu or any Linux distro for that matter. 

thx -

---

### Post by johann_p on 2006-12-10
This is getting more and more absurd -- from several web pates it seems that the same products often come in different versions and could contain different chips or modifications, so you can never be really sure if it will work. 
](*,)

---

### Post by FrodoB on 2006-12-10
Post 10 in this thread covers WPA-PSK, it does work.

For the purposes of debugging you should use WEP or no security, once  you have the card working then add WPA-PSK in.  

If you try to do it all at once you can really work too hard on the wrong things.

> **jckay said:**
> Hi all - I'm also trying to get my D-Link DWL-G630 card (atheros) working. Using Synaptic in Ubuntu v6.10 seemed to do the trick (as far as loading the madwifi modules), but yet I still cannot connect to my WLAN. It's an 11g wlan, and I use WPA-PSK for security, but can I get some guidance? Did I just read that WPA is not supported in Linux? Not at all? Never? No way? 

If true, that is a terrible setback to my using Ubuntu or any Linux distro for that matter. 

thx -

---

### Post by FrodoB on 2006-12-10
> **johann_p said:**
> This is getting more and more absurd -- from several web pates it seems that the same products often come in different versions and could contain different chips or modifications, so you can never be really sure if it will work. 
](*,)


What you are saying is true, but finding an Atheros product is not that difficult, just look for 108Mbps, or better yet contains the AirPlus XtremeG, Atheros, or Atheros Super-G name on it. The ones listed in post 2 are good bets. If you find some from a vendor you like you can just post links to them and someone can help you figure out if they are really Atheros devices.

---

### Post by FrodoB on 2006-12-10
I should add that you do not want to get any pre-N devices, most all of them are not yet supported by mAdWiFi for Atheros or others in native drivers.  If those things work at all it will be through ndiswrapper.


Here is the mAdWiFi compatibility list:

[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

---

### Post by dscott60 on 2007-01-22
Hi 

I have this wireless adapter too and I'm running 6.10.  I know this is a stupid, basic question but, what do you mean by "after a bootup or insertion of the device in Edgy?"  I'm brand new to this.  I loaded Ubuntu yesterday, so I don't even know the basics.  

Thanks  


> **FrodoB said:**
> I am not the person to answer the WPA-PSK issue, but the Atheros devices are supposed to do it. If you want to test any card, you should test it with no security or WEP, because WPA-PSK configuration is not a GUI driven affair in Ubuntu or any other Linux that I have used.

For PCI the best bet for, works out of the box, is an Atheros based card.

Usually something that says 108Mbps, or better yet contains the Atheros or Atheros Super-G name on it.

Here are some example Atheros devices:

DWL-G510: (Atheros)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=783131&CatId=368)

DWL-G520: (Atheros)
[http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869](http://www.amazon.com/D-Link-DWL-G520-Wireless-Adapter-802-11g/dp/B00007LTBI/sr=11-1/qid=1165277181/ref=sr_11_1/002-9810405-1660869)


Netgear WG311T: (Atheros)
[http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx](http://www.netgear.com/Products/Adapters/SuperGWirelessAdapters/WG311T.aspx)
[http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=1-1/qid=1165670769/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics](http://www.amazon.com/Netgear-WG311T-Mbps-Wireless-Adapter/dp/B0001N6LCM/sr=1-1/qid=1165670769/ref=pd_bbs_sr_1/002-9810405-1660869?ie=UTF8&s=electronics)
[http://www.newegg.com/Product/Product.asp?Item=N82E16833122134](http://www.newegg.com/Product/Product.asp?Item=N82E16833122134)


D-Link DWL-G650: (Atheros)
[http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6](http://www.amazon.com/D-Link-DWL-G650-Wireless-Cardbus-Adapter/dp/B00007LTB6)
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=485115&CatId=367)


If you see the Atheros advertising or the 108Mbps then you are probably in the right track unless you are buying on line and they are selling multiple chipset versions of the same card model, which happens from time to time.

Warning! Atheros USB devices do not just work in Linux. For USB devices there are not a lot of works out of the box cards that I can recommend, but there are several good ones if you are willing to compile drivers. Here are devices that I have tested myself with good results:


USB Devices:

Zonet ZEW2500P works out of the box. This device is about $25 at NewEgg:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833130111](http://www.newegg.com/Product/Product.asp?Item=N82E16833130111)

It does have a slow startup, it takes about 12-15 seconds for the device to start working after a bootup or insertion of the device in Edgy. I suspose it is dowloading and starting firmware.

It uses a Ralink rt2570 series chipset and kernel module.

It works well with WEP, I cannot comment upon WPA as I have not yet tried it.

---

