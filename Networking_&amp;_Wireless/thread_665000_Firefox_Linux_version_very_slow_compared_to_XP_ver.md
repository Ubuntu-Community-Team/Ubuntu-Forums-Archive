---
title: "Firefox: Linux version very slow compared to XP version"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by reesje on 2008-01-11
Hi guys,

I don't want to start a fight here, I am just asking out of curiosity. I have a dual boot machine with both XP and Linux. In ubuntu the standard browser is firefox (currently version 2.0.0.11), I have installed the same version in XP. Also I have added the same plugins and add-ons in both environments, with roughly the same options and disabled IPv6 (didn't make a difference).

The thing is I have noticed that the linux version is slower than the XP version. With no add-ons other than fasterfox (I use this to tell how much time it takes to load a page) the XP version loads a page 2 times as fast as the linux version, and I can see that the CPU load is significantly higher in Linux. If I add the add-on "Image Zoom 0.3" there is no detectable decrease in speed in XP where as in Linux it slows down firefox to the point where it takes 3-5 times what it takes in XP. If I add the flash plugin it makes it even worse (although this is hardly a problem with firefox).

As a funny sidenote I can tell you that I installed Firefox in Wine and that is also faster than the native linux version!

Has anybody experienced this as well or is it just me? Is Firefox optimized for Windows use?

As suplemental info I can tell you that the machine is a XP2500@2GHz with a Radeon 9600 with 7.12 driver. Compiz turned off, this slows scrolling in the windows/documents unbearably slow.

I have also installed Ubuntu on my laptop (Pentiium M 2GHz) and it seems slow with firefox as well, and it also seem to load the CPU a lot when running Firefox.

Opera is much much much faster (faster than Firefox in windows), but it doesn't have the flexibility I wan't so I am not using that normally.

Thanks for your time!

BR,
René

---

### Post by HermanAB on 2008-01-11
You probably have a lame DNS in your /etc/resolv.conf.  Test the DNS servers with 'dig' then put the fastest one at the top of the file.

Cheers,

Herman

---

### Post by reesje on 2008-01-12
> **HermanAB said:**
> You probably have a lame DNS in your /etc/resolv.conf.  Test the DNS servers with 'dig' then put the fastest one at the top of the file.
I have DHCP for both Ubuntu and XP, so I don't see how that should affect the speed. Furthermore Ubuntu under wine runs faster that the native linux version as well and it is using (I assume) the same DNS server. And Opera is fast as well (much faster than firefox under any operating system).

Also I don't see how DNS lookup should max the load on the CPU?

I hope someone has an explanation and maybe a solution, because surfing in Ubuntu/Firefox is really slow. I know my machine is not very uptodate HW wise, but I don't see why Firefox should be this slow.

Thanks for your input.

BR,
René

---

### Post by steeleyuk on 2008-01-12
You might want to look into disabling IPv6 (if you don't require it). [This]("http://ubuntuforums.org/archive/index.php/t-87798.html") goes about explaining how to do it in Ubuntu.

You might also want to disable it into Firefox. In the location bar, type about:config and filter for ipv6. Change the value to true.

There's no guarantee that this will work however.

---

### Post by reesje on 2008-01-12
> **steeleyuk said:**
> You might want to look into disabling IPv6 (if you don't require it). [This]("http://ubuntuforums.org/archive/index.php/t-87798.html") goes about explaining how to do it in Ubuntu.

You might also want to disable it into Firefox. In the location bar, type about:config and filter for ipv6. Change the value to true.

There's no guarantee that this will work however.
I don't see how that should be a solution. As you can see from my first post, IPv6 is already turned of in Firefox. If it was a system level problem it should also be slowing down Opera and Firefox in Wine. It doesn't. It also doesn't make sense that this should be in question of IPv6 when it seems to be the processor determining the speed. Browsing in Firefox in Ubuntu loads the CPU significantly more than Firefox in Wine.

Can it be that Firefox is optimized for Windows and that is the reason that it runs so poorly under Linux? Im sure most people don't see it because they don't have old HW like me. If I were running it op a C2D I probably wouldn't have noticed it - but unfortunately I don't. And buying new HW to run poorly written software is a spiral without an end. If poor programming is the problem in this case.

What do you guys think? Has anybody else noticed the  Linux version being very slow compared to XP version even after you've done the optimizations that can be found various posts in various forums?

BR,
René

---

### Post by yoasif on 2008-01-12
I just switched from Mac OS X to Gutsy, and I agree; Linux web browsing is oddly slow compared to other OSes on the same hardware. 

However, I'm now using Opera, and it's quite quick. You might want to give that a shot. 

Install Opera 9.5beta to have Flash working, also.

---

### Post by Red Shift on 2008-01-12
I too have noticed that Firefox (from the repos) under Ubuntu is slower than Firefox under Windows.

My solution is to download Swiftweasel, an optimized build of Firefox for Linux.

I think you should rename the .mozilla folder in your user directory to .mozilla_old to prevent conflicts.  A new .mozilla folder will be created the first time you use Swiftweasel.  Apply your settings of choice.

The Athlon XP is a 32-bit processor and you're using a 32-bit OS, therefore download the .deb or tar.gz for i386 architecture and Athlon XP.

Your choices are:
swiftweasel-2.0.0.11_athlon-xpubuntu-i386.deb
swiftweasel-2.0.0.11_11-30-07_athlon-xp.tar.gz

[http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717)

---

### Post by yoasif on 2008-01-12
I haven't found the Swift* apps to be much faster (and my brother has complained of stability problems).

I'd just go to Opera and wait for the new version of Epiphany featuring Webkit rendering.

---

### Post by caen1944 on 2008-01-15
Hi Folks,

Same problem for me. Firefox is unusably slow under 7.10. It used to be just fine when I used 7.04. Things are fast as usual under windows.

Down in the bottom of the firefox window, it seems to stick on "looking up ..." or "transfering data from ..."

I have disabled IPv6 but to no avail.

This is really annoying. I cant use opera as it isn't available for 64 bit linux. I hope someone finds an answer.

Good luck

---

### Post by kneewax on 2008-01-15
I agree,  Like the others here I have found FF very slow in Ubuntu - despite following all the helpful advice on the forum. Disabling IPv6  helped a little BUT FF is much swifter in XP.  It really is an issue and one of the things stopping me from making the full switch over to the otherwise superb Ubuntu.

Kneewax

---

### Post by LeDechaine on 2008-01-17
Agreed **again**!

I've just installed Ubuntu 7.10 this week, and one of the first things i noticed was the slowness of Firefox in Ubuntu compared to XP, which is also installed (dual boot) on my computer. And I can *really* see the difference, because firefox is running very well under windows, and is even playing youtube videos without any problems (but high CPU usage though), but under linux, looking at youtube videos is square useless (maybe 5 images/second?!), scrolling in all webpages is **really** laggy, **zero** fluidity, and firefox even often freezes for 5-10secs (black and white) when i open like 10 tabs for looking at 10 different forum pages, while on XP, opening 20-30 tabs is nothing, and everything is **still** fluid even with all these tabs open!

Hey, i even notice lag when i hold down a letter to type right here!

Like i said, I can *really* see the difference, because i'm on a Pentium 3 866 with 320 megs of ram! ;)

**EDIT:** Solved my problem by setting the System -> Preferences -> Appearance -> Visual effects (tab) to None!
Now everything is fluid! Perfect! :D

---

