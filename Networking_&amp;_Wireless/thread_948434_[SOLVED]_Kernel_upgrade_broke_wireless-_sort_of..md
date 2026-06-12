---
title: "[SOLVED] Kernel upgrade broke wireless- sort of."
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2008-10-15
Hi All

Just accepted the update from the manager, which included an upgrade from 2.6.24-19 to 2.6.24-21.  Since doing that, something strange has been going on with wifi and Wicd.

I can start Wicd normally, and it detects 2-3 wifi networks, as usual, except that *it doesn't detect my own network*, which is set to connect automatically, and is normally the strongest signal (~80% as opposed to ~50% on other networks).

The router seems to be working fine- it's connected now (I'm using 2.6.24-19 at the sec), and also seems to be working with my mobile phone.

Other info- Wicd 1.5.3, Ubuntu Hardy on c2d laptop.

This doesn't make any sense to me- please help!
Charlie

---

### Post by HaguMe on 2008-10-15
I have a similar problem here, but instead of detecting any network, it doesn't detect anything!

I hate kernel switching! :lol

---

### Post by Hadesdarklord on 2008-10-15
Every time I load a new kernel, I need to re-compile and reload my Atheros Drivers.

Usually not a problem.

Now, of course, the 8.04 -21 kernel is generating a "kernel panic" involving interrupts and the wlan driver.

<sigh>

---

### Post by HaguMe on 2008-10-15
kernel panic? How can you resolve that?

Anyways, It wouldn't be good to always re-compile Atheros drivers after kernel updates... but I guess I should live with that.

Greetings.

---

### Post by TDave on 2008-10-15
I'm in a similar boat, I'm afraid (although I'm reassured others have had it..!)

Basically, all through today I've been connected fine to the WPA2 connection at work. Ran the updates (foolishly without consulting the forums and the like first - one day I'll learn!) and, upon restarting, I could no longer connect to anything through NetworkManager to the previous network (it used to auto-connect on startup), although it makes like it's trying to connect continuously but to no avail.

The usual 'Click Icon to Show Me What's Available' route fails to bring up anything at all. Unfortunately, booting back from the .19 version also seems to fail at the same tasks.

It's confusing at best and I can't think of any other diagnostic stuff I can run that could be useful - suggestions welcome.

So far, iwconfig --version doesn't bring up anything out of the ordinary, and iwconfig alone seems to detect the interface just fine.

Is this possibly a NetworkManager problem? I'll hopefully be able to add more detail to this later on after getting a bit more chance to prod it.

If anyone has any suggestions in the meantime it'd be greatly appreciated. :-)

*Ninja Edit*: Wireless device is using the iwl4965 driver and is a PRO/Wireless 4965 device.

---

### Post by politenessman on 2008-10-15
I'm having the same issue. I have an Asus eepc 900, which has been rock solid until I rebooted, after the latest update this morning. Now my wireless networking doesn't work. As a recent convert from windows to ubuntu, I have little to no experience messing about with linux so I have no clue how to fix this.

Any help would be welcome

---

### Post by AznPat on 2008-10-15
i have the same problem.when i updated my kernels my wireless does not even appear..it totally elements my wireless..i m using a atheros 802.11 card..if anybody can help me i would really appreciate it..thanks

---

### Post by TDave on 2008-10-15
**General Update**

Well, this appears to be a Network Manager problem, although quite how, when it wasn't one of the updates that seemed to break this, confuses the bejeezus out of me.

Using this link - [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) - to remind myself how to do it from the command line, I was successfully able to connect to the unsecured network I knew existed in the local area, all the while NetworkManager spins its symbols uselessly in the corner.

The command line route worked fine and I can access all the sites I'd expect to through it (including this one).

I haven't yet tried to reconnect to the WPA network, but will do shortly.

As a temporary workaround, hopefully the above link will help.

---

### Post by politenessman on 2008-10-15
Interesting.

lshw -C network gives me full details on both my ethernet adapter and my wireless adapter. However, the wireless adapter has no logical name.
I wonder if that is the problem? Any thoughts?

---

### Post by TDave on 2008-10-15
> **politenessman said:**
> 
lshw -C network gives me full details on both my ethernet adapter and my wireless adapter. However, the wireless adapter has no logical name.
I wonder if that is the problem? Any thoughts?

