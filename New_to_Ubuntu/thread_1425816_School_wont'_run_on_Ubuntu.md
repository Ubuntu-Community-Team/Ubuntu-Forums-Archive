---
title: "School wont' run on Ubuntu"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Aster-Phoenix on 2010-03-09
Hello, I've been using Ubuntu 9.10 for about a week now and its great. But I am online schooled and my school website doesn't support linux and will not work. Is there a program that makes my school think I'm running Windows or Mac?

---

### Post by undecim on 2010-03-09
Check out the user agent switcher extension for firefox.

---

### Post by dearingj on 2010-03-09
You could try Firefox's User Agent Switcher extension. A lot of web sites determine your operating system based on your user agent.

---
edit: I see I was beaten to the punch :)
You can find a list of user agents, downloadable as an xml file (which can be imported by the extension) here: [http://techpatterns.com/forums/about304.html](http://techpatterns.com/forums/about304.html)

---

### Post by Black Hawk on 2010-03-09
Hi. 

Are there specific things that doesn't work in linux or are you simply blocked from using the site because it detects that you are running linux. If the latter is the case try looking into the user agent switcher addon for firefox. It masks your browser, and you can make the site "think" that you are running IE/Firefox/Chrome on Windows. NOTE: this does not fix actual issuse with the site, but you might get around a blocking machanism.

---

### Post by oingk on 2010-03-09
To download the extention the others have suggested, you have to use Firefox browser and go here:
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

and click "Add to Firefox"

---

### Post by TurnOfTide on 2010-03-09
User agent switcher might work. But oddly enough some java applets actually can be made to only work on IE and not firefox.... (how a developer caused that to happen is an atrocity in all things java and just programming in general).


It may be that you really need to run IE, if you are running into that situation. Also it is probably your school's and your school's official IT policy that you must run 1) windows and 2) IE. As much as they may not be fun, it does help to have/follow standards though. You can always inquire about that.

---

### Post by bornagainpenguin on 2010-03-09
> **TurnOfTide said:**
> As much as they may not be fun, it does help to have/follow standards though. You can always inquire about that.

Mandating Windows or Internet Explorer when not strictly needed is the *opposite* of having standards, not the presence of them.

--bornagainpenguin

---

### Post by Aster-Phoenix on 2010-03-09
Well the add on didn't work and i know i can run it on Firefox cuz thats what i used on my old windows machine.

---

### Post by oingk on 2010-03-09
Did you set the add-on to behave as Internet Explorer?

---

### Post by doas777 on 2010-03-09
have you installed the sun java runtime?
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

blackboard and many other sites require sun java, and unfortunately the open version (icedtea I believe) does not quite cut it.

how do you know that it doesn't work? do you get a message that you have to use IE, or does it just fail to load at some point?

---

### Post by rewyllys on 2010-03-09
Aster-Phoenix, what is the URL of your school's Website?  If you're willing to provide it, some of us could try checking it out to see what might work in Ubuntu to use the Website.

---

### Post by Aster-Phoenix on 2010-03-09
The website is time4learning.com but you have to log in to get to the lessons in which it has the problem. With the app i was able to get to the lessons which is an improvement as it used to just say linux is not supported. 
I don't mind giving the log in credentials to who wants them, theres not much you can do except look at my report card xD

---

### Post by doas777 on 2010-03-09
> **Aster-Phoenix said:**
> The website is time4learning.com but you have to log in to get to the lessons in which it has the problem. With the app i was able to get to the lessons which is an improvement as it used to just say linux is not supported. 
I don't mind giving the log in credentials to who wants them, theres not much you can do except look at my report card xD


if it specifically states that linux is not supported, then it is still leaking your system identification, even with the altered agent string.

---

### Post by doas777 on 2010-03-09
hmmmm. I'm able to run the lesson demos without trouble. I haven't hacked my agent string, so they must check at or after login.

---

### Post by anthonyrossbach on 2010-03-09
Also maby its telling your OS by the fact that the Firefox in Ubuntu is made for Ubuntu try installing wine and installing safari you may be able to use the site after that!

If not you can use windows for school!

You can if you have a XP CD have windows on a portion of your computer for school. I do that and XP only needs a 6-10GB portion so there is lots of space left on Ubuntu.

To install if you make a new portion on your hard drive by running ubuntu 8.10+ off a CD you can make a portion and when installing windows XP you should be able to install in that portion!

---

### Post by rewyllys on 2010-03-09
I just spent a few minutes at time4learning.com.  I was able to use the demos without difficulty.  It occurred to me that your problem might lie with your browser.  I'm using Firefox 3.5.8 and some add-ons, of which the only one that seems to me possibly related to your problem is "Ubuntu Firefox Modifications", v. 0.8.  

