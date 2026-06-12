---
title: "ubuntu causes slow downloads"
date: 2005-05-06
forum: Networking &amp; Wireless
---

### Post by veritas366 on 2005-05-06
I didn't think this was a Ubuntu issue, but after some testing I have found the following. 

When I run a speed test in Ubuntu (from testmy.net) to clock my download speeds from my ISP I get around 1.5mbps...less than half of what I should.  My ISP tech is on the way here!

I signed on over on the Windows partition and the speed is DOUBLE what it is when in Ubuntu.  I have no idea what settings have led to this.  Can someone help me out and tell me what info you need to figure out why my connection is so much slower in Ubuntu?  Thanks!

Edit:  I'm in Ubuntu and posting the internet speed test results.  Then I am going into Windows and present those results.  No differences in hardware setup.  These are actually a bit higher than they have been the last few days. Please somebody help me out here.  I'm sure there are simply some settings that need changing but I don't know what they are:

> Ubuntu Speed Test
:::.. Download Stats ..:::
Connection is:: 1764 Kbps about 1.8 Mbps (tested with 1496 kB)
Download Speed is:: 215 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (main)
Test Time:: Sat May 07 2005 09:19:31 GMT-0500 (CDT) 
Bottom Line:: 31X faster than 56K 1MB download in 4.76 sec 
Diagnosis: May need help : running at only 49.36 % of your hosts average (comcast.net) 
Validation Link:: [http://testmy.net/stats/id-RJ6YLW7M4](http://testmy.net/stats/id-RJ6YLW7M4) 
 

Okay, now below is the same test while in the Windows OS.  I note that the speeds aren't great here either, though I think the router has something to do with that. When directly connected without the router while in Windows, I get well over 3mbps.  However, notice that the speeds are certainly above those obtained in Ubuntu.

> ::::.. Download Stats ..:::
Connection is:: 2435 Kbps about 2.4 Mbps (tested with 2992 kB)
Download Speed is:: 297 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (main)
Test Time:: Sat May 7 09:26:31 CDT 2005 
Bottom Line:: 43X faster than 56K 1MB download in 3.45 sec 
Diagnosis: May need help : running at only 68.13 % of your hosts average (comcast.net)   

I have searched but everything on here is about lack of connectivity or wireless.  I have an ethernet router...but the router isn't the issue (though router tweaks would be welcome as well) as I get the same slow speeds when directly connected without the router.

---

### Post by veritas366 on 2005-05-07
Bump...so I can stay on the first page.

---

### Post by veritas366 on 2005-05-08
Show me some love \\:D/

---

### Post by alastair on 2005-05-08
Not much of an idea - you don't describe your hardware at all though.

What are you connected through? Modem? router?

---

### Post by alastair on 2005-05-08
Sorry - I see you say ethernet router ...

IF there is no special s/w used on the Linux side, I have no idea of the problem.

---

### Post by veritas366 on 2005-05-08
Well, at one point I did put Firestarter on...but saw that with a router that was sort of redundant and I took it back off...so it may be that a setting was changed. 

 I posted here, knowing I was short on specifics, hoping that someone could tell me even what settings to LOOK at.  I've been googling but networking and TCP/IP stuff is confusing to me, I must admit.

I will repeat, though, that Windows is faster.  This should embarrass us!  The speed difference at times is quite significance...and the only difference is the OS.

---

### Post by veritas366 on 2005-05-10
Daily bump

else moderator please move this to the place where unwanted threads go to die.  :-?

---

### Post by veritas366 on 2005-05-11
Doin the bump!

---

### Post by Bob D. on 2005-05-11
I don't think the issue is with Ubuntu. Here's my test using Ubuntu from the same test site. I have Comcast broadband, same as you:

 > :::.. Download Stats ..:::
Connection is:: 4226 Kbps about 4.2 Mbps (tested with 2992 kB)
Download Speed is:: 516 kB/s
Tested From:: [http://testmy.net/]("http://testmy.net/") (main)
Test Time:: Wed May 11 2005 11:20:40 GMT-0700 (PDT) 
Bottom Line:: 75X faster than 56K 1MB download in 1.98 sec 
Diagnosis: Looks Great : 18.47 % faster than the average for host (comcast.net) 
Validation Link:: [http://testmy.net/stats/id-XIJ93UNDG]("http://testmy.net/stats/id-XIJ93UNDG")  

This is tested using Firefox as browser and through my Netgear router. Firestarter is not (and has never been) installed. There should be no IPtables rules on this computer, though I've never checked.

I'm going to boot this system to XP and see what it shows. Be right back.

EDIT: OK, below is my download from the same testsite using the same file size. Again this is using Firefox on XP, through the Netgear router. This XP system has Avast A/V active and the Sygate Personal Firewall software firewall active also.

 > :::.. Download Stats ..:::
Connection is:: 4085 Kbps about 4.1 Mbps (tested with 2992 kB)
Download Speed is:: 499 kB/s
Tested From:: [http://testmy.net/]("http://testmy.net/") (main)
Test Time:: Wed May 11 2005 11:35:46 GMT-0700 (Pacific Daylight Time) 
Bottom Line:: 73X faster than 56K 1MB download in 2.05 sec 
Diagnosis: Looks Great : 14.52 % faster than the average for host (comcast.net) 
Validation Link:: [http://testmy.net/stats/id-J53XH8RCO]("http://testmy.net/stats/id-J53XH8RCO")  

Downloads on Ubuntu are slightly, slightly faster than downloads on XP for me. Note that Comcast has upgraded service in my area to the 4 Mbps service.

I don't know what your particular issue could be, but it appears distinct to you and not a reflection of Ubuntu overall.

Bob

---

### Post by veritas366 on 2005-05-11
Well, I wasn't saying that Ubuntu in general was slower...just that this was so on  my computer.  My assumption is that there is a setting that is wrong on my computer and i was hoping to get some help figuring out what it was.  The fact that Ubuntu works on your system (and I assume on a vast majority of systems) does not actually provide any information that will be helpful (unless it turned out LOTS of people had this issue.)

Let's look at it this way, there is nothing different EXCEPT the operating system when I test on XP and ubuntu.  Same hardware.  So what else could it be other than some setting in Ubuntu?  I'm going to pop in the Ubuntu live CD and see what the speed is there.  If it's comparable to XP then I'll know that something on my installed Ubuntu got messed with.  Problem is...I don't know nearly enough to figure out what it is!

---

### Post by Bob D. on 2005-05-11
> Well, I wasn't saying that Ubuntu in general was slower.

Hmm, may not be what you _meant_ but when you say:

 > Thread title = "ubuntu causes slow downloads"  

and

 > I will repeat, though, that Windows is faster. This should embarrass us! The speed difference at times is quite significance...and the only difference is the OS.
 
it is easy to see how one might be confused.


Thinking back, was this an issue prior to installing Firestarter? Did you run any test prior to installing Firestarter and setting up some rules? 

Can you reinstall Firestarter and see if any rules are still present? I don't know how else to check if you have any IPtables settings still in place that might be the issue. It's the only thing I can think of that might be causing such a difference.

Hmmm, you are still running slower on XP than you should when using your router than without it. How does Ubuntu run without the router?

Bob

---

### Post by veritas366 on 2005-05-11
Well, that's true about the confusion, I suppose.  I said in the first post:

> I'm sure there are simply some settings that need changing but I don't know what they are: 

That has been my thought all along.  Now, I did not actually ever measure the speed before Firestarter, but I have measured without the router and that has made no difference.  I started to notice the speed change though recently as I tried to download various files.

Now, the reason I posted here is I don't know the first thing about IP tables...how to find them, how to interpret them, how to change them.  So I was hoping someone might help me figure out what to post in order to diagnose this problem.  

I will reinstall firestarter, but need directions as to what to do once it is installed.

Also, I'm going to reboot using the Live Cd and test speed that way.  I'll be back in a bit.

---

### Post by veritas366 on 2005-05-11
Okay, I am in Ubuntu, but it is from the Live CD.  This is not exactly a perfect comparison, because the live cd is warty and I have hoary, so it could be a hoary issue with my system or simply some other setting that needs tweaking.

Here is the speed test with the live cd...almost exactly the same as with XP...and much faster than with the installed Ubuntu.

> :::.. Download Stats ..:::
Connection is:: 2698 Kbps about 2.7 Mbps (tested with 2992 kB)
Download Speed is:: 329 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (main)
Test Time:: Wed May 11 2005 16:50:01 GMT+0000 (UTC) 
Bottom Line:: 48X faster than 56K 1MB download in 3.11 sec 
Diagnosis: May need help : running at only 75.66 % of your hosts average (comcast.net) 
Validation Link:: [http://testmy.net/stats/id-ULPR27XZ0](http://testmy.net/stats/id-ULPR27XZ0)  

Okay, I am now printing the results using Hoary which is installed on my system.  Pretty big difference.

> :::.. Download Stats ..:::
Connection is:: 1080 Kbps about 1.1 Mbps (tested with 2992 kB)
Download Speed is:: 132 kB/s
Tested From:: [http://testmy.net/](http://testmy.net/) (main)
Test Time:: Wed May 11 2005 16:56:41 GMT-0500 (CDT) 
Bottom Line:: 19X faster than 56K 1MB download in 7.76 sec 
Diagnosis: May need help : running at only 30.29 % of your hosts average (comcast.net) 
Validation Link:: [http://testmy.net/stats/id-RVIXY6KNZ](http://testmy.net/stats/id-RVIXY6KNZ)  

This confirms my suspicion that something has gotten changed in my Ubuntu settings but I don't know enough to figure out what.  Absent that...is there a config file I can safely delete that will be reconfigured automatically.  If the LIve CD can make it work, obviously Ubuntu can detect the correct settings.  Something has just gotten tweaked incorrectly.

---

