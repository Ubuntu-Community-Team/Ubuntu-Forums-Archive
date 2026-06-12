---
title: "No Firefox"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-02-08
Firefox shows up in installed programs, the icon is present, when I click on it the searching sign appears, after 10sec it just returns to mouse cursor , but FF does not show on screen.

Chrome loads as normal, but if I try to import anything from FF to chrome it tells me not possible whilst FF is running and to close it. :confused: :confused: :confused:

Don't know if this makes sense.

---

### Post by Blutkoete on 2011-02-08
Maybe Firefox has problems on start-up.

Would you mind opening up a terminal (in the menu, 'Utilities') and call *firefox* from there? That might give you an error message what is going wrong.

---

### Post by Robert1305 on 2011-02-08
Thanks Blutkoete, but having only just started using Linux not sure how to use terminal. not mastered exact commands.:rolleyes:

---

### Post by Joeb454 on 2011-02-08
You simply need to open a terminal (Applications > Accessories), and then type ```
firefox
``` then paste the output of that here :)

You can paste the output as it appears by surrounding it in [noparse]```
 
```[/noparse] tags.

---

### Post by migs73 on 2011-02-08
And the easiest way to get the 'code' tags is to click on the # button a the top of the message entry box (see below)

---

### Post by Robert1305 on 2011-02-08
Thanks Joe but when I do as you say it tells me "[COLOR="Red"]command not found[/COLOR]"

---

### Post by Lucradia on 2011-02-08
> **Robert1305 said:**
> Thanks Joe but when I do as you say it tells me "[COLOR="Red"]command not found[/COLOR]"

Have you installed a development release recently?

---

### Post by jonny163 on 2011-02-08
If you go in the "Ubuntu Software Centre", click "Installed Software" and find Firefox (it is labelled in mine as "safe and easy web browser from Mozilla". 
Try uninstalling it and then reinstalling it from the Software Centre or Terminal

From Terminal:
```
sudo apt-get install firefox
```

And enter password when prompted

---

### Post by Robert1305 on 2011-02-08
Thanks jonny will try that, one thing I forgot to add, when I first switch my PC on the Firefox browser opens and functions OK for a few minutes, but the first time I close Firefox that's when It refuses to open again

---

### Post by Robert1305 on 2011-02-08
I was going to try what jonny suggested when I noticed that there were two FF extensions installed so I removed one of them, before I could see if it had made any difference we had a power cut, the cut lasted for about 5mins, when I restarted my PC everything worked OK, and the FF problem seems to have been resolved.

Did removing the extension do the trick or was it the power cut, will never know, but whatever I'm a happy bunny. :lolflag:

---

### Post by migs73 on 2011-02-08
What was the extension? Just in case anyone else has a similar problem. (don't think I'll tell them to switch off the power whilst removing though!!!)

---

### Post by sydbat on 2011-02-08
> **Robert1305 said:**
> I was going to try what jonny suggested when I noticed that there were two FF extensions installed so I removed one of them, before I could see if it had made any difference we had a power cut, the cut lasted for about 5mins, when I restarted my PC everything worked OK, and the FF problem seems to have been resolved.

Did removing the extension do the trick or was it the power cut, will never know, but whatever I'm a happy bunny. :lolflag:Most likely the removal of the add-on. There are some that just mess with some peoples Firefox for reasons unknown.

---

### Post by cyb3r_sn4k3 on 2011-02-08
Last time I checked power cuts only made things worse :P

---

### Post by Robert1305 on 2011-02-08
> **migs73 said:**
> What was the extension? Just in case anyone else has a similar problem. (don't think I'll tell them to switch off the power whilst removing though!!!)

Just labelled FireFox extension, with this underneath.............

This is a transitional dummy package to ease the migration from the ubufox to the new xul-ext-ubufox package. You can remove it safely.

---

### Post by jonny163 on 2011-02-09
Reminds me of that red tag that goes underneath batteries that you have to remove before you can use them lol
Glad its sorted

---

