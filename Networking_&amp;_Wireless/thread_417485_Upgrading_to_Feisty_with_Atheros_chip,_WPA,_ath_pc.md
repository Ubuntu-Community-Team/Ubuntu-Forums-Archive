---
title: "Upgrading to Feisty with Atheros chip, WPA, ath_pci driver and Belkin AP"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by petermck on 2007-04-21
Hi
I've just upgraded to Feisty and I'm very impressed with the progress that's been made. Thankyou to everyone that worked on it. I'm glad I made the change.
Unfortunately when I tried the network upgrade it locked up half way through. I then could not reboot. I had to resort to the CD with a clean install from scratch (I needed to clean it out anyway). The ability to role back from an upgrade, or gracefully exit and role back is really a must. I had everything backed up, but still...
Once I had it installed everything seemed to be a lot easier to set up. Especially the media stuff for Gstreamer viewing .wmv files etc.
Anyway, the main problem I had was setting up my wireless connection. I have a Toshiba Satellite M50 laptop with an Atheros chip (AR5005 I think), and a Belkin AP.
I could get it to work on Edgy with wpa_supplicant, but not with network-manager-gnome (NMG). Since this is now standard on Feisty I thought I'd give it another go. In the past I had tried NMG with the plain passphrase, passphrase in quotes, hex passphrase, every combination, nothing worked, but I knew WPA Supplicant worked because I could connect without NMG.
Initially I had the same problem with Feisty. Neither plain or hex passphrases would work. This time I decided to have a look at the Belkin AP (model F5D7230). 
It turns out this has an option under the security setting to 'obscure' the passphrase for WPA or not. It was set to [COLOR="black"]**not **[/COLOR]obscure. As soon as I changed this and rebooted the AP I could connect. 
Key ring manager still does not store the passphrase properly (I get a prompt for the keyring password at login, but I'm not so concerned about that), but other than that wireless is now working fine.
Hope this helps someone.  :)

---

### Post by spd106 on 2007-04-22
The keyring-manager issue is by design, however you can get round it by installing the pam-keyring package and editing the /etc/pam.d/gdm file. The details are available somewhere in the forum.

---

### Post by petermck on 2007-04-22
Thanks for the advice. When you say 'by design' are you referring to the design of network-manager or Keyring? I have another password stored in Keyring for access to a networked share, but the first time I rebooted, Keyring asked if I wanted to allow file manager to access once or always. I chose always and its never asked this again.

---

### Post by spd106 on 2007-04-23
To be honest I not fully certain why this happens, I got the information from this FAQ [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-db70c07a5d8c88d63faf6b9b98d94cec5307cd04](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-db70c07a5d8c88d63faf6b9b98d94cec5307cd04)

There is a guide to installing it here [http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

---

### Post by drumkitcat on 2007-05-16
> **petermck said:**
> Hi
I've just upgraded to Feisty and I'm very impressed with the progress that's been made. Thankyou to everyone that worked on it. I'm glad I made the change.
Unfortunately when I tried the network upgrade it locked up half way through. I then could not reboot. I had to resort to the CD with a clean install from scratch (I needed to clean it out anyway). The ability to role back from an upgrade, or gracefully exit and role back is really a must. I had everything backed up, but still...
Once I had it installed everything seemed to be a lot easier to set up. Especially the media stuff for Gstreamer viewing .wmv files etc.
Anyway, the main problem I had was setting up my wireless connection. I have a Toshiba Satellite M50 laptop with an Atheros chip (AR5005 I think), and a Belkin AP.
I could get it to work on Edgy with wpa_supplicant, but not with network-manager-gnome (NMG). Since this is now standard on Feisty I thought I'd give it another go. In the past I had tried NMG with the plain passphrase, passphrase in quotes, hex passphrase, every combination, nothing worked, but I knew WPA Supplicant worked because I could connect without NMG.
Initially I had the same problem with Feisty. Neither plain or hex passphrases would work. This time I decided to have a look at the Belkin AP (model F5D7230). 
It turns out this has an option under the security setting to 'obscure' the passphrase for WPA or not. It was set to [COLOR="black"]**not **[/COLOR]obscure. As soon as I changed this and rebooted the AP I could connect. 
Key ring manager still does not store the passphrase properly (I get a prompt for the keyring password at login, but I'm not so concerned about that), but other than that wireless is now working fine.
Hope this helps someone.  :)


Hi,

I also have a Toshiba Satellite laptop, and currently running Edgy. I'm considering upgrading to Fiesty.

Can you tell me what software you used to back up everything, and what exactly you did back up? I would like to either make an image of the drive somehow, or at least get an iron-clad backup before proceeding to upgrade.

thanks

Paul

---

