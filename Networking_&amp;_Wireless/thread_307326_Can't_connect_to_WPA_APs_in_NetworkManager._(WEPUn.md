---
title: "Can't connect to WPA APs in NetworkManager. (WEP/Unencrypted is fine)"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2006-11-26
I'm trying to connect to my WPA PSK AP, but I can't do it. When I set the router to WEP or unencrypted, it works fine, but no dice with WPA.

When I've got the router set to WPA, I go to NetworkManager and select my network, it prompts for the WPA (PSK) password, but then it spins and spins but never connects, and eventually times out. 

If I do the same thing when the AP is unencrypted or has WEP, I connect without a hitch.

I don't even know where to begin to troubleshoot. Can anyone give me some tips?

Thanks,
Jamie

My configuration:
Dell Latitude D620
Ubuntu Edgy
Broadcom 4311 (Dell 1390) wireless card (Using NDISWrapper)
NetworkManager

---

### Post by groggyboy on 2006-11-26
is wpa_supplicant installed?

try typing "locate wpa_supplicant" in the terminal to check.

---

### Post by Jamie Jackson on 2006-11-26
Yeah, it's installed.

Also, I followed these instructions, which told me to create a */etc/default/wpasupplicant* file containing:

ENABLED=0

...so I did that, too. (Not sure what it's for though.)

Let me know if there's any more diagnostic info I can provide.

Thanks,
Jamie

---

### Post by groggyboy on 2006-11-26
i'm not sure how to help you.  i can see from a forum search that you aren't alone with this problem.

have you [looked here]("http://hostap.epitest.fi/wpa_supplicant/") to make sure your card is supported?

i see from another thread that you've been [to this debian site]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html"), and presumably followed their advice.

you could try left clicking the networkmanager icon, choosing to connect to a different wireless network, and manually reentering the info.

there is another program out there called connection-manager.  its still in beta, and not as polished as network-manager, but it may be able to do for you what network-manager cannot do.  if you are curious, [this thread]("http://www.ubuntuforums.org/showthread.php?t=299462") explains it.

if all else fails, you could try configuring wpa_supplicant manually, using the [ubuntu wiki howto]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo").

other than that, I'm clueless.  :-?   sorry to get your hopes up.

---

### Post by Jamie Jackson on 2006-11-26
> **groggyboy said:**
> i'm not sure how to help you.  i can see from a forum search that you aren't alone with this problem.
have you [looked here]("http://hostap.epitest.fi/wpa_supplicant/") to make sure your card is supported?
Yeah, it claims to support ndiswrapper, which I'm using.
> 
i see from another thread that you've been [to this debian site]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html"), and presumably followed their advice.

Yeah, those are the instructions I'm working with at the moment.
> 
you could try left clicking the networkmanager icon and then choosing to connect to a different wireless network.


I went to a friend's house (with WPA) today, and no luck there either. :-(

> 
if all else fails, you could try configuring wpa_supplicant manually, using the [ubuntu wiki howto]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo").
other than that, I'm clueless.  :-?   sorry to get your hopes up.

No problem, thanks. I'll hold off on the manual setup for now, in hopes that someone has an easier answer...

Thanks again,
Jamie

---

### Post by James79 on 2006-11-27
I positively couldn't get NetworkManager to work with my card either. Basically it requires that you remove (disable?) your network card in /etc/network/interfaces so that it can take over possession of your wireless card. I'm not sure if that's an accurate way of putting it (as I'm a newb as well), but it's something along those lines.

In the end, the *simplest* method of getting Ubuntu to use my wireless card was to configure it manually myself. To do so, you need to edit your /etc/network/interfaces file to read something like this:


```

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
wpa-driver madwifi
wpa-conf managed
wpa-ssid linksys
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-passphrase <enter 63 alpha crap here>
address 192.168.0.10
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers <put your dns ip here>

```

Obviously, change the wpa-driver, wpa-ssid, wpa-passphrase and ip addresses to suit your setup. This will get your WPA wireless working with a static ip. Your wireless card may not be named "ath0" either, you may need to change that as well.

If you want to use DHCP, change the word "static" in the iface command to "dhcp", and remove the relevant ip addresses towards the end.

And that's IT. If this works, you won't need to use NetworkManager at all. I had it working in seconds using this method!

Hope that helps!

---

### Post by Jamie Jackson on 2006-11-27
James79,

A couple of questions: 

Do you have an /etc/default/wpasupplicant file? If so, what are the contents?

Also, did you have the same issue with NetworkManager as I do? (It connected to WEP and unencrypted networks, but not WPA?)

Last, the things I don't recongnize in your config are:
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP

Are these particular to your network, or are those generic?

Thanks,
Jamie
P.S. I still ultimately want to use NM (seems nice for mobile use), but would be happy to have a workaround such as yours.

---

### Post by James79 on 2006-11-27
> **Jamie Jackson said:**
> 
Do you have an /etc/default/wpasupplicant file? If so, what are the contents?


I don't have access to this particular machine at the moment. I believe if you have wpasupplicant installed you will have this file regardless, but I did *not* need to modify it whatsoever. It's my understanding that you can put the parameters I gave you in either wpasupplicant, OR interfaces. I prefered the later. The syntax is a little different when you choose to place it in the former.

> **Jamie Jackson said:**
> 
Also, did you have the same issue with NetworkManager as I do? (It connected to WEP and unencrypted networks, but not WPA?)


Initially, yes. I eventually got it "working" to the point where it could connect (after I found a post mentionning that the wireless nic needs to be unmanaged by /etc/network/interfaces, which wasn't obvious imo...), but I would constantly get prompted to enter in a password to connect. That problem has a workaround too, but the solution I'm suggestion worked flawlessly for me in a matter of minutes and seemed to me to be a lot "cleaner".

> **Jamie Jackson said:**
> 
Last, the things I don't recongnize in your config are:
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP

Are these particular to your network, or are those generic?


I did not change any of those, I copied them as-is from examples found on the internet. A quick google'ing revealed [this page]("http://kanotix.com/FAQ-id_cat-140.html") which has a table describing the various options. 

Admitedly, if you need to connect to more than one access point this may not be the best solution for you. Perhaps a more knowledgeable member would have a workaround for that.

---

### Post by Jamie Jackson on 2006-11-30
I got mine going with WPA, NetworkManager, and NDISWrapper. I modified [this wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#preview") to document what I did.

Thanks,
Jamie

---

