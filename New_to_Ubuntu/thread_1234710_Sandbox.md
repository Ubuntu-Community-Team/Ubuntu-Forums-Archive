---
title: "Sandbox"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by BobJam on 2009-08-08
I used to use "Sandboxie in Windows when I wanted to go to suspicious sites to rate them for WOT.  If they contained malware, which they often did, I could just close the sandbox after I was done and I had it set to automatically delete itself.

It was similar to a VM, though if you go to the Sandboxie forum, most of the users, and also the author of Sandboxie, will claim that it was "different" from a VM.

In any case, arguments notwithstanding, is there something like Sandboxie for Ubuntu?  Or would running a VM be the Ubuntu way?

---

### Post by Sidewinder1 on 2009-08-08
I don't believe any of that sort of thing is necessary in Ubuntu/Linux. I run Firefox with the addons AdblockPlus and Noscript. Been clickin' away since 2007 and not even one instance of malware; your milage may vary. 
If you're looking for something in Ubuntu that will alert you to malware in web pages, perhaps someone else has a suggestion.
HTH,
Side

---

### Post by credobyte on 2009-08-08
NoScript works like a Sandbox - each and every symbol of JavaScript will be automatically ( by default ) blocked - once you check it, you can unblock it.

---

### Post by BobJam on 2009-08-08
> **Sidewinder1 said:**
> I run Firefox with the addons AdblockPlus and NoscriptI have and use ABP and NS, but I'm a security freak, plus visiting sites that likely have malware is an added risk.

In Windows, I ran FF sandboxed and with ABP and NS.  Probably overkill, but I did in fact visit a few sites that had malware that defeated ABP, NS, and the sandbox.  In those rare, but scary cases, I had to immediately disconnect . . . which I did through a script I had for calling Task Manager.

