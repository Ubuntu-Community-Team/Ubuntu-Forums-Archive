---
title: "limited internet access"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by iloguerrero on 2008-10-29
I really need help with my internet access.
I connect via ethernet cable and it shows that i'm connected but i have limited access. I can browse some sites but not others. I have no clue what the problem is. i called up my internet provider but they said that they didn't provide help to linux users.
If some one can point me in the right direction that would be greatly apreciated.

ilo

---

### Post by scizzo on 2008-10-29
Hello,

What exactly do you mean with it that you can't access the site. If you are using firefox or the like what happens? It does not connect to the site or it gives you errors?

Can you ping the host that you want to access?

---

### Post by iloguerrero on 2008-10-29
i can easily get on to google and some other sites on firefox but when i try to check my email on hotmail or surf other sites it looks like its loading but never does.
i've pinged all the site and it comes back good...not sure what the problem is.
thanks

---

### Post by scizzo on 2008-10-29
Its not just that you have the browser set to work offline?

In File menu in the browser.

---

### Post by iloguerrero on 2008-10-29
no i made sure of that. I've had this problem for a while and i really what to get rid of my windows but i need the internet to work on ubuntu.

---

### Post by scizzo on 2008-10-29
And no plugins blocking access through firefox? Can you try to access websites with links in command line instead also?

---

### Post by iloguerrero on 2008-10-29
how can i access links via command line? sorry, i'm pretty new to linux in general.

---

### Post by iloguerrero on 2008-10-29
any one have any suggestions?...

---

### Post by iloguerrero on 2008-10-30
any one?

---

### Post by lophie on 2008-10-30
does your provider require proxy? if it does. check if your firefox get the proxy setting from your entry or the environmental setting. if it one of those, try to use the other one.

---

### Post by iloguerrero on 2008-10-30
i'm pretty sure the proxy is fine. is this a common problem accesing some site but not others?
thanks

---

### Post by iloguerrero on 2008-10-31
i'm pretty sure my provider doesn't need proxy. Is this a normal problem? to access some but not all sites?

---

### Post by Plumtreed on 2008-10-31
I have a similar problem with a mobile broadband connection in the UK! I can access everything via Vista on this connection but, through Ubuntu via NetworkManager 0.7, I get a restricted access. I can't access certain websites but others are fine. The restriction seems to come from the ISP's end because the windows brought up to indicate the restrcted connection bears their name & logo. The carrier claims to not have any restrictions in place. It becomes awkward because they think you are discussing porn sites but this restriction applies to more sites than just porn sites. I tend to believe the ISP because there are no restrictions when using the Windows OS.

The restrictions appear to be the sort you might find on a mobile phone type of internet connection so I think NetworkManager puts me on to a 'lower-grade' of connection, GSM rather than 3G.??????

For starters where are you located? UK? Who is your ISP?

---

### Post by iloguerrero on 2008-10-31
i'm in spain and my provider is orange. I've had bad experience with them in the past so i wouldn't be suprised if it is them but just like you i have no restrictions on vista. is there a way to change the restrictions if it is the network manager?
thanks!

---

### Post by Plumtreed on 2008-10-31
I am located in an area that does not get the best 'coverage' by 3 and they admit it! I think that it might be a clue to the problem. 

However, I get a very good signal when using the Vista operating system so I firmly beleive the 'bug' is with Ubuntu. If it goes well with Vista it should do just as well in Ubuntu!

Sorry, I don't have any answers and I thought that someone more knowledgeable would step in to assist us if we keep the thread going long enough.:popcorn:

Try the following for more details about editing your connection, it doesn't have much info for Spain though...

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

---

### Post by iloguerrero on 2008-10-31
thanks!
i'll have a look and see if i can edit something. if i find somwething out i'll post.
ilo

---

### Post by iloguerrero on 2008-10-31
oh by the way, what specs do you have? maybe its the computer, if no one else is having this problem then maybe it's not ubuntu.

---

### Post by iloguerrero on 2008-11-01
bump?

---

### Post by Plumtreed on 2008-11-01
I don't think it could be the PC because I use the same Laptop for Vista jn a dual boot configuration. If it goes OK in Vista it shoyld work in Ubuntu, especially NetworkManager 0.7.

I have an Acer Aspire 5315 notebook, Celeron 560, 2.13 GHZ and 2Gb Ram.

I'm going to try to match up the Windows configuration with that in NetworkManager in the hope it does something.

I some times wonder why I go to all the trouble because everything works in Windows without even trying! I don't even dislike windows.:confused:

---

