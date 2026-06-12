---
title: "Someone sniffed my WiFi"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by Peacepunk on 2007-01-30
Hi Community

I found someone to have sniffed into my WiFi, faking the mac address of my laptop to access with, I guess, breaking the wep key.

System is UBUNTU 6.06
WiFi Box is a Linksys BEFW11S4 802.11b firmware 1.52.02

From now, I disabled the WiFi...

But for changing all passwords/ssid, any advice on this MAC issue ? Will I have to change the MAC address of my laptop? how? [I have to guess the intruder knows a fair bit in this, MAC fooling doesn't seem to be of average knowledge]

How long does WPA stands in front of an attacker? Does it worth the change?

This is foolproofed: Laptop is switched off, ISP just reset-ed his MB-counter to 0 this morning at 8am (new month, new bill), I didn't use internet at all & it shows I used 10Mb this morning, which is impossible.

Advice ? where to look for logs of what went trough the Linksys box?

---

### Post by Floppyjoe on 2007-01-31
I don't have much advice for you but I believe WPA encryption is far more secure than WEP. The attacker would change tactics from sniffing packets to probably trying to guess the password with a brute force dictionary attack. In this case use a really long secure passphrase to thwart intruders. I would definitely use The WPA if it is available to you.

---

### Post by bionnaki on 2007-01-31
WEP is easy to crack. Use WPA.

---

### Post by netztier on 2007-01-31
> **Peacepunk said:**
> Hi Community

I found someone to have sniffed into my WiFi, faking the mac address of my laptop to access with, I guess, breaking the wep key.



Ouch. This is the hard way of learing that MAC access lists, WEP encryption (and not broadcasting the SSID, while we're at it) offer about as much security as a garden fence two feet high.

Faking a mac-address with Ubuntu can be as easy as **sudo aptitude install macchanger** followed by **sudo macchanger -m 11:22:33:44:55:66 wlan0**.

By all means use WPA-PSK or WPA2-PSK with a long, good passphrase! And make sure it's not one that can be guessed (wife's maiden name, dad's middle name) or is somehow dictionary-based.

best regards

Marc

---

### Post by Peacepunk on 2007-01-31
Hey, here comes the answers! Great

[SIZE="3"]Thanks **Marc**[/SIZE]

Is **macchanger** safe to use ? I know I do not have an issue with the Linksys box to make it acknolwedge a new MAC, my concern are more around the wireless hardware that would err... hate it? reject it? Stop working?[I] Sony Vaio wireless intel bg2200-something
[/I]
The WiFi box here is able to work on** WPA Pre-Shared** and **WPA Radius**

With reference to the Howto published as sticky by **Wieman01**, wich one would be recommended?

[I]I tried to avoid DCHP already but can't: any link to the safe setting of Fixed-IP setup?
Never been able to connect without  a broadcasted ssid with ubuntu, BTW.[/I]

Cheers

Jean-Philippe

---

### Post by julian67 on 2007-01-31
Your neighbour (or whoever) wouldn't even need to crack your wep if you left the router password at default. Make sure you disable the ability to admin the router via wi-fi. Only a cabled user who knows the **_strong_** password should be allowed to change any settings. Change the default password or anyone can just telnet in and configure your router how they like, view the wep keys and see any mac address you have allowed to access the router.

---

### Post by netztier on 2007-01-31
> **Peacepunk said:**
> 
Is **macchanger** safe to use ? I know I do not have an issue with the Linksys box to make it acknolwedge a new MAC, my concern are more around the wireless hardware that would err... hate it? reject it? Stop working?[I] Sony Vaio wireless intel bg2200-something
[/I]

I wouldn't know why it should be unsafe. I have however found that after upgrade to 6.10 and it's new version of NetworkManager and madwifi-ng drivers, it would no longer work with my Atheros-based card. It accepts the new address for both ath0 and wifi0, and **ifconfig -a** actually showed the new MAC address. Running Kismet in parallel on another laptop however revealed that all frames sent by that wireless NIC still had the original address :-(

There is no reason why the WiFi box should not accept a new MAC address as a WLAN client - unless of course you forget to add that new address to the "white list" of allowed MAC addresses.

> **Peacepunk said:**
> 
The WiFi box here is able to work on** WPA Pre-Shared** and **WPA Radius**


Then by all means activate and use it! Make that Pre-Shared Key (PSK) good and long!

> **Peacepunk said:**
> 
[I]I tried to avoid DCHP already but can't: any link to the safe setting of Fixed-IP setup?
Never been able to connect without  a broadcasted ssid with ubuntu, BTW.[/I]


I see absolutely no benefit in deactivating DHCP. If you want to make sure you always have the same IP address, configure a "reservation" or a "static lease" for your MAC address, or whatever your WiFi box calls this feature. IMO, insisting on static IP addresses is asking for operational/administrative hassle and trouble - beside the fact that current NetworkManager in ubuntu has some difficulty running with static IP addresses in some networks and DHCP in others. 
If access to your network is properly secured (see: WPA-PSK, WPA-RADIUS etc.), then it's perfectly safe to use DHCP and enjoy the flexibility and comfort that comes with it. Plus

As other posters (julian67) hinted, there's more points to consider:
[LIST]
[*]disable configuration access to your WiFi box from WLAN. Most of these have a configuration option to explicitely deny or allow this.
[*]deactivate HTTP and telnet  and use HTTPS or SSH (if available) as access method to configure your WiFi box.
[*]use a good and long password to protect your WiFi box's web or shell interface. No, not the same as the WPA-PSK.
[/LIST]

best regards

Marc

---

### Post by Peacepunk on 2007-01-31
Sure, at least my WiFi box WAS proteced by a password of my own... Dumb user indeed, but not _that_ dumb. Will change it though.

telnet de-activated, remote admin de-activated.

Will implement WPA Pre-Shared then, thanks.

Thanks for the DCHP advice: I receive a lot of people in my office, and they do need to connect to my network.

Laptop is still on 6.06 (for the LTS feature, I do not see the point in changing my OS every 6 months) so I may give macchanger a go if I spot the MAC of it on the network while the laptop's in its case, after switch to WPA & renewal of all passphrases.

Thanks to all.

Jean-Philippe.

---

### Post by Peacepunk on 2007-02-01
Ok, got it right following wieman01 howto on wpa. Struggled a bit more on the auto-connect while booting, it's working as well but lacks a touch of... Elegance?

It simply restart the network during boot-up, which is slow & get you to the text-based boot screen.

Happy anyway, I hope the wpa start-up on boot isue gets sorted someday.

To be totally happy I'd still have to try without ssid broadcast. Later.

cheers

Jean-Philippe

---

### Post by wieman01 on 2007-02-15
> **Peacepunk said:**
> Ok, got it right following wieman01 howto on wpa. Struggled a bit more on the auto-connect while booting, it's working as well but lacks a touch of... Elegance?

It simply restart the network during boot-up, which is slow & get you to the text-based boot screen.

Happy anyway, I hope the wpa start-up on boot isue gets sorted someday.

To be totally happy I'd still have to try without ssid broadcast. Later.

cheers

Jean-Philippe
Hello Peacepunk, 

To make the boot process a bit faster while restarting your network, try Static IP instead. You don't have to disable DHCP for this purpose, all you have to do is follow the HOWTO and assign a static IP to your client PC. I know the "restart issue" is ugly, however, you won't even notice if you make use of static IP rather than DHCP in your case. All other PCs could still use DHCP which is an advantage because it means less administrative effort.

As for disabling the broadcast of ESSID, try this option: 
> wpa-ap-scan 2
"1" stands for broadcast enabled, "2" for hidden broadcast.

---

### Post by Peacepunk on 2007-02-15
Hi Wieman, Thanks for the follow-up.

from your setup:

> 
address** 192.168.168.40**
netmask **255.255.255.0**
network** 192.168.168.0**
broadcast **192.168.168.255**
gateway** 192.168.168.230 **
dns-nameservers** 192.168.168.230**


From my WiFi Box' Setup page:

> 
Local IP Address:               ** 192  .168  1.  1. **	*--  Original, unchanged 	*
 Subnet Mask:	         ** 255 . 255 . 255 . 0** *--  Original, unchanged 	*

Local DHCP Server:            *** Enable 	 ***

Start IP Address:               **192.168.1.100	** 	 *--  Original, unchanged 	*
Number  of  Address:         ** 4** *(sensible choice, never more than 4 pc's here)	* 	 	 
DHCP  Address  Range:        **192.168.1.100 ~ 103	 **	 
Client Lease Time:	          **0** minutes *(0 means one day)	* 	
 
Static DNS 1: 	                     **203 .144  . 65 . 2**	 	 
Static DNS 2:                    **  203  144. 66 . 3	** 	 
Static DNS 3: 	                     **.210  80. 58 .66 	** 	 

WINS: 	 ** .0  0. 0 .0** 

Now, I tanslated
> 
address *from* **192.168.168.40*** into ***192.168.103** * target for laptop*
netmask seems to be same, **255.255.255.0**


What should then, according to the values given by my wifi box, be the other values ?
> 
network **192.168.168.0**  - - Will it be *network **192.168.1.1* ?**
broadcast** 192.168.168.255**   - -Will it be *network ** 192.168.1.255* ?**
gateway **192.168.168.230**  - - *NotAClueHere* 
dns-nameservers **192.168.168.230**  - - *NotAClueHere* 


[CENTER]**[SIZE="4"]???[/SIZE]**[/CENTER]

Thanks.

---

### Post by wieman01 on 2007-02-15
Hi Peacepunk, 

This is it:
> address 192.168.1.99
netmask 255.255.255.0
network  192 .168 1. 0
broadcast  192 .168 1.255
gateway  192 .168 1. 1
dns-nameservers  192 .168 1. 1
Your client PC will have the IP address **"192.168.1.99"** to avoid that it conflicts with PCs using the DHCP IP range. I also assume that your router acts as a DNS gateway, so the DNS nameserver will be **"192 .168 1. 1"**.

Gateway is your router's IP address: **192 .168 1. 1**

---

### Post by Peacepunk on 2007-02-15
**_that_** was fast

*Implementing & testing, report later.*

many thanks.

---

### Post by Peacepunk on 2007-02-15
It's all about *Elegance*...  and speed.

Moving to fixed IP does not break the startup splash anymore, boot is faster, no disruption.

*&&*

I have the pleasure to report the method as working with** 6.06LTS** on both [COLOR="#a0522d"]Gnome[/COLOR] & [COLOR="Sienna"]Enlightenment DR16[/COLOR].
[RIGHT]*[COLOR="DimGray"] [?why do people change OS every six months?][/COLOR]*[/RIGHT]

Cheers Wieman, I owe you something liquid if you ever come near Phnom Penh.

---

### Post by wieman01 on 2007-02-15
Welcome! I should have mention this in the first place. Guess I'll change the second post in my thread accordingly.

---

