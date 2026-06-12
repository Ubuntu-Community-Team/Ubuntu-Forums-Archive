---
title: "Odd Connection Issue"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by derouge on 2005-10-26
I managed to get my wireless internet up and running, using aDlink DWL-G520 Rev B Card .. works fine; fast and consistent. Sorta. The thing is every time I log back in (after restarting computer) my internet will not be up, which is quite annoying. I've been toying with it for a couple days now, and about 15 minutes ago I think I hit the nail on the head. 

I opened the terminal and used sudo iwconfig ath0 .. and configured it to the right channel and essid. I then noticed that the "Rx invalid nwid" number was going up. No clue what that meant, so I shrugged my newbie shoulders and looked at some other things. I saw the Mode was "Managed" and on the upstairs wireless comp I know we used Ad-Hoc. So I set it to Ad-Hoc. The Link Quality number immediately jumped from 24~ to 75. I opened up Firefox and tried browsing around, but only got loooong loading with no content. So I changed the mode back to managed, and then re-opened Firefox and tested.

Walah, I was online. Now .. the question is, what the heck?!? First off why won't my internet come up by itself when I shut down? Second, is this Managed->Ad-Hoc->Managed Mode thing a potential fix? If it is it's really not a big hassle to do every time, but it's a hassle I'd rather not have. In addition, the rest of my family is even more computer retarded than me .. and completely unaware of Linux, so I'd like it to just come up when it boots so I dont have to deal with their connection issues.

Any ideas? Need more clarification, just ask. :)

---

### Post by carlosqueso on 2005-10-26
I'm as much a linux n00b as you myself...but I know about the managed/Ad-hoc difference since I have a wireless network at home.  Ad-hoc is how computers connect to other computers.  If you are using a router, that is a managed situation.  Since I'm assuming you have a router to use the internet with your wireless, you should used managed.   I hope this part helps.   As for the other part, you have to edit some file, but I can't help ya there since my wireless card seems to be incompatible and I'm too cheap to buy another when I use my comp less than 10' from my router. *shrugs*

---

