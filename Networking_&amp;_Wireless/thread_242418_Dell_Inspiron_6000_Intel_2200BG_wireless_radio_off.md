---
title: "Dell Inspiron 6000 Intel 2200BG wireless radio off"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by happy-and-lost on 2006-08-23
OK, I've checked and the drivers are all installed for it, but I can't turn the radio on :( This Dell uses Fn-F2 to turn it on in Windows...

Apparently, if I patch my kernel with the following: "CONFIG_NET_RADIO=y", it'll work.

Thing is... I have no idea how to patch my kernel! Any help, or any other working solutions for this problem?

Cheers :)

---

### Post by funchords on 2006-08-27
I have an Inspiron 6000 with the 2200BG and the Fn-F2 works.  This is with Dapper 6.06 just installed.

The other Dell Fn keys work, too.

---

### Post by Muffy on 2007-07-24
I have the same problem. Any suggestions?

---

### Post by jggonz on 2007-08-08
I just had a similar issue with a Dell Latitude D600. The radio would not turn on by pressing the Fn+F2 key combination. After some time in diagnosing drivers, Dell's Quickset, and replacing the minipci (I had a new one), I went into the BIOS one more time and looked at page 3 of 7. This BIOS revision is A08. 

On the bottom portion of that page should be a section dedicated to the "Wireless Configuration" of the machine.

Make sure that the laptop is indeed recognizing the wifi card plugged into its minipci slot, and that the MiniPCI Status option is set to "Enabled"

Now, in order for the Fn+F2 key combination to work, the option labeled: "Wireless Control" is set to: "<Fn+F2>/Application> and that the "Wireless" option is set to "On"

This solved my issue and it might help in similar situations and with other DELL laptops.

---

