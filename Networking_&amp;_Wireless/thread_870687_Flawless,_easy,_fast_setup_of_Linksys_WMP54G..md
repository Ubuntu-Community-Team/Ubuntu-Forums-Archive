---
title: "Flawless, easy, fast setup of Linksys WMP54G."
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2008-07-26
I had the Linksys WUSB54GC wireless adapter. It worked fine for me until about 2 weeks ago. I don't know if the adapter went bad or if I glitched my system.

Anyway, I went out today to buy the Netgear WG311T. Contrary to what the websites for the local computer supply shops say, no one carries it.

So, I decided on the Linksys WMP54G. There are 2 differant ones, both called WMP54G. The one I wanted cost $54 and is called a network adapter. This one was not in stock. The other one is called a PCI adapter and cost $39. The $54 one is a super fast model of the $39 one. I don't know why one is called a network adapter and one is called a pci adapter. I had to settle for the $39 one.

I plugged it into my PCI slot and booted up. I then went to system>administration>network. I enter the ESSID (network name) and the network password. The system immediately went on line and my web pages load almost instantly every time.

If this continues to function properly I am going to try to locate the $54 card and try it out to see if it really is faster.

By the way, I ended up buying the Linksys WMP54G pci adapter at Office Depot. I also want to add that on the card itself, it says that this is version 4.1, which this website... [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) ...says is supported but 'does not work out of the box'. 

Great product as far as I can see and it appears to have been made with Ubuntu Hardy in mind.

---

### Post by sputnikkk on 2008-07-26
Have you rebooted with it yet?

Seems like most of the time all is well, until reboot ...  then NetworkMisManager munges the WPA and passkey seetings - so you need to re enter them, good to go until the next boot.

Mine is also defaulting to 1Mbps setting

out of curiosity - what does the result of iwconfig at the command line on your install look like?

Glad your rockin!

---

### Post by sofasurfer on 2008-07-26
CRAP!! You're right. I need to re-enter my encryption key after every reboot. HOWEVER, don't dispare. 

This is the exact same problem I had with my Linksys WUSB54GC, and I was able to solve it. The /etc/network/interfaces file needs to be edited. However, I will need time to figure it out again. But the help I needed came from this thread... [http://ubuntuforums.org/showthread.php?t=731361](http://ubuntuforums.org/showthread.php?t=731361)

I found the solution in post #22. Post #21 shows my original file. Post #22 shows how it needed to be changed.

Remember, this was for Linksys WUSB54GC, not WMP54G.

But I am confidant that the answer IS in that thread. Right now though, I have to go to bed. I'll try to work on this tomorrow.

EDIT::
I didn't make it to bed. I decided to try to fix this thing and surprise, surprise, I did it... I think.

Here is my new /etc/network/interfaces file...

```

auto lo
iface lo inet loopback
auto wlan1
iface wlan1 inet dhcp
pre-up sleep 20 


wpa-psk ca66ab13e787c36828640db42ccd7bfe2ead7b99ee845a3e7e5507fa71d44788
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid belkin

```

You should first save a copy of your /interfaces file as it is right now.
Next, create a new file containing the first 5 lines shown above. Note that you may have to change the references to 'wlan' to reflect what is shown in your present file... you may need to use 'wlan0' or 'wlan1' or what ever is in your present file. The secong group of 5 lines is what will be added to the file by your computer after you edit your settings in system>administration>network.

This is all I can tell you right now. I hope someone else confirms this info before you take my word for it. But I will tell you that this information was learned from the above mentioned thread and my internet adapter now appears to be working perfectly.

---

### Post by sofasurfer on 2008-07-26
P.S.
You asked for my iwconfig output. Here it is.

```

daryl@linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"belkin"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:F1:1A:2C   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=74/100  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by charonred on 2008-10-12
I was having similar problems and this solution/work-around seems to have fixed my 'Hardy' wireless connection & password/key problems so that my network is detected and connected, and keeps working even after re-booting.

NOTE: I wouldn't remove 'Network Manager' as that may kill your ethernet connection (it may not, but it has on one PC).

My laptop which runs Hardy, but with the KDE instead of Gnome, gave me a hint on how to get wireless working - it connects fine as it uses 'kwifi' and not 'Network Manager'.

As I use Gnome on my other PCs I went looking for something similar.

I used Synaptic to install 'wifi-radar' - I then put in the relevant settings into it and presto, I have wireless networking; and then I rebooted, and yep I still had wireless - after several reboots I still had wireless, so I recommend using 'wifi-radar' instead of Gnome's sometimes buggy 'Network Manager' 

(note: I'm using WEP, but I think it'll still work with WPA)

---

