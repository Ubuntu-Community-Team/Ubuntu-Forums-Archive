---
title: "RaLink 5370 must unplug and re-plug after boot to connect, Ubuntu 18.04.4 Minimal"
date: 2020-02-29
forum: Networking &amp; Wireless
---

### Post by stevetheburger on 2020-02-29
Hello Ubuntu Forums,

I am attempting to connect my Dell Optiplex 755 desktop to my university's wifi using a RaLink 5370 adapter over wpa_supplicant. Fortunately, after a lot of hair pulling I figured out that the adapter works after I remove the adapter and put it back in. While this is a much better situation than what I was in earlier, I do find having to remove and replace the adapter on each boot up to be irritating. This would also prevent me from connecting on boot which would theoretically enable me to auto-sync git repositories with a remote server I have set up at home, which is the end goal of this project. While my computer does have a perfectly good ethernet card, my dorm room does not have an outlet for it, otherwise I would be using that. Also, the Ubuntu I am using is the minimal image, so it lacks a desktop environment, only having the console.

Since then I have done some research into the supplicant as well as kernel modules, and learned a lot that I did not know before, however I still do not see what the problem is as the supplicant works perfectly after the remove and replace, which seems to me to point to a driver issue that occurs during the boot; however, the computer appears to recognize my adapter correctly, although giving it a rather absurd interface name. 

The modules that lsmod gave after boot included rt2800usb, rt2x00usb, rt2800lib, and rt2x00lib. I did a comparison using cat and diff between lsmod before removing and replacing the adapter, lsmod after replacement, and lsmod after connecting successfully. It appears that it is using the correct driver(s) and, if I understood it correctly, according the Kconfig file here: [https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tree/drivers/net/wireless/ralink/rt2x00/Kconfig](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/tree/drivers/net/wireless/ralink/rt2x00/Kconfig), the rt2800usb should support my adapter's chipset. The only difference was that after connecting the ccm driver was applied, which after some short research appears to me to be a cryptographic module, probably involved with the supplicant.

I digress. So, here is the pastebin for the wireless-info taken after boot. A more experienced set of eyes might be able to find the issue there.
[https://pastebin.com/CxiJbdTr](https://pastebin.com/CxiJbdTr)

Thank you and please let me know if more information is needed.

---

### Post by chili555 on 2020-03-02
Your file /etc/network/interfaces and your netplan file call for connection to different access points and different passwords.

In fact, /etc/network/interfaces  is deprecated in favor of netplan. Please revert the file to its default state:

```
auto lo
iface lo inet loopback
```Next, let's check netplan for any errors:

```
sudo netplan generate
sudo netplan -debug apply
```

Are there any interesting messages there?

Next, I recommend that your regulatory domain be set explicitly. Check yours:

```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

```
sudo nano /etc/default/crda
```

Change the last line to read:

```
 REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Reboot and show us:

```
dmesg | grep wlx
```

---

### Post by stevetheburger on 2020-03-03
Hello chili555,

So I have changed the interface file back to its original settings and set the country code to my country.

Neither run of netplan printed anything.

For the output of dmesg | grep wlx I got:
[     11.823502] rt2800usb 2-3:1.0 wlx000f00586099: renamed from wlan0
[     12.699891] IPv6: ADDRCONF(NETDEV_UP): wlx000f00586099: link is not ready

---

### Post by chili555 on 2020-03-03
Is Network Manager installed and running?```
ps aux | grep -i network
```If so, we wonder why you tried to get the wireless working with /etc/network/interfaces AND netplan and yet didn't use Network Manager.

That is a lot of conflicting hands on the steering wheel!

---

