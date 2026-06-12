---
title: "Wireless connection drops out in Kubuntu 14.10"
date: 2015-06-11
forum: Networking &amp; Wireless
---

### Post by pwabrahams on 2015-06-11
I'm running Kubuntu 14.10, and I share with many others the problem of my wireless connection dropping out every few minutes.  This does not happen in Windows, and it didn't happen in older versions of Kubuntu.  There have been many reports of this problem but apparently no consensus on a solution.  I've concluded from reading other threads on this issue that iwlwifi is somehow responsible, but there's disagreement about what parameters to provide to it.  I've tried several variations on **iwlwifi 11n_disable=*n***, so far without success.  Does anyone have further wisdom on this subject?  Considering that it only occurs in certain Ubuntu variants, is there any known hardware influence?

---

### Post by mörgæs on 2015-06-13
If would be interesting if you could test 15.10 in a live boot to see if the problem is still there.

---

### Post by pwabrahams on 2015-06-13
I did an update of 14.10, including some additional repositories, and the problem hasn't recurred yet. But who was it who recently said "Absence of evidence is not evidence of absence"?  I can only wait, hope, and see.

I tried 15.10 but gave up on it, at least for the time being, because of several issues, among them the inability to have different wallpapers on different desktops and the lack of window numbers in the window list widget.

---

### Post by mörgæs on 2015-06-13
I think the quote is an old one.

Good, maybe the bug is already fixed in 14.10. You have this release a month more, so best wishes for the remaining time.

Time for marking the thread 'solved'?

---

### Post by pwabrahams on 2015-07-27
I'm still intermittently encountering this problem.

---

### Post by Bucky Ball on 2015-07-28
> **pwabrahams said:**
> I'm still intermittently encountering this problem.

14.10 has reached end-of-life since this thread was posted and is no longer supported so I suggest you upgrade to 15.04 or clean install 14.04 LTS (supported until 2019) and see if you have issues then. The repositories for 14.10 are closed so we can't give you much help with that (as it is no longer supported here or by Canonical). 

Good luck.

---

### Post by pwabrahams on 2015-12-16
I've backed down to 14.04 and I see the same behavior there.  What's more, it's been reported in 15.10.

---

### Post by mörgæs on 2015-12-17
Good, please post the link.

---

