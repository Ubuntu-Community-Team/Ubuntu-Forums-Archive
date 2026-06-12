---
title: "Revert option in 10.04?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by kangarootoo on 2010-04-27
Okay, hello to you all. I am a pretty savvy computer user when it comes to Windows. I've been using Windows for a long time. I'm 30 now and while I've messed around with Linux in the past (Knoppix) I had recently installed Ubuntu 9.10 and found it to be pretty awesome. I loved how it worked out of the box.

My question here is when I installed 10.04 LTS the title bar buttons being on the left was insane to me. I recently saw a post where a screenshot was posted where it showed an option in the appearance options application to revert back to the right hand side. Is this a real thing and will it be available in the final release? That's all I want to know. If I have to continue using Ubuntu with the close button right next to the file option (which makes no logical sense) I'm going to try some other distribution.

Also, I am aware there is a way to change the title bar buttons in other ways but it messes up the aesthetics. I'm anal and I can't stand stuff looking messed up, even in the slightest.

Please don't flame me. 

Love,
Kangaroo

---

### Post by ubunterooster on 2010-04-27
[ubuntu-tweak!]("http://ubuntu-tweak.com/") is what I used :D

Edit: inflamitory remark removed towards developers

---

### Post by Calash on 2010-04-27
Also remember that not all themes have them on the left.  Some have them on the right.  They will prompt you if you want to move them to the left.

Outside of that there are several ways to move them back.  Check the development forum for more information.

---

### Post by kangarootoo on 2010-04-27
Here's the screen I am talking about:

[http://launchpadlibrarian.net/45330207/Appearance_Pref.jpg](http://launchpadlibrarian.net/45330207/Appearance_Pref.jpg)

What I want to know, is will this be an option in the final version of 10.04? I'm currently using the LTS version and there is no option like that in the appearance preferences.

---

### Post by Calash on 2010-04-27
LTS is the current version.  You are running the RC (Release Candidate).  In a couple of days that will turn into the full release.

That option shows up when you use an older theme that puts the buttons on the right, as I pointed out.  It will be in release, but it is not going to do what you think it will.  It is asking if you want the buttons to move to the left on an older theme that has them on the right.

How to get the buttons on the right has been covered in this post as well as in the development forum.  You should check there, at least until 10.04 is officially released.

---

### Post by ubunterooster on 2010-04-27
After installing ubuntu-tweak, go to applications>systemtools>ubuntu-tweak. From there go to window manger settings. under window titlebar layout uncheck custom and then check "right"
@sharky: I was teasing developers w/o being rude:"Edit: inflamitory remark removed towards developers" _was_ the inflamitory remark. Harmless and yet understood.

---

### Post by kangarootoo on 2010-04-27
Thanks you guys. I will check it out.

---

### Post by oleink on 2010-04-27
You just mean the buttons min max and close right?

---

### Post by uRock on 2010-04-27
> **ubunterooster said:**
> [ubuntu-tweak!]("http://ubuntu-tweak.com/") is what I used :D

Edit: inflamitory remark removed towards developers

How'd you get ubuntu-tweak for Lucid. All of my searches bring up Karmic as being the newest. Not that I want to change the buttons, they work great on the left for me.

---

### Post by Calash on 2010-04-27
Alternate way

Open a terminal and type gconf-editor

On the left navigate to >apps>metacity>general


The string in button_layout controls the placement.  I run with the following

```

menu:minimize,maximize,close

```

Menu on the left,buttons on the right.


ubuntu-tweak is a great app and worth the install, but if you want to use built-in options this will work for you.

---

### Post by oleink on 2010-04-27
In Terminal

Windows and Ubuntu 9.10:
gconftool-2 --type string --set /apps/metacity/general/button_layout ':minimize,maximize,close'

Ubuntu 10.04 early releases:
gconftool-2 --type string --set /apps/metacity/general/button_layout 'minimize,maximize,close:'

Mac:
gconftool-2 --type string --set /apps/metacity/general/button_layout 'close,maximize,minimize:'

---

### Post by ubunterooster on 2010-04-27
> **uRock said:**
> How'd you get ubuntu-tweak for Lucid. All of my searches bring up Karmic as being the newest. Not that I want to change the buttons, they work great on the left for me.

Add source:```
ppa:tualatrix/ppa
``` then get the ubuntu-tweak pakage via synaptic.
Edit: Why is this not here by default yet? It's very useful for many things[including installation of 64bit flash]

---

### Post by henry cow on 2010-04-27
I am a newbie, but I am having trouble understanding why programmers have to "mess with" everything.

Even when some buttons move to the left, many/most stay on the right. WTF?

Seems exactly like Microsoft changing EVERYTHING in Office 2007 so that even the simplest and most common tasks become a nightmare.

Believe me, I am all for progress and improvement, but there needs to be a reason behind change.

Can anyone explain to me why the buttons moved?

perplexed in NJ

---

### Post by ubunterooster on 2010-04-27
The target audience of ubuntu is those who used MS. Should we really be veering away from that? I don't use the buttons (prefer keystrokes) but _still_ find it distracting. I've asked that in several threads of this....still awaiting an answer...

---

### Post by Calash on 2010-04-28
> **henry cow said:**
> I am a newbie, but I am having trouble understanding why programmers have to "mess with" everything.

Even when some buttons move to the left, many/most stay on the right. WTF?

Seems exactly like Microsoft changing EVERYTHING in Office 2007 so that even the simplest and most common tasks become a nightmare.

Believe me, I am all for progress and improvement, but there needs to be a reason behind change.

Can anyone explain to me why the buttons moved?

perplexed in NJ

Progress cannot be made by standing still.  It was a development decision that they believe, down the road, will provide a benefit to us as users.  Apparently they have some plans for this change.  Personally I am curious as to what they are.

---

### Post by waynefoutz on 2010-04-28
> **henry cow said:**
> I am a newbie, but I am having trouble understanding why programmers have to "mess with" everything.

Even when some buttons move to the left, many/most stay on the right. WTF?

Seems exactly like Microsoft changing EVERYTHING in Office 2007 so that even the simplest and most common tasks become a nightmare.

Believe me, I am all for progress and improvement, but there needs to be a reason behind change.

Can anyone explain to me why the buttons moved?

perplexed in NJ


I think it was a dumb decision as well. When I oput Ubuntu on a Windows user's computer, I try and make things look as familiar as I can. This just adds an extra step. It's easy enough to fix with the gconftool commands oleink posted above, but still, why? I don't know. They just want to try and be different I guess. It's just another reason why I think Linux Mint is and will remain a better Ubuntu version for newbies, especially those migrating from Windows. They plan on keeping them to the right.

---

### Post by jvc26 on 2010-04-28
A few people have commented on this from Ubuntu central command ;)

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633)

