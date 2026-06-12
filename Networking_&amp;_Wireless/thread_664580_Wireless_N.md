---
title: "Wireless N"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by Meph1st0 on 2008-01-11
Anyone having any luck with 802.11n networking yet?  Just curious.  If so, what equipment did you get?

---

### Post by Junglizer on 2008-01-11
Haven't purchased anything myself as its still in Draft-N (Draft 2.0 based off of TGn's 1.10 rework, which means a reflash will probably save you from having to buy all new hardware once 802.11n is fully ratified.) But I have no need for N devices anyways. Look! Look! I'm rambling!

---

### Post by Meph1st0 on 2008-01-11
dang....,....oh well.

I guess I'll keep waiting. :)

---

### Post by MaindotC on 2008-01-12
> **Junglizer said:**
> Haven't purchased anything myself as its still in Draft-N (Draft 2.0 based off of TGn's 1.10 rework, which means a reflash will probably save you from having to buy all new hardware once 802.11n is fully ratified.) But I have no need for N devices anyways. Look! Look! I'm rambling!

I haven't read the IEEE docs yet, but I sat in on some of the meetings that the engineers were having to upgrade our campus network to N and they mentioned that one of the provisions of the standard is that all hardware must be backwards compatible.  For example, if you have an N access point, it MUST be compatible with G adapters in order to be 802.11n compliant.

---

### Post by Meph1st0 on 2008-01-12
That does remind me of another question I had.  I too had heard that it's supposed to be backward compatible with G adapters.  However, G networks are also backward compatible (generally) with B adapters.  But the caviat is that if there are any B adapters on a G network then the entire network has to slow down to accomodate the B adapter.  Will that be the same case with N networks that have G adapters?  Will an N network have to slow down to accomodate a PC with a G card?  

If that's the case then in order to have a fully N network you've got to replace every NIC on your home network which would be expensive.  And then there are other devices on my network that can't have their wireless cards upgraded.  For example, I've got a brother printer that has a built in G card that I use.  I've also got a Wii and a Tivo that can only use G network cards.  Am I stuck with G networking in that case?

It'd be cool if I could transfer files between two pcs that have N cards at full speed and then only slow down if I'm transfering files to a machine that happens to have a G card in it.

I hope all that was understandable.  I might have rambled a little too much there.

---

### Post by MaindotC on 2008-01-13
I say it will not affect speed transmission and my reasoning is that I participated in speed testing for different protocols - http, ftp, smtp, and so forth.  We conducted tests on G adapters and N adapters.  A 20 meg file uploaded with G took like 20 mins.  N took 8 mins.  They were used on the same access point, and although I doubt this inhibited the results I should specify that transfers were not conducted at the same time.  Btw - our university is Morrisville State College and documentation of our implementation is on Network World.

I know that's not a definite answer from an IEEE representative, but does that give you some comfort upgrading to N?

---

### Post by kegobeer on 2008-01-13
Any G device on an N network will cause the entire network to slow to G speeds.  This is a well documented issue.  There are also no drivers that allow N speeds for Linux as of yet.  The best you get is G speeds with N devices.

---

### Post by MaindotC on 2008-01-13
Could you provide some links of the documented issue?  Thank you.

---

### Post by Meph1st0 on 2008-01-22
wow, not cool.

---

### Post by MaindotC on 2008-01-22
> **Meph1st0 said:**
> wow, not cool.

Don't count your chickens - I find it hard to believe the speed of a network is dependent on any one node.  I'm still waiting for his "well documented" references.  According to him, anytime I want to slow down someone's wireless network I just use an 802.11a adapter and watch the frustration on all the other users.

---

