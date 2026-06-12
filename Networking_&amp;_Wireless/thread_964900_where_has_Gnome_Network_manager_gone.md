---
title: "where has Gnome Network manager gone"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by don on 2008-10-31
Hi All, I have just upgraded to 8.10 and Network Manager Applet has gone. Any ideas how to get it back or is there a replacement utility that adds all the 3G stuff advertised on the Ubuntu site?

BTW, I checked from Add/Remove programs and "Network Manager" is still installed.

Regards, Don.

---

### Post by Kobalt on 2008-10-31
Press Alt+F2 and enter this to launch back Network Manager : 
> nm-applet

---

### Post by don on 2008-10-31
Thanks Kobalt, the answer was elegant and simple as always.

Regards, Don.

---

### Post by Claudestephane on 2008-10-31
Hoping to find answer to my challenge, I discovered Alt-F2 simply put another instance of network manager on my menu panel, but clicking on it replicated the menu that comes from existing icon, namely "manual configuration" Clearly a setting tweak needed, as I am sending this very message over my wifi network, BUT the network icon doesn't display signal strength, as it once did. searching for "nm-applet 0.6.6" in synaptic package manager brought up a big zero. Being able to pick a public wifi network based on signal strength remains a valuable capacity. Any help welcome.

Claude

---

### Post by knix on 2008-10-31
try running "sudo iwlist scan" in the terminal to see if your wireless drivers are working.

---

### Post by Claudestephane on 2008-10-31
Thanks Knix,

Wireless drivers appear to test well, which doesn't surprise me as this entire interchange is occurring over wireless. left click on network manager icon > Manual config  and right click > enable networking which has been selected, and edit wireless networks. The latter brings up a blank list of wireless networks, inspite of the fact that I am clearly connected. Is there another place in Ubuntu Hardy Heron, where network manager settings are configurable?

---

### Post by pmsumner on 2008-10-31
What I had to do was:

1. Edit /etc/networks/interfaces (sudo nano /etc/network/interfaces)
2. Comment out all references to anything that was not ath0 auto, eth0 auto, wlan0 auto, eth0 auto or lo (some of these may not apply to you)
3. Restart the PC (I tried without, it all went pear-shaped quickly and am yet to figure out why it wouldn't connect - it may simply be a case of restarting the right process but don't know which)
4. Go back to nm-applet (alt-F2 or edit System/Preferences/Sessions before rebooting to make t load automagically) and add wireless network.  All is good.

Your mileage may and probably will vary considerably

---

### Post by river2884 on 2008-10-31
Network interface and network is horrible, horrible in 8.10. go back to what was good.

---

### Post by Claudestephane on 2008-10-31
The wifi connection is working well. Its just the applet that resides on the bottom panel that fails to show all wireless networks, as it did ~a week ago. The problem will only be annoying when I'm out in the public space, in search of the best available network.

---

### Post by jonofan on 2008-11-01
I previously had wicd installed before upgrading and network manager disabled. The upgrade removed wicd from my installation and I'm not too sure how to start the GUI for network manager?

When I try to start nm-applet manually I get the following and nothing appearing in front of me. 

```
** (nm-applet:12109): WARNING **: No connection defined
```

[FONT="Courier New"]**ps aux | grep nm**[/FONT]  shows that nm-applet is running.
I just need to get nm running so I can join my wireless network to re-install wicd.

---

### Post by mmand on 2008-11-02
Hi all. I have the same problem don had, except Kobalt's tip didn't fix it.

I have tried various things:

killall nm-applet
reinstall nm-applet
make sure nm-applet was in System->Preferences->Sessions (and I removed --sm-disable)
started nm-applet using alt+f2
started nm-applet using terminal; got no error when running it normally, but got error: 

```
** (nm-applet:32122): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:32122): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```when I tried to sudo it

I have removed Notification Area from my panel and re-added it (a few times, with nm-applet running and without). I thought I saw a flicker in the Notification Area when I started it once, but there was nothing there.

I think the only thing I have yet to try is change my theme (I use a dark one to save my eyes, I absolutely cannot use a light theme).

Does anyone have any ideas? If you need any other error messages or anything, feel free to ask. My wireless seems to work OK if I use a static IP (which I do at home, but cannot while on the road without risking IP overlap and the complications that come with that).

The new System->Preferences->Network Configuration also has me all screwed up. I see my home network in there, and tried getting DHCP working with the network I'm on right now, but got nothing. I ended up commandeering another computer to check what IPs were being used (and which the router wouldn't dish out with DHCP) so I could use a static IP. While that worked for this network, it would not if I were in a coffee shop or at another Wi-Fi hotspot.

Edit: Alright, so I tried changing my theme to Human (figured that would be a safe one, I'm not sure what the default Ibex theme is) with no such luck. It stayed gone.

---

### Post by holscher on 2008-11-02
> **mmand said:**
>  ...

I have the Exact same problem.

---

### Post by ninocass on 2008-11-02
same here :(

---

### Post by eiffel on 2008-11-04
Re: wireless won't work and icon doesn't show
I was having this problem after the recent upgrade and I found somewhere (well, here: [https://bugs.launchpad.net/ubuntu/+s...er/+bug/253948](https://bugs.launchpad.net/ubuntu/+s...er/+bug/253948)) that the solution for getting NetworkManagr back in the system tray was to delete all the lines in /etc/network/interfaces apart from:

auto lo
iface lo inet loopback

That worked for getting NetworkManager back but now my laptop freezes up when I boot up with my network card inserted or shortly after inserting my network card. Maybe it won't do this for you. So I'm looking for a better solution so that I can get my laptop back online.

So I'd recommend making a copy of /etc/network/interfaces first, if you want to try that.

---

### Post by karlatsaic on 2008-11-05
oops meant to post here [http://ubuntuforums.org/showthread.php?t=971482](http://ubuntuforums.org/showthread.php?t=971482)

---

