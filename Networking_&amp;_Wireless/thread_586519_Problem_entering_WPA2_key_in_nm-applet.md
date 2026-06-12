---
title: "Problem entering WPA2 key in nm-applet"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by penguins! on 2007-10-22
Right so I've been having problems trying to get Feisty to accept a network key.  I know that my setup supports WPA2 AES because ubuntu will connect when I use a simple passphrase.

I want something a little more secure though and entered a 64-bit hex for the router. Windows and even my Skype phone will accept this without problems but nm seems to  refuse it.

I've noticed that the fields for entering WEP keys allow you to specify whether  it's ASCII or a hex or whatever but when the dialogue appears for my network it correctly recognises it as WPA2 but there is only one field with no option to specify what type of key it is.

I enter the hex and it doesn't connect.

Any  ideas ?   :confused:

Any help would be greatly appreciated, I'm stuck with windows and I feel like I've lost a limb :(

Thanks!

---

### Post by wieman01 on 2007-10-22
WPA should not let you enter in HEX, only plain text. It might occur that NM does not like certain special characters, but apart from this it should work. Do you have the WPA/WPA2 option at all?

---

### Post by penguins! on 2007-10-22
Yep, the WPA2 option shows up and nm realises that this is the type of network I'm trying to connect to, it just won't accept the key.

The problem might make more sense if I put it in context. I have a wireless network that I need 3 devices to connect to, one ubuntu box, one XP box and a wifi skype phone.

I wanted reasonably good security so I opted for a random WPA2 AES  key, maximum length. None of the devices have a problem with a short passphrase but it was when I tried to get the maximum length one working that the problems started.

Couldn't get all the devices to accept a passphrase that contained random characters so I opted for entering a hex key which the router allowed me to do. Windows and the skype phone accept this no problem but I just can't get nm to connect now using the hex. I've tried modifying it on the keyring too (which looks like it stores all wireless keys in hex format) but no joy.

---

### Post by wieman01 on 2007-10-22
> **penguins! said:**
> Yep, the WPA2 option shows up and nm realises that this is the type of network I'm trying to connect to, it just won't accept the key.

The problem might make more sense if I put it in context. I have a wireless network that I need 3 devices to connect to, one ubuntu box, one XP box and a wifi skype phone.

I wanted reasonably good security so I opted for a random WPA2 AES  key, maximum length. None of the devices have a problem with a short passphrase but it was when I tried to get the maximum length one working that the problems started.

Couldn't get all the devices to accept a passphrase that contained random characters so I opted for entering a hex key which the router allowed me to do. Windows and the skype phone accept this no problem but I just can't get nm to connect now using the hex. I've tried modifying it on the keyring too (which looks like it stores all wireless keys in hex format) but no joy.
Two points, penguins... as I had the same trouble when I updated my WPA2-AES key.

**a.** Some special characters cause problems, try alpha-numeric first.

**b.** They maximum key length that some routers allow are too long for Network Manager. You will be able to confirm that... When you put in the key the "Connect" button will be grayed out until you shorten the key. In my case 63 characters were the maximum length.

_**EDIT:**_
This is a good pass key generator that you can use: [http://darkvoice.dyndns.org/wlankeygen/]("http://darkvoice.dyndns.org/wlankeygen/")

---

### Post by TBerben on 2007-10-28
I have another problem related to WPA2: my router demands a 64-character key while knetworkmanager's character maximum is 63. Anyone know how to solve this?

---

### Post by wieman01 on 2007-10-29
> **TBerben said:**
> I have another problem related to WPA2: my router demands a 64-character key while knetworkmanager's character maximum is 63. Anyone know how to solve this?
Choose a passphrase that is shorter than 64 characters. Your router should let you do so, for sure. Although it might suggest 64 characters.

---

### Post by martin0641 on 2008-06-08
63 is the max that wpa2 can take for a keysize, it then uses it to generate the full 128/256 bit key via sha-1 

I use Hardy, and if I go in manually and set the WPA2 and stick in my key it works.  I save the settings and when I get back, it's on WPA, not WPA2.  Then I have to manually set it again, this is a bit annoying.  Ideas?

---

