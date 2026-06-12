---
title: "WTF, FIREFOX?!?!  YouTube won't work and browser occasionally goes grey."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Murderuption on 2009-03-08
Alright, I be lovin' Ubuntu thus far.  It's sleek, fast, and way easier to use than Windows.  It's the anarchist's OS!  

Except for one thing.

Firefox has been blowing some major *** on me.  YouTube won't work at all.  Whenever I try and load a video, the screen goes grey and I have to force quit.  This occurs every time.  In addition, the browser tends to go grey on occasion and I have to force quit.  

Any help would be greatly appreciated, my brothers (or sisters)!

Thanks.

---

### Post by st33med on 2009-03-08
Do you by any chance use the 64 bit Ubuntu? Have you downloaded the nonfree flash codec?

Also, I wouldn't blame it on Firefox because Flash is plain bloated and lame, but we all have to use it to watch YouTube and such, eh?;)

---

### Post by Murderuption on 2009-03-08
I'm running x86, not 64.  I've got the codec too.

---

### Post by sports fan Matt on 2009-03-08
What version of FF? Some people have reported the latest version as broken

---

### Post by Murderuption on 2009-03-08
I'm running 3.0.7

---

### Post by sports fan Matt on 2009-03-08
That version by alot of people has reported bugs and hiccups..

---

### Post by Murderuption on 2009-03-08
What are my alternatives?

---

### Post by metallicamike on 2009-03-08
do you have all of the gstreamer plugins from add/remove?

---

### Post by metallicamike on 2009-03-08
> **Murderuption said:**
> What are my alternatives?

epiphany or opera would work. but i don't use them so im not entirely sure

---

### Post by Murderuption on 2009-03-08
> **metallicamike said:**
> do you have all of the gstreamer plugins from add/remove?

Say what? :confused:

---

### Post by metallicamike on 2009-03-08
:lolflag: go to applications->add/remove programs and seach gstreamer and hit the checkboxes on anything that says gstreamer plugin in it, and check ubuntu restricted extras. 
P.S. Grats me on my 200th post!!!!!!\\:D/

---

### Post by IsmailBhai on 2009-03-08
use opera. its nice.

---

### Post by Bearly Able on 2009-03-08
Uninstalling the mozilla-plugin-gnash worked for me, but I'm using 8.04.  Still, it might be worth a try.

---

### Post by fly2thesun on 2009-03-15
I was having similar problems. Thanks to the suggestions in this thread, I was able to make it work. ( Firefox 3.0.3, Ubuntu 8.10 on Pentium3 )
I installed flashplugin-nonfree and removed mozilla-plugin-gnash.
But that was not enough.
It finally worked when I removed swfdec-mozilla.

At least in my case, both mozilla-plugin-gnash and swfdec-mozilla were crap. Mozilla-plugin-gnash was waiting forever to start playing. swfdec-mozilla stalled the whole browser. Only flashplugin-nonfree worked, and I had to remove the other two in order to force firefox to use flashplugin-nonfree.

---

### Post by Bryantos on 2009-03-15
As far as the browser going grey when *not* on Youtube, try clearing your private data. **ctrl+shft+delete** is the shortcut, or you can also do it through **Tools -> Clear Private Data **

If you do not want to lose all of the pages you have looked at (Thereby not allowing you to use the back button to view previous pages and/or check your history), then uncheck the browsing history box.

If you are logged in to a site and do not want to have to re-login, then uncheck the cookies box.

You will *easily* see a notable increase in browsing speed after you clear the private data.

Hope that helps!

---

### Post by Robert505189 on 2009-03-15
I have tried opera don't care for it firefox works fine I had a similar problems inculing a stupid play icon in place of just playing the  flash which drove me nut but once you get all your plugins there should be no probs with fire fox

---

