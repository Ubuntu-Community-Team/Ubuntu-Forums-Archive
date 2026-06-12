---
title: "http://-kol.deviantart.com/ not working"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by klerfayt on 2008-05-26
I can't access [http://-kol.deviantart.com/](http://-kol.deviantart.com/) for some strange reason. The page exists and at least one person on irc was able to access it because he was using windows.
exact error I get
[http://i29.tinypic.com/2lj1ap0.png](http://i29.tinypic.com/2lj1ap0.png)

---

### Post by prshah on 2008-05-26
> **klerfayt said:**
> I can't access [http://[color=red]-[/color]kol.deviantart.com/](http://[color=red]-[/color]kol.deviantart.com/) for some strange reason. The page exists and at least one person on irc was able to access it because he was using windows.
exact error I get
[http://i29.tinypic.com/2lj1ap0.png](http://i29.tinypic.com/2lj1ap0.png)

Works fine here; in the url shown, you have a hyphen; works if you remove that hyphen.

---

### Post by dashnak on 2008-05-26
I deleted the "-" from the url and it worked just fine

---

### Post by klerfayt on 2008-05-26
No you don't get it. If you remove - then you get to different page. It's supposed to be [http://-kol.deviantart.com/](http://-kol.deviantart.com/) with "-". And it works in windows apparently.

---

### Post by prshah on 2008-05-27
> **klerfayt said:**
> No you don't get it. If you remove - then you get to different page. It's supposed to be [http://-kol.deviantart.com/](http://-kol.deviantart.com/) with "-". And it works in windows apparently.

Well I tried replacing the "-" with "%2D" (Hex code for "-") and neither nslookup, ping, firefox or lynx could find the remote site. Guess someone with Windows will have to confirm whether it works or not; i doubt if it will.

---

### Post by klerfayt on 2008-05-27
I think I made this part clear:
I got two positive confirmations over irc that the page does work in windows

---

### Post by jetsam on 2008-05-27
Yep.  Works in Windows.

I think that leading hyphen is against some spec or another, and in an ideal world deviantart wouldn't allow it and Windows wouldn't resolve it either.

The page is sort of accessible through Google cache:
[http://209.85.141.104/search?q=cache:d3Hfzy6HVGwJ:-kol.deviantart.com/+%22http://-kol.deviantart.com/%22&hl=en&ct=clnk&cd=1&gl=us]("http://209.85.141.104/search?q=cache:d3Hfzy6HVGwJ:-kol.deviantart.com/+%22http://-kol.deviantart.com/%22&hl=en&ct=clnk&cd=1&gl=us")

If you want to see one of the sub links that also starts with "-kol" , you have to click on it, then paste the url into a Google search, then click on the cache result.   

I couldn't figure out a better solution.  It seems the Linux resolver doesn't like the hyphen.

---

