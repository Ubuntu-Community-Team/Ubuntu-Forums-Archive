---
title: "Prep for install where internet connection is Verizon DSL"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-05-29
I am going to wipe my g/f's XP machine (kids loading too much crapware on it and viruses) and load 10.04.

Question is, they use Verizon DSL and I seem to recall having to configure some special setup when they got it to make it work (had to use an install disk).

This machine connects wirelessly to a combo DSL modem and wireless router.  My guess is I shouldn't have to do anything special, just get the PC to connect to the router, correct?

---

### Post by jerrrys on 2010-05-29
wireless may have to be set, but yes you are correct, verizon software not needed

---

### Post by quadproc on 2010-06-10
> **Newbie2910 said:**
> ...
This machine connects wirelessly to a combo DSL modem and wireless router.  My guess is I shouldn't have to do anything special, just get the PC to connect to the router, correct?
I just finished getting run through the ringer with a Verizon DSL problem and finally getting a solution.  My problem is probably different than yours but the summary might be useful so here it comes.

I have a Verizon DSL connection at this location.  However, my ISP is an independent company.  Verizon supplies the phone service and the DSL link to their switching plant while the ISP supplies my Internet functions.  Originally, Verizon provided me with a Fujitsu DSL modem which worked fine.  After some years Verizon sent a different modem (a Westell 6100) to replace the Fujitsu because Verizon was changing their modems at their switching plant.  The new modem worked for about a year.

A few days ago I was unable to connect to any Internet site.  Troubleshooting the problem with my ISP, I finally learned that the Westell modem had failed in an unusual way: it worked fine on the Ethernet side, it worked fine on the DSL side (which is all that the ISP can test), but neither side could talk to the other side.  Replacing the modem fixed the problem, but ...

Replacing the modem turned out to be a big problem.  Verizon refused to replace the failed one.  I obtained a Verizon compatible modem from a local retailer and started to install it.  When I got to the section about PPPoE, I called my ISP to get the user/password and learned that the Verizon modem could not be used because my ISP does not do PPPoE (a technology which is becoming legacy).  So I had to get a different modem which did not require PPPoE.  In my case this is an Actiontec model.

So, there are several things to be learned from this story.  Probably the most important for you is to check with your ISP to be sure that your modem will be compatible with the ISP's setup.

quadproc

---

