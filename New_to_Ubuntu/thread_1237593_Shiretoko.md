---
title: "Shiretoko ???"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by ericstrom on 2009-08-11
Suddenly my Firefox icon is gone and replaced with something called Shiretoko. This seems to be some type of version of FireFox or something. I'm not sure why suddenly appeared on my desktop and replaced firefox. I don't remember downloading it.

Also checked Add/Remove and I don't see anything called Shiretoko. 

How do I get rid of Shiretoko ?
How do I get Firefox back (it is already selected in add/remove)
Why did Shiretoko suddenly show up ?

---

### Post by nothingspecial on 2009-08-11
It`s firefox-3.5. Did you do some updates? If so you have updated it.

Don`t worry about it.

---

### Post by ericstrom on 2009-08-11
I upgraded to 3.5.

But what if I want the FireFox iccon back ? What if I don't want Shiretoko showing up all over my browser ?

---

### Post by j.bell730 on 2009-08-11
Shiretoko was the development name for Firefox 3.5.
Linux users still have the beta version, they will get updated soon to the release versions, it's not that big of a deal.

---

### Post by louieb on 2009-08-11
This is not the 1st time Mozilla and Ubuntu/Debian have gone different ways over Firefox and Thunderbird naming and logo. Believe Debian still uses the name Iceweasel for Firefox.  

Last time (2006) it happened some people wrote scripts to restore the Firefox and Thunderbird logos. Anyway just watch around some script writer that feels the same way you do will post a script or how-to for restoring  the Firefox logo.  

:guitar:History does repeat itself.

---

### Post by Tibuda on 2009-08-11
See [http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

---

### Post by amitabhishek on 2009-08-11
> **ericstrom said:**
> I upgraded to 3.5.

But what if I want the FireFox iccon back ? What if I don't want Shiretoko showing up all over my browser ?

Ignore repos if you don't like the name and icon. Grab the tarball of Firefox 3.5 from Firefox's website and install the tarball.

---

### Post by lovinglinux on 2009-08-12
> **ericstrom said:**
> Suddenly my Firefox icon is gone and replaced with something called Shiretoko. This seems to be some type of version of FireFox or something. I'm not sure why suddenly appeared on my desktop and replaced firefox. I don't remember downloading it.

Also checked Add/Remove and I don't see anything called Shiretoko. 

How do I get rid of Shiretoko ?
How do I get Firefox back (it is already selected in add/remove)
Why did Shiretoko suddenly show up ?

See explanations and solutions at [http://ubuntuforums.org/showpost.php?p=7768729&postcount=23](http://ubuntuforums.org/showpost.php?p=7768729&postcount=23)

It's a thread discussing exactly the same problem.

---

### Post by kestal on 2009-08-12
Personally, I kind of like the idea of having codenames on the versions themselves. However, I'd prefer keeping the firefox icon as well as mentioning firefox in the name. As right now it just mentions Shiretoko, rather than -- Blah Blah Blah "- Mozilla Firefox Shiretoko" --

3.6 is codenamed Namoroka, so that should be interesting on Karmic when they switch the default to 3.5. RC of 3.6 should be available around the official launch of Karmic, too. So there will be people who will probably bring this up around the launch date of Karmic, as well. I usually adopt the next version of Firefox when it hits Beta, sometimes before depending on stability and the amount of bugs.

---

### Post by lovinglinux on 2009-08-12
> **kestal said:**
> Personally, I kind of like the idea of having codenames on the versions themselves. However, I'd prefer keeping the firefox icon as well as mentioning firefox in the name. As right now it just mentions Shiretoku, rather than -- Blah Blah Blah "- Mozilla Firefox Shiretoku" --

3.6 is codenamed Namoroka, so that should be interesting on Karmic when they switch the default to 3.5. RC of 3.6 should be available around the official launch of Karmic, too. So there will be people who will probably bring this up around the launch date of Karmic, as well. I usually adopt the next version of Firefox when it hits Beta, sometimes before depending on stability and the amount of bugs.

The issue is not the name or the logo, but the fact that a lot of people installed Firefox 3.5 using alternative or semi-official repositories and now they are getting unwanted, unstable updates that are messing with the official icon launchers and symlinks of Firefox 3.0.

---

### Post by kestal on 2009-08-12
Odd.. I have Shiretoko (which is 3.5, just unbranded to my knowledge? - Check the about section), and I have not had any problems with unstable updates or messing with anything.

The way I understand it... The icon changed, and the name. Everything else is the same to me. Its just that firefox 3.0 is Jaunty's default/official firefox version, right? 3.5 will not be branded for Jaunty, but starts to be branded for Karmic as their official/default .. while Karmic will not be able to automatically update to 3.6, but rather be able to install Namaroka, so people can switch back between 3.5 and 3.6 while the bugs in 3.6 get hammered out for 10.4 as their branded Firefox (if 3.6 namaroka is far enough in its developement and bug testing, that is).

Isn't just naming it shiretoko a way for people to be able to experience Firefox 3.5 (not named as such) for Jaunty (Default/Official firefox = 3.0) by creating another profile with the same bookmark list. Again, I have not had any problems with Shiretoko (unbranded firefox 3.5) at all, and the reason they do this is so that you can run both side by side.

Is this, somehow, an incorrect evaluation of Shiretoko? They decided to keep its name in order to be able to use both versions side by side. (unless updated/removed/reinstalled a specific way), as it is the final version according to my about page.

---

### Post by lovinglinux on 2009-08-12
> **kestal said:**
> Odd.. I have Shiretoku (which is 3.5, just unbranded to my knowledge? - Check the about section), and I have not had any problems with unstable updates or messing with anything.

That's because you have just installed it from the universe repositories. People experiencing issues are those that added ubuntu-mozilla-daily or ubuntu-mozilla-security to their software sources, so they will continue to get updates between Mozilla's official releases. Which means you still have Shiretoko 3.5.2 as you should, but the other users already have 3.5.3pre or something like that, which is the one causing the issue with the official logo and symlinks. Basically, it seems that this version of Shiretoko is replacing the Firefox launcher logo and symlink to firefox-3.5.3pre instead of just being accessible through "Applications >> Internet >> Shiretoko Web Browser". So now, the users are unable to launch FF 3.0 from the regular launchers.

> **kestal said:**
> The way I understand it... The icon changed, and the name. Everything else is the same to me. Its just that firefox 3.0 is Jaunty's default/official firefox version, right? 3.5 will not be branded for Jaunty, but starts to be branded for Karmic as their official/default .. while Karmic will not be able to automatically update to 3.6, but rather be able to install Namaroka, so people can switch back between 3.5 and 3.6 while the bugs in 3.6 get hammered out for 10.4 as their branded Firefox (if 3.6 namaroka is far enough in its developement and bug testing, that is).

That's not the issue. The question is not why FF 3.5 is branded Shireotoko, but why the regular launchers were replaced with Shiretoko link and logo. It shouldn't be happening if you just install FF 3.5 from the universe repositories, since it creates it's own launchers. The problem now is that Shiretoko is hijacking FF 3.0 launchers.

> **kestal said:**
> Isn't just naming it shiretoku a way for people to be able to experience Firefox 3.5 (not named as such) for Jaunty (Default/Official firefox = 3.0) by creating another profile with the same bookmark list. Again, I have not had any problems with Shiretoku (unbranded firefox 3.5) at all, and the reason they do this is so that you can run both side by side.

You are correct and you shouldn't experience any problems because you still have Shiretoko 3.5.2.

---

### Post by kestal on 2009-08-12
**Edit:** 
You must have posted within 10 seconds of mine as I refreshed in a previous window 
and saw nothing new. However, I see what you mean. I did a clean install of Firefox 3.5, 
so perhaps that changes things in my case. Sorry for the intrusion ;)


**HOWEVER**, with that said, the original posters quote:

> I upgraded to 3.5.

But what if I want the FireFox iccon back ? What if I don't want Shiretoko showing up all over my browser ?

He seemed confused why Shiretoko was on his browser to begin with, rather than just seeing Mozilla Firefox, Firefox 3.5, etc. Thus, that is why I replied with the things I did :) Without reading between the lines, really, on the other problems you mentioned :P

