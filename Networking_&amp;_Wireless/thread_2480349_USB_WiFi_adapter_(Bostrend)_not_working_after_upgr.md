---
title: "USB WiFi adapter (Bostrend) not working after upgrade to 22.04"
date: 2022-10-26
forum: Networking &amp; Wireless
---

### Post by mike98032 on 2022-10-26
Hello,

Yesterday I upgraded to Jammy and lost all network connectivity. I was able to get back wired connectivity by editing /etc/NetworkManager/NetworkManager.conf to "managed=true", yet I can't add back my Bostrend AC3 USB WiFi adapter, after a couple years solely using that device with no issues on the previous version of Ubuntu. 

I can see the device by running the 'lsusb' command (it is manufactured in two pieces that fit together):


[LIST]
[*]Bus 002 Device 004: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
[*]Bus 001 Device 003: ID 0bda:b812 Realtek Semiconductor Corp. 802.11ac NIC
[/LIST]

[LIST]
[/LIST]

Yet I can't find a way to add that to a WiFi network, even using the Network Connection GUI, where I added my static IP address and Gateway the same way I manually setup my wired connection.

BTW, I got this far by following this thread which has so far been very helpful:

[https://ubuntuforums.org/showthread.php?t=2454779](https://ubuntuforums.org/showthread.php?t=2454779)


Any help would be greatly appreciated.

---

### Post by morrownr on 2022-10-26
Hi Mike,

Your device ID indicates the chipset in your adapter is a Realtek rtl8812bu. Here is a repo with a driver and extensive instructions:

[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

If you did an upgrade and did not remove the old driver first, you may want to go to the section on Driver Removal first and run:

$ sudo ./remove-driver.sh

...so as to clean things up a bit. Then you can start at the beginning of the README (or the Installation Instructions).

The url to the Main Menu is shown below as it may have information of interest to a Linux usb wifi user:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Nick

---

### Post by mike98032 on 2022-10-27
Thank you Nick. I will try this when my schedule clears out and report back. Much appreciated!

---

### Post by mike98032 on 2022-10-29
@[COLOR=#000000]morrownr I located my driver directory, "[/COLOR]rtl88x2bu-5.8.7.4.37264.20200922",[COLOR=#000000] installed the script and ran it. 

It displayed the following:

[/COLOR]Error! The module/version combo: rtl88x2bu-5.13.1 is not located in the DKMS tree.
Deleting 88x2bu.conf from /etc/modprobe.d
Deleting rtw88_8822bu.conf from /etc/modprobe.d
Deleting source files from /usr/src/rtl88x2bu-5.13.1
The driver was removed successfully.

After reboot I ran 'dkm status' and got this result:

rtl88x2bu/5.8.7.4.37264.20200922, 5.4.0-131-generic, x86_64: installed

I didn't expect this, but maybe I'm not understanding it. Do you think I'm ready to delete the driver directory and install a new driver?



[COLOR=#000000]

[/COLOR]

---

### Post by morrownr on 2022-10-29
> I located my driver directory, "rtl88x2bu-5.8.7.4.37264.20200922", installed the script and ran it.

Oh my. There is a lack of communication going on here. The above is an old driver that you have previously installed. It is not the driver I sent you to. There should be no "installed" to the script I talked about as it is part of the driver that you should download from my site.

Let's start over.

We need to purge that old driver you have installed. Try 

$ sudo dkms remove -m rtl88x2bu -v [COLOR=#000000]5.8.7.4.37264.20200922[/COLOR] --all

Then run $ dkms status again and if there is nothing reporting, things are probably clean enough. You can then delete that old driver directory.

Once that is complete, go to the driver repo I sent:

[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

...and follow the installtion instructions.

Nick

---

### Post by mike98032 on 2022-10-29
Nick,

When I say I installed the script and ran it, I meant the driver removal script:

sudo ./remove-driver.sh

That is what displayed the verbose message.

---

### Post by morrownr on 2022-10-29
> **mike98032 said:**
> Nick,

When I say I installed the script and ran it, I meant the driver removal script:

sudo ./remove-driver.sh

That is what displayed the verbose message.

Mike,

Yes, I recognize the message. Disregard the part where it says ERROR as that dkms telling us you did not have the version of the driver the script was looking for. I probably need to supress that line and maybe add a routine to look for old stuff and remove it. My concern was that it appeared that you copied the script into the directory from the old driver which was not what I intended.

Did you do the rest of what I mentioned?

Nick

---

### Post by mike98032 on 2022-10-30
Nick,

Thanks for your help. The new driver is installed and my WiFi adapter came to life. I turned off my wired connection and did an internet speed test running off my WiFi and it was fast. However I can't get to websites so I will probably delete my WiFi profile and add that back.

-Mike

---

### Post by morrownr on 2022-10-30
Mike,

Forgetting all previous WiFi profiles is a good idea. It may be a good idea to run the following from the driver directory so as to check settings:

$ sudo ./edit-options.sh

I default the driver to USB2 but if you are using the adapter in a USB3 port, there is a setting there to turn USB3 support on. There is documentation in the file that is opened by the above and it could be a good idea to take a look. The chipset you are using along with the driver you now have installed can be very fast in managed mode. 

Something to keep in mind is that the driver is constantly updated, A good way to update is:

$ git pull
$ sudo ./remove-driver.sh
$ sudo ./install-driver.sh

An update evert 3-4 months can be a good idea. If you are installing an update that updates the kernel version from say 5.15 to 5.19 then you need to do the above before you do the upgrade or you might be without internet when you reboot.

Good luck.

Nick

---

