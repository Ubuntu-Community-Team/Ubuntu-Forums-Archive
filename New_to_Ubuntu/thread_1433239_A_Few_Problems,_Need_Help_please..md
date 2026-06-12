---
title: "A Few Problems, Need Help please."
date: 2010-03-18
forum: New to Ubuntu
---

### Post by IneedHelps on 2010-03-18
After Installing Ubuntu On My HP Laptop, I'm Having A Few Problems

[1] The Sound Does Not Work Through The Speakers, Only Works If I Plug Headphones in.
[NEED FIXED]

[2] The Wireless Light On My Laptop Flickers When I'm Connected To The Internet? Does Anyone
Know How to make it a stay on the solid ON colour [Being Blue, orange when off]

[3] Is There Anyway to mount a samsung Mobile g3410, Like a Usb Drive etc, to make it show up on the desktop.

If anyone Could help me Fix These Problems I would Be Very Grateful And Would Consider A permanent Switch To The Linux community.

Thanks You.

Ineedhelps.

---

### Post by spiderbatdad on 2010-03-18
not sure on the led's I believe you will need to create a file in /etc/modprobe.d (possibly name it ipw2200.conf) in the file a single line reading 
```
options ipw2200 led=1
```

 This information is the result of a quick search and finding this old thread [http://ubuntuforums.org/showthread.php?t=83789](http://ubuntuforums.org/showthread.php?t=83789)

However, the file system has changed, and the above is a more accurate example of the present. 

I would also recommend one topic per threaad...but that's just my opinion.

---

### Post by sandyd on 2010-03-18
> **IneedHelps said:**
> After Installing Ubuntu On My HP Laptop, I'm Having A Few Problems

[1] The Sound Does Not Work Through The Speakers, Only Works If I Plug Headphones in.
[NEED FIXED]
[B]can you open a terminal, and type in

[/B]```
**lspci > ~/Desktop/lspci.txt**
```[B]
there should now be a file named "lspci.txt" on your desktop.
attach it.[/B]


[2] The Wireless Light On My Laptop Flickers When I'm Connected To The Internet? Does Anyone
Know How to make it a stay on the solid ON colour [Being Blue, orange when off]
```
[B]sudo touch /etc/network/if-up.d/iwl-no-blink
sudo chmod u+x /etc/network/if-up.d/iwl-no-blink
gksudo gedit /etc/network/if-up.d/iwl-no-blink[/B]
```[B]

copy and paste this
[/B]```
[B]#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
  for dir in /sys/class/leds/iwl-phy*; do
    echo none > $dir/trigger
  done
fi[/B]

```[B]

and click save.

[/B]```

[B]sudo touch /etc/pm/sleep.d/00wireless
sudo chmod u+x /etc/pm/sleep.d/00wireless
gksudo gedit  /etc/pm/sleep.d/00wireless[/B]
```[B]

copy and paste this in and click save.
[/B]```
[B]#!/bin/sh
case "$1" in
        resume|thaw)
                /etc/network/if-up.d/iwl-no-blink
        ;;
        *)
        ;;
esac[/B]
```[3] Is There Anyway to mount a samsung Mobile g3410, Like a Usb Drive etc, to make it show up on the desktop.
[B]
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363329)[/B] If anyone Could help me Fix These Problems I would Be Very Grateful And Would Consider A permanent Switch To The Linux community.

Thanks You.

Ineedhelps..

And I just realized. the [code] tags cant be bolded as well, or otherwise there will be some weird formatting issues...

---

### Post by xhalarin on 2010-03-18
Did you mean Samsung B3410 (not G)?  Do you have the USB cable for it?

---

### Post by rahulshah on 2010-03-18
just connect your mobile phone's usb cable and plug it into the laptop. Ubuntu will automatically configure it for u to use. U can also use bluetooth which is also quite simple. 

There is sound icon on the panel above the screen. Click on it and go to preferences. There must be something that says volume amplifier or something like that, just unselect it and your sound will work. I am using fedora now so cant tell you the exact option. But i am sure you can make it work from volume preferences.... :)

My wifi light is off on fedora but wifi works. It behaves a little weird on linux. It doesn't matter all I care is that wifi works..... :D

I hope that helps... Have gun:)

---

