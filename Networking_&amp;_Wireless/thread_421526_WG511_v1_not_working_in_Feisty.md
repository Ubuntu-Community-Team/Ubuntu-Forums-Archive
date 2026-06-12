---
title: "WG511 v1 not working in Feisty"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by gracedman on 2007-04-24
I am running Feisty for AMD64 with a netgear WG511 wireless PCMCIA card.  This is the old style which uses the Prism54 driver and the isl3890 firmware.

The drivers load and the card appears fine (link light is solid) but it does not associate with the wireless access point.  It almost seems as if it is not taking the essid (it is hidden by the AP).  The essid shows up in iwconfig but, if I look in KWiFiManager, it does not.  My WAG511 (atheros chipset) works fine.

How do I begin troubleshooting this issue? Thanks - John

---

### Post by bnuytten on 2007-04-24
Try to associate the network card with the access point. Either use /etc/network/interfaces or iwconfig to do your thing. Check /var/log/messages for errors... If you want to search for wireless networks iwlist wlan0 scanning.

Maybe have quick look at [this page]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting?highlight=%28wifi%29") or other pages on the [Ubuntu wiki]("https://wiki.ubuntu.com/")

---

### Post by gracedman on 2007-04-24
Thanks for the quick reply.  Unfortunately, it doesn't seem to help.  For example, if I do an ifdown and then ifup, this shows up is messages:

Apr 24 17:28:24 jaspav kernel: [12394.763073] pccard: CardBus card inserted into slot 0
Apr 24 17:28:24 jaspav kernel: [12394.763307] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
Apr 24 17:28:24 jaspav kernel: [12394.763315] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 20 (level, low) -> IRQ 20
Apr 24 17:28:25 jaspav kernel: [12395.196990] p54: LM86 firmware
Apr 24 17:28:26 jaspav kernel: [12396.025570] wiphy4: hwaddr 00:09:5b:83:50:29, isl3890

All seems fine, all looks fine.

When I do iwconfig eth1:

eth1      IEEE 802.11g  ESSID:"CanYouSpellAloysius"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

All looks good except for the Not-Associated message.

Strangely, if I then do an sudo iwlist eth1 scanning, I get:

eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:A0:8E:00
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz
                    Signal level=63/100
                    Encryption key:off
                    Extra:tsf=000000a963868181

Notice the difference in the ESSID and the Mode.

If I try to change the mode with sudo iwconfig eth1 mode managed, I get:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Device or resource busy.

Where do I go from here? Thanks - John

---

### Post by chili555 on 2007-04-24
The mode on the interface is *already* managed. You want it to be 'managed' because you want the access point (master) to dictate the channel, rate, etc. and the WG511 to follow orders. No need to command eth1 to what it already is.

I think your only problem is the hidden ESSID. I suggest:```
sudo iwconfig eth1 essid ""
sudo dhclient eth1
```If that doesn't work, I have read Wicd associates with hidden ESSID's. [http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/) The site is currently down; I imagine so many Ubuntu-ans want it, they have crashed the server...again.

---

### Post by gracedman on 2007-04-24
Thanks very much again.  I probably was not clear enough on the situation.  The ESSID is hidden and the one in the iwconfig output is correct.  The strange thing is that it does not show up as the ESSID when the AP is scanned with iwlist nor does it show up in KWiFiManager.

I did misinterpret the mode in iwlist - I now see that is the mode of the AP and not the card.  However, something seems wrong in that I cannot change the mode of the card.  For example, if I try to put it in monitor mode, I get the same resource busy error.

I did using iwconfig to set the ESSID to "" and then set it back to the hidden value but that did not work,  The IP address is statically assigned so there is no need for dhclient.

What should I try next? Thanks - John

---

