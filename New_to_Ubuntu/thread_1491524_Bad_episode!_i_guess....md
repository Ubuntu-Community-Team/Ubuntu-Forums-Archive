---
title: "Bad episode! i guess..."
date: 2010-05-23
forum: New to Ubuntu
---

### Post by UpSignal on 2010-05-23
This is what's being annoying me quite some time...
I don't like the default network manager from gnome, because it doesn't have an option to refresh wireless
networks. and it doesn't do it, because in my room i have a network, and in the kitchen i don't. so, i went from the kitchen to my room...and nothing. i waited for some time...and nothing. so, i swithed wireless off 
and on again, and there it goes. So, basically i needed a manager that refreshes network.
Good, i went to WICD since it has a good reputation and i already used it before. So i open up synaptic, installed it, and removed network-manager-gnome. Reboot, and here it goes! So, i typed the password for the
wpa.. and...surprise! it said to me "error: bad password" something like that. I started to became nervous, since i was on vacation, and i needed internet. So, i went to my friend's house and used his wireless (he doesn't have a cable). He gave me the password...and boom! Bad password! I was about to pull my hair off..
Open up synaptic, searched for the gnome network and tried to installed...yep...couldn't do it, because i need an internet connection. i tried to connect again to all my networks with the known passwords and no luck. Thank you WICD. I spent the rest of my hollidays without internet. Didn't brought my cds, so...nothing i could do about it. These are the times when i really want to install windows. I love linux, no doubt i love it...it's fast, stable, secure, fun...it's awesome...and 99% of the time, i don't miss windows. But sometimes...god damn, it just doesn't work when i most need it to work. You know, i already used WICD about 5 or 6 times...never failed to me. It failed on my hollidays. Omg... i'm not asking for help..because there is nothing i can do now. more like an annoying episode...
Now i know what are you guys going to say... "you shouldn't have removed gnome-network untill you were 100% sure WICD was fine", ok...whatever. My bad :s

---

### Post by -humanaut- on 2010-05-23
You probably removed your ndiswrappers when you deleted network-manager you don't have to delete it when you install WICD because WICD will default anyway.

---

