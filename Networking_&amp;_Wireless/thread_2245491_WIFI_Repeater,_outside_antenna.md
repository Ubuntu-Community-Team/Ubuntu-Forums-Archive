---
title: "WIFI Repeater, outside antenna"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by guitodd2 on 2014-09-24
Looking to set up a WIFI repeater at our place at the lake.  We have a trailer at Lake Merwin and they recently have added "camp-wide" free WIFI from the bath house buildings in each loop. One of these buildings is about 500 feet away.  Walking around with my phone I loose the WIFI signal about halfway up the road.  I have line-of-site to the building from the peak of the roof over my trailer.  I'm looking at mounting a high-gain directional YAGI style (fishbone) antenna to the peak of my building and aiming it at the building housing the WIFI signal. 

I'm having trouble understanding what I need as far as hardware from there.  Digging around the forums, I have found routers that will work as a repeater but am not understanding if I need two devices.......

My hope is to grab the signal with the high-gain outside antenna and repeat the signal at my site so I can use my Iphone, laptops around my site and a ROKU device for Netflix and Pandora at the TV.  My hope is that it doesn't get too complicated in the way that it's fairly reliable.  I'm a decent troubleshooter, but I don't want my wife to have trouble with it if I'm not there.  I'd like to hack a system together but will pay for reliability if that makes sense.

Anybody have any ideas? Or can point me to a good resource to learn more?

---

### Post by tgalati4 on 2014-09-24
A pullbox of Cat6 cable is cheap and will give you 1000 feet.  I would just run it along the ground or string it in the trees.  You will get a couple of years out of it in outdoor use.

As far as repeating WiFi:

[http://www.technewsworld.com/story/79050.html](http://www.technewsworld.com/story/79050.html)

[http://www.wireless-nets.com/resources/tutorials/wi-fi_repeaters.htm](http://www.wireless-nets.com/resources/tutorials/wi-fi_repeaters.htm)

[http://www.pcmag.com/article2/0,2817,2427010,00.asp](http://www.pcmag.com/article2/0,2817,2427010,00.asp)

This is one application where powerline extenders may actually work.  Remote location, assume both points share the same AC voltage-phase, not too much noise from other power sources.

My first choice would be to string up a clothesline.  Weather and distance make this a difficult WiFi solution.  There are laser and microwave solutions, but they are pricey.  Of course, you could also pull fiber, but a simple clothesline would be the best.

Make a map and post it with distances, obstacles, and lines of sight.  Any network topology starts with a map.  You can carve it into a tree trunk with a chainsaw and take a picture with a phone, or just draw it on a napkin.  Watch for bears.  They don't like IT types.

---

### Post by guitodd2 on 2014-09-24
That's funny... running CAT5 would be best but, the issue is that I don't have actual access to the router itself on the other end to plug into it. Believe me!  I eyed the crappy little padlock securing the building, decided that I could bury the line at the gravel road easy enough, and looked for nice trees and the right spray paint color to conceal the CAT5 over the paved road at the building....:-\"

---

### Post by guitodd2 on 2014-09-24
Looking at the links Tgalati4 sent, it appears that a Linksys router will do what I need in repeater mode.  I still need to address the fact that I'm trying to grab a signal out-of-range of the standard antennas.  Not knowing exactly how the radio(s) in the Linksys works.....   I'm wondering if I'd need two matching impedance antennas or if I could simply plug a high-gain outdoor antenna into one side of the unit and if the other antenna on the back will provide me with the site signal.

---

### Post by tgalati4 on 2014-09-24
You can probably get a connection with a tin can and a standard antenna.  The issue is you won't get the bandwidth to stream anything--let alone music.  Most AP's drop to 1 or 2 Mbits/sec at the far end of their range.  I'm familiar with [Meraki]("https://meraki.cisco.com/products/wireless/antennas-power") equipment and you can get decent range and support lots of users, but bandwidth is still poor for streaming at far distances.  OK for email and web browsing.  What type of internet service is available in your neck of the woods?

---

### Post by guitodd2 on 2014-09-24
I'm not sure just yet who the service is through or how they are getting it to each of the 20 common buildings within the 770 acres.  When I snooped around and found the building housing the new WIFI signal, I saw shinny new looking CAT5 cable coming out of a pipe in the ground next to the building which tells me they pulled a lot of cable. It's a mile or so from there to the office where I'd suspect to be the source.

 I then snooped with my laptop and got a full strength signal at the building.  I'm sure I won't get too much for bandwidth if a connection is being split that many ways.....   My though process is that 85-90% of the people that have places up there are too old to care about WIFI and most of that age group are snowbirds and head south for the winter hopefully leaving ME with the best of what there is for bandwidth;)  
We are fairly close to Vancouver Wa. where Comcast is king.  I fear it might be a satellite connection and best I can hope for is that it will be a two-way and not rely on a phone connection for upload bandwidth.

This is a new system that hasn't been published to the population just yet.  I have just been nosey and watching the progress and getting bits of info.  I will figure it out.

---

### Post by guitodd2 on 2014-09-24
BTW.. thanks for the links!  I did't get much actual work done today... but gained some good knowledge on the WIFI topic.   I'll check out the Cisco Meraki stuff too and will post how it goes in case it'll help others.

---

### Post by tgalati4 on 2014-09-25
Well, if you work with the owners, "Those that can articulate the problem are often the ones chosen to fix it."

You could present some ideas and offer to provide some labor to make a better/more useful network topology.  Often networking decisions are based on what is simple and cheap and not performance-driven.  My neighbor's ATT broadband crapped out.  U-Verse broadband running on 60-year-old copper pair that had been wire-nutted together.  And it was running through a DSL filter.  So I'm not sure how they are getting faster than DSL speeds with this setup (as they were sold)--they are not.

Satellite dish internet is a step up from cans-and-string.

---

### Post by guitodd2 on 2014-09-25
Good point.  It's technically a member owned private campground with a board of directors, committees and of property owner volunteers that steer all this stuff.  This might be a good cause to get involved in.  I typically try to avoid the stress of the politics and spend my time there relaxing an fishing..... since this is the kind of crap I deal with at work all day.  But you are right in this case.  If snooping doesn't get me what I need.  'can't hack em.. join em'.

I'm ordering an Amped SR10000 and an external Yagi antenna today.  Going to try it out up there and see what happens.  I can use the higher powered router at home if it's a bust.

---

