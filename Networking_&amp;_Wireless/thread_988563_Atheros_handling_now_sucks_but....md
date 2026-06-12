---
title: "Atheros handling now sucks but..."
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2008-11-20
So, back in the days of Edgy 6.10, I pulled out a Broadcom mini-pci card in favor of an Atheros card.  Of course it just worked!

So now we have Intrepid... and take it what it is worth, the whole Atheros thing is just a bumbled mess.  You have ath5k, and you have madwifi ad neither seems to be able to manage a connection.  I have blacklisted, modprobed and rmmoded until my poor machine doesn't know what should and should not be loaded:confused:  I even went for the hand compiled madwifi-hal latest.  Worked until last week.  Update and bam, I just can't connect.  It stalls on getting an ip.  Does this from command line too.  Yes, I recompiled and reinstalled. %$!&

Put the Broadcom adapter back in.  It has been in storage for maybe two years.  Since Hardy, I have seen that ndiswrapper is not handled correctly or more accurately, not in the proper sequence.  None of the workarounds seems to work around it for me.

However, I will give props to the Hardware Manager and its use of the fw-cutter and firmware.  It works.  Today anyway.  It seems to manage the device such that it "shuts down temporarily" when no traffic is happening.  Not so bad... maybe my battery will be spared.

---

### Post by aysiu on 2008-11-20
I know you tried *ndiswrapper* with the Broadcom. Have you tried it with the Atheros, too?

I have an Atheros wireless in my Eee PC and have had no luck with madwifi. ndiswrapper is the only thing that'll work for it on Ubuntu.

---

