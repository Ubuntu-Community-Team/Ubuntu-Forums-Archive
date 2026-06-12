---
title: "Networking lessons learned from power surge"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by secdroid on 2007-03-02
Lost my electricity for approximately 1 second, apparently due to high winds.  Just long enough for computer, clocks, etc. to go down.

When computer rebooted, my Dapper (6.06) worked, except DSL download speed was poor.  Decided to boot a Live CD and do an fsck to check/fix filesystem errors.  The fsck found & fixed several errors.  Did a second fsck to verify and filesystem was pronounced "clean."

Rebooted Dapper and still had DSL download speed problem.  Checked DSL download speed using a test computer on another port of the same hub as the suspect box.  Test computer had normal speed.  Plugged suspect box into hub port just tested by test computer.  Suspect box still slow.

Did power down of suspect box.  Powered down hub & DSL modem/router for good measure.  Waited 30 seconds.  Powered up DSL modem/router, hub, and computer -- in that order.  No change.  Sigh...

Booted Dapper Live CD on suspect box and had difficulty getting DHCP address, even though I had been getting address dependably with installed Dapper.  Curiouser & curiouser!

Booted Puppy Linux Live CD on suspect box and couldn't get DHCP address.  Aha!

Powered down suspect computer, hub, and DSL modem/router for three minutes.  Powered up DSL modem/router, hub, and computer -- in that order.  Puppy Live CD got DHCP address and DSL download speed tested normal.  Booted Dapper on suspect box via HD and tested.  DSL download speed was normal.

Moral of the story: Hardware can get into a weird state due to power surges and a 30 second power down may not solve the problem.  Keep the equipment powered down long enough for the power supply capacitors to drain down all the way.

---

### Post by nyinge on 2007-03-02
Thanks!  Now I realize that merely rebooting the router may not be sufficient sometimes.  :)

---

### Post by secdroid on 2007-03-02
Additional moral: Wake-on-LAN NIC power down should be done by pulling the power cord, not just pushing the front panel power switch (as I did on the first, 30 second power down).

There is a small amount of juice supplied to a "powered down" motherboard so that things like wake-on-LAN and the front panel power switch work.  Unplug the computer's power cord, in order to be certain that the motherboard is fully powered down.

---

### Post by tturrisi on 2007-03-02
moral of the story is:  UPSs are worth every penny!

---

### Post by secdroid on 2007-03-02
> moral of the story is: UPSs are worth every penny!

True, but pricey.  Ideally I'd have a UPS for the networking stuff (location 1) and another for the computer (location 2).  Most businesses have the servers and principle networking stuff on UPS, but very few user workstations.  We home users are even less likely to use them.

Besides, I had a chance to learn something today. Priceless!!!  :)

---

### Post by nyinge on 2007-03-02
With 40 bucks, you can pick up a decent one for use with the monitor, computer and the router (if it is nearby).  I think it's worth it.

---

### Post by RandomJoe on 2007-03-02
If you keep a sharp eye out, UPSes can be surprisingly cheap.  I went by Office Depot the other day to pick up a new UPS for my office (I just started, and before I arrived they had basically no LAN infrastructure) and found one UPS that was supposed to be $130, but rang up $54.  900VA APC model!  I suddenly decided I needed another one here at home... ;)  Evidently this was the last of a previous-version of the same model.  The only difference I could find is the new version includes a filter for a cable line.

But the best deals have been freebies.  An astounding number of people and businesses _throw away_ UPSes rather than replace the worn out batteries.  I got two 1400VA APC SmartUPS from my last employer when the corporate IT folks just sent brand new UPSes and told us to get rid of the old ones.  These things run about $400-500 new, replacement batteries were a little over $100.  I also wound up with a few smaller units that various people in the office had picked up because they were tired of the power bumps, but abandoned after they got laptops and no longer saw a need.  (I did try to get them to use the things anyway, but no joy...  Oh well, my gain!)

I now have every electronic device in my house at the very least surge-protected but mostly all on UPS.  I haven't had a hardware failure on anything since doing this, which leads me to believe however "good" the power may seem, there is still enough noise, surges and sags to damage the electronics over time.  It also makes for killer uptimes on the server and router boxes in the back room! :)

---

