---
title: "Flashing wifi light - 8.10"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Databit on 2008-10-27
I just upgraded to the Intrepid Ibex beta to give it a go. Wireless is working great but the wifi light is constantly flashing...which is horrible.

I found an old posting saying to run
echo "0" | sudo tee /sys/bus/pci/devices/0000\:0c\:00.0/led
to fix it but it doesn't seem to work for me. It also used the phrase "So, as you could have found out by reading the README" but didn't tell what readme and I'm not sure which to read either. 

Anyone have an idea on how to permanently shut this light off?

this might help. not sure:
databit@databit-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by Databit on 2008-10-28
Seriously this is horrible. Is this working as designed or should I file a bug report?

---

### Post by allanmboyd on 2008-10-30
Agreed. This is driving me even crazy. Please someone say how to stop this.

---

### Post by ProtoBot on 2008-10-30
Thirded. Any help in this respect will save your local ProtoBot many headaches...

---

### Post by Arrdee on 2008-10-31
Fourthed(?). Oh I'm so glad somebody else is having this problem. How do we stop it?

---

### Post by dark42 on 2008-10-31
Also same problem here, with my Dell XPS M1330 and Intel 4965AGN WiFi card.

---

### Post by mcmorry on 2008-10-31
Me too.
Dell Precision M90
Intel Corporation PRO/Wireless 3945ABG

It seems to be not a bug but a design feature. 

However I've found this: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211)

We could try some workaround descripted there.

---

### Post by nickzeff on 2008-11-01
Annoying the hell out of me too, on my Dell D820.

---

### Post by yeats on 2008-11-01
I'm having the same issue - I'm using a Dell Latitude D630.  I wonder if it's just a Dell issue?

---

### Post by yeats on 2008-11-01
I'll also mention that I'm running Kubuntu, so it's not Gnome-related.

---

### Post by Databit on 2008-11-02
Got it woo hoo. This is in one of the comments on
[http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html](http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html)

Create the a file called iwl-no-blink in /etc/network/if-up.d
in the file put the following:
```

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
	for dir in /sys/class/leds/iwl-phy*X; do
		echo none > $dir/trigger
	done
fi

```

chmod it to be executable:
```
chmod 755 iwl-no-blink
```

Reboot

No more flashy light. Browse the web happier

---

### Post by funchords on 2008-11-04
Related link:

[INDENT][http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1771]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1771")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211")[/INDENT]

Whoever thought this was a good idea must have a laptop where the LED isn't very visible.  I do like the idea of making it optional, or using a hack to stop the madness.  

My preference:
Blue when it's associated and working, including while doing IO
Orange when it's killed or unassociated 
Blinking never -- or maybe when something recent needs user attention (such as high priority events being logged)

---

### Post by funchords on 2008-11-04
> **Databit said:**
> Got it woo hoo. This is in one of the comments on
[http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html](http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html)

Create the a file called iwl-no-blink in /etc/network/if-up.d
in the file put ...

Didn't work for me. I can see that the script ran, but the LED flashes all the same.

---

### Post by ant1060 on 2008-11-05
Same here, I have installed the script and chmod 755'd it but the wifi light still flashes.
Does anyone know how to turn it off like it was in Hardy?
PLEASE!

---

### Post by dmundi on 2008-11-05
bump

---

### Post by gogo242 on 2008-11-05
bump

---

### Post by namgar on 2008-11-07
I followed the instructions above and they didn't work for me.

I changed the script to look like this:

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
	for dir in /sys/class/leds/iwl-phy*; do
		echo 0 > $dir/brightness
	done
fi

And have found that the LED will either stay on solid, or go off (I have seen it do both), but most importantly it doesn't flash.

---

### Post by ant1060 on 2008-11-07
Hi Namgar!
I tried your script but my wifi light is still flashing :(  Have you any more ideas?
Thanks so much for posting, BTW ...

---

### Post by namgar on 2008-11-08
Well I was playing some more and found that if I do this:

for dir in /sys/class/leds/iwl*;do echo rfkill0 > $dir/trigger;done
for dir in /sys/class/leds/iwl*;do echo none > $dir/trigger;done

The led ends up being on solid.

I'm not really sure why, I have some theories but without pulling out the code and looking at it for a while I can't be sure.

My only other advice is to just play with the trigger and brightness settings to see if you can find a combination that works.

---

### Post by frankleeee on 2008-11-08
Don't forget the tape option cover it up.

---

### Post by chadlewis on 2008-11-09
> **namgar said:**
> I followed the instructions above and they didn't work for me.

I changed the script to look like this:

#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
	for dir in /sys/class/leds/iwl-phy*; do
		echo 0 > $dir/brightness
	done
fi

And have found that the LED will either stay on solid, or go off (I have seen it do both), but most importantly it doesn't flash.

This one worked for me. Light is solid now. Thanks!

---

### Post by frecon on 2008-11-10
> **namgar said:**
> ..
I changed the script to look like this..

It start to blink again if I switch off and on the wifi and bluetooth (with my hardware switch on dell m1330). But as long as I don't do that it seem to work.

---

### Post by jsully1 on 2008-11-17
The script didn't work for me - any other ideas?

---

### Post by Databit on 2008-11-26
Just an update from my end. The scripts worked for me...for about a day then started flashing again despite no changes to the scripts. Kinda odd. Finally got frustrated and bought a new laptop. Now no more flashing wifi light ;)

