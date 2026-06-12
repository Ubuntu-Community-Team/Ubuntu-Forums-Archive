---
title: "Wireless Light Blinking During Internet Activity."
date: 2010-03-20
forum: New to Ubuntu
---

### Post by IneedHelps on 2010-03-20
Is there Any Way in which you can make the wireless light of my HP g61-110sa Laptop have the solid on colour [blue] instead of flickering between blue and orange when some kind of internet activity is taking place?

Thanks

Craig Mills

---

### Post by linuxman94 on 2010-03-20
No, you can't.  That feature is controlled by the card's firmware.  You have no control over it.

---

### Post by IneedHelps on 2010-03-20
are you sure because im seeing a lot of posts of ways to fix it?

---

### Post by linuxman94 on 2010-03-20
Hmmmm. :-k I'll look into it.

---

### Post by hansdown on 2010-03-20
> **IneedHelps said:**
> are you sure because im seeing a lot of posts of ways to fix it?

Have those posts helped you fix it?

---

### Post by IneedHelps on 2010-03-20
They Have Not, If Someone Could Help Me Fix This I Would Be Much Grateful Its A pain :P

---

### Post by teward on 2010-03-20
_*First, Typing Like This Is Kind Of Annoying, Since You Don't Need To Capitalize Every Word.*_

Second, I've got 3 different computers.  One uses a wireless card that's external (so it doesn't blink ever), another is this Netbook (the wireless card is a Broadcom, luckily the drivers on Ubuntu Netbook Remix had the proprietary drivers), and the other is my Dell laptop, using Intel.  The Intel is the only one that blinks, and I think its something with the drivers.  Not sure if they will help you, as drivers vary from card-to-card.

---

### Post by lavinog on 2010-03-20
You have the option of physically modifying the leds.
If you have 2 leds (1 blue and 1 amber), you could put electrical tape over the amber one.
If it is a single led, you might be able to disconnect a wire or a lead to the amber.

If the blinking is annoying, and you don't want to open up the computer, you could cover the indicator externally. (Do you really need to see the solid blue light anyway if your connection is working?)

Just some thoughts.

---

### Post by hictio on 2010-03-20
I'll jump and ask here as well, I have a Thinkpad T43, and I have noticed that the WiFi LED (below the laptop screen) sometimes blinks, and sometimes don't, and there is no pattern, it doesn't have anything to do with the network activity going thru the WiFi card...

For what I have Googled, the blinking should be related to the traffic that passes over the WiFi, but I don't see any relation with the blinking and the real activity.

---

### Post by AndyDeGroo on 2010-03-21
It actually may be possible control those LEDs depending on wifi card and driver.
One way to check if there are any way to control LEDs in your machine - look for lines like "Registered led device" in your /var/log/dmesg

I'm using Ralink PCI card in my PC and there are two matching lines in my dmesg:
```

[   12.696545] Registered led device: rt61pci-phy0::radio
[   12.696565] Registered led device: rt61pci-phy0::assoc

```don't know if it is possible to control somehow those LEDs.

To check what kind of beast is your card run this command in terminal:
```
sudo lshw -class network
```mine says:
```

  *-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wmaster0
       version: 00
       serial: 00:08:a1:a7:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.20.2 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:ef000000-ef007fff

```but if you like GUI tools, get hardinfo or something similar.
Then try searching your cards model and/or driver name to find out more.

---

### Post by IneedHelps on 2010-03-21
> **AndyDeGroo said:**
> It actually may be possible control those LEDs depending on wifi card and driver.
One way to check if there are any way to control LEDs in your machine - look for lines like "Registered led device" in your /var/log/dmesg

I'm using Ralink PCI card in my PC and there are two matching lines in my dmesg:
```

[   12.696545] Registered led device: rt61pci-phy0::radio
[   12.696565] Registered led device: rt61pci-phy0::assoc

```don't know if it is possible to control somehow those LEDs.

To check what kind of beast is your card run this command in terminal:
```
sudo lshw -class network
```mine says:
```

  *-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wmaster0
       version: 00
       serial: 00:08:a1:a7:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.20.2 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:ef000000-ef007fff

```but if you like GUI tools, get hardinfo or something similar.
Then try searching your cards model and/or driver name to find out more.


------
I found this.

[   10.637259] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.637994] Registered led device: ath9k-phy0::radio
[   10.638012] Registered led device: ath9k-phy0::assoc
[   10.638028] Registered led device: ath9k-phy0::tx
[   10.638045] Registered led device: ath9k-phy0::rx

---

### Post by luttermann on 2010-03-21
> **AndyDeGroo said:**
> 

