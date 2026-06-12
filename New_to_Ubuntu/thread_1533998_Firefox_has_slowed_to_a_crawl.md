---
title: "Firefox has slowed to a crawl"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by jfloydb on 2010-07-18
Somehow (perhaps after the last updates) Firefox has slowed to a painful crawl. Any suggestions? I like Firefox, but can anyone suggest a different, faster browser? Thanks.

---

### Post by aeronutt on 2010-07-18
Chrome.

---

### Post by k3lt01 on 2010-07-18
> **aeronutt said:**
> Chrome.Better still- Chromium! It is Chrome without all the Google tracking added to it.

Do you have any add-ons installed in FireFox? Sometimes they will slow it down especially after an update.

---

### Post by spcwingo on 2010-07-18
You can try disabling ipv6.  To do that in the address bar on Firefox enter:

```
about:config
```

Then in the filter dialog enter:

```
ipv6
```

On the one entry just double-click it.  ;)

---

### Post by Talon2 on 2010-07-18
[http://www.google.com/chrome/](http://www.google.com/chrome/)

---

### Post by Chris1274 on 2010-07-18
SeaMonkey is great. It's like Firefox lite, very fast.

---

### Post by QIII on 2010-07-18
Hey, guys.  How about doing something different and actually attempting to solve the OP's problem before just saying to use something else?

jfloydb - Please have a look at lovinglinux' blog.  He posts here.  He has a lot of extremely good information on his blog.  It may very well be that he will be along to help.

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

---

### Post by k3lt01 on 2010-07-18
> **QIII said:**
> Hey, guys.  How about doing something different and actually attempting to solve the OP's problem before just saying to use something else?Wow an original thought! If you read abov your post some of us have actually and also answered his other question as well by giving a recommendation of other browsers.

---

### Post by Wragie on 2010-07-18
Stumbled across this thread and also had noticed the slows in firefox. The disable ipv6 has it smokin along nicely now. 

Now if I can get it to open in new tabs all the time instead of windows and tabs I'd be happy.

THANKS!!;)

Dave

---

### Post by techunit on 2010-07-18
> **Chris1274 said:**
> SeaMonkey is great. It's like Firefox lite, very fast.
Seamonkey is firefox (just with more... same browsing engine)... it is made by the same company...

---

### Post by techunit on 2010-07-18
> **techunit said:**
> Seamonkey is firefox (just with more... same browsing engine)... it is made by the same company...
I would recommend that you try reinstalling firefox...

```
sudo apt-get reinstall firefox
```

if that doesn't help then try deleting the .firefox folder in your homefolder. Hit CTRL H to bring up the hidden files and delete the .firefox folder... (note this will reset firefox so please back up your bookmarks..

---

### Post by dmiracle74 on 2010-07-18
> **jfloydb said:**
> Somehow (perhaps after the last updates) Firefox has slowed to a painful crawl. Any suggestions? I like Firefox, but can anyone suggest a different, faster browser? Thanks.

I would check what add-on's you have installed.  One of them may not like the version you are using.  Firefox does a pretty good job checking an addon for compatibility when it loads but some slip through the cracks.
To see if it is an addon open a terminal session and type in firefox -safe-mode that will disable them until you exit.

You may also try to empty your browser cache....though a plugin or addon program is more likely.

Dale

---

### Post by Talon2 on 2010-07-19
> **QIII said:**
> Hey, guys.  How about doing something different and actually attempting to solve the OP's problem before just saying to use something else?

Hey Ace, read the OP's original message.  He asked for something else.

---

### Post by owners4life5 on 2010-07-19
i don.t have much experience with firefox... but i can answer half of your question.

go to 
[http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by jfloydb on 2010-07-19
Thanks for the replies. The only add-on that I'm using in Firefox is Add Blocker Plus. At this very moment I am trying Chromium. I think that I could like it, but the scroll-bar doesn't have any up or down arrows (at least not on my screen), which makes fine scrolling problematic. I will consider all the advice, even disabling ipv6 and/or re-installing Firefox. Thanks again.

---

### Post by dmiracle74 on 2010-07-19
> **Talon2 said:**
> Hey Ace, read the OP's original message.  He asked for something else.
No actually in his first part of his sentence he asked for suggestions about the problem, then he asked for other browsers.
So actually there was two questions. ;-)

---

### Post by Kellemora on 2010-07-19
Hi jfb

The latest versions of FireFox are loaded with bugs.