---

### Post by chezzo on 2008-12-09
following (i think) the instructions in this thread, i now have a script reading
> 
#!/bin/sh
if [ "$IFACE" = "wlan0" ]; then
for dir in /sys/class/leds/iwl*;do echo rfkill0 > $dir/trigger;done
for dir in /sys/class/leds/iwl*;do echo none > $dir/trigger;done
for dir in /sys/class/leds/iwl*;do echo 0 > $dir/brightness;done
fi

but it's still not working... i'm using a dell inspiron 640m. anyone?

---

### Post by Jack Crossen on 2008-12-17
Maybe use the "iwconfig" command to check the id of your wireless adapter?

Mine is on "eth1" so I revised the script to

#!/bin/sh
if [ "$IFACE" = "eth1" ]; then
	for dir in /sys/class/leds/iwl-phy*; do
		echo none > $dir/trigger
	done
fi

The other change I made to the original is to use "iwl-phy*" rather than "iwl-phy*X". The phy*X is intended to stop the blink on tx/rcv but for some reason that didn't do the trick for this laptop.

I'm using an Inspiron E1405 with the Intel 3945 wireless adapter and this script made the light stop blinking for now.

---

### Post by ClanClover on 2008-12-21
Thanks Jack, been trying to cure the blinking LED for weeks on my Inspiron 6400 without success; your script worked a treat. 

Also for anyone new to Linux (like me!) the command to make the script executable requires superuser access so the command in terminal mode should be:

sudo chmod 755 iwl-no-blink

HTH

Thanks again Jack

---

### Post by joshuajtl on 2009-02-08
I tried everything in this forum thread and nothing worked, but I then found this solution and it worked:

a script in /etc/network/if-up.d/noblink with:

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger


run it, it works...

I found it here:
[http://ubuntuforums.org/archive/index.php/t-966511.html](http://ubuntuforums.org/archive/index.php/t-966511.html)

---

### Post by Quirinius on 2009-02-17
> **joshuajtl said:**
> I tried everything in this forum thread and nothing worked, but I then found this solution and it worked:

a script in /etc/network/if-up.d/noblink with:

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger


run it, it works...

I found it here:
[http://ubuntuforums.org/archive/index.php/t-966511.html](http://ubuntuforums.org/archive/index.php/t-966511.html)

Thanks for your help!

When I ran the script, I saw a couple of errors passing by. Then I relized that the light stopped flashing, this means in my case that you can also fix this problem with only the following lines:

#!/bin/sh
echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger

=D>

---

### Post by AegisTalons on 2009-02-27
I'm running Dell XPS m1330 with Intel 4965 AGN on Ubuntu 8.10. I don't know about you guys, but I kind of liked the blinking wifi light as it shows me a quick reference when data is being transferred over the wifi. I agree with you guys, that if it annoys you there should be an easy option to turn it off, in a more user friendly approaching through the [System] -> [Preferences] options. 

That is one thing that linux, at least Ubuntu, needs to do better is allowing all these options to be configurable through GUIs instead of CLIs as it is intimidating for a lot of people to use it.

---

### Post by Apple Guy on 2009-03-22
> **joshuajtl said:**
> I tried everything in this forum thread and nothing worked, but I then found this solution and it worked:

a script in /etc/network/if-up.d/noblink with:

#!/bin/sh
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:assoc/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:radio/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:RX/trigger
echo none > /sys/bus/pci/drivers/iwl3945/0000:0b:00.0/leds/iwl-phy0:TX/trigger

echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger


run it, it works...

I found it here:
[http://ubuntuforums.org/archive/index.php/t-966511.html](http://ubuntuforums.org/archive/index.php/t-966511.html)

All I had to use is:
echo none > /sys/class/leds/iwl-phy0:RX/trigger
echo none > /sys/class/leds/iwl-phy0:TX/trigger
echo none > /sys/class/leds/iwl-phy0:radio/trigger
echo none > /sys/class/leds/iwl-phy0:assoc/trigger

and it works!  Thanks!!!!:popcorn:

---

