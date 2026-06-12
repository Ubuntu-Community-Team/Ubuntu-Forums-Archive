---
title: "How to connect a Wired LAN to a Wireless Community LAN?"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by middlewordie on 2007-01-17
I get my internet access from [Boundless]("http://boundless.coop") - a wireless community network running via linux machines to provide free or very cheap wireless access. It's £5 a month for up to 2MB/s, which is great for almost everything I need it for.

I have three computers in my flat, two are running xp for tv/gaming and one recently installed with Edgy which I would like to use for working from home - I'm working on my boss on that one ;) . I'd like to network all three for file sharing, games over LAN and net access via boundless.

I'm a newbie when to comes to linux, although i've had a poke about with this issue before, but with rather disappointing results
[http://ubuntuforums.org/showthread.php?t=338231]("http://ubuntuforums.org/showthread.php?t=338231")

Has anyone else connected a LAN to a WLAN to get internet access (I appreciate this is not the usual way round to do it!) before? Is there some form of off the shelf client box I can buy that works with linux? Or is my best bet to get a super low spec machine and have it act as my router? I'm not so keen on that due to the cost of continuously power consumption.

Thanks in advance - any help would be much appreciated!

---

### Post by netztier on 2007-01-17
> **middlewordie said:**
> Is there some form of off the shelf client box I can buy that works with linux? Or is my best bet to get a super low spec machine and have it act as my router? 

You need two things (though not necessarily separate devices):

[LIST]
[*]a WLAN device that acts as a "WLAN Client" or "Workgroup bridge"
[*]a router that does NAT/PAT, "Hiding" "IP Masquerading" or however you wish to call the feature that hides a number of internal addresses behind one external address.
[/LIST] 

So consider buying a bit of hardware; a WLAN access point that can be switched to "client" or "workgroup bridge" mode will connect to the community WLAN. I like the ZyXEL G570S particularly for that, it's what I'd call a "woolly egg-laying milk-pig" (if translated more or less literally from german ;) ) and comes at at reasonable price.

You then hook this device (running as WLAN Client) up to the "external" LAN port of a plain standard "broadband" router such as a Netgear RP614.  If you'd like to run your own WLAN, you could take a Linksys WRT54G instead, just make sure you use a different SSID and a different 802.11 channel at least 4 channels away from the community WLAN.

There are modified (OpenSource)-Firmwares for the Linksys WRT54G family and a whole set of products from other vendors using the same platform internally. With these alternative firmwares (for example OpenWRT), you might be able to achieve the same thing withing one small box instead of two. Beware however that this may void the warranty on the device and that it's not "just point and klick" to configure.

The one-box solution can also be done with Linux on a low or mid-spec PC. Equip it with a WLAN card that connects to the community WLAN and hook it up to your internal wired network. The rest is done pretty much the same way as you'd configure a Linux PC to be a broadband router. Google and forum search will help a lot here.

best regards

Marc

---

### Post by middlewordie on 2007-01-17
Thanks for the advice!

Just to check I understand you correctly can you have a quick look at the attached - is this the system what you are saying I need?

---

### Post by kvonb on 2007-01-17
....or you can very easily setup the Ubuntu machine to be your router if it is going to be on all the time.

I have the sort of setup that you are looking at, only in reverse.  My Internet comes in via Ethernet and I then share that out via both Wireless and Ethernet.

The hard part is getting your wireless working, if you can do that, the rest is a doddle!

Let me know if you need more info.

Regards, Kev :)

---

### Post by middlewordie on 2007-01-17
Thanks for the offer Kev! 

From what I've read, wireless and linux is not a the best combination and I'm doubly stuffed because I need wireless working to access the net to get help on it. I'm determined to crack it though...:)

---

### Post by netztier on 2007-01-17
> **middlewordie said:**
> Thanks for the advice!

Just to check I understand you correctly can you have a quick look at the attached - is this the system what you are saying I need?

That prettily sums it up, yes.

One question: What do you exactly mean by *file sharing*? If it's just within your (wired) LAN, from PC to PC, using Windows directory shares and Samba on the Ubuntu box, or is it "file sharing" with the Internet with BitTorrent, eDonkey and the bunch of peer-to-peer platforms?

In the former case, your router is just a plain LAN Switch with probably 4 ports. Additionally, it will serve as a DHCP server for your internal PCs and will dole out addresses.

For the latter case, there'll be some additional configuration needed on the router (so-called port-forwarding or pinholing; read the HOWTOs and FAQs of the file-sharing program of your choice to know which ports to forward).


