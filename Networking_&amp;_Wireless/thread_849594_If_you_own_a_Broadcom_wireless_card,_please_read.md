---
title: "If you own a Broadcom wireless card, please read"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2008-07-04
I spend a lot of time here trying to help people get their wireless going in Ubuntu.  One thing that would make it easier for us to help each other on the forums, and for new users to help themselves, is to have a comprehensive database of Broadcom chipsets and whether/how well they're supported by the b43 and bcm43xx drivers.  As far as I know, comprehensive documentation like this does not currently exist.

I know that there are lists put out by the developers regarding which chipsets are supported, but just because the b43 developers think their driver will work with a certain card doesn't necessarily mean that it really will, in my experience.  Furthermore, I've read of lots of people for whom the b43 driver sort of works, but either has unacceptable signal strength or drops connections arbitrarily.  The same is true for bcm43xx.

Consequently, it would be great if there were a list somewhere with the lspci output for each model of Broadcom card and a definite answer as to whether it is supported by b43 and/or bcm43xx and/or ndiswrapper, as well as any special steps that are necessary to get it working.  This would help to avoid guesswork when trying to help new users get their wireless card working, and would help people to configure wireless themselves without having to start threads here. 

If everyone who owns a Broadcom chipset replies to this thread, it would be easy to quickly build a working database of driver compatibility.  I propose this template:

**1. your Ubuntu release** (Hardy, Gutsy...)
**2. name that your card is sold under** (e.g. "Linksys XXX a/b/g"...), if you know it.  Revision number is also important, if applicable.
**3. lspci output for your card**
**4. drivers that you are *certain,* based on your personal experience, work with this card (b43, bcm43xx and/or ndiswrapper)**.  If ndiswrapper, it would be nice to link to the Windows drivers that you used.
**5. any special steps required to make the card work**...in other words, did you have to do anything besides check the box in Hardware Drivers (aka Restricted Drivers in Gutsy)?
**6. anything else that would be useful to know**...e.g. does the connection become flaky if you're not really close to the wireless access point?  Are you unable to connect with WPA?

If this thread gets responses, we can build a database and put it in the [community documentation]("https://help.ubuntu.com/community/") somewhere.

If you own a Broadcom card that works on your computer but aren't sure how to get all of the information above (e.g. you don't know what lspci means or how to tell which driver you're using), feel free to ask.

I think this would help clear up a lot of confusion regarding the different Broadcom drivers and chipsets.  If you have five minutes, please take the time to respond in order to save future generations some headache.

---

### Post by kevdog on 2008-07-04
I think Jamie Jackson has compiled an extensive list for ndiswrapper -- although not included are all the chipsets, its very extensive none-the-less.  That is a starting point.  Its an excellent thread in the wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by pytheas22 on 2008-07-04
Thanks for that link.  It does look like a pretty comprehensive list.  It would be nice if it could be expanded, however, to also cover bcm43xx and b43.  These days only a handful of Broadcom cards still *need* ndiswrapper to work.  Many will work with ndiswrapper *as well as* bcm43xx or b43, but it's always better to use the native drivers where possible.  So it would be nice to know which cards are supported by which native drivers.

Also, I think that it's confusing to put a page about ndiswrapper under WifiDocs/Driver/bcm43xx/Feisty_No-Fluff.../WifiDocs/Driver/Ndiswrapper would be a better place.  bcm43xx is *not* ndiswrapper and has no direct relationship with ndiswrapper.  There seems to be a lot of confusion with users thinking that ndiswrapper either only applies to Broadcom cards, or that it's the only (or preferred) way to get Broadcom cards working.  For instance, right at the top of the [community documentation page for ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") is a suggestion to try using bcm43xx as an alternative to ndiswrapper.  Not only is this outdated (since Hardy uses b43, not bcm43xx), but it's completely misleading and confusing for people who don't have Broadcom cards.  If I'm a new user trying to figure out why my Intel or Atheros or Ralink card isn't working, reading about bcm43xx and seeing no results is only going to frustrate me--especially if I don't know which chipset my card uses, as most new users don't.

So any volunteers for information about your Broadcom card and b43/bcm43xx?

---