```

[   12.696545] Registered led device: rt61pci-phy0::radio
[   12.696565] Registered led device: rt61pci-phy0::assoc

```don't know if it is possible to control somehow those LEDs.



It is indeed! have a look in /sys/class/leds there you will find the leds that are controlable from userspace. In the leds folder there should be one folder for each led, and within that you will find a "file" that's called trigger, now if you read it with cat like this:
```
cat /sys/class/leds/some-led-name/trigger
```
you can see all the currently possible trigger modes, on my machine for instance (IBM ThinkPad T43p)
it looks something like this:
```

# cat /sys/class/leds/tpacpi\:\:power/trigger
[none] AC-online BAT0-charging-or-full BAT0-charging BAT0-full rfkill0 rfkill4

```
now if I want to change the Power-led on the computer to indicate if the battery is charging i can do this:
```

# echo BAT0-charging > /sys/class/leds/tpacpi\:\:power/trigger
```

What types of triggers there is available depends on what drivers are loaded in to the kernel. there is a few drivers/modules you might want to look at:

ledtrig-timer
ledtrig-default-on
leds-pca955x
leds-wm8350
leds-pca9532
led-class
ledtrig-gpio
leds-dac124s085
leds-net48xx
leds-alix2
leds-lp3944
ledtrig-backlight
leds-wrap
ledtrig-heartbeat
leds-bd2802
leds-da903x
leds-gpio

---

### Post by IneedHelps on 2010-03-21
I think this might be something to do with the device,

none ACAD-online BAT0-charging-or-full BAT0-charging BAT0-full rfkill0 phy0rx phy0tx phy0assoc [phy0radio] 

what would i change to make it just solid blue when my internet is connected?

---

### Post by AndyDeGroo on 2010-03-22
You can try ```
echo phy0assoc > /sys/class/leds/YOUR::LED_DEVICE/trigger
``` but that's just a guess.
Note: replace YOUR::LED_DEVICE with your actual device name. Autocomplete with TAB is your friend. ;)

phy0assoc may stand for "associated with access point"
phy0tx - transmitting
phy0rx - receiving
rfkill0 - radio signal is off (killed)

I tied echoing rfkill0 to my LEDs trigger, but none of LEDs changed and I presume that driver does not actually send that state to hardware.
Then I tried echoing zero to brightness file in both of my LED devices' directories and voilà - lights are out. And values in those files have persisted over reboots.
So far I know that current state is indicated by one which is in brackets.

For me this is just an experiment out of curiosity because my LEDs are behind my PC on PCI board and does not bother me.

---

### Post by AndyDeGroo on 2010-03-22
**Warning:** Your system may freeze if you set wrong trigger for LEDs and if driver of particular device is buggy!

Somehow I managed to freeze my Ubuntu twice, by setting trigger to phy0rx or phy0tx.
After hard-resetting I checked log files, but there was no evidence to suggest that something went wrong.

Maybe I should report this bug to rt61pci/rt2x00pci driver maintainers?
Although dpkg -S rt61pci lists only linux-image and linux-headers packages, which makes me think that I should file bug to kernel package maintainers.

---

### Post by wasmgrr on 2011-09-30
I'm having the same problem, but it has only recently started.
I'm sure I have not changed anything other than the normal updates, and noticed a few days ago that my bright blue light that was normally solid, is now blinking constantly!
GRR
So if anyone knows what has changed and how to possibly fix it so that it is solid again, that would be great.
I have read a heap of fixes for different versions of Ubuntu and am not sure if I try them it will work and if not how do I undo any changes made :(
I have v11.04 but don't know off hand what network card/driver/anything a bit more technical. I will find out and post those details soon.

---

### Post by wasmgrr on 2011-09-30
> **wasmgrr said:**
> I'm having the same problem, but it has only recently started.
I'm sure I have not changed anything other than the normal updates, and noticed a few days ago that my bright blue light that was normally solid, is now blinking constantly!
GRR
So if anyone knows what has changed and how to possibly fix it so that it is solid again, that would be great.
I have read a heap of fixes for different versions of Ubuntu and am not sure if I try them it will work and if not how do I undo any changes made :(
I have v11.04 but don't know off hand what network card/driver/anything a bit more technical. I will find out and post those details soon.


OK, found a REALLY easy solution...
[http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops)
Seems to work just fine for me in version 11.04
Yay!!!
:)

---

### Post by Ruisou on 2011-10-18
That fix worked under 11.04, but since oneiric it no longer works. back to the blinking.

---

### Post by h2oskr on 2011-10-19
Same. Had a solution in 1104 but none for 1110. See more info in:
[http://ubuntuforums.org/showthread.php?t=1595290](http://ubuntuforums.org/showthread.php?t=1595290)

---

