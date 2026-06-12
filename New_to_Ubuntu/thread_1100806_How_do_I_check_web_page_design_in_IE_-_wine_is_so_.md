---
title: "How do I check web page design in IE - wine is so slow"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by kapi on 2009-03-19
how on earth do I develop web sites in ubuntu and test them in IE. I am a die hard FF user but obviously I need to test my designs in IE 6 , 7 and now 8.

Loaded wine then ies4linux but was not overly impressed. Kind of defeats the purpose of having Ubuntu if i have to go back and use MS just to test. I love Ubuntu - have converted since Dec 08 and no going back. 

Any suggestions very welcome . . . Thanks

kapi

---

### Post by freak42 on 2009-03-19
you could use a virtual machine (vmware or virtualbox) to load a windows within ubuntu.

---

### Post by kapi on 2009-03-19
yeah thanks - I thought about that, even tried it yesterday. Just seemed a little complicated. will try again

Thanks for your input

Kapi

---

### Post by D3ath on 2009-03-19
There are some things we just can't do and the upcomming IE8 we will not be able to do anything in linux with that for a while. I would set up a small vm for windows if you are a die hard web designer.  It is needed to test on browsers! Kinda sucks but that windows and there proprietary software!

---

### Post by mlentink on 2009-03-19
Kind of begs the question...

....how do you test with safari?

---

### Post by kapi on 2009-03-19
good points in the linked document. made me think.

linux is not windows and as such should be treated accordingly.

Thanks

---

