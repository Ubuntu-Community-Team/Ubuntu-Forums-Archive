---
title: "length of WEP 64/128-bit ASCII key"
date: 2008-01-23
forum: Networking &amp; Wireless
---

### Post by Pitt Stains on 2008-01-23
Hi,

I'm struggling with the network manager.  My network requires a key that is of the WEP 64/128-bit ASCII type, open system.  I have set up at least two other laptops this way, but not without trouble.

The main problem is this: the network manager appears to expect the key to be either 5 or 13 characters long; if the key is any other length, the "Login to network" button remains greyed out.  My key is 26 characters long.

I think this might be some kind of bug.  With each of the other two laptops I've set up here, I encountered the same scenario but found that after attempting to log in multiple times using the other available choices (WEP 128-bit passphrase, etc.), suddenly the WEP 64/128-bit ASCII lights up when I enter my 26-character key.

Has anyone else experienced this?  If so, how did you get around it?  I imagine the WEP key and ESSID are stored somewhere in a text file, and I wouldn't mind editing that manually to bypass what appears to be a bug in the GUI.

And of course, if I am wrong about something, someone please set me straight.

Thanks,
Pitt

---

### Post by schaumkeks on 2008-01-24
> **Pitt Stains said:**
> I'm struggling with the network manager.  My network requires a key that is of the WEP 64/128-bit ASCII type, open system.  I have set up at least two other laptops this way, but not without trouble.

The main problem is this: the network manager appears to expect the key to be either 5 or 13 characters long; if the key is any other length, the "Login to network" button remains greyed out.  My key is 26 characters long.

I think this might be some kind of bug.  With each of the other two laptops I've set up here, I encountered the same scenario but found that after attempting to log in multiple times using the other available choices (WEP 128-bit passphrase, etc.), suddenly the WEP 64/128-bit ASCII lights up when I enter my 26-character key.

Has anyone else experienced this?  If so, how did you get around it?  I imagine the WEP key and ESSID are stored somewhere in a text file, and I wouldn't mind editing that manually to bypass what appears to be a bug in the GUI.

And of course, if I am wrong about something, someone please set me straight.

The 26 character key you have must be the hexadecimal representation of a WEP-128-bit key. So you have to select WEP 64/128-bit HEX in NetworkManager dialog.

You can easily convert this one to its ASCII representation. Group all 26 characters into pairs with a leading "\x" and write them like this:
```
echo $'\x33\x33\x34\x34\x35\x35\x36\x36\x37\x37\x38\x39\x39'
3344556677899
```
They ASCII key can obviously be used better by human beings.

The other way around you can convert a WEP-128-bit ASCII key to hex via:
```
echo -n '3344556677899' | od -An -t x1 | tr -d ' '
33333434353536363737383939
```

Bye, Sven

---

### Post by alauro on 2008-03-19
Thank you Thank you Thank you. I finally put in the right keywords for my search and found this post which finally helped me use the network manager to connect to a wireless network. I have used wicd but lately it was causing problems and this post solved my issue. Thank you!

---

### Post by thisisunsane on 2008-05-27
> **Pitt Stains said:**
> Hi,

I'm struggling with the network manager.  My network requires a key that is of the WEP 64/128-bit ASCII type, open system.  I have set up at least two other laptops this way, but not without trouble.

The main problem is this: the network manager appears to expect the key to be either 5 or 13 characters long; if the key is any other length, the "Login to network" button remains greyed out.  My key is 26 characters long.

I think this might be some kind of bug.  With each of the other two laptops I've set up here, I encountered the same scenario but found that after attempting to log in multiple times using the other available choices (WEP 128-bit passphrase, etc.), suddenly the WEP 64/128-bit ASCII lights up when I enter my 26-character key.

Has anyone else experienced this?  If so, how did you get around it?  I imagine the WEP key and ESSID are stored somewhere in a text file, and I wouldn't mind editing that manually to bypass what appears to be a bug in the GUI.

And of course, if I am wrong about something, someone please set me straight.


I appear to have a sort of similiar issue.  I previously had 7.04 and had entered a 128bit WEP HEX key into the keyring via Network Manager to connect to a wireless network.  I upgraded to 7.10 a bit ago, but haven't attempted to add a new WEP key until tonight.  I can still connect to the WEP network I had previously set up, but I can't add a new network with a WEP key.  Well, I can, but only if it's a passphrase.  When I select 64/128 HEX key the "Login to Network" button is grayed out unless there are exactly 10 letters in the text field.  I think it's only wanting to accept a 64bit key.  For 64/128 ASCII the button is always grayed out.  With a Windows machine I can connect to the network with the 26 character hex key without incident.

Any help would be much appreciated.

---

