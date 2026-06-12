---
title: "How hot is too hot?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-04-09
I've got an HP laptop, which is about 2 years old. 1.6GHz AMD Turion 64x2 processor, 1GB memory, nvidia 6150 geforce GO integrated graphics, etc. it gets the job done.

Anyway, I'm converting some .avi files to dvd using devede and my laptop is getting pretty warm. The fan is cranking out some major heat. There isn't much dust, certainly none blocking the airways.

So my GPU reading (from the gnome applet I've got) is 86C, which is confirmed by the nvidia control panel. My CPU is at 70-71C.

Is it normal for a laptop to get that warm? I'm only using 390MB of RAM, and each core of my CPU is running between 25-100% over time, but mostly trading off between 50% and 85%.


Bottom line: how hot is too hot for the CPU and GPU? Should I be worried about running my computer too hard for too long? E.G. 3+ hours doing an .avi to .iso conversion at around 65C

Maybe I should look into external cooling fans, or prop my laptop up off my desk?

---

### Post by accooper on 2009-04-09
I have always been told that to get the longest life from a DVD burner you should not burn more than 3 in a row, and wait about 30 minutes before burning more.

:guitar:

Andrew

---

### Post by SuperSonic4 on 2009-04-09
Eh, I wouldn't like to run it that high, I think my BIOS says the CPU cut off is 85C and the System is 65C

---

### Post by Mokoma on 2009-04-09
if you have the know how, invest in some decent thermal paste and use it on both the cpu and gpu

---

### Post by Lazy-buntu on 2009-04-09
> I have always been told that to get the longest life from a DVD burner you should not burn more than 3 in a row, and wait about 30 minutes before burning more.

I'm not burning anything though. 

I'm converting some avi files to dvd. 3 AVI --> 1 DVD

I'll give my computer a chance to cool down before I burn the DVD, but it's in the middle of the conversion still. I'm looking to find out basically what the thresh hold temperature for a laptop CPU/GPU should be. Do I need to set these up in Ubuntu?

---

### Post by Mokoma on 2009-04-09
> **Lazy-buntu said:**
> I'm not burning anything though. 

I'm converting some avi files to dvd. 3 AVI --> 1 DVD

I'll give my computer a chance to cool down before I burn the DVD, but it's in the middle of the conversion still. I'm looking to find out basically what the thresh hold temperature for a laptop CPU/GPU should be. Do I need to set these up in Ubuntu?

is it a nvidia intergrated chip??

---

### Post by mkvnmtr on 2009-04-09
Right now my desktop is running 43C, 36C and 30C. My laptop I have never been able to get lm-sensors working on but when it feel warm ton the touch I put an external fan on it. I am no expert but I have had a couple of laptops shut down because of heat. If one gets to 50 C I start worrying.

---

### Post by Mokoma on 2009-04-09
meep

---

### Post by EnglishSparrow on 2009-04-09
My laptop never gets above 70C EVER. My desktop only reached that high when a wire got caught in the cpu fan. I run devede and my cpu works at 100% also with around 60C temps.


80C could melt the plastic on your laptop. My friend had his reach 84C and his laptop melted to the couch:lolflag:

I would put it in front of an A/C or a fan of some kind. And 86C gpu? Wow, you could fry an egg on that keyboard I imagine by now!

---

### Post by Mokoma on 2009-04-09
> **EnglishSparrow said:**
> My laptop never gets above 70C EVER. My desktop only reached that high when a wire got caught in the cpu fan. I run devede and my cpu works at 100% also with around 60C temps.


80C could melt the plastic on your laptop. My friend had his reach 84C and his laptop melted to the couch:lolflag:

I would put it in front of an A/C or a fan of some kind. And 86C gpu? Wow, you could fry an egg on that keyboard I imagine by now!

my 8800 runs at over 90c unless the fan is maxed to 100%

---

### Post by FrankT-Qc on 2009-04-09
Well, actually your machine is built to limit itself to safe temperatures...  If it starts shutting down on you, you're playing in the danger zone if it's just hot to the touch, I wouldn't be too worried about temperature.


A little exception for your battery... You can drastically shorten it's life by keeping it too hot. When you do intensive stuff, you could take the battery off...

---

### Post by EnglishSparrow on 2009-04-09
> **Mokoma said:**
> my 8800 runs at over 90c unless the fan is maxed to 100%

Sounds like you have some heating issue? My 8600GT idles 34C. Playing games it reaches 70C. GPUs these days can take 150C+, but a laptop...

---

### Post by Lazy-buntu on 2009-04-09
GPU is nvidia 6150 geforce GO

---

### Post by Mokoma on 2009-04-09
> **Lazy-buntu said:**
> GPU is nvidia 6150 geforce GO

run this script and see if it makes any difference

---

### Post by Mokoma on 2009-04-09
> **EnglishSparrow said:**
> Sounds like you have some heating issue? My 8600GT idles 34C. Playing games it reaches 70C. GPUs these days can take 150C+, but a laptop...

no these things run hot dude. the 4870x2 runs at 90c idle so its really nothing

---

### Post by Mokoma on 2009-04-09
> **Mokoma said:**
> run this script and see if it makes any difference

ugh, stupid thing.

run this script

---

### Post by Lazy-buntu on 2009-04-09
I don't even think my laptop idles at 50C lol. I'll post my idle temperatures when I give my laptop some time to cool down.

---

### Post by jdong on 2009-04-09
In general, these chips are designed for sustained operation at around 90-100C; check the specs on the chip to be sure.

---

### Post by loomsen on 2009-04-09
> **EnglishSparrow said:**
> My laptop never gets above 70C EVER. My desktop only reached that high when a wire got caught in the cpu fan. I run devede and my cpu works at 100% also with around 60C temps.


80C could melt the plastic on your laptop. My friend had his reach 84C and his laptop melted to the couch:lolflag:

I would put it in front of an A/C or a fan of some kind. And 86C gpu? Wow, you could fry an egg on that keyboard I imagine by now!

Never! Even the default threshold for !slowing down - not shutting down! set by the nvidia guys is 110°C.

Melting on the couch *lol* was it a FisherPrice My1stNotebook?

---

### Post by Lazy-buntu on 2009-04-09
> **Mokoma said:**
> ugh, stupid thing.

run this script

Isn't nvclock used to over clock? Why would I want to over clock my graphics?

edit: According to the nvidia control panel (Nvidia X Server Settings) it's default cut off is 130C

---

### Post by Mokoma on 2009-04-09
> **Lazy-buntu said:**
> Isn't nvclock used to over clock? Why would I want to over clock my graphics?

its can also control fan speed, its what i use to control my 8800 fan

---

### Post by Shpongle on 2009-04-09
my laptop gets really hot some times but , its never shut down or anything, id keep an eye on it tho , make sure the fans are not being blocked  even if you have to raise it with some books or stuff.


on a quick note about devede , its great iv used similar apps in windows and it has taken days (for real) to convert vids where as devede usually takes at most an hour, and doesnt hog all the system resources. im sure thats due to the efficiency of linux too though

id research your system to see if its a common issue too, and back up your stuff just in case. . . you never know

---

### Post by Lazy-buntu on 2009-04-09
Seeing as the default "Slowdown Threshhold" is 130C, and it's showing 85C in the yellow (color coded, red being hot), do I need to ramp up my fan speed?


Also, where would I find the CPU thresh hold temp?

---

### Post by Mokoma on 2009-04-09
> **Lazy-buntu said:**
> Seeing as the default "Slowdown Threshhold" is 130C, and it's showing 85C in the yellow (color coded, red being hot), do I need to ramp up my fan speed?


Also, where would I find the CPU thresh hold temp?

dude try that script, see if it makes any difference!!

---

### Post by Lazy-buntu on 2009-04-09
> **Mokoma said:**
> dude try that script, see if it makes any difference!!

No offense, but you've got 19 posts and no reference for the script contents :lol:

---

### Post by Mokoma on 2009-04-09
> **Lazy-buntu said:**
> No offense, but you've got 19 posts and no reference for the script contents :lol:

DOH >.< 

im not trying to hack you!!

that script gets nvclock and forces the fan speed to 100%, if your gpu even has a controllable fan!

---

### Post by Yvan300 on 2009-04-09
Heat and laptops come in the same package, because they are so compact, heat escape has always been a problem to manufactures. I myself realize that my cpu temperature will rise at times, especially when playing games, never got a system shut down from the heat but performance would decrease instead. My 2 ghz processor would clock at 1 - 1.5 ghz to prevent the production of heat. Must be some built in function from AMD :)

