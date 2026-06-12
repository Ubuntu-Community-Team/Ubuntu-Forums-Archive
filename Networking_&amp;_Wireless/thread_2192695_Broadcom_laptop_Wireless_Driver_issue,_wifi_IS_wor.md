---
title: "Broadcom laptop Wireless Driver issue, wifi IS working, but odd Boot Errors."
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by shahanakhter on 2013-12-09
Since I've been told broadcom wireless and ubuntu drivers can be a nightmare I shouldn't be complaining since [SIZE=3]**my wifi is actually working almost all of the time**[/SIZE], and I wouldn't complain except that I think this seemingly benign start up issue has seeped into other parts of my system.

So here's what happened:

Using a laptop dell inspiron n5010, came with windows 7, came with this wireless card, lspci:
```
[FONT=Ubuntu Mono]12:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)[/FONT]
```

After some dual booting and eventual dbaning and wiping windows, I'm now using a clean installation of Ubuntu 12.04 LTS

When I started using it everything was fine and fast and the wireless worked, and never kept prompting me for passwords or anything BUT I never has the normal ubuntu boot screen, with the orange dots and the logo. 
Now most people have told me this is normal and not a big deal and not to worry about it.
but here is how my boot sequence goes:

1-BIOS loads normal
2-blank purple screen
3-black
4-laptop screen off
5-black screen print out some kind of 'error' message?
        ```
[FONT=Ubuntu Mono] [    9.625943] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1[/FONT]
```
6-ubuntu orange dots screen for 1 second
7-normal log in, wireless is working fine


NOW I thought to fix this I'd have to install the broadcom wireless driver using jocke-gtk
BUT every time I used jockey it just said 'downloading and installing..." for HOURS and I eventually had to hard reboot...
However, when I hard rebooted it DID say the broadcom wireless proprietary driver WAS installed, but I never thought it installed proper since jockey always "froze"

so after this I get the same boot sequence except at step 5 i get a black screen that prints out this(I know this is just an info message):

