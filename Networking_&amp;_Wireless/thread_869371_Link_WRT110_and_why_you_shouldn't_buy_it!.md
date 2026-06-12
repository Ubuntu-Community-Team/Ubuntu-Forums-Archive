---
title: "Link WRT110 and why you shouldn't buy it!"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by jpastore on 2008-07-24
I have a Dell m90 and I recently Purchased a Linksys WRT110 Wireless N router. 

I now realize that the N protocol is not 100% supported and I can live with that for now. My problem is that I purchased the router around the time Hardy came out. Initiating large file transfers, bit torrent, downloading O/S iso's would cause my wireless network connection to appear as connected but not allow any data to be transmitted requiring that I manually reconnect to my wireless network. 

The first thing I did was see if there was a firmware update. There was not, the stock firmware was it. So I contacted Dell, they have a Linux team that's very friendly and in the U.S. so you don't have to deal with some script reading idiot with a horrible accent in India that won't pay attention to what you say...kinda like the Linksys support team...I'll get to that in a minute.

I got Dell to RMA the wireless card in my laptop, an Intel 3945-g card...twice...

Through some useful advice in #ubuntu on irc.freenode.net I reloaded various modules and libraries and got everything working... but still large transfers ruined my day...Which is annoying because, putting aside the recreational/research downloads... I download postgresql dumps from clients on a regular basis for a variety of support reasons... 

I went so far as to buy the N version of the Intel 3945.

Same problem.

Little research turned up that some other Ubuntu users were having a similar problem, one user solved it by returning the router and buying a Netgear. I personally love Cisco and Linksys...up until about last night...

After spending hours on live chat with 4 different support reps because reboots disco'd my network connection...I finally got them to say you should connect our RMA department to get this resolved.

So I did, but I explained to them that through a wired a connection everything was fine, from my wife's XP laptop wirelessly everything was fine...only from my Ubuntu box was there a problem. 

I've had problems in the past where driver updates required a firmware update...my previous XPS had a driver update and whenever I connected to the network I kicked everyone else off until I updated the firmware. So I checked again and w00t there was an update to 1.0.04...did a firmware update...still the same problem...

So I went to my friends house who had a Linksys WRT54g...hey look no problems...I went to another location with a different router...I forget the make and model but same thing: everything was good...

only at home with the wrt110 was there a problem. 

So by process of elimination it looks like this driver and that firmware have a hard time talking to each other. I'm going to guess that the problem is on the Linksys side since this wouldn't be the first time and I can communicate with other devices fine...

They wanted to replace it with the same model. I tried to use logic and reason but the low wage script reading idiots on the other end of the phone wouldn't see reason and blocked me with company policy...we can only exchange like model for like model...we cannot do a model exchange...I said it's clearly pointless to replace with the same model but they wouldn't have it...I even offered to take a refurb of a lesser model...I just wanted something that would work. 

Coincidently, I happened to have a new WRTU54G-TM As I just switched from Vonage to T-Mobile to save $15 a month...not to rant off topic but 

<rant>
Vonage now charges a $40 disconnect fee and there's a lot of other hidden charges like the activation charge...somehow my bill was $95. They couldn't explain where they other $55 came from...that's getting disputed...
</rant>

So interestingly enough when I got the new router running at the head of the network I fire up azureus since that kills my network connection the fastest and everything seemed ok until I saw intermintently that my speed would drop to 0kbs... So I tried changing the MTU in the router to 1300 and everything is rocking pretty solid now...

Previously I was a little reluctant to switch out my router because my cable company issues static ip's based on the mac of the router and again this is another team of underpaid morons that are generally don't care about anything...(Advanced Cable Communications in South Florida better than DSL but their support just sucks) and the management team is really cheap... so no chance I'll ever see DOCSIS3 while I live here until well after FIOS comes to town...

Long and sort of it is...don't buy the Linksys WRT110...the support staff upset me so much I'll buy netgear from now on...now sure how I feel about buying Cisco anymore either...I know it's a different division...but on principle alone I very annoyed...

so right now I lost my static ip needed for some of the work I do and hopefully I'll get that resolved when level 2 support comes to work tomorrow...

---