---

### Post by Joeb454 on 2009-04-09
> **Yvan300 said:**
> My 2 ghz processor would clock at 1 - 1.5 ghz to prevent the production of heat. Must be some built in function from AMD :)

I think most modern processors support CPU scaling, which sounds like what you were experiencing there :)

---

### Post by Mokoma on 2009-04-09
> **Joeb454 said:**
> I think most modern processors support CPU scaling, which sounds like what you were experiencing there :)

zzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by stalkier on 2009-04-09
> **Lazy-buntu said:**
> I've got an HP laptop, which is about 2 years old. 1.6GHz AMD Turion 64x2 processor, 1GB memory, nvidia 6150 geforce GO integrated graphics, etc. it gets the job done.

Anyway, I'm converting some .avi files to dvd using devede and my laptop is getting pretty warm. The fan is cranking out some major heat. There isn't much dust, certainly none blocking the airways.

So my GPU reading (from the gnome applet I've got) is 86C, which is confirmed by the nvidia control panel. My CPU is at 70-71C.

Is it normal for a laptop to get that warm? I'm only using 390MB of RAM, and each core of my CPU is running between 25-100% over time, but mostly trading off between 50% and 85%.


Bottom line: how hot is too hot for the CPU and GPU? Should I be worried about running my computer too hard for too long? E.G. 3+ hours doing an .avi to .iso conversion at around 65C

Maybe I should look into external cooling fans, or prop my laptop up off my desk?

I would invest in a laptop cooler. It brings the heat down A LOT. Trust me. I used my laptop for some major stuff and it used to get hot. When I had the cooler going it was very cool. However, the cooler dont last too long. About 6 months or so running all the time. Not too bad though.

---

### Post by Lazy-buntu on 2009-04-09
What are some good practices for keeping your hardware in good shape (preventing damage or wear and tear do to heat)? Like only run it hard for X amount of time straight. After X amount of time, give it Y amount of time to cool down. Things like that.

Update: after conversion was finished I'm down to 46C CPU and 71C GPU temps, which aren't too abnormal I don't think.

---

### Post by loomsen on 2009-04-09
> **Mokoma said:**
> run this script and see if it makes any difference

Well, chapeau, this is one of the worst pieces of code I've ever heard anyone call a "script"

:D 

1st line produces an error with superuserprivileges
2nd line forces your card to enable support for unsupported hardware? Why would you do that? (despite the lack of reason, you most likely aren't allowed to access your device directly anyway.)

Jeez, I do not think it's the script what controls your card. You didn't even specify any environment.

So, no use for running it, it would only produce errors anyway (if it would run at all)

---

### Post by blueridgedog on 2009-04-09
> **Lazy-buntu said:**
> I've got an HP laptop, which is about 2 years old. 1.6GHz AMD Turion 64x2 processor, 1GB memory, nvidia 6150 geforce GO integrated graphics, etc. it gets the job done.

Anyway, I'm converting some .avi files to dvd using devede and my laptop is getting pretty warm.

Others have commented on the heat issue, I just wanted to mention that the root cause the the intense CPU activity associated with the encoding.  I also do a good bit of video encoding and transcoding, but would not do it on a laptop.  The processing runs the CPU at 100% for a long time.

As an aside, have you looked at potentially down clocking your CPU as a test?

---

### Post by loomsen on 2009-04-09
> **Lazy-buntu said:**
> 
Update: after conversion was finished I'm down to 46C CPU and 71C GPU temps, which aren't too abnormal I don't think.

solid avg.


> I would invest in a laptop cooler. 

So did I, but in a passive one :) Just a piece of swung metal which makes my notebook a notebook a notebook "air" :D

(I wouldn't buy an active cooling device cause of the noise...)

---

### Post by loomsen on 2009-04-09
> **blueridgedog said:**
> Others have commented on the heat issue, I just wanted to mention that the root cause the the intense CPU activity associated with the encoding.  I also do a good bit of video encoding and transcoding, but would not do it on a laptop.  The processing runs the CPU at 100% for a long time.

As an aside, have you looked at potentially down clocking your CPU as a test?

[You could try this too, significantly improved the governance and controls on my notebook as the first screenshot shows](http://www.thelinuxnewb.com/)

---

### Post by accooper on 2009-04-09
My son has a Gateway and the bottom of his laptop is quite warm to the touch.

I do know converting AVI files to DVD is VERY CPU intensive and the more work the CPU does the hotter it gets.

:guitar:

Andrew

---

### Post by Mokoma on 2009-04-09
> **loomsen said:**
> Well, chapeau, this is one of the worst pieces of code I've ever heard anyone call a "script"

:D 

1st line produces an error with superuserprivileges
2nd line forces your card to enable support for unsupported hardware? Why would you do that? (despite the lack of reason, you most likely aren't allowed to access your device directly anyway.)

Jeez, I do not think it's the script what controls your card. You didn't even specify any environment.

So, no use for running it, it would only produce errors anyway (if it would run at all)

thats funny it works perfectly on my desktop and laptop.......maybe you dont know how to run a script properly >.>

---

### Post by loomsen on 2009-04-09
...

Actually I didn't want to expose you like that, but, now that you did that work:

[quote="Your script"]
sudo apt-get nvclock
nvclock -f -F 100
[/quote]

Do you know what a script is?

Your passing nvclock as an option to apt-get...resulting:
> 
docter[~] sudo apt-get nvclock
E: Invalid operation nvclock
docter[~] 


It's not even executable, how could it be without a definition of any SYSPATH

---

### Post by Mokoma on 2009-04-09
> **loomsen said:**
> ...

Actually I didn't want to expose you like that, but, now that you did that work:



Do you know what a script is?

Your passing nvclock as an option to apt-get...resulting:


It's not even executable, how could it be without a definition of any SYSPATH

heres a screen of it working perfectly........

---

### Post by Mokoma on 2009-04-09
yeah. you also defeated your own argument. if it wasnt executable you wouldnt get the 

"E: Invalid operation nvclock"

you would get

"bash: /home/whateveryourusernameis/whereveryoudownloadthescripttoo/nvclock.sh: Permission denied

please only call my script bad if you know what your talking about >.>

also the script is 

sudo apt-get INSTALL nvclock
nvclock -f -F 100

just for the record :)

---

### Post by loomsen on 2009-04-09
LOL

keep going :D

---

### Post by Mokoma on 2009-04-09
> **loomsen said:**
> LOL

keep going :D

with what? ¬¬

---

### Post by loomsen on 2009-04-09
Honestly?

Buddy, you initially posted the script 2 hrs ago, last changed your post 19 minutes ago, your current attachement has 0 views yet, jeez, is this your first time on the internet alone or are you just drunk?

---

### Post by Mokoma on 2009-04-09
> **loomsen said:**
> Honestly?

Buddy, you initially posted the script 2 hrs ago, last changed your post 19 minutes ago, your current attachement has 0 views yet, jeez, is this your first time on the internet alone or are you just drunk?

yeah and i double checked the original script. it works. why are you trying to start a fight?

---

### Post by loomsen on 2009-04-09
My goodness... 
You penetrated that other guy in like 7 posts to finally run your "script", otherwise I wouldn't even have looked at it. :D

That's it, now you got me, I ran out of trollfood.

---

### Post by Mokoma on 2009-04-09
> **loomsen said:**
> My goodness... 
You penetrated that other guy in like 7 posts to finally run your "script", otherwise I wouldn't even have looked at it. :D

That's it, now you got me, I ran out of trollfood.

wtf are you talking about. if your going to start an argument make sense >.<

---

### Post by jmate24 on 2009-04-09
mine gets to about 87C but i have had no trouble with it and i encode videos from dvd using thoggen. but what i do to keep it there is i prop up the front of my laptop with a thin hard plastic hard drive box that i got when i received my terrabyte hard drive so that there would be more air flow underneath. i am going to have to invest in a laptop cooler though (it is an inch thin box with a fan inside that blows air into and away from the bottom of my laptop. i just set my laptop on top of it and it has batteries)

So be smart and safe and purchase one of those. plus if you leave your laptop on a soft surface (i.e. couch, bed, lap, &c., &c) then you are sure to have a burnout (either the laptop, you yourself, or a FIRE HAZARD)

Jmate24--

---

### Post by Tyke91 on 2009-04-09
Both trolls keep it down and lets talk about laptop heating... and for the record, instead of writing a script, why not tell him to just copy/paste those two lines? >.<

I generally keep mine raised (with books) or on a table with good ventilation (i've got a cast iron mesh coffee table :P )

I don't usually have heating issues, although my NVidia 9800 in my desktop did hit 100C before I figured out how to turn the fan on :D now it idles at 45

---

### Post by jdong on 2009-04-09
Just a friendly reminder to keep it civil in here; no need to get heated up over a script when it's the GPU that's burning ;-)

---

### Post by Lazy-buntu on 2009-04-09
> **jdong said:**
> Just a friendly reminder to keep it civil in here; no need to get heated up over a script when it's the GPU that's burning ;-)

You can laugh when it's not your GPU :lol:

Anyway, it seems like one of the previous posts was right.Encoding video is highly demanding of the CPU. After the task was done, the CPU cooled downed very quickly.

Now on to a different problem, but I saved that for another thread.

Side question: where did they move the "mark thread as solved" button to?

---

### Post by jdong on 2009-04-10
> **Lazy-buntu said:**
> 

Side question: where did they move the "mark thread as solved" button to?

/dev/null for now... It was identified as one factor in the slew of database corruption events we were experiencing a while back...

---

### Post by Mokoma on 2009-04-10
the guy was trying to start a fight, it was as civil as it could be >.<

---

### Post by x C0MMAND0 x on 2009-04-10
Check out my thread on this same topic from a while ago.

[http://ubuntuforums.org/showthread.php?t=1006632](http://ubuntuforums.org/showthread.php?t=1006632)

---

### Post by skintythe1andonly on 2009-05-03
I have exactly the same laptop and have been running ubuntu since Fiesty. I have never noticed my fan when idle ever until I upgrated to jaunty. The fan is on all the time now and my GPU temp is just below 80 degrees most of the time. This is not good. I think there are two issues here. Most people who say its ok possibly are running desktops, which is plugged in the whole time. Since my udate, Ive seen my battery life decrease by about 30%. I invested in a 9 cell battery which also props up the laptop, and allows vertilation.

---

### Post by jmate24 on 2009-05-04
as i have said b4, invest in a laptop cooler!! you just install batteries and turn it on then set your laptop on it and it does the rest!!

I have even jerry-riged 2 old cpu fans and proped my laptop on 2 Zip 100 and 2 floppy drives placed one fan under near the cpu fan and made sure that it was blowing up into the laptop cpu fan and then with the other i set it on its side next to the vent and have it blowing outward.

so far i have reduced 87C to 74C!!

---

### Post by CrystalShadow on 2009-05-05
You have to keep in mind a few things.

Yes, that's a very high temperature, and that's not good for batteries.

BUT, laptops inherently have cooling issues. (and don't be tempted to put one on a soft surface, like for instance a bed.)

Ubuntu told me my CPU temperature while idle was 57 celsius.
And you know what? That doesn't even seem high to me given how hot my laptop generally feels. That's just the way it's built.

Have a look at CPU specs some time too. It might surprise you, but the 'safe' operating temperature of a laptop cpu is typically at least 20 celcius higher than a desktop equivalent.

Eg, if the desktop CPU hits thermal cutout at 90 celcius, the laptop equivalent will often still be alright until it hits 110...

That's just the reality of laptop cooling...
The only major problem is that heat + Lithium Ion batteries is not a good combination.

---

