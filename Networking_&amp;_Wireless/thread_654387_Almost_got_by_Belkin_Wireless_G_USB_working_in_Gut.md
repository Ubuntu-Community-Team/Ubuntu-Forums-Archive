---
title: "Almost got by Belkin Wireless G USB working in Gutsy"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by Palcrypt on 2007-12-31
I used ndiswrapper to install the drivers off the  Belkin cd. I can see the wireless network just fine, and when I try access it I input the WEP security key and it keeps prompting me to reinput the key without actually connecting. Any ideas on how to fix this. I know I'm inputting the correct WEP key. I've double and triple checked it.

---

### Post by ModelM on 2007-12-31
Try enclosing the key in double quotation marks when you enter it. That's bitten me a couple of times.

---

### Post by Palcrypt on 2007-12-31
nope. that didn't work. it doesn't even let you enter double quotes in the hex key field.

---

### Post by Palcrypt on 2007-12-31
just an update: I read that some people had more success when using wicd, so I installed that and I'm still unable to get an IP. I can see the wireless network just fine, but it won't obtain an IP.

---

### Post by Palcrypt on 2007-12-31
anyone else have this kind of problem ever?

---

### Post by Palcrypt on 2008-01-06
seriously. My two options right now are boot into Ubuntu and run a long cable out to my living room if i want to be online or just run windows. I really need help with this. Any suggestions would GREATLY be appreciated.

---

### Post by ModelM on 2008-01-06
I'm running WPA here & don't know much about WEP. If you're entering a key in hex, have you tried preceding the key with 0x to designate hexadecimal? This is only a guess, but perhaps the key is correct but the software is expecting a different format like the 0x designator, or separating the bytes  with spaces - 0f 33 2b instead of 0f332b. I'm only guessing here & you can have your money back if it doesn't work...

:)

---

### Post by Palcrypt on 2008-01-07
I'm not really sure what I did, but it's working now. I removed WICD and it started working. I'm just not going to mess with it now :)

---

