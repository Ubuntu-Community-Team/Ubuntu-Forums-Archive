---
title: "how to use internet through bluetooth???"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by saikat_tapu on 2009-04-26
hi friends,

i want to use nokia 6680 as modem.
how can i use it as modem connecting through blue-tooth???

---

### Post by johnwillis on 2009-04-26
I have had more success doing this through a USB cable to my N95 - Ubuntu picked it up as a mobile broadband connection from Ubuntu 8.10 onwards so long as you select "PC Suite" when you connect the phone to the PC/laptop.

Hope this helps...

-J

---

### Post by saikat_tapu on 2009-04-26
> **johnwillis said:**
> I have had more success doing this through a USB cable to my N95 - Ubuntu picked it up as a mobile broadband connection from Ubuntu 8.10 onwards so long as you select "PC Suite" when you connect the phone to the PC/laptop.

Hope this helps...

-J
but there is some problem with my mobile's usb port..........so i need to connect it through bluetooth......if you know anything then tell me............how to

---

### Post by johnwillis on 2009-04-26
It can be done, you should be able to treat your phone as a modem using the blue tooth icon in the tray of GNOME (so long as your bluetooth stack is supported)

Set up the device to pair and make it a COM port when given the option... then set up a new network connection under the "Network Connections" under the administration menu, select dial up as the type and the appropiate port you just created...

Then type in a PAYG dial up internet provider and your all good...

If you want to use your mobiles 3G connection then bear in mind that you will need a USB connected phone as far as I know...

Also worth noting is that most UK mobile providers do NOT allow you to attach your mobile to a laptop/games console for surfing/downloading as it breaks your agreement with them. If caught you could be fined or taken to court...

It is exactly this reason why Apple removes all applications from it's iPhone store that allow you to do that!

-J

---

### Post by hatalar205 on 2009-04-26
The following link can be helpfull. I did with Samsung E250 and it worked.
[https://help.ubuntu.com/community/BluetoothDialup#Listing%20Bluetooth%20devices](https://help.ubuntu.com/community/BluetoothDialup#Listing%20Bluetooth%20devices)

---

### Post by saikat_tapu on 2009-04-27
> **hatalar205 said:**
> The following link can be helpfull. I did with Samsung E250 and it worked.
[https://help.ubuntu.com/community/BluetoothDialup#Listing%20Bluetooth%20devices](https://help.ubuntu.com/community/BluetoothDialup#Listing%20Bluetooth%20devices)
hey, that was a good try.........but still not able to connect the mobile..........:(

---

### Post by hatalar205 on 2009-04-27
> **saikat_tapu said:**
> hey, that was a good try.........but still not able to connect the mobile..........:(

Same link
[https://help.ubuntu.com/community/BluetoothDialup#Listing%20Bluetooth%20devices](https://help.ubuntu.com/community/BluetoothDialup#Listing%20Bluetooth%20devices)
This Headline
**Installing Bluetooth and dialup packages**

---

### Post by jrc4ever on 2009-05-10
still doenst work :-(

---