### Post by chili555 on 2007-04-24
I guess I don't understand. You say the ESSID is hidden which is confirmed in scanning:> eth1 Scan completed :
Cell 01 - Address: 00:14:6C:A0:8E:00
ESSID:""But then you say:> the one in the iwconfig output is correctHowever, iwconfig says:> eth1 IEEE 802.11g ESSID:"CanYouSpellAloysius"So how, exactly is "" the same as "CanYouSpellAloysius"?> something seems wrong in that I cannot change the mode of the cardNot every card does every thing. You can find out what is available with:```
sudo iwpriv eth1
```Here is mine, for example:```
eth1      Available private ioctls :
          set_power        (8BE0) : set   1 int   & get   0      
          get_power        (8BE1) : set   0       & get  80 char 
          set_mode         (8BE2) : set   1 int   & get   0      
          get_mode         (8BE3) : set   0       & get  80 char 
          set_preamble     (8BE4) : set   1 int   & get   0      
          get_preamble     (8BE5) : set   0       & get  16 char 
          reset            (8BE7) : set   0 int   & get   0      
          monitor          (8BE6) : set   2 int   & get   0 
```As you can see, my card does do monitor mode.

---

### Post by hiddensphinx on 2007-04-24
my Netgear WG511U detects the network ID but "sees" a WPA signal as a WEP signal and offers me no other choice :(

---

### Post by gracedman on 2007-04-24
Thank you, Chili.  Perhaps I've remembered incorrectly but, when one does specify a hidden ESSID and then scans, doesn't the ESSID show up in the iwlist scanning output rather than ""? I thought "" only showed up in the ESSID was hidden and the card did not know the ESSID.

Thus, I would have expected the ESSID returned by iwconfig to match that of iwlist since I configured the card to use the hidden ESSID.  I was pointing out that they are different and I expected them to be the same.

I'm also a bit taken aback by the inability to change the mode.  I have used this card in monitor mode before under Fedora Core 3.  I was using Kismet and AirSnort at the time to do some security work.  If I do a sudo iwpriv eth1, I only get:

eth1      Available private ioctls :
          param            (8BE0) : set   2 int   & get   0
          get_param        (8BE1) : set   1 int   & get   1 int
          test_param       (8BE4) : set   2 int   & get   0

Thanks - John

---

### Post by stchman on 2007-04-25
> **gracedman said:**
> I am running Feisty for AMD64 with a netgear WG511 wireless PCMCIA card.  This is the old style which uses the Prism54 driver and the isl3890 firmware.

The drivers load and the card appears fine (link light is solid) but it does not associate with the wireless access point.  It almost seems as if it is not taking the essid (it is hidden by the AP).  The essid shows up in iwconfig but, if I look in KWiFiManager, it does not.  My WAG511 (atheros chipset) works fine.

How do I begin troubleshooting this issue? Thanks - John

Try installing the madwifi drivers using my procedure:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It worked on my Atheros card.

---

### Post by gracedman on 2007-04-25
Thanks, Stchman.  I do have a WAG511 which uses an Atheros chipset and that works fine with the madwifi drivers.  Alas, this WG511 uses a prism chipset and the prism54 drivers.  I can't imagine that the madwifi drivers will work for a non-Atheros chipset - John

---

### Post by tl3000 on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/105357](https://bugs.launchpad.net/bugs/105357) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **gracedman said:**
> Thanks, Stchman.  I do have a WAG511 which uses an Atheros chipset and that works fine with the madwifi drivers.  Alas, this WG511 uses a prism chipset and the prism54 drivers.  I can't imagine that the madwifi drivers will work for a non-Atheros chipset - John


See related bug report and add your inputs.

---

### Post by gracedman on 2007-04-27
Thanks tl - John

---

### Post by tl3000 on 2007-04-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You're welcome!  However, I was finally able to get my WG511v1 working with a temporary solution.  See related bug report... FYI.



[EDIT - Update]  I think there may be other issues with the native prism54 drivers besides the WPA problem with Network Manager. After some more extended uses and rudimentary testing, I noticed that the wireless connection's performance is severely degraded. The data throughput rate is about a quarter of what its maximum capability used to be under Edgy, and it fluctuates wildly. It now takes about 4 times longer than before with Edgy to transfer a ~1GB file between two PCs on the LAN. I also noticed that the network activities LED (amber) on the WG511v1 flashes constantly even when the wireless connection should be at idle. Normally, this LED stays dark-not flashing dimly and rapidly--and doesn't light until there's traffic activities. I suspect that the drivers may be issuing extraneous packets and tying up the bandwidth for actual data transfers. I'm no network expert so I'm unable to sniff and check for those suspected packets. I'm uncertain but I also believe that the wireless connection and bit transfer rate is unaffected and is operating at its 802.11g peak rate of 54Mbps--even with all the detected network signal levels being degraded too. Again, I think there may be other issues with the native drivers too...

---

### Post by gracedman on 2007-04-28
Thanks again. Alas, I have another wireless card that uses WPA so I guess I'm stuck until they fix Network Manager.  At least I know I'm not out of my mind :)  - John

