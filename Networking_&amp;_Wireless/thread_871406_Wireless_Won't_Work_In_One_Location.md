---
title: "Wireless Won't Work In One Location"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by tdashroy on 2008-07-26
Okay so I am having a problem with my wireless.  I have a Dell 1420n and my wireless works at my house, which has WPA encryption, and it works anywhere public.  But, my problem is that when I go over to my girlfriends house the wireless has a WEP 128 bit encryption and when I try to log on the network manager comes up after a minute or so and asks me for the password again.  Any suggestions on how I might go about fixing this?

---

### Post by tdashroy on 2008-07-27
Is there any other information I might be able to give that might get me some replies?

---

### Post by dmizer on 2008-07-27
Well, if it works everywhere else except one location, odds are that the location is the problem rather than Ubuntu.

Try rebooting your girlfriends router.  Does the wireless setup have MAC filtering enabled?  What router does she have (make and model number)?  Is she running alternative firmware?

---

### Post by daleus on 2008-07-27
I had trouble at first with WEP, I hadn't realised (being a dunce) that My 128 WEP key was actually "HEX" and I had to set the type to "shared" not "open".

if I didn't set it to "shared key" it would ask me over and over for the key, just try double check the settings.

---

