---
title: "HOWTO: Atheros AR5007EG wireless"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by bmartin on 2008-05-12
[COLOR="Red"]**As of Intrepid Ibex (Ubuntu 8.10), this HOWTO is considered obsolete. Please use [this wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") instead. Credit goes to eks for pointing this out.**[/COLOR]

---

### Post by fissionmailed on 2008-05-12
I could be wrong but the madwifi patch is just for 32-bit.  Unless they have a new HAL which is what I thought read was the problem.

---

### Post by bmartin on 2008-05-13
> **fissionmailed said:**
> I could be wrong but the madwifi patch is just for 32-bit.  Unless they have a new HAL which is what I thought read was the problem.
My mistake. I'll fix my message and link to another HOWTO.

---

### Post by Snappo on 2008-05-14
Would this work with my ar5000?

---

### Post by bmartin on 2008-05-15
> **Snappo said:**
> Would this work with my ar5000?
As long as you're using a 32-bit OS, it should. AFAIK, MadWiFi has worked with almost all Atheros wireless chipsets for quite some time. The AR5007EG was a notable exception; my girlfriend has that chipset in her laptop. It has been painful, even with NDISwrapper.

I tried to change the title to reflect the fact that the MadWiFi drivers should work with any 32-bit *buntu... apparently I can only change the title of the first post.

---

### Post by Alfred_McGee on 2008-05-15
I used a fix based on the same tarball, posted recently by Tom-X, but it said to disable Atheros Hardware Access Layer (HAL), which I did. My ar5007eg card now works nicely, but when I try to suspend or hibernate my laptop, the screen goes black, fills with code and freezes until I shut the computer down. Is that a problem for people using this fix by bmartin as well? His now-outmoded ndiswrapper fix for the same wifi card was once used and loved by millions of very feisty and gutsy people, so it seems reasonable to expect that this new fix will work better than the one I'm using, or that somebody on this thread will post a solution to the suspend problem. Anyone?

---

### Post by bmartin on 2008-05-15
> **Alfred_McGee said:**
> when I try to suspend or hibernate my laptop, the screen goes black, fills with code and freezes until I shut the computer down. Is that a problem for people using this fix by bmartin as well?
I can try performing a suspend or a hibernate on the laptop when I get home, to see if I'm having the same problem. I'll get back to you on that.
> **Alfred_McGee said:**
> His now-outmoded ndiswrapper fix for the same wifi card was once used and loved by millions of very feisty and gutsy people
I wouldn't say it's outmoded. AFAIK, 64-bit users can't use the patched MadWiFi. I would also guess that you could try using NDISwrapper, and if it solves your problems, you might want to stick with it.

Using NDISwrapper in Hardy, my girlfriend's wireless performance was flaky, at best, whereas it was fine in Feisty and Gutsy. Hardy has so many hardware support improvements that I don't think I'll be reverting to Gutsy or Feisty any time soon.

---

### Post by thecowking on 2008-05-16
Just a quick thanks, I've been trying to get my Toshiba Equium P200-1ED to get the wifi working for weeks now, then I found this thread and it was working by the end of the first post!

My thanks :)

---

### Post by saikas on 2008-05-16
Hi,

I want to ask, does this code work on my Amil A1650G? Becouse i'm trying all week to work my wireless, but still nothing. 
I'm new on Ubuntu and just don't know any code.

---

### Post by Snappo on 2008-05-16
> **bmartin said:**
> As long as you're using a 32-bit OS, it should. AFAIK, MadWiFi has worked with almost all Atheros wireless chipsets for quite some time. The AR5007EG was a notable exception; my girlfriend has that chipset in her laptop. It has been painful, even with NDISwrapper.

I tried to change the title to reflect the fact that the MadWiFi drivers should work with any 32-bit *buntu... apparently I can only change the title of the first post.

