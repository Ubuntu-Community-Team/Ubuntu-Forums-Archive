---
title: "My wep key is too long to enter in ubuntu...any thoughts?"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by tmcarson1 on 2008-07-07
I have recently switched over to wireless.  Have a Linksys Wireless-B usb adapter.

I pull up the network manager, and when I put it to wep, which is what my router is set to for security, my wep code that the router gives me is 26 digits long, and only 16 fit in the key box in the network manager in ubuntu.

What am I doing wrong?  Driving me crazy! lol

:confused:

---

### Post by chili555 on 2008-07-07
Are you putting it in '40/128 bit Hex' which is where I believe 26-character keys go?

---

### Post by tmcarson1 on 2008-07-07
> **chili555 said:**
> Are you putting it in '40/128 bit Hex' which is where I believe 26-character keys go?

I don't remember seeing that as an option.

Will reboot Ubuntu and make a note of the choices the network manager offers me.  Will report back here shortly.

---

### Post by tmcarson1 on 2008-07-07
> **chili555 said:**
> Are you putting it in '40/128 bit Hex' which is where I believe 26-character keys go?

Ok, in ubuntu Hardy, the network settings box has the following options:

WEP Key (hexadecimal)
WEP Key (ascii)
WPA Personal
WPA2 Personal

I do not see any option to make it 128bit instead of 64bit for the WEP key.

Any further thoughts are greatly appreciated!

---

### Post by stchman on 2008-07-07
> **tmcarson1 said:**
> I have recently switched over to wireless.  Have a Linksys Wireless-B usb adapter.

I pull up the network manager, and when I put it to wep, which is what my router is set to for security, my wep code that the router gives me is 26 digits long, and only 16 fit in the key box in the network manager in ubuntu.

What am I doing wrong?  Driving me crazy! lol

:confused:

I recommend you use WPA or WPA2 for your wireless security.  WEP is easily cracked.  Then make your WPA passphrase at least 30 characters long with uppercase, lowercase, symbols and numbers.

---

### Post by tmcarson1 on 2008-07-07
> **stchman said:**
> I recommend you use WPA or WPA2 for your wireless security.  WEP is easily cracked.  Then make your WPA passphrase at least 30 characters long with uppercase, lowercase, symbols and numbers.

Thanks for the reply, but how do I tell my router I am going to use WPA instead of WEP?    I don't think I saw that option in my router's settings.

---

### Post by Thirtysixway on 2008-07-07
If WEP isn't an option on your router, see if there is a newer firmware verson available from the manufacturer.

---

### Post by tmcarson1 on 2008-07-07
> **Thirtysixway said:**
> If WEP isn't an option on your router, see if there is a newer firmware verson available from the manufacturer.

WEP is an option, but WPA is not.  Is that what you meant?

---

### Post by chili555 on 2008-07-07
Your 26-character WEP goes in WEP hexidecimal. Even though it looks loke it won't fit, just keep typing. It will all go in.

---

