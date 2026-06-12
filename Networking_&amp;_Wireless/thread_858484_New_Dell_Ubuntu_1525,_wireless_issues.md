---
title: "New Dell Ubuntu 1525, wireless issues"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by JeepinDoug on 2008-07-13
Hi all, I am a new Ubuntu user.
I received my dell 1525 with Ubuntu 7.10 a couple of days ago. I turned on the box and directly went to Update Manager to catch all the updates. The box had a wireless connection the second I entered my WEP key.
During a large file download the box locked up.
Hard boot was the only choice.
This happened again during the same download.

I thought it would be a good idea to update to 8.04 and did so.
The 64 bit install went flawlessly from disc, then Update Manager again.

At this point wireless network sees my router but will not connect to the internet.
I thought it may be a driver issue.
My box has a Intel Corp PRO/wireless 3945ABG,
Hardware Support quotes;
"Works perfectly on a fresh Ubuntu 6.06 (Dapper) installation. On older versions, works if you manually install the ipw3945 module (from ipw3945.sf.net), the ipw3945 daemon and the ipw3945 firmware ucode (requires ieee80211 kernel support). Not detected at all on my system. Automatically detected and correct drivers loaded on Edgy, Gutsy and Hardy." 

What do I need to do here?
8.04 is Hardy, correct?
TIA, Doug

---

### Post by JeepinDoug on 2008-07-14
Since help is fairly slim here, let me update my progress.

Network wireless set up changed when updating from 7.10 to 8.04.1.
With 7.10 I went; SYSTEM/ADMINISTRATION/NETWORK. Clicked properties for wireless connection, down arrowed my ESSID, set password type, entered WEP key and set configuration for DCHP. Allowed the configuration to establish and BAM! Online access!

Since the 8.04.1 reformat this sequence didn't work. I had to go SYSTEM/ADMINISTRATION/NETWORK and click "enable roaming". 
Then left click the "Manual network configuration" in the top right corner of the screen> Now signal strength of all local wireless systems show. Click the radio field of my signal and it prompts;
Wireless security>
   WEP 128-bit passphrase
   WEP 64/128-bit hex
   WEP 64/128-bit ASCII
   LEAP
Passphrase or Key>
Authentication>
   Open System
   Shared key


My wireless security is WEP mode, 64 bit 10 hex digits> I must assume WEP 64/128-bit hex is the field I select on my box.

Didn't work, my wireless card sees the signal strongly but will not connect (logon to my router).
**I also disabled my security for my router, open to my neighborhood and I still couldn't get on it.**
Security issue or driver issue?

Hopefully someone will gain from this info and I assure you I will post a successful conclusion, I promise.

---

### Post by JeepinDoug on 2008-07-15
Update;
System/ Admin/sofware sources. go to Updates, check Unsupported updates (hardy-backports).
Go to terminal, command;
sudo apt-get install linux-backports-modules-hardy-generic

Reboot and login to your wireless.
It does ask for a Admin pass to unlock a keyring.
I don't know how to enable auto enter this though.
Solved.

---

