---
title: "Wireless in Koala"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by bytescribe on 2010-01-21
Hi, there!

My boyfriend installed Koala (Ubuntu 9.10) tonight, and I'm very impressed just with the opening log-in screen! (I'm easily amused...what can I say?)

I look forward to installing it on my own computer, but what I need to know is: will the ndiswrapper software configurations for wireless I have for Hardy Heron work with Karmic Koala? I wanna test this out before I go spending money on DSL cable (though I DO prefer DSL anyway).

I'm using:

1)A Linksys router (downstairs, hooked up to my parents' computer)
2)A Linksys wireless adapter--it uses a Ralink chipset.

I don't have the model numbers on me right away for either peripheral, as I'm at my bf's house at the time being. But I at least would like a general idea of how my config settings for Hardy might work for Koala.

Thanks,
Kat ^.^

---

### Post by mikewhatever on 2010-01-21
Perhaps I don't quite understand the question, but what if your ndiswrapper configurations from Hardy do not work? Why would it matter? You know the hardware works, and having a clean install of Karmic, it shouldn't be a big deal to create new configurations if needed.

---

### Post by Sidewinder1 on 2010-01-21
Hardy "should" configure itself. All you may need to input is the wireless name, not sure the default name of linksys routers but if you've connected to it before, you probably already know. In addition you'll need to put in the WEP or WAP key and you should be good to go.
HTH,
Side

P.S. Forgot, you're using Karmic, my wife keeps reminding me of that type of fault :-) should be the same for KK...

---

### Post by bytescribe on 2010-01-22
Perhaps I should have made myself more clear. Back when I first started working with wireless in general, I learned about blacklisting the native Linux wireless drivers (the ones I read that got changed when Ubuntu went from Gutsy to Hardy) in order for ndiswrapper and the windows-based files to work properly. As for the WPA/WEP, I could not do that intially because my parents' computer was screwed up and therefore I could not get the passcode link from the CD-ROM that came with the Router (so I've been riding on someone else's unsecured signal for a good year now...naughty me, I know!). Now the folks have a new computer, so I can do the process completely fresh. 

I just wanted to know if I could simply back up the blacklist config file that I changed (in the modprobe folder), ndiswrapper, gtk and windows-based files I got from the CD (BEFORE my parents' computer screwed up) onto my USB flash drive and use them on Koala once I get Koala installed on my computer...

Hope that makes things more clear...

Thanks,
Kat ^.^

---