I run a 32 bit system and it failed to work. :(

---

### Post by bladebot on 2008-05-16
<3 THANK GOD.  I offer my girlfriend as payment.

---

### Post by Alfred_McGee on 2008-05-19
Wifi card works, but my Acer is still unable to suspend or hibernate. It wasn't a problem before this fix. In the midst of the code on my screen after it goes black, I see things like this: 
ieee80211_vap_detach
ath_vap_delete
ath_detach
ath_pci_remove
pci_device_remove

This is not a complete transcription of the code that comes up, but it does seem to hint that the problem is related to my Atheros card. Anybody know how to fix this so I don't have to go back to the shame of Ndiswrapper?

---

### Post by bmartin on 2008-05-19
> **Alfred_McGee said:**
> Anybody know how to fix this so I don't have to go back to the shame of Ndiswrapper?
If NDISwrapper works... that's cool. I don't have anything against it. Does your wireless work better and faster w/ this new driver?

As for support, try the [MadWiFi mailing list]("http://madwifi.org/wiki/Support").

---

### Post by Alfred_McGee on 2008-05-19
Yeah, it's better. Having native Linux drivers makes it possible to put my AR5007 in monitor mode, and stuff like that, and all the other features are at least as good. For some reason, Wicd now refreshes its display of AP signal strength much more frequently. This improvement, which makes Wavemon almost redundant, is probably due to the new Wicd version rather than the new Linux drivers, but still, it sure helps when you're hunting for that sweet spot...

---

### Post by bmartin on 2008-05-21
> **bladebot said:**
> <3 THANK GOD.  I offer my girlfriend as payment.
I'm married, but thanks for the offer.
> **Alfred_McGee said:**
> Wifi card works, but my Acer is still unable to suspend or hibernate. It wasn't a problem before this fix. In the midst of the code on my screen after it goes black, I see things like this: 
[B]ieee80211_vap_detach
ath_vap_delete
ath_detach
ath_pci_remove
pci_device_remove[/B]

While I can't say how it can be fixed (it probably requires modification of the driver source code), I'd recommend you complain to the guys at MadWiFi. Let them know what you're seeing when you attempt to suspend/hibernate, particularly those messages above (the stuff I put in bold).

I'm putting a [link to the ticket submission page]("http://madwifi.org/wiki/TicketSubmissionGuidelines") on the first post. In order to get these drivers fixed, you're going to have to tell them about your problem. Please be patient with them; they may need you to run test out your problems so they can diagnose what's wrong.

---

### Post by beN..87 on 2008-05-23
using a samsung r60+ its got ATI Radeon chips in it - this should work cos ive got that wireless chip 100% - ive done it this way - and niceguy's way - all on a fresh laptop with fresh install - still no luck -- i can get ubuntu up and running - graphics are sweet as a nut, it recognises the wireless signal after i install madwifi - ive tried bothe versions - the 2537 you used here and the 3366 version here in nicedudes way [http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)  ---   anyways it still wont work even with synaptic disabling the jockey and whatnot - i get a signal - but cannot get an IP adress - it isnt the box cos that works with XP, Vista , and Linux on another Machine.

i reckon its the ATI proprietry driver that nicedude talks about in that last thing i linked to - but ive tried it his way and it doesnt work either - something to do with the ATI chips proprietry driver locking stuff up? 

any ideas?

---

### Post by mD3m4r415 on 2008-05-26
hello
i have used this tut and it worked until i restarted my laptop.. now i try to redo it but that will not work.. please post how to do it and make it stay like that after a reboot.

---

### Post by bmartin on 2008-05-26
> **mD3m4r415 said:**
> please post how to do it and make it stay like that after a reboot.
```
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci
```
The first command makes it so that the driver will be inserted when you reboot.

The second command inserts the driver. Make sure you **copy and paste** the commands into the terminal.

---

### Post by Alfred_McGee on 2008-05-27
This fix by bmartin has now been updated, it seems, to use the 3366 tarball, instead of the 2756 one that apparently gave me suspend/hibernate trouble before. My laptop suspends now, but installing an rt73 wifi card on it seems to have disabled ar5007eg function. At first, both cards worked beautifully, but after a reboot, my Atheros card seems to be dead again. It might have something to do with Ubuntu network managing software getting reinstalled with the rt73 drivers. Does anybody know?

---

### Post by ElEdTech on 2008-05-28
> **Alfred_McGee said:**
> This fix by bmartin has now been updated, it seems, to use the 3366 tarball, instead of the 2756 one that apparently gave me suspend/hibernate trouble before.

The 3366 Tarball fixed the suspend and hibernate issues I was having with 2756 as well. Before I would get a crazy black screen with lots of white text. After uninstalling the 2756 tarball and reinstaling the 3366, my wifi works and my suspend/hibernate works!

---

### Post by bmartin on 2008-05-28
> **Alfred_McGee said:**
> This fix [...] My laptop suspends now, but installing an rt73 wifi card on it seems to have disabled ar5007eg function.
Are you trying to double your bandwidth? I don't have any experience with setting up a **network bridge**, which is probably what you want. Normally you'd only have one wireless device working at a time.

Thanks for letting me know that this fixed the suspend/hibernate problems. I updated the driver on my gf's computer so that she'll have that functionality, should she ever decide to use it.

---

### Post by Samnsparky on 2008-05-30
Wow! I am **very** impressed! It worked on the first try and (appears) to be faster than the ndiswrapper alternative.

Good Work!

p.s. I had to use the additional commands to get my card fully functional:

echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

---

### Post by quentindemetz on 2008-05-31
I love you - I had installed Gutsy 64 bit before and had so much pain with ndiswrapper, this is the reason I'm on 32-bit hardy today! Thanks!

---

### Post by Alfred_McGee on 2008-05-31
Hi bmartin. On Feisty, it wasn't necessary to use network bridge, I used to use two wifi cards (rt73 and ar5007eg) at the same time- a very useful practice when running certain applications. I do remember RutilT seemingly snuffing out my ar5007eg card (running with ndiswrapper) for a time, but the problem somehow solved itself. I don't know how that happened, though, and I don't seem to be able to get it to happen again in Hardy. Two other forum members have reported having the same issue...

Since this problem never emerges before rebooting, I wonder if it has something to do with the command "sudo modprobe ath_pci" Anybody know what file this command writes to, or whether I am barking up the wrong tree?

---

### Post by bmartin on 2008-05-31
> **Alfred_McGee said:**
> Since this problem never emerges before rebooting, I wonder if it has something to do with the command "sudo modprobe ath_pci" Anybody know what file this command writes to, or whether I am barking up the wrong tree?
That command loads the Atheros driver into memory. AFAIK, modprobe doesn't do any I/O (i.e., file writing). In fact, it hardly does anything at all; the kernel itself resolves/loads whatever dependencies the kernel module (read: driver) has. modprobe simply initiates the process.

You'd probably have to get a wireless expert to give you a hand w/ tracking down the problem. The **dmesg** command prints out a list of kernel messages, which tell you about some of the hardware-related things happening in the OS. The /var/log/messages file might contain a few clues, too. They both are updated on certain hardware events.

---

### Post by gusanto on 2008-06-03
> **bmartin said:**
> ```
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci
```
The first command makes it so that the driver will be inserted when you reboot.

The second command inserts the driver. Make sure you **copy and paste** the commands into the terminal.

Hi Bmartin,
Following your suggestion, my wireless card is autodected after boot but I still need to refresh my connection (I use wicd) to connect to internet. Before upgrading to Ubuntu 8.04, it's autodected and autoconnected. Any more idea for this?

---

### Post by mix25 on 2008-06-06
It's not work. I installed it, i can see it on my panel i see my home wifi network. i try to connect i put my password for the network but then doesn't connect. What can i do?

---

### Post by bmartin on 2008-06-06
> **mix25 said:**
> It's not work. I installed it, i can see it on my panel i see my home wifi network. i try to connect i put my password for the network but then doesn't connect. What can i do?
Since I don't want to respond to this question over and over, I put a FAQ at the bottom of the first post, copied from another thread I wrote. It should provide some guidance. You're experiencing the most common problem people have (i.e., I can see networks, but I can't connect to them). The solutions are vary.

---

### Post by lorgonjortle on 2008-06-07
bmartin, you are my hero. I have been trying for weeks to get this working, I have tried so many things... Installed/downloaded so many files... and all I had to do was this. Thanks so much!

---

### Post by hvshah69 on 2008-06-14
It seems like madwifi servers are down just when I decide to try this method:(

Can anyone host the patched driver *madwifi-nr-r3366+ar5007.tar.gz* please. I badly need it.

Thanks.

---

### Post by bmartin on 2008-06-14
> **hvshah69 said:**
> Can anyone host the patched driver *madwifi-nr-r3366+ar5007.tar.gz* please. I badly need it.
[http://blakecmartin.googlepages.com/madwifi-nr-r3366ar5007.tar.gz](http://blakecmartin.googlepages.com/madwifi-nr-r3366ar5007.tar.gz)

There's a limited supply of bandwidth for this site, so grab it soon.

---

### Post by hvshah69 on 2008-06-14
Many thanks bmartin for hosting the file. You certainly saved me.

I love Ubuntu Community and the support that is available.

Cheers:)

---

### Post by hvshah69 on 2008-06-14
OK. It is a no-go for me. I have Acer Aspire 5570Z with AR5007EG card

I was running ndiswrapper before this but it would not connect to a secured wifi. So I decided to uninstall ndiswrapper and give this a try. Now I am not sure whether I have been successful at removing all the traces of ndiswrapper from the system. 

But here is the error I get while executing the *modprobe* command

```
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-18-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Here is the output of dmesg | grep ath_
```
[   30.798382] ath_pci: Unknown symbol _ath_hal_attach
[   30.798510] ath_pci: Unknown symbol ath_hal_process_noisefloor
[   30.798927] ath_pci: Unknown symbol ath_hal_computetxtime
[   30.799290] ath_pci: Unknown symbol ath_hal_mhz2ieee
[   30.799452] ath_pci: Unknown symbol ath_hal_detach
[   30.800071] ath_pci: Unknown symbol ath_hal_probe
[   30.800874] ath_pci: Unknown symbol ath_hal_init_channels
[   30.801164] ath_pci: Unknown symbol ath_hal_getwirelessmodes
[ 1165.382637] ath_hal: 0.10.2.2-ATHEROS (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133, RF2425)
[ 1165.387099] ath_pci: Unknown symbol ieee80211_check_mic
[ 1165.387281] ath_pci: disagrees about version of symbol ieee80211_encap
[ 1165.387287] ath_pci: Unknown symbol ieee80211_encap
[ 1165.387448] ath_pci: disagrees about version of symbol ieee80211_input
[ 1165.387454] ath_pci: Unknown symbol ieee80211_input
[ 1165.387597] ath_pci: disagrees about version of symbol ieee80211_ifattach
[ 1165.387603] ath_pci: Unknown symbol ieee80211_ifattach
[ 1165.387895] ath_pci: Unknown symbol ieee80211_skb_untrack_debug
[ 1165.388042] ath_pci: disagrees about version of symbol ieee80211_beacon_update
[ 1165.388049] ath_pci: Unknown symbol ieee80211_beacon_update
[ 1165.388218] ath_pci: Unknown symbol ieee80211_dev_kfree_skb_list_debug
[ 1165.388572] ath_pci: disagrees about version of symbol ieee80211_vap_setup
[ 1165.388579] ath_pci: Unknown symbol ieee80211_vap_setup
[ 1165.388684] ath_pci: disagrees about version of symbol ieee80211_ifdetach
[ 1165.388690] ath_pci: Unknown symbol ieee80211_ifdetach
[ 1165.388856] ath_pci: Unknown symbol ieee80211_find_txnode_debug
[ 1165.388978] ath_pci: disagrees about version of symbol ieee80211_input_monitor
[ 1165.388984] ath_pci: Unknown symbol ieee80211_input_monitor
[ 1165.389239] ath_pci: disagrees about version of symbol ieee80211_crypto_newkey
[ 1165.389245] ath_pci: Unknown symbol ieee80211_crypto_newkey
[ 1165.389438] ath_pci: disagrees about version of symbol ieee80211_crypto_setkey
[ 1165.389445] ath_pci: Unknown symbol ieee80211_crypto_setkey
[ 1165.389651] ath_pci: disagrees about version of symbol ieee80211_dump_pkt
[ 1165.389657] ath_pci: Unknown symbol ieee80211_dump_pkt
[ 1165.389784] ath_pci: Unknown symbol ieee80211_dev_alloc_skb_debug
[ 1165.389896] ath_pci: disagrees about version of symbol ieee80211_ioctl_create_vap
[ 1165.389903] ath_pci: Unknown symbol ieee80211_ioctl_create_vap
[ 1165.390089] ath_pci: disagrees about version of symbol ieee80211_stop_running
[ 1165.390096] ath_pci: Unknown symbol ieee80211_stop_running
[ 1165.390312] ath_pci: Unknown symbol ieee80211_dev_kfree_skb_debug
[ 1165.390452] ath_pci: disagrees about version of symbol ieee80211_cipher_none
[ 1165.390459] ath_pci: Unknown symbol ieee80211_cipher_none
[ 1165.390656] ath_pci: disagrees about version of symbol ieee80211_crypto_delkey
[ 1165.390662] ath_pci: Unknown symbol ieee80211_crypto_delkey
[ 1165.390840] ath_pci: Unknown symbol ath_debug_global
[ 1165.391043] ath_pci: disagrees about version of symbol ieee80211_beacon_miss
[ 1165.391049] ath_pci: Unknown symbol ieee80211_beacon_miss
[ 1165.391152] ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
[ 1165.391158] ath_pci: Unknown symbol ieee80211_beacon_alloc
[ 1165.391268] ath_pci: disagrees about version of symbol ieee80211_getcfframe
[ 1165.391274] ath_pci: Unknown symbol ieee80211_getcfframe
[ 1165.391384] ath_pci: disagrees about version of symbol ieee80211_iterate_nodes
[ 1165.391391] ath_pci: Unknown symbol ieee80211_iterate_nodes
[ 1165.391517] ath_pci: disagrees about version of symbol ieee80211_vap_attach
[ 1165.391523] ath_pci: Unknown symbol ieee80211_vap_attach
[ 1165.391649] ath_pci: Unknown symbol ieee80211_wme_updateparams
[ 1165.391769] ath_pci: Unknown symbol alloc_skb_debug
[ 1165.391874] ath_pci: disagrees about version of symbol ieee80211_ibss_merge
[ 1165.391881] ath_pci: Unknown symbol ieee80211_ibss_merge
[ 1165.392078] ath_pci: Unknown symbol skb_copy_debug
[ 1165.392526] ath_pci: disagrees about version of symbol ieee80211_rate_attach
[ 1165.392532] ath_pci: Unknown symbol ieee80211_rate_attach
[ 1165.392658] ath_pci: Unknown symbol ieee80211_unref_node_debug
[ 1165.392884] ath_pci: disagrees about version of symbol ieee80211_rate_detach
[ 1165.392891] ath_pci: Unknown symbol ieee80211_rate_detach
[ 1165.393134] ath_pci: disagrees about version of symbol ieee80211_send_qosnulldata
[ 1165.393141] ath_pci: Unknown symbol ieee80211_send_qosnulldata
[ 1165.393268] ath_pci: Unknown symbol ieee80211_find_rxnode_debug
[ 1165.393388] ath_pci: disagrees about version of symbol ieee80211_create_vap
[ 1165.393394] ath_pci: Unknown symbol ieee80211_create_vap
[ 1165.393704] ath_pci: Unknown symbol ieee80211_skb_track_debug
[ 1165.393805] ath_pci: disagrees about version of symbol ieee80211_input_all
[ 1165.393812] ath_pci: Unknown symbol ieee80211_input_all
[ 1165.393959] ath_pci: Unknown symbol ieee80211_ref_node_debug
[ 1165.394154] ath_pci: disagrees about version of symbol ieee80211_start_running
[ 1165.394161] ath_pci: Unknown symbol ieee80211_start_running
[ 1165.394259] ath_pci: disagrees about version of symbol ieee80211_vap_detach
[ 1165.394266] ath_pci: Unknown symbol ieee80211_vap_detach
[ 1165.394363] ath_pci: disagrees about version of symbol ieee80211_announce
[ 1165.394369] ath_pci: Unknown symbol ieee80211_announce
[ 1165.394464] ath_pci: disagrees about version of symbol ieee80211_mark_dfs
[ 1165.394469] ath_pci: Unknown symbol ieee80211_mark_dfs
[ 1165.394596] ath_pci: disagrees about version of symbol ieee80211_chan2ieee
[ 1165.394601] ath_pci: Unknown symbol ieee80211_chan2ieee
[ 1165.395065] ath_pci: disagrees about version of symbol ieee80211_dturbo_switch

```

Output from iwconfig is

```
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions
```
Can anyone help?

---

### Post by hvshah69 on 2008-06-14
Update to the above post:

Problem Solved on Rebooting the machine:KS

Thanks to the OP for posting the instructions.

I still need to make sure that I can stay connected with WPA protection.

---

### Post by rezuke on 2008-06-15
Thanks a bunch bro.  I didn't think that these steps worked for me until I tried to connect to my home network and when I did there were no problems whatsoever.  You see I was trying to connect to my schools WiFi connection but for some reason I can't seem to (I'll have to look into that one).  Anyway once I installed it when I was at school it didn't seem to work.  So my first reaction was that it might have been because I can never connect or the install just didn't work.  I've never had good experience getting WiFi to work on Linux and so far I think this had to be the easiest install for me.  I just had to wait and use my home connection before I knew that it really work.  So anyway thanks for the help.  Now I have more of a reason to use Ubuntu over Vista.

---

### Post by Robin.Muilwijk on 2008-06-28
Thanks for the post, I was able to uninstall ndiswrapper and get my atheros card up and running in 5 minutes with this guide.

---

### Post by destoned on 2008-06-29
I am new with ubuntu and I am trying to get my arth5007 wireless card to work.I must have tried for about 3days reading trying to understand but most commands don<t work on my terminal.I would need a (How to) from verifing my card to installing the files.I downloaded the madwifi-nr-r3366+ar5007.tar.gz file but I don<t know where to find it nor how to install it.Please Help.

---

### Post by bmartin on 2008-06-30
> **destoned said:**
> I must have tried for about 3days reading trying to understand but most commands don<t work on my terminal.
None of these commands are unusual. If they're not working in your terminal, either something is very broken and you should reinstall your OS, or you're not actually running Ubuntu. They should each do **something**. If you're getting "command not found" errors, something very serious is wrong with your install... or you're not using Ubuntu.
> **destoned said:**
> I would need a (How to) from verifing my card to installing the files.I downloaded the madwifi-nr-r3366+ar5007.tar.gz file but I don<t know where to find it nor how to install it.
The file is probably in your "Desktop" directory. To get there in the terminal, open the terminal up and type:
```
cd ~/Desktop
```
This is assuming you downloaded it in Firefox. If you downloaded it using the **wget** command from the terminal, it'll be in whatever directory you were in when you ran the wget command.

To verify you have an Atheros wireless "card", copy and paste the following into a terminal:
```
lspci | grep -i "Atheros.*Wireless"
```
If it outputs anything, you have one. If not, you don't. If you don't have one, this HOWTO won't help you with your wireless device.

Make sure you're using a 32-bit version of ubuntu.
```
uname -m
```
Should output "i686" or "i386" or something like that. If it says anything about 64, you're using a 64-bit version. In that case, you'll want to try NDISwrapper. There are other HOWTOs for that.

If you've gotten this far, try the commands in the first post. If they're not working, run this command:
```
cat /etc/issue
```
And make sure it outputs "Ubuntu" and some numbers and other junk.

After running the commands in the first post, you may have to restart your computer. The wireless device will probably be called "ath0". To check for its existence, run:
```
iwconfig
```
You should see something like this:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  [...]
```

If you've gotten this far, then you need to make sure your wireless device is scanning for networks. Run:
```
sudo iwlist scanning
```
You should see something like this:
```
ath0     Scan completed :
          Cell 01 - Address: 00:17:3F:65:91:62
                    ESSID:"belkin54g"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=71/100  Signal level=-47 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003c277cdf10
          Cell 02 - Address: 00:13:10:3C:2A:F1
                    ESSID:"pimpdaddy"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level=-72 dBm  Noise level=-72 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000d28151eef
          Cell 03 - Address: 00:12:0E:83:2A:BB
                    ESSID:"07B407531293"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level=-81 dBm  Noise level=-72 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000008216c88235
          Cell 04 - Address: 00:18:39:B3:F7:40
                    ESSID:"Ceralane"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/100  Signal level=-81 dBm  Noise level=-72 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000033216a6e186
          Cell 05 - Address: 00:17:3F:6B:C2:83
                    ESSID:"Ativa54gjay"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/100  Signal level=-83 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000332140a2181
```

If instead you see "no scan results", then you'll have to figure out how to enable your wireless radio. Some wireless devices have a switch on them, while others have a keyboard combination (such as Fn+F2). After figuring it out, run the command again and make sure your wireless network appears.

Then your device is ready to connect. Go to System > Administration > Network and set up your wireless network.

---

### Post by cammino on 2008-07-05
Thanks so much for your posting of this procedure. Have been trying to enable my Atheros wireless card on a Acer Aspire 3680 for quite some time. Worked great in just 5 minutes, spent way too much time elsewhere.

---

### Post by NMbottlecap on 2008-07-08
thanks to this walk through I am typing currently on my Ubuntu computer via WPA Thanks mate

---

### Post by eldenico on 2008-07-09
bmartin: Thanks to you, You're great! You're my hero! I've been trying to run my wireless for a long year. It works fine!.

I bought an Acer Aspire 5570-2405; I've read many posts and they never works, but just doing what you said it inmediatly works.

Many, many, many thanks.!!!!!!

Best Regards

---

### Post by pjcvdpol on 2008-07-10
So far so good, but what happens next is that my laptop freezes. argh!!!! I posted this thread, no-one reacted so far :-( [http://ubuntuforums.org/showthread.php?p=5355677#post5355677](http://ubuntuforums.org/showthread.php?p=5355677#post5355677)




> **bmartin said:**
> None of these commands are unusual. If they're not working in your terminal, either something is very broken and you should reinstall your OS, or you're not actually running Ubuntu. They should each do **something**. If you're getting "command not found" errors, something very serious is wrong with your install... or you're not using Ubuntu.

The file is probably in your "Desktop" directory. To get there in the terminal, open the terminal up and type:
```
cd ~/Desktop
```
This is assuming you downloaded it in Firefox. If you downloaded it using the **wget** command from the terminal, it'll be in whatever directory you were in when you ran the wget command.

To verify you have an Atheros wireless "card", copy and paste the following into a terminal:
```
lspci | grep -i "Atheros.*Wireless"
```
If it outputs anything, you have one. If not, you don't. If you don't have one, this HOWTO won't help you with your wireless device.

Make sure you're using a 32-bit version of ubuntu.
```
uname -m
```
Should output "i686" or "i386" or something like that. If it says anything about 64, you're using a 64-bit version. In that case, you'll want to try NDISwrapper. There are other HOWTOs for that.

If you've gotten this far, try the commands in the first post. If they're not working, run this command:
```
cat /etc/issue
```
And make sure it outputs "Ubuntu" and some numbers and other junk.

After running the commands in the first post, you may have to restart your computer. The wireless device will probably be called "ath0". To check for its existence, run:
```
iwconfig
```
You should see something like this:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  [...]
```

If you've gotten this far, then you need to make sure your wireless device is scanning for networks. Run:
```
sudo iwlist scanning
```
You should see something like this:
```
ath0     Scan completed :
          Cell 01 - Address: 00:17:3F:65:91:62
                    ESSID:"belkin54g"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=71/100  Signal level=-47 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003c277cdf10
          Cell 02 - Address: 00:13:10:3C:2A:F1
                    ESSID:"pimpdaddy"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level=-72 dBm  Noise level=-72 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000d28151eef
          Cell 03 - Address: 00:12:0E:83:2A:BB
                    ESSID:"07B407531293"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level=-81 dBm  Noise level=-72 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000008216c88235
          Cell 04 - Address: 00:18:39:B3:F7:40
                    ESSID:"Ceralane"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/100  Signal level=-81 dBm  Noise level=-72 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000033216a6e186
          Cell 05 - Address: 00:17:3F:6B:C2:83
                    ESSID:"Ativa54gjay"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/100  Signal level=-83 dBm  Noise level=-72 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000332140a2181
```

If instead you see "no scan results", then you'll have to figure out how to enable your wireless radio. Some wireless devices have a switch on them, while others have a keyboard combination (such as Fn+F2). After figuring it out, run the command again and make sure your wireless network appears.

Then your device is ready to connect. Go to System > Administration > Network and set up your wireless network.

---

### Post by racie on 2008-07-10
I did the tutorial, and everything seemed to have installed fine, but there is still no wireless option in "Network Settings."  I went into BIOS and changed some of the things that might help--Enabling the wireless at boot, etc.  I pressed Fn+F2 and nothing happens.  I switched the wireless switch on my laptop back and forth, but nothing happened.  How can this work for 74% of the Ubuntu users who viewed this topic, but not me?

---

### Post by Darkchef on 2008-07-11
> **hvshah69 said:**
> It seems like madwifi servers are down just when I decide to try this method:(

Can anyone host the patched driver *madwifi-nr-r3366+ar5007.tar.gz* please. I badly need it.

Thanks.

This method worked perfectly, just remember to do EXACTLY as the instructions tell you. However, the wifi light at the front of the laptop doesn't light up and is permanently on.

The madwifi server should be working :s

---

### Post by mattlezeay on 2008-07-12
ok, so I have been trying this forever and I am still working on it. I tried the trouble shooting and when I run iwconfig, I only get 
lo no wireless connection
eht0 no wireless connection

What do I do if it isn't setting up the card?

---

### Post by Darkchef on 2008-07-12
The driver works but it on some occassions when i boot it decides not to load the wireless driver, this seems a bit too buggy for me, is ndiswrapper a better option??

---

### Post by The Judderman on 2008-07-15
Thanks so much for this How To. Worked a treat on my new laptop!

---

### Post by kleugers84 on 2008-07-18
Thanks for the post! This did work for me after just a few minutes. However, I have since rebooted my laptop and now it is not working again. iwconfig does not show ath0. I will have to play around with it some more when I get home tonight.

---

### Post by bmartin on 2008-07-18
> **kleugers84 said:**
> Thanks for the post! This did work for me after just a few minutes. However, I have since rebooted my laptop and now it is not working again. iwconfig does not show ath0. I will have to play around with it some more when I get home tonight.
It's possible that your kernel version changed. If your computer was formerly not hooked up to an Internet connection, you probably just downloaded the new kernel and will have to reinstall the driver. You can hard-code which kernel version boots by default, but I wouldn't advise it.

It might also be the case that it's not starting up by default. Did you add the module name (ath_pci) to /etc/modules?

I'd start with those two things. Let me know if that solves your problem.

---

### Post by The Judderman on 2008-07-20
Thanks for this great HowTo. 

Funnily, it worked beautifully on a new install, without complications. Then on one day, it stopped working! I couldn't figure it out, untill I diabled the HAL tab on system>Admin>Hardware Drivers. Then it worked great!

Just for info...

Thanks!

The Judderman

---

### Post by jpirie on 2008-07-20
> **bmartin said:**
> [COLOR="Red"][B]The following was tested on 32-bit Ubuntu. It [COLOR="DarkOrange"][SIZE="5"]WILL NOT WORK[/SIZE][/COLOR] on a 64-bit Linux OS.



Here's some code that you can use to download, compile, and install the kernel module (read: driver) for the AR5007EG wireless chipset.

Hi everyone,
How do you suggest that someone tries to get the Atheros card operating when without it they have no internet conne4ction?  My modem is downstairs hard wired and all computers are wireless.  
Is there a way to utilise a windows Vista PC to download files etc and then try and apply the fix?

Thanks hopefully.

James

---

### Post by bmartin on 2008-07-20
> **jpirie said:**
> Hi everyone,
How do you suggest that someone tries to get the Atheros card operating when without it they have no internet conne4ction?  My modem is downstairs hard wired and all computers are wireless.  
Is there a way to utilise a windows Vista PC to download files etc and then try and apply the fix?

Thanks hopefully.

James
It'd be tough. You'd have to download the build-essential package and all of its dependencies, plus your kernel headers, and install everything manually with dpkg. Then you could download the code, compile and install it, and you'd be up and running.

If you can use a wired connection, do so. It'll make the whole process much less painful.

---

### Post by agentphish on 2008-07-20
worked like a charm.
Compaq c762NR.

Thanks VERY much, I know NOTHING about Linux/Ubuntu and I'm trying to set my laptop up for the first time with it.

peace

---

### Post by jpirie on 2008-07-21
> **bmartin said:**
> It'd be tough. You'd have to download the build-essential package and all of its dependencies, plus your kernel headers, and install everything manually with dpkg. Then you could download the code, compile and install it, and you'd be up and running.

If you can use a wired connection, do so. It'll make the whole process much less painful.
Ok, thanks for the advice.  SOunds like It may be easier to move my entire network centre up here for a day some time!  Takes my phone offline too though :(
There is another option however.  Dump the Atheros card and get a PCI belkin!  The Atheros chipset is built in to my Motherboard and has never inspired confidence!  IN fact, the original board wouldn't connect with anything until a BIOS udate came along.
I'll give it some thought.
I don't suppose the latest release of Hardy offers any solutions??   :icon_frown:

---

### Post by bmartin on 2008-07-21
> **jpirie said:**
> Ok, thanks for the advice.  SOunds like It may be easier to move my entire network centre up here for a day some time!  Takes my phone offline too though :(
There is another option however.  Dump the Atheros card and get a PCI belkin!  The Atheros chipset is built in to my Motherboard and has never inspired confidence!  IN fact, the original board wouldn't connect with anything until a BIOS udate came along.
I'll give it some thought.
I don't suppose the latest release of Hardy offers any solutions??   :icon_frown:
I have two laptops that run Hardy and have the Atheros 5007 chipset, and they both required these steps.

The Atheros chipset works very well after you have the driver installed. People used to get it working using NDISwrapper, but the performance with this driver is much better.

Even if you buy another chipset, you'll probably have to do something to get the wireless to work. Few wireless devices work out-of-the-box. It depends on which chipset you have. Atheros requires manual intervention. Broadcom has a driver, but you have to download the firmware. The RT chipsets all have 3rd party drivers readily available. Some of them work automatically, but it's rare, and the brand of the device doesn't tell you much about whether it will work automatically or not. See the list [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

---

### Post by agentphish on 2008-07-21
> **bmartin said:**
> It's possible that your kernel version changed. If your computer was formerly not hooked up to an Internet connection, you probably just downloaded the new kernel and will have to reinstall the driver. You can hard-code which kernel version boots by default, but I wouldn't advise it.

It might also be the case that it's not starting up by default. Did you add the module name (ath_pci) to /etc/modules?

I'd start with those two things. Let me know if that solves your problem.

I am having the same issue now. It worked the first time /w no problems, then after a reboot, I got nothing. I don't know what to try. I'm a total n00b and feel helpless because I don't know crap about terminal commands. I am seemingly unable to locate the /etc/modules folder in my main filesystem folder (where I assume it is) to place (ath_pci) into.

can someone please advise? Thanks!

---

### Post by Bachstelze on 2008-07-21
> **agentphish said:**
> I am having the same issue now. It worked the first time /w no problems, then after a reboot, I got nothing. I don't know what to try. I'm a total n00b and feel helpless because I don't know crap about terminal commands. I am seemingly unable to locate the /etc/modules folder in my main filesystem folder (where I assume it is) to place (ath_pci) into.

can someone please advise? Thanks!

If you're still using the version of madwifi that originally was in the first post of this thread, please download and install the one I mention in my note instead.

---

### Post by bmartin on 2008-07-21
> **HymnToLife said:**
> If you're still using the version of madwifi that originally was in the first post of this thread, please download and install the one I mention in my note instead.
Cool. Thanks for the info. I have a couple of computers to try it out on. Will it work on a 64-bit install, as well?

Hopefully the kernel module is distributed along with the next kernel, or pushed out as an update, or something like that. There are a lot of frustrated 5007 users that would love to have their chipsets working OOTB.

---

### Post by bmartin on 2008-07-21
> **agentphish said:**
> I am having the same issue now. It worked the first time /w no problems, then after a reboot, I got nothing. I don't know what to try. I'm a total n00b and feel helpless because I don't know crap about terminal commands. I am seemingly unable to locate the /etc/modules folder in my main filesystem folder (where I assume it is) to place (ath_pci) into.

can someone please advise? Thanks!
A quick way to load the kernel module manually is
```
sudo modprobe ath_pci
```
/etc/modules is a file, not a folder. To modify it, use
```
sudo gedit /etc/modules
```
However, you should use the newest driver. If there isn't a thread about it already, I'll write one up during my lunch break. I have a meeting right now.

---

### Post by Bachstelze on 2008-07-21
> **bmartin said:**
> Cool. Thanks for the info. I have a couple of computers to try it out on. Will it work on a 64-bit install, as well?

It should, though I've never tried it myself (the only relevant chipset I have is the one in my EeePC).

---

### Post by bmartin on 2008-07-23
I was unable to test the new driver on a Hardy LiveCD. My test subject, an Acer 5050, has a buggy ACPI and requires debugging/rebooting in order to get the ACPI working properly. I was unable to so much as get the wired networking working.

If anyone out there has previously tried this solution on a 64-bit install, try it again with the new driver and let us know whether it works or not.

---

### Post by Foxcow on 2008-07-27
Subscribed.  I am going to try this as soon as I get to my hotel

---

### Post by noneofit on 2008-07-28
hello.  I am new go ubuntu and have installed in on an acer 5100 laptop with the atheros ar5007eg.  From reading the forums I figure that I need to install the driver or maybe the ndiswrapper. But my ethernet port is broken, is there anyway I can download the packages with windows and install them on ubuntu?  Just normally?  

The atheros is turned on and is recognized by ubuntu but there are no wireless connections in the network connections.  Please, could someone confirm the driver is my problem?  Thank you.

---

### Post by efmaitnieh on 2008-07-31
when first try i can install driver succefully then i install vga driver using envy after that my network card can't be recognized by the ubuntu
then i retry to install driver 
when i write the ;
(sudo) modprobe ath_pci
it gives an error like that
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Operation not permitted

what is the problem and how can i solve or fix it
thanks

---

### Post by bmartin on 2008-07-31
> **noneofit said:**
> hello.  I am new go ubuntu and have installed in on an acer 5100 laptop with the atheros ar5007eg.  From reading the forums I figure that I need to install the driver or maybe the ndiswrapper. But my ethernet port is broken, is there anyway I can download the packages with windows and install them on ubuntu?  Just normally?  

The atheros is turned on and is recognized by ubuntu but there are no wireless connections in the network connections.  Please, could someone confirm the driver is my problem?  Thank you.
No, your problem is that your wireless radio is turned off. There's usually a switch on the outside of your computer case, or a keyboard combination (such as Fn+F2) which will turn on the wireless radio.

A quick way to scan for wireless networks is to type the following into a terminal:
```
sudo iwlist scanning
```

---

### Post by bmartin on 2008-07-31
> **efmaitnieh said:**
> when first try i can install driver succefully then i install vga driver using envy after that my network card can't be recognized by the ubuntu
then i retry to install driver 
when i write the ;
(sudo) modprobe ath_pci
it gives an error like that
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Operation not permitted

what is the problem and how can i solve or fix it
thanks
Hmmm... that's usually an indicator that you need "root permission" to perform the given operation. If you typed **modprobe ath_pci**, you'd receive that error. However, if you typed **sudo modprobe ath_pci**, you shouldn't receive that error. The sudo program gives you permission to perform just about any feasible operation on your computer (and should be used with caution).

---

### Post by jpirie on 2008-08-01
> **bmartin said:**
> I have two laptops that run Hardy and have the Atheros 5007 chipset, and they both required these steps.

The Atheros chipset works very well after you have the driver installed. People used to get it working using NDISwrapper, but the performance with this driver is much better.

Even if you buy another chipset, you'll probably have to do something to get the wireless to work. Few wireless devices work out-of-the-box. It depends on which chipset you have. Atheros requires manual intervention. Broadcom has a driver, but you have to download the firmware. The RT chipsets all have 3rd party drivers readily available. Some of them work automatically, but it's rare, and the brand of the device doesn't tell you much about whether it will work automatically or not. See the list [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").
Hi again bMartin,
Made the plunge and moved my network upstairs for the morning.  Your original code pasted into my Terminal worked like a charm first try!
Perfect.
Many many thanks.

James...back online at last.

---

### Post by mckinnley on 2008-08-02
i've done everything that you guys said to do but it still isn't working. when i type in "iwconfig" i get

lo        no wireless extensions.

eth0      no wireless extensions.

and when i type in "sudo iwlist scanning" i get this

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

i have the switch turned on and i tried the fn+f2 thing and it won't work. i've noticed that nobody else seems to have gotten these results from it, so can anyone help me out with this?

---

### Post by bmartin on 2008-08-02
> **mckinnley said:**
> i've done everything that you guys said to do but it still isn't working. when i type in "iwconfig" i get

lo        no wireless extensions.

eth0      no wireless extensions.

and when i type in "sudo iwlist scanning" i get this

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

i have the switch turned on and i tried the fn+f2 thing and it won't work. i've noticed that nobody else seems to have gotten these results from it, so can anyone help me out with this?
You're not at the stage where Fn+F2 or a switch will help you out at all. Considering you only have lo and eth0, your Atheros chipset (assuming you have one) isn't detected by the system. Try running **sudo modprobe ath_pci** and see if it shows up in the **ifconfig** list. If it doesn't, try **sudo ifconfig ath0 up**.

---

### Post by mckinnley on 2008-08-02
i typed "sudo modprobe ath_pci" into the terminal and got this

WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '&#8220;blacklist'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '&#8220;blacklist'

ok, i guess i'll type "ifconfig" into it and see what i get.
wow... it did something

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:9f:63:65  
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe9f:6365/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16851 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9775337 (9.3 MB)  TX bytes:716102 (699.3 KB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12300 (12.0 KB)  TX bytes:12300 (12.0 KB)

i believe this is the thing that it needed to do
should i type "sudo ifconfig ath0 up" or should it work right now?

ok i entered that and here's what i got

ath0: error fetching interface information: Device not found

edit: i should have that exact same wireless card. i have a toshiba setallite a215, which according to the specs, has that same chip in it. i don't know why it isn't recognizing it.

---

### Post by bmartin on 2008-08-02
> **mckinnley said:**
> WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '“blacklist'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '“blacklist'
This is a bad thing.

To fix the problem, use **sudo gedit /etc/modprobe.d/blacklist** and remove lines 40 and 41.

To make sure the driver is loaded, use the following:
```
lsmod | grep ath_pci
```
You should get some output. If you don't, the driver isn't loaded.

**sudo modprobe ath_pci** loads the driver. When you run that command, it should have **no output whatsoever**. If there is any output, there is a problem.

---

### Post by mckinnley on 2008-08-02
ok so i did the first thing and deleted lines 40 and 41, so then i went to the second thing and i guess i got some output. here is what i got.

ath_pci   101024 0
wlan      207728 1  ath_pci
ath_hal   192592 1  ath_pci

i have no idea what this means, so what do i do now?

---

### Post by bmartin on 2008-08-02
> **mckinnley said:**
> ok so i did the first thing and deleted lines 40 and 41, so then i went to the second thing and i guess i got some output. here is what i got.

ath_pci   101024 0
wlan      207728 1  ath_pci
ath_hal   192592 1  ath_pci

i have no idea what this means, so what do i do now?
The **lsmod** program shows you what kernel modules (basically, drivers) you have loaded; grep searches for a piece of text in the output of the program; so in this case, we only see lines with *ath_pci* in them. That's all.

The fact that ath_pci shows up indicates that your Atheros driver is loaded. If **ifconfig** shows only eth0 (or eth1, or whatever), and lo, that means you have no wireless device detected.

When the Atheros driver is working properly, it'll show up as ath0 (or something like that). It should be visible now. If not, try **sudo ifconfig ath0 up**. If that doesn't work, I'm out of ideas.

---

### Post by mckinnley on 2008-08-02
ok, so i did that and i got this

ath0: ERROR while getting interface flags: no such device

it's weird though, ubuntu seems to think that this wireless card simply doesn't exist in my computer, and yet i'm using it right now as i type... weird. so you don't have any idea of what i can do now? that sucks, maybe someone else can help me. it always seems like things always work for other people but they never work for me. it's always such a huge pain in the ***.
i'll get it working eventually.

---

### Post by bmartin on 2008-08-02
> **mckinnley said:**
> ubuntu seems to think that this wireless card simply doesn't exist in my computer, and yet i'm using it right now as i type... weird. so you don't have any idea of what i can do now?
Not really.

Did you receive any errors while compiling or installing the driver? If the driver didn't install property, you'd still be using the old kernel module and it wouldn't show your chipset.

What does **modinfo ath_pci | grep version** say? Mine says:
```
version:        svn r3772
srcversion:     5552256905B159E11968545
```

---

### Post by mckinnley on 2008-08-03
version   0.9.4
srcversion   D3FD3BD11169A96DBCFF8DE

---

### Post by bmartin on 2008-08-03
> **mckinnley said:**
> version   0.9.4
srcversion   D3FD3BD11169A96DBCFF8DE
There's your problem. You have the wrong version of the driver. It doesn't support the AR5007EG chipset.

OK, first, remove the current driver from memory
```
sudo modprobe -r ath_pci
```
Then run the instructions in the first post. Make sure you don't receive any errors.

Then use **modinfo ath_pci | grep version** to verify that the version of the driver is r3835.

If the version is wrong, something went wrong in the process. Copy and paste the commands into the terminal and you shouldn't have a problem.

---

### Post by mckinnley on 2008-08-04
i ran that line and then i ran the thing from the first post. so it took a while but the terminal finally stopped with the line

99% [906 Sources bzip2 0]

and now it won't do anything
when i typed in the command to see what version it says it still tells me

version:        0.9.4
srcversion:     D3FD3BD11169A96DBCFF8DE

so it seems that it didn't do anything. is there a reason why it stopped on that line? is there something that i'm supposed to do at this point?

edit: when i looked through all the stuff that it was doing from the first post i'm seeing "error reading from server" pop up a lot. this is probably the reason why it isn't working.
also when i try to run the update manager it fails to do a lot of the stuff that it's trying to do. then the whole thing just stops and i have to exit the whole thing because it just won't do anything. i have a feeling that it's this specific internet that i'm getting that won't let me download all the updates.

---

### Post by bmartin on 2008-08-04
> **mckinnley said:**
> i ran that line and then i ran the thing from the first post. so it took a while but the terminal finally stopped with the line

99% [906 Sources bzip2 0]

and now it won't do anything
when i typed in the command to see what version it says it still tells me

version:        0.9.4
srcversion:     D3FD3BD11169A96DBCFF8DE

so it seems that it didn't do anything. is there a reason why it stopped on that line? is there something that i'm supposed to do at this point?

edit: when i looked through all the stuff that it was doing from the first post i'm seeing "error reading from server" pop up a lot. this is probably the reason why it isn't working.
also when i try to run the update manager it fails to do a lot of the stuff that it's trying to do. then the whole thing just stops and i have to exit the whole thing because it just won't do anything. i have a feeling that it's this specific internet that i'm getting that won't let me download all the updates.
That could be it. **sudo aptitude update** command (equivalent to **sudo apt-get update**) updates your list of software packages. It has little to do with the version of ath_pci.

I don't know why it would be hanging at that step. You might be able to get by if you run only the second part of that line: **sudo aptitude -y install build-essential linux-headers-$(uname -r)**. Then just copy and paste the remaining lines and you should be good to go.

---

### Post by noneofit on 2008-08-04
> **bmartin said:**
> No, your problem is that your wireless radio is turned off. There's usually a switch on the outside of your computer case, or a keyboard combination (such as Fn+F2) which will turn on the wireless radio.

A quick way to scan for wireless networks is to type the following into a terminal:
```
sudo iwlist scanning
```

Thank you very much for the reply.  I've had a similar experience to mckinnley.  There is an external switch and it's on.  But I've typed in iwconfig and sudo iwlist scanning with the same results as mckinnley.  But I think I am missing the first steps of even installing a driver because my wired ethernet port is physically broken.  I was hoping there was a way I could download the packages with windows, and then transfer them to ubuntu and install it manually.  Thank you for any advice.

---

### Post by noneofit on 2008-08-04
> **noneofit said:**
> Thank you very much for the reply.  I've had a similar experience to mckinnley.  There is an external switch and it's on.  But I've typed in iwconfig and sudo iwlist scanning with the same results as mckinnley.  But I think I am missing the first steps of even installing a driver because my wired ethernet port is physically broken.  I was hoping there was a way I could download the packages with windows, and then transfer them to ubuntu and install it manually.  Thank you for any advice.


Sorry for the double post.  I've extracted the tar file for the madwifi driver but I need a little bit of guidance on how to install it.  I have tried typing "make" and the directory starting with "/home...." (sorry can't remember the exact directory).  The tar is extracted to the desktop.  But it says it can't find make.  I tried this because it says, in the install readme in the tar, to type "make" in the top directory of the tar.  I'm just not totally sure what "top directory" means, or the exact command I need, or if I'm typing the right command for the directory.  Thanks for any help.

---

### Post by bmartin on 2008-08-04
> **noneofit said:**
> Thank you very much for the reply.  I've had a similar experience to mckinnley.  There is an external switch and it's on.  But I've typed in iwconfig and sudo iwlist scanning with the same results as mckinnley.  But I think I am missing the first steps of even installing a driver because my wired ethernet port is physically broken.  I was hoping there was a way I could download the packages with windows, and then transfer them to ubuntu and install it manually.  Thank you for any advice.
It'll be a long and tedious process... if there's any way at all you can get a network connection in Ubuntu, it'd save you a lot of time.

I'll put up some instructions. Do you have a 32-bit or 64-bit processor? I'm assuming you're using a PC and not a Mac.

---

### Post by bmartin on 2008-08-04
For those of you that have no internet connection in Linux and want to download/install the packages manually, I've placed instructions in the FAQ section on the first page. Have at it.

---

### Post by Mon Jiller on 2008-08-05
I just wanted to say thanks for this. I had been trying to get the 64bit version working for a few hours to no avail. I installed the 32bit Ubuntu and this worked like a charm. 

I wish I tried this version hours ago. :grin:

---

### Post by JB_1980 on 2008-08-05
I was having problems with my atheros card, and installed a driver according to another How To. Well, it didn't work out so well. So I just did a fresh install, and went through your How To, and now my wireless works like a charm. I am using Ubuntu 8.04 amd64, so I was worried that it might not work. But it is running smoothly. Thanks for your help, you have alleviated a big headache. \\:D/

---

### Post by xnevermore on 2008-08-05
I've been using this for months on 64-bit Ubuntu. The ndiswrapper method did NOT work for me however.

Please edit original post to state that this does indeed work on 64-bit versions.

---

### Post by kajillin on 2008-08-08
I am connected through the lo, but in my firewall it shows that both ath0 and wifi0 are both active but the wifi0 is always active. when i try to switch just to the ath0 it say the device does not exist... also why does it say that the linux restricted hardware drivers are in use, are they and its just not the ubuntu provided, or what.

---

### Post by steam73 on 2008-08-11
Hi,
I am fairly new to linux and very new to Ubuntu. I installed Ubuntu just yesterday on an acer Aspiron 5720 with atheros 5007 wifi. My non-computer-linking wife was complaining about vista being very slow, and XP does not have a good working wifi driver for this wificard. The above method of installing the atheros driver worked, but I was still puzzled about how to get connected, non of the above posts are clear enough for me. After a few minutes of looking around I found this kind of works.
What I did was click on 'System/network then 'unlock' and click on the wireless-icon. There I inserted the SSID, WPA2, and password. This worked like charm. But after a reboot, the connection does not come back. When I look at the wifi setting, it is changed to WPA i.s.o. WPA-2!

How can I make this setting stick to WPA-2? And is there a command-line way to doe this?

---

### Post by bmartin on 2008-08-11
> **kajillin said:**
> I am connected through the lo, but in my firewall it shows that both ath0 and wifi0 are both active but the wifi0 is always active. when i try to switch just to the ath0 it say the device does not exist... also why does it say that the linux restricted hardware drivers are in use, are they and its just not the ubuntu provided, or what.
It's normal for both ath0 and wifi0 to be enabled. There's an option in the restricted drivers manager for Atheros HAL support, which should be **disabled**, as the new driver doesn't use HAL.

---

### Post by bmartin on 2008-08-11
> **steam73 said:**
> Hi,
I am fairly new to linux and very new to Ubuntu. I installed Ubuntu just yesterday on an acer Aspiron 5720 with atheros 5007 wifi. My non-computer-linking wife was complaining about vista being very slow, and XP does not have a good working wifi driver for this wificard. The above method of installing the atheros driver worked, but I was still puzzled about how to get connected, non of the above posts are clear enough for me. After a few minutes of looking around I found this kind of works.
What I did was click on 'System/network then 'unlock' and click on the wireless-icon. There I inserted the SSID, WPA2, and password. This worked like charm. But after a reboot, the connection does not come back. When I look at the wifi setting, it is changed to WPA i.s.o. WPA-2!

How can I make this setting stick to WPA-2? And is there a command-line way to doe this?
I've never heard of this problem before. You might want to post this message in its own thread in the wireless and networking forums.

If you change the setting to WPA-2 again, does it work? If not, I'd guess the problem's elsewhere. Try reinstalling the driver.

My fiancee's computer has XP and Hardy Heron on it and her AR5007EG is working fine is XP. If you're looking for a functional XP driver, I could probably help you out. I imagine it's the same driver as is used in the NDISwrapper method.

---

### Post by steam73 on 2008-08-11
I will start a new thread on this then. So you do not have to reply on these remarks. But yes, after I reset the wifi settings to WPA2 again, and fill in the password again, within a few seconds I have network connection again.

About half a year ago I tested an XP-driver but it was very buggy. The problem seams (as I understood from forum posts on this back then) that supposedly the same card in an Acer needs a different driver then that card in a Toshiba. If this is better now than 6 months ago, I am interested in the driver you use. But I will tell my wife only after I am out of possibilities with Ubuntu :lolflag:!

---

### Post by mello08 on 2008-08-15
thanks, this is the 5th guide that i tried and the only one that works :D

im using a compaq presario C793TU with the same atheros chip

---

### Post by nualaor on 2008-08-20
It really works, just fine only by your primary advice.
Thank you very very much.:)

[Acer Aspire 4520]

---

### Post by Perpetual on 2008-08-20
Question, each time there is a new kernel update, will this process have to be repeated to get wireless working?

Thanks for the HOWTO!

Landon

---

### Post by pmsumner on 2008-08-21
Unfortunately every time the kernel is updated you will need to re-do the:

```
make && make install
```

:(

I've also found that you get better results deleting the downloaded/built-in kernel modules first, though I don't know if this is necessary.

---

### Post by Perpetual on 2008-08-21
> **pmsumner said:**
> Unfortunately every time the kernel is updated you will need to re-do the:

```
make && make install
```

:(

I've also found that you get better results deleting the downloaded/built-in kernel modules first, though I don't know if this is necessary.

Yeah, found that out lastnight after a load of updates.  Lost wireless.  :sigh:

---

### Post by sarahparker on 2008-08-23
Thanks,
I finally got AR5007EG working on my Toshiba Satellite A305D S6848.
I followed bmartin's instructions and then also had to move to WICD.
After I installed WICD my network-manager was unstalled and so I lost internet connection. I had to go to System > Admin > Network and enabled Wired Connection first.
I also enabled wireless connection and found my ESSID in the drop down menu at which time I could connect to my wireless network.
Thanks again,
~Sarah

---

### Post by bmartin on 2008-08-25
> **pmsumner said:**
> Unfortunately every time the kernel is updated you will need to re-do the:

```
make && make install
```

:(

I've also found that you get better results deleting the downloaded/built-in kernel modules first, though I don't know if this is necessary.
Even better would be **make clean && make && sudo make install**.

That cleans out the old compiled code before building the new kernel modules.

Why can't this be included in the restricted drivers manager, or something to that effect?

---

### Post by Perpetual on 2008-08-25
bmartin, thanks for this.  Works perfect.  Not sure yet how I plan to handle any kernel updates in the future, may just pin the kernel rather than dealing with reinstalling the driver.

I have read that Intrepid will have the 2.6.27 kernel which I believe supports Atheros cards.

---

### Post by bmartin on 2008-08-25
> **Perpetual said:**
> bmartin, thanks for this.  Works perfect.  Not sure yet how I plan to handle any kernel updates in the future, may just pin the kernel rather than dealing with reinstalling the driver.

I have read that Intrepid will have the 2.6.27 kernel which I believe supports Atheros cards.
That's excellent news. Thanks for the update.

Being the scriptmonkey that I am, I wrote a script that starts up with the computer, detects a kernel version change, and rebuilds all of my custom-installed modules (currently only ath_pci, on my fiancee's laptop). I used to rebuild fglrx as well.

Not much usually changes within a release of Ubuntu; I've never seen a major kernel upgrade (they usually release a few different revisions), so you're probably safe to pin it in your menu.lst file... and then unpin it when Intrepid's released, as the problem should be resolved by then.

I used to work on a project called WiFix to take care of the wireless problem, but eventually so many cards were supported by Ubuntu that people were running the project and creating problems, rather than solving them. I'm glad to see that Ubuntu's finally getting almost up-to-speed on driver issues, since the 3rd party jerks that write the drivers scarcely bother to write one for Linux.

---

### Post by berov on 2008-08-25
Thanks a lot. it worked now.
I am using  Notebook MSI VR601X-011BG.
I am not sure tough if it worked because I switched the button for wireless ON or because of the double quotes which I put around my WEP hex key.
Until now I used a D-Link wireless usb adapter without the button switched on and without quotes.

I tried without quotes and the network became unreachable. Then I put them back - no network again. After restart Network reappeared :).
What is going on ?

---

### Post by bmartin on 2008-08-25
> **berov said:**
> I tried without quotes and the network became unreachable. Then I put them back - no network again. After restart Network reappeared :).
Are you typing commands into a terminal? I'd use the built in wireless or **wifi-radar** or **wicd**.

---

### Post by berov on 2008-08-26
I am using the GUI for Network Manager -Pure Ubuntu with GNOME.


it looks like this in terminal:
```

berov@berov-laptop:~$ cat /etc/network/interfaces 

iface ath0 inet dhcp
wireless-key "myverysecretkeyblabalablaba10hexadecimal"
wireless-essid berov-home

auto ath0
```

I think about using WICD

---

### Post by dreamthink on 2008-08-31
Thanks "bmartin", another 32 Bit success, it worked like a dream, my only trouble (as a complete nOOb) was finding your post in the first place !

Blissfully wireless since this morning running:  Ubuntu 8.04 on an Acer Aspire 3680 !

---

### Post by dentog on 2008-09-05
Thanks a lot !!!!!

Is there not painfull way to get a newer driver, how can I upgrade it?

---

### Post by bmartin on 2008-09-05
> **dentog said:**
> Thanks a lot !!!!!

Is there not painfull way to get a newer driver, how can I upgrade it?
Not really. Actually, I heard that in the Intrepid release, they're going to use a new kernel that has an Atheros driver built-in. If that's actually true, users won't have to do this anymore.

Intrepid Ibex (the next version of Ubuntu) [slated for release]("https://wiki.ubuntu.com/IntrepidReleaseSchedule") at the end of next month. I'll probably just grab the new kernel while sticking with Hardy Heron.

Before Intrepid is released, I'll check to see whether or not the new kernel does in fact support the Atheros AR5007EG chipset and let you know. If you're intending to upgrade to Intrepid when it comes out, you'll have something to look forward to.

---

### Post by cybrsaylr on 2008-09-05
> **bmartin said:**
> Not really. Actually, I heard that in the Intrepid release, they're going to use a new kernel that has an Atheros driver built-in. If that's actually true, users won't have to do this anymore.

Hope Intrepid comes quick because I still can't get my wireless back on my few month old Toshiba laptop. Lost it a couple weeks ago after installing 4 updates and have been strugging since to get it back. It used to work great. Went through this thread trying the fixes with no success.....still have no wireless and can't get any wireless networks to show as they did in the past when I had wireless.

---

### Post by bmartin on 2008-09-05
> **cybrsaylr said:**
> Hope Intrepid comes quick because I still can't get my wireless back on my few month old Toshiba laptop. Lost it a couple weeks ago after installing 4 updates and have been strugging since to get it back. It used to work great. Went through this thread trying the fixes with no success.....still have no wireless and can't get any wireless networks to show as they did in the past when I had wireless.
Intrepid's date will most likely stay fixed at 30. Oct.

If one of the updates was a kernel upgrade, you can use the old kernel. If you dual-boot, select the older kernel version in the GRUB menu. If you are running Ubuntu only, you'll have to hit ESC during boot to see that menu.

If you find a kernel version that works well, you can "pin" a kernel version so that you always use that kernel version. It'll remain pinned until you unpin it. More info can be found [here]("http://ubuntuforums.org/showthread.php?t=259280").

---

### Post by bmartin on 2008-09-05
For anyone following this thread checking for updates to the driver, I just updated the instructions with the newest driver (3. Sep). The previous version is 1. Aug.

---

### Post by cybrsaylr on 2008-09-05
> **bmartin said:**
> 
If one of the updates was a kernel upgrade, you can use the old kernel. If you dual-boot, select the older kernel version in the GRUB menu. If you are running Ubuntu only, you'll have to hit ESC during boot to see that menu.
Believe that was what happened, it was a kernel update, then did a required reboot and lost wireless from that point on.

I have a dual boot with Vista and tried using the old kernel but it didn't get wireless working again as another poster on another thread here recommended. I've tried so many fixes here I fear it may have messed things up in Hardy. At least Hardy still runs great wired.
BTW wireless still functions trouble free with Vista but I seldom use Vista anymore.

---

### Post by yanney on 2008-09-08
just to start off, im a pretty big noob at linux, but a huge computer nerd. 

when i type in > sudo modprobe ath_pci to the terminal, i get the following message.
> FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)


can anyone help me? please go into detail when you help too, because linux is tough to people just starting out. i've tried linux before, but i never stuck with it because i couldnt figure out how to set up the wireless.

please help soon.

---

### Post by bmartin on 2008-09-08
I'd retry the installation. I'm using the same kernel version as you are and it's working fine. There's no magic fix for that error.

---

### Post by yanney on 2008-09-08
rety the installation of ubuntu, or the installation of the drivers?

---

### Post by bmartin on 2008-09-08
> **yanney said:**
> rety the installation of ubuntu, or the installation of the drivers?
Sorry for the vagueness. Just reinstall the wireless driver.

---

### Post by yanney on 2008-09-08
im still getting that error. i wish this worked, i dont want to go back to linpus or xp. ubuntu works so good on this laptop.

---

### Post by bmartin on 2008-09-08
> **yanney said:**
> im still getting that error. i wish this worked, i dont want to go back to linpus or xp. ubuntu works so good on this laptop.
What have you installed since you installed Ubuntu? The only things I can think of that would cause this problem are related to compilation (e.g., wrong version of GCC, wrong version of kernel headers).

This sounds like a problem with your setup, not your method. I don't think you're doing anything wrong. You're using Hardy Heron, right?

---

### Post by yanney on 2008-09-08
im using One Linux (onelinux.org)

would switching to something else change the problem? cause i will gladly switch to hardy as long as its not too big for my laptop. (i have the 8gig acer aspire one)

---

### Post by bmartin on 2008-09-08
> **yanney said:**
> im using One Linux (onelinux.org)

would switching to something else change the problem? cause i will gladly switch to hardy as long as its not too big for my laptop. (i have the 8gig acer aspire one)
I bought an Acer 5050-3875 and put Linux on it. I won't be buying another Acer, ever.

Hardy would probably fit on your laptop, but you wouldn't have much room for anything else. I don't know what packages OneLinux uses, but my guess is that there's an incompatibility in the mix. I've never heard of the distribution before and it's beta software, so that could be the problem.

Did your system come with OneLinux on it? If so, why wasn't the wireless working in the first place?

If this group is targeting the Acer Aspire One specifically, maybe they know how to get this piece of hardware working. Many Acer laptops have this wireless device.

---

### Post by yanney on 2008-09-08
my system came with linpus linux on it. but it was too restrictive (couldnt install new programs, had to use their messenger, etc)

then i put XP lite on it, but it wasnt good either. then, one linux was made for this laptop, but i dont know why the wireless doesnt work. 

are there any versions of linux that are small and that ill have an easy time with the wireless on? prefferably ubuntu versions. 

i want to be able to use this method, and i like the way ubuntu is set up.

---

### Post by bmartin on 2008-09-08
> **yanney said:**
> my system came with linpus linux on it. but it was too restrictive (couldnt install new programs, had to use their messenger, etc)

then i put XP lite on it, but it wasnt good either. then, one linux was made for this laptop, but i dont know why the wireless doesnt work. 

are there any versions of linux that are small and that ill have an easy time with the wireless on? prefferably ubuntu versions. 

i want to be able to use this method, and i like the way ubuntu is set up.
Unfortunately, I don't think small was much of a consideration. There's Xubuntu, which is the smallest of the three. Ubuntu will fit on your machine with no problem. You probably won't have space for much else.

[Here are the recommended minimum requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements").

---

### Post by yanney on 2008-09-08
thank you for all the help. im going to go make an Ubuntu CD, install it, and ill be back to let you know if it works. thanks! bye

---

### Post by yanney on 2008-09-08
everything seems to have gone according to plan. im just waiting for the updates to install so i can restart.

---

### Post by yanney on 2008-09-08
the wireless just doesnt seem to want to work

sudo modprobe ath_pci  doesnt show the error anymore, but the laptop still doesnt recognize a wireless card.

any ideas?

---

### Post by bmartin on 2008-09-08
Not really. Normally, the card comes up as **ath0**. No networks show up if you type **sudo iwlist scanning**?

---

### Post by yanney on 2008-09-08
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

thats the only thing that shows up. =/

im afraid i may have to go back to linupus via my recovery disk

---

### Post by bmartin on 2008-09-08
> **yanney said:**
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

thats the only thing that shows up. =/
Does **sudo ifconfig ath0 up** help? What's the output of **modinfo ath_pci**?

---

### Post by cybrsaylr on 2008-09-08
I got the same output as yanney:

tt@tt-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tt@tt-laptop:~$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
tt@tt-laptop:~$ modinfo ath_pci
filename:       /lib/modules/2.6.24-19-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     60703EF59C04C8C6859AC83
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           tpc:Enable/disable per-packet transmit power control (TPC) capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
tt@tt-laptop:~$


Still can't get wireless back......

---

### Post by bmartin on 2008-09-08
> **cybrsaylr said:**
> version:        0.9.4
The version should be svn r3861.

Something went wrong with your install. It looks like you still have the built-in kernel module. Pay attention during compilation and let me know if anything goes wrong.

---

### Post by cybrsaylr on 2008-09-08
> **bmartin said:**
> The version should be svn r3861.

Something went wrong with your install. It looks like you still have the built-in kernel module. Pay attention during compilation and let me know if anything goes wrong.
How do I correct that?
I'm not sure of what to do next?

---

### Post by bmartin on 2008-09-09
> **cybrsaylr said:**
> How do I correct that?
I'm not sure of what to do next?
Follow the instructions in the first post, then run **modinfo ath_pci** and make sure you have the right version. Then restart your computer and check again. Seriously. The version should be svn r3861. If it is, check to see if your wireless is working. It should be.

When you update your packages in Ubuntu, you might download a new kernel. When that happens, you have to run the instructions in the first post again. The alternative to this is pinning your kernel version.

---

### Post by cybrsaylr on 2008-09-09
> **bmartin said:**
> Follow the instructions in the first post, then run **modinfo ath_pci** and make sure you have the right version. Then restart your computer and check again. Seriously. The version should be svn r3861. If it is, check to see if your wireless is working. It should be.

When you update your packages in Ubuntu, you might download a new kernel. When that happens, you have to run the instructions in the first post again. The alternative to this is pinning your kernel version.
Put this in terminal:

> sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

Then ran: modinfo ath_pci 
and still got this, the same version:

> tt@tt-laptop:~$ modinfo ath_pci
filename:       /lib/modules/2.6.24-19-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     60703EF59C04C8C6859AC83
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           tpc:Enable/disable per-packet transmit power control (TPC) capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
tt@tt-laptop:~$ 

---

### Post by Phoom on 2008-09-10
Thanks! It worked like a charm.

For the record, the computer I used it on is a HP laptop dv5-1003nr and installed AMD64 bit version of Ubuntu. 

After running your code as a script file and restarted, the hp laptop detected it and worked perfectly.

---

### Post by yanney on 2008-09-11
im about to install xubuntu and try again. wish me luck.

---

### Post by yanney on 2008-09-11
this method didnt work for me in Xubuntu either, so i used ndiswrapper in xubuntu and got it to work. its running good now.

---

### Post by bmartin on 2008-09-12
> **yanney said:**
> this method didnt work for me in Xubuntu either, so i used ndiswrapper in xubuntu and got it to work. its running good now.
Sounds like you have a slightly different chipset from everyone else. I can't believe the luck you've had. I'm glad you have it working now.

You might not have suspend/hibernate functionality with the NDISwrapper method, and if they do work, the device might not "wake up". Have you tried them yet?

---

### Post by jlawson on 2008-10-01
I am trying to do the wireless thing also.  Not having much luck.  Below is my attempt and the errors I am receiving.  It appears that everything is going great until I do my first 'make'.  Then i start receiving errors and warning.  

Anyone have ideas?
john

john@john-laptop:~$ sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
[sudo] password for john: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for build-essential
No candidate version found for build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
john@john-laptop:~$ cd
john@john-laptop:~$ ls
Desktop    Examples       Music     Public     Videos
Documents  madwifi-0.9.4  Pictures  Templates
john@john-laptop:~$ wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)
--21:54:49--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)
           => `driver.tar.gz'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,418,145 (4.2M) [application/x-gzip]

100%[====================================>] 4,418,145      1.12M/s    ETA 00:00

21:54:55 (785.50 KB/s) - `driver.tar.gz' saved [4418145/4418145]

john@john-laptop:~$ tar xf driver.tar.gz
john@john-laptop:~$ ls
Desktop        Examples                             Music     Templates
Documents      madwifi-0.9.4                        Pictures  Videos
driver.tar.gz  madwifi-hal-0.10.5.6-r3861-20080903  Public
john@john-laptop:~$ cd madwifi-hal-0.10.5.6-r3861-20080903/


*** Start of Errors ***

john@john-laptop:~/madwifi-hal-0.10.5.6-r3861-20080903$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/john/madwifi-hal-0.10.5.6-r3861-20080903 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath.o
  CC [M]  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_radar.o
  CC [M]  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_hal_extensions.o
  CC [M]  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath/if_ath_pci.o
  LD [M]  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath/ath_pci.o
  CC [M]  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/ah_os.o
  HOSTCC  /home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c: At top level:
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c: In function 'main':
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal/uudecode] Error 1
make[2]: *** [/home/john/madwifi-hal-0.10.5.6-r3861-20080903/ath_hal] Error 2
make[1]: *** [_module_/home/john/madwifi-hal-0.10.5.6-r3861-20080903] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

---

### Post by pmsumner on 2008-10-01
Here's your problem:

> No candidate version found for build-essential
No candidate version found for build-essential

Somewhere in the output to your aptitude update && aptitude install build-essential

I don't know how to fix that at this time of the morning but for some reason aptitude can't find the build-essential package.

---

### Post by EdenFuchs on 2008-10-02
Hi,

Followed your instructions in the masochistic scheme (without an Internet connection).
Got to the stage when I did "sudo dpkg -i *.deb", and did not know what to do next.
I thought of improvising and doing the "wget -O driver... " command, with the local path of the [COLOR="Navy"]madwifi-hal...tar.gz[/COLOR] instead of the http:// path. does that make sense?
anyway, it said "... unsupported scheme"

any advice?

---

### Post by donaldshelton on 2008-10-12
This worked until I got to the command  wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6)

I got the following response:

--2008-10-12 16:00:18--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6)
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-10-12 16:00:19 ERROR 404: Not Found.


Now what?  I have a 32 bit system

---

### Post by Perpetual on 2008-10-12
> **donaldshelton said:**
> This worked until I got to the command  wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6)

I got the following response:

--2008-10-12 16:00:18--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6)
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-10-12 16:00:19 ERROR 404: Not Found.


Now what?  I have a 32 bit system

Looks to me like you cut off the end of the command.  It should be

```

wget -O driver.tar.gz http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz

```

---

### Post by bmartin on 2008-10-12
> **donaldshelton said:**
> This worked until I got to the command  wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6)

I got the following response:

--2008-10-12 16:00:18--  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6)
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2008-10-12 16:00:19 ERROR 404: Not Found.


Now what?  I have a 32 bit system
The code box cuts off the text. You missed part of the URL. The entire things is

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)

Make sure you copy the entire URL.

---

### Post by helwitch on 2008-10-14
> **bmartin said:**
> [COLOR="Red"]Note: the driver in the instructions may not be the newest version released. If there's a newer version, it can be found [here](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)
I believe if you link to [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz) that it always links the latest version.

---

### Post by bmartin on 2008-10-14
> **helwitch said:**
> I believe if you link to [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz) that it always links the latest version.
Thanks for the tip; I updated the instructions.

---

### Post by tuxdalinuxpenguin on 2008-10-21
One thing i just noticed. I did this with a fresh install of ubuntu and the kernel was "2.6.24-19-generic", then i just did updates and the wireless stopped working. The kernel was updated in the updates to "2.6.24-21-generic" i tried to remake it and the modprobe threw an error saying it could not find a file. To fix this i had to pretty much start it over. I do not know if anyone else had this problem but its the only issue, id did disconnect me a couple times, but i will have to see if thats going to keep happening.

The process i did to fix this was as follows:
 *-remove the madwifi* dir using sudo of course
 *-extract the tar again
 *-make and sudo make install
 *-then modprobe it... then i had to reboot to get it to see any wireless connections, i should have tried iwlist ath0 scanning.

But thanks for the info on this, ndiswrapper and the drivers for this card suck... 1 out of 10 drivers seemed to work and the drivers that work with that distro change from distro to distro. Debian the drivers for x64 and 32 versions worked great from [www.atheros.cz](www.atheros.cz) and ubuntu was different (thats how i stumbled onto it tonight) and opensuse failed to even work as usual. Also mandriva just locked up on its initial boot when it tried to load the nics. 

Also my final word is this, why is it linux and atheros seem incompatable??? my view is different now with my laptop but my desktop has the atheros l1 nic in it and i havnt found a distro that will detect that automatically. :S but o well.

~Tuxdalinuxpenguin

---

### Post by bmartin on 2008-10-22
> **tuxdalinuxpenguin said:**
> Also my final word is this, why is it linux and atheros seem incompatable??? my view is different now with my laptop but my desktop has the atheros l1 nic in it and i havnt found a distro that will detect that automatically. :S but o well.

~Tuxdalinuxpenguin
Every time your kernel is upgraded, you'll have to reinstall the MadWiFi driver.

For the longest time, NDISwrapper sufficed and wireless wasn't the top priority. Since I've started using Ubuntu (back in the Edgy days), many wireless chipsets have gone from completely unsupported to completely supported, but there's still a long way to go, I fear.

Broadcom was probably the most notable example; it seemed at the time that everyone had a Broadcom chipset and was having a miserable time. I think Gutsy Gibbon was the first distribution to support Broadcom OOTB.

Now it seems that the thorn in everyone's side is Atheros. Intrepid Ibex has built-in support via the ath5k driver. I've tried it; it works spectacularly.

Intrepid is scheduled for release 30. Oct.

---

### Post by Skylancer on 2008-11-01
WOO! Wireless working again! \\:D/
Ive always had broadcom in the past with my hp latops.
Now with the DV5-1000 series I have Atheros.
Now I just need to patch Backtrack with the newest madwifi...

---

### Post by tuxdalinuxpenguin on 2008-11-02
> **bmartin said:**
> Every time your kernel is upgraded, you'll have to reinstall the MadWiFi driver.

For the longest time, NDISwrapper sufficed and wireless wasn't the top priority. Since I've started using Ubuntu (back in the Edgy days), many wireless chipsets have gone from completely unsupported to completely supported, but there's still a long way to go, I fear.

Broadcom was probably the most notable example; it seemed at the time that everyone had a Broadcom chipset and was having a miserable time. I think Gutsy Gibbon was the first distribution to support Broadcom OOTB.

Now it seems that the thorn in everyone's side is Atheros. Intrepid Ibex has built-in support via the ath5k driver. I've tried it; it works spectacularly.

Intrepid is scheduled for release 30. Oct.

Well mine doesnt work im going to look into it and see what the problem is. I just installed intrepid and it automatically turned that on and well it shows another device in iwconfig but no wireless extension. To top it off the snapshots.madwifi.org that domain is no longer accessable. Im guessing it may be temporary but all day today (Nov 2 2008) it has been down, and madwifi.org was down at around 1pm central time also but now its back up. But if anyone figures out if the built in driver in ubuntu works with  the ar5007eg wireless card let me know how you did it, if i figure it out i will put it up here.

---

### Post by tuxdalinuxpenguin on 2008-11-03
wget -O driver.tar.gz [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz) there changed domains?

---

### Post by eks on 2008-11-03
> **tuxdalinuxpenguin said:**
> To top it off the snapshots.madwifi.org that domain is no longer accessable. Im guessing it may be temporary but all day today (Nov 2 2008) it has been down, and madwifi.org was down at around 1pm central time also but now its back up. But if anyone figures out if the built in driver in ubuntu works with  the ar5007eg wireless card let me know how you did it, if i figure it out i will put it up here.

**[SIZE="4"]Yes, the built in driver works on Intrepid[/SIZE]**. Here are some links:

[http://ubuntuforums.org/showpost.php?p=6089169&postcount=3](http://ubuntuforums.org/showpost.php?p=6089169&postcount=3)
[https://answers.edge.launchpad.net/ubuntu/+question/49927](https://answers.edge.launchpad.net/ubuntu/+question/49927)

In short, install linux-backports-modules-intrepid package, turn on the driver on System/Administration/Hardware Drivers and make sure **only** ath_pci and ath_hal are blacklisted on /etc/modprobe.d, and comment every blacklisting of ath5k you find.

---

### Post by tuxdalinuxpenguin on 2008-11-03
Well i did see that first link you posted... i tried that but it was kind of quirky. It did not seem to connect well to wep encrypted connections but the mad-wifi driver works pretty well with it, though not the fastest. I'm going to book mark that for a later time and see if after a couple updates here and there it may change.

---

### Post by pmsumner on 2008-11-03
Thanks for that post.  I've got it working with the "proper" drivers now, so no longer will there be a need to recompile every time there's a new kernel release.

Connfused me for a bit - no longer is the wireless card known as ath0 - wlan0 is the future!

---

### Post by dj9928 on 2008-11-05
I'd like to know what I am doing wrong? I am using an Acer Aspire 5715z, Wireless is not shown in my netwrok connections, I go into hardware and it shows my Atheros AR5007EG and it is activated but when I go into network connections there is nothing there and no option to scan etc, I have ran the code in the 1st thread and it downloaded and installed a few thing, then there where updates available which I installed and rebooted but still no sign of my wireless anywhere,

---

### Post by eks on 2008-11-05
> **dj9928 said:**
> I'd like to know what I am doing wrong? I am using an Acer Aspire 5715z, Wireless is not shown in my netwrok connections, I go into hardware and it shows my Atheros AR5007EG and it is activated but when I go into network connections there is nothing there and no option to scan etc, I have ran the code in the 1st thread and it downloaded and installed a few thing, then there where updates available which I installed and rebooted but still no sign of my wireless anywhere,

Try the built-in modules. More information here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Problem is, since you've tried to install the driver manually, you might have to do all the steps mentioned on the first part.

Don't panic, it's not that difficult. Almost everything on Linux are just text files, open and easily accessible. ;)

---

### Post by dummiebeginner on 2008-11-06
Hi all,

I have this laptop with this atheros AR5007EG wifi card and have been trying to install the driver for very long without success because I have never used linux and the instructions are impossible for me to understand.

So I read here at the first post that Ubuntu 8.10 automatically installs the driver. So I tried it yesterday but it didn't work.

In addition, my laptop also lacks the driver for the graphic card and I need to install  the sis672 driver for the resolution to get to 1280x800. It works perfectly in Ubuntu 8.04 but for some reason it doesn't work in Ubuntu 8.10. So, with 8.10 neither of them work.

Could you tell me if the sis672 driver for 8.04 works also in 8.10 and if so, how because the system I learnt is not working anymore? And could you tell me if I have to do something for the atheros ar5007eg to work?

Please simple step by step explanations. This is really difficult for a total beginner.

Thanks

---

### Post by eks on 2008-11-06
> **dummiebeginner said:**
> I have this laptop with this atheros AR5007EG wifi card and have been trying to install the driver for very long without success because I have never used linux and the instructions are impossible for me to understand.

So I read here at the first post that Ubuntu 8.10 automatically installs the driver. So I tried it yesterday but it didn't work. 

Regarding your Sis graphic card, you could try asking the question here: [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)  I really don't know anything about it, I'm just a guy that had some experience making Atheros work on the latest version of Ubuntu and I'm trying to help other people.

If you recently installed 8.10 on this laptop, you can go on System/Administration/Hardware Drivers. This is where Ubuntu lists the hardware drivers in use. You should see an Atheros driver listed, if it's not activated, try activating it. The buttom is on the bottom of the window. After that, reboot.

If that doesn't work, you can go to Synaptic Package Manager (it's listed on System/Administration/). That is the best way to to install and uninstall programs on your Ubuntu, since the management is done entirely by the system. Do a search for "backports", and install the package called *"linux-backports-modules-intrepid"*. After that you should have a new driver listed on the Hardware Drivers window, mentioned on the paragraph above. It's called *"Support for 5xxx series of Atheros 802.11 wireless LAN cards"*. Activate it and reboot.

If neither of this options work, you do indeed need to do something using the command line because there are some residues left from the previous tries you did that are blocking the drivers from working. If think it's too complex, you could consider reinstalling Ubuntu from scratch, or try to learn a bit of the inner workings of Ubuntu.

If you choose the later (which I recommend ;)), just asks which of the steps [listed on the Wiki here]("http://help.ubuntu.com/community/WifiDocs/Driver/Atheros") are confusing and I can try to explain.

---

### Post by dummiebeginner on 2008-11-06
Thanks eks.

I read in other threads that 8.10 doesn't take the sis672 driver anymore, so it is all useless. There are thousands of people with laptops using this bloody SIS graphic card and the only driver around made by a guy named Barros Lee who used to work for SIS, only works in version 8.04 and without 3D.

Do your instructions for atheros ar5007eg work for Ubuntu 8.04? If so, I will try to understand and use them, but it sounds terribly difficult for me.

Thanks again.

---

### Post by dj9928 on 2008-11-07
> **eks said:**
> Try the built-in modules. More information here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Problem is, since you've tried to install the driver manually, you might have to do all the steps mentioned on the first part.

Don't panic, it's not that difficult. Almost everything on Linux are just text files, open and easily accessible. ;)

Well I done that an its still not working, Its not blacklisted anywhere, infact there is nothing that mentions Ath5 or whatever that is, however in the hardware there it is and its activated, its just not working

---

### Post by eks on 2008-11-07
> **dummiebeginner said:**
> Do your instructions for atheros ar5007eg work for Ubuntu 8.04? If so, I will try to understand and use them, but it sounds terribly difficult for me.

No, unfortunately it most probably won't. The ath5k module on the linux-backports-modules-intrepid package is only available for Intrepid. I think, since the name implies it. On 8.04 you will probably have to download and compile manually the driver...

I did that 6 months ago, I'm not sure I can remember but I can try. And there might be other people available to help, since this is still an available way to make it work also on Intrepid.

---

### Post by thor2002ro on 2008-11-08
in terminal:

sudo apt-get install linux-backports-modules-intrepid

go to System -> Administration -> Hardware Drivers and uncheck Atheros wifi(bug led not working and ath_pci doesn't compile on the new kernel)

reboot and works :P

---

### Post by dj9928 on 2008-11-08
Grrr. I have tried Kubuntu 8.10 and still no joy, Its detected ok but there is no sign of it anywhere.

---

### Post by staceyhome on 2008-11-09
Thanks guys, it works on Intrepid or in simple words Ubuntu 8.10 64-bit system. I have installed madwifi HAL October release. Currently I have tested only WEP 128-bit connection, but I will try WPA too. The most pleasing part is the fact I can switch my radio on-off and it still resumes the connection. I have never seen it before on Solaris.

So thanks again.

---

### Post by staceyhome on 2008-11-09
> **dj9928 said:**
> Grrr. I have tried Kubuntu 8.10 and still no joy, Its detected ok but there is no sign of it anywhere.

You are not quite right buddy, see my comment above and in addition don't forget to do this:
 
1) blacklist ndiswrapper in /etc/modprobe.d/blacklist
2) blacklist ath_pci and ath_hal in the same file above
3) deactivate original atheros driver in proprietary drivers list via GUI

That should do the job! Good luck!:guitar:

---

### Post by the_jaguar on 2008-11-09
I have a Dell Mini 9 with Ubuntu 8.10 on it. I am having trouble getting Ubuntu to recognize my Wireless card.
I checked the hardware drivers section in the Administration menu and it lists the Atheros driver as being enabled. But I don't see any wireless networks.
Based on some advice, I installed wicd, but that didn't help either.
When I run "lshw -C network", it lists my Atheros card, but as network UNCLAIMED. How am I supposed to solve this?

EDIT: After further reading, I installed linux-backports-modules-intrepid, disabled the default Atheros wireless drivers, and left the Atheros 5xxx drivers enabled. lshw now lists my Atheros card as "network DISABLED". 

I am not sure if this question has been asked before. If there is a post describing a solution for this problem, I would appreciate it if you can point me in the right direction.

---

### Post by the_jaguar on 2008-11-09
I enabled my wireless card by "ifconfig wlan0 up" and I now have wireless working :)

---

### Post by enigmageek on 2008-11-12
Hello all. I have a Toshiba A205 S5843 laptop with AR5007EG chipset. Using the original instructions of bmartin with the newest ath_hal wireless works perfectly. I recently built the latest 2.6.27 kernel from kernel.org in Hardy cuz I don't want to give up my KDE 3.5.10 yet. I installed DKMS to recompile certain drivers upon kernel updates,madwifi, virtualbox, etc., automatically. I have the dkms.conf file for madwifi_hal and it works great. Just a thought. As far as the ath5k which comes with Intrepid and also the ath9k, it might give some functionality to AR5007EG but it may be spotty. The Madwifi guys said this chipset isn't fully supported, yet. Good luck and thank you bmartin for your excellent post.If anyone wants, I can post the dkms conf and commands to add, build, etc. Also I use scripts to reset networking, set link speed, etc. after resume from suspend.
Regards,
Ray
Ubuntu Hardy 8.0.4.1- 2.6.27.5
Windows Vista and XP via VirtualBox ;)

---

### Post by dummiebeginner on 2008-11-16
Thanks to all for your help.

I never managed to make it work, but I finally found, after months of despair, that Mandriva One 2009 works prefectly in my bl**dy laptop.

So, if anyone is desperate as I was trying to have Linux in these Linux incompatible Fujitsu-Siemens Esprimo Mobile V5535 with problems in the SIS Mirage 3 graphic card (sis 671/672 driver) and the Atheros AR5007EG wifi, this is an alternative that works. Just install, connect the wifi by the password and ready to use. Neither graphic problems (1280x800 resolution) nor wifi.

Thanks to all of you again. I managed to have Linux finally, after months of trying things.

---

### Post by Perpetual on 2008-11-17
> **dummiebeginner said:**
> Thanks to all for your help.

I never managed to make it work, but I finally found, after months of despair, that Mandriva One 2009 works prefectly in my bl**dy laptop.

So, if anyone is desperate as I was trying to have Linux in these Linux incompatible Fujitsu-Siemens Esprimo Mobile V5535 with problems in the SIS Mirage 3 graphic card (sis 671/672 driver) and the Atheros AR5007EG wifi, this is an alternative that works. Just install, connect the wifi by the password and ready to use. Neither graphic problems (1280x800 resolution) nor wifi.

Thanks to all of you again. I managed to have Linux finally, after months of trying things.

I just gave a copy of Mandriva 2009 to a co-worker that has never touched Linux.  It works really well...right out of the box.

---

### Post by Wosscoe on 2008-11-28
Hi Bmartin,

i used you advise and it worked, so i linked this forum page to the kubuntuforums.net posting i submitted. hope you dont mind, i gave you full credit,,,,, just spreading the work 

your thingy here helped me heaps,,,,,,,:guitar:

---

### Post by brandonostler99 on 2008-12-03
i'm done with ubuntu, i was running dual boot, i'm not a  programmer and will never be one, i was under the impression that it was better than windows, i have tried to figure out all of this talk on here but it isn't in any kind of speech that the "computer illiterate" can understand, thanks but no thanks i'll  stick with windows, i may regret it but i can at least understand what i'm doing on windows.

---

### Post by gluefish on 2008-12-03
> **thor2002ro said:**
> in terminal:

sudo apt-get install linux-backports-modules-intrepid

go to System -> Administration -> Hardware Drivers and uncheck Atheros wifi(bug led not working and ath_pci doesn't compile on the new kernel)

reboot and works :P

Thanks! Worked for me.  
:popcorn: Took me forever to find this message, though; I request that you copy it up to the #1 message.

---

### Post by ntlam on 2008-12-22
Hello

I have a problem installing madwifi:

make
cd: 1: can't cd to /lib/modules/2.6.22-14-generic/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-generic/build is missing, please set KERNELPATH.  Stop.

Anyone gives me some hints please.

Lam

---

### Post by ntlam on 2008-12-22
Never mind. I updated new kernel but kept on logging on to old one so that's the problem.

---

### Post by ShadowXRougeXEver on 2009-01-12
Oh thankyou soo much for this information!
I've been trying to get wireless on Ubuntu for ages and your post got me working instantly!
As proof, I'm posting this using the wireless!
Thanks :)

---

### Post by scaldwellk on 2009-01-12
I will need to try this.

---

### Post by kevdog on 2009-01-12
Has this method been replaced by simply adding the linux-backport-modules which installs the ath5k driver?

---

### Post by thor2002ro on 2009-01-12
yep

---

### Post by kevdog on 2009-01-12
So the original post should be modified.  Meaning keep this way as a backup or secondary method, and add the repository way with ath5k driver as the primary method -- since this method IMO is much easier and it uses an open source HAL layer as opposed to traditional madwifi.

---

### Post by waj1122 on 2009-01-28
I just want to say "Thank You" for this thread. I was using madwifi to run the wireless AR5007EG on my laptop. This is so much easier (I used the wiki instructions).

Bill

---

### Post by CheezRulz on 2009-01-31
Dude, you are my hero!!! I joined this website and put you as my referer. I have been trying many different things for 3 days and this is the only thing that worked. Thanks! :D:D:D

---

### Post by Turiko on 2009-02-22
Odd... i have never gotten wifi to work in ubuntu, and now with ibex it hasn't changed. Does anyone know where to get the drivers so i can transport them over onto my ubuntu pc with a usb stick and give me the commands required to install it from there? Most people that use a non-working wifi can't connect to the internet ;).

---

### Post by bmartin on 2009-02-22
> **Turiko said:**
> Does anyone know where to get the drivers so i can transport them over onto my ubuntu pc with a usb stick and give me the commands required to install it from there? Most people that use a non-working wifi can't connect to the internet ;).
They should be in the packages shown [here](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.27/).

You need the package for your kernel and architecture. You can obtain these by running **uname -r -m**. For example, that outputs **2.6.27-9-generic i686**, so I'd grab **linux-backports-modules-2.6.27-9-generic_2.6.27-9.5_i386.deb**, since I have kernel 2.6.27-9 and a 32-bit OS (if you have a 64-bit OS, it'll output x64 or something like that).

Next, you need to install the package on your Ubuntu computer using the following commands (assuming you copied the file to your desktop):
```
cd ~/Desktop
sudo aptitude install linux-backports-modules-2.6.27-9-generic_2.6.27-9.5_i386.deb
```

You should then run the following command to make sure the ath5k driver loads up by default:
```
echo "ath5k" | sudo tee -a /etc/modules
```

Then, you'll probably want to blacklist the other Atheros driver, so it doesn't load up and cause a conflict:
```
echo "ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Finally, you'll want to edit the blacklist file by hand and make sure that ath5k **is not** listed in there. You'll have to edit the file as an admin, using the following command:
```
sudo gedit /etc/modprobe.d/blacklist
```

---

### Post by b3ta on 2009-02-24
> **bmartin said:**
> They should be in the packages shown [here](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.27/).

You need the package for your kernel and architecture. You can obtain these by running **uname -r -m**. For example, that outputs **2.6.27-9-generic i686**, so I'd grab **linux-backports-modules-2.6.27-9-generic_2.6.27-9.5_i386.deb**, since I have kernel 2.6.27-9 and a 32-bit OS (if you have a 64-bit OS, it'll output x64 or something like that).

Next, you need to install the package on your Ubuntu computer using the following commands (assuming you copied the file to your desktop):
```
cd ~/Desktop
sudo aptitude install linux-backports-modules-2.6.27-9-generic_2.6.27-9.5_i386.deb
```

You should then run the following command to make sure the ath5k driver loads up by default:
```
echo "ath5k" | sudo tee -a /etc/modules
```

Then, you'll probably want to blacklist the other Atheros driver, so it doesn't load up and cause a conflict:
```
echo "ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Finally, you'll want to edit the blacklist file by hand and make sure that ath5k **is not** listed in there. You'll have to edit the file as an admin, using the following command:
```
sudo gedit /etc/modules
```

On the last step, do you mean the file /etc/modprobe.d/blacklist ? ;)

Anyways, did these steps and still not working. Can't find ath5k under modprobe either.

Edit: Is it just me or is the ath5k module impossible to find? :O Have enabled backports as the wiki says, but i just can't find the module ath5k.

---

### Post by bmartin on 2009-02-24
> **b3ta said:**
> On the last step, do you mean the file /etc/modprobe.d/blacklist ? ;)
Indeed I did. I updated my post, in case anyone's following along.

> **b3ta said:**
> Edit: Is it just me or is the ath5k module impossible to find? :O Have enabled backports as the wiki says, but i just can't find the module ath5k.
Try looking under System > Administration > Hardware Drivers. The Atheros driver isn't listed under there?

---

### Post by b3ta on 2009-02-24
> **bmartin said:**
> Indeed I did. I updated my post, in case anyone's following along.


Try looking under System > Administration > Hardware Drivers. The Atheros driver isn't listed under there?

It is listed there, "Support for Atheros 802.11 wireless LAN cards."

...

"This driver is activated and currently in use."

But no, it is not working. :(

---

### Post by mplinux on 2009-03-13
**SOLVED!!!**
Here is what I did per bmartin and other threads tips. 

Prereq:
I had a Clean install of Ubuntu 8.10.

1ST STEP:
Installed NDIS wrapper from Synaptic Package Wrapper(Search for NDISGTK) or Add/Remove Applications (search for ndis) **Because I'm not to familiar with terminal I preferred to download the 
NDIS wrapper Interface**

2ND STEP:
Downloaded the appropriate driver for my 64-bit driver. If you have  32-bit just make sure to download that driver. I grabbed the link from this [**THREAD**]("http://ubuntuforums.org/showthread.php?t=512828")
Click [ here ]("http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz").for 64 bit. 
Click [here]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz").for 32 bit. 
- Opened downloaded File on Desktop --> Extracted files to my home folder.

4TH STEP:
Open NDIS wrapper that I installed earlier by going to SYSTEM>ADMINISTRATION>WINDOWS WIRELESS DRIVERS. 
- SELECTED +Install New Driver
- Located net5211.inf file by going to Ar5007eg folder -->ar5007eg-->net5211.inf
- Select Install

3rd STEP
Go to SYSTEM> ADMINISTRATION> HARDWARE DRIVERS
Deactivate "Support for Atheros 802.11 wireless LAN cards."

4TH STEP
Rebooted and my Wireless Card is now WORKING!! 

**The only problem I had was that Network Manager did not want to accept my password for my router for some reason. I knew it was correct...I decided to try out WICD network manager. Quote:"Wicd is an open source wired and wireless network manager for Linux which aims to provide a simple interface to connect to networks with a wide variety of settings"

5TH
I went to [WICD]("http://wicd.sourceforge.net/download.php") web page.

This is the instructions to download and set up WICD on their website. 

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, **intrepid**).**MAKE SURE YOU REPLACE hardy with intrepid**. You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.


6TH STEP:
REBOOTED Selected my network from WICD tray Icon. Selected network...selected WPA2 for my security settings/set password... and it was like MAGIC!! now I have a fully functional connection!!!

I hope this helps!!! There is hope out there for those of us using the darn Atheros AR5007EG cards!

---

### Post by tedvip on 2009-04-20
Hi all, I had done all bmartin told us to do, but still failed.
The output of lsmod and iwlist scan was
> 
debian:/home/shibaolin# lsmod |grep ath
ath_pci 203800 0
wlan 192368 1 ath_pci
ath_hal 300704 1 ath_pci
ath5k 87264 0
mac80211 139680 1 ath5k
cfg80211 21576 2 ath5k,mac80211

debian:/home/shibaolin# iwlist wlan0 scan
wlan0 Interface doesn't support scanning : Network is down 


The output of lspci was
> 
...
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
...


I post this thread in windows, so I need some help, thanks in advance.

---

### Post by bmartin on 2009-04-20
> **tedvip said:**
> Hi all, I had done all bmartin told us to do, but still failed.
The output of lsmod and iwlist scan was [snip]
I've removed the obsolete instructions from the first post. Please use the wiki page instead.

---

