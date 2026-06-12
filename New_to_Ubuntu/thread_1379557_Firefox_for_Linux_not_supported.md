---
title: "Firefox for Linux not supported"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Desert Sailor on 2010-01-12
Intuit is a Microsoft lap dog.  I am trying to help my daughter with some work with her company using Quick Books On Line.  I tried to log on and got an error message saying I had to use Windows Explorer 6 or higher or Firefox for Windows version 3.0 or higher.

Is there a work around for this, so I don't have to restart to the Windows virus?   What's so damn special that Firefox for Linux can't be supported?

---

### Post by JackRock on 2010-01-12
I did some research on their site, and it seems even the FF in Windows is in "beta", not production...but it can be used.  It seems ActiveX controls need to be installed/used, so that may be the problem.

---

### Post by studmf on 2010-01-12
> **Desert Sailor said:**
> Intuit is a Microsoft lap dog.  I am trying to help my daughter with some work with her company using Quick Books On Line.  I tried to log on and got an error message saying I had to use Windows Explorer 6 or higher or Firefox for Windows version 3.0 or higher.

Is there a work around for this, so I don't have to restart to the Windows virus?   What's so damn special that Firefox for Linux can't be supported?


You could install Safari using wine.....see **[Here]("http://www.youtube.com/watch?v=Gft8t7lwTTI&feature=response_watch")**
Also you could install Virtualbox and install windows as the guest OS

---

### Post by SteveHillier on 2010-01-12
I had a similar situation recently when I needed to run a DVR camera monitoring system on a PC.
The DVR software needed some active X elements that were not available for FF so I could only run this in IE7 or IE8.
You may have a similar problem.

---

### Post by katie-xx on 2010-01-12
I have a similar situation with our office firepass system.
I cant remote in with Linux as an active X control needs to be installed.
Quite common I believe.
Kate

---

### Post by Sir Jasper on 2010-01-12
Hi,

Firefox (all versions) for Windows work in Wine. With Wine installed the portable version of say, 3.5.7 could be downloaded from PortableApps [http://portableapps.com/](http://portableapps.com/) (see top right) and installed into say, your Home directory.

If you need IE6 (for Wine) as well, or instead of FF, it is available in Wine-Doors and also works very well in Wine.

My regards

---

### Post by studmf on 2010-01-12
> **Sir Jasper said:**
> Hi,

Firefox (all versions) for Windows work in Wine. With Wine installed the portable version of say, 3.5.7 could be downloaded from PortableApps [http://portableapps.com/](http://portableapps.com/) (see top right) and installed into say, your Home directory.

If you need IE6 (for Wine) as well, or instead of FF, it is available in Wine-Doors and also works very well in Wine.

My regards

I like the FF Portable recommendation.

---

### Post by SteveHillier on 2010-01-12
I don't think the OP was saying that they could not run FF in Windows.
They were saying (at least I think they were saying) that when they run the 'Quick Books On Line' system using FIrefox then that website demands that they run it in a version of IE greater than 6.

If I read this right then your comment > **Sir Jasper said:**
> Firefox (all versions) for Windows work in Wine. whilst perfectly correct will not help the OP with their problem.

---

### Post by mocoloco on 2010-01-12
Very good question, it must not require ActiveX for FF on Windows, so why the OS restriction?  Doesn't make sense to me either, probably they're being lazy and don't want to test/support it so they just block it.

Maybe you could use the [Firefox user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59").  It doesn't have FF Win by default but you could google for a profile for it.

---

### Post by Desert Sailor on 2010-01-12
Thanks guys for all the ideas.  I tried to get IE8 going in Wine, but that didn't work.  I didn't think about FF for Windows running under Wine.  I think I'll give that a try.

---

### Post by SteveHillier on 2010-01-12
Apologies to Sir Jaspar, I might have been hasty in my criticism of his contribution.  I now see where he is coming from.

---

### Post by Nottawa on 2010-01-12
I had a web site that I needed access to but could not with Ubuntu's version of Firefox.  I installed Mozilla's Firefox and was then able to access the page and all its features.  It seems that many pages don't like Shiritoko/Ubuntu FF.

---

### Post by Sir Jasper on 2010-01-12
Hi,

I think it was carlee who recently explained how to install IE8 in Wine (and I believe it worked).

Perhaps you could try the search box (above top right) with IE8 as the main search term and carlee in the poster section?

I have no idea about ActiveX and Wine or your particular financial program and my apology if I have misunderstood your needs.

My regards

Steve, there is no need to apologise (and you may be right) - if we can help between all of us then that will suit our questioner.

---

### Post by tom.swartz07 on 2010-01-12
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

Im not sure if anyone touched on this, but its well worth a shot.
Especially because you need the ActiveX controls...

---

### Post by Desert Sailor on 2010-01-12
OK...  Thanks to all of you, that was great help, and very fast.  We have a working solution, I'll mark the thread SOLVED.  

I was able to copy my version of Firefox for Windows from my "library" on my Windows partition, and install it under Wine.  Took about 30 seconds, and works perfectly.  Quick Books On Line thinks I am on FF for Windows and I have full and complete access.  

THANKS!!!!!

---

### Post by b0b138 on 2010-01-12
FYI, if I go to the site and click through to Quick Books Online Free and click Start Now, I get a browser not supported yadda yadda page.

But, with user agent switch set to IE, I get to create a login. Not sure if it will keep working past that, but something to look into.

---