---

### Post by yarko on 2009-08-19
The problem w/ shiretoko branding is how it identifies itself to the network - this makes it impossible to connect to actions (today, for example, I could not join a webinar - "only IE or Firefox supported").  Since my firefox 3.0 seems non-existent (?)  I wound up rebooting in Fedora to join.   Had the same experience with a jquery demo page;  this repeats.

Branding can be whatever, but at the protocol level, the browser should correctly identify itself so that it is functional!

---

### Post by square_monkey on 2009-08-29
I found that changing part of the UA string solved the problem; you can follow these steps:

1. In your address bar type 'about:config'
2. Agree to the disclaimer if presented
3. Below the Tab Bar in the text field labeled 'Filter' (Ctrl+F to select) type 'useragent'
4. Locate the key 'general.useragent.extra.firefox' and change the value from 'Shiretoko/3.5.2' to a UA string that is supported by the website you are visiting.

I loaded up Firefox 3 and copied 'Firefox/3.0.13', but [with Google you can find a complete list](http://www.google.co.uk/search?hl=en&safe=off&q=list+of+useragent+strings&btnG=Search&meta=).

---

### Post by dj-toonz on 2009-08-29
I don't understand this Fedora 11 already has Firefox 3.5 has the default browser & thunderbird 3 in the repos but Ubuntu users are stuck with firefox 3.0.13 as the default browser intill ubuntu 9.10 comes out in oct then that will have firefox 3.5 (yes I know you can download firefox 3.5 from the update repos but that gives u 2 browsers like downloading & using ubuntuzilla to get firefox 3.5, why can't ubuntu progress like fedora & have the bleeding edge software in it, saves us having to resort to using ppa repos to keep the system up to date with the latest software

---

### Post by Norm24 on 2009-08-29
This is what I did to make sure I have the very latest Mozilla release.[HTML]http://www.psychocats.net/ubuntu/firefox[/HTML]

---