### Post by pwabrahams on 2015-12-17
Here's the link:
[https://answers.launchpad.net/ubuntu/+question/266033](https://answers.launchpad.net/ubuntu/+question/266033)

Note that the problem in both 14 and 15 is inconsistent: it looks as though it's been solved and then it turns out it hasn't been solved.

---

### Post by chili555 on 2015-12-17
> **pwabrahams said:**
> Here's the link:
[https://answers.launchpad.net/ubuntu/+question/266033](https://answers.launchpad.net/ubuntu/+question/266033)

Note that the problem in both 14 and 15 is inconsistent: it looks as though it's been solved and then it turns out it hasn't been solved.That's a link to rt61pci dropping; not iwlwifi. They are entirely different.> there's disagreement about what parameters to provide to it. I've tried several variations on **iwlwifi 11n_disable=n**, so far without success. Where n is what? A number? The parameter is clealy described in:```
modinfo iwlwifi
```> <snip>

parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           **11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX** (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
The parameter I suggest is 11n_disable=8.

What's in there now?```
cat  /etc/modprobe.d/iwlwifi.conf
```In my experience, iwlwifi is very sensitive to the access point. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot and tell us if the performance is improved.

---

### Post by pwabrahams on 2015-12-17
I've made the changes you suggested and my wireless connection is working -- for now.  The problem, as usual, is how to determine if it's *really* working.  I've had the experience before of making suggested changes, seeing my wireless apparently working, and then an hour or a day later having it drop out again.  Others have had the same experience.  I'll post again to this thread if and when it fails.  It's just like determining if a particular Turing machine will ever halt.

---

### Post by chili555 on 2015-12-17
We look forward to your further report.

---

### Post by pwabrahams on 2015-12-18
Alas, after a few hours of untroubled operation, I encountered a drop-out again.  If it's relevant, my router is a TP-Link WR841N.  And I only see the problem in Kubuntu 14.x.

---

### Post by pwabrahams on 2015-12-19
I just discovered this in **/var/log/syslog**:

NetworkManager[1060]: <info> (wlan0): IP6 addrconf timed out or failed.

So I've disabled IPV6 in Network Manager.  I'll see if the problem recurs.  But what am I losing by doing this?  And what might be causing addrconf to fail?

---

### Post by chili555 on 2015-12-19
> **pwabrahams said:**
> I just discovered this in **/var/log/syslog**:

NetworkManager[1060]: <info> (wlan0): IP6 addrconf timed out or failed.

So I've disabled IPV6 in Network Manager.  I'll see if the problem recurs.  But what am I losing by doing this?  And what might be causing addrconf to fail?It simply means that Network Manager tried and failed to obtain an IPv6 address. It will use a dummy placeholder fe80::xx address instead.

It probably means that either your wireless access point doesn't support IPv6 or your ISP doesn't yet support it or both. Setting NM to ignore IPv6 saves a few moments looking for what is unobtainable.

Recall that I suggested you ignore IPv6 previously.

---

### Post by pwabrahams on 2015-12-21
Here's what's in syslog after the latest failure:

```
Dec 21 22:55:47 Aspire-E1-731 dbus[706]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 21 22:55:47 Aspire-E1-731 dbus[706]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 21 22:55:48 Aspire-E1-731 NetworkManager[1056]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1832
Dec 21 22:55:48 Aspire-E1-731 avahi-daemon[907]: Withdrawing address record for 192.168.0.106 on wlan0.
Dec 21 22:55:48 Aspire-E1-731 avahi-daemon[907]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.106.
Dec 21 22:55:48 Aspire-E1-731 avahi-daemon[907]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 21 22:55:48 Aspire-E1-731 dnsmasq[1843]: setting upstream servers from DBus
Dec 21 22:55:48 Aspire-E1-731 NetworkManager[1056]: <warn> DNS: plugin dnsmasq update failed
Dec 21 22:55:48 Aspire-E1-731 NetworkManager[1056]: <info> Removing DNS information from /sbin/resolvconf
Dec 21 22:55:48 Aspire-E1-731 NetworkManager[1056]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```
Does this provide enough indication of the problem?

---

### Post by Bucky Ball on 2015-12-21
As chili555 has suggested, but you haven't responded to, click the network icon> Edit> edit the wireless network connection> on the IPv6 tab, set to 'Ignore'. 

See if that makes a difference.

---

### Post by pwabrahams on 2015-12-22
Sorry I was unclear in my last post "Still no joy".  I have disabled ipv6 and I still have problems.  The syslog excerpt in that post seems to have nothing to do with ipv6.  However, before I disabled ipv6 I was indeed getting drops related to ipv6, and the syslog entries from back then do show that ipv6 was the problem.

---

### Post by chili555 on 2015-12-22
> **pwabrahams said:**
> Here's what's in syslog after the latest failure:

<snip>
Does this provide enough indication of the problem?Not really. It just shows that it dropped. Any other clues here?```
cat /var/log/syslog | grep -e iwl -e 80211 | tail -n20
```Are you still in 14.10? We might just upgrade the driver and firmware, if so.

---

### Post by pwabrahams on 2015-12-22
> **chili555 said:**
> Not really. It just shows that it dropped. Any other clues here?```
cat /var/log/syslog | grep -e iwl -e 80211 | tail -n20
``` 

I tried the selective search of syslog you recommended and it showed nothing of interest.   But perhaps I need to try it again the next time the connection drops.  Now that I've nixed IPV6, it happens much less often.

> Are you still in 14.10? We might just upgrade the driver and firmware, if so.

I actually was running 14.10 for a while, but I dropped back to 14.04 when I had trouble updating it.  14.10 is no longer maintained, as you know, while 14.04 is LTS.  Where can I find upgraded driver and firmware that works with 14.04?

---

### Post by chili555 on 2015-12-22
> **pwabrahams said:**
> I tried the selective search of syslog you recommended and it showed nothing of interest.   But perhaps I need to try it again the next time the connection drops.  Now that I've nixed IPV6, it happens much less often.



I actually was running 14.10 for a while, but I dropped back to 14.04 when I had trouble updating it.  14.10 is no longer maintained, as you know, while 14.04 is LTS.  Where can I find upgraded driver and firmware that works with 14.04?Before we proceed, let's verify your exact device:```
lspci -nnk | grep 0280 -A2
```The process may look something like this, but let's get our facts straight before we buy a Ford part for a Mercedes.

Perhaps: [http://ubuntuforums.org/showthread.php?t=2300927&highlight=backports](http://ubuntuforums.org/showthread.php?t=2300927&highlight=backports) Post #5. Maybe...

---

### Post by pwabrahams on 2015-12-22
Here is the information:
```
pwa@Aspire-E1-731:~/.kde/Autostart$ lspci -nnk | grep 0280 -A2
07:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
        Subsystem: Lite-On Communications Inc Device [11ad:0642]
        Kernel driver in use: ath9k

```

---

### Post by chili555 on 2015-12-23
> Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
        Subsystem: Lite-On Communications Inc Device [11ad:0642]
        Kernel driver in use: ath9kYou haven't an iwlwifi device at all. All of this, gleaned from various forum posts, will never help:> I've concluded from reading other threads on this issue that iwlwifi is somehow responsible, but there's disagreement about what parameters to provide to it. I've tried several variations on iwlwifi 11n_disable=n, so far without success.I regret that we didn't verify your exact device 20 posts back. I apologize.

I suggest you try:```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```Reboot and let us hear your report.

---

### Post by pwabrahams on 2015-12-23
I tried your suggestion and I still get occasional dropouts.  Here is my ath9.conf file:
```
options ath9k nohwcrypt=1

```
and here is iwlwifi.conf:```
options iwlwifi 11n_disable=1
```

I should say, though, that before I ignored ipv6 I was getting errors that clearly were related to ipv6.  I don't get those errors any more.  I would guess that the log I excerpted from 12/21  at 22:55 provides the best clue we have.

---

### Post by pwabrahams on 2015-12-24
I've captured the section of syslog that seems to show just how the connection is being lost, but I don't know how to interpret it.   It is here: [http://pastebin.com/UAgpAx2j](http://pastebin.com/UAgpAx2j)

---

### Post by Hadaka on 2015-12-24
Hi, please do..
```
sudo rm -rf /etc/modprobe.d/iwlwifi.conf
```
then post the output of..
```
sudo iw reg get
lsmod | egrep "ath9|iwl"
nmcli nm
```
thanks.

---

### Post by pwabrahams on 2015-12-25
```
pwa@Aspire-E1-731:~$ sudo su
root@Aspire-E1-731:/home/pwa# iw reg get
country US:
        (2402 - 2472 @ 40), (3, 27)
        (5170 - 5250 @ 40), (3, 17)
        (5250 - 5330 @ 40), (3, 20), DFS
        (5490 - 5600 @ 40), (3, 20), DFS
        (5650 - 5710 @ 40), (3, 20), DFS
        (5735 - 5835 @ 40), (3, 30)
        (57240 - 63720 @ 2160), (N/A, 40)
root@Aspire-E1-731:/home/pwa# lsmod | egrep "ath9|iwl"
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  1 ath9k
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
root@Aspire-E1-731:/home/pwa# nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  

```

---

