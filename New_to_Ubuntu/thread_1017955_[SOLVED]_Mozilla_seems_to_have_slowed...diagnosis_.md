---
title: "[SOLVED] Mozilla seems to have slowed...diagnosis help?"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by joejoe148 on 2008-12-21
Green green ubuntu hardy user.  I seem to have triggered something in firefox that has slowed it down.  My guess is when I tried to load flash.  I am going back to that right now but I dont know any diag tools that may help.  My speed doesnt seem to be processor related, the hard drive isnt active.  Its just web page loads taking a long time.  Is there the equivalent of the windows task manager where I can see processes and cpu load etc?

---

### Post by SamNSane on 2008-12-21
System / Administration / System Monitor may be helpful to you, in that it's similar to Task Manager in Windows.

Firefox under Ubuntu can be a real dog depending on a lot of things. Flash can be a problem, but I've more often found the trouble to be related to the scripts that are used with Flash at various Web sites. Some of those will bring an entire system to standstill, and I've even the java vm trigger a shutdown due to the CPU reaching critical temp on some laptops.

---

### Post by joejoe148 on 2008-12-21
Thats scary.  This laptop isnt the newest but is should be beefy enough to browse the web.  I found "top" and what I can see is no problems.  sigh.

---

### Post by SamNSane on 2008-12-21
Well, if TOP and / or System Monitor aren't showing you any process making inappropriate use of CPU cycles that's going to make it a little harder to figure out what's going on. If you're watching your CPU / system / GPU temps you should be okay.

There are so blasted many things that can cause browser creep, some of which affect the rest of the system and some of which don't. Upon re-reading your original post I think that your problem may very well be caused by an add-on or the JRE. If it's the JRE then it's likely to be a lot worse at some sites than at others. Removal of the add-ons and then careful testing as you add them back might reveal something. I don't know what to do about JRE problems -- except not use it, which isn't very practical these days.

I'm pretty annoyed by how easily Firefox can be brought down by something as simple as the scripting on a standard newspaper crossword puzzle page. And when the JRE problem causes the whole system to shut down due to thermal overload, that's just ridiculous.

There are a number of bug reports filed on this sort of issue on launchpad. They date back at least a couple of versions of Ubuntu, and I see little evidence that it's being worked on.

I presume that it's fixable. The systems I've seen this on work just fine under much heavier loads in WinXP and Vista.

---

### Post by mkvnmtr on 2008-12-21
There are a couple of options in preferences that can use a lot of time. One is tell me if the site is a suspected attack site and the other is tell me if it is a suspected forgery. If you feel safe doing it uncheck these to see if that is eating up a lot of time. On mine it was. Ad blocker also was taking a lot of time. I had installed more than one list for it to check and it was a mistake.

---

### Post by Cracauer on 2008-12-21
We had a number of cases where the urlclassifier wrecked people's firefox.

What's the largest file in your profile?

---

### Post by joejoe148 on 2008-12-22
OK, a little more info, pentium m laptop with 512 meg memory.  Just loaded hardy and have been slowly trying to build a functional computer.  web browsing seemed fine but no flash sites(i hadnt really tried them after I realized flash wanst installed so I am not sure) I installed flash and things just creeped.  I removed the package and reinstalled it.  I also removed firestarter as the last thing I had installed. But i had also done some magic to get the wireless working (fwcutter) and attempted some more magic (alien) for printer drivers.  all of these occurred before I started really paying attention to web speed.  Hell Maybe its the wireless.  sigh 

Yes some sites seem slower than others.  This site (ubuntu forums) works but it is much slower than the comparable celeron laptop on xp.  Cnn doesnt load completely, my.yahoo looks like its done but the page load indicator is still running even after several minutes.  I assume thats java.  the 929dave.fm website, it has flash on it, is pitiful and brings back memories of dial up.
Does ubuntu benefit from clean installs like windows?  I wonder is I should start over and get the wireless running and then see.

Its OK, im on vacation :)

---

### Post by joejoe148 on 2008-12-22
largest file in my profile? I am going to have to begin my looking up urlclassifier and get back to you

---

### Post by SamNSane on 2008-12-22
> **joejoe148 said:**
> OK, a little more info, pentium m laptop with 512 meg memory.  Just loaded hardy and have been slowly trying to build a functional computer.  web browsing seemed fine but no flash sites(i hadnt really tried them after I realized flash wanst installed so I am not sure) I installed flash and things just creeped.  I removed the package and reinstalled it.  I also removed firestarter as the last thing I had installed. But i had also done some magic to get the wireless working (fwcutter) and attempted some more magic (alien) for printer drivers.  all of these occurred before I started really paying attention to web speed.  Hell Maybe its the wireless.  sigh 

Yes some sites seem slower than others.  This site (ubuntu forums) works but it is much slower than the comparable celeron laptop on xp.  Cnn doesnt load completely, my.yahoo looks like its done but the page load indicator is still running even after several minutes.  I assume thats java.  the 929dave.fm website, it has flash on it, is pitiful and brings back memories of dial up.
Does ubuntu benefit from clean installs like windows?  I wonder is I should start over and get the wireless running and then see.

Its OK, im on vacation :)

Offhand, I'd say that you may have found a way to while away your vacation time!

;)

Seirously, are you saying that this Hardy installation is an upgrade installation from an earlier version of Ubuntu? If that's the case, then the use of workarounds like you've had to use for your wireless and printer functionality can really ball things up if those changes were made before the version upgrade. Upgrade installations work reasonably well for bog standard installations, but use of proprietary drivers, ndiswrapper, replacements for standard parts of the distro (like using a replacement network manager), and other special alterations of the distro seems to cause a lot of problems for the upgraded OS.

If you decide to do a clean installation, I recommend that you proceed very methodically. First get your basic networking running the way you want it. Then, after you've got Internet working and have had a chance to be sure that a basic Firefox installation works okay, add things like flash and add-ons **one-at-a-time**, testing browser performance after each change. Also, test the browser performance at sites you use a lot after each change in browser / add-on settings. That way you're much more likely to find out which add-ons and settings cause the browser to be slower.

A Pentium M should work okay with Ubuntu, but 512 MB memory for these operating systems with a full gnome desktop is a little on the low side. However, I'm sure that the memory capacity itself is not the primary cause of your problems, because you'd be seeing slowness in other aspects of operation in addition to browser performance.

If you want to test from where you're at instead of doing a clean installation, I'd suggest removing the java vm and removing all plugins and add-ons from the browser and testing it that way. (Pages won't load entirely if they use scripting and flash, but you'll still have an idea of basic browser speed.) Then put the java vm back and test the browser. Then add flash and test. Then other add-ons (one-at-a-time) with testing after each. But if the browser is slow right from the get-go, I'm thinking you might need a clean installation.

---

### Post by joejoe148 on 2008-12-22
Thanks for the replay, yes you are correct about spending vacation time.  The install was a clean install of 8.04 but since I am brand spanking new to this I solve problems with the first idea i find on the forums or google.  I cant say I am learning a bunch because some of the instructions are cryptic even when I try to analyze the commands one by one. It does seem to be java thats the problem, I wandered around online for about an hour and most sites loaded cleanly, if a little slow, unless I went to a big page like cnn or something busy with a bunch of stuff running. 

something funny, the openjdk.java.net website wouldnt load.  I suppose it uses java.

thanks again.

---