### Post by lukjad on 2009-03-19
This may not be everything you are looking for, but there is a project called IEs4Linux. I'm not sure if you already have this, but if not: [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by doas777 on 2009-03-19
check this out:
[http://browsershots.org/](http://browsershots.org/)

point it to a site you wanna test, and fire away. it will capture screenshots of what it renders like in each of a huge number of engines. i can't guarantee it will work perfectly for ya, but give it a try. 
the process takes some time.

---

### Post by jlochhead on 2009-03-19
> **mlentink said:**
> Kind of begs the question...

....how do you test with safari?

Safari works well in wine last time I checked.

...Although you might be talking about a new version that I seem to remember hearing about.

---

### Post by kapi on 2009-03-20
wine is so slow, and now that I have checked y site in ie6 (thanks to wine) I want to explode - looks like its been hit by a truck. Whats annoying is that its perfect in opera and FF - it validates perfectly in w3c but in IE I look like a kindergarden web designer. no offence to kindergarden web designers.

tried loading vista via virtual box - its way too mauch hassle ensuring access to host drives etc. Pitty someone couldn't come up with a better solution

---

### Post by Kellemora on 2009-03-20
Hi Kapi

For testing web pages you'll need a lot more than just different browsers!

You'll need different computers and monitors as well!

Web pages do NOT display the same way, even using the same browser, on different types of computers and monitors.

Especially those web sites that use Proprietary Coding within their scripts.

Even using Firefox, but working from a different computer that afternoon, I kept skipping over a web site because it didn't look like the one I was looking for.  It was SO DIFFERENT I didn't even recognize it after visiting the same web site nearly every day.  Kept thinking my link went bad until I started looking at it closer.
All I thought to myself at the time, once discovering I was on the right web page alright, what clutz turned this place into such a mess.
Then I went back to my own desk and it looked exactly how it always did.
Went back to that desk again and what a mess.
Text outside of the frames, frames overlapping frames, ads on top of articles, etc.

I still have a LOT of weird things happen when viewing web sites using Firefox in 64 bit Ubuntu.  Missing buttons, misplaced images, etc., but they look OK in 32 bit Ubuntu, but never as well as they look from XP-Pro running Firefox.

We don't use IE for anything here!
Even changed banks twice because they went with Proprietary Code!
And that was back in my daze of using the Doze too!

TTUL
Gary

---

### Post by kapi on 2009-03-21
Firstly - I think Ubuntu is great! 

However I have a dilema, As with all web developers we need to test our sites etc in IE ( as a high percentage of user soley use IE). I used to develop with notepadd++ but now use Geany(fantastic software).

Anyway, testing IE in ubuntu is a no go. I know there is wine and IES4LINUX but they both frankly don't cut it. I have installed vista via virtualbox but that kind of defeats the purpose of using ubuntu. So my question is this, there must be a viable solution to this problem. I know there are other developers out there that use ubuntu and that experience the same problem. so whats the solution? I like ubuntu and think it has massive potential for business and personal use, this is only the beginning of a linux revival.

Let me know your thoughts - someone out there has the answers

Thanks

Kapi

---

### Post by hyper_ch on 2009-03-21
ask M$ to create a standards conform browser (and instead of vista why not using a vanilla xp)

---

### Post by paydaydaddy on 2009-03-21
Here is my take on your issue. If you are serious about web developing then you have to have the tools of the trade. That means having access to the various platforms that you intend to support. Best scenario is multiple machines and devices. You solution may be a dual boot system. Depending of your situation, networking with friends and associates may be the answer. Of course, I may not have a clue what I am talking about.

---

### Post by kanikilu on 2009-03-21
> **paydaydaddy said:**
> Here is my take on your issue. If you are serious about web developing then you have to have the tools of the trade. That means having access to the various platforms that you intend to support. Best scenario is multiple machines and devices. You solution may be a dual boot system. Depending of your situation, networking with friends and associates may be the answer. Of course, I may not have a clue what I am talking about. Agreed. I'm a novice web developer (more of a "maintainer" than "developer"), and I use Ubuntu to test Firefox and Opera, XP in VirtualBox to test IE, and a Mac to test Safari.

I've heard about [BrowserShots](http://browsershots.org/), but haven't tried it yet since I have access to the platforms/browsers I need...

---

### Post by kapi on 2009-03-21
Thanks for all your input, but my challenge was this. In MS i used to be able to test FF, Opera, and IE using one single OS. 

In Ubuntu (1 single OS) I can only test FF, Opera and a few other mini league browsers. Thats my point.in response to your answers - Yeah I can have many different tools(Operating systems) and Yeah I could network with others to test my sites, but in effect its not as efficient as using one system that covers such a wide range. 

Hopefully the Ubuntu team will take note and sort something out in the near future - in the mean time it looks like the virtual machine is the only answer.

---

### Post by hyper_ch on 2009-03-21
you got any suggestion as to what the ubuntu devs should do here?

---

### Post by Bearly Able on 2009-03-21
I'm dual-booting XP and Ubuntu, and the only reason I've kept XP is to test Web pages.  I may be extreme, but I also test Opera and Firefox on both platforms and Safari on Windows.  At the moment, I can't afford a Mac, but have friends who will test for me; maybe not efficient, but it works for me.

---

### Post by kapi on 2009-03-21
no unfortunately, I realise that Ubuntu and other linux developers have their hands tied as far copyright and restriction on the use of IE code or rendering engines but hey, they are a clever bunch and I have no doubt that something will turn up eventually.

---

### Post by hyper_ch on 2009-03-21
so wouldn't it be better to promote use of free software instead of making everything also horrible M$IE-broken-compliant?

---

### Post by kapi on 2009-03-21
yeah very good - but it doesnt help the average business user who needs to sort todays problems so as to earn a wage. I agree Yes by all means support compatibility and open source but in the mean time we still need to deal with the issues of today. telling everyone how wonderful open source is and how linux can aid their business is good but not everyone sees it that way especially clients who want results

---

### Post by PukingPenguin on 2009-03-21
Sounds like wishful thinking on your part, I'm afraid. There is very little incentive for anyone to build something that behaves as badly as IE just so developers don't have to run a virtual machine....

---

### Post by andyrue304 on 2009-03-22
I develop my php sites on Ubuntu with komodo edit 5.0 (which is awesome by the way and free: [http://http://www.activestate.com/komodo_edit/]("http://http://www.activestate.com/komodo_edit/")).

When I'm cross-browser testing, I use [synergy]("http://synergy2.sourceforge.net/") to control multiple screens with the same keyboard and mouse so I can still dev on Ubuntu while having my laptop running windows and not have to reboot the whole time. :D

I also use [IEtester]("http://www.my-debugbar.com/wiki/IETester/HomePage") on windows, which is great apart from lack of flash support.

This method seems the least hastle for me when dealing with fricking IE.

---

### Post by rem on 2009-03-26
Having the same problems with testing websites and it got even harder since IEs4Linux is not maintained anymore. Anyways, I can somehow manage with [NetRenderer Firefox extension]("https://addons.mozilla.org/en-US/firefox/addon/6455") (works almost in real time). Maybe it's going to help you as well.

---

### Post by skymera on 2009-03-26
> **kapi said:**
> wine is so slow, and now that I have checked y site in ie6 (thanks to wine) I want to explode - looks like its been hit by a truck. Whats annoying is that its perfect in opera and FF - it validates perfectly in w3c but in IE I look like a kindergarden web designer. no offence to kindergarden web designers.

tried loading vista via virtual box - its way too mauch hassle ensuring access to host drives etc. Pitty someone couldn't come up with a better solution

Ok since you bad mouth Wine.

Make your own compatability layer that runs faster.
Done it? I'm eager to try it :)

---

### Post by nickcollie on 2009-03-27
Agree about using NetRenderer.  Also have a look at browsershots for testing on a whole range of browsers, machines, screens.  It is slow but worth it.

---

### Post by michaelzap on 2009-03-27
I use XP in VirtualBox to test sites on IE6, IE7, IE8, Safari Windows, and Google Chrome. You can setup different snapshots of your system so that you can have multiple versions of IE for testing. It's really the best way that I've found to test a site properly, since Wine isn't quite the same and you can't test scripts and other things using browsershots.org (although that is a great tool for checking your design on multiple systems).

I haven't found a good way to test Safari for the Mac yet, so if anyone has any suggestions (other than buy a Mac, which I don't plan on doing) please post them.

I think we're actually going to stop supporting IE6 very soon. That nasty browser came out in 2001 (!) and it's still the bane of our existence. People really, REALLY shouldn't be using it anymore, so in the future we may just do a browser test and send IE6 users to a page explaining why they need to use an updated browser (for our sanity, their security, and the good of humanity) with links to download Firefox, IE, and Opera. Even for commercial websites like the ones that we do, I think the time has finally come where we can cast IE6 onto the dung heap of history.

---

### Post by rem on 2009-03-28
> I think the time has finally come where we can cast IE6 onto the dung heap of history.

I already started doing that. I'm not a full time designer, mostly programming, but anyways, when doing websites I am not supporting IE6 only if the client is specifically asking it. I honestly had my share of IE6 in the past so now, with all these great new technologies and fancy browsers, it is time to do some real websites

---