Was the bugthread on launchpad - big name comments are listed at the first post.

J

---

### Post by uRock on 2010-04-28
I don't understand why people think that all Windows users are only capable of using buttons on the right. If they aren't up for change, then people shouldn't be forcing ubuntu on them. It is a weak argument.

If you say that you use Windows all day at work then come home and fire up your system and that you are thrown off by the button location, then you have a decent argument.

If you want them on the right, then just put them there. At least you have that option.

---

### Post by louieb on 2010-04-28
lol - Mark Shuttleworth - Ubuntu benevolent dictator for life - move from being CEO to the development side. This guy paid the Russians to shoot him into outer space. -  Moving the min,max,close buttons to the left  - just his way of letting us know - Ubuntu is going to try new ways out. 

Sometime for the better - new theme colors - GRUB2 - sometimes not. But Ubuntu is not going to stand still. - Hold on - it will be an interesting ride.

---

### Post by uRock on 2010-04-28
> **oleink said:**
> So to all of you who are ******* and keep saying  "well if they don't wanna switch just because the buttons changed" shut  up!

When I came to ubuntu, I was expecting something different. If someone is coming to Linux expecting Windows they will end up making a u-turn anyway. I wonder how many people bought a Mac and returned it because they couldn't get used to the change with the buttons in a different place.

---

### Post by oleink on 2010-04-28
> **uRock said:**
> When I came to ubuntu, I was expecting something different. If someone is coming to Linux expecting Windows they will end up making a u-turn anyway. I wonder how many people bought a Mac and returned it because they couldn't get used to the change with the buttons in a different place.

It's not that its just that linux already takes getting used to. A few of my friends already don't like ubuntu because of the changes.  They say they're used to windows.  and I already addressed your comment about why it would cause people not to switch it has nothing to do with expecting windows or not.  It has everything to do with already getting used to pretty much every other thing that is linux related it takes time.  And you're very foolish to believe it isn't so.

and now the post was removed which is why I'm getting a password cracker

---

### Post by alvevind on 2010-04-28
Here is a mouse-click only solution to revert the buttons to the right:

1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select value "Ambiance"
5. Select tab "Window border" and select value "Ambiance"
6. Select tab "Icons" and scroll down and select value "Ubuntu-mono-dark"

The result is the default "Ambiance" theme but with the buttons on the right side where they always have been.
:)

ALTERNATIVE SOLUTION:

