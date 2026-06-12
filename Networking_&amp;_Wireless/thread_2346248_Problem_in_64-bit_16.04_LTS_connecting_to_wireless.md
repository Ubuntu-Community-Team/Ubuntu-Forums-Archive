---
title: "Problem in 64-bit 16.04 LTS connecting to wireless regularly; looking for a patch"
date: 2016-12-12
forum: Networking &amp; Wireless
---

### Post by Tupaq on 2016-12-12
Hello fellow Ubuntu users,
I have the exact same problem described in the link below:
[http://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues](http://askubuntu.com/questions/762198/16-04-lts-wifi-connection-issues)
I am looking for [this]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/ChangeSummary/16.04.1") patch (specifically, patch for Bug 1574347) for my laptop but, though it says it is availible, I can't seem to find the patch itself to download so that I may solve my wireless connection problem.
Thank you all for your help!

---

### Post by Keith_Helms on 2016-12-12
Are you sure you don't already have the fix?  If you've been applying updates it should have come down to you automatically.

If you click on the bug number it takes you here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574347](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574347)

If you then click on Fix Released next to Ubuntu, you'll see this description:

```
**Bug description**

  [Impact]
NM needs to re-read the DEVTYPE after the device name changed, an  example is that WiFi network list disappears from network manager applet
 [Testcase]
1. Boot the system. It should include a wireless device.
2. In a terminal, run 'nmcli dev'.
3. In the correct case, the line for the wireless device should read  "wifi" under the TYPE column. In a failure case, it will read  "ethernet".

 After upgrading to the new version, the repeating the above steps should give expected behavior.
 [Regression Potential]
Potential of causing regression is relatively small for a one line change to re-read a value to be known.
 ---
 Problems:-
 1. The network manager applet does not show the list of WiFI APs it can find.
2. The network manager applet does not the name of the AP to which it is connected
3. The icon of the applet shows two vertical arrows in opposite  direction - the wired connection symbol and NOT the wifi connected icon.
 Temporary Workaround:-
Log out and again log back in.

```

When I run the test case on my 16.04 system, I see 

```
DEVICE    TYPE      STATE        CONNECTION 
wlp3s0    wifi      connected    KHWIFI50   
enp4s0f1  ethernet  unavailable  --         
lo        loopback  unmanaged    --      
```

Which seems to indicate the fix has been applied on my system.

---

### Post by jeremy31 on 2016-12-13
The patch might still be [https://bugzilla.gnome.org/show_bug.cgi?id=764803](https://bugzilla.gnome.org/show_bug.cgi?id=764803)

If you have the networking icon issue try
```
systemctl restart network-manager.service
```

---

### Post by Tupaq on 2016-12-24
Thanks for all the help; I've been using Ubuntu for a while but I'm still not sure how to actually download either of the patches that either jeremy31 or Keith_Helms linked to: I just see code (am I supposed to install this via the terminal?)

---

### Post by Tupaq on 2016-12-24
I'd also like to note here is what I get when I run Keith_Helms' test in my terminal:
DEVICE  TYPE      STATE        CONNECTION 
wlan0   wifi      connected    ATT808     
eth0    ethernet  unavailable  --         
lo      loopback  unmanaged    --

---

### Post by praseodym on 2016-12-25
No need for patching if it is *that* driver:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=[COLOR="#FF0000"]1[/COLOR]" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot. No change? Then repeat it with "2" in the red slot

---

### Post by Tupaq on 2016-12-26
[FONT=arial narrow]Hi everyone,
I now have to reboot my laptop every time I close it to get back on the Internet (but when I click "lock" and leave it open it stays connected). Also, I am unable to update software via Software Updater: It says "failed to download repository information" even though it also says "the software on this computer is up to date" and I'm obviously on the Internet.
I tried praseodym's code with both a "1" and a "2" but have yet to reboot; here is the output with "1" in the red slot:
> options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1.
I think jeremy31's:[/FONT]
systemctl restart network-manager.service

[FONT=arial narrow]may have been the fix I was looking for; I'll get back to you. Thank you!
[/FONT]

---

### Post by Tupaq on 2016-12-26
> systemctl restart network-manager.service didn't work I'm sorry to say, though it did prompt me for my password.

---

### Post by jeremy31 on 2016-12-27
Try praseodym's command using ant_sel=0 as it is usually only needed with newer HP laptops

---

