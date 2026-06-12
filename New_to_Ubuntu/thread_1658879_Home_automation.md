---
title: "Home automation"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by trocadero72 on 2011-01-03
I am new to both Ubuntu and home automation and in the process of buildning a house (starting this spring) and would like to take the opportunity to "Automate" my house, mostly consisting of central server with media library and web based control of lighting and lastly control and monitoring of "house parameters" like heating power usage etc, without spending a fortune (budget appr 1000€)

Any good tips on where to start and things to include in the building project in order to be able to control it. preferably some easy test projects i can start on, like buying a used plc or something.

Best regards
John

---

### Post by trocadero72 on 2011-01-03
Oh and i forgot, for those providing good assistance there will be a reward in the form of a FREE flight (30 min) over Stockholm, since I live in Sweden

/John

---

### Post by albert s on 2011-01-03
[http://www.cyberhomesltd.co.uk/index.html](http://www.cyberhomesltd.co.uk/index.html)

[http://installautomation.net/?gclid=CMHV--ednqYCFUYe4QodQz5gaA](http://installautomation.net/?gclid=CMHV--ednqYCFUYe4QodQz5gaA)

[http://www.smarthome.com/_/index.aspx](http://www.smarthome.com/_/index.aspx)

I use these guys quite a bit,
[http://cpc.farnell.com/](http://cpc.farnell.com/)

a lot depends on your location, I assume its Europe somewhere by your costing in euros, but where?

although TBH 1000eur wont go very far once you start to control lighting etc.

---

### Post by albert s on 2011-01-03
[http://ehem.com/shop/](http://ehem.com/shop/)

try here, its in swedish so unfortunately I dont understand it much...  :(

---

### Post by trocadero72 on 2011-01-03
Thanx for the info.  anyone know any good forums for home automation?

---

### Post by oldfred on 2011-01-03
I would think about spending most of your budget on configuring the house for the future. Most house control systems are based on wireless as it is very difficult to go back into an existing house and add wiring, but if you do it while it is being build it does not add much to the cost. Hardwired Ethernet connections would be easy to add during construction. 

But will the future change to fiber? While it may not be worthwhile to run fiber, now it may be possible to arrange for conduit to allow adding fiber in the future.  Do not know Swedish electrical codes, but I would investigate what is available from your electrical contractor, if he is familiar with electronic wiring systems like you want.

---

### Post by perspectoff on 2011-01-03
I automated my house some years ago with LinuxMCE.

It was a fun project but I'll not do it again.

A central computer is not the best way to automate a house, generally, IMO. 

I now have local feedback loops for each system instead -- HVAC, lights, pool, sprinklers, outdoor security, etc.

The reason is that my family is more unpredictable than I could anticipate with the settings of a central control system (for lighting, etc.)

Having motion sensors and timers for lights in each room, for example, works far better than centralized control. Further, it is less expensive to implement (the local control modules for a smarthome can cost a fortune, eventually). Further, clever settings for HVAC thermostats works better than central control as well. (Besides, there are microclimates in my house that the central control just couldn't register and adjust for.)

The best system was Zoneminder for surveillance, but that can be installed as a separate package. Recently I saw a $50 home system at Radio Shack that does almost the same thing, though, so I don't think I'd go through the trouble of Zoneminder again, except for work (where I love it).

Further, for shared media, a central NAS (network attached storage) on the home LAN was easier to implement and keep organized than most media centers such as XBMC, Mythbuntu, LinuxMCE, or other thing.

I can stream anything stored on the LAN's central NAS to any computer (or network device such as a network-aware TV) without any tricky configuration.

I ended up getting rid of Mythbuntu, XBMC, and even MythTV for this reason. I just use VLC (or even a plain old web browser with plugins) to watch my media. I use Audacious (or any audio player such as Amarok or Rhythmbox) for streaming audio (and I listen exclusively to Internet Radio over Shoutcast). I associate the media files so that I only have to click on them once (from a File Manager) to start them up in the appropriate application.

This way, my media is available to Windows, Linux, and Mac boxes over the LAN equally. Minimal fuss.

I do recommend at the minimum a wireless-N capable LAN, however. My kids and I all stream at the same time, and 3 or more streams over wireless-G can cause hiccoughs.

---

### Post by trocadero72 on 2011-01-05
Thanx for the info! NAS is also included in the plans and i will satisfy with that now!

The question on how to automate and from what vendor/vendors is still to be solved

/John

---

### Post by rolnics on 2011-01-05
I can't help on any specific points, but I would recommend like  a previous poster, that you make the house future proof. 

Hindsight is a wonderful thing!

Where I work we are now in the 2nd year of a newly refurbished office and in the last few months we've had problems with power due to external reasons. A flood in a basement for one and a distribution board blowing. This has highlighted issues with security, mainly the external doors lock with magnets and what do they need power! If the company had paid a little more in money and attention these doors could have been backup by our generator and we wouldn't have to turn to manually locking each door, just in case the backup battery fails!

So what I'm saying is if you can include in the build stuff for future proofing, the cost should be less then doing after the house is complete.

---

### Post by migs73 on 2011-01-05
try these guys;

[http://www.regin.se/](http://www.regin.se/)

Not cheap but the kit is well built and looks good, oh and they're Swedish.

---

### Post by albert s on 2011-01-05
X10 is IMO deffo the way to go,
and you can control everything from every control point,
ie, turn the bathroom light on using the garage panel,(if you so wish to set it up that way)
you can also connect it to the internet or cellular network so you can change settings when you are not at home etc.
its the dogs dangly bits :KS
but not cheap.  :(

fibre I dont think will really become much of an issue for this sort of stuff as it simply doesnt need the speed.

---

