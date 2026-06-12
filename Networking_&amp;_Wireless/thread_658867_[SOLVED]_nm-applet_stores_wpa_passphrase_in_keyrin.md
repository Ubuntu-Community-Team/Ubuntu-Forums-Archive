---
title: "[SOLVED] nm-applet stores wpa passphrase in keyring, but still asks for it on reboot?"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by jly on 2008-01-05
Hi,

Not new to Linux in general... Rather new to Ubuntu, as it's almost the only one that recognizes my wireless card, without having to load other modules or recompile kernel. In fact, I wanted a simple distro for my wife :-)

Now, here's my problem. Using nm-applet in roaming mode. Connecting to my wireless network using wpa/passphrase/tkip... All fine, I can see he stores the passphrase in the keyring(login). But when I reboot the laptop, nm-applet doesn't look for it in the keyring it seems, in stead it asks me for the passphrase in stead of the keyring password??

I cannot find a single trace of a problem in any of the log files...

I need help :-)

Regards,
Johan

---

### Post by jly on 2008-01-05
Oh, I forgot to mention... Laptop is an HP nc4010...

Thx,
jly

---

### Post by ugm6hr on 2008-01-05
That's very bizarre...

If Network Manager is misbehaving, maybe consider Wicd?  See the link below.

---

### Post by jly on 2008-01-06
Tried wcid, same story... as long as I don't reboot (log off, log on) automatic logon to the wireless network is working... As soon as I reboot, I have to manually reconnect, even with wcid.

So, I'm back with the gnome network manager...

Any other idea's on what might be going wrong?

My AP is a Cisco AP1131, hidden ssid, wpa-psk...

Thx,
jly

---

### Post by jly on 2008-01-07
Hi guys,

Me again... Still no working solution found.

Anyone out there who can help me? Or tell me where I can find logs for the gnome network manager? Or put it into some debugging mode? :-)

Thx,
jly

---

### Post by zipperback on 2008-01-07
Log files are usually stored in /var/log  unless otherwise specified.

- zipperback
:popcorn:

---

### Post by jly on 2008-01-07
Nothing I can use in /var/log/

The wireless connection happens in 5 stages, seen in syslog... If i'm not mistaken (i'm at work for the moment), it hangs at stage 2 and after a while it asks to enter the psk again...
But I don't see any entries in any of the logs, why he can't retrieve the psk from the keyring...

