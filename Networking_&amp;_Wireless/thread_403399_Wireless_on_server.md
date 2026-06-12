---
title: "Wireless on server"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by astronouth7303 on 2007-04-07
On Monday, I'll be able to access my feisty server. I have until Wednesday morning to make this work.

I have a Belkin High-Speed 802.11G card (model FSD7001), chipset is Broadcom BCM4306KFB.

I need to install it on a headless server (no X) and be able to configure it later from the command line (I won't know the wireless configuration it until I get there on Thursday).

The server is running Feisty Fawn server edition using the desktop kernel. (Still can't get ACPI to work. :rolleyes:) The hardware is that of a desktop, so I do have a keyboard, mouse, and monitor available.

I'm not going to worry about trying to bridge the current ethernet connection and the future WiFi one.

I figured I should get a head start on directions.

What web pages describe this? Can anyone post some step-by-steps? I'm not very good with Linux yet, so I appreciate any information posted.

---

### Post by spd106 on 2007-04-07
You can get the bcm43xx driver firmware from [here]("http://linuxwireless.org/en/users/Drivers/bcm43xx"), it should be a simple matter to extract the files ready for copying to the /lib/firmware folder when you get to the server.

I would also suggest that you have a copy of the windows driver ready to switch to ndiswrapper in case bcm43xx fails to work. There are many many guides for this around and the process hasn't changed since Edgy.

As you'll be using wireless you will probably want to familiarise yourself with WPA and specifically wpa_supplicant. This forum [thread]("http://ubuntuforums.org/showthread.php?t=318539") covers a lot of the common settings, but might be overkill with all of the EAP types you probably won't need.

Also take a copy of openssh-server, which you will need for remote access. A google search will turn up lots of information about this, but I'll recommend this [page]("https://help.ubuntu.com/community/SSHHowto") as it's ubuntu specific.

---

