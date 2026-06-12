---
title: "Boot straight into firefox..."
date: 2010-01-25
forum: New to Ubuntu
---

### Post by dustywb on 2010-01-25
I am wondering if there is a way to boot into a full screen browser on start up where users are locked out of everything else. Basically from the log in screen they type in their password then ubuntu comes up directly to firefox in full screen mode to a specified website and they would be locked to this website only. Hope this makes sense lol.

Thanks for any help
Dustin

---

### Post by mbzn on 2010-01-25
New user, block all websites(excluding the one you need), add firefox as a startup app,(i believe fullscreen can be found under about:config). then remove everything from desktop and all unneeded privileges.

Maybe there's an easier way???

---

### Post by nerdy_kid on 2010-01-25
i believe he wants to bypass the DE and have X load just firefox (and probably the env vars to theme the gtk) there was a thread floating around a while ago along those lines, but i cant find it :(

---

### Post by dustywb on 2010-01-25
> **mbzn said:**
> New user, block all websites(excluding the one you need), add firefox as a startup app,(i believe fullscreen can be found under about:config). then remove everything from desktop and all unneeded privileges.

Maybe there's an easier way???

Cool thanks! Now to install it on a test pc and see how it works :D

---

### Post by dustywb on 2010-01-25
> **nerdy_kid said:**
> i believe he wants to bypass the DE and have X load just firefox (and probably the env vars to theme the gtk) there was a thread floating around a while ago along those lines, but i cant find it :(

That would be perfect if that's possible, I'll search around some more.

---

### Post by nerdy_kid on 2010-01-25
i do know its possible, sorry i cant help more :S

---

### Post by texaswriter on 2010-01-25
Dustywb> Test your google fu, or even search this forum for these keywords: firefox kiosk 

also try: web kiosk

Like to hear how this goes, considering setting a Linux web box up for roommates.

---

### Post by dustywb on 2010-01-25
> **texaswriter said:**
> Dustywb> Test your google fu, or even search this forum for these keywords: firefox kiosk 

also try: web kiosk

Like to hear how this goes, considering setting a Linux web box up for roommates.

Thanks for the tips! I found a Firefox add-on called R-Kiosk which is at [https://addons.mozilla.org/en-US/firefox/addon/1659](https://addons.mozilla.org/en-US/firefox/addon/1659) anyways this works exactly how I need it to it disables everything and launches in full screen, the only way for people to navigate is by using what's on the page I set to home which is great so no surfing away from where I want them to be! 

Anyways still googling around to find out how to have Firefox start-up automatically when an account is logged into and limiting a user account to only be able to use the modified Firefox, don't want them to be able to do anything else or have access to any other programs. Unless logged into an admin account of course then I want them to have full privileges.

Thanks for all the help so far and any tips or advice on how to proceed would be much appreciated.
Dustin

---

### Post by josephellengar on 2010-01-25
> **dustywb said:**
> Thanks for the tips! I found a Firefox add-on called R-Kiosk which is at [https://addons.mozilla.org/en-US/firefox/addon/1659](https://addons.mozilla.org/en-US/firefox/addon/1659) anyways this works exactly how I need it to it disables everything and launches in full screen, the only way for people to navigate is by using what's on the page I set to home which is great so no surfing away from where I want them to be! 

Anyways still googling around to find out how to have Firefox start-up automatically when an account is logged into and limiting a user account to only be able to use the modified Firefox, don't want them to be able to do anything else or have access to any other programs. Unless logged into an admin account of course then I want them to have full privileges.

Thanks for all the help so far and any tips or advice on how to proceed would be much appreciated.
Dustin

Just curious what you're using this for, if you don't mind sharing

---

### Post by dustywb on 2010-01-26
> **rossholley said:**
> Just curious what you're using this for, if you don't mind sharing

I'm in the planning and testing faze but I am looking at some web based pos software and I don't want employees to have access to the rest of the computer. Just want them to be able to ring up sales and then go work, not try to surf the internet and waste time lol

---

### Post by freak42 on 2010-01-26
to start up an app, look under system-> prefs -> startup applications  (that's on 9.04) (before it might be under an entry called sessions or something similar). (Hint: I think you have to be logged in as the user this should happen to)

there are also config file ways of starting up stuff at different boot/login stages, but I am no expert in that area.

hth

---

