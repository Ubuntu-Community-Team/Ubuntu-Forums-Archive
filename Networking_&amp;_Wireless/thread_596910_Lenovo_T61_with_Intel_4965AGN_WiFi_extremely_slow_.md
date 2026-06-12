---
title: "Lenovo T61 with Intel 4965AGN WiFi extremely slow wireless speeds"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by kudar on 2007-10-30
wired connection is fine(of course its a different interface)  someone else must be experiencing this problem.  i have tried disabling ipv6 and upgrading router firmware.  been going at this for 2 weeks now. any info is appreciated.

---

### Post by jpeach on 2008-05-15
Did you ever figure out the problem?  I am running Hardy on the some equipment as you and getting the same problem.  dl and ul both max out at around 18 kbytes/sec no matter what the network is.

---

### Post by Kevbert on 2008-05-15
How many bars of signal can you see ?  Low signal - try relocating router.
Can you see other networks ? If yes, try changing to another channel.  If no, are you near any cordless phones (not cell phones), microwave ovens (anything that works at 2.4GHz).

---

### Post by jpeach on 2008-05-15
Kevbert

Depending on what network I am on, there is 50%-100% power.  So that is not the issue.

Again, depending on the network I am on I can see a few to 20+ networks.  That does not seem to make  a difference.

On my router I have changed channels and that has not helped.  In North America we are only allowed to use channels 1-11 (I think).  However, my modded router supports up to channel 14 (I think).  These illegal channels should have less noise on them.  However, changing it to an illegal channel did not help.

---

### Post by Kevbert on 2008-05-15
Hi again.  I've been looking around for a solution on Google and found this:

> IBM power manager software that was controlling the power on my wireless card. I created my own power location, kept the wireless adapter settings to Maximum Performance and it has done well since.

It seems to be a hardware/setup related issue on these PCs and is not a problem with the OS.

Hope this helps.

---

### Post by jpeach on 2008-05-15
Kevbert

I located the thread you just quoted and read it carefully.  They were talking about problems under Vista not Ubuntu/linux. 

[http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=4088&view=by_date_ascending&page=1]("http://forums.lenovo.com/lnv/board/message?board.id=T_Series_Thinkpads&thread.id=4088&view=by_date_ascending&page=1")

It seems that going from Vista to Vista SP1 fixed their problem.  As for changing the power settings on the wireless card... I am clueless on how to do that in Ubuntu.  I have poked around the network and power settings and could not find anything.  Google was no help either.  Do you have any suggestions on how to create a "power location, kept the wireless adapter settings to Maximum Performance"?

---

### Post by Kevbert on 2008-05-15
On the thread they mention IBM power management software.  Maybe this is restricting your speeds as the modem is in low power mode.  How to get round this may be a problem.  I've noticed that there are many different makes of laptop which use this wifi modem (eg Sony) and many people are having your problem with many different OS including Vista, XP, Ubuntu, Gentoo.  Have you tried the linux driver on the Intel website ? see: [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")
It looks like the modem first came out when 802.11n was in draft/flakey but you should still get 802.11b/g speeds (but restricted by what the modem/router is connected to, wire/cable).

---

### Post by jpeach on 2008-05-15
Kevbert

That is actually an older driver (1.0.0) then the 1.2.0 that I am currently using.  From the link that you sent me I was able to find the Open Source Driver project and filed a bug with them [http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1669]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1669")

---

