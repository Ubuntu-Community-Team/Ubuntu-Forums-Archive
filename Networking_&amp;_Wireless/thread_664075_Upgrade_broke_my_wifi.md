---
title: "Upgrade broke my wifi"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by elainevdw on 2008-01-10
I had a pretty old install of Xubuntu on my computer, but the wifi worked just fine. Today I decided to boot it up and upgrade everything. It said there was a new version of Ubuntu to install, so I walked through the steps. The only problem it had upgrading was with Samba -- three Samba packages installed with errors, but browsing through the forums I fixed all of that, so everything should be installed perfectly now. I'm not totally upgraded, though, because there are some packages that I needed to download stuff for before installing, and with the wifi down, I can't.

When I run iwconfig, it finds wlan0, running on the proper ESSID and everything. But the Link Quality, Signal level and Noise level are all 0. I can't ping my router (192.168.1.1) -- it says "Network is unreachable." 

If I run ifconfig, it tells me that the IP is 127.0.0.1 and the subnet mask is 255.0.0.0, so it's very obviously not connecting to anything.

If I run ifup wlan0, it says "Interface wlan0 already configured."

I ran invoke-rc.d networking restart, and it didn't help... ended with "No DHCPOFFERS received."

Oh, and it can't see any of the wifi connections in my apartment complex, either (there are usually about half a dozen of them at any given time). I forget what the command for that was, but it doesn't see them.

Any ideas about what I can do?

Thank you so much!

---

### Post by Agent86 on 2008-01-11
Hello! Need a little more info. What kind of wireless card do you have? Run the following command in a terminal:

```
lspci
```
and post the output here. Try this command too:

```
sudo /etc/init.d/networking restart
```
and post that output. Do you know what kind of wireless security you are using? WEP, WPA, WPA2, none?

And which version of Xubuntu are you running now? 7.10 (Gutsy Gibbon), 7.04 (Feisty Fawn), 6.10 (Edgy Eft)?

---

### Post by pytheas22 on 2008-01-11
Another thing to check is that your card is running in the proper mode, which is probably 11g.  If it's in 11a or 11b it may not be able to see networks running on 11g.  Post the output of

```
iwconfig wlan0
```

> I forget what the command for that was, but it doesn't see them.

that command would be iwlist wlan0 scan

---

### Post by elainevdw on 2008-01-11
Agent86 and pytheas22, thanks for your help!

You know what is so bizarre? I booted up this morning and started running the commands you asked for to give you the output... and after running iwconfig one more time, I noticed that it was showing a strong signal level! Which it wasn't doing yesterday! So I started up Firefox and sure enough, it's working again.

That is so weird. All I did was reboot the system and take the card out (to get the exact model number) and then plug it back in. I did both of those things yesterday too and it didn't help at all.

Hopefully it will continue working. I appreciate your time. :KS

Have a great week,

Elaine.

---

