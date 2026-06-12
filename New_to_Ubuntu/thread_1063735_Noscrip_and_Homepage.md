---
title: "Noscrip and Homepage"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by dave r on 2009-02-08
Been on Ubuntu a few weeks now and its very good. However having read up on the security side of Ubuntu I would still like my surfing to be a little more secure and run Noscript. But I have a problem. Noscript blocks my home page. I am using [http://www.wunderground.com/wundermap/?lat=52.36999893&lon=-1.48000002&zoom=10&pin=Coventry%2c%20United%20Kingdom](http://www.wunderground.com/wundermap/?lat=52.36999893&lon=-1.48000002&zoom=10&pin=Coventry%2c%20United%20Kingdom) as my homepage. Noscript blocks this even if I put it on my white list. I can't seem to find a way to stop it doing this. As a result I have stopped using Noscript for now. Does anyone here know how to stop it doing this?

---

### Post by egalvan on 2009-02-08
I run noscript on firefox,
went to that page, hit the "temporarily allow all this page"
allowed the site to open.
displayed some weather map

I had to hit that option three times, btw.

Might be something on your noscript options

ErnestG

---

### Post by Mud.Knee.Havoc on 2009-02-08
> **dave r said:**
>  Noscript blocks this even if I put it on my white list. I can't seem to find a way to stop it doing this. As a result I have stopped using Noscript for now. Does anyone here know how to stop it doing this?

Are you **just** putting wunderground.com into the whitelist?  If so, that's probably not enough.  If you go to that site, right click the NoScript "S" at the bottom right of the browser.

You should see that it's running scripts from wunderground.com, tacoda.net (which I think is just for tracking/advertising), wxug.com, etc.  Some of these extra scripts may be related to advertising, but some may be necessary for drawing the map and other things.  

If you're writing any addresses in the whitelist, you're doing it wrong. :)  You just need to go to that site, right click the "S" and select "Allow ____" (add name of site).  This will make sure that it adds it to the whitelist properly (no spelling mistakes or anything else that may happen if you write your own whitelist).  I just right clicked and added wunderground.com and it seemed to draw the map fine.  I didn't bother with the others - I may be missing some other functionality on the site, though.

---

### Post by dave r on 2009-02-08
Thanks lads. Sorted.

---

