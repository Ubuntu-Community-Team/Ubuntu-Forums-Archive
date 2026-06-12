---
title: "Ubuntu and AOL Cable Broadband"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by DWRZ on 2007-02-08
When I'm up at college, Ubuntu works no problem, I can connect through Ethernet or wireless. Right now I'm home and sadly my folks to use AOL Cable Broadband (not Dial-Up, not DSL, Cable Modem and Linksys Router+Wireless). I can't convince them to switch to RoadRunner ($40 v. $20 per month) so unless AOL goes bankrupt or stops Broadband service I'm stuck with this situation.

AOL works fine when I boot Windows XP... I have to use their AOL Dialer software (still don't know for what technical reasons a Dialer is necessary and what it does) to connect but it works both Ethernet and Wireless fine. 

So...first question, because I just want to know: Can or can't I connect through AOL Cable Broadband using Ubuntu? If I can, what's the way?

I've done a lot of research on Google, visited "Linux Cable" websites, even e-mailed people who've posted similar posts-- no luck. So I'm going to scream with joy if somebody can help me figure this one out. :D

---

### Post by jimbren on 2007-02-08
Are the router and modem configured so that the router passes the authentication to AOL, or do the windows clients have to pass the authentication?  I did a quick Google using "aol broadband linux" as search terms and came across some entries that say you have to have the router pass the authentication.

With my SBC DSL set up, I had to put the DSL modem in bridged mode in order to do this.  You might have to do the same.  

And you might have to...eek...call AOL tech support for instructions on how to do it.

Good luck.


jimbo

---

### Post by DWRZ on 2007-02-08
Thanks for the help.

Right now I can only connect to AOL using AOL Dialer on Windows XP. I've tried authenticating through the router using PPPoE, but apparently (I might be wrong) that works only on DSL and not Cable Modem. Still, if anyone knows a way of not using the Dialer and connecting to a Cable connection only through the Router, that'd be great. 

Calling AOL Tech support... they don't support Linux, though I guess I could always give it a shot. :\

I'm using XP now and it sucks! :(

---

### Post by DWRZ on 2007-02-08
Well, it's nice to take a step in what looks to be a promising direction. I found something called "penngy" that seems to make this possible (or so it's said)...

I installed penggy via Synaptic (browsing on my neighbors slow unsecured wireless). I then edited the cfg file to use tcpip and use my screename and so on, and added my password in another file.

I then typed in penggy in the terminal and it tried to connect to AmericaOnline.aol.com and then also listed an ip adress XXX.XXX.XXX.XXX:5190. After some time it says it cannot resolve or it fails or something and then tries again and fails again.

Any idea what I can do next? I've not been able to find any documentation on penggy unfortunately... :\

I'll seriously paypal $10 to whoever gets this working for me. Maybe more (but not much, I'm a student). The thought of having to use XP every time I'm home makes me cringe.

---

### Post by jimbren on 2007-02-09
have you actually tried putting an AOL username and password in the router config and seeing if it authenticates for you?

---

### Post by jimbren on 2007-02-09
Sorry if I read like a jackass in my last reply--not my intent.

I found an article that [might relevent to you]("http://www.smallbusinesscomputing.com/webmaster/article.php/2248681").  The article itself talks about AOL's DSL service working with a router and how the cable service has problems with it.

What gets me here is that you've got a router in your set up.  I can't help but think that you should be able to provide an AOL user\pass to the router in the router's configuration itself and then just use that.

It may not be as pretty for the other AOL clients in the house--I don't know if they would have to jump through hoops to sign onto their own profiles or not--but it should be doable.

Linux is a dirty word at AOL.  You might want to look through their support pages for how to connect something else--a Tivo or an Xbox--to AOL Broadband cable, and I bet you'll make progress.

jimbo

---

### Post by dannyboy79 on 2007-02-09
See the attached pic for possible advice. this is what my netgear router looks like. (it's a WGT624, v2 i think) normally I don't have the box that states, "Does your internet connection require a  login" but I checked it to see what would happen. It's asking for authentification. Does your router have this?

---

