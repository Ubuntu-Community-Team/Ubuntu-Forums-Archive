---
title: "Firefox 3.5 question"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by Messyhair42 on 2009-08-24
a few weeks ago i installed firefox 3.5 on 9.04. recently i've been having a weird thing happen, i normally open links in tabs with a middle click, but if i middle click on blank space or even text (something that's not a link) it takes me to an old page i've viewed, possibly whatever i have in my clipboard but not totally confirmed on that. i find this very annoying when i miss the actual link or something. this happen to anybody else?

---

### Post by wirate on 2009-08-24
me too

---

### Post by zkriesse on 2009-08-24
I've not had that happen to me on Ubuntu when I had 3.5 on it, but now I'm running 3.0 Figured it's just safer that way.

---

### Post by zkriesse on 2009-08-24
Hey waqar....you link in your signature? if you highlight the text awesome video...there's an option in the signature edit to add a link to it. you click that and then you can add a link to the text so it's click-able and it'll go right to the page.

---

### Post by aysiu on 2009-08-24
Try typing ```
about:config
``` in the address bar and then typing ```
middlemouse
``` in the filter bar, then changing *middlemouse.paste* to *false*.

---

### Post by bodhi.zazen on 2009-08-24
How did you install Firefox 3.5 ?

I found the version in the repositories was buggy, easier to download the binary directly from mozilla (and simply put it in /usr/local/bin (the whole firefox directory is in /usr/local/bin/firefox).

---

### Post by johngilda87 on 2009-08-24
can we use both new and old firefox version together?

---

### Post by cataztrophe on 2009-08-24
@john
um...maybe, you can try it!

@aysiu
thnx for share! :D

---

### Post by Messyhair42 on 2009-08-24
> **aysiu said:**
> Try typing ```
about:config
``` in the address bar and then typing ```
middlemouse
``` in the filter bar, then changing *middlemouse.paste* to *false*.

no change

@bodhi.zazen: i got the .tar.gz from the mozilla website and used the method described via psychocats

---

