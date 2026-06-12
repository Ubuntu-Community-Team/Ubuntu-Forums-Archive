---
title: "Cannot adjust lcd brightness on thinkpad R40e"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by stuckagain on 2009-05-24
Hi All,

I have wubi-installed Ubuntu 8.10 on an IBM thinkpad R40e laptop, dual booting with Winxp. The video/lcd brightness seems to be stuck at its maximum level (with power). I have tried out the following so far, without success -

1. blacklisting the video module (brightness flickers constantly! )

2. tried various echo commands suggested in this forum. I get a "not supported" or some such message.

sudo echo -n 50 > /proc/acpi/video/VID/LCD0/brightness

or

vim /etc/acpi/thinkpad-brightness-up.sh
echo 4 > /proc/acpi/ibm/cmos

3. keytouch software - The keytouch-editor does not recognize the brightness function keys while creating the keyboard file.

4. kmilo is an option, but it's only for KDE front-end.

5. FYI. 
/usr/share/acpi-support/IBM.config does not list any R40e model (mine is 2684RA7). Does this mean Thinkpad R40e is not supported by Intrepid? That would be a showstopper.

6. FYI. During start-up, I noticed the message - 

"thinkpad_acpi: CMOS NVRAM (0) and EC (1) do not agree on display brightness level."
-----------------------------------------------------------------------------------------------------

Any suggestions? Please go slow with the geek stuff as i am new to linux (and other operating systems).

---

### Post by stuckagain on 2009-05-24
Any takers? You can tell me your ideas for any thinkpad model - not necessarily R40e. I know it's an old one.

---

### Post by stuckagain on 2009-06-04
I found/noticed a workaround. The lcd brightness can be set in windows and it stays set for the linux session! The NVRAM value seen in the startup message gives this value.

---

