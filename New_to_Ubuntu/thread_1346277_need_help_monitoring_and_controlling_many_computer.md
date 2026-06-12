---
title: "need help monitoring and controlling many computers bandwith usage"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by hyperhopper on 2009-12-04
Hello!
I need help monitoring and controlling many computers bandwith usage.

This one is running vista (for games, plz dont kill me), and there is one running XP and another running ubuntu.

How can i monitor how much bandwith each computer is using, and put limits on how much they can use?

we are all behind the same router.

---

### Post by stoogiebuncho on 2009-12-05
Some router's can keep track of bandwidth.  I'd play around in the settings and see what's there.  If you tell us what model router you have, someone may know how to set it up.  

I don't really know any way other than that if you're using multiple computers.

---

### Post by hyperhopper on 2009-12-05
linksys model # WRT54GS version 6 wireless g broadband adapter 2.4 ghz

---

### Post by Paddy Landau on 2009-12-05
> **hyperhopper said:**
> This one is running vista (for games, plz dont kill me)
This isn't a Windows-bashing forum. You're welcome to use Windows and any other operating system that you want or need ;)

---

### Post by hyperhopper on 2009-12-05
mmk, thx!

uahg.. is there any way to just monitor without controlling, to prove that im not the one hogging the bandwith, and my dad is,

---

### Post by oldsoundguy on 2009-12-05
If you are playing games on line with your Windows computer, that is the one hogging the bandwidth.

In practicality, there really is no method to control or monitor bandwidth on a HOME network setup with out some serious programming. A business situation with network drives and server setup is a different story.

To top that, unless you are on a limited bandwidth DSL or (shudder) dial-up, all machines should function without a problem. I have 7 on my network .. two of which are XP machines which only go on line to report to BOINC and for updates (and for an on line college course I am taking in Photo Shop).

I never have a bandwidth issue on the computers .. I do when some idiot sets up a server on a home node and starts stealing bandwidth .. but that does not happen that often.

---

### Post by BDNiner on 2009-12-05
You would have to find a way to monitor bandwidth from your router. I don't think that your linksys router has those capabilities because it is not an enterprise device.

---

### Post by hyperhopper on 2009-12-05
well, the thing is, when i play online games, my dad is fine (he runs a really crappy computer, dont know how old it is (ubuntu))

but when i browse the web, i powerbrowse, and have like 50 tabs open, but i use noscript, adblock, and a lightweight firefox. he swears that he gets literally NO internet connection when im browsing, so i want to 

A see who is using how much bandwith at any time.

B limit his bandwith so when he Downloads music it doesnt make my games laggy. (B is optional)

whats the best way to at least monitor how much bandwith each computer is using?

---

### Post by stoogiebuncho on 2009-12-05
Well, on Ubuntu you can go to System > Administration > System Monitor and click on the Resources tab.  It will tell you what your current upload and download speed is as well as how much total you have uploaded and downloaded since the last reboot.

I would imagine Windows has something similar, but I don't know off the top of my head where it is.

---

### Post by cariboo on 2009-12-05
Have a look at bandwidthd, it is in the repositories.

---

### Post by jflaker on 2009-12-05
If it is a matter of you want to slow certain traffic in favor of other traffic, you will need to look at QoS....Quality of Service in your router will prioritize traffic and allow stuff like port 80 (http) a higher priority thus making things faster.  

I am not sure if your router supports QoS traffic control, but that is where to start.  

another option is to look at DD-WRT for your router...this is a replacement firmware which gives you far greater control....get on IRC to make sure you get the right version or you can brick your router....

---

### Post by oldsoundguy on 2009-12-05
One question.

Just WHO is paying the bill?

IF it is your dad, tough darts on your on line gaming being "laggy" (that could be your computer anyway)

If you want to eliminate that .. get your own connection and PAY for it.

---

### Post by Narcolepsy06 on 2009-12-05
> **jflaker said:**
> 
another option is to look at DD-WRT for your router...this is a replacement firmware which gives you far greater control....get on IRC to make sure you get the right version or you can brick your router....

That would be my suggestion too.  If you have a router that is able to run DD-WRT, it does give you a lot more freedom to control the router's connections, and maybe even monitoring.

Unfortunately, the monitoring or bandwidth limiting would have to be done at the router, because the router is the device the traffic is going through.

---

