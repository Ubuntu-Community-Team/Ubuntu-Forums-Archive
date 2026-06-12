---
title: "No Wifi on Lenovo Thinkpad T60 (Gutsy)"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by johann_p on 2007-10-16
I have installed Gutsy prerelease on my Lenovo T60, installed all the updates and had no luck getting the Wifi to work.

The network manager shows the SSIDs of available networks (including mine with high strength) and when I click on that network, a GUI is shown where I can enter my passphrase and where WPA is already selected as the encryption.

After entering the passphrase and clicking OK, the computer tries to connect for a while, then obviously fails and re-shows the GUI with the passphrase information.

I have triple-checked that the passphrase is entered correctly (and clicked to display it) this is definitely not the cause.

When I run kwifimanager while trying to connect to the wlan, it shows the SSID correctly after a while and then shows the MAC of my WLAN router correctly, but never is able to obtain an IP. So it seems everything works except the WPA authentification.

I am really disappointed with WLAN support -- I have tried this with several computers, several wifi cards and several versions of Ubuntu now and never had any luck connecting to my WPA-protected network.

I really do not know what to do --- I NEED to connect my laptop to that network and changing the securtiy to anything other than WPA is definitely not an option and outside of my control.

Administrator is telling me to use Windows instead (which I have tried and which works).

Frustratingly, I have seen posts on the internet where people claim that this is supposed to work, but no error message or other indication what could be different is displayed.

I'd even be prepared to buy an additional Wifi PCI card if there was a *guarantee* that it will work -- but seeing so many unanswered help posts about people struggling with things that are supposed to work, I am a bit sceptic.

(BTW, I also tried the same laptop with OpenSuse 10.3 before I installed Gutsy and the WLan did not work there either).

                                                               __________________

---

### Post by MountainX on 2008-02-21
I'm in the same boat with a T61p and Gutsy. ... could use some help.

---

### Post by tashmooclam on 2008-02-21
My response may or may not be useful. I installed 7.1 on a Dell laptop with a Broadcom mini card for wireless. After much trouble, I decided to just swap the card with an Intel card ($25 ebay). The Dell website had diagrams, etc. for installing the card, which I followed. This SOLVED all wireless issues. Ubuntu 7.1 contains the Intel wireless card drivers.

---

### Post by MountainX on 2008-02-23
See if this thread helps you:
[http://ubuntuforums.org/showthread.php?t=699442http://ubuntuforums.org/showthread.php?t=699442](http://ubuntuforums.org/showthread.php?t=699442http://ubuntuforums.org/showthread.php?t=699442)

---

