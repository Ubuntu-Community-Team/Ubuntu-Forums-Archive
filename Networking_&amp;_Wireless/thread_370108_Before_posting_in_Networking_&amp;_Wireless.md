---
title: "Before posting in Networking &amp; Wireless"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by bapoumba on 2007-02-25
When troubleshooting wireless, it's important that your system is fully updated by opening a terminal, CTRL+ALT+T. Using a wired internet connection, please run:
```
sudo apt update
sudo apt dist-upgrade
```
and reboot if necessary. 

If the issues persist, it is recommended that you install pastebinit, by running:
```
sudo apt install pastebinit
```
This will enable the wireless script to, upon your approval, upload the obtained data to pastebin, creating at the same time a link to it in your terminal, permitting you to paste it to a forum thread.

Once that's done, download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. You can run it using this command:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

**If you aren't able to connect to the internet with the affected system, including via a wired connection, just [navigate to this link]("https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385")** and follow the instructions there on how to the run wireless script without an internet connection.

If** 'Broadcom' **appears in the output next to **'[0280]'**,  head over to the**[ Broadcom guide]("http://ubuntuforums.org/showthread.php?t=2214110").**

Please choose a clear and informative title when creating your thread:
[LIST]
[*]"Atheros ABC123 drops connection, Ubuntu 14.04", is an acceptable thread title, concise and informative.
[*]"Heeelp, wireless doesn't work", is completely vague and meaningless.
[/LIST]
[INDENT]
[/INDENT]
Here is a list of [supported wireless cards]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") in the Community wiki - which includes PCI, miniPCI, PCMCIA, built-in, and USB. This list is maintained by the Ubuntu community, so please do think about contributing to it, following these [guidelines]("https://help.ubuntu.com/community/WikiGuide").

Further details about the script are available [here]("https://github.com/UbuntuForums/wireless-info").

---

