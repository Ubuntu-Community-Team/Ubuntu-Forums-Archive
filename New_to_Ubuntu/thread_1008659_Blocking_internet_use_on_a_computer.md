---
title: "Blocking internet use on a computer"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-11
Hi. I am running Ubuntu, Hardy heron 8.04. I am the main computer in this household, with another computer (teenage daughter downstairs lol) connected to mine wirelessly. In the past when I have tried to take away internet privileges so `other` things could be accomplished (ie. homework, chores)..well it has not been pretty. So, I am being a coward, I know, ha ha, but I was wondering if there was a way to go into my computer`s settings, and block this other computer from accessing the internet, so it might appear that there is a problem with our ISP, rather than an intentional suspension of privileges,  I already know how to make mine seem that way (work offline setting). thanks for any ideas.

---

### Post by howefield on 2008-12-11
Is it a router which is sharing the internet access between the computers ? 

If yes, you can easily restrict access, but exactly how would depend on the model/make.

---

### Post by bobnutfield on 2008-12-11
If you are using a wireless router, you can go into the routers setting page (usually a web-page at your routers address) and simply disconnect.  My Belkin router offers this by simply clicking disconnect.

---

### Post by halitech on 2008-12-11
if you aren't using wireless on yours (other then to share with your daughter) then just disable your wireless.

just taking a stab based on the way I understand your post.

---

### Post by Lakeside5 on 2008-12-11
I didn`t think I`d get this many and so quickly, responses. I think this is a common issue lol. The Linksys router is hooked up to my computer (usb cable) and to the modem, which is connected to my phone line,adsl. Her computer used to be physically connected with a cable to the router, until our new puppy chewed it in half! Now she connects wirelessly. I don`t know if I want to disable my whole router, as I am learning web serving too, to host a development site and learn Joomla etc.  Is there no way I can just change a setting somewhere in my home network or router to prevent her connecting to my internet, since I`m assuming that my computer is the main computer, the one primarily connected to the internet? thanks guys.
ooops Halitech, just reread your post, can you tell me exactly *how* to disable the wireless? sorry to be so dense lol

---

### Post by Iowan on 2008-12-11
How does her computer get IP address?  If it's via DHCP somewhere, you might feed a "bad" address (outside subnet). If you have your machine set up for [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), you might be able to tweak or shut down the forwarding.

---

### Post by Kellemora on 2008-12-11
Hi Lakeside

It's been a couple of years since I've had to set up my router, knock on simulated wood grain, hi hi........

But it seems to me there was an option to set times allowed and times not allowed for outside connections and there was a different file for each of the plugs in the back.

So I could set jack 1 open between 7AM and 9PM with a closed period from 4PM to 6PM.  Or maybe it was Deny an IP between 4PM and 6PM and between 9PM and 7AM.

The best way to find out is to just go into your router setup tables with a web browser and see what features are available in it.  Or if it allows scripts to be written for it, which would be great too.

TTUL
Gary

---

### Post by handydan918 on 2008-12-11
> **Lakeside5 said:**
> 
ooops Halitech, just reread your post, can you tell me exactly *how* to disable the wireless? sorry to be so dense lol

If you can post the exact make and model of your router, someone can probably google it for you and find the manual online, and figure out how to shut down the wireless transmitter. 

That "someone" might even be you...

---

### Post by howefield on 2008-12-12
Exactly which linksys model do you have, for instance on this page

[http://register.wireless.utoronto.ca/?page=linksys](http://register.wireless.utoronto.ca/?page=linksys)


it describes (point eight) how to add the machines MAC address to the router, you can then permit/deny access as required.

---

### Post by Onesimus on 2008-12-12
You could think about installing Time Keeper.  It is software that is currently been developed to ensure that users have a limited period of time on the computer.  This may be a lot easier than modifying your wireless settings to fool your daughter into thinking that there is a network fault.  Also it may teach her time management on the computer.


Links to Time Keeper can be found at:
[http://ubuntuforums.org/showthread.php?t=887769]("http://ubuntuforums.org/showthread.php?t=887769")

Hope this helps

---

### Post by stevoo on 2008-12-12
What do you mean you are coward ! 

Tell her to do her homework or no computer time. Lock it down ( i remeber my first one used to have a key LOL ) and my dad wouldnt open it until i finished my homework.

She is gonna cry for some days, but eventually she will stop and starts reading faster in order to get more game time. 

If she lies, take her online time away. 
A lot of online time is bad. You need to set a limit into this !

---

### Post by Lakeside5 on 2008-12-12
Ummm..not to get too personal here but.. she is not a little kid, she is 15, and trust me, I`ve tried programs like timekeeper, and `taking away priveleges` before, but then my computer has an `accident` so...(she is what they call ODD, even ran away when I took away the puter and the phone, or even MSN and Facebook, the real root of  all the teenage drama and distracions in her life).  I find it`s just easier for the computer to `malufunction` ocassionally, if you know what I mean, so ya, a bit of a coward maybe, but I just want some  peace as I have a little 7 year old too :).

---

### Post by gpsmikey on 2008-12-12
Been there, done that :mad:  Most of the Linksys routers I have worked with allow you to allow various machines do or do not have internet access (usually by MAC address).  This allows you to configure it so the restricted computers can still share files, get to the printer etc, just don't have internet access.  You can also configure them for specific times.  **[COLOR="Red"]CHANGE THE ROUTER PASSWORD [/COLOR]**):P

I had a problem with my son for a while getting up after we had gone to bed and surfing "inappropriate sites".  What seemed to make as much impression on him as anything was after he managed to get come crap installed again on the system, I told him that since I was going to have to spend the morning cleaning up after him, he was going to spend an equal amount of time cleaning the bathroom - included scrubbing around the toilet with an old toothbrush.  Seemed only fair :lolflag:  Fortunately, that phase has passed (my daughter was never a problem) and all machines are now not restricted at all.

mikey

---

### Post by Paqman on 2008-12-12
> **Lakeside5 said:**
> Now she connects wirelessly.

Depending on what your model of router offers, you should be able to turn off the wifi without disabling the router.

However, I doubt she's going to be fooled. After all, your machine will still be able to connect. You should probably just be straight with her. I'm not surprised you had trouble in the past though. Teenagers these days socialise a lot on the net, so cutting her off totally is pretty harsh. If she's having toruble with getting school work done maybe keep her to a scheduled period of no internet access every night that you both agree on?

---

### Post by Lakeside5 on 2008-12-12
To Howefield and handydan918: I have this router:Linksys BEFW11S4 V4
I will follow up on everyone`s suggestions when I get a chance. I do have another related problem, that I really hope someone could help me with. I have tried before to just look at my network connections, and disable the wireless, BUT I can`t seem to get in there. I mean, I go to: System..Administration..Network, and click on Network, but it never comes up. I was just now able to ge into network by doing: Places..Network, but am puzzled by what I see there. Here is a screenshot: [[IMG]http://i34.photobucket.com/albums/d104/thortess/th_Network.png[/IMG]](http://s34.photobucket.com/albums/d104/thortess/?action=view&current=Network.png)
I don`t know who or what `Darcy` is, and I can`t seem to delete it, I don`t see anything that says `wireless` specifically, like when I had a (ugh) Windows OS and network, I would just right click on the wireless icon and had the choice to disable.
*edit* Oh, I just noticed it says it is a `Windows Network`(dòh) so maybe not worth what I discovered further, by clicking on the Windows Network icon? There was `MSHOME` and `Workgroup`, MSHOME had: user-14bfde04c7. I am tempted to delte this, as it may be her connection? But it won`t let me do it anyway, says `Operation not supported by backend`  What on earth does that mean? Thanks everyone.

---

### Post by howefield on 2008-12-12
Log into your router and navigate to the page that looks like this and disable wireless..

[http://ui.linksys.com/files/BEFW11S4/v4/1.52.02/WLbasic.htm](http://ui.linksys.com/files/BEFW11S4/v4/1.52.02/WLbasic.htm)

It is an interactive mock up of your router setup pages.

I'm assuming you know how to log into your router ?

---

### Post by LowSky on 2008-12-12
most routers can be logged into using this web adress
you can access it from Firefox,
[192.168.0.1]("192.168.0.1")

You can also retrict access to some websites right from the router. And change the admin password, if she knows it what good is it...  If you worry about her being online too much and not doing homework, and being tough fails because she will run away, then let her run. She will come back. Set rules and don't cave. Best thing to do is always have "family time" something like 6-8 the whole family has to be in the same room. Or if you can't then give rules about her grades, tell her she needs a B average or she looses privalges. No compromises.  If you let her know you are a push over you will never win. Teens are always fghting for freedom, but you need to explain to them that freedom comes at a price.

---

### Post by howefield on 2008-12-12
> **LowSky said:**
> most routers can be logged into using this web adress
you can access it from Firefox,
[192.168.0.1]("192.168.0.1")
Not this one, you don't

It is 192.168.1.1

---

### Post by donkyhotay on 2008-12-12
As mentioned previously in this situation I would log into the router and disable the wireless as well. But one thing to be aware of is that no type of security or 'lock out' is going to be 100% certain. Kids are smart and they're usually better with a computer then many parents think they are. All the solutions we are providing here mean nothing if you have a next door neighbor with an unprotected wireless network. Also, changing the password on the router is good to prevent her from just turning the wireless back on but pushing the little reset button on the back of the router will wipe out that password allowing her to turn it right back on again.

---

### Post by Paqman on 2008-12-12
> **donkyhotay said:**
>  All the solutions we are providing here mean nothing if you have a next door neighbor with an unprotected wireless network.

Good point. If that were the case, she'd be better off logging on to her own network than breaking the law by using someone else's.

---

### Post by Lakeside5 on 2008-12-12
Thanks Howefield, I had to reset my router back to factory default, reset my password, and set some other things for some reason, but in the end I took your advice. Thanks to everyone else who took all this time and effort to help, if this doesn`t work I will be looking into these other suggestions, and also, Paqman, unfortunately you have a point too, but if I see that happening I will not allow it, at least I have the `legal` argument on my side :) thanks again everyone.