The last known properly working version of FireFox was version 3.6.3

When they released version 3.6.4 it was messed up royally and wouldn't even run on some computers.
Within a day or two, they popped out with version 3.6.5 which was supposed to correct the non-loading issue, 
Then a couple of days later, they came out with 3.6.6 and all it did was make the memory leak from 3.6.4 move elsewhere, they actually made the problem worse.
FireFox beyond version 3.6.3 is NOT compatible with Flash!

Rather than undoing the mess they made, they are working on FireFox 4 now, so any chance of getting the mess they turned version 3 into just ain't gonna happen now.

If version 4 has the same problems, after using FireFox for years, I will just find another browser and consider FireFox ancient history.
One often wonders WHAT ON EARTH they were thinking when they destroyed a great program?

TTUL
Gary

---

### Post by k3lt01 on 2010-07-19
> **Kellemora said:**
> FireFox beyond version 3.6.3 is NOT compatible with Flash!Sorry but that is just so incorrect it isn't funny. I, and many others, are currently on 3.6.6. I visit some pretty heavily laden flash sits and believe me there is NO problem with flash and FF. If you are having difficulties I would suggest you start doing some detective work on your setup and find out what is actually the problem.

Also if you have a memory leak have you done anything to find it? have you filed bug reports? have you attempted to help the Moz.devs. fix it (that is if it is actually FF causing the issue). I have a pretty weak (read old, lame, low powered and poverty pack) laptop and FF doesn't give it any grief whatsoever.

---

### Post by lovinglinux on 2010-07-19
> **QIII said:**
> jfloydb - Please have a look at lovinglinux' blog.  He posts here.  He has a lot of extremely good information on his blog.  It may very well be that he will be along to help.

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)

I'm here :) How can I help?

I would start by installing and running [SQLite Optimizer](https://addons.mozilla.org/en-US/firefox/addon/11198/). You will see the difference after running it.

> **jfloydb said:**
> Thanks for the replies. The only add-on that I'm using in Firefox is Add Blocker Plus. At this very moment I am trying Chromium. I think that I could like it, but the scroll-bar doesn't have any up or down arrows (at least not on my screen), which makes fine scrolling problematic. I will consider all the advice, even disabling ipv6 and/or re-installing Firefox. Thanks again.

Is not just only the lack of scroll bars. It lacks several things and can't be customized at all. Lots of people like it, but I don't. I still think Firefox is a much better browser and it works perfectly here, even with more than 60 extensions installed.

> **techunit said:**
> if that doesn't help then try deleting the .firefox folder in your homefolder. Hit CTRL H to bring up the hidden files and delete the .firefox folder... (note this will reset firefox so please back up your bookmarks..

Is not just your bookmarks that are deleted, but also passwords, extensions (including their databases), all Firefox settings, cookies and so on.

I don't like to recommend this method and I ask other users to not spread it. Instead I recommend creating a new profile using the profile manager and testing it. If it works, then you can copy some important files from the old profile. See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

> **Kellemora said:**
> Hi jfb

The latest versions of FireFox are loaded with bugs.

The last known properly working version of FireFox was version 3.6.3

When they released version 3.6.4 it was messed up royally and wouldn't even run on some computers.
Within a day or two, they popped out with version 3.6.5 which was supposed to correct the non-loading issue, 
Then a couple of days later, they came out with 3.6.6 and all it did was make the memory leak from 3.6.4 move elsewhere, they actually made the problem worse.
FireFox beyond version 3.6.3 is NOT compatible with Flash!

Rather than undoing the mess they made, they are working on FireFox 4 now, so any chance of getting the mess they turned version 3 into just ain't gonna happen now.

If version 4 has the same problems, after using FireFox for years, I will just find another browser and consider FireFox ancient history.
One often wonders WHAT ON EARTH they were thinking when they destroyed a great program?

TTUL
Gary

I'm tired of replying this message across different threads. Looks like your are campaigning against Firefox and ignoring my replies. The information you are spreading is totally incorrect: 

[LIST]
[*]firefox works perfectly, including versions 3.6.3, 3.6.4 and 3.6.6
[*]there is no version 3.6.5, never was
[*]version 3.6.6 was released to increase crash protection timeout and not several bugs as you claim
[*]I have no memory leaks with any of those versions and haven't seen complains about that, except from you
[*]Firefox 3.6.3 and above ARE compatible with flash (I have no problems with flash whatsoever) and since 3.6.4 it doesn't crash the browser due to flash plugin isolation
[*]they are working on Firefox 4 a lot longer than you think and just renumbered version 3.7
[/LIST]

---

### Post by Linux000 on 2010-07-19
Chrome, it is superfast, and doesn't slow down.

---

### Post by lovinglinux on 2010-07-19
> **Linux000 said:**
> Chrome, it is superfast, and doesn't slow down.

Try to open a bunch of pages and you will see how much memory it uses. That can cause overall slow down in some systems.

---

### Post by QIII on 2010-07-19
> **Talon2 said:**
> Hey Ace, read the OP's original message.  He asked for something else.

What did he ask for first?

---

### Post by Linux000 on 2010-07-19
I've opened tons of tabs, 53 or so tabs and it only used 290MB of ram. But to clarify, I've never had it slow down, with 2GB of ram.

---

### Post by QIII on 2010-07-19
> **k3lt01 said:**
> Wow an original thought! If you read abov your post some of us have actually and also answered his other question as well by giving a recommendation of other browsers.
 
Actually, I did.

One poster gave a possible solution without reference to another browser.  Since the OP's first question was asking for help with Firefox, he got it right.

Yours contained a suggestion.  However, it came after suggesting another browser.

All other answers went to other browsers, and the root problem was otherwise ignored.

I have nothing against using another browser.

---

### Post by Linux000 on 2010-07-19
> Since the OP's first question was asking for help with Firefox I thought he asked for suggestions for another browser. >  I like Firefox, but can anyone suggest a different, faster browser?

---

### Post by libssd on 2010-07-19
> **jfloydb said:**
> Thanks for the replies. The only add-on that I'm using in Firefox is Add Blocker Plus.
Ad Blocker Plus can slow FF down a little, but if that's the only one you're running, it shouldn't be that bad. Nevertheless, try disabling it and restarting FF to see if you notice any difference.

---

### Post by lovinglinux on 2010-07-19
> **Linux000 said:**
> I thought he asked for suggestions for another browser.

Indeed he asked, but it seems the OP would prefer to fix Firefox. Anyway, I share QIII frustration, specially in regard to Chrome users. There are tons of threads asking for help with Firefox, that Chrome users like to jump in and instead of providing a solution they recommend installing Chrome. This is really annoying. They tend to turn every support thread into a browser war. 

I have even considered created a banner that says "This is not a Chrome thread" :)

