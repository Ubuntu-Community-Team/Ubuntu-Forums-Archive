---
title: "Lenovo t60p leap + wpa + open works but wep fails"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by hstenzel on 2007-07-07
Greetings--

I have a Lenovo t60p with Ubuntu 7.04.  A few weeks ago I was able to successfully connect with leap, wpa, wep, and open; then wep broke.

I tried all sorts of things to fix it -- config with iwconfig, with wpasupplicant, with interfaces file,  etc.  I used various iwpriv commands.  None of the tricks that have worked before had any success whatsoever.

So, as a debug measuere, I booted the 7.04 desktop livecd.  I tried to configure the atheros -- still no luck; would work with open or wpa, but not with wep (had no access to leap at that time).  This surprised me since I had was successfully using wep before the ordeal started.

Also as a debug measure, I took the old Cisco Aironet 350 (airo_cs driver) card from another laptop and tried it.  It only supports open and wep, but open works and wep fails *on the t60p.*  This same card works fine on other machines (with Ubuntu, from 5.x through 7.04).  Similarly, only wep works on the t60p   Same behavior from the live cd as from my current setup.

So, it can't be the card -- see the same behavior with two different cards.
It can't be a broken install -- same behavior with livecd and installed version.
It can't be that it never worked -- it clearly did.

The only common denominator is the machine, why would it only affect wep on two different wireless cards?

I appreciate any insights, thanks.

 --Harley

---