### Post by spiderbatdad on 2010-03-18
[http://blog.crossedstreams.com/ubuntu/flickering-wireless-led-in-ubuntu-810-intrepid-ibex/](http://blog.crossedstreams.com/ubuntu/flickering-wireless-led-in-ubuntu-810-intrepid-ibex/)

The arch linux forum also has more info on this wireless led issue as well, with some expanded options in case the above doesn't solve the problem: [http://bbs.archlinux.org/viewtopic.php?id=74269](http://bbs.archlinux.org/viewtopic.php?id=74269)
Also here: [http://ubuntuforums.org/archive/index.php/t-1017700.html](http://ubuntuforums.org/archive/index.php/t-1017700.html)

---

### Post by IneedHelps on 2010-03-18
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

------------------------

Also The Wireless Light Fix Didn't Work, Its Everytime I open A New internet page or some kind of activity is happening the light will flicker, it did not do this in Windows.

Thanks

---

### Post by IneedHelps on 2010-03-18
> **xhalarin said:**
> Did you mean Samsung B3410 (not G)?  Do you have the USB cable for it?

Yes Sorry G, But When I do connect it Via Data Cable nothing appears on the desktop.

---

### Post by sleepee on 2010-03-18
im a noob myself, but i remember having the same thing happen to me with my wireless light on my HP.

everytime i'd download or upload, or just have my wireless connection be in use, the light would flash orange/blue.

it's not doing that anymore, but tbh, i don't remember how i did that or how it happened..
but if i remember, i'll be sure to post back...

btw, as far as the no sound issue, i too had some similar problems with my hp...
i just upgraded to the lastest alsa version and my sound worked..
here's a link to a useful how-to if you want to try that:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by sandyd on 2010-03-18
> **IneedHelps said:**
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

------------------------

Also The Wireless Light Fix Didn't Work, Its Everytime I open A New internet page or some kind of activity is happening the light will flicker, it did not do this in Windows.

Thanks
the funny thing is that I have exactly the same hardware as you in my dell laptop.
and sound worked out of the box....

whats the output of```
aplay -l
```

---

### Post by sandyd on 2010-03-18
> **IneedHelps said:**
> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

------------------------

Also The Wireless Light Fix Didn't Work, Its Everytime I open A New internet page or some kind of activity is happening the light will flicker, it did not do this in Windows.

Thanks
the funny thing is that I have exactly the same hardware as you in my dell laptop.
and sound worked out of the box....

[s]so, it should be working...[/s]


read :[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269027)

---

### Post by IneedHelps on 2010-03-18
> **carlee said:**
> the funny thing is that I have exactly the same hardware as you in my dell laptop.
and sound worked out of the box....

whats the output of```
aplay -l
```

I'm Currently trying a solution just now which is upgrading ALSA, Thanks For Your Suggestion On The Wireless problem but do u know any other ways that could fix it? as i said its just when things are downloading, loading new page or any kind of internet activity it will flicker.

Thanks

---

### Post by sandyd on 2010-03-18
> **IneedHelps said:**
> I'm Currently trying a solution just now which is upgrading ALSA, Thanks For Your Suggestion On The Wireless problem but do u know any other ways that could fix it? as i said its just when things are downloading, loading new page or any kind of internet activity it will flicker.

Thanks
same thing on mine. Ubuntu uses it to indicate network activity.

---

### Post by IneedHelps on 2010-03-18
> **carlee said:**
> same thing on mine. Ubuntu uses it to indicate network activity.

:P I'm Just one of those picky people i guess ;) I will Get Back To You On The Output of that other code, If anyone else knows of a fix then please feel free to post :)

---

### Post by sandyd on 2010-03-18
> **IneedHelps said:**
> :P I'm Just one of those picky people i guess ;) I will Get Back To You On The Output of that other code, If anyone else knows of a fix then please feel free to post :)
Ive actually posted the link to the exact solution in my other post.
It seems to be affecting HP laptops.
Ive nomitnated the bug for release in Lucid (dolphinaura is my username over there), but weel have to see about that....

---

### Post by IneedHelps on 2010-03-18
Sound Is Fixed Thanks to A solution Above, THANK YOU! : D

Now To Just fix the bloody internet light and my phone connecting :)

thanks for all of your help !

---