If you're using something other than v. 3.5.8 of Firefox with this add-on, I would suggest that you try using them.  If you don't have Firefox at present, the Synaptic Package Manager (under System > Administration) will install it for you.  Once you have Firefox, go in its Menu to Tools > Add-ons > Get Add-ons.   Then choose "Browse All Add-ons", look for "Ubuntu Firefox Modifications", and select and install it.

Assuming you can get to a particular lesson at time4learning.com this way, you'll see an outline of a window. Click inside the window, and the lesson should start running.

Hope this helps you.

---

### Post by doas777 on 2010-03-09
just outta curisoity, did you change the OS in the agent as well?
here is mine:P
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.8) Gecko/20100214 Ubuntu/9.10 (karmic) Firefox/3.5.8

does yours look more like this?
Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.8) Gecko/20100202 Firefox/3.5.8

---

### Post by anthonyrossbach on 2010-03-09
> **rewyllys said:**
> I just spent a few minutes at time4learning.com.  I was able to use the demos without difficulty.  It occurred to me that your problem might lie with your browser.  I'm using Firefox 3.5.8 and some add-ons, of which the only one that seems to me possibly related to your problem is "Ubuntu Firefox Modifications", v. 0.8.  

If you're using something other than v. 3.5.8 of Firefox with this add-on, I would suggest that you try using them.  If you don't have Firefox at present, the Synaptic Package Manager (under System > Administration) will install it for you.  Once you have Firefox, go in its Menu to Tools > Add-ons > Get Add-ons.   Then choose "Browse All Add-ons", look for "Ubuntu Firefox Modifications", and select and install it.

Assuming you can get to a particular lesson at time4learning.com this way, you'll see an outline of a window. Click inside the window, and the lesson should start running.

Hope this helps you.

That may be the best way to start and if you cant and if in the future you need windows you can run both and/or you can use wine to run a windows browser not made for Ubuntu and that may help trick them.

I make websites for a living and I find what OS they are using by the browser and then the OS that package is made for so if you install Safari in wine It should trick it if that is how they are doing it!

---

### Post by arochester on 2010-03-09
If you Google: linux time4learning.com

It shows: [http://www.facebook.com/posted.php?id=85610959500&share_id=343549222375&comments=1](http://www.facebook.com/posted.php?id=85610959500&share_id=343549222375&comments=1)

Which says:  Time4Learning.com  Excellent "how to" video for anyone using Time4Learning on a Linux operating system! Many thanks to Maid Mercy for a great resource. If a picture is worth a thousand words then a video is priceless!
Help with time4learning and Linux
[www.youtube.com](www.youtube.com)
This video is to show a fix for Linux users who want to use time4learning but can't. This will fix log in issues , and navigating. I have found a problem with 5th grade math using Linux. I do have a fix for it , but it's not permanent. ...

---

### Post by stevenh512 on 2010-03-09
> **anthonyrossbach said:**
> You can if you have a XP CD have windows on a portion of your computer for school. I do that and XP only needs a 6-10GB portion so there is lots of space left on Ubuntu.

To install if you make a new portion on your hard drive by running ubuntu 8.10+ off a CD you can make a portion and when installing windows XP you should be able to install in that portion!

If you absolutely have to run Windows, you don't have to repartition your HD and you can run it as a guest OS right inside Ubuntu. Just download VirtualBox (virtualbox.org) and set up a VM for running Windows.

I'm sure the install will be a little slower than you'd expect, but once you install the guest OS additions it should be pretty quick. I've never done Windows under Linux this way before, but I've done the opposite and Ubuntu 9.10 Desktop with the guest additions runs almost as fast in VirtualBox under XP and Win7 as it does natively.

---

### Post by Aster-Phoenix on 2010-03-09
> **arochester said:**
> If you Google: linux time4learning.com

It shows: [http://www.facebook.com/posted.php?id=85610959500&share_id=343549222375&comments=1](http://www.facebook.com/posted.php?id=85610959500&share_id=343549222375&comments=1)

Which says:  Time4Learning.com  Excellent "how to" video for anyone using Time4Learning on a Linux operating system! Many thanks to Maid Mercy for a great resource. If a picture is worth a thousand words then a video is priceless!
Help with time4learning and Linux
[www.youtube.com]("http://www.youtube.com")
This video is to show a fix for Linux users who want to use time4learning but can't. This will fix log in issues , and navigating. I have found a problem with 5th grade math using Linux. I do have a fix for it , but it's not permanent. ...
THANK YOU THANK YOU THANK YOU!!!!! It works now thank you so much!!!!!

---

### Post by Lifebandit on 2011-01-28
Thanks guys for this information!! I recently switched my family to Ubuntu and my son is also home schooled through Time4learning. I spent the last 4 days trying to get the web site to work properly on the Linux version of Firefox. I already had the User Agent addon installed but it didn't want to run under IE 6, 7 or 8. I downloaded that XML file that was mentioned and that gave me more agents to choose from. Got it to work with firefox 3.0.10(winxp) agent. 

Very nice, thanks again.

---

