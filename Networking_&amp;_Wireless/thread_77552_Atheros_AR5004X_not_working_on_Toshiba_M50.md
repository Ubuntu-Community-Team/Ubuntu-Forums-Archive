---
title: "Atheros AR5004X not working on Toshiba M50"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by netdance on 2005-10-17
OK, I'm a bit of a noob.

After a very good experience with a Toshiba A45 and Ubuntu Hoary, I decided to buy another Toshiba.  Sadly, my experience this time isn't quite as good.

Specifically, I'm having a really odd problem with my wireless card.

The card itself is a Atheros AR5004X.

Breezy recognizes the card, I can see a ath0 device.  Everything seems to work, in fact, until I try to get a dhcp connection - I can't, and no mysterious incantation seems to be able to help me.

I suppose that this may be related to WEP, I don't currently have access to an open network, but I intend to try it tomorrow on one.

One other weirdness - in lspci, I can see that the card is recognized as a AR5212.  This is, of course, the wrong card.  I wonder if that's part of the problem?

Any suggestions?

I've taken a look at ndiswrapper, but there is no .inf file associated with the card, only a sys file.  Which doesn't work, of course.

Any suggestions gleefully accepted...  Any at all.

---

### Post by netdance on 2005-10-17
OK, it looks like the real problem is with the WEP.  

On an open network, I can connect no problem.

On a WEP enabled network, I'm having no luck at all.

I've double and triple checked the WEP password, but I'm getting no joy.  And no error messages either.

Anyone seen this?  Any suggestions?

---

### Post by netdance on 2005-10-17
OK, feelin' dumb.

I've found what the problem is:  in Hoary, there was only one option for WEP password.

In Breezy, there are two options:  Hex, and String.

My password was entirely numeric, so, silly me, I thought it might be a string. (i.e., It didn't have any A-F characters.)

If you tell network setup that it's a string, a "s:" is prepended to the WEP password in /etc/network/interfaces

If you tell network setup that it's hex, nothing is prepended.

So, if you're using a 2Wire Device (which is standard for Yahoo DSL in my area), this problem may bite you :-)

As for why I didn't notice before now - I have no idea.  I could have *sworn* that I checked this, but I guess I missed it somehow before now.

---

### Post by pcpinkerton on 2007-08-24
Well I can top that in my interfaces file I put 2wirexxx in lower case and could not for the life of me get it to work then I changed to UPPER CASE 2WIREXXX  and bingo !! it is working. hehe.

System details: Kubuntu Gutsy 7.10 AMD64
                       Acer Aspire 5100 AMD64 Turion 64x2 TL50
                       Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

Home Network:  AT&T 2Wire Gateway 


          cheers !!

---

