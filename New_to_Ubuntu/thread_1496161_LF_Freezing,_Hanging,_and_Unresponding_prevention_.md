---
title: "LF: Freezing, Hanging, and Unresponding prevention steps/tips"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Mr. R on 2010-05-28
I would probably say that even though my usage time of Ubuntu is very limited, I would enjoy using this operating system if it didn't hang, freeze, or go unresponsive. Sometimes the GNOME panel will hang where the Menubar, notification bar, and other functions are. Sometimes the system will hang (can use keyboard and move mouse) or freeze entirely (cannot move mouse or use keyboard).

The program that has most frequently gone unresponsive is Firefox. This is understandable because I use it all the time. So I bet if I used other applications more frequently, then they may freeze/hang more frequently.

I'm looking for tips, techniques, and ways to prevent these situations from happening on Ubuntu 10.04. When I use Windows 7, of course it rarely ever hangs or freezes. The worst that has happened so far is computer CPU usage latency. The nice thing in Windows is you can easily kill a background task by putting in its name, but not a daemon with kill.

I'm tired of Firefox crashing. I reinstalled Firefox after saving my bookmarks to see if a clean install would help. Since it happens randomly, I cant really tell if it will happen again.

And basically my questions are:

What prevention tips and techniques can I do to prevent Ubuntu from crashing, hanging, freezing, and becoming unresponsive less frequently or never?

Where are reported log files of freezes are kept, what keywords are used to  identify them, and how do I quickly find them?

How do I kill a task simply by entering its name, and how do I make the  firefox-bin task automatically end itself when the Firefox browser  closes after force quit?

Thank you for your help.

---

### Post by widda on 2010-05-28
I'll watch this thread with interest, I hadn't quite formulated the right question, but I believe that's the question:)

---

### Post by Mr. R on 2010-05-29
> **widda said:**
> I'll watch this thread with interest, I hadn't quite formulated the right question, but I believe that's the question:)
I see.

Well, I thought 8.04 was more stable, but I only consider distros with LTS, and I needed full iPod support.

---

### Post by widda on 2010-05-29
For what it's worth, I have come across in my travels here one cause of such misbehaviour: having a desktop background image of a size greater than 1400 pixels in width.

---

### Post by Mr. R on 2010-05-29
> **widda said:**
> For what it's worth, I have come across in my travels here one cause of such misbehaviour: having a desktop background image of a size greater than 1400 pixels in width.
Mine is 1280x1024. If it slows down x too much or anything then maybe I can try to rid myself of the background for a bit.

---