1. Download modified theme from [http://people.ubuntu.com/~dylanmccal...e-Right.tar.gz](http://people.ubuntu.com/~dylanmccal...e-Right.tar.gz)
2. System > Preferences > Appearance
3. Click the button "Install"
4. Open folder "Downloads"
5. Select file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"


(From: [http://ubuntuforums.org/showthread.php?t=1464709](http://ubuntuforums.org/showthread.php?t=1464709) )

---

### Post by uRock on 2010-04-28
> **oleink said:**
> and now the post was removed which is why I'm getting a password cracker
And what will that do for you here?

---

### Post by lisati on 2010-04-28
> **uRock said:**
> And what will that do for you here?

Maybe get the attention of the forum staff...... :(

---

### Post by bodhi.zazen on 2010-04-28
> **oleink said:**
> and now the post was removed which is why I'm getting a password cracker

Firefox has a built in password strength tester.

Here is another online one (if you trust entering your PW into that kind of thing) :

[http://www.passwordmeter.com/](http://www.passwordmeter.com/)

---

### Post by oleink on 2010-04-28
> **uRock said:**
> And what will that do for you here?

Thats a nonsensical question

---

### Post by waynefoutz on 2010-04-29
> **uRock said:**
> I don't understand why people think that all Windows users are only capable of using buttons on the right. If they aren't up for change, then people shouldn't be forcing ubuntu on them. It is a weak argument.

If you say that you use Windows all day at work then come home and fire up your system and that you are thrown off by the button location, then you have a decent argument.

If you want them on the right, then just put them there. At least you have that option.

Well, that may be true. But here is my situation: I've been an Ubuntu user since Gutsy Gibbon came out. I have a daughter, who is married to a fellow in the US Navy. He is stationed 2000 miles away from me, and the husband is out to see for 3 months at a time. She calls me one day frantic, her Windows install is broken, she's a typical Windows user, she knows how to use a functioning computer, but once it's broke she's lost. Installing Windows is a nightmare, even if you know exactly what you're doing. After the install, you have to get it online, which in most cases is a challenge, and get all the correct drivers. Then you have the 2-5 hour process of downloading and installing all the updates, which is where most novices mess up. They don't get all the updates, and lo and behold, a week later, the computer is a non functioning infected mess once again. Walking her through this process over the phone would have been a nightmare for me, and something I just don't have time for.  

So, I got her to go to a neighbor's computer, and I walked her through the process of downloading Linux Mint 8 and burning it to a cd. She then stuck it in her computer, followed the prompts, and 15-20 minutes later she had a fully functioning computer. Everything worked out of the box. I chose Mint because 1. the multimedia codecs, java, and flash are installed out of the box on a clean install, and 2. the gnome menu has been reworked so that it well, looks more like Windows. After telling her how to install and uninstall programs with Mint's version of Ubuntu Software Center, she's happily chugging along nicely, I haven't gotten one question from her about the computer in the last three months. I asked her about a week ago how it was working out for her, she loves it. I didn't "force it on her." Well maybe I did, but it worked out great, and the fact that Mint  somewhat resembles Windows helped out a lot. Yeah I know KDE is out there, but I find it a lot harder for novices to use than gnome.

---

### Post by oleink on 2010-04-29
> **waynefoutz said:**
> Well, that may be true. But here is my situation: I've been an Ubuntu user since Gutsy Gibbon came out. I have a daughter, who is married to a fellow in the US Navy. He is stationed 2000 miles away from me, and the husband is out to see for 3 months at a time. She calls me one day frantic, her Windows install is broken, she's a typical Windows user, she knows how to use a functioning computer, but once it's broke she's lost. Installing Windows is a nightmare, even if you know exactly what you're doing. After the install, you have to get it online, which in most cases is a challenge, and get all the correct drivers. Then you have the 2-5 hour process of downloading and installing all the updates, which is where most novices mess up. They don't get all the updates, and lo and behold, a week later, the computer is a non functioning infected mess once again. Walking her through this process over the phone would have been a nightmare for me, and something I just don't have time for.  

So, I got her to go to a neighbor's computer, and I walked her through the process of downloading Linux Mint 8 and burning it to a cd. She then stuck it in her computer, followed the prompts, and 15-20 minutes later she had a fully functioning computer. Everything worked out of the box. I chose Mint because 1. the multimedia codecs, java, and flash are installed out of the box on a clean install, and 2. the gnome menu has been reworked so that it well, looks more like Windows. After telling her how to install and uninstall programs with Mint's version of Ubuntu Software Center, she's happily chugging along nicely, I haven't gotten one question from her about the computer in the last three months. I asked her about a week ago how it was working out for her, she loves it. I didn't "force it on her." Well maybe I did, but it worked out great, and the fact that Mint  somewhat resembles Windows helped out a lot. Yeah I know KDE is out there, but I find it a lot harder for novices to use than gnome.

That is exactly what I was getting at.  Thank you that is a much better way to put it than I did which is why my post got removed:popcorn:

---

