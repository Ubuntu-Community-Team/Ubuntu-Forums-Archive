---
title: "Correct wifi password not connecting to router"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by joeybananas12 on 2014-04-03
Hello everyone.

I'm having a problem with connecting to my wifi.  The WPA2 key i provide is correct.  everyother device on the network has no problems connecting.  When I boot into win7 on the same machine and use the same card it connects fine.  When I first boot into ubuntu wicd connects to the router (DHCP gives it 192.168.1.103 which is what the router is supposed to give this machine)  I cannot ping the router, other machines in the network or outside the network, other devices cannot ping my machine.  If I disconnect from the wifi and try and reconnect to the wifi it is unable to connect.  the wicd gui says it's an invalid password in the status bar down the bottom.

I'm currently using a USB tether through my droid device to connect to the internet

Attatched below are the results from running wild mans wireless_script located at [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script).

[ATTACH]251680[/ATTACH]

Thanks for your patience.

---

### Post by varunendra on 2014-04-05
Any specific reason why you are using Wicd instead of Network Manager? Did it solve the purpose? If not, I'd suggest to revert back to Network Manager by installing it (*network-manager* and *network-manager-gnome* packages) and purging Wicd. It is usually easier to troubleshoot with default components.

Right now, there is one thing that I don't like to see - using **[COLOR="#FF0000"]TKIP[/COLOR]** encryption algorithm, and that too with WPA2. This combination shouldn't be allowed in the first place, not sure why some router manufacturers do. Please log into your router's web interface and change the encryption algorithm from **[COLOR="#FF0000"]TKIP[/COLOR]** to **[COLOR="#0000CD"]AES (CCMP)[/COLOR]**.

Another thing - if "**Where IP**" is your access-point, also change this SSID to something that doesn't contain blank spaces or special characters. For example, try "**Where_IP**". Also try channels 1 or 11, they offer better signal quality. Reboot the router after saving any changes.

**PS:**
Welcome to Ubuntu Forums! :)

---

### Post by joeybananas12 on 2014-04-05
Hi,

No luck I'm afraid.

I purged wicd and have reinstalled NetworkManager (I had changed to wicd after this problem had started and after doing some brief research I found some people claim that wicd fixed it for them)

The wireless settings now look like the following, i'll put all options my router gives me:
SSID: where_IP
Channel: 1
Wireless mode: B/G/N mixed
Authentication: WPA2-PSK
Encryption: AES (It was my understanding that TKIP was a stronger encryption type than AES)

I rebooted the router and my pc for good measure.  Still no luck.

Here is the (probably too long) tail of the syslogs