---

### Post by gt24 on 2007-04-28
The bug reports mentioned above (well, 105858 in paticular) allowed my Netgear WG511 v1 card to work properly with a WPA network.  I was extremely frustrated that nothing allowed this card to work... that was until I ran into this thread.

Network manager can be disabled by going to System > Preferences > Sessions and unchecking Network Manager.

Wifi radar can be used at this point to manage wireless, although in a less elegant fashion.  The benefit of this is that the Network Manager need not be uninstalled, just disabled as indicated above.  A wpa_supplicant.conf file needs to be created in /etc/wpa_supplicant/ and wrote appropriately...

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=admin

network={
      ssid="YourSSID"
      scan_ssid=1
      key_mgmt=WPA-PSK
      psk="YourKeyGoesHere"
}
```

Also, /etc/wifi-radar.conf needs modified near the top to point to the right interface (either wmaster0 or wlan0).  The Wifi Radar interface can be launched and for the WPA driver, you should type in wext.

Other than that, now wireless works!!  :)

---

### Post by GNUoob on 2007-05-03
i read as much of the post as i could but im not seeing any answers. all i see is an error reporting. Am i missing a solution somewhere?

i have a wg511 v1 as well and am running Kub-feisty as well.

---

### Post by bnuytten on 2007-05-03
> **GNUoob said:**
> i read as much of the post as i could but im not seeing any answers. all i see is an error reporting. Am i missing a solution somewhere?

i have a wg511 v1 as well and am running Kub-feisty as well.

Isn't the answer to be found on this url?

> **tl3000 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858) [br].[/br] ----------------------------
You're welcome!  However, I was finally able to get my WG511v1 working with a temporary solution.  See related bug report... FYI.


---

### Post by chili555 on 2007-05-03
> I think there may be other issues with the native prism54 drivers besides the WPA problemI agree. I used to have one of these and the little yellow LED would start blinking so much it glowed solid! A look in /var/log/messages showed multiple instances of something about, if I remember correctly, 'tx_queue,' or similar. This is not Ubuntu related, since I had this problems with Fedora Core 5 and 6 as well as Ubuntu. 

In desperation, as a last step before I adjusted it's attitude with an ice-pick, I installed ndiswrapper via Synaptic, grabbed the XP driver from Netgear's site and installed it. It works perfectly! I never tried WPA, but I'd assume it would work.

---

### Post by tl3000 on 2007-05-03
There are definite problems and issues with the native prism54 drivers used in Fiesty for the WG511v1 besides the WPA bug in Network Manager.  With the native drivers, the WG511v1 seems to be forced into the 802.11b mode--which was what Wifi-radar was revealing.  Somehow, the card was still able to connect with my 802.11g-only network which is very strange... I've no clue what's going on here.  This might explain the rapid and constant flashing of the activities LED, degraded performance, slower throughput, and weaker signal strengths.

Another observation, Network Manager in Fiesty is defintely broken, and it seems to be unable to handle and use keys properly with the keyring modules.

I was finally able to get NDISwrapper working with the WG511v1's Windows 2K driver (netwg511.inf) on Fiesty and connect to an 802.11g network with WPA--as I had with Edgy--over the weekend.  I've been testing the wireless connection in the last several days, and it seems to be working much better now but it still has one issue.  The wireless connection seems to be unable to automatically renew IP leases to stay connected--as before with Edgy.  When the IP lease expires, the Internet and LAN connections are gone, and I need to manually reconnect via WICD even though it still reports that its wirelessly connected.

Steps taken to enable an 802.11g WPA wireless connection via WG511v1 on Ubuntu Fiesty:
[probably not the most efficient or proper approach but it worked for me]

-- Completely remove Network Manager (network-manager & network-manager-gnome packages)
    via Synaptic Package Manager
[I tried disabling the Network Manager session as suggested in a previous post but I found that there were still some conflicts and this procedure did not work for me until I completely removed Network Manager.]

-- Install NDISwrapper (ndiswrapper-utils-1.9 & ndiswrapper-common packages)
    via Synaptic Package Manager

-- Disable the native Prism54 drivers:

sudo modprobe -r prism54pci
sudo modprobe -r prism54common
sudo gedit /etc/modprobe.d/blacklist

add the following 2 lines to the end and save:

blacklist prism54pci
blacklist prism54common

-- Install the WG511v1 Windows 2K driver:
[download or copy the netwg511.inf & WG511ICB.sys files to the Home Folder]

sudo ndiswrapper-1.9 -i netwg511.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo gedit /etc/modules

add the following line to the end and save:

ndiswrapper

-- Download WICD [version 1.2.6] from:
    [http://ubuntuforums.org/attachment.php?attachmentid=30324&d=1177142011](http://ubuntuforums.org/attachment.php?attachmentid=30324&d=1177142011)

[EDIT - update] for latest version:
   can be found at their new [official website]("http://wicd.sourceforge.net/").
   [Version 1.2.7 is more Fiesty-friendly.  The random loss of Internet & LAN connections
   mentioned above disappeared with this latest version.  Wireless is fully working now.]

    and install [which also installs & uses wapsupplicant automatically]

-- Configure WICD accordingly with the necessary network parameters.

-- In order to get this to work for me, I had to:

Click on Preferences
Select 'wext' for the WPA Supplicant Driver & click OK
Repeat, and switch to the 'ndiswrapper' selection
then finally repeat, and switch back to 'wext' selection

Restart system, and wireless connection should work now.

---

### Post by MeeMaw on 2007-05-03
> **chili555 said:**
> I agree. I used to have one of these and the little yellow LED would start blinking so much it glowed solid! A look in /var/log/messages showed multiple instances of something about, if I remember correctly, 'tx_queue,' or similar. This is not Ubuntu related, since I had this problems with Fedora Core 5 and 6 as well as Ubuntu. 

In desperation, as a last step before I adjusted it's attitude with an ice-pick, I installed ndiswrapper via Synaptic, grabbed the XP driver from Netgear's site and installed it. It works perfectly! I never tried WPA, but I'd assume it would work.

And it does work - I have the exact card chili is talking about - it works with ndiswrapper- and I'm using WEP at the moment, but it does support WPA - doing sudo iwlist wlan0 key I get
wlan0     2 key sizes : 40, 104bits
          4 keys available :
                [1]: xxxx-xxxx-xx (40 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:restricted
          Authentication capabilities :
                WPA
                CIPHER TKIP
                CIPHER CCMP
          Current key_mgmt:0x0
          Current cipher_pairwise:0x0
          Current cipher_group:0x0

Don't give up!!!!    :)

---

### Post by Chonnawonga on 2007-05-03
tl3000, thank you from the bottom of my heart.

Thank you, thank you, thank you.

I've been wrestling with this for days, and had literally booted up the affected computer with an Edgy CD to downgrade when I checked the forums one more time, and found your post. Eureka. It works.

That's a really funny bit at the end, what with changing the settings back and forth on Wicd. Do you know what that does?

Oh, and one other thing: I should point out that it's necessary to have all the Win2000 driver files in the home directory, not just the .inf file. Or so it seemed to me.

Again... thank you. You saved me a very painful downgrade.

---

### Post by tl3000 on 2007-05-03
> **Chonnawonga said:**
> tl3000, thank you from the bottom of my heart.

Thank you, thank you, thank you.

I've been wrestling with this for days, and had literally booted up the affected computer with an Edgy CD to downgrade when I checked the forums one more time, and found your post. Eureka. It works.

That's a really funny bit at the end, what with changing the settings back and forth on Wicd. Do you know what that does?

Oh, and one other thing: I should point out that it's necessary to have all the Win2000 driver files in the home directory, not just the .inf file. Or so it seemed to me.

Again... thank you. You saved me a very painful downgrade.

You're very welcome!  I wrestled with this problem for a few weeks now--ever since upgrading to Fiesty.  I almost gave up too...  Anyway, glad that the fix also worked for you too.

As to the odd switching procedure, I have no idea... only that it might be a programming error in WICD, and that switching the selection causes the proper settings to take effect somehow.  Your guess is as good as mine.

You're right, I did leave out one other necessary Windows driver file (WG511ICB.sys) in the Home Folder.  Thanks for catching it.

---

### Post by waelas on 2007-05-07
@tl3000: thanks a lot, it worked for me, too. (Netgear WG511v1, kubuntu)

Because I'm using Kubuntu, I don't have to use wicd, though...

---

### Post by tl3000 on 2007-05-07
> **waelas said:**
> @tl3000: thanks a lot, it worked for me, too. (Netgear WG511v1, kubuntu)

Because I'm using Kubuntu, I don't have to use wicd, though...

Cool!  Glad to hear another connection is made!

Just curious and potentially helpful to other Kubuntu users, please let us know how you handled the WEP/WPA keys--if used--without using a network manager like WICD.  Did you use wpa_supplicant to manually set up the network parameters in its configuration file?  Or did you used some other KDE network manager?  I used WICD so that I can easily switch between and connect to different wireless networks without having to manually enter the parameters each time I connect to a different network.  WICD would manage the various network profiiles as I travel between network sites.  Thanks.

---

### Post by Revolution on 2007-05-08
I have a WG511V1 on Feisty and it worked first time on an open network. I havent tried it on WPA or WEP yet.
I used the SSID 'any' and it works and connects to any open network with DHCP.
Also the SSID box in the wireless setup screen is a drop-down which lists all SSIDs it can hear.
One thing was it didnt show any signal strength yet my WG511V2 card does show signal strength.

---

### Post by gt24 on 2007-05-15
An update...

My wireless card was blinking its' transmission light non-stop with the built in prism54 drivers.  In a non-related issue (I thought there was a problem with Linux... but it was an issue with my router... DOH), I switched to the ndiswrapper driver from a current Netgear download (netwg511 extracted from an install).  Once I rebooted my router (see above), my card works much better... the prism54 drivers must have some major issues.

Note though that I did try ndiswrapper drivers before with the Gnome Network Manager to no avail (it would never connect).  I'm not using Wicd right now (I couldn't get it to work, it wouldn't grab an IP address), so I am back to Wifi Radar.  Eitherways, without any managers what-so-ever, you can manually run things from the command line as a test.

First make sure you have a wpa_supplicant.conf file in the /etc/wpa_supplicant/ folder.  The following commands are more so to test and not to run full time, so you will need to enter the first command in one terminal window, the second command in another, and test your connection with a browser.  (Ey, I'm confusing...)

sudo wpa_supplicant -Dwext -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -K

sudo dhclient wlan0

Also, wmaster0, if that connection is seen, is some goofy thingy put in by Wifi Radar, go figure.

I GREATLY appreciate the earlier walkthrough though.  I followed it to get my ndiswrapper operational (was convenient and worked beautifully).  Thanks!

---

### Post by Scrib on 2007-07-10
PLEASE HELP!!! I've got a WAG511 and I'm trying to use it with WPA. My WAG511 was picked up by Ubuntu but failed to connect to my WPA encrypted router - same as you guys.

I tried a few thing on this forum and now my problem is worse. I now don't have any wireless at all oly wired!! ARRGHHH!! Some of the threads talked about installing madwifi, which i now beleieve was already installed - opss - which I think has totally screwed it.

Is there a simple way to get myself back to where I started from - i.e. reinstalling something - madwifi?? I've looked in ADD/REMOVE and cannot see anythng fro MADWIFI. The MADWIFI site isn't to easy to follow and, as a newby, if i try to instal the .deb packages it appears to be a version from 2004.

Its annoying because my box is duel booted with Fedora 7 and it was a breeze to sort this out with my WAG511 and Unbuntu is supposed to be more user friendly - PLEASE HELP.

---

### Post by Scrib on 2007-07-10
I got back to where I was by following this article:

[http://ubuntuforums.org/showthread.php?t=485579&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=485579&highlight=madwifi)

So - only got the WPA thingto fix. I'll review this thread and see if I can get it to work. Nearly there!

---

### Post by Scrib on 2007-07-12
I've hit a problem. Everything installed ok, but when I launch Wicd, put in my wireless settings, set the perferences to "NSDiswrapper" and then click "connect". It just sits there with a "Generating WPA configuration file..." message.

Anyone any ideas.

---

### Post by imdano on 2007-07-12
Make sure you're giving it your normal ascii passphrase, not the hex version.  Also make sure your passphrase is at least 8 characters and only uses letters and numbers, I've had problems using other symbols in the past.  You might try manually setting up your wpa through the console to make sure it works correctly as well.  I can help you with that if you want, and then show you how you'd have to change wicd to get it to work automatically.

edit: Also are you actually using Ndiswrapper as your network driver?  Your previous posts suggest you're using madwifi, which means you should use wext as the wpa supplicant driver in your wicd settings.

---

### Post by Scrib on 2007-07-15
OK heres were I'vr got to - I changed my key to remove any funny characters, so its now just letters and numbers and its over 8 chars long - still no joy.

Any more ideas?

---

### Post by Scrib on 2007-07-15
Just noticed something - I had a console open when I tried to connect (using ndiswrapperin Wicd preferences) and got a log of "log" errors from the "UBuntu Kernal" in the console window.

I wonder if there is a problem with Wicd. I did use the latest (stable) version and no the one listed in the instruction above.

I also noticed that if I use the madwifi drivers (by selecting them from Wicd preferences) I get past the "Gernerating WPA configuration file..." message and get "Obtainin IP adress". However this times it comes up with "not connected". :(

---

### Post by imdano on 2007-07-15
Did you try using wext instead of ndiswrapper as your wpa supplicant driver in wicd settings?  From your earlier post you made it sound like you were using madwifi drivers, not ndiswrapper.  My understanding is that with madwifi you're supposed to used wext as your wpa supplicant driver (not madwifi, which is kind of strange).

---

### Post by gracedman on 2007-07-15
I find my WG511 is finally working without intervention after the latest round of patching.  Thanks to whomever fixed it! - John

---

### Post by tva995 on 2007-07-16
thanks tl3000 for your very helpful post... i'm running feisty and was able to get two pcmcia cards working on my laptop using ndiswrapper and wicd... one is an encore card with the rtl 8185 chipset (i thought it had the ralink 2500 chipset when i bought it) and the other is a zoom card with the isl3890 chipset... i believe the key is using wicd because neither card could work with encryption using network manager and gnome network manager... thanks again...

---

### Post by redeemer on 2007-07-17
> **tl3000 said:**
> 
-- Install the WG511v1 Windows 2K driver:
[download or copy the netwg511.inf & WG511ICB.sys files to the Home Folder]

Dumb question - where do I download these files from?

Thanks,
Tom.

---

### Post by redeemer on 2007-07-18
> **redeemer said:**
> Dumb question - where do I download these files from?

Thanks,
Tom.
Ah, I had to download the ZIP file (containing the drivers) from netgear.com, then extract them from data1.cab using the cabextract program. I took the drivers from this directory:

~/WG511v300/Disk1/Driver_2k_File_Group

Is that correct? My problem now is, with wicd I get as far as "Obtaining an IP addres..." which never successfully occurs. Any thoughts people?

Cheers,
Tom

---

### Post by 555 on 2007-07-18
I too have a problem with WG511v1 and tried the suggestion by tl3000 but can't get it to work still. I think i've done it right and followed his instructions but i'm new to ubuntu coming from windows xp. For me Wicd manager just says no wireless networks found even though i removed prism and installed the driver files from home that i transfered from Xp (.ini) and it says its installed. Now the green light just flashes and theres no yellow at all but with network manager i could get yellow light albeiit flicking dimly and fast. Also it did pick up another nearby wireless network but just not mine and could not connect to it when i put the ssid and wep key in. 

My post is here [http://ubuntuforums.org/showthread.php?p=3041916&posted=1#post3041916](http://ubuntuforums.org/showthread.php?p=3041916&posted=1#post3041916)

Some people are saying they have it working out of the box or did after updates but i'm not sure what to do as the laptop ubuntu is on has to connect to wireless. Wired works fine.

---

### Post by mastergunner on 2007-08-17
.....

---

### Post by Zhengtonic on 2007-09-13
I keep hearing that the WG511v1 issue is no more,
and everything works out of the box now with the latest update.
I undo'ed the workaround by tl3000 (really appreciated it), 
and guess what ... still the same problems as 2 month before. 
Well is it just me ,or do some of you still have the same problems 
with your card after the latest update?

---

### Post by nomenklatura on 2007-09-15
Hi,

I too have been having the problems above. Is there a less fussy solution to this than the one outlined by tl3000, or is that the only way to go? I find the reduction of signal quality an unacceptable compromise in the long term.

I'm sure you have heard it all before, but I consider this to be a step in the wrong direction for Ubuntu to have taken. I was not expecting to ever have to deal with this kind of thing in the year 2007.

---

### Post by mastergunner on 2007-09-15
I cant get my netgear WG511 to even light up. I have removed network manager and have WICD but it just doesnt light up anymore. Can someone help a noob out. Thanks.

---

### Post by rebird242 on 2007-10-29
I need the netgear driver files for the  WG511v1 so I can used NDISWRAPPER. My laptop has already been formatted to linux. I cant download and extract the drivers since my desktop doesnt have that card. If someone could post a link with the two files in a zip files it would save me a HUGE amount of hassle.

Thanks,

---

### Post by j2fraser on 2008-02-01
You know what drives me crazy about this? I could not get my WG511v1 fully working in Ubuntu (see all the fantastic help I got [_here_]("http://ubuntuforums.org/showthread.php?t=531538")), but I start up Kubuntu and... voila, it just works! How is it that it can just work, automatically, in Kubuntu -- no ndiswrapper, /etc/interfaces tweaks, nada -- but can't get off the ground in Ubuntu? I wish I had (I don't) the technical competence to translate the wireless functionality for these cards in KDE/ubuntu over to Ubuntu, but I wouldn't have the foggiest of where to start. I know that this is just one little problem amongst many faced by those trying to get various pieces of (frequently outdated) hardware to work in Ubuntu and Linux, but I would love to see the person/people who made this work in Kubuntu help those who are trying to get it working in Ubuntu... :-? Until then, it's Kubuntu on the notebook!

---

### Post by tl3000 on 2008-02-01
For Gutsy version of Ubuntu, the solution for the WG511v1 is posted here:

[http://ubuntuforums.org/showpost.php?p=3624512&postcount=2](http://ubuntuforums.org/showpost.php?p=3624512&postcount=2)

[Edit] You need to reboot after the steps described in the above post.

The solution in this thread is for the Feisty version.

---