[COLOR=#ff0000][I]This is after installing proprietary wireless driver via glitchy jockey-gtk
[/I][/COLOR]        ```
[    7.934709] INFO @wl_cfg80211_attach : Registered CFG80211 phy
```

[B]and I should mention at both of these that it's like a 70/30 chance my laptop crashes and I have to hard reboot <- this is the main reason of why I'm posting here and want to fix this, I want a normal boot sequence.

[/B]So where I am now is using this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
to get things right, but it's just not working out, I need help.

[COLOR=#0000ff]**here's my dmesg**[/COLOR]:  [http://paste.ubuntu.com/6545864/](http://paste.ubuntu.com/6545864/)  Line 702

**[COLOR=#0000ff]lspci -vvnn | grep 14e4[/COLOR]**```
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
```

And there just seems to be so much crap out there about this specific driver not being good the '4313' and '4727' keeps coming up.

[I]side: I know this may not be related and I'll probably have to make a new thread for it, AND i'm hoping this solves this, but since the first day of installation my ubuntu has become very slow in odd ways.  hitting the launcher button now has a like 3 second delay and first use of alt-tab is also very slow, but that's about it.  is this symptomatic of something.. obvious?  or no?  my laptop isn't that old, and off a live USB it runs fine in terms of the alt-tab and launcher...
[/I]

&#8203;thank you./

---

### Post by chili555 on 2013-12-09
Wow! That's quite a collection of problems you have there! Let's attack them one at a time and see if fixing the biggest problem fixes all the remaining problems. 

First, ignore the Additional Drivers tool. It sometimes offers, at least in the case of your 14e4:4727, the *wrong* driver. Second, let's remove the wrong driver:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and let us know if things are improved.

---

### Post by shahanakhter on 2013-12-09
Yeah i know, thank you for helping.

Okay so uninstalling that showed: 

```
(Reading database ... 283961 files and directories currently installed.)Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.12.1-031201-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169

```

And now it's that first abnormal boot screen I described that is blank purple, black, off, black with:

         ```
[COLOR=#000000][FONT=Ubuntu Mono][    9.625943] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1[/FONT][/COLOR]
```
then logo + orange dots for a second.  

So this disabled/uninstalled the proprietary right?  So this has worked fine in the past, not getting prompted for password all the time, wifi working but it has crashed like this before at tart up...  though i know that could be a different issue, what exactly does that message mean?  If my wifi is working fine, can I disable that message and have a normal boot?

---

### Post by chili555 on 2013-12-09
> So this disabled/uninstalled the proprietary right? Correct. I believe the native driver brcmsmac is more appropriate for your enigmatic device. We'll see.

Let's continue working the flaws until we are out of warnings:> W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-3.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168g-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8106e-1.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8411-2.fw for module r8169Now that you have, apparently, solid wifi, let's check the firmware:```
ls -al /lib/firmware/rtl_nic/
```If it reports that there is no such file or directory, let's get it:```
sudo apt-get install linux-firmware
```This part:> upport for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1...is caused by the module b43 that probably shouldn't even be loading! Let's check:```
lsmod | grep -e wl -e b43 -e brcmsmac
```

Note to chili:

Possible reference: [http://unix.stackexchange.com/questions/93738/b43-wireless-driver-error](http://unix.stackexchange.com/questions/93738/b43-wireless-driver-error)

---

### Post by shahanakhter on 2013-12-09
Okay, and yeah oddly enough the wifi has been functioning 98% fine lol.  It's just the boot errors and occasional freezes that are irking me...

so [COLOR=#000000][FONT=Ubuntu Mono]ls -al /lib/firmware/rtl_nic/ =

[/FONT][/COLOR]```
total 68drwxr-xr-x  2 root root  4096 Dec  2 18:45 .
drwxr-xr-x 69 root root 20480 Dec  3 19:07 ..
-rw-r--r--  1 root root  2076 Nov  8  2012 rtl8105e-1.fw
-rw-r--r--  1 root root  1492 Nov  8  2012 rtl8168d-1.fw
-rw-r--r--  1 root root  1324 Nov  8  2012 rtl8168d-2.fw
-rw-r--r--  1 root root  5500 Nov  8  2012 rtl8168e-1.fw
-rw-r--r--  1 root root  3920 Nov  8  2012 rtl8168e-2.fw
-rw-r--r--  1 root root  3872 Nov  8  2012 rtl8168e-3.fw
-rw-r--r--  1 root root  3136 Jul 12 10:00 rtl8168f-1.fw
-rw-r--r--  1 root root  1232 Nov  8  2012 rtl8168f-2.fw
-rw-r--r--  1 root root  1824 Nov  8  2012 rtl8402-1.fw
-rw-r--r--  1 root root  1840 Jul 12 10:00 rtl8411-1.fw



```[COLOR=#000000][FONT=Ubuntu Mono]

so i have linux-firmware installed. 

and [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep -e wl -e b43 -e brcmsmac[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] =[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]```
brcmsmac              564551  0 brcmutil               15618  1 brcmsmac
cordic                 12574  1 brcmsmac
b43                   397438  0 
mac80211              635046  2 brcmsmac,b43
cfg80211              505004  3 brcmsmac,b43,mac80211
ssb                    62919  1 b43
bcma                   52185  3 brcmsmac,b43



```
[COLOR=#000000][FONT=Ubuntu Mono]
and yes, that sounds great!  If we could just eliminate it from the boot sequence, maybe that'd fix things.
[/FONT][/COLOR]

---

### Post by chili555 on 2013-12-09
Yes, you have linux-firmware installed but not the files it's complaining about. Please try:```
sudo apt-get install --reinstall linux-firmware
```Perhaps a fresh copy will help us. Now try:```
gksudo gedit /etc/modules
```Is b43 listed? If so, remove it, proofread, save and close gedit. Now do:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
exit
```Now reboot. Do you get any errors? Let's confirm that it *isn't* loaded:```
lsmod | grep -e wl -e b43 -e brcmsmac
```

---

### Post by shahanakhter on 2013-12-09
ok re-installed firmware,

b43 was not listed 
[ATTACH=CONFIG]248468[/ATTACH]
and this was added
[ATTACH=CONFIG]248467[/ATTACH]




that lsmod command showed:    

```
brcmsmac              564551  0 mac80211              635046  1 brcmsmac
brcmutil               15618  1 brcmsmac
cfg80211              505004  2 brcmsmac,mac80211
cordic                 12574  1 brcmsmac
bcma                   52185  2 brcmsmac



```


AND here is what happened upon first reboot after that.  Same exact boot sequence **with out any kind of error message.  **It was just a series of blank screens, a screen turn off, then the ubuntu logo screen for a second.  Oh and wifi worked fine upon login.

If the normal good old days ubuntu log in screen is too much to ask for, or just won't be possible that's fine, I can settle for this, but it essentially boots at the same speed. I thought getting rid of the load time for the error message would save time, so was it just masked?  Or some other very complex issue, I'll need time and reading to comprehend lol.

In any case, this is awesome, thanks friend!  Did the above specs look solid?

rebooting again now.

---

### Post by chili555 on 2013-12-09
The blacklist and lsmod look correct. Next, I'd look for clues here right after boot:```
less /var/log/syslog
```'less' will allow you to scroll back and forth with the arrow keys. Get out of less with q. syslog is timestamped, so note the time as the screen is going black and look for problems at and before that time. If syslog is sparse or empty, try:```
less /var/log/syslog.1
```

It sounds like a video issue; check for errors (EE) here:```
cat /var/log/Xorg.0.log | grep EE
```I am not very experienced in video issues, so we may have to refer the issue, once we find it, to specialists.

---

### Post by shahanakhter on 2013-12-10
Oh man, bad news, so after that last shutdown, I booted up and it froze like 3 times in a row had to hard reboot 3 times...  So I left it off for a while, hence why i didn't reply sooner.

And  just turned it on a second ago, it went:  

BIOS
blank purple
blank black blinking cursor
blank black... ... ... frozen.  hard reboot.

grub(which doesn't usually show up i guess only after crashes), pick regular ubuntu, worked fine.

I don't know if this'll happen 100% of the time, or if it's an issue from something else, but since the blacklisting of b43 this is happening, 
here's the dmesg from my most recent boot: [http://paste.ubuntu.com/6549625/](http://paste.ubuntu.com/6549625/)

and my syslog.. :  [http://paste.ubuntu.com/6549636/](http://paste.ubuntu.com/6549636/)

that EE command showed this:

                   ```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.444] Initializing built-in extension MIT-SCREEN-SAVER



```


haven't unblacklisted b43 and rebooted yet, will wait to see what you say.  Again it could be something else, but last 3 boots... odd.
still
also, thanks for your help, really appreciated it, with out you i'd be square zero :)

---

### Post by chili555 on 2013-12-10
> haven't unblacklisted b43 and rebooted yet, will wait to see what you say.We are many time zones apart. You posted this as I was sleeping. 

I didn't see anything alarming in dmesg. There are one or two curious things that don't seem to keep the machine from booting correctly. Your syslog is a different matter. First, we see the wireless interface is eth1; that's generally the interface associated with the Broadcom STA driver wl. Aren't we using brcmsmac?? In that case, the interface should be, ideally, wlan0 and not eth1. Is the syslog the most recent? Can you please pull a later file for us and paste it?```
cat /var/log/syslog | grep -i -e warn -e error | tail -n100
```Again, if it is sparse or empty, get syslog.1.

This looks a little strange:> rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]It is, unfortunately, outside my narrow area of semi-expertise. You might Google it or ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)  I have no idea if it is serious or trivial but it sounds scary to me. Please check here: [http://askubuntu.com/questions/249490/rsyslogd-stopped-writing-to-var-log-syslog-two-days-ago](http://askubuntu.com/questions/249490/rsyslogd-stopped-writing-to-var-log-syslog-two-days-ago)  If, in fact, syslogd stopped writing some time ago, that explains the eth1 above and may be why we can't find the error yet.

---

### Post by Rob Sayer on 2013-12-23
I had the same wireless adapter in my netbook and I had a lot of problems with it when I ran kubuntu 12.04, but not like this ... though I don't think it's just the bcm adapter that's giving you problems either.

As mentioned, bcmwl-kernel-source didn't work, though it did in 13.04.  I'd recommend never using "additional drivers" to install that type of thing in ubuntu but do it in synaptic or terminal instead.  I don't think additional drivers does a very good job of resolving dependencies.

Installing linux-backports-modules-cw-3.6-precise-generic worked for me in 12.04 though.  I just did a search in my posts here and that's what I came up with.  I may have more notes on the subject (doubt it though) but they'd be on another HD at home,

While I've been getting decent performance since 12.04, I'm starting to believe that the best solution with some of these wireless adapters is to just find one of those usb wireless dongles that *does* have decent linux support.

---

