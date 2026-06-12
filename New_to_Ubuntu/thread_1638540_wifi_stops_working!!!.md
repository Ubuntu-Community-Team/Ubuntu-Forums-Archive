---
title: "wifi stops working!!!"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by ypokharel on 2010-12-05
i have installed ubuntu 10.10 and i am a new user. the wifi was working fine till today but automaticlly stops working and in the sign of wifi "networking disabled" pop up. i have ubuntu and windows both in my laptop. Wifi works fine in windows but dosent on ubuntu....Need help ASAP...and sound is also not working. My laptop is SONY VAIO VPCEB24FX.

---

### Post by anewguy on 2010-12-05
Open a terminal window, type the following, and post all of the outputs back here so we can see what type of wireless adapter chipset you are dealing with:

lspic <press enter>

lsusb <press enter>

iwconfig <press enter>

ifconfig <press enter>

lshw -C network <press enter>


We need to know all of that so we can see what driver you might need.  In the mean time, there is something you can try on your own:

- temporarily hardwire your laptop to your router

- open a terminal window and type:

sudo apt-get update <press enter>  Wait for that all to finish.

- open System/Administration/Other Drivers.  If there is a driver listed there for your wireless, enable it.  It may download something when you do, so wait for it to finish.

- physically disconnect the hardwire to your router

- right-click on the network manager icon and be sure "Enable Wireless" shows and is enabled.

- left-click on the network manager icon to see if wireless networks show.


Remember, if your router doesn't broadcast the ESSID (e.g., it's a hidden network), you must left-click of the network manager icon and select "Connect To Hidden Network" option.

If you use encryption, you must specify it and match the password/passphrase.

Dave ;)

---