Another important thing to watch for is this: On the community WLAN, there (most probably) will be a DHCP server doling out addresses, too. If these are "public" internet addresses, there's no problems. If however the addresses used are from the specific ranges defined in RFC1918 (i.e. from [FONT="Courier New"]10.*.*.*[/FONT] or [FONT="Courier New"]172.[16-31].*.*[/FONT] or [FONT="Courier New"]192.168.[0-255].*[/FONT]), you must pick a different range from the listed above for your LAN - you can configure this on your router and it's DHCP Server function. Depending on which product you'll buy, it'll have [FONT="Courier New"]192.168.0.* [/FONT]or [FONT="Courier New"]192.168.1.* [/FONT]preconfigured, and it might be that you'll have to change this to another range (e.g. [FONT="Courier New"]192.168.100.*[/FONT]).


A word about WLAN encryption: speaking about a "community WLAN", you imply that the WLAN is "public". As such, it probably will run with no or weak encryption, and even if encrypted (with WEP), someone else is bound to know the key, and it'll be very easy to eavesdrop on the WLAN part of the network. Therefore, you should be remember that a lot of protocols such as POP3 (download from the mailbox) or SMTP (sending mail) use cleartext transfer and cleartext passwords.

I therefore suggest that you ask your email provider if their services are also available via the "secure" variants of the Protocols, POP3S or POP/SSL, SMTPS, SMTP/TLS, SMTP/SSL etc. If you are using a webmail service, you should make sure that there is a HTTPS-based access to it and use only this one. Your neighbor doesn't need to know your email passwords, does he? ;-)

When working interactively with other hosts on the internet, try to use SSH instead of telnet, SFTP/SCP instead of FTP, and if at all possible, try to tunnel other needed protocols to these hosts (such as X) through SSH - or a VPN solution, where available/applicable.

It is one thing to use unsecure protocols across the Internet if you can trust that most segments will be wire- or fibre-based (which of course won't protect your data from the ISP's employee mirroring a switchport and playing around with dsniff to grab passwords).

Using an unprotected WLAN as "last mile" (i.e. between your ISP and your home) is a thing of different scale. Wherever possible, I'd absolutely insist on using the secure protocols, SSH or VPN tunnels.


best regards

Marc

---

### Post by middlewordie on 2007-01-18
Marc - thanks for this help. The security point is a good one.

I don't use bit-torrent (at the moment). so I think the more complicated set up can wait for a bit. I'll go shopping this weekend and keep you updated.

Cheers

Nick

---

### Post by middlewordie on 2007-01-18
Before I go :-k  at the shops can I just garner some further thoughts?

Firstly - will the [Netgear RP614]("http://www.netgear.co.uk/pdfs/RP614.pdf") receive DHCP on one side (from the wireless node via a bridge) and issue DHCP on the other side as suggested? It looks like it but I'm no expert!;) 

Secondly - what type of bridge will work? Does it need to be anything special? Will this [Belkin]("http://www.ebuyer.com/UK/product/61885") one do the job?

---

### Post by netztier on 2007-01-18
> **middlewordie said:**
> Before I go :-k  at the shops can I just garner some further thoughts?

Firstly - will the [Netgear RP614]("http://www.netgear.co.uk/pdfs/RP614.pdf") receive DHCP on one side (from the wireless node via a bridge) and issue DHCP on the other side as suggested? It looks like it but I'm no expert!;) 


Definitely. Been there, done that, used it in exactly that very mode several times. Internet-over-cable by cablecom.ch here in Switzerland works that way: They provide you with a cable modem you plug your DHCP-enabled device into, be that a PC, a Linux box or a broadband router of your choice. 

On the inside, the RP614 will be a DHCP server for your PCs, if I remember correctly, it uses 192.168.0.1 for itself and serves addresses from the 192.168.0.* range.

> **middlewordie said:**
>  Secondly - what type of bridge will work? Does it need to be anything special? Will this [Belkin]("http://www.ebuyer.com/UK/product/61885") one do the job?

Should do, as should most gaming adapters. However, these are gaming adapters or WLAN client "only" and can't be used for other purposes. Another disadvantage I have discovered for some of them is the lack of WPA or WPA2 support; Linksys and Netgear gaming adapters only support WEP128, for example (when I checked a few months ago). In some environments, this is just not good enough. Seems that the Belkin supports WPA-PSK with a firmware update.

The ZyXEL I suggested also has this "gaming adapter mode", but can be converted to work  as a workgroup bridge (to connect multiple clients to a WLAN), as a basic access point and also as a WLAN repeater. 

You might of course also use such a "workgroup bridge" with a small Switch/Hub to connect your three PCs to the WLAN. You'd have to check if it is allowed and possible to request multiple DHCP leases with a single subscription or if there's any technical restrictions in place to prevent this.