### Post by Stigmata13 on 2010-05-29
As for the firefox problem, I'd recommend giving Google Chrome a try
[http://www.google.com/chrome](http://www.google.com/chrome)
It's very easy to install, and out of the box generally runs better than firefox does (from what I can tell)
Alternatively I've heard some good things about Swiftfox, which is pretty much firefox just optimized for your type of cpu.

---

### Post by Mr. R on 2010-05-29
> **Stigmata13 said:**
> As for the firefox problem, I'd recommend giving Google Chrome a try
[http://www.google.com/chrome](http://www.google.com/chrome)
It's very easy to install, and out of the box generally runs better than firefox does (from what I can tell)
Alternatively I've heard some good things about Swiftfox, which is pretty much firefox just optimized for your type of cpu.
I have used Chrome, and it does run quicker. I cannot help the fact that I have been a Firefox user for a long time. I have addons that I cannot use without Firefox. I have two separate profiles for more privacy settings and less plug-ins; and more history settings with more plug-ins. The file menu bar and everything is more useful for me in Firefox than Chrome. Simply put, Firefox has more functionality than Chrome, and I like programs, browsers, or anything with more functionality and customization. It is the reason why OpenOffice.org and MS Word 2003 are better than MS Word 2007 in those areas. Not a lot of people think these features are important, but my preferred applications don't change easily if I see important or intriguing features missing in other ones.

tl;dr line:
I have used Chrome before, but it's not really what I'm looking for, but I can try SwiftFox.

---

### Post by Stigmata13 on 2010-05-29
> **Mr. R said:**
> I have used Chrome, and it does run quicker. I cannot help the fact that I have been a Firefox user for a long time. I have addons that I cannot use without Firefox. I have two separate profiles for more privacy settings and less plug-ins; and more history settings with more plug-ins. The file menu bar and everything is more useful for me in Firefox than Chrome. Simply put, Firefox has more functionality than Chrome, and I like programs, browsers, or anything with more functionality and customization. It is the reason why OpenOffice.org and MS Word 2003 are better than MS Word 2007 in those areas. Not a lot of people think these features are important, but my preferred applications don't change easily if I see important or intriguing features missing in other ones.

tl;dr line:
I have used Chrome before, but it's not really what I'm looking for, but I can try SwiftFox.

That's reasonable, I was the same way, and right now I still use both firefox and chrome.
You can get swiftfox here: [http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)
I've heard it gives a performance increase, but I don't think it's going to be a huge one. All your addons you use should work just fine though.

---

### Post by lovinglinux on 2010-05-29
> **Mr. R said:**
> I have used Chrome, and it does run quicker. I cannot help the fact that I have been a Firefox user for a long time. I have addons that I cannot use without Firefox. I have two separate profiles for more privacy settings and less plug-ins; and more history settings with more plug-ins. The file menu bar and everything is more useful for me in Firefox than Chrome. Simply put, Firefox has more functionality than Chrome, and I like programs, browsers, or anything with more functionality and customization. It is the reason why OpenOffice.org and MS Word 2003 are better than MS Word 2007 in those areas. Not a lot of people think these features are important, but my preferred applications don't change easily if I see important or intriguing features missing in other ones.

tl;dr line:
I have used Chrome before, but it's not really what I'm looking for, but I can try SwiftFox.

I agree. Chrome simply cannot do what I do with Firefox and can't be customized at all.

See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) or if you prefer to go directly to my site, then [http://firefox-tutorials.blogspot.com](http://firefox-tutorials.blogspot.com)

Firefox works like a charm for me.

---

### Post by Mr. R on 2010-05-31
Alright, so I've used Swiftfox and it works  fine. It so much quicker than FireFox. However, it did crash on one occasion. The strange thing about this is that I could start System Monitorup after the crash, but soon after, other things stop working. It's kind of strange because sometimes I get a randomly set time or a chance to start other programs without them freezing, and soon they can freeze when I perform any functions inside them. Oh, I also have to forcefully shutdown my computer. After the shutdown the uninterruptable process firefox-bin/swiftfox-bin cannot be quit by kill, force, or anything that I currently know, the next time I boot up data can be damaged (Ubuntu may start analyzing the disk for errors.)

So I read the article and disabled Block reported attack sites and Block reported web forgeries. I read about freezing due to memory problems. I'm not sure memory is a problem, but I'll run Swiftfox/FireFox in safe mode and see if it shows up anything. I just uninstalled one plug-in I'm not using anymore, I have AdBlock Plus, Unplug, Ubuntu Firefox Modifications, and DownThemAll! Right now swiftfox-bin is at about 70MB.

I read that the ps and kill functions would work, so I'll try those next time if, by luck, I can get a terminal open after the browser freezes.

---

### Post by widda on 2010-06-02
Mr R
My at-least-once-a-day freeze/hang -(after which I can limitedly get about awhile with Tab Enter Backspace etc till I screech to a halt)- has nothing to do with firefox- I use only Opera, because I think it's the best.
I don't do brutal shutdown anymore, cos there's ctrl alt F1 to get commandline into which put "sudo shutdown -r now" without the quotes, where "r" means restart [or ctrl alt F7 to return to prettywindows].

But anyway I guess it's good that we're the only 2 people in Linuxland to experience freeze/hang LOL

---

### Post by Mr. R on 2010-06-09
> **widda said:**
> Mr R
My at-least-once-a-day freeze/hang -(after which I can limitedly get about awhile with Tab Enter Backspace etc till I screech to a halt)- has nothing to do with firefox- I use only Opera, because I think it's the best.
I don't do brutal shutdown anymore, cos there's ctrl alt F1 to get commandline into which put "sudo shutdown -r now" without the quotes, where "r" means restart [or ctrl alt F7 to return to prettywindows].

But anyway I guess it's good that we're the only 2 people in Linuxland to experience freeze/hang LOL
I had just figured that out too: the "sudo shutdown 0"
I have to guess that hard shutdown makes problems. It's not like Windows where hard shutdowns are as safe as normal ones.

OK, thanks for the tip.

---

