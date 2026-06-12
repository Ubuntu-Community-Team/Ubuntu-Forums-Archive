---
title: "Help - my wireless is cactus!"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by Quotidian Minutia on 2008-07-09
I have been working for weeks (literally) trying to get my wireless to work.  A few days ago I finally succeeded, and had it connected for about 24 hours.  Then I (stupidly) tried to adjust things so that it would automatically connect each time I turned on my computer, and since then, I can't connect wirelessly at all.  I've thoroughly searched the forums, and have made use of lots of very helpful how-to guides, especially this one [http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110](http://ubuntuforums.org/showthread.php?t=400236&highlight=dwa-110)

I was originally trying to get a Netgear Wireless-G PCI Adapter WG311 to work.  However, after no joy with that (and reading on the forums about so many other people finding it a nightmare) I gave up.  Now I'm onto a D-Link DWA-110, which is what finally worked, but now doesn't.  The WG311 is still physically in my computer, and the DWA-110 is connected via USB.

Other things I've tried:

Installing ndiswrapper with the appropriate driver
Uninstalling Network Manager, and using Wicd instead
Doing a whole lot of command line stuff that I don't fully understand (but I'm good at following directions!)

What seems to have been the nail in the coffin was attempting this:

> If the instructions above did work for you, here's what you can do to make the interface be brought up automatically across reboots:

   1. Edit the /etc/network/interfaces file
      Code:

      gksu gedit /etc/network/interfaces (if you are using Ubuntu)
      kdesu kate /etc/network/interfaces (if you are using Kubuntu)

   2. Look for a section containing "wlan0", if there is no such section, add the following to the bottom of the file:
      Code:

      auto wlan0
      iface wlan0 inet dhcp

   3. Beneath those lines, add the following (*):
      Code:

      	pre-up ifconfig wlan0 up
      	pre-up iwconfig wlan0 essid YOUR_ESSID
      	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

   4. If you have it installed (you will if you are using dapper), remove network manager (!)
      Code:

      sudo aptitude purge network-manager


If you have an ASCII wep key, make sure to prefix it with an "s:" (without the quotes). There should be no white space between the semicolon and the actual key. If the key is shared you need to add "restricted" (again without the quotes) directly after the "key" part. Make sure to seperate "restricted" with a space on either side of the word. Thanks to NewWithoutClue for pointing this out.

If you are using WPA security on your wireless network, then your /etc/network/interfaces file should look like this:

Code:

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra



Since doing that, I can't seem to connect at all.  And my computer seems to be doing odd things (like having difficulty starting up sometimes, and doing what I tell it to very slowly).  I'm quite worried that I've inadvertently messed something important up, but I don't know how to check! 

Any and all help greatly appreciated!

---

