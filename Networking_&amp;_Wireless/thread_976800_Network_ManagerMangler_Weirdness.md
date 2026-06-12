---
title: "Network Manager/Mangler Weirdness"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by RMOP on 2008-11-09
NM has done some unwanted and unimagined things with my network connections.

All this after moving to 8.10. Never saw this with 8.04. I am using the backports approach to wifi on my eee PC instead of Madwifi, which may be a source of the problem. Who knows?

1) After initially working fine, my Auto eth0 connection failed and refused to reconnect. I examined it and noticed a MAC address in the properties of the connection. Since I didn't recall a MAC address being present in my Auto eth0 connection under 8.04 (maybe I never had cause to notice) and since this one wouldn't connect, I created a new connection w/o a MAC and with a different name and it worked fine. I left Auto eth0 unchanged. Later, I noticed that NM had created ANOTHER Auto eth0 connection, with a MAC address, and it then NM began connecting automatically through Auto eth0 when I plugged in my cable. So, I've now got TWO (2) identically named connections called "Auto eth0" and the one I created called just "Ethernet." One of the Auto eth0 connects now w/o a problem.

2) The wireless part is really fun. The WPA key keeps gets replaced by an alpha-numeric string, with numbers ranging 0-9 and letters a-f. SOMETIMES I get prompted for a WPA key, enter it, but find that what is actually being saved is the NM-generated a-n string, not the more complicated one I provide. Even odder to me is the fact that my wireless is connected now, even though the properties of that connection reflect the a-n string, not my own WPA TKI key. Just now, after I declined to re-enter my WPA key for the umpteenth time, it connected anyway and the network icon on the panel said "Wireless network connection to (none) 95%" -- this later reverted to the correct SSID for my wireless network.

3) My Bluetooth/3G phone connection is working fine. I can have all three connections active at once.

Time frame for all of this fun since installing 8.10 is about 36 hours. I'm glad things are still working, mostly, but these random NM-generated changes represent (to me) a strange and unstable state of affairs. I've noticed others have had their WPA key changed, but my experience with NM suggests even more problems with that application.

Suggestions?

---

### Post by JeremyHarrison on 2008-11-09
I'll second the comments. I just formatted a partition that had previously held a recent version of Mint Linux and did a new install of 8.10.

I have been having problems since the installation this morning with the wireless connection. Once it drops, it replaces the password with alpha-numeric characters and it refuses to pick up up the connection again until I reboot. 

Another problem I found was in moving from one network location to another. The wireless applet maintains a list of the the routers from the old location and there was nothing I could do, short of rebooting, to get it to see the router in the new location.

Going into sleep is a regular cause of the wireless pain. 

I hope someone has some advice because a laptop that can't be put into sleep mode is very limited. And I hate having to reboot.

---

### Post by ber0tec on 2008-11-10
Same problem here with Atheros. The WPA key keeps gets replaced by an alpha-numeric string after every wake up from suspend. My  work-around:
[LIST]
[*]uncheck "Enable Wireless" in Network Manager menu
[*]reload Atheros device driver:```
sudo modprobe -r ath_pci 
sudo modprobe ath_pci
```
[*]enable Wireless again 
[/LIST]

---

### Post by davidyu on 2008-11-10
I encounter ths similiar problem after I upgrade to 8.10.
Every time, I reboot Ubuntu, my wep wireless always could not be connected.
And Ubuntu prompts a dialogbox : Authentication required by wireless network. Funny thing is the password already included in the dialogbox. I click "Connect" button, and then the wireless was connected again.  I still look for best solution for this boring wireless issue in 8.10.
Any good idea ?

---

### Post by davidyu on 2008-11-10
My networkmanager works smoothly now after I did sth.
1. I put all 3 files in /etc/modprobe.d/blacklist
   blacklist ath_pci
   blacklist ath_rate_sample
   blacklist ath_hal