### Post by Plumtreed on 2008-11-01
When operating in Vista the 3 Network in the UK provides an 'interface' that allows me to select whether I 'prefer' 3G or not. So I have always selected 3G. I guess that is what I get and therefor there are no restrictions.

In Ubuntu & NetworkManager there doesn't appear to be a way to select the 3G network. So, I get what ever is available and that is the 3 GSM network which is for mobile phones. 

I'm guessing and I hope someone reads this thread and knows the answer. In fact, I'm going to start a new thread to see If I can get some help!

---

### Post by iloguerrero on 2008-11-01
ok.
i still can't figure out my problem. I still have limited access and can't download the updates or anything similar. It's very annoying, i want to get rid of windows and just work off ubuntu.
what i might do is download aother distro and see if it works on that.
by the way, are you from australia?

---

### Post by Plumtreed on 2008-11-02
Yes, from Australia but in England for about 6 months! Using the 3 Network.

I will let you know if I stumble across anything!

---

### Post by iloguerrero on 2008-11-02
thanks,
i'm from oz as well just in spain for a while. If i find something out i'll let you know.

---

### Post by iloguerrero on 2008-11-02
have just tried to work the wired internet on kubuntu, fedora and mandriva and no luck, i have the same problem on every distro. I'm starting to think its not just ubuntu...jeje.
might be my network card, i am stumped. I'm going to start a new thread about this problem, with my specs.
good luck

---

### Post by Plumtreed on 2008-11-02
I got it 'sorted' but with a negative outcome. My theory seemed to be right, NetworkManager puts me into the fastest network which is a mobile phone network but that is restricted. I can get into the 3G network but that is dead slow perhaps because I am in an area a bit remote?? However, it is not restricted!

I went to 'edit connections' and added the configuration details for the 3G network and waited, literally seconds, for things to load. It is like the old dial-up. It does all the right things but v/slow:(

---

### Post by Plumtreed on 2008-11-03
Speed is at a reasonable level and initially it must have been affected by the activity by other subscribers.

I copied the APN and password as used in Vista and that was all that was needed. I may have solved it earlier but didn't identify that fact through impatience. The initial positive handshake took considerable time to register. It now goes OK!

The APN suggested for 'Pay-as-you-Go' is 'three.co.uk' which I changed to '3internet'.

Have a go in the area of using a different APN it may work for you!

It may be warmer in Spain but is a bit cold and wet here, from NSW and it will be nice and warm there!

---

### Post by ancianoman on 2008-11-16
> **iloguerrero said:**
> I really need help with my internet access.
I connect via ethernet cable and it shows that i'm connected but i have limited access. I can browse some sites but not others. I have no clue what the problem is. i called up my internet provider but they said that they didn't provide help to linux users.
If some one can point me in the right direction that would be greatly apreciated.

ilo





Sorry Buddy, I have a gateway M1625 and running a realtek 8169 and am having the same exact problem.Lots of luck if I find a solution I'll get back to you...You're not alone

---

### Post by iloguerrero on 2008-11-17
I have been able to find a solution to the problem but not pinpoint the actual problem.
I had a suspicion that it could be the dns server so i changed it but i still had the same problem.
A friend came by and had his mac and he had the exact same problem. What we did was to connect another modem to the modem i have and connect to that one...It works perfectly!
The dns server changed and it seems to work fine, the only problem is that we don't actually know what the problem was.
Hope this helps..

good luck.
ilo

---

### Post by vitiate on 2008-11-19
I am having the same problem. I'm running a Dell t3400. And a site I cannot load is the Dell site describing my machine. It really seems random which site I can/can't load. And it isn't that I can't connect, firefox just stops loading a site. dell.com loads the top menu part, and then stops. ti.com loads the menu and then stops. If I continuously hit refresh, the site loads a little bit more and then stops. That is using firefox 3 btw. If I use wget from the command line, same issue, it gets to about 30% then stops and the eta just climbs higher and higher. Maybe there is something about these sites? 
On this same machine on the same connection, but running windows xp, the sites load just fine. So I am pretty sure it is Ubuntu/Linux not doing something correctly.

more sites that don't work:
[http://www.whitehouse.gov/history/presidents/al16.html](http://www.whitehouse.gov/history/presidents/al16.html)
[http://lincoln.lib.niu.edu/](http://lincoln.lib.niu.edu/)
[http://www.ddj.com/cpp/cuj.jhtml](http://www.ddj.com/cpp/cuj.jhtml)
[http://www.thetruthaboutcars.com/](http://www.thetruthaboutcars.com/)

---