```
$ cat /var/log/syslog | tail -n 50
Apr  6 11:48:43 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: disconnected -> inactive
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) started...
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> (ra0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) scheduled...
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0) Stage 1 of 5 (Device Prepare) complete.
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) starting...
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> (ra0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0/wireless): connection 'Where_IP' has security, and secrets exist.  No new secrets needed.
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Config: added 'ssid' value 'Where_IP'
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Config: added 'scan_ssid' value '1'
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Config: added 'auth_alg' value 'OPEN'
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Config: added 'psk' value '<omitted>'
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Activation (ra0) Stage 2 of 5 (Device Configure) complete.
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> Config: set interface ap_scan to 1
Apr  6 11:48:44 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: inactive -> scanning
Apr  6 11:48:46 li-TARDIS wpa_supplicant[931]: ra0: Trying to associate with 00:60:64:b2:0c:e2 (SSID='Where_IP' freq=2412 MHz)
Apr  6 11:48:46 li-TARDIS kernel: [  408.319422] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:48:46 li-TARDIS kernel: [  408.319678] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Apr  6 11:48:46 li-TARDIS wpa_supplicant[931]: ra0: Association request to the driver failed
Apr  6 11:48:46 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: scanning -> associating
Apr  6 11:48:49 li-TARDIS kernel: [  411.469593] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:48:51 li-TARDIS wpa_supplicant[931]: ra0: Authentication with 00:60:64:b2:0c:e2 timed out.
Apr  6 11:48:51 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: associating -> disconnected
Apr  6 11:48:52 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: disconnected -> scanning
Apr  6 11:48:52 li-TARDIS wpa_supplicant[931]: ra0: Trying to associate with 00:60:64:b2:0c:e2 (SSID='Where_IP' freq=2412 MHz)
Apr  6 11:48:52 li-TARDIS kernel: [  414.470198] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:48:52 li-TARDIS kernel: [  414.470449] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Apr  6 11:48:52 li-TARDIS wpa_supplicant[931]: ra0: Association request to the driver failed
Apr  6 11:48:52 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: scanning -> associating
Apr  6 11:48:55 li-TARDIS kernel: [  417.470578] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:48:57 li-TARDIS wpa_supplicant[931]: ra0: Authentication with 00:60:64:b2:0c:e2 timed out.
Apr  6 11:48:57 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: associating -> disconnected
Apr  6 11:48:58 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: disconnected -> scanning
Apr  6 11:49:00 li-TARDIS wpa_supplicant[931]: ra0: Trying to associate with 00:60:64:b2:0c:e2 (SSID='Where_IP' freq=2412 MHz)
Apr  6 11:49:00 li-TARDIS kernel: [  422.677507] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:49:00 li-TARDIS kernel: [  422.677795] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Apr  6 11:49:00 li-TARDIS wpa_supplicant[931]: ra0: Association request to the driver failed
Apr  6 11:49:00 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: scanning -> associating
Apr  6 11:49:04 li-TARDIS kernel: [  426.471786] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:49:05 li-TARDIS wpa_supplicant[931]: ra0: Authentication with 00:60:64:b2:0c:e2 timed out.
Apr  6 11:49:05 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: associating -> disconnected
Apr  6 11:49:06 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: disconnected -> scanning
Apr  6 11:49:07 li-TARDIS wpa_supplicant[931]: ra0: Trying to associate with 00:60:64:b2:0c:e2 (SSID='Where_IP' freq=2412 MHz)
Apr  6 11:49:07 li-TARDIS kernel: [  429.472365] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 182
Apr  6 11:49:07 li-TARDIS kernel: [  429.472661] ==>rt_ioctl_siwfreq::SIOCSIWFREQ(Channel=1)
Apr  6 11:49:07 li-TARDIS wpa_supplicant[931]: ra0: Association request to the driver failed
Apr  6 11:49:07 li-TARDIS NetworkManager[854]: <info> (ra0): supplicant interface state: scanning -> associating
```

Thanks for you help so far, and for the welcome!

---

### Post by varunendra on 2014-04-05
Could you give me the link to the driver and the guide/post that you followed to install the sta driver? So that I can confirm that everything there was as it should be.

Also, which country are you in? We may try explicitly defining the CRDA country code to make sure the driver uses correct RegDomain settings.

---

### Post by joeybananas12 on 2014-04-05
I'm fairly certain I was using this link - [http://superuser.com/questions/663190/asus-pce-n53-11n-n600-pci-e-adapter-on-3-x-kernel](http://superuser.com/questions/663190/asus-pce-n53-11n-n600-pci-e-adapter-on-3-x-kernel)

I'm in Australia.

What I can't figure out is why it suddenly decided to stop working.  Like it was working fine and then I boot into win7 and didn't go back for a week or so, boot back into ubuntu and it stopped working.

---

### Post by varunendra on 2014-04-08
Sorry, with my current inability to respond back in time or dedicate much time on forums, I may not be able to help you further.

For now, the only suggestion I have for you is to try the following -
```
sudo iw reg set AU
```

Then check -
```
iw reg get
```
It should now show country code 'AU' instead of '00'. If this doesn't help, these are people who I think may be able to help you - chili555, Wild Man, praseodym, Hadaka. These are also busy people, so I can't say anything about their availability either.

Sorry once again, I wish I could help, but right now I'm not able to.

---

### Post by joeybananas12 on 2014-04-08
Still no luck I'm afraid.

Thank so much for taking time to help in any case.

I'll make do for now  :)

---

