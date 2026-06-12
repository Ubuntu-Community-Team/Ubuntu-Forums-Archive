---
title: "Urgent help please, i need to do a 'Fiddler trace' and don't have a clue how?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by liviococcia on 2010-09-26
Hello Members, i'm having problems with my Hotmail account and Windows live tech support are asking for a 'Fiddler trace, trouble is being such a novice I don't know how to get one, or run the software to provide them with this log file in Ubuntu, I have search but am very unclear on what's to be done.

Any help would be great, there's also a bit of urgency regarding the above.

kind regards
Livio

---

### Post by QLee on 2010-09-26
Well, not surprisingly, those MS support people want you to run a piece of Windows software, likely because they will understand the output from it and troubleshoot from that.

If you choose to detail what problem you are having with your Hotmail account on Ubuntu, there is probably someone here who uses Hotmail and would be able to help.

I don't have any idea if that program would work with wine.

---

### Post by liviococcia on 2010-09-26
> **QLee said:**
> Well, not surprisingly, those MS support people want you to run a piece of Windows software, likely because they will understand the output from it and troubleshoot from that.

If you choose to detail what problem you are having with your Hotmail account on Ubuntu, there is probably someone here who uses Hotmail and would be able to help.

I don't have any idea if that program would work with wine.
Hello QLee thanks for the reply, i have posted my initial problem with the Hotmail issues i've been having, please see the link below...

[http://ubuntuforums.org/showthread.php?t=1574301](http://ubuntuforums.org/showthread.php?t=1574301)

...and had no luck, i'd also posted on the Mozilla forums, again without success.

I thought i'd better try Windows Live hotmail for help, as i though it may be related to a problem with the Hotmail account itself, so-far the problem has been escalated to there higher section, but there asking for a 'FiddlerCap' trace, which is as you've said, a windows based utility.

I have found reference to something called a 'Tamper Data' plug-in for Firefox, but as Windows live support have asked for a data log file from 'Fiddler', is there a Ubuntu or linux version, if not, what can i offer the live support team?

So far i'm thinking that a 'Tamper Data' text log file might help them, if they accept it.

Kind regards

---

### Post by QLee on 2010-09-26
[QUOTE=liviococcia]Hello QLee thanks for the reply, i have posted my initial problem with the Hotmail issues i've been having, please see the link below...

[http://ubuntuforums.org/showthread.php?t=1574301](http://ubuntuforums.org/showthread.php?t=1574301)

...and had no luck, i'd also posted on the Mozilla forums, again without success.[/QUOTE]
Not too surprising, yours is an intermittent problem, the hardest to diagnose, sometimes it works and sometimes it doesn't, with firefox, yet it always works with chrome.

[QUOTE=liviococcia]I thought i'd better try Windows Live hotmail for help, as i though it may be related to a problem with the Hotmail account itself, so-far the problem has been escalated to there higher section, but there asking for a 'FiddlerCap' trace, which is as you've said, a windows based utility.[/QUOTE]
If it was a Hotmail account trouble then I wouldn't think those other two computers that you have and which don't have the trouble using that account would function correctly as they do.

My first guess, given the symptoms you have detailed, would be an intermittent hardware fault, on the one computer that shows the trouble. Edit: Sorry I didn't finish this before sending. It should also state, but, then it shouldn't always work in chrome.

[QUOTE=liviococcia] I have found reference to something called a 'Tamper Data' plug-in for Firefox, but as Windows live support have asked for a data log file from 'Fiddler', is there a Ubuntu or linux version, if not, what can i offer the live support team?
...[/QUOTE]

Only they could detail the details they need. I don't know what you could try. I expect if you mention any GNU/Linux they will state they don't support that, similar to the way many ISPs do. If you knew exactly what data they needed, there might be a way to get that. However, chances are good that the first-tier, support person who will be helping you doesn't really know what is needed and is only capable of following a decision tree from the output of that program.

Another possibility, perhaps someone on this forum has that software and is familiar with running it and could advise of the output.

---

### Post by sandyd on 2010-09-26
[http://liveidsupport.spaces.live.com/blog/cns!4D45F3F81F297BB6!111.entry](http://liveidsupport.spaces.live.com/blog/cns!4D45F3F81F297BB6!111.entry)

---

### Post by liviococcia on 2010-09-27
Thanks all members for your help, QLee your completely right about 'Chrome', but there's something about Firefox that i like, i think there's more functionality in it, but i've never had any Hotmail issues on any computer of mine using Chrome, i'm not sold on the idea of a hardware fault being the problem, unless it's the T-Mobile mobile broadband related in some way?

Sandyd, thanks for the link, but i'm looking for a Ubuntu/Linux version of Fiddler or FiddlerCap.

I've contacted Windows Live support, and explained the problem regarding a FiddlerCap trace, and asking if they would consider using the Firefox extension utility 'Tamper Data' log instead, they havn't come back to me with a rejection to this as yet, i have to say that given that the 'Support team' know that i'm using a Linux os they been very helpful, and not just cast the problem's i'm having aside, but shown me every consideration. 

I think Live Support have also looked at my Hotmail accounts settings at there end, and at the moment i'm testing the account between all the computers i have, and i've been able to login and use the account on each, maybe this is a fluke, so i'll continue the test and report back here, and to Windows live support.

kind regards

---

### Post by QLee on 2010-09-27
[QUOTE=liviococcia]Thanks all members for your help, QLee your completely right about 'Chrome', but there's something about Firefox that i like, i think there's more functionality in it, but i've never had any Hotmail issues on any computer of mine using Chrome, i'm not sold on the idea of a hardware fault being the problem, unless it's the T-Mobile mobile broadband related in some way?[/QUOTE]

To be sure I'm stating it clearly, I would have thought hardware fault *except* for the fact that chrome always works.

Given the symptoms, I'd suspect a possible configuration of firefox on that unit because the other two with firefox work. That doesn't explain the intermittent nature of the problem. If it was my system I would carefully compare firefox versions and configuration between the faulty machine and one of the working ones.

[QUOTE=liviococcia]...  'Support team' know that i'm using a Linux os they been very helpful, and not just cast the problem's i'm having aside, but shown me every consideration. [/QUOTE]
Great, then they are more helpful than a lot of ISPs. Very often people report that ISP support doesn't support "Linux", I know mine doesn't. 

Still, if they would tell exactly what info they want, it probably would be possible to find it from Ubuntu but that's not to say it would be easy. I hope the results of your current tests are success.

---

### Post by liviococcia on 2010-09-27
Hello QLee, well i've come back tonight to the computer that suffers the problem with my Hotmail account, and guess what? it's back to it's old tricks after around 1 day's use.

I had progessively gone from this computer to my other computers all with sucessfull use of the account, then signed on this morning using my workplace's Windows XP pro using IE 8 browser all was ok, then signed on tonight and the computer that was ok 24 hours ago, is now back with the same old problem.

I tell you, i think i'm going to give up on this ongoing issue, and Firefox, i just think there's something not compatible between Windows Hotmail Live and Firefox, it's not robust against the new Hotmail format, cookies, or the websites instructions.

Thanks for all the help members have given me, i think i'll just use Chrome and come back to Firefox in a future versions. 

Kind regards
Livio

---

