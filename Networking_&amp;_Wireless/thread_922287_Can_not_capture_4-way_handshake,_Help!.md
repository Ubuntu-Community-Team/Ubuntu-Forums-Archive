---
title: "Can not capture 4-way handshake, Help!"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by sh_son on 2008-09-17
Hi,

I finally got my D-Link DWL-G122 C1 fully working and tested with '--test' option in aireplay-ng.

The problem is that I can capture packets and decrypt WEP key using aircrack-ng however I can not capture 4-way handshake.

--- Storyline ------

1. Setup my router using WPA-PSK, passphrase is 'hellothisistest'.
2. Connect a laptop to my router (and connected)
3. Start airodump-ng to capture 4-way handshake
4. I try sending DeAuth to the client to reauthenticate with the router
5. The client reconnects but airodump-ng shows no sign of 'handshake' being captured
6. Repeated the process several times but no luck

Anyone can help with capturing the handshake?
Thanks in advance.

- Eric

---

### Post by rlzyoner on 2008-09-17
Your monitor card must be in the same mode as the both the client and Access Point

You may also need to set the monitor card to the same speed

---

### Post by sh_son on 2008-09-17
> **rlzyoner said:**
> Your monitor card must be in the same mode as the both the client and Access Point

You may also need to set the monitor card to the same speed

Thanks for your quick reply but; I did not get you meant.
I did the following in the terminal window;

# sudo su
# ifconfig wlan3 up
# iwconfig wlan3 mode monitor
# iwpriv wlan3 rfmontx 1
# airmon-ng start wlan3
# airodump-ng -c 1 --bssid 00:00:00:00:00:00 wlan3
# aireplay-ng -0 5 -a <BSSID> -c <Client MAC> wlan3

and the output of the aireplay-ng was something like;
Sending DeAuth to Station  -- STMAC 11:11:11:11:11:11
Sending DeAuth to Station  -- STMAC 11:11:11:11:11:11
Sending DeAuth to Station  -- STMAC 11:11:11:11:11:11
Sending DeAuth to Station  -- STMAC 11:11:11:11:11:11
Sending DeAuth to Station  -- STMAC 11:11:11:11:11:11

Do you know why it is not working?
I have followed the instructions but still not working.

Regard.

---

### Post by rlzyoner on 2008-09-17
Also,
Are you writing airodump-ng to a file.
The command should look something like this

airodump-ng -c 1 --bssid 00:11:22:33:44:55 -w psk ath1

Then when you get the handshake, run aircrack-ng on psk*.cap

---

### Post by sh_son on 2008-09-17
> **rlzyoner said:**
> Also,
Are you writing airodump-ng to a file.
The command should look something like this

airodump-ng -c 1 --bssid 00:11:22:33:44:55 -w psk ath1

Then when you get the handshake, run aircrack-ng on psk*.cap

Sorry, I forgot to put that option in so my command line would be;

# airodump-ng -c 1 --bssid 00:00:00:00:00:00 -w eric wlan3
# aircrack-ng -a 2 -w <dictionary.lst> eric-01.cap

But even I repeat deauthentication and reconnecting to the router, it still does not say 'Handshake' on airodump-ng.
The distance I am testing is about 2 meters from host (me).

Thanks in advance.

---

### Post by rlzyoner on 2008-09-17
You could try sending a few more packets and slowing down the packet rate

aireplay-ng -0 5 -x 10 -a (ACCESSPOINT) -c (CLIENTMAC) wlan3

---

### Post by sh_son on 2008-09-17
> **rlzyoner said:**
> You could try sending a few more packets and slowing down the packet rate

aireplay-ng -0 5 -x 10 -a (ACCESSPOINT) -c (CLIENTMAC) wlan3

Thank you very much for being so supportive;
I have not got access to Ubuntu at the moment so when I get it I will post see how it went; probably about 2hrs later.

Regard.

---

### Post by rlzyoner on 2008-09-17
No worries, Peace

---

### Post by sh_son on 2008-09-26
Thank you for your quick replies and supports;
I figured out that the reason why I was not able to
capture the handshake was I was too far away from my router.

It worked fine when I was a metre away from it;

Thanks.:)

---

