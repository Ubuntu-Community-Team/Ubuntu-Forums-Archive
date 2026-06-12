---
title: "How to get ThinkPad 11a/b/g/n Wireless working? Please help!"
date: 2008-01-15
forum: Networking &amp; Wireless
---

### Post by lemonicetea on 2008-01-15
I followed the procedure on the ThinkWiki..
[http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)
Everything is OK, while I type: "ndiswrapper -l". It says :"net5416         driver installed, hardware (168C:FF1D) present" But when I type ifconfig or iwconfig, It did not give anything like wlan0, just as the instruction say..Anybody know the reason of this? Any suggestion is welcome. Cheers.

---

### Post by bismark on 2008-01-15
> **lemonicetea said:**
> I followed the procedure on the ThinkWiki..
[http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)
Everything is OK, while I type: "ndiswrapper -l". It says :"net5416         driver installed, hardware (168C:FF1D) present" But when I type ifconfig or iwconfig, It did not give anything like wlan0, just as the instruction say..Anybody know the reason of this? Any suggestion is welcome. Cheers.

Which a/b/g/n card do you have? Is it the Atheros AR5418, which you can find by typing ```
lspci | grep -i wireless
```?

If it is then I have found the best way to get it "working" is to follow the instructions on madwifi.org at [http://madwifi.org/wiki/UserDocs/GettingMadwifi]("http://madwifi.org/wiki/UserDocs/GettingMadwifi") in the section "Downloading via Subversion"

Also read [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

About the only additional thing you need to do then is modify /etc/default/linux-restricted-modules-common to have DISABLED_MODULES="ath_hal" set.

This has been the only way I've been able to get the AR5418 a/b/g/n to work somewhat reliably, never had any luck with ndiswrapper.

---

### Post by lemonicetea on 2008-01-17
Thanks Bismark:
I am still a newbie..I followed the "downloading via subversion". Then I dunt know what to do next...Could you give me some stey by step instructions. Thanks a lot.What is that subversion thing for?

---

### Post by bismark on 2008-01-17
> **lemonicetea said:**
> Thanks Bismark:
I am still a newbie..I followed the "downloading via subversion". Then I dunt know what to do next...Could you give me some stey by step instructions. Thanks a lot.What is that subversion thing for?

Subversion explanation: [http://en.wikipedia.org/wiki/Subversion_%28software%29](http://en.wikipedia.org/wiki/Subversion_%28software%29)

That's much easier to read then anything that I could type up and would probably be wrong in ;)

First off you'll need to prepare your workstation to build the drivers.  You'll need the following packages installed.

```
sudo apt-get install build-essential sharutil gcc linux-headers-`uname -r`
```

Then follow these instructions on ThinkWiki, [http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008]("http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008")

Finally, edit /etc/default/linux-restricted-modules-common so that it looks like so
```

...
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"

```

Additional links found in the forums and on madwifi.org
[http://ubuntuforums.org/showthread.php?t=588890](http://ubuntuforums.org/showthread.php?t=588890)
[http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY](http://ubuntuforums.org/showthread.php?t=572971&highlight=AR5418+GUTSY)
[https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi](https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi)
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by lemonicetea on 2008-01-18
Hi,Bismark:

Thank you very much for your help..I have successfully installed the driver get it working now. Now I have another problem about the screen resolution. Do you have any suggestions? Presumably you have the same laptop as I do.

Here is the link to the post:
[http://ubuntuforums.org/showthread.php?t=671029](http://ubuntuforums.org/showthread.php?t=671029)

Thanks again for your help!

---

### Post by bismark on 2008-01-18
> **lemonicetea said:**
> Hi,Bismark:

Thank you very much for your help..I have successfully installed the driver get it working now. Now I have another problem about the screen resolution. Do you have any suggestions? Presumably you have the same laptop as I do.

Here is the link to the post:
[http://ubuntuforums.org/showthread.php?t=671029](http://ubuntuforums.org/showthread.php?t=671029)

Thanks again for your help!

Unfortunately if you are using the newest drivers then I can't really help you out.  I tried them out and ended up reverting back to what was in the Feisty Repository.
```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1700
OpenGL version string: 2.0.6334 (8.34.8)

```

I know when I tried the newest ATI drivers out I could never get my display to run at 1680x1050.

Update:
It seems the ATI driver just released to day might have fixed this issue.
[http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html)

Check it out.  I usually wait until the drivers are in Envy and use that to install them.

Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

