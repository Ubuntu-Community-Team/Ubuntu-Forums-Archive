---
title: "Broadcom problem"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Vodka_island on 2008-11-04
Hi!

My wireless card is not working and I've browsed the forums and google and sorry for making my own thread as am sure this has been asked alot but could I get help installing the drivers?

My card is Broadcom 802.11a/b/g and I think I downloaded the correct driver (windows version) but can't get it to work on Ubuntu.

I have installed ndiswrapper. My attempt to install was I extracted the .exe (I ran the installer in Windows and unzipped the data onto removable media)

There was 2 .ini files in it and tried to 'ndiswrapper -i filename.ini' in the console. However it did not work?

Could anyone help me? Even point me to the correct url for the driver (am an inexperienced/newbie user).

Anyways am impressed with linux and think the community is great but wouldnt trust my granny with it :guitar:

Thanks in advance!

---

### Post by Ayuthia on 2008-11-05
> **Vodka_island said:**
> Hi!

My wireless card is not working and I've browsed the forums and google and sorry for making my own thread as am sure this has been asked alot but could I get help installing the drivers?

My card is Broadcom 802.11a/b/g and I think I downloaded the correct driver (windows version) but can't get it to work on Ubuntu.

I have installed ndiswrapper. My attempt to install was I extracted the .exe (I ran the installer in Windows and unzipped the data onto removable media)

There was 2 .ini files in it and tried to 'ndiswrapper -i filename.ini' in the console. However it did not work?

Could anyone help me? Even point me to the correct url for the driver (am an inexperienced/newbie user).

Anyways am impressed with linux and think the community is great but wouldnt trust my granny with it :guitar:

Thanks in advance!

Well, the Windows driver should be a bcmwl5.inf.  The Vista drivers will not work on ndiswrapper.  You will also need a bcmwl5.sys (32-bit) or bcmwl564.sys (64-bit) file to help make it all work.

Here is a link that might help:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

