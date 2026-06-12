---
title: "Hardy, Wicd, How to automatically connect to Internet?"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by LillaEpsilon on 2008-05-01
I use the Wicd network manager in Hardy Heron, and it works well -- except that I have to manually connect to the internet (both wired and wireless) when I

a) turn the computer on, or
b) wake the computer up from "sleeping" after it has been left for a while.

I have checked the "automatically connect" on my home/work networks in the particular networks' settings in Wicd, but that doesn't seem to make any difference.

Ideas, anyone?
Thanks!

---

### Post by khaelo on 2008-07-06
First post alert...I have the exact same issue in Xubuntu 8.04.  Any solutions in the past two months?  Search didn't turn up anything on this particular problem.

Details:  WEP encrypted home network.  Wicd sees the network and connects when told to do so, the login info stays in its memory, and the autoconnect box is checked under "Advanced Settings."  It just refuses to connect automatically on boot.  I have to click "connect..." on the tray icon, select my network from the list, and tell it "Connect" again.  It's better than the "keyring password" nm-applet demanded, but still rather annoying.  :confused:

Edit:  Also, I completely(?) removed the default Network Manager -- two packages, uninstalled via Synaptic.  I see other posts talking about Wicd and Network Manager interacting/interfering with one another, but my Wicd download wouldn't install until I got rid of Network Manager.  Don't know if that makes a difference, but I thought I'd throw it out there.

---

### Post by imdano on 2008-07-06
Try the newest version (1.5.0rc5) from [www.wicd.net/latest](www.wicd.net/latest) and see if works then.  The directory structure changed quite a bit from 1.4.2 (no more /opt/wicd/), so make sure you read the man entry after you install.

---

### Post by linuxonbute on 2008-07-06
> **imdano said:**
> Try the newest version (1.5.0rc5) from [www.wicd.net/latest](www.wicd.net/latest) and see if works then.  The directory structure changed quite a bit from 1.4.2 (no more /opt/wicd/), so make sure you read the man entry after you install.

I added the following repository to 8.04 and used synaptic to install wicd:
[http://apt.wicd.net](http://apt.wicd.net) gutsy extras

This removed network manager and installed wicd ( into /opt/wicd etc )

after configuring it it worked fine. It should also keep being updated as new versions come out.

---

### Post by imdano on 2008-07-06
Right now the newest version in the apt repository is 1.4.2.  1.5.0 will be added once it reaches its final release (probably not for another week or two, our packager is on vacation right now).  If 1.4.2 is working fine there's no harm in waiting, but 1.5.0 is a pretty big improvement so its worth trying now if you're having problems.

---

### Post by khaelo on 2008-07-08
Aquiring new repositories is beyond my Linux-skills right now, so I picked up a 1.5.0 "testing" from SourceForge.  Wicd's buttons now look nicer.  :)  However, the original problem still stands.  Did I need to uninstall the older version?  I just installed the new one from the .deb file and assumed it would update/replace the previous installation, but maybe that isn't the case?  Also, where is the man entry?

The refusal to autoconnect isn't limited to encrypted networks, either, by the way.  I tested it on a teashop's WiFi.  Also, the problem is occurring in an identical manner on both my Dell Inspiron 600m laptop (Xubuntu 8.04 on a harddrive partion) and my EEE PC 900 (eeeXubuntu 7.10 on SDHC card).  So I don't think hardware is behind this, thank goodness.

---

### Post by imdano on 2008-07-09
Is the autoconnect problem something you only see on reboot?  Or does it also not connect if you manually disconnect, then restart the wicd daemon/tray?  The man entry should be found just by running "man wicd", but its possible that wasn't added until after the most recent rc5 build (I can't remember...).

Most likely this problem is caused by your wireless interface not coming up until after wicd's autoconnection logic runs.  I'm not really sure if the delay is related to the card/driver itself or something related to network configuration.  I'll think about a solution, though it might be tricky to test because I can't reproduce it.

