---
title: "Wireless Connection issues/problems ... again"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by dardack on 2007-06-18
Ok so i thought i had figured out my connection drop issues, by uninstalling NM, and going manual/wicd.  Aparently i was wrong.  Since i thought this was happening again, i opened 3 terminals 2 to ping, 1 to run iwconfig when the problem happens.  As far as I can tell my problem doesn't occur in set intervals, seems to be random.  And if no one can help me fix this i'm leaning towards going back to windoze and that's something i really dont' want to do, but it's just so annoying.

Ok i have the bestbuy brand PCI wireless card, not called BestBuy something like Dytex, with the Arethos Chipset i believe AR5005G (not at home to check).
I have NM uninstalled and wicd installed (i think i tried on 2.16 kernel with WICD uninstalled and same issues).

So i run ping to my router and ping to google.com.  WHen the issues occur, both pings are just sitting there, displaying the last ping but nothing moving on, than after 30-60 seconds, sometimes longer, 5-15 pings just appear with RT from google.com in the 10,000 to 100,000 and my router in the thousands to 10,000's.  Usually google.com is consitently when the connection is up from 49-51ms, and my router .9 to 2 ms.

Also, when i run iwconfig when the ping is just sitting there, iwconfig shows that my link strength is double what it normally is (wicd confirms this).  Normally i run about 20%-25% when my connection is working.  When this problem occurs its up above 50% to even 60%.

As far as i can tell nothing in my /var/log directory is changed at or around the time of these problems.  If anyone can point me in a place to run some debuging/logging so i can figure out what's going on.  This is very annoying, especially if i'm playing WoW or downloading music or watching stuff online, or listening to the radio.  I am very discouraged by this right now.  I really hope someone responds with some ideas.  I have searched the forums, and there seems to be a lot of some connection issues happening, just no fixes that i can find.

---

### Post by dardack on 2007-06-18
Ok so i remembered some more stuff.  I think it happens only when i'm doing something online.  Like playing wow or downloading, etc.  I usually leave those 2 terminal windows open with ping running.  Whenever i come back i scroll all the way up as far back as it will keep it and (AFAIR) there isn't one instance of this issue happening.  All the latency are in the respective ms of 48-51 for google and .9-2ms for my router.
I've read some other people having their internet drop under loads, but theirs usually doesn't come back up on it's own, the have to reboot or restart networking.  

Also, if anyone knows of some commands i can run to enable more debugging and try to figure this out.  It's just so frustrating.

---

### Post by charleseddy on 2007-06-18
Hey.  I'm not a network genius, so I can't see what your problem is.  Here is some documentation to look through, though.

[https://help.ubuntu.com/community/WifiDocs/NetworkManager]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")

Also, when you get frustrated and there's something really hard to fix, hop in #ubuntu in IRC.  There, you get instant help, and it will take a load off.  Sometimes people ignore difficult problems in the forums, but in IRC it's one to one help.  This can be accessed through GAIM.

ce

---

### Post by dardack on 2007-06-18
I appreciate the link but i've long ago removed Network manager because i had even more issues with it than i do now.  I now use wicd (for awhile i was connecting manually in a terminal each time i rebooted).  Hopefully tonite i can hope on IRC and get some help.  It's very frustrating.

---

### Post by charleseddy on 2007-06-18
Understandable.  Just, in IRC, if you see that the helpers are busy don't worry.  Sometimes it takes them a minute to finish.  But it's more of a getting help and less of a waiting thing, which you should appreciate.

Thanks,
ce

---

### Post by dardack on 2007-06-19
Thanks i went and someone pointed me to a website that said the AR5005G drivers that are restricted and come with Ubuntu have their issues.  So i did have to use ndiswrapper.  I'm going to post my steps just incase someone stumlbes over this.  

So i connected to internet with the restricted drivers.  I got ndiswrapper installed through snaptic package manager.
I edited my /etc/modprobe.d/blacklist file and added at end of file:
blacklist bcm43xx
blacklist ath_pci
blacklist ath_hal

unclicked the AERTHOS driver in the restricted manager driver thing.  Rebooted.

I than copied my driver from my cd and ran:
sudo ndiswrapper -i ~/net5211.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper

rebooted.

BROKE my install.  I missed the part where it says to not use the CD drivers, as they might not be tested.  So i had to do a fresh install.

ran:
lspci
lspci -n

found my PCI ID: 168c:001a (rev 1)

Just went into each list on ndiswrappers website and under A, and acer laptop has the same PCI id, so downloaded thos drivers.
Followed steps above, again, and now i have more than double my signal strength all the time from the low 20%'s before to up above 60%.  And so far no more connection issues, i mean it was only one night, more testing will be needed, but things are looking up.

---

### Post by charleseddy on 2007-06-19
Glad you had a good experience!  Remember, we're always here in the forums and IRC to help out.

cheers,
ce

---