However, with a workgroup bridge in place, you won't have the (albeit basic) firewalling function the routers offer. So anyone could "walk into your wired LAN" while sitting in a Van outside your garden fence. Not what you want, actually.

A router with it's single external ethernet interface will look like a single device to your ISP, and he'll have a hard time finding out that there's actually more than one PC behind it.


best regards

Marc

[COLOR="Red"]AH.. and one most important thing before buying anything:

How does this Community WLAN control access? Is there some web-based portal you have to authenticate yourself with? Is it done via MAC-Address registration? Authentication keys, WEP or WPA, WPA2? That's an important thing to know before you go and buy the WLAN adapter, because it may have to have special capabilities...[/COLOR]

---

### Post by middlewordie on 2007-01-19
With regard to the bridge/WLAN adapter

> **netztier said:**
>  Should do, as should most gaming adapters. However, these are gaming adapters or WLAN client "only" and can't be used for other purposes. Another disadvantage I have discovered for some of them is the lack of WPA or WPA2 support; Linksys and Netgear gaming adapters only support WEP128, for example (when I checked a few months ago). In some environments, this is just not good enough. Seems that the Belkin supports WPA-PSK with a firmware update.

The ZyXEL I suggested also has this "gaming adapter mode", but can be converted to work  as a workgroup bridge (to connect multiple clients to a WLAN), as a basic access point and also as a WLAN repeater. 

True - a repeater might be useful if I have visitors, but I'm inclined to keep it simple and Ubuntu and Wireless do not seem to be he best of bed fellows...

> AH.. and one most important thing before buying anything:

How does this Community WLAN control access? Is there some web-based portal you have to authenticate yourself with? Is it done via MAC-Address registration? Authentication keys, WEP or WPA, WPA2? That's an important thing to know before you go and buy the WLAN adapter, because it may have to have special capabilities...

boundless.five is free access, unencrypted and anyone can (and does) use it. It was originally set up to allow local government workers to log in to their office network when working, but then given to the coop for public access. Is this likely to be a security concern if I have my LAN connected to it?

---

### Post by netztier on 2007-01-20
> **middlewordie said:**
>  Is this likely to be a security concern if I have my LAN connected to it?

Not if you use some device to separate the community WLAN from your private wired LAN.

Normal broadband routers such as the RP614 do exactly this. The hide your internal network from the external one, refuse all incoming connection attempts (unless configured otherwise) and make all outgoing connections look like they were coming from a single Client system. This is enough to call them "little firewalls", and rightly so.

If you were using a Workgroup bridge to connect your PCs to the community WLAN, there'd be no such protection and your PCs' security would rely solely on the stability of their software firewalls (if installed and activated) and/or the robustness of the network services you run on them (file & printer sharing, SSH server etc). 

I consider it best practice to run a private LAN (or WLAN, at that) behind a firewalling router, and would never suggest otherwise. My (W)LAN is mine, not my neighbor's.

best regards

Marc

---

### Post by middlewordie on 2007-01-20
Thanks for the thoughts - they pretty much match mine, whic means I must be learnig something!

I think I'm going to go for:

WG602 to pick up wireless signal from boundless.
WG614 to act as my firewall/router for the LAN, wihc will also have WLAN capabilities. I will presumably have to use some form of encryption over both LAN and WLAN, right?

Should be able to pick up both from Ebay for <£60!

---

### Post by netztier on 2007-01-21
> **middlewordie said:**
> 
WG602 to pick up wireless signal from boundless.


Sounds good. You'll need to run in "Wireless bridge" mode and connect it to the Router's external or "internet" port.

> **middlewordie said:**
> WG614 to act as my firewall/router for the LAN, wihc will also have WLAN capabilities. I will presumably have to use some form of encryption over both LAN and WLAN, right?

That'll rather be WG**R**614, right?

Sounds good. If you run your own WLAN, it'll be an extension of your internal LAN, not the community WLAN, very much like a an additional "wireless" switch port of the internal 4-port switch on the WGR614. 

Make sure you use a different channel on your private WLAN, or you'll have performance-decreasing interference on both WLANs. Leave a gap of at least four channels between your own and the community WLAN. A wireless sniffing tool such as **kismet** (on Linux) or **Netstumbler** (on Windoze) can help you determine which channel the community WLAN uses. On Windows, some WLAN drivers come with their own scanning tools that also show which channels are used.

Encryption is only needed for your own WLAN part; traffic on the wired LAN won't leak out to the WLAN. For a LAN, there is no industry standard for encrypting the entire traffic.

My original suggestion was to use the encrypted or "secure" versions of common protocols (wherever possible) when communicating with hosts out on the Internet, since already the second stretch of network is the community WLAN which runs unencrypted and open, as you pointed out. 

best regards

Marc

---