Could it be a problem of the keyring itself? I never had to enter a password for the keyring? ( I don't have the workaround configured to use the login password as the keyring password) Maybe it's new in 7.10?

Besides this issue and the ugly default theme, I'm starting to love this Ubuntu release.

Regards,
jly

---

### Post by lobner on 2008-01-13
Hello, if you come up with an answer for this issue, please post here.

I am experiencing the same.
On reboot, it starts connection to my home-network, and then it asks for the passphrase.
An if I reconnect to the network, it does not.

Regards,

---

### Post by zipperback on 2008-01-13
You should really try WICD it resolved alot of issues for me.

wifi reconnects at reboot automatically and doesn't ask for any additional information once it's properly configured.

- zipperback
:popcorn:

---

### Post by jly on 2008-01-14
I did try WICD... same results...

I can see nm-applet stores the passphrase in the keyring, but after a reboot it's not using it... it never asks me for the keyring password, in stead it always asks for the wpa passphrase... :-(

For now, I can live with it... but, If I don't find a working solution by the end of the week... I'll give fedora8 a try...

Thx,
jly

---

### Post by ugm6hr on 2008-01-14
The fact that both NM and Wicd ask for the passphrase each time suggests it is an issue with how your wifi security is set up, because NM uses the Gnome keyring, while Wicd stroes the passphrase independently.  Seems very bizarre that both would be struggling with this.

As for NM not asking for a keyring pasword - the "workaround" with libpam seems to be a default for Gutsy (unlike Feisty), so the keyring password is automatically identical to your user login, and is not asked for.

What security settings do you use?  I think hiding your SSID will normally cause NM to ask each time.  Although I thought Wicd got around that problem (tho not sure).

---

### Post by jly on 2008-01-14
Indeed, but I already tried broadcasting my ssid. No improvement there. I didn't try broadcasting my ssid with WICD however... I'll try later today.

Thx,
jly

---

### Post by jly on 2008-01-14
Oh, and I'm also stuck with this one:

[http://ubuntuforums.org/showthread.php?t=641644]("http://ubuntuforums.org/showthread.php?t=641644")

My wireless only works in roaming mode, not in manual mode...

---

### Post by ugm6hr on 2008-01-14
> **jly said:**
> Oh, and I'm also stuck with this one:

[http://ubuntuforums.org/showthread.php?t=641644]("http://ubuntuforums.org/showthread.php?t=641644")

My wireless only works in roaming mode, not in manual mode...

Not sure what you mean.  That thread asks about static IP, as well as non-roaming.

Static IP does not work with Network Manager (does with Wicd).

NM will not work unless you have roaming on.

I don't understand why you would want roaming off, to be honest (unless you had static IP).

---

### Post by jly on 2008-01-14
Well, the guy wants to use the manual mode to set a static ip, but in manual mode he cannot connect to his wireless lan.

Same for me... In manual mode, I cannot connect at all to the wireless and I don't care about static ip or not... I'm talking about the wireless link... In manual mode, nm-applet doesn't do sh*t :-(

To conclude, I don't care if I have to use roaming or manual mode, I just want my wireless to work without me (well, my wife in fact) having to provide the wpa passphrase on every reboot...

thx all!

---

### Post by ugm6hr on 2008-01-14
> **jly said:**
> Same for me... In manual mode, I cannot connect at all to the wireless and I don't care about static ip or not... I'm talking about the wireless link... In manual mode, nm-applet doesn't do sh*t :-(


That is true.  As I said - NM only works with roaming on.

If you use Gutsy, with SSID broadcast, NM *should* remember your WPA passphrase.  Of course - in your case, it appears not to.  Not sure why.

As stated - try Wicd with SSID broadcast.

Other thing that may be worth looking at with Wicd is entering the passphrase in "xxxx" (i.e. with " either side).  Something to do with the difference between a HEX passcode and an ASCII passphrase (or something like that).

---

### Post by jly on 2008-01-14
> **ugm6hr said:**
> If you use Gutsy, with SSID broadcast, NM *should* remember your WPA passphrase.  Of course - in your case, it appears not to.  Not sure why.


I can see NM **does store it** in the keyring, the thing is, that it doesn't use it for connecting to the Wireless after a reboot. As you know, it's asking me for it...
I've been looking for a way to 'debug' NM to see what it is actually doing. Does it even try to access the keyring? If it does, what is going wrong?

Thx already! And I'll try the WICD again this evening, this time broadcasting my SSID. (although I prefer not to ;-) )

---

### Post by jly on 2008-01-15
Hi,

Tried WICD again last evening. Took 5 minutes to load when I logged into X. Don't think that's normail either... Didn't have the time to reconfigure my AP to broadcast my ssid, so... Update will be for this evening.

Regards,
Johan

---

### Post by jly on 2008-01-16
Tried with broadcasting my ssid and networkmanager... Same result.
WICD is running very very slow and gives same results as networkmanager...

So, my ssid is hidden again and I'll post here the output of a good and failing attempt with networkmanager...

The failed attempt is when the laptop is started and a user first logs in. After a while nm-applet asks me for the PSK (although it's in the keyring) but now (since I tried wicd again) it even fails to connect after I pass is my PSK. It just stops trying to connect. I then need to click the icon and select my 'ssid' from the list, which suddenly becomes visible? (remember it's hidden). When I now select my ssid I'm almost instantly connected to my network without having to pass it my psk! This can be seen in the good attempt below.

:confused::confused::confused:

**Anyone??**


**Failed attempt:**

Jan 16 20:33:31 nc4010 NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  SWITCH: no current connection, found better connection 'ath0'. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Will activate connection 'ath0/jlnet666'. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Device ath0 activation scheduled... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) started... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0/wireless): access point 'jlnet666' is encrypted, but NO valid key exists.  New key needed. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'jlnet666'. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) New wireless user key for network 'jlnet666' received. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 20:33:31 nc4010 NetworkManager: <info>  Activation (ath0/wireless): access point 'jlnet666' is encrypted, and a key exists.  No new key needed. 
Jan 16 20:33:32 nc4010 NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 16 20:33:32 nc4010 NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Jan 16 20:33:32 nc4010 NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant3^I' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was '0' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6a6c6e6574363636' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:33:33 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 20:33:35 nc4010 NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jan 16 20:33:54 nc4010 last message repeated 2 times
Jan 16 20:33:56 nc4010 NetworkManager: <info>  Activation (ath0/wireless): disconnected during association, asking for new key. 
Jan 16 20:33:56 nc4010 NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'jlnet666'. 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0) New wireless user key for network 'jlnet666' received. 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 20:34:18 nc4010 NetworkManager: <info>  Activation (ath0/wireless): access point 'jlnet666' is encrypted, and a key exists.  No new key needed. 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant4^I' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was '0' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6a6c6e6574363636' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 20:34:19 nc4010 NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jan 16 20:34:50 nc4010 last message repeated 4 times
Jan 16 20:35:14 nc4010 last message repeated 3 times
Jan 16 20:35:19 nc4010 NetworkManager: <info>  Activation (ath0/wireless): association took too long (>60s), failing activation. 
Jan 16 20:35:19 nc4010 NetworkManager: <info>  Activation (ath0) failure scheduled... 
Jan 16 20:35:19 nc4010 NetworkManager: <info>  Activation (ath0) failed for access point (jlnet666) 
Jan 16 20:35:19 nc4010 NetworkManager: <info>  Activation (ath0) failed. 
Jan 16 20:35:19 nc4010 NetworkManager: <info>  Deactivating device ath0. 
root@nc4010:/var/log# 
root@nc4010:/var/log# 
root@nc4010:/var/log# 
root@nc4010:/var/log# 





