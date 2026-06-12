---
title: "Need help with wireless networking!"
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by ArachnoKnight on 2005-05-09
Hello everone, this is my first time posting here, and I am in dire need of help.  I need to get my computer that is running the newest version of Ubuntu to network with my 2 other computers running Windows XP using my Linksys router.  What I really need is to get my computer that is running Ubuntu back on the net, like it used to be when I had Win XP on it and it was networked with everything else.  I have no idea how to use Ubuntu, for this is my first time ever trying Linux.  I like it so much better that Windows.  So, if anybody could point me to a site where there are detailed instructions on how to do this or if you could make the instuctions, that would be great!  Explain it to me like I'm a 2 year-old.  I'm only 17 and REALLY need help with all of this networking crap.

---

### Post by Zelut on 2005-05-09
Well first of all I hope you dont get discouraged when you run into problems with linux / ubuntu.  Things generally tend to take a little more work compared to Windows but we think its worth it :)

Anyway, concerning wireless you may be limited.  Wireless networking isn't supported very well in linux so you'll only be able to get it to work if you have a supported card.  I actually have a emachines notebook with built-in 54g wireless that just wont work under ubuntu / linux.  Its too bad, but thats just how it is right now.

Here is a list of supported wireless cards.  If yours is on the list we'll be able to set you up.  If not... well, you'll need to find a wired solution until it is supported.

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) (supported hardware - if you see tested/supported on your card you're ok.)

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/#whard](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/#whard) (great resource)

Hope this helps for now.  Happy to answer any other questions that I'm able.

---

### Post by ArachnoKnight on 2005-05-09
My router is a Linksys 802.11g WRT54 S.  It's not on the list so does that mean that I cannot network them?

---

### Post by Zelut on 2005-05-09
another use actually pointed out nsiswrapper ([http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)) which attempts to use windows drivers for use under linux.  I haven't used it yet but I'm going to give it a try now.  That may be a solution for you...

---

### Post by ArachnoKnight on 2005-05-10
Yup, I still need help.

---

### Post by Zelut on 2005-05-10
Well since looking into this issue more I've managed to get my wireless to work using ndiswrapper on my emachines notebook (54g onboard broadcom shipset).  Take a look into ndiswrapper (google it) and see what support you can find there.  I'm sure they'll be more able to help you with something this specific.

---