So is there at least a way I can do the immediate disconnect? ("immediate" meaning that I don't have to go through a bunch of clicks and windows . . . 'cause by that time the malware has done the dirty deed . . . we're talking seconds here)

> **Sidewinder1 said:**
> your milage may varyThat's what I'm worried about.

> **Sidewinder1 said:**
> something in Ubuntu that will alert you to malware in web pagesI'm pretty much already alerted since I'm already visiting suspicious sites.

One of the main reasons I'm looking for a sandboxed environment is because I click on links in these suspicious sites, and I actually **WANT** to go where they direct to, not avoid them.  ABP and NS are avoidance schemes, so in many cases they don't fit the scenario.

A VM in Ubuntu, maybe even with Windows and the Sandboxie software (now that's really overkill), seems like it might be suited for this.

I've used the word "overkill" a few times, but with the malware variants I've seen, I'm not so sure there is such a thing as "overkill".

In a normal operating environment, yes, things like APB and NS, and Linux especially, are enough.  But I'm not talking about a "normal" environment.  I'm **LOOKING** for these exploits.

A "test machine" would be appropriate, but right now I don't have the dough to do that.

I don't want to risk my day-to-day and **ONLY** machine (or be constantly restoring from a known clean image), so that's why I'm looking for extra security.  Until I get more comfortable, I may just stop my WOT rating activities.

---

### Post by Sidewinder1 on 2009-08-08
VM sounds like the way for you to go. Even if that's too much of a PIA, I would suspect that since, in Ubuntu, you don't have root privileges, unless you use sudo or gksudo, even if you clicked on everything imaginable, the worst that would happen is that somehow FF gets borked. If you've made a copy/backup of your bookmarks, it's a simple reinstall of FF.

---

### Post by BobJam on 2009-08-08
To reiterate, would be nice too to have some sort of "instant" kill switch for my connection . . . DSL.  I could always just flat out shut the thing off, but I'd like to be able to do something less drastic than that.

Most firewalls have that capability, but I'm looking for something native to Ubuntu.

And to reiterate again, my "instant" means that I don't have to go through a bunch of clicks and windows . . . 'cause by that time the malware has done the dirty deed . . . we're talking seconds here.

I'm sure Ubuntu has something like that . . . I just can't find it.

BTW, thanks for the responses.

---

### Post by Liolikas on 2009-08-08
Learn how to type:
pppoe stop
really fast. something like pp/TAB/ stop

---

### Post by 3rdalbum on 2009-08-08
I don't think you'll find any malware that runs on Ubuntu and takes advantage of any Firefox security holes to install. It sounds like that "sandboxie" thing doesn't really do a lot, if malware can get through it.

That is, if you were really getting malware at all. I was reading a post on Cnet from a Windows users asking for advice - he'd just seen one of those animated GIFs pretending to be an "online security scanner", he'd clicked what he thought was a Cancel button and it took him to an anti-virus vendor's website. He was convinced that he'd just been infected by malware.

Parts of the internet are malicious, but modern web browsers have reasonable security.

Use a virtual machine. If you "save state" rather than shutting down, you barely have to wait any time for loading. There's never been a virus that can escape a virtual machine; actually viruses tend to be programmed not to run if they detect that they are running in a VM, so even your virtual environment is pretty safe.

---

### Post by Liolikas on 2009-08-08
One time I entered site with MEPIS Linux and saw Image with text "your computer is infected" in image Windows Xp "my computer" burning in flames and suggestion to scan my register for free. So I scanned it and "scanner" even failed to detect that I do not have register and windos at all :D :D but it detected ~50 "failures" and suggested to buy fix for reasonable 50$ price. :D 
Epic lol it was.

But I am sure that many windows users believed in that crap.

---

### Post by BobJam on 2009-08-08
> **Liolikas said:**
> but it detected ~50 "failures" and suggested to buy fix for reasonable 50$ price . . . But I am sure that many windows users believed in that crap.

Those are called "rogues", and they are becoming more and more prevalent.

Some of them even mimic the Windows Security Center, convincing users . . . noobs especially . . . that the message is legit and it is from Microsoft.

Registry cleaners are particularly likely to be rogues, followed by fake/fraudulent antivirus programs.

Most Windows installations, even clean new ones, will have 100's of registry errors, but they are trivial . . . things like remnants left over from software installations, missing .dll's, etc.  They **DO NOT** slow down your machine.

However, when a noob sees that a rogue registry cleaner says there are "200 serious registry errors", and it says it can speed up your machine if it removes them, that cold hard cash is pried from the noob's hands.

Another problem with these things, and a more significant one, is that the purpose of many of these things is . . . **IDENTITY THEFT**.

The noob will make the purchase with a credit card, and you can guess the rest of the story.

Most rogue programs don't contain malware per se . . . they rely on scaring the bejesus out of a noob . . . consequently, a lot of malware detection programs don't detect them.

However, there are lists . . . Dancho Danchev's blog, hpHosts, malwareurl.org are just a few.

There is one that has even made so much money that they can advertise on TV.  "******Fast.com" is a notable rogue.  (Don't want to post the full name here because I don't want to risk getting the forum owners embroiled in a law suit).

Better get off the soap box.  As I said, I'm a security freak.

---

### Post by BobJam on 2009-08-08
> **3rdalbum said:**
> It sounds like that "sandboxie" thing doesn't really do a lot, if malware can get through it.
There is no such thing as 100% security . . . unless you encase your machine in concrete and never get on line.  Not defending Sandboxie here, but it does indeed thwart most malware penetration attempts.  See below for more details.

> **3rdalbum said:**
> That is, if you were really getting malware at all
It sounds like you are using the strict technical definition of "malware".

Relative to the term "malware" . . . there is a technical definition and a "common usage" definition. Very often the two are different.
 
 While sticklers may insist that the technical definition is the "right" one, "malware" in common usage is generally taken to be ANY malicious code, which could be anything from spyware code designed to extract personal information or to defeat encrypted messaging, **CODE IN APPS THAT WILL DISPLAY DUBIOUS SCAN RESULTS THAT WILL SCARE A NOOB INTO PURCHASING THE APP, (ie. rogue registry scanners)**, all the way to virus code designed to destroy data on your machine.

 When you say "malware", that is what most people think off, with the exception of technorati that adhere to technical definitions, and who sometimes are quick to point out that you are "wrong" to think otherwise. Of course, they are correct insofar as technical definitions are concerned, but in the case of "malware" that technical definition does not portray what the common usage is.

 And I think scareware that relies on social engineering is in this broader definition of malware.

In any case, I will guarantee you that I've encountered plenty of strict definition malware in visiting suspicious sites for the purpose of rating them safe or not.
 
> **3rdalbum said:**
> I was reading a post on Cnet from a Windows users asking for advice - he'd just seen one of those animated GIFs pretending to be an "online security scanner", he'd clicked what he thought was a Cancel button and it took him to an anti-virus vendor's website. He was convinced that he'd just been infected by malware.See post #10 here.

> **3rdalbum said:**
> Parts of the internet are malicious, but modern web browsers have reasonable securityBetter than security programs is . . . common sense.  My favorite sig line on security forums:  "Ultimately, the only protection against phishing, forged Web pages, downloading malware, and other threats is the technology located between the user's ears."   

> **3rdalbum said:**
> There's never been a virus that can escape a virtual machineOh yes there has.  See:

"An Empirical Study into the Security Exposure to Hosts of Hostile Virtualized Environments" at [http://taviso.decsystem.org/virtsec.pdf](http://taviso.decsystem.org/virtsec.pdf)

Granted, this was in a lab, but it's only a matter of time 'till the malware writers figure this out.

 > **3rdalbum said:**
> actually viruses tend to be programmed not to run if they detect that they are running in a VM"Detecting System Emulators" at [http://www.seclab.tuwien.ac.at/papers/detection.pdf](http://www.seclab.tuwien.ac.at/papers/detection.pdf)

---

### Post by skidz on 2009-09-25
I am with BobJam...

I just switched over to Ubuntu 1 week ago, and out of everything Sandboxie I miss the most. Actually, its the only thing I miss :)... If you want to leave no history of surfing to a site (for example a bank, or pron).. but there is tons of other uses for it... I even used it to run Opensim, which is beta, and most likely not secure virtual world server. It basically gave you a rollback feature, kinda like a virtual machine. I do wish there was a way I could do that on Ubuntu, especially being new to the OS.

---

### Post by BobJam on 2009-09-25
I guess the closest you could come is to run another iteration of Ubuntu within a virtual machine.  Ubuntu "inside" Ubuntu . . . hmmmmm . . . sounds pretty secure.

Don't know if that can be done, but I assume so.

Actually, I run Windows XP within a VM, and recently installed Sandboxie there.  IE8 works fine in a sandbox.

But I would like to run Ubuntu as secure as I can (within usable limits of course . . . I don't want to go overboard), so I may try Ubuntu in a VM within my Ubuntu.

Since I purposely go to suspicious sites for purposes of rating safety (WOT), I need to be as secure as I can.  I run FF with NoScript and ABP, but running it within a VM might make me feel safer when visiting those suspicious sites.

I wouldn't need to run ONLY in the VM, just when I know I'm going to do some rating.

Will try it, and report back, skidz.

---

### Post by scorp123 on 2009-09-25
> **BobJam said:**
> I guess the closest you could come is to run another iteration of Ubuntu within a virtual machine.  Ubuntu "inside" Ubuntu . .  Don't know if that can be done, but I assume so. VirtualBox 3.0.x in "seamless" mode. Firefox would run inside the VM, but thanks to "seamless mode" it would appear as if it were running on your normal desktop.

And then ... maybe you are interested to read this?
[http://ubuntuforums.org/showpost.php?p=7892943&postcount=2](http://ubuntuforums.org/showpost.php?p=7892943&postcount=2)

That thread was about using two accounts + two browsers: one for normal everyday activities, the other for online banking.

You could do the same thing: Linux being a multi-user system you could create a second user account (and please: make sure that account is not a member of the "admin" group and thus can't execute "sudo" !) and then surf the web using that account, especially dangerous web sites. And when you're done you delete that account again including that user account's /home/nameOfuser folder. Voila. Done.

> **BobJam said:**
>  but running it within a VM might make me feel safer when visiting those suspicious sites. Well, the VM has the advantage that you could take a snapshot and each time when you're done you return to that snapshot, discarding any potential harmful changes that may have originated from your last session.

---

### Post by Don1500 on 2009-09-25
> **BobJam said:**
> I guess the closest you could come is to run another iteration of Ubuntu within a virtual machine.  Ubuntu "inside" Ubuntu . . . hmmmmm . . . sounds pretty secure.

Don't know if that can be done, but I assume so.

Actually, I run Windows XP within a VM, and recently installed Sandboxie there.  IE8 works fine in a sandbox.

But I would like to run Ubuntu as secure as I can (within usable limits of course . . . I don't want to go overboard), so I may try Ubuntu in a VM within my Ubuntu.

Since I purposely go to suspicious sites for purposes of rating safety (WOT), I need to be as secure as I can.  I run FF with NoScript and ABP, but running it within a VM might make me feel safer when visiting those suspicious sites.

I wouldn't need to run ONLY in the VM, just when I know I'm going to do some rating.

Will try it, and report back, skidz.

OK, you want security, but still be able to see whats coming into a machine connected to a "Suspect" web site, right. Load a Pen drive with Ubuntu, remove the hard drive from the machine, and boot from the pen drive. You will have a complete system that you can throw away after you are done. No inter action with anything but your BIOS, which you can flash from a clean pen drive if you want. You can get a 1 gig drive, which is plenty to run a full up Ubuntu or Kubunto if you want, for less than $20. Oh yes, if you format the pen to ext4 your windows can't read it.

For even more security, go to your nearest HolidayInn Express, sit in the lobby and use their wifi. Now nobody will know who you are.

---

### Post by skidz on 2009-09-25
VirtualBox in seamless mode sounds like a good solution. Thanks :) Would be easier than switching users every time I want to check my bank balance. Thanks to everyone for the reply.

---

### Post by egalvan on 2009-09-25
> **BobJam said:**
> 

A "test machine" would be appropriate,
 but right now** I don't have the dough to do that.**


On Craig's List...
a few weeks ago I saw a gentleman selling two computers...
complete except for hard drive
both 1.8GHz P-4's, 
Dell Optiplex had 512Meg RAM
HP had 256Meg RAM.

To quote...
"$30 each, $40 both, or they are going in the dumpster"...

I think a Jackson waived under his nose would have sealed the deal for both.


I also saw this ad

"Free... 17" CRT-type monitor. Works, GET IT OUT OF MY CLOSET!"


NOTE -->MY OPINION<--NOTE

anyone who resides within the Continental United States is able to "afford" a computer.
maybe not a 4.4GHz Quad-Core with 16GB RAM and dual-SLI-mode video cards,
but a working computer... 

Go to a "mom-and-pop" type computer store and ask them what the CHEAPEST computer they have, that is at least a P-III.
I think you will be surprised.

---