---

### Post by Lakeside5 on 2008-12-12
Gpsmikey, I love your solution:) that wouldn`t work here tho, and it`s not just homework, I don`t want internet because she `lives` in the basement from whence she plots sudden `escapes` past midnight via MSN, and cars showing up...trying to clip this `nightlife` sigh. You`re not allowed to lock doors from the inside, so the next best thing is locking up msn. And I hear what some of you are saying, and actually appreciate the input, I guess she is a tough case though, as I have to do some drywalling this weekend, for all the times I `put my foot down` (she likes to punch holes...:twisted:

---

### Post by gpsmikey on 2008-12-12
No, you don't have that quite right -- **[COLOR="Red"]SHE needs to do some drywalling this weekend [/COLOR]**with you supervising.  If she can break it she can fix it - about time she learned that too. :evil:

You are right about not locking doors from the inside, but if you put an embedded magnetic sensor on the door (so she can't get to the wires) connected to an alarm, you can tell when she is leaving.

mikey

---

### Post by donkyhotay on 2008-12-12
I would assume she has the ability (and willingness, which pretty much amounts to the same thing) to override any software restrictions you put on the system. I would probably replace the wireless router with a non-wireless one (and just have her do her homework on the other computer). Remember, it's your network and internet connection so you can do what you want with it. It sounds to me that you have more of a personal problem and less of a technical problem though.

---

### Post by LowSky on 2008-12-12
> **donkyhotay said:**
>  It sounds to me that you have more of a personal problem and less of a technical problem though.

Thats what this comes down to, don't lock up the router, lock up her attitude. :lolflag:

Since we are going beyond the linux help, I have some suggestions.

No Wireless in the house, use only a wired connection.  Unplugg the modem and store when you go to bed. Who pays for her stuff you or her. If she punches holes in drywall, take away her bedroom/bathroom door. runs away, turn off her phone, hell do that now. make her do her own laundry, clean her own room, and don't give her any cash. You set all the rules not her, she is yours until she is 18.

---

### Post by Paqman on 2008-12-13
> **donkyhotay said:**
> Remember, it's your network and internet connection so you can do what you want with it.

That's not really how it works with unruly teenagers. The more you squeeze them, the more they'll slip through your fingers. It's about *resolving* the power struggles between parent and child, not escalating them.

---

