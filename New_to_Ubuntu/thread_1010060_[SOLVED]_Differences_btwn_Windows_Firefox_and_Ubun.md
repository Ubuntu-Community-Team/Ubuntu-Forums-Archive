---
title: "[SOLVED] Differences btwn Windows Firefox and Ubuntu Firefox?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by FountainDew on 2008-12-13
I have two minor quirks with Firefox in Ubuntu compared to Windows. For example, why does the BACKSPACE button no longer take you back to the previous page? Where do downloaded files go when you choose the "Open with..." option?

---

### Post by binbash on 2008-12-13
if you want your backspace button works like windows : 

write about:config
and search for backspace
change browser.backspace_action to 0

---

### Post by Kareeser on 2008-12-13
Another difference is the switch "browser.urlbar.clickSelectsAll", which decides what to select when you click the address bar once. In Windows, the entire address is selected (like in IE as well). In Ubuntu's Firefox, this is turned off by default, and *double-click* selects the entire URL.

---

### Post by FountainDew on 2008-12-13
thanks for the quick replies, i actually didnt know about the click select thing. thanks for that tip and the tip about getting backspace to work. :)

---

### Post by mister_pink on 2008-12-13
Files downloaded when you select "Open with..." mostly go to the /tmp directory. They should get deleted when you close the program you opened them with or sometimes when you end your firefox session.

---

### Post by lazylew on 2008-12-14
> **binbash said:**
> ...
write about:config
and search for backspace
change browser.backspace_action to 0
I see it solved the question for FountainDew, but I'm afraid I have the same question and do not understand the reply.
Where do I write it? I tried "about:config" in terminal but that's not it apparently.

---

### Post by DrSkalpell on 2008-12-14
lyzylew:
You write "about:config" in the url field in firefox

---

### Post by TVTrukChik on 2008-12-14
You type it in the Firefox address bar... where you'd normally type a URL.

---

### Post by lazylew on 2008-12-14
> **TVTrukChik said:**
> You type it in the Firefox address bar... where you'd normally type a URL.
wow, that brought me to a place I've never been :-)

the operation was successfull 
(wondering if there's a reason the backspace usage for browsing back is is not default; it seems so logic and handy I don't want to miss it)

thank you people!

---

### Post by jay li on 2008-12-14
In case you want to make an interval within textarea, what you gonna do?

---

### Post by lazylew on 2008-12-14
> **jay li said:**
> In case you want to make an interval within textarea, what you gonna do?
ehm... in case that question is addressed to me; I don't understand it, really

I just checked in terminal as well as other places, and the backspace still works for deleting text to the left - guess I misunderstand you?

---

### Post by jay li on 2008-12-14
I meant in firefox not other applications.

---

### Post by lazylew on 2008-12-14
> **jay li said:**
> I meant in firefox not other applications.
I see, well it still works when working on a text, be it the search box or typing an email; no problem :p

---

### Post by jay li on 2008-12-14
Thanks.

---

### Post by vikrant82 on 2008-12-14
Why not use standard shortcuts like Alt+Left or Alt+Right keys,

---

### Post by adobrakic on 2008-12-14
One button is easier to press than two.
:p

---

