---
title: "Noob wifi qustions"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by NobleSavage on 2007-01-08
My biggest obstacle in completely moving to Ubuntu is Wifi. I need to get WPA2 working on my Thinkpad notebook.  I have IPW2200.

I've read through this forum a few times and I'm a little confused. Before I start tinkering I'd like to ask a few questions.

NetworkManager - I'm assuming this does not work with WPA2? 

If I follow the Howto that is stickied above is it incompatible with NetworkManager?

I've confused by in the Howto concerning WPA-PSK key generation:

I know my ascii key and ssid, but what is the passphrase? I currently do not use or have a pass phrase?

Thanks for any help.

---

### Post by tweedledee on 2007-01-09
> **NobleSavage said:**
> My biggest obstacle in completely moving to Ubuntu is Wifi. I need to get WPA2 working on my Thinkpad notebook.  I have IPW2200.

I've read through this forum a few times and I'm a little confused. Before I start tinkering I'd like to ask a few questions.

NetworkManager - I'm assuming this does not work with WPA2? 

If I follow the Howto that is stickied above is it incompatible with NetworkManager?

I've confused by in the Howto concerning WPA-PSK key generation:

I know my ascii key and ssid, but what is the passphrase? I currently do not use or have a pass phrase?

Thanks for any help.

At least on Edgy (maybe with Dapper?), Network Manager DOES work with WPA2 (at least so it is claimed, I can vouch for WPA).  If you want to use Network Manager, it should pretty much just work (as long as you haven't done any manual configuration first).  If not, follow the instructions on the wiki: [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo).  Personally, I found configuring wpa manually be to easier, as long as you won't be needing to change networks.  If you want to follow the procedure on the sticky you mentioned, it probably won't work well with network manager.

Your ASCII key is most likely your passphrase, if you've been using WPA.

---

### Post by kipeloff on 2007-01-10
To generate WPA passhprase in hex format, you will need 'wpasupplicant' package installed.
Then use the following command to generate hex key,
> wpa_passphrase 'your_ssid' 'your_ascii_key'

---

