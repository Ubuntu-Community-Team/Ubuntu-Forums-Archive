---
title: "VPN (PIA) does not work with a Linux encrypted drive or home folder..."
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by linux-ioi on 2016-08-25
Hello, I'm attempting to leave the Windows OS entirely and have installed Ubuntu (MATE) for a test run, but hopefully make it permanent if I can get couple of issues resolved.

One issue is lack of a driver for a Canon scanner I use, but that's not relevant to this forum.

The other issue, which has me posting here involves a VPN service (Private Internet Access) in use here, that apparently is unable to function with/from a fresh installation of Linux  when the installer setup uses either of its encryption options.  I initially chose to have the Linux installer encrypt the entire drive, then installed the PIA-VPN software (v59-v62) and was never able to establish a connection.  I then tried re-installing Linux and only having it encrypt the 'HOME' folder/directory, but still was not able to connect with the PIA-VPN service.  Last, I tried a third fresh Linux install with NO-encryption used, and only then did the PIA software allowed for a connection to their VPN service.  I've inquired for more insight on the issue with PIA, but have not heard back so I'm wondering if anyone here knows of any other VPN service that's confirmed to work WITH/FROM a Linux encrypted drive, or at the very least an encrypted 'HOME' folder?

Thanks much your time.

---

### Post by TheFu on 2016-08-25
If you are using PIA-specific software, contact them for support.
If you are using openVPN (the repo version DOES work with PIA-L2TP, dm-crypt, and 16.04), I'll try to help.  Can't help with other PIA encryption modes - definitely not with PPTP.  So, if you are using openvpn and L2TP, please post your config files to get help. When doing that, please post using "code tags" so they line up nicely. Too hard to read otherwise.

I don't use encrypted home folders, for multiple reasons. The dm-crypt was installed as part of the fresh installation process.

In other posts here, I've helped folks with PIA, so search for that. Just know that dm-crypt disks don't matter at all - at least from what I can tell.  

Oh, and welcome to the forums.

---

### Post by linux-ioi on 2016-08-26
Thanks for the offer to assist.  It is their installer (v59-v62) I've attempted to use.  They only started providing the installer as of v59. Before that I found at their forums a Linux user who had posted instructions on how to setup connecting to the VPN via the Linux ?Network Manager? (I think...), but even after all the hoops were jumped to make that work it appears they could only use the minimal encryption settings (SHA1 authetication, 128-AES encryption, RSA-2048 handshake).  Their all in one installer app. provides better options (SHA-256 authetication, 256-AES encryption, RSA-4096 handshake). I'm completely new to Linux so I'm afraid the info. you asked me to provide is not within my scope just yet.  If what you might be suggesting is the same sort of Network Manager config. setup as the previous noted user at the PIA forums offers, then it'll likely be a waste of your generous offer to help since I'm hoping to keep using the better encryption connection setting in use here.  As far as PIA's installer goes, I noticed all the folders and files PIA installs (both hidden and not) are placed within the Linux 'HOME' folder and I'm assuming since it fails to connect with their VPN when that folder is encrypted (by the fresh Linux install) some of their files are have issue with where they've been installed/placed.  Sorry if that's hard to follow with what I'm trying to say.  Lack of sleep here.  Anyway, going with that line of thought as to the conflict I tried run the PIA (v62) installer from higher/alternate directory other than the encrypted 'HOME' one, but kept being told (in the terminal) I couldn't run it elsewhere within Linux.  I noted all that to PIA days/weeks ago and they've not replied.  My renewal with them is up soon so I was checking in here if other providers were confirmed to work with/from encrypted Linux drives and/or home folders so I can just switch providers if PIA hasn't figured it out and are just keeping silent in hopes most of their Linux users are just willing to for go encrypting their systems.  That's kind of ironic if so, since we pay them to secure data via their VPN to/from the internet so why wouldn't we also want it to be secured at the home/drive level too.Thanks again for your reply.  Hope someone else here can confirm an alternate VPN and/or method of getting PIA's (v62+) installer to work with/on an encrypted Linux system.

---

### Post by linux-ioi on 2016-08-26
Sorry for the above post looking like one long paragraph!!!  Not sure why it did that and I can't seem to correct it!

---

### Post by TheFu on 2016-08-27
> **linux-ioi said:**
> Sorry for the above post looking like one long paragraph!!!  Not sure why it did that and I can't seem to correct it!

DON'T use encrypted HOME. No other solution will work with this either.

DO use encrypted whole disks. Every VPN will work with it. However, by using stock openvpn then the HOME isn't involved with the connections. All that information is stored in /etc/openvpn/ .... IME.

Also, I think you've misread the encryption available between their installer and stock openvpn. Yes, there were some manual steps on their website to use L2TP, but as for block length, I can't imagine PIA was using anything other than openvpn.  We all know the surest way to have broken encryption is to invent your own. That applies to PIA too.

---