2. After reboot,
   Comment out  all 3 lines  in /etc/modprobe.d/blacklist
3. Reboot again, networkmanager works fine and doesn't request wireless again.

---

### Post by JeremyHarrison on 2008-11-10
Davidyu,

Can you walk us (or at least the perpetual newbies among us) through what you did in a little more detail? I would love to get rid of this darn problem. Are they blank files that you created or did you get them from somewhere? If so, where?

Edit: 

Okay, figured it out. You add those lines to the blacklist file in the folder you mentioned... Trying it now. Will report if it works for me as well.

2nd Edit:

I decided to try something else first. I selected Hardware Drivers from the Administration menu and saw that there are different drivers for the Atheros card. I'm and trying them and, so far, on a first boot, it picked up right away. I haven't put it through any tests yet, however, like sleep mode or moving to a new location.

---

### Post by RMOP on 2008-11-11
Well, I seem to have stumbled upon something that works, and has continued to work following several reboots and multiple simultaneous and sequential connections using wired, wireless and bluetooth modem. The irony is that I'm not entirely sure *why* it's working, but I'll tell you *what* I tried and *why*, to the degree that I can. It was mostly just experimental serendipity born from frustration. I was seriously considering reverting to Ubuntu 8.04...

1) I've always defined my network connection names by my router names (e.g, DD-WRT, etc.), rather than by SSID, since the latter tend to be a bit long as they are based on the location of my routers (e.g, MyName-AtHome-ISPName, MyName-Traveling, etc).

2) When my defined connections quit working from NM, and I kept getting requests for my WPA key, I decided to use the "*Connect to Hidden Wireless Network..*." option. However, my defined wireless NEVER showed up under this option, only "New" was available. So, I picked "New" and entered by router's SSID.

3) NM again prompted my for the WPA key, which I duly entered, and a connection was quickly established.

4) I go back to "Edit connections" to see what's happened. There is now a NEW wireless entry (no surprise) named "*Auto MySSID*." OK. I can live with that.

5) I Disable/Enable wireless. The connection is broken and then automatically re-establishes. Nice.

6) I plug in my CAT5 cable and THAT connection is established w/o breaking the wireless. Hmm...promising, I think.

7) I used wvdial to establish a bluetooth phone modem connection alongside active wired and wireless connections. No problem.

8) I cycled through variations of this to convince my now skeptical self that this whole setup is really working. Reboot a few times. It's working for now.

9) Observable oddity: the most recent time that my wireless connected, the wireless top panel icon reported, first "*Attempting to join the wireless network MySSID.*" However, upon connecting, it reported "*You are now connected to the wireless network '(none)'."* And, a left-click on the icon showed a list of the wireless networks, including my router's SSID. The radio button next to my router's SSID was unselected! Later, the message switched to report connection to my SSID, and the radio button, on second inspection, had also been selected.

10) I disabled/enabled wireless once again, and this time the connection to my hidden SSID was quick, and the icon reported the correct info straight away, not the "**(none)" nonsense. BUT, after a reboot, it reverted to the "(none)" business and continued to report that illogical state for some time. And, yes, the connection routes just fine, and my Ubuntu machine is actively registered on my router.

Conclusions? **NM displays highly idiosyncratic behavior**. But, for me, letting NM do the defining of networks seemed to help. Your mileage, of course, may vary. I'll try this all again when I'm traveling with my Linksys WTR54GS. I only hope it's as satisfactory as things now seem to be at home.

Good luck to you.

> **JeremyHarrison said:**
> I'll second the comments.

---

### Post by JeremyHarrison on 2008-11-12
RMOP,

I went through the approach you suggested step by step but it didn't work for me. The only difference now is that my network applet tells me it's connected even though it isn't. 

Can you check your password and see if it is still being replaced by a random series of alphanumeric characters?

How does not submit a bug report to the devs that make changes to these things? I woudl love to see this fixed.

---

