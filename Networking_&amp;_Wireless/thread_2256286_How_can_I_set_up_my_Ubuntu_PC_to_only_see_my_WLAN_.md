---
title: "How can I set up my Ubuntu PC to only see my WLAN but not other WLANs?"
date: 2014-12-11
forum: Networking &amp; Wireless
---

### Post by Ulf_Dunkel on 2014-12-11
I maintain some Ubuntu PCs which should be set up to auto-connect to my friends' WLAN when they see it. I have simply set up the PCs in their locations, selected the friends' WLAN, entered the WLAN password once and everything seemed to work fine. But now some of these friends complain that they are randomly re-asked for a WLAN password.

How can I set up things in Ubuntu so that only a specified WLAN will be used if any?
How can I assure that the successfully entered password has been stored successfully, too?

Goodie question:
How can I do all this via console? (I have access to their PCs via VPN.)

---

### Post by bobthebaritone on 2014-12-12
[SIZE=2][FONT=comic sans ms]Hi Ulf_Dunkel,[/FONT][/SIZE]

[FONT=fixedsys][COLOR=#000000][/COLOR][/FONT][COLOR=#000000]How can I set up things in Ubuntu so that only a specified WLAN will be used if any?>[/COLOR][FONT=fixedsys][COLOR=#000000][/COLOR][/FONT][FONT=fixedsys][SIZE=1][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=comic sans ms][COLOR=#000000]This [/COLOR][COLOR=#000000]depends[/COLOR][COLOR=#000000] a lot on the version of Ubuntu you are using. Following the doco at [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager) and ensure that you end up with files that specify your desired outcome.


[/COLOR][/FONT][/SIZE][SIZE=1][FONT=arial][COLOR=#000000]How can I assure that the successfully entered password has been stored successfully, too?>

[/COLOR][/FONT][/SIZE][SIZE=2][COLOR=#000000][FONT=comic sans ms]This makes me think you may not be using network-manager. It is a simple process using network-manager to edit the wireless connection, and check the passphrase. 

[/FONT][/COLOR][/SIZE][SIZE=1][FONT=arial][COLOR=#000000]Goodie question:[/COLOR]
[COLOR=#000000]How can I do all this via console? (I have access to their PCs via VPN.)

[/COLOR][/FONT][/SIZE][SIZE=2][COLOR=#000000]Try nmcli...network manager at the command line!

Cheers,

Bob

[/COLOR][/SIZE]

---