**Good attempt:**

Jan 16 20:38:27 nc4010 NetworkManager: <debug> [1200512307.918379] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'jlnet666' 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ath0 / jlnet666 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Deactivating device ath0. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Device ath0 activation scheduled... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) started... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0/wireless): access point 'jlnet666' is encrypted, but NO valid key exists.  New key needed. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) New wireless user key requested for network 'jlnet666'. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) New wireless user key for network 'jlnet666' received. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan 16 20:38:27 nc4010 NetworkManager: <info>  Activation (ath0/wireless): access point 'jlnet666' is encrypted, and a key exists.  No new key needed. 
Jan 16 20:38:28 nc4010 NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD ath0^I^Imadwifi^I/var/run/wpa_supplicant8^I' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was '0' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 6a6c6e6574363636' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  SUP: response was 'OK' 
Jan 16 20:38:29 nc4010 NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan 16 20:38:37 nc4010 NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jan 16 20:39:09 nc4010 last message repeated 4 times
Jan 16 20:39:17 nc4010 NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jan 16 20:39:19 nc4010 NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'jlnet666'. 
Jan 16 20:39:19 nc4010 NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jan 16 20:39:19 nc4010 NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Jan 16 20:39:20 nc4010 NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Jan 16 20:39:20 nc4010 NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Jan 16 20:39:20 nc4010 NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
Jan 16 20:39:21 nc4010 dhclient: wifi0: unknown hardware address type 801
Jan 16 20:39:22 nc4010 NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0 
Jan 16 20:39:22 nc4010 dhclient: wifi0: unknown hardware address type 801
Jan 16 20:39:24 nc4010 NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Jan 16 20:39:25 nc4010 dhclient: DHCPREQUEST on ath0 to 255.255.255.255 port 67
Jan 16 20:39:25 nc4010 dhclient: DHCPACK from 192.168.1.1
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.4.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: New relevant interface ath0.IPv4 for mDNS.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Registering new address record for 192.168.1.4 on ath0.IPv4.
Jan 16 20:39:25 nc4010 NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface ath0 
Jan 16 20:39:25 nc4010 NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 16 20:39:25 nc4010 NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
Jan 16 20:39:25 nc4010 NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    address 192.168.1.4 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    netmask 255.255.255.0 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    broadcast 192.168.1.255 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    gateway 192.168.1.1 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    nameserver 195.238.2.22 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    nameserver 195.238.2.21 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    nameserver 192.168.1.1 
Jan 16 20:39:25 nc4010 NetworkManager: <info>    domain name 'domain_not_set.invalid' 
Jan 16 20:39:25 nc4010 NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 16 20:39:25 nc4010 NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
Jan 16 20:39:25 nc4010 NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Withdrawing address record for 192.168.1.4 on ath0.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.4.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Interface ath0.IPv4 no longer relevant for mDNS.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.4.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: New relevant interface ath0.IPv4 for mDNS.
Jan 16 20:39:25 nc4010 avahi-daemon[4715]: Registering new address record for 192.168.1.4 on ath0.IPv4.
Jan 16 20:39:25 nc4010 dhclient: bound to 192.168.1.4 -- renewal in 35688 seconds.
Jan 16 20:39:26 nc4010 NetworkManager: <info>  Clearing nscd hosts cache. 
Jan 16 20:39:26 nc4010 NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jan 16 20:39:26 nc4010 NetworkManager: <info>  Activation (ath0) successful, device activated. 
Jan 16 20:39:26 nc4010 NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
Jan 16 20:39:26 nc4010 NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 16 20:39:26 nc4010 NetworkManager: <debug> [1200512366.237876] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'jlnet666' 
Jan 16 20:39:26 nc4010 ntpdate[5875]: adjust time server 91.189.94.4 offset -0.115813 sec
Jan 16 20:39:28 nc4010 avahi-daemon[4715]: Registering new address record for fe80::212:79ff:fe3f:792c on ath0.*.

---

### Post by jly on 2008-01-17
up we go... 	:redface:

---

### Post by jly on 2008-01-18
Hi all,

GOOD NEWS ;-)

Wireless is working fine now! Except that it's not with UBUNTU... :-(

Last night I loaded Sabayonlinux pro edition 1.1 and all is working like a charm. I must admit that startup is slower than ubuntu and I personally would prefer gnome but since it's for my wife I went for KDE...

Maybe I'll try the next release of UBUNTU again... ;-)

Regards,
Johan

---

