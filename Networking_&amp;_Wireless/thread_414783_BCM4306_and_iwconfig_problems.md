---
title: "BCM4306 and iwconfig problems"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by crazy_cat on 2007-04-20
ok, i've been running ubuntu for about 4 days and just installed fiesty.  i have a laptop with a BCM4306 wireless card.  i've followed the [HOWTO]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-fe1ec89e4caea9768f41bf6c7bd9c52d29dbec9d") to no avail.  

basically, i can view my wireless network, but i cant connect.  follow the instructions, i reverted to a WEP key on my access point and used that key at first, on my windows and my mac, i was using WPA2. but i couldnt connect with the WEP key.  "iwlist scan" showed the wireless network, but not "iwconfig." 

then i totally disabled the security on the wireless to test if i could access it that way (after deleting the key from the network manager.  now i can at least see the wireless network.  

just ,fyi, ive really tried to search thru the forums and online for an answer, and i appreciate any help...

---

### Post by crazy_cat on 2007-04-20
sorry for the double post.  with WEP and WPA disabled from the router side, i can run "dhclient wlan0" and connect wirelessly.  but i cant connect via network manager (GUI).  if i try and connect with the manager, i cant even ping my router.  but i can run "iwconfig" and this:

IEEE 802.11g  ESSID:"DALLAS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
(that's without a network key, connecting via network manager in gnome, and running iwconfig)

i dont like leaving my wireless connection unsure.  

i'm not familiar enough with this system to trace down the problem that would allow "dhclient" to connect but not the network manager.

---

### Post by crazy_cat on 2007-04-21
i've found several other treads with similar problems...it seems to be systemic.

---

### Post by nightofnih on 2007-04-23
I have been using Ubuntu since 6.10 and the combination of ndiswrapper/wpa_supplicant/netwrok-manager worked pretty well for me - but after I installed feisty I have been having problem just like you are describing. BTW, I have the exact same wireless chipset like yours (BCM4306). I can see all the networks through network-manager - it even tells if they are protected or not and what signal strength they are but connecting to any of the WPA/WPA2 protected networks never works. The network-manager animated icons just spins and spins and none of the two blobs goes green. The funny thing is that I can see my neighbors unprotected network and it connects to it just fine - I don't want to do that really. From what I have learned so far is that this problem is in the newest network-manager so I am trying to use an alternative to network manager - its called "WPA Gui". I will post here if I get lucky with that.

---

### Post by rko618 on 2007-04-24
I am having the same problem.  The bcm4306 worked 'ok' in Edgy but no luck with the same method in Fiesty :(.  Anyone get a fix for this?

---

### Post by rko618 on 2007-04-24
Sweet! I got my wifi working!  Here is what I did

Followed this howto: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

I used the ndiswrapper method instead of the native bcm43xx driver.  I couldn't get the bcm43xx driver to work.  But I was probably just doing something wrong.  So I followed the ndiswrapper method.  There are a lot of little things that you can mess up on so be careful.


I hate networking issues but damn does it feel good when it works.

---