---

### Post by LillaEpsilon on 2008-07-09
Hi guys, I didn't see your replies until now, so please excuse the late reply.

I found a partial solution to the problem, through this forum: [http://wicd.net/punbb/viewtopic.php?id=6](http://wicd.net/punbb/viewtopic.php?id=6)

It turns out that checking "automatically connect" only works for your "default profile", which you have to set manually.

That is, now I can automatically connect to the wired network because I chose it to be my default profile. But I still have to manually connect to wireless networks. You can probably also set your home wireless as default (I didn't try that), my problem is that I use many different networks daily, but I can only choose one of them as default (or, in my case, all the wired ones).

So I would like to be able to have several "accepted" networks, but I haven't figured out how. If anyone finds out, please tell!

---

### Post by imdano on 2008-07-09
The "default profile" thing only applies to wired networks.  You can set as many wireless networks as you want to automatically connect.  It works like this:
- The autoconnect method starts.

- It checks for the presence of an ethernet cable.

- If it finds one, it will automatically connect according to the "Wired Autoconnect" option selected in wicd's preferences window.  There are three options:
    1) Use default profile
    2) Prompt for profile
    3) Use previously selected profile

- If "Use default profile" is selected, wicd will search through all the wired profiles you have to see if you've checked the "Use as default profile" checkbox for any of them.  If it finds one, it connects using that profile.  **This is what is currently happening in your case.**

- If there is no ethernet cable plugged in, or if "Use default profile" is selected, but none of your wired profiles have the default profile checkbox selected, wicd will try to connect to a wireless network.  **This is what was happening before you selected a default wired profile.**

- If wicd is set not to or cannot connect to a wired network, it will go through all the networks found in your wireless scan, and check to see if "Automatically connect to this network" is selected.  As soon as it finds one, it tries to connect to that network.  Now, for some reason wicd wasn't completing this step properly for you.  I mentioned some possible reasons why in my last post.

---

### Post by LillaEpsilon on 2008-07-15
Thanks for the explanations imdano. I may have ignored intelligent things you said before because your lanugage is a bit out of my "first cup of ubuntu"-vocabulary. 

But my wicd does not ever automatically connect to any wireless network (and it automatically connects to all the wired networks I use, I don't know if that is interesting. Why does default profile only apply to wired networks?)

But these are minor problems, which I hope will be fixed in the next version.

---

### Post by imdano on 2008-07-16
> **LillaEpsilon said:**
> But my wicd does not ever automatically connect to any wireless networkI mentioned some possible reasons for this in a previous post.  For most people, wicd automatically connects to wireless networks without any trouble.  But there is a small group it doesn't work for, typically only when their computer boots initially.  I think this is either a driver issue or some quirk in their network configuration (outside of wicd).  I'm working on a way to make it work for everybody, but as I said before, its hard to tell if anything I try works because wicd automatically connects just fine for me.
> **LillaEpsilon said:**
> Why does default profile only apply to wired networks?)Well, with wireless networks, its easy to just have a "Automatically connect to this network" option because each wireless network is unique.  However, there isn't a good way to tell if your ethernet cable is plugged into your router, your neighbors router, or a plug at work.  To make it possible for a user to have unique settings for any number of different locations they could be using an ethernet connection, we created the wired profile system.

