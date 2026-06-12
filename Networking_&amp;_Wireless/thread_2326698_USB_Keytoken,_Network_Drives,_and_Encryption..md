---
title: "USB Keytoken, Network Drives, and Encryption."
date: 2016-06-03
forum: Networking &amp; Wireless
---

### Post by ian.canino on 2016-06-03
_Summary:_
I would like to use a USB drive that contains key or keys that I carry around with me as a second factor authenticator, not only for my laptops that I take with me, but also for a personal server at home. I would like to use this USB key for all instances of data access whether local or remote. Is this possible? and what's the setup?

_Setup-_
[LIST]
[*]Home Server (PPC -- Powerbook G4 -- Ubuntu Server 16.04)
[/LIST]
[INDENT]-- Accessible remotely (internet) or locally (LAN) through ssh-key only access (no password)
-- Local and External Drives with sensitive data. Not yet encrypted, but want to)[/INDENT]

[LIST]
[*]Two laptops (Both Intels, Ubuntu Desktop 16.04)
[/LIST]
[INDENT]-- Local drive with sensitive data, not yet encrypted. Each laptops data is 'mirrored' on the Home Server using various Unison implementations. Of course, I would rather just have the home directories stored in Home Server but was  told this implementation is complex for my scale of use.[/INDENT]

[LIST]
[*]No centralized directory service or SSO setup of any kind <-- was told this implementation to be rather complex for the size of my setup. However, each machine has identical username/UID/GID setup for my account on each.
[*]No SAMBA implementation. I have been using primarily sshfs. Open to any other implementations.
[/LIST]

_Use Cases_
[LIST=1]
[*]Turn on any of either of two laptops. Insert USB drive containting key(s), Insert Password to de-crypt local data and access system. The same USB drive is used for either laptops.
[*]When working remotely via said laptops, access into remote Home Server with USB drive still plugged in laptop, poll key(s) as requirement to mount Home Server encrypted drives (and also for logging in).
[*]Use same usb drive when attempting to access the Home Server account/data locally as well and use it to decrypt locate HomeServer drives.
[/LIST]

[U]Known Resources
```
[Setting up Pam for USB Use]("https://linuxconfig.org/linux-authentication-login-with-usb-device")[/U]
``` I haven't yet done this. Is this an appropriate first step for above prospered implementation?

Any advice is appreciated. I hope I was clear and concise.

---

### Post by TheFu on 2016-06-03
SmartCARD  [http://www.tldp.org/HOWTO/pdf/Smart-Card-HOWTO.pdf](http://www.tldp.org/HOWTO/pdf/Smart-Card-HOWTO.pdf)
The Ubuntu way for SmartCards: [http://ubuntuforums.org/showthread.php?t=1557180](http://ubuntuforums.org/showthread.php?t=1557180)

I´ve seen SmartCards used by multiple people in my LUG, but also saw many others fail to get it working due to different issues. Often old/incompatible readers or cards with the wrong standards.  

I decided to go with a Yubikey instead. The versions I have have 4 slots for different purposes. Get 2 of these.

---

### Post by ian.canino on 2016-06-04
This appears to be an implementation that meets my requirements as stated above. However, I would like to avoid the purchase of additional hardware and use my existing stock of USB flash drives. Also the link provided talks about using Smartcards *in lieu *of passwords. Isn't this poor practice as it means it is no longer 'two-factor' authentication? Or is my knowledge of security measures dated?

---

### Post by TheFu on 2016-06-04
> **ian.canino said:**
> This appears to be an implementation that meets my requirements as stated above. However, I would like to avoid the purchase of additional hardware and use my existing stock of USB flash drives. Also the link provided talks about using Smartcards *in lieu *of passwords. Isn't this poor practice as it means it is no longer 'two-factor' authentication? Or is my knowledge of security measures dated?

I don´t have a smartcard, but with PAM you can specify which different methods are required for access.  Also, I thought a smartcard required a pin or password to gain access. It has been over a year since the last time I saw one.

With YubiKey, you can setup OTP plus passwords or just merge both into a single data entry {passwd}+{YubiKey Input} for the total login password. You can swap that around or have *something you know* at the front AND end surrounding the yubikey input.  I didn´t look into the solution too hard because I didn´t want the hassle of setting up OTP on every system for logins, but those systems need to work without network connections too. While my portable devices are more secure than the average person´s, I don´t expect them to be 100% impenetrable. Actually, for the last 4 yrs, I´ve purchased these devices with the plan to leave them behind if anything funny happens in a foreign country - basically, assume they are not trustworthy again.

It is frowned upon to just provide links that google would find, but [https://linuxconfig.org/linux-authentication-login-with-usb-device](https://linuxconfig.org/linux-authentication-login-with-usb-device) for Linux seems reasonable. In the same search results were similar solutions for Windows which I didn´t look at.

OTOH, I know nothing about using USB and key files for anything. Really shouldn´t have responded at all.

---

### Post by ian.canino on 2016-06-09
The link provided relates specifically to login authentication procedures. I am looking for one step further: the presence of a usb drive-ley is required to access a remote encrypted drive as well.

---

### Post by TheFu on 2016-06-10
> **ian.canino said:**
> The link provided relates specifically to login authentication procedures. I am looking for one step further: the presence of a usb drive-ley is required to access a remote encrypted drive as well.

For the remote system, if it is the OS/boot drive that is encrypted, I believe **console** access will be required.  
If it is just a data drive, you can manually decrypt the partition, then mount/umount it as needed.  I do this, just with really, really, really, long passphrases on portable disks. Don´t know of any built-in ways to automate this over a remote connection. I suppose you (or anyone) could setup polling on that connection in a script - perhaps using a reverse ssh connection? Not elegant, but could work.

An interesting problem.  We are well beyond my direct experience.  Making something like this workable for the masses would be a great How-To.

---

