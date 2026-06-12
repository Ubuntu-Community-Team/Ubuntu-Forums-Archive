---
title: "Intel Blacklisted?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by freakbofo on 2009-04-23
well i couldnt wait and upgraded to jaunty.I having trouble getting compiz to run on startup,so looked around and it seems that my chipset has been blacklisted,which is a 965 family i think.Blacklisted?what does that mean?Apparently they not very good or what?can i fix it.i have managed to get it working on startup by putting the compiz icon in the startup menu,but it seems to me to be taking a lot longer to get a usable desktop than it was before.

thanks,and sorry if it sounds a bit dumb,im confused at the moment.

---

### Post by Hospadar on 2009-04-23
Have you installed the restricted drivers? (System->Administration->Hardware Drivers)

Does 3d/compiz work at all for you?
-From a terminal, run glxgears, do you see 3d gears?
-From a terminal, run "glxinfo | grep direct" does it say "Direct Rendering: Yes"?

That blacklist you are seeing is probably not what really concerns you.  A lot of older modules get blacklisted just to make sure they don't interfere with their replacements.  Unless you know for sure, It's best just to leave things like that (although if you're confident that you can boot off a live cd and fix things like that if they make your machine choke, I say go for it)

---

### Post by cariboo on 2009-04-23
Have a look at the [Januty Release Notes]("http://www.ubuntu.com/testing/jaunty/beta"), under Know Issues. That should answer some of your questions.

---

### Post by freakbofo on 2009-04-23
Gears yes,rendering yes.um compiz is working okay,but the way i have to get it to run at startup just makes my desktop very choppy when i log on.i suppose it not too big of a deal,i can wait a bit longer lol.

---

### Post by starcannon on 2009-04-23
[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance regressions on Intel graphics cards]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards")

I have a few netbooks with these intel chipsets in them, I'm keeping 8.04 on those; remember, 8.04 is an LTS (Long Term Support) release, so it will perform fine, and affords intel gpu owners plenty of time for the new xserver bugs to be worked out.

GL however you decide to go about your upgrade path.

---

### Post by MockY on 2009-04-23
So since all my laptops is running Intel graphic, I should basically not upgrade at all. This is shitty and I hope they soon will resolve this. I was really looking forward to install Jaunty today...crap. What a disappointment. How on earth can they release it into the wild with such major bug?

---

### Post by starcannon on 2009-04-23
> **MockY said:**
> So since all my laptops is running Intel graphic, I should basically not upgrade at all. This is shitty and I hope they soon will resolve this. I was really looking forward to install Jaunty today...crap. What a disappointment. How on earth can they release it into the wild with such major bug?

It's not an LTS Release, I imagine they will have it ironed out by the time the next LTS comes along. If you run in the LTS upgrade cycle then your not outdated, and your on the most stable release at any given time. Upgrading an entire OS twice a year is not something I personally do on my mission critical machines, I save that for my toy boxes.

Hit the bargain bins online and put together a low cost toybox for these bi-annual release, you'll have all the fun of geeking out, without any of the irratation of messing up your main computer. Anyway, just my 2 cents on the subject.

GL and have fun.

---

### Post by MockY on 2009-04-23
LTS release or not, such a major bug should not be present in a "regular" final release. It is a huge bummer since I wanted to see how well it performed on SSD, and another shot at fixing my mic issues (on both machines). Since Intrepid currently works to satisfaction (besides the microphone issues) on both my wife's laptop and on my main laptop, I guess I just have to accept the fact that I can't upgrade till October.

---