This worked really well for making settings customizable for different locations but made autoconnection a little more complicated, because as I said before, there's no way to know where you're plugged in.  So we have a few different ways you can set wicd to autoconnect.  Most people just use the "Connect to my default profile" option (this is what you're using) that just uses some fairly standard settings to connect.  The other options provide more flexibility for people don't want to always connect using the same profile.

---

### Post by eternaluxe on 2008-08-11
I'm having the same issue.  I think you are right, imdano.  In what order should this occur, and what can I do to check it?
I'm using a netgear wg111v2(usb) with  wpasupplicant/wext driver and wicd.

or

is there a script I can run automatically on login that will tickle wicd?

Thanks
eternaluxe

---

### Post by morphious on 2008-08-21
Hi people.

I've installed Wicd on my notebook since I had Ubuntu 8.04, because I couldn't run my wireless connection manually with wpa_supplicant. It worked perfectly.

About two months ago, I noticed that my wicd doesn't connect at startup to WLAN anymore.

This is what helped me to solve this problem:

1. Delete all wired connection profiles,
2. Check out /opt/wicd/data/wired-settings.conf file, it should look now something like this:

```
sudo gedit /opt/wicd/data/wired-settings.conf
```

```
[DEFAULT]
afterscript = None
broadcast = None
dns3 = None
ip = None
dns1 = None
use_static_ip = False
use_static_dns = False
default = True
netmask = None
dns2 = None
beforescript = None
disconnectscript = None
gateway = None
use_global_dns = False

```

3. If this doesn't help you, check out logs: /opt/wicd/data/wicd.log, paste it here, we'll see what we can do with it.

My wicd version: 1.4.2 (exactly the same as in the repositories).
There is also great chance that this bug isn't anymore in newer versions.

I hope it'll help somebody.

Greetings,
morhpious.

---

### Post by flanagan on 2008-11-11
None of the previous suggestions worked for me, but I was able to solve my particular problem through a bit of trial and error. My version of Wicd is 1.5.0 under Ubuntu Hardy 8.04.

Here is the situation and my convoluted thought process.

I have a Dell Inspiron 9300 laptop and Wicd would not automatically connect under any circumstances: not on reboot, not on cold start, not on return from hibernation, not on return from suspend. It worked flawlessly otherwise and always connected obediently if I brought up the GUI to manually connect. There were no apparent errors in /var/log/wicd/wicd.log.

After various experimentations, I re-read the man page where it described the logic used by Wicd to determine how to connect to networks on startup:

> If  the  user chooses, wicd will try to automatically reconnect when it
detects that a connection is lost.  If the last known connection  state
is wired, wicd will first try to reconnect to the wired network, and if
it is not available, wicd will  try  any  available  wireless  networks
which  have automatic connection enabled.  If the last known connection
state is wireless, wicd will first try to reconnect to  the  previously
connected network (even if that network does not have automatic connec&#8208;
tion enabled), and should that fail, it will try both a  wired  connec&#8208;
tion  and  any available wireless networks which have automatic connec&#8208;
tion enabled.

I noticed that it does not say what Wicd does if the last known connection state is disconnected. I concluded that Wicd, on startup, thinks that both things are True: (a) a connection has been "lost"; and (b) the last known state was "disconnected".

My solution was simply to check the box for *Automatically reconnect on connection loss* under Wicd's preferences in the GUI.

For those who prefer to edit the config files manaully, change the setting to:

```
auto_reconnect = True
```
when you:
```
sudo gedit /etc/wicd/manager-settings.conf
```

---

### Post by dgavenda on 2008-11-12
flanagan,

Yes that works.  But, I assume there's still an issue.  Regardless, it works and I am happy again.

Thx for the info.

---

### Post by lylex on 2008-11-21
Using the check box for Automatically reconnect on connection loss under Wicd's preferences in the GUI, seems to work for me.

I'm running wicd 1.5.3 under Ubuntu 8.04 on a Dell X1.  Recently, the autoconnect to my home wifi seemed to stop working.  I could connect manually.  I could restart wicd and it would autoconnect.  But not at boot time, until now.

Thanks...Lyle

---

### Post by perstromgren on 2009-02-21
I did not realize that every network I can see has it's own "Auto reconnect" checkbox in the wicd mgr GUI! It is visible by clicking the leftpointing triangle. It was not obvious to me that this was clickable. I can't fins any documentation that mention this either, where is it?

I use Wicd Manager 1.5.8 under Ibex.

Per.

**Edit**: I confirm that the above solved my problem, my system now always autoconnects.

---

