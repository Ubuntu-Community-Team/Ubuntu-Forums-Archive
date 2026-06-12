---
title: "Belkin F5D7000"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by MacUsr on 2006-11-02
I have a Belkin F5D7000 wireless adapter. It works after I first install, then when restart, it doesn't. I think I saw something here that showed how to edit a file so that something in the startup process changes. I'm a Linux nwebie and any directions will have to be specific.

---

### Post by MacUsr on 2006-11-03
no one can help?

---

### Post by MacUsr on 2006-11-03
please! I want to get this fixed :(

---

### Post by TiredBird on 2006-11-05
Take a look at [this 'howto post']("http://www.ubuntuforums.org/showpost.php?p=1707809&postcount=1") and see if it gets you there.

---

### Post by frank05 on 2006-11-05
I may have the same card as you. It took a bit of jiggling around with network manager to get it to work but I eventually managed it. My network setup is fairly simple however. 
Are you on an encrypted network or is the essid of your access point hidden? what's the output of iwconfig when its not working?

edit: actually, i may not have the same card. belkin, being so clever use the same product number for two cards with entirely different chipsets. mine uses the ralink chipset, but others use broadcom. In the case of broadcom, your best bet is to use ndiswrapper. There are however open source drives for the ralink (aka rt2500 drivers). check the output of lspci to see which one you have.

---

### Post by TiredBird on 2006-11-05
I am using WEP and yes I hid both the essid and the encryption code.

I'm afraid I don't really know very much, that's why I documented my efforts when I finally got it working. I was hoping it might save someone else the hours and hours of trial and error that it took me to finally make it work. 

I'm embarrassed to say that I don't have any idea what 'iwconfig' is. If it's something I should be using please let me know.

---

### Post by TiredBird on 2006-11-05
I've been doing a little research on 'iwconfig' since my last post and I can provide this much info.

When run from my Xubuntu installation I get the following:

wlan0     IEEE 802.11b  ESSID:"***********"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:57:BD:90:21:59
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management: off
          Link Quality:100/100  Signal level:-42 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Note: Again I have wiped out the ESSID. I also changed the mac address on the Access Point. When I have an 'iwconfig' from the Ubuntu installation, I'll post that too. Should be a couple of minutes.

---

### Post by TiredBird on 2006-11-05
Okay, here it is from Ubuntu 6.06:

wlan0     IEEE 802.11b  ESSID:"**********"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:57:BD:90:21:59
          Bit Rate:54 Mb/s   Tx-Power:14 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management: off
          Link Quality:100/100  Signal level:-35 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I guess I shouldn't be surprised that they are remarkably similar since I used the same directions on both installations.

Since I have just discovered 'iwconfig', thanks to you, I would be happy to have any advice you might wish to offer. Also, I'll try to help you in any way I can with my limited knowledge.

---

### Post by frank05 on 2006-11-05
Sorry TiredBird my post was mostly directed MacUsr (maybe I should have been clearer), I wondered if his card was correctly resolving his access point id which is why I enquired about the iwconifg output. I also wanted to point out that his card may not be the same chipset as your own.

Basically, alot of what network-admin does with wlan cards is actually done through iwconfig. Thankfully I haven't had to use many features of iwconfig yet. The most difficult setup I had to do was with a broadcom nic like yours. In that case however I was using WPA encryption and so most of the configuration was done through wpa_supplicant and not through iwconfig.

---