What does ifconfig bring up for the interfaces? That should certainly bring up the name you want to use to address it (potentially ath0, wlan0, eth1 - could be others I'm unaware of).

---

### Post by politenessman on 2008-10-15
> **TDave said:**
> What does ifconfig bring up for the interfaces? That should certainly bring up the name you want to use to address it (potentially ath0, wlan0, eth1 - could be others I'm unaware of).

lo and eth0 only.
No wireless adapter at all.

Edit to add - it looks like its not configured. I'll see if I can get it configured

---

### Post by TDave on 2008-10-15
Just thinking a bit more about this...

One of the updates I definitely installed today was dbus related (granted, I can't remember the names of the dbus packages and their version numbers). Thinking back to the problem being focused on NetworkManager, NetworkManager communicates using dbus and hal (if I remember rightly...) - does anyone with any clue have any idea if that could be related or, more to the point, what I could run that could help diagnose this further?

Guess it's time to see if this is a reported bug by people who know more than me.

---

### Post by LunaEqualsLuna on 2008-10-15
Same problem here i just updated and now my wireless is broken >_>.

How do I undo this update. I really gotta start paying attention to these updates now and wait a few weeks before I update.  I certainly will in the future once I get this wireless sorted out. Sort of a if it ain't broke don't fix it mentality. Because everything was running perfect and now this annoyance has occurred.

---

### Post by politenessman on 2008-10-15
ok, now I am getting really mad.
No wireless = no internet connection (I am writing this from another machine)
Every damn thing I've found so far insists on me downloading something and its all CLI - I have no clue about most of that stuff.
Can anyone tell me how to get this working again, or roll back the recent updates?

I am so screwed without a net connection on that machine.

---

### Post by soro2005 on 2008-10-15
It may be dbus related, but definitely has to do with the kernel upgrade as well. I can use the old kernel and connect to the wireless router without a problem.

To use an older kernel version: Hit the <esc> key as soon as the Grub loader comes up (immediately after switching on the machine), then select a different kernel version from the list.

---

### Post by TDave on 2008-10-15
> **soro2005 said:**
> To use an older kernel version: Hit the <esc> key as soon as the Grub loader comes up (immediately after switching on the machine), then select a different kernel version from the list.

Yep, for some reason that option still isn't doing it for me, although quite why, I'm not sure. Even in the 'safe' mode on the older kernel it doesn't seem to bring any joy, although maybe I'll try that again just to be certain.

politenessman: Best I can suggest at this point is confirming or denying that the tip from soro2005 regarding the kernel selection at bootup works for you. As for 'downgrading' to what you had previously, my honest answer is that I don't know.

Anyone know if this has been raised as a bug already? I can't find anything obvious in my searches so far, but then I haven't used Launchpad much.

---

### Post by politenessman on 2008-10-15
> **soro2005 said:**
> To use an older kernel version: Hit the <esc> key as soon as the Grub loader comes up (immediately after switching on the machine), then select a different kernel version from the list.

I did not know that. Thank you! Worked like a charm and I am back to having internet connection again!

---

### Post by soro2005 on 2008-10-15
Nice to be able to help with the easy advise. :-) I'm sure somebody is looking into it. These things are usually fixed within a couple of hours.

---

### Post by TDave on 2008-10-15
Well...

It ain't necessarily clean, or tidy, but I found a workaround for this in the meantime that at least seems to get my unencrypted connections up and running, and that was to use the repository of packages for NetworkManager0.7 as per this thread:

[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

The usual caveats should obviously be taken with that, as mentioned in that thread.

It should also be noted that I cannot currently connect to the WPA network using the 'new and improved' NetworkManager which, it appears, is due to the choice of Encryption (TKIP etc) being lost from the NM options. I am going to look into workarounds for this shortly. I suffered this under OpenSuSE 11.0 as well (which ships NM7.0 as standard)

It connects to the open and WEP areas without issue though.

I wouldn't necessarily recommend this from a stability point of view because of the problems I've encountered with WPA, but it might be worth a go.

---

### Post by LunaEqualsLuna on 2008-10-15
reverting to the old kernel did the trick. Changing the default kernal in /boot/grub/menu.lst from 0 to 2 made the changes permanent. until i figure out what went wrong I shall be sticking with the old kernel! 
:)

---

### Post by Shimatta1 on 2008-10-15
Had the same problem (Inspiron 700m, Intel PRO 2100 b/g (IIRC)) after upgrading.  Got my hands on a wired connection, re-ran Update Manager and found a new package waiting for me: linux-firmware.  Installed that, restarted, and wireless was working again.

Hope this helps.

---

### Post by samwisgg on 2008-10-15
> **Shimatta1 said:**
> Had the same problem (Inspiron 700m, Intel PRO 2100 b/g (IIRC)) after upgrading.  Got my hands on a wired connection, re-ran Update Manager and found a new package waiting for me: linux-firmware.  Installed that, restarted, and wireless was working again.

Hope this helps.

I just re-ran my update-manager and found nothing.
My wireless network was broken also. Choosing the old kernel from the grub menu is for the moment the only way to be back in business. By the way : I do NOT use network manager (I de-installed it) so the problem is not related to that. The only thing I found out with the new kernel was that the wireless network device name (under the old kernel 'wlan0') simply didn't exist.

---

### Post by TDave on 2008-10-16
Hmm, interesting stuff.

Shimmatta1: I, too, was unable to find the package 'linux-firmware' either in updates or in doing a general update - what extra repositories do you have set up?

samwisgg: Yeh, it's strange, rolling back to the previous kernel did precisely jack all for me, and starting up with the latest kernel kept my device there as it was before (wlan0) and enabled me to connect to it via iwconfig and work fine with it that way. Just as updating NetworkManager to 0.7 allowed me to connect to WEP and Open networks, although the config options for my WPA connection seemed to be limited, so that didn't connect.

At the minute, I'm back where I started, with NM 0.66 not working for some strange reason, and connecting via iwconfig and manually editing the wpa_supplicant.conf.

Realistically, I'll probably just stick with this if I get comfortable with it, but it still seems a bit confusing that so many people are struggling with slightly different results.

---

### Post by TDave on 2008-10-16
Well... this is odd.

Decided to sack off the old Kernel idea and go back to booting by default into -21 again (since neither method was working) and.. for some reason... it all just works.

/me shrugs.

I haven't added or removed anything different from yesterday (tell a lie: I installed the cups updates) and I'm still on NWM 0.66 but it seemed to somehow correct itself.

---

### Post by stevemarkus on 2008-10-16
Hi All.

I have had a similar problem. I´m using the Atheros AR242x 802.11abg Wireless Adapter and on rebooting after the kernel update, could not connect wirelessly. When I clicked on the network interface icon, I got an error &#346;IOGIFFLAGS. I have recompiled the madwifi driver and now wicd can see the networks, which it couldn before, and can connect (hooray). However, the connection is very intermittent and keeps disconnecting - it is unusable really.

I have tried using the .19 version of the kernel but this seems to have similar problems now. Not sure how to fix this - has anyone got any ideas ?

Best wishes,
Steve.

---

### Post by shane2peru on 2008-10-16
> **stevemarkus said:**
> Hi All.

I have had a similar problem. I´m using the Atheros AR242x 802.11abg Wireless Adapter and on rebooting after the kernel update, could not connect wirelessly. When I clicked on the network interface icon, I got an error &#346;IOGIFFLAGS. I have recompiled the madwifi driver and now wicd can see the networks, which it couldn before, and can connect (hooray). However, the connection is very intermittent and keeps disconnecting - it is unusable really.

I have tried using the .19 version of the kernel but this seems to have similar problems now. Not sure how to fix this - has anyone got any ideas ?

Best wishes,
Steve.

Same problem and same chipset here!  Keep posting if something is found. I will keep hunting and post if I find a solution too.

Shane

---

### Post by Helos on 2008-10-16
Same chipset also, But Instead of recompiling madwifi I installed the new network manager, when that didn't work I reverted back to .19 and now its working fine...

---

### Post by shane2peru on 2008-10-16
Ok, here is the fix at least for Ahteros AR242x chipset.  I took this from a few different posts and places. 

Step 1 - download madwifi.
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz

```

2.  Unpack it:
```

tar -zxvf madwifi-hal*.tar.gz

```
3.  Unload any previous drivers
```

cd madwifi-hal*/scripts
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh -r `uname -r`
cd ..

```
4.  Make new drivers
```

sudo make && sudo make install

```
5.  Get rid of the ubuntu drivers that aren't working
**System -> Administration -> Hardware Drivers ** Uncheck both hal and Atheros support

6.  Reboot (to get rid of Ubuntu drivers)

7. Load madwifi drivers:
```

sudo modprobe ath_pci

```

Should work, if it does and you don't want to load the drivers every time to use it you can load it on boot up with this:

```

sudo gedit /etc/modules
ath_pci

```
Just add that ath_pci to the end of the file and it will load on boot from now on.  Hope that helps! Unloading the previous drivers is a key part including the Ubuntu drivers, that is what was holding me back.

Shane

---

### Post by FokkerCharlie on 2008-10-16
OK- Solved now at my end.

Uninstalled the backports modules that I had installed.  I had this on to get the LED working on my Intel 3945 wifi card.

And for the record- it's an unsupported module, so not really Ubuntu/Canonical's fault, from my POV!

I imagine that this solves the snag for all 3945/4945 users, and with the above fix for Atheros users, I'm marking this thread solved.

Cheerio
Charlie

---

### Post by UberWookieks on 2008-10-17
Soro: thanks. My wireless stopped functioning after the update (I'm on a 2,1 Macbook) and choosing the older kernel at boot did the trick. I'm a Gentoo refugee and didn't know how that was done in Ubuntuland.

---

### Post by soro2005 on 2008-10-17
@Charlie: Great, thanks! I can confirm this for Intel 3945: Just removed all the packages called linux-backports-modules, and it's back on. There seems to be some onflict there.

---

