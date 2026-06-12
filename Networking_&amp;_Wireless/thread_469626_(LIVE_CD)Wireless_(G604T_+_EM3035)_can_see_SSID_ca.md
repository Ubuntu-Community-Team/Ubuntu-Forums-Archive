---
title: "(LIVE CD)Wireless (G604T + EM3035) can see SSID cant connect / XP / Ether both work."
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by phonixor on 2007-06-10
**SOLUTION IN POST 3!!!**

There are a looot of posts about this topic, but i couldn't find a solution out there yet, but sorry if i might have overlooked...

Description:
I am using a live CD to test out ubuntu (because i wanted to be sure that i could still use internet before i made the final switch), but i cant seem to get my wireless to work properly...
I can see my wireless network (SSID) but i cant seem to be able to connect it.

My resent failures:
I tried enabling/disabling WEP.
I tried manual connection (kinda made ubuntu crash).
I tried ubuntu 6.06(.1) cause i read this topic ([http://ubuntuforums.org/showthread.php?t=419905](http://ubuntuforums.org/showthread.php?t=419905) (someone with same router\problem in there)) , but it seamed that my wireless card wasn't supported... (and wireless settings made ubuntu crash)
I get instant access when i use my Ethernet port... but thats not what i need...
(Oooh on XP my wireless works (sometimes even when it says it doesn't ;p (silly billy)))

Tech stuff:
I have a D-Link G604T Wireless Router
I have an EMINENT EM3035 wireless usb adapter (though have tried it on an other computer with a differend wireless card aswell (same problems)).
(checked the EMINENT site but couldn't find any help\drivers for Linux, and it seems that since i can find my SSID it should work....)

any help will be greatly appreciated,
with kind regards,
GJS

PS:
ooh i really like the new NFTS support... the new white logo...
only think i didn't like is the stupid new status bar (which is XP like and goes back and forth like a cylon/knight rider, but without the coolness),the status bar and loading screen of 6.06 looked better...

---

### Post by phonixor on 2007-06-10
Well its no more (life cd)... i thought maybe i get lucky and  i just installed ubuntu...
Still no wireless connection for me here.... But luckily my LAN works...

i had a private message form someone using the same router... and he bought a new wireless adapter and now it seems to work...
so i think i can safely conclude that my adapter is the trouble maker.... 


---------------------------terminal------------------------
lsusb -v | less
---------------------------------------------------------------
Bus 001 Device 002: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2570 802.11g WiFi
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
  bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
  bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              300mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
--------------------------------------------------------------------
i really don't see how this is gonna help me any further...
cause i cant even see anything like "EM3035" or something like that to indicate that it really is this product...
a well i guess i gotta continue hacking.... which is funny but not really productive... 


anyone had this problem before?
or is willing to help me out?
pretty plzzz

PS:
oooh it  gives me great pleasure that i just killed that stupid Totem media player and replaced it with VLC, and made it work in firefox!!!
(Remove both with "synaptic package manager" (ignore all things like "ubuntu... needs this") use "add/remove" to download both vlc and firefox(again) and use the "synaptic package manager" to install "mozilla-plugin-vlc" and voila!!!)
oooh and i also played TatSet (based on the card game SET) in Wine!!! ([http://www.tatset.com/](http://www.tatset.com/)) FREE GAME BTW!!!!
(high scores are mentained in "C:\"windows\TatSet.ini)

---

### Post by phonixor on 2007-06-15
WHOOOHOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!
:popcorn:

I DID IT!! well kinda...

EM3505 apparently needs a RT2500usb driver...
(i later saw that sourceforge had also some projects working on this... haven't checked these though...)

1:  download the: "3035all.zip" from the EMINENT website (this is the driver)
2: unzip it and run it on a windows machine (Wine crashes....)
3: copy the directory "RALINK" to your Ubuntu system (using samba (is already installed and working on a default Ubuntu))
(located in c:\program files\...)
4: add/remove (add here ;p) Windows Wireless Drivers  (ndiswrapper driver installation tool)
(more info on [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/))
5: open up a console, and type something like
--------------
ndiswrapper-1.9 -i "/home/phonixor/Desktop/RALINK/RT7x Wireless LAN Card/Installer/WINXP/rt2500usb.inf"
-----------------
6 : then type:
-----------------
ndiswrapper -l
-----------------
to confirm if it is installed properly
i got something like
============
 RT2500 : driver installed
       device (14E4:4320) present (alternate driver: rt2570)
============
i think "rt2570" is the Ubuntu default driver.... (Someone confirm this plzzz ;p)

if you have no alternate driver i think it should work now else goto step 7!

7: try till succeed (I had to Unplug my Wireless network adapter... (and maby reboot...))
----------------------
sudo rmmod rt2570
----------------------
replace rt2570 with the alternate driver found in step 6...

Enjoy your wireless!!! (you should see not only the SSID's now but also the connectivity... (a very welcome change ;p))

(8: remove the RDLINK dirs... from my desktop and pray that if i soon reboot my comp step 8 wasnt a mistake ;p... )


(not sure about step 4: as description says its only a front end... which ain't working)


hope this helps other people....
any questions: [email]phonixor@gmail.com[/email] (you may spam all you want... dont think there are any spambots out there that havent found me yet ;p)

(cost me about 2 days to figure this damn thing out... a well least i learned something ;p... i hope....)

---

