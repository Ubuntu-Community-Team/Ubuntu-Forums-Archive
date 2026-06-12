---
title: "Weak wireless signal (far away from router)"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by SegaFan on 2008-04-13
Simple problem, my PC is too far from my router. I get a signal but it's weak, it comes and goes and it's not really usable. It's impossible to move my PC anywhere else and extremely inconvenient to move my router from where it is.

Do you have any tips on how I can boost the signal/reception?

I thought about the possibility of getting a better antenna for the wireless network card, but I don't even know if you can readily get them, or how well that would work.

Thanks.

---

### Post by Kevbert on 2008-04-13
I had the same problem.  Got an external antenna plus lead for the wireless card and it boosted the signal and resolved the problem.  If your router had a detachable antenna it may be worth replacing it with a new antenna and extension lead and repositioning this antenna for maximum signal.  The only problem is that external interference is also boosted.  Previously I could only see two wireless signals, with the external (card) antenna I can see six.  The other thing you may need to do is change wireless channels (at the router) as in the UK most wireless routers seem to be set to channel 1 (default).

---

### Post by Kevbert on 2008-04-13
An external antenna can be found here:
[http://www.amazon.co.uk/WiFi-Wireless-Network-WLAN-Antenna/dp/B000PHCZBA/ref=sr_1_8?ie=UTF8&s=electronics&qid=1208119281&sr=1-8]("http://www.amazon.co.uk/WiFi-Wireless-Network-WLAN-Antenna/dp/B000PHCZBA/ref=sr_1_8?ie=UTF8&s=electronics&qid=1208119281&sr=1-8")

---

### Post by fazavon on 2008-04-13
or the free alternative...

[http://www.freeantennas.com/projects/template2/index.html](http://www.freeantennas.com/projects/template2/index.html)

yes it looks a little funny but it boost my range about 30%

That my friend is cheap,quick and what more can one ask for in life?

thanks

//j

---

### Post by chili555 on 2008-04-13
You could install a repeater. I have a Linksys WAP54G that has a repeater mode. It's installed half way between the router and the far end of the house. It takes the signals it receives and boosts them and re-broadcasts them. It's limited to a specific ESSID and MAC address. It doesn't have to be connected to anything except AC power, so it sits on a shelf behind a family picture. I finally have 80/100 signal strength when I answer emails propped up in bed!

router----------------------------------->repeater----------------------------------->laptop

---

### Post by SegaFan on 2008-04-13
Thanks Kevbert, that could be just what I need. I'm not sure whether you can replace the antenna on my router but you definitely can on my wireless PCI card. Is interference a major problem?

I will also look at fazavon's solution, and chili555's if neither of those work.

The only place in my house that doesn't have a good wireless signal is where I have my PC!

---

### Post by Kevbert on 2008-04-14
Interference can be a problem from such things as microwave ovens and digital cordless phones as they work at the same frequency.  Also other wireless networks may be on the same channel (so reduced speeds will occur) or nearby channels as they overlap.  See [http://en.wikipedia.org/wiki/List_of_WLAN_channels]("http://en.wikipedia.org/wiki/List_of_WLAN_channels")
Each channel is 5MHz higher in frequency than the previous, but the frequency band is 12MHz.  Therefore as stated previously you may need to change your router frequency.
I suppose using a cable from the router to the PC is out of the question (do you have a LAN connection ?)  You can get cables up to 30m long and you wouldn't have signal problems and the connection would be more secure.

---

### Post by SegaFan on 2008-04-14
I'm reluctant to change anything on the router because it took long enough to set up as it is, what do you have to do to change the router frequency? I can only see one other wireless network at the moment, but as you say I might see more.

A cable would be more inconvenient than moving the router, due to the layout of my house it would be very difficult. I don't see that security would be any more of an issue if I do nothing to boost the range of signal itself, only the range of the receiver.

---

### Post by Kevbert on 2008-04-14
To change channels you need your router IP address (see [http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm]("http://compnetworking.about.com/od/workingwithipaddresses/f/getrouteripaddr.htm"))
The next thing is to open your internet browser and enter this address.  In my case it would be [http://192.168.0.1](http://192.168.0.1)  for my Netgear router.  You'll then get a window which asks for a username and password.  In my case the default would be 'admin' and 'password' (without quotes) from this a new window will be displayed with set-up details for your router/modem including Network Key. 
 I'd advise you to change your router password as anyone who can see your wireless can in theory change it by entering default settings providing they choose the correct IP address.  Here in the UK there have been instances where this has happened and the user has been hacked or illegal use of wireless has been made.  There was a TV program on this a few months back.
If you don't have these, or the user manual, you can google for the router manufacturer's home page.
If you make any mistakes or forget new settings, there normally is a reset switch on the back of the router.  If you press and hold in this (for up to 10 seconds) all the settings should return to their default values.

---

### Post by Kevbert on 2008-04-14
Silly me.  To get your router IP address go to System-Administration-Networks select DNS tab and it will be there.

---

### Post by SegaFan on 2008-04-15
Looks straight forward, I think I will go for that external antenna, thanks again.

---