---

### Post by lovinglinux on 2010-07-19
> **Wragie said:**
> Stumbled across this thread and also had noticed the slows in firefox. The disable ipv6 has it smokin along nicely now. 

Now if I can get it to open in new tabs all the time instead of windows and tabs I'd be happy.

THANKS!!;)

Dave


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=163936&stc=1&d=1279566640[/IMG]

---

### Post by oldsoundguy on 2010-07-19
sometimes an ad-on will go south.  Disable one at a time in a process of elimination.
(for instance x-marks went bad on the latest version of FF on this particular computer.  Not sure if it has been fixed yet, but it really borked the browser until I removed it!

---

### Post by lovinglinux on 2010-07-19
> **oldsoundguy said:**
> sometimes an ad-on will go south.  Disable one at a time in a process of elimination.
(for instance x-marks went bad on the latest version of FF on this particular computer.  Not sure if it has been fixed yet, but it really borked the browser until I removed it!

Indeed. I don't use Xmarks anymore because of performance issues. I also had a similar problem when Ghostery was updated recently. It made Firefox very slow, specially when switching tabs. Most of the problems have been fixed on a recent release, but I don't use it anymore.

Anyway, a good place to start would be my [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by ankspo71 on 2010-07-19
> **Wragie said:**
> Stumbled across this thread and also had noticed the slows in firefox. The disable ipv6 has it smokin along nicely now. 

Now if I can get it to open in new tabs all the time instead of windows and tabs I'd be happy.

THANKS!!;)

Dave

Hi Wragie,
Try installing the Tab Mix Plus firefox addon. I remember it having a "single window mode". It has a ton of other tab and window related options.
[https://addons.mozilla.org/en-US/firefox/addon/1122/](https://addons.mozilla.org/en-US/firefox/addon/1122/)
Hope that helps.

---

### Post by k3lt01 on 2010-07-19
> **QIII said:**
> Actually, I did.I'm not to sure about that purely because of the quote below

> **QIII said:**
> One poster gave a possible solution without reference to another browser.  Since the OP's first question was asking for help with Firefox, he got it right.The OP asked 2 (TWO) questions, I think if your being serious anyone who doesn't answer both is doing the OP a dis-service.

> **QIII said:**
> Yours contained a suggestion.  However, it came after suggesting another browser.Does it really, I mean REALLY, matter what order we answer the questions in? Aren't you being a bit to pedantic? What is the problem with asking him a question? I asked him about add-ons, some have problems. It is no use discussing each and every one unless I know what ones he has. Maybe then we could give him the direct assistance he requires instead of leading him up the garden path with a heap of irrelevant detail about stuff he hasn't got.

> **QIII said:**
> All other answers went to other browsers, and the root problem was otherwise ignored.That is up to the individual who replies, I don't think you have a right to chastise anyone for answering how they want to.

> **QIII said:**
> I have nothing against using another browser.Somehow I doubt it, you seem to have an issue with people answering the second part of the OPs question. The fact is he has a problem, some are answering both aspects others are giving suggestions on browsers. I just wonder why you think people giving the advise they want to is a problem.

---

### Post by Linux000 on 2010-07-19
> Indeed he asked, but it seems the OP would prefer to fix Firefox

He still asked for other options, so there's no reason people can't give him other options.

---

### Post by QIII on 2010-07-19
Since my flamethrower seems to have run out of fuel, I will retire.

I hope the OP was able to correct his problem with Firefox.

---

### Post by jfloydb on 2010-07-19
Thanks to everyone for your replies, especially to lovinglinux. I will enter one more post soon to let you all know how everything worked out. Thanks again.

---

### Post by tahitiwibble on 2010-07-20
> **lovinglinux said:**
> Indeed. I don't use Xmarks anymore because of performance issues. I also had a similar problem when Ghostery was updated recently. It made Firefox very slow, specially when switching tabs. Most of the problems have been fixed on a recent release, but I don't use it anymore.

Anyway, a good place to start would be my [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Hello there lovinglinux, I like x-marks a lot, does it always slow FF down? If so, is there an equivalent out there that doesn't? Thanks. :)

---

### Post by ov3rcl0ck on 2010-07-20
Chromium(or chrome) is probably the better idea, Chrome uses webkit which is alot faster than Gecko, which is what Firefox uses. Also Chrome sandboxes all the plugins/extensions, making it more stable, fast, and secure, because they're all in there own process meaning if one crashes the whole browser doesn't go down with it, and it can then also utilize multiple CPUs making it faster.

Tabs/windows are also separated into sandboxed processes to prevent the whole browser from freezing/crashing if only one tab/window freezes/crashes. This also makes it alot faster because now you can use parallel processing for loading 2 different pages.

Chrome is also built with the V8 engine, which is really really fast. It will turn slow Jscript into fast machine code with a JIT compiler.

Chrome/Chromium has sooo many benefits security, stability, and especially speed wise.


> **lovinglinux said:**
> Try to open a bunch of pages and you will see how much memory it uses. That can cause overall slow down in some systems.
Also I've benchmarked this. Recent versions of Chrome(for about the last 4 months), Chrome uses less memory per tab/window than Firefox. Chrome also renders pages about 6 times faster. Also with Chrome no need for bloaty firebug, because chrome has a development tool built right in with the same features, and it doesn't load into memory until you launch it.

---

### Post by k3lt01 on 2010-07-20
@ov3rcl0ck. I use both browsers however I stick to FF more often than not. Why? well because Chromium is a slug on startup, meaning it is extremely slow. The only reason I use it is because I have 2 yahoo email address' and FF wont let me use both easily so my personal one is in FF and my secondary (automotive stuff) one is in Chromium.

When I start Chromium my laptop lags, badly. It is a resource hog while FF starts crisply 99% of the time. Shut down a tab in FF it goes almost instantaneously, try to shut down one in Chromium and .... well .... cuppa coffee anyone???? Chromium may work brilliantly for you but I cannot say it is all that good for me on my laptop. Chrome is even worse, and on my sisters laptop Chrome is just as bad as MS IE.

---

### Post by lovinglinux on 2010-07-20
> **tahitiwibble said:**
> Hello there lovinglinux, I like x-marks a lot, does it always slow FF down? If so, is there an equivalent out there that doesn't? Thanks. :)

No, it doesn't slow down always, just sometimes when syncing. Recently I started to use [Firefox Sync](https://addons.mozilla.org/en-US/firefox/addon/10868/) (aka Weave), which will be a default feature of Firefox 4. Unfortunately, they seem to have screwed with the latest version, hence the several bad reviews on the site. So I would wait for Firefox 4 to be safe.

> **ov3rcl0ck said:**
> Also Chrome sandboxes all the plugins/extensions, making it more stable, fast, and secure, because they're all in there own process meaning if one crashes the whole browser doesn't go down with it, and it can then also utilize multiple CPUs making it faster.

Mozilla introduced flash plugin isolation since Firefox 3.6.4, which works better than Chrome in my opinion. The browser and the tab doesn't crash. Instead you get a notice where the plugin content should be displayed.

"At this time Firefox offers crash protection for Adobe Flash, Apple Quicktime and Microsoft Silverlight on Windows and Linux computers. Support for other plugins and operating systems will become available in a future Firefox release" (aka Firefox 4).

About Chrome extensions, there are some pros and cons. Extensions don't slow down the browser, but are limited in functionality. Additionally, the permission method (least privilege) makes them more secure, but since Google doesn't review any extensions like Mozilla does, is fairly easy for someone to spread a malware extension [with all the permissions it needs](http://thenextweb.com/google/2010/07/09/hacker-creates-plugin-that-trashes-chromes-security). According to [this video](http://www.youtube.com/watch?v=DO-nzPqhdXw), it is only safer for extensions with vulnerabilities.

Here is a quote from the video:

> If you install a malicious extension, all bets are off.

> **ov3rcl0ck said:**
> Tabs/windows are also separated into sandboxed processes to prevent the whole browser from freezing/crashing if only one tab/window freezes/crashes. This also makes it alot faster because now you can use parallel processing for loading 2 different pages.

I agree.

> **ov3rcl0ck said:**
> Chrome/Chromium has sooo many benefits security, stability, and especially speed wise.

I don't see it. You can't customize anything, it lacks features like sidebar, status bar, about:config, themes that can actually modify the interface and not only put an image in the background like Personas does, extensions that can modify the browser itself and you can't even move the toolbar icons to a more useful position.

It is indeed more secure, but I never had any security issues with Firefox, so I don't see this as a benefit to switch. In regard to speed, the javascript performance is really good and you can see the difference when benchmarking it with Peacekeeper, but in the real world it doesn't make any difference to me. I run Firefox with more than 60 extensions and I have no complains.

> **ov3rcl0ck said:**
> Chrome also renders pages about 6 times faster.

No way. I have been comparing Chrome and Firefox lately and I can't see any difference, although Chrome performs milliseconds faster. 

> **ov3rcl0ck said:**
> Also with Chrome no need for bloaty firebug, because chrome has a development tool built right in with the same features, and it doesn't load into memory until you launch it.

I guess you haven't seen the new Firefox 4 Heads Up Display.

---

### Post by Kellemora on 2010-07-20
> **k3lt01 said:**
> Sorry but that is just so incorrect it isn't funny. I, and many others, are currently on 3.6.6. I visit some pretty heavily laden flash sits and believe me there is NO problem with flash and FF. If you are having difficulties I would suggest you start doing some detective work on your setup and find out what is actually the problem.

Also if you have a memory leak have you done anything to find it? have you filed bug reports? have you attempted to help the Moz.devs. fix it (that is if it is actually FF causing the issue). I have a pretty weak (read old, lame, low powered and poverty pack) laptop and FF doesn't give it any grief whatsoever.

Hi K3

We can DUPLICATE the FireFox problems in FLASH on all EIGHT COMPUTERS we have here and each computer is different, some AMD, some Intel, all different makes from Dell, eMachines, Compaq, HP and several built ups.

ZERO problems with version 3.6.3
When they came out with 3.6.4 is when the problems started.
We let them know about the first problem, version 3.6.5 was supposed to fix it.
The memory loss problem (actually failure to recognize mouse clicks and/or store the data) in version 3.6.6 was only relocated to a different area of a test grid.

We duplicated the problem well over 40 times on each computer with exactly the same errors each and every time.
Mozilla received all the test data and they too could duplicate the problem.
Their suggestion:  Use FireFox 3.6.3 until they release version 4!
In other words, they created a problem and then abandoned it!

The problem does not appear in Chrome, Chromium, Safari, Netscape or Mozilla, only in FireFox versions 3.6.4 and up!

Using a grid on a screen with each cell as a function, 100% of the time, the new release of FireFox will show the cell as selected, but fail to record the data from that cell, and on exactly the same cells, no matter how many separate places on the screen we place the grid.
On a 21 cell tall by 7 cell wide grid, the lower 1/3 of the grid misses the data in the shape of an upside down house, identical across all 5 grids we could place on the screen.
As I said, it doesn't matter where we place the grid on the screen, it's the exact same cells that show active but fail to save the data.

If we change the size of the grid, to lets say 9 x 18 it still has the same problem in the same cells, just doesn't make it look like an upside down house is all.  In fact, we had to play with different grid sizes until we hit one that gave the visual appearance of an upside down house.  Else at first the missing data seemed random.

We spent several days setting up to test this LEAK and a few more days trying it out on each and every computer.  It's NOT the computers!  It's NOT Flash!  It can only be duplicated on FireFox versions 3.6.4, 3.6.5 and 3.6.6..........  The problem does not appear on version 3.6.3.......or any previous versions of FireFox for that matter.
The problem started when they released 3.6.4 and only got worse!

TTUL
Gary

---

### Post by itisbasi on 2010-07-20
Get rid off all the add-on bloat and Firefox should get better!! Why not try Opera. According to me it is probably the best browser around, the only thing that it lacks are extensions. If you just can't manage without the addons and extensions, try chrome. Chrome works like a charm even with all the extension bloat.

---

### Post by Irony on 2010-07-20
> **ov3rcl0ck said:**
> Also I've benchmarked this. Recent versions of Chrome(for about the last 4 months), Chrome uses less memory per tab/window than Firefox. Chrome also renders pages about 6 times faster. Also with Chrome no need for bloaty firebug, because chrome has a development tool built right in with the same features, and it doesn't load into memory until you launch it.
Yes but can you drag a bookmark exactly to where you want it?

---

### Post by QIII on 2010-07-20
Kellemora --

Very interesting stuff.

Is what you found a memory leak as defined in computer science terms, or  poor memory use?  I mean, did you examine the source code and run the  application using tools to detect memory leaks?  Are objects created and  memory allocated, but the objects not destroyed and the memory not  released?  If the systems had a limited amount of memory, is the memory  eventually consumed so that other applications or even the OS start  throwing segmentation faults?

I know that a lot of Firefox is written in C and C++.  Did the  developers forget things like destructors, for instance?

I'd be very interested to know.  Poor memory use is crappy.  Real memory  leaks can be dangerous to an OS and possibly even to hardware.

---

### Post by tahitiwibble on 2010-07-20
> **lovinglinux said:**
> Recently I started to use [Firefox Sync](https://addons.mozilla.org/en-US/firefox/addon/10868/) (aka Weave), which will be a default feature of Firefox 4. Unfortunately, they seem to have screwed with the latest version, hence the several bad reviews on the site. So I would wait for Firefox 4 to be safe.

Nice one! Thank you :)

---

### Post by k3lt01 on 2010-07-20
> **Kellemora said:**
> Hi K3

We can DUPLICATE the FireFox problems in FLASH on all EIGHT COMPUTERS we have here and each computer is different, some AMD, some Intel, all different makes from Dell, eMachines, Compaq, HP and several built ups.Good morning Kellemora.

I can honestly say I have never had the difficulty you are describing and I am now refurbishing 2nd hand machines to give away. I have 3 machines I personally use, my father's laptop and 3 I gave away a few weeks ago. None of these machines have this difficulty and I have used and/or tested each machine extensively so I am sure I don't give away something that is going to cause someone to get a bad impression of Ubuntu.

Please trust me, I'm not saying I don't believe you, I'm just saying I have not come across the problem you are referring to.

Is there a bug report on this? if yes what is the number?

---

### Post by steven.c.king on 2010-07-28
> **QIII said:**
> Hey, guys.  How about doing something different and actually attempting to solve the OP's problem before just saying to use something else?

jfloydb - Please have a look at lovinglinux' blog.  He posts here.  He has a lot of extremely good information on his blog.  It may very well be that he will be along to help.

[http://lovinglinuxblog.blogspot.com/](http://lovinglinuxblog.blogspot.com/)
OK. You got a deal.  Here is a fix that I found somewhere, and it stopped my endless waiting for pages to open.  Here is what he said to do:

"
This is how anyone can fix the Firefox slow problem in Ubuntu 10.04
 Open your Firefox and type about:config at URL address bar and hit  enter. To make a False into True, select the line to change, and double  click. On the 2nd option change, right click and select Modify
 - network.http.pipelining > Make it True
 - network.http.pipelining.maxrequests > Make it 8 or 10
 - network.http.proxy.pipelining > Make it True
 - network.dns.disableIPv6 > Make it True
 I hope this helps for some users"


Below is the link; it worked for me.



[http://crenk.com/fix-the-firefox-slow-problem-in-ubuntu-10-04/](http://crenk.com/fix-the-firefox-slow-problem-in-ubuntu-10-04/)

---

### Post by lovinglinux on 2010-07-28
> **steven.c.king said:**
> OK. You got a deal.  Here is a fix that I found somewhere, and it stopped my endless waiting for pages to open.  Here is what he said to do:

"
This is how anyone can fix the Firefox slow problem in Ubuntu 10.04
 Open your Firefox and type about:config at URL address bar and hit  enter. To make a False into True, select the line to change, and double  click. On the 2nd option change, right click and select Modify
 - network.http.pipelining > Make it True
 - network.http.pipelining.maxrequests > Make it 8 or 10
 - network.http.proxy.pipelining > Make it True
 - network.dns.disableIPv6 > Make it True
 I hope this helps for some users"


Below is the link; it worked for me.



[http://crenk.com/fix-the-firefox-slow-problem-in-ubuntu-10-04/](http://crenk.com/fix-the-firefox-slow-problem-in-ubuntu-10-04/)


Please quote another tutorial. The **maximum network.http.pipelining.maxrequests** value is 8. Here is a good one [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html) (not mine btw).

Also check this - [http://devcentral.f5.com/weblogs/macvittie/archive/2009/04/02/http-pipelining-a-security-risk-without-real-performance-benefits.aspx](http://devcentral.f5.com/weblogs/macvittie/archive/2009/04/02/http-pipelining-a-security-risk-without-real-performance-benefits.aspx)

---

### Post by oldsoundguy on 2010-07-28
This is faster than that is faster than this is faster than that ... sheesh a hamster commercial.

The difference between most is just 1/10s of seconds as to on line, and your internet connection can vary between loads as much as that.

What counts is just how much resources does that browser use.  Is it hogging up memory that could be used for multi tasking?

(note that they did not even BOTHER to test anything IE!!)
[http://dotnetperls.com/chrome-memory](http://dotnetperls.com/chrome-memory)

---

### Post by lovinglinux on 2010-07-28
> **oldsoundguy said:**
> (note that they did not even BOTHER to test anything IE!!)
[http://dotnetperls.com/chrome-memory](http://dotnetperls.com/chrome-memory)

Cool. Bookmarked to quote to Chrome users who hijack Firefox threads ;)

---

### Post by jfloydb on 2010-09-13
This really seems to have helped! I don't know why; I will read more and figure it out tomorrow. Thanks again to lovinglinux!

> **lovinglinux said:**
> I would start by installing and running [SQLite Optimizer](https://addons.mozilla.org/en-US/firefox/addon/11198/). You will see the difference after running it.

---

### Post by lovinglinux on 2010-09-14
> **jfloydb said:**
> This really seems to have helped! I don't know why; I will read more and figure it out tomorrow. Thanks again to lovinglinux!

You are welcome. I optimize my databases with that extension regularly.

---

### Post by Zenmij on 2010-09-14
Thanks Lovinglinux. I wouldn't like to swap browsers just yet, it seems there's more 'smoke than fire' from Chrome users right now.

---

### Post by lovinglinux on 2010-09-14
> **Zenmij said:**
> Thanks Lovinglinux. I wouldn't like to swap browsers just yet, it seems there's more 'smoke than fire' from Chrome users right now.

You should see Firefox 4. It is incendiary :)

---

### Post by soldier1st on 2010-09-17
try lovinglinux's suggestion as if you like a certain browser then stick to it and browsers themselves don't slow down but something will cause it.

---

### Post by torturednacho on 2011-03-28
> **Wragie said:**
> Stumbled across this thread and also had noticed the slows in firefox. The disable ipv6 has it smokin along nicely now. 
 
Now if I can get it to open in new tabs all the time instead of windows and tabs I'd be happy.
 
THANKS!!;)
 
Dave
 
 
I hope this works, I'll be trying it in the morning.

---

