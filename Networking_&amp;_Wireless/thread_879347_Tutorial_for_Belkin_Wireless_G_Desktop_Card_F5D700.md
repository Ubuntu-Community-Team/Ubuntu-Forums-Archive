---
title: "Tutorial for Belkin Wireless G Desktop Card F5D7000UK on Orange Broadband"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by ernz on 2008-08-03
Hi! I put this tutorial together specifically for people with the Belkin Wireless G Desktop Card and who are using Orange broadband (UK). Note that the exact make and firmware of your card may differ slightly from my own. In which case, I recommend you read [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) thoroughly 
before attempting this tutorial. 

According to Ndiswrapper, this is MY card info:
20. Card: Belkin 54g Wireless Network Card F5D7000uk

*      Chipset: Unknown, lspci gives 'Belkin Unknown device 700f (rev 20)'
*      pciid: 1799:700f
*      Driver: Ndiswrapper 1.45, driver from CD - blkwgdv7

THESE INSTRUCTIONS ARE TAYLORED TO THIS CARD FOR ORANGE BROADBAND!

Note that you will also need the original installation CD with the XP drivers. I am requesting permission to post the driver files with this post, as a user has already requested them.

The initial steps of this tutorial require a hard-wired ethernet connection for settings management and driver downloads. Work-arounds can be found at the Ndiswrapper link above.

[SIZE="6"]Step 1[/SIZE]

Blacklist the free drivers using...
```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

[SIZE="6"]Step 2[/SIZE]

Install ndisgtk using..
```
sudo apt-get install ndisgtk
```

[SIZE="6"]Step 3[/SIZE]

Access the Windows Wireless Drivers frontend for Ndiswrapper through System > Administration. 

Hit Install New Driver, and navigate to the .inf file for the XP drivers. (I would keep a local copy of these files too, just incase the CD goes missing)

[IMG]http://www.freeimagehosting.net/uploads/fd1b7c6bfd.png[/IMG]

If it doesn't look like this:

[IMG]http://www.freeimagehosting.net/uploads/9bd127eebf.png[/IMG]

Then something is wrong with the card or drivers.
[SIZE="6"]
Step 4[/SIZE]

Ensure that your wireless is actually up and running on your Livebox. Orange makes the process very easy, and child-like PROVIDED you use windows or a Mac. They are reluctant to give you the router admin IP over the helpdesk so we have to do a bit of tinkering to make this work properly. Here is how to make sure wireless is up and running on the Livebox...

Navigate to IP address [http://192.168.1.1](http://192.168.1.1) in firefox...
[IMG]http://www.freeimagehosting.net/uploads/54fc4596ac.png[/IMG]

Log in with:
```
Username: admin
Password: admin
```

Click Security > Wireless Connection, and check that your settings all match mine. The blurred parts are just private details I don't want to release into public domain.

[IMG]http://www.freeimagehosting.net/uploads/b6fd6eea23.png[/IMG]

It's a good idea to copy the key into a local text file. Make sure it gets deleted later. Ensure wireless LAN is checked.

In Configuration > Advanced > Wireless make sure your settings look like this:

[IMG]http://www.freeimagehosting.net/uploads/1efa5e9def.png[/IMG]

You should be on WEP security only, with easypairing enabled.

In Configuration > Advanced > Network, ensure DHCP is ON.

[IMG]http://www.freeimagehosting.net/uploads/9d542a7160.png[/IMG]

Restart your Livebox, Press the 1 and 2 buttons on the back of the Livebox (To start "easypairing") and you are now ready to connect. The Wireless light on the Livebox will flash. Note that the default pairing time is around 10 minutes by default. If you take any longer to connect than this, you will need to press the easypairing buttons again.

[SIZE="6"]Step 5[/SIZE]

Restart the PC (I did - Don't know if it actually makes a difference) and unplug the ethernet cable. We are now ready to establish a manually configured wireless connection to the Livebox. Click on the networking applet in the Notification Area and select Manual Configuration.

[IMG]http://www.freeimagehosting.net/uploads/c7e56b25de.png[/IMG]

Unlock the dialog, select Wireless connection and hit Properties for that. Uncheck 'Enable roaming mode'. You should be able to select your Wireless network name (ESSID) from the drop down menu. Give it a minute, it might need time to find it. If it does not find it, then there is something wrong with your drivers, card installation or Livebox. See Ndiswrapper link above for more detailed instructions and ensure your Livebox is configured as instructed. Select WEP key (Hexadecimal) and enter your key EXACTLY as it appeared in the config page. This is where that temporary key file can come in handy - you can just copy and paste it from there. The key is also printed on the underside of the Livebox.

[IMG]http://www.freeimagehosting.net/uploads/d48f0e41f9.png[/IMG]

Ensure the connection settings are Automatically Configured (DHCP) and hit OK. 

Ubuntu will switch network interfaces to the new configuration and you SHOULD now be connected wireless...ly... :)

Hope this helps! :)

---

### Post by regomodo on 2008-08-04
`

---

### Post by regomodo on 2008-08-05
`

---

### Post by regomodo on 2008-08-05
`

---

### Post by ernz on 2008-08-05
Hi Regomodo, Sorry that the tutorial did not help with your specific problem. It looks like your previous ndiswrapper attempts were causing issues, and an incorrect driver was being used. (It was the one I linked you to. Sorry)

I am requesting permission to post the driver files here for anyone else who has similar issues with this card and requires the drivers.

Cheers,
Ernz

---

