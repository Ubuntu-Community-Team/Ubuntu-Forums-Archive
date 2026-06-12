---
title: "Cpu gone mad!!!!"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-02-25
Alright this all started randomly. It seems sometimes i start a Program and my CPU Basically uses 50% + on that one program. I mean like im just using firefox and my CPU is over 75%. I have no clue whats going on any sudgestions? TYVM!!!

     Ravernomina


Edit: Now IT just Won't Stop even if i Exit out of all my Programs!!!

---

### Post by kansasnoob on 2009-02-25
My guess is flash! Try going to firefox and clicking on Tools > Add-ons > get add-ons and install Flashblock 1.5.8, then restart Firefox.

Flash will still work fine (maybe even better), you'll just need to click a "button"!

---

### Post by Ravernomina on 2009-02-25
I've also ben seeing my computers ubuntu start-up slowing down. Ubuntu has been acting weird lately ive used chkrootkit and rkhunter and nothing :l. So really idk what to do any more just ugh this sucks -_-.

---

### Post by Ripose on 2009-02-25
Install the **htop** package so you can see EVERYTHING that is running, if you find anything strange post it here.

---

### Post by HittingSmoke on 2009-02-25
> **kansasnoob said:**
> My guess is flash! Try going to firefox and clicking on Tools > Add-ons > get add-ons and install Flashblock 1.5.8, then restart Firefox.

Flash will still work fine (maybe even better), you'll just need to click a "button"!

[NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") > FlashBlock

---

### Post by nelskurian on 2009-02-25
firefox need more memory.try some tips to tweak.

**$ for f in ~/.mozilla/firefox/*/*.sqlite; do sqlite3 $f 'VACUUM;'; done**

For more information try the link

[http://linuxlight.blogspot.com/2009/02/firefox-tweaks.html]("http://linuxlight.blogspot.com/2009/02/firefox-tweaks.html")

---

### Post by Ravernomina on 2009-02-25
Alright ill install all that tonight when i get home from Class. It will end up being fixed when i get home i bet you :lolflag:.

---

