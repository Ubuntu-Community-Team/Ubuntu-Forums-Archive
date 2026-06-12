---
title: "Can't connect at all"
date: 2007-08-10
forum: Networking &amp; Wireless
---

### Post by Tomkin on 2007-08-10
I just installed Kubuntu Dapper Drake yesterday, and I'm having some Internet issues. (OK, you probably guessed that part.)

First, I tried to connect by a wireless network. I tried to enable the eth1 wireless but everytime I hit the Enable button it disabled itself instantly.

After some Googling around I discovered that this was a relatively common problem with bcm43xx cards that could be fixed by fwcutter. Unfortunately, I could not install it with Adept seeing as I had no wireless. I attempted to plug in a network cable, but Kubuntu gave no sign of recognizing it that I could tell.

In summary, **I cannot get internet in any way, either wired *or* wireless.**

So my question is, what the heck is wrong, and how do I fix it without Adept?

I have fwcutter and the Windows drivers on a CD, but I have no clue how to install fwcutter properly from a CD. Any help would be appreciated - thanks! EDIT: It seems that the only way to compile fwcutter from source requires Build-Essential, which you need Internet (i.e. Adept) to get. It seems rather stupid that way, since Build-Essential will primarily be used by people who had to transfer the source from another computer via CDs.

-Tomkin

---

### Post by Jamie Jackson on 2007-08-10
Well, if you decide to get a more modern version (Feisty), [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") should work...

---

### Post by Tomkin on 2007-08-10
I should mention that I'm very new to Linux, and I thought installing a less-stable version would make my life more complicated than it is already. Is this a valid concern?

Also, your method uses apt-get, which uses the internet unless I'm mistaken? Keep in mind that I don't believe my machine is connecting *at all*, either via wireless *or* network cable. If there were some way to simply install the pertinent files - I have everything on my desktop (fwcutter and the Windows drivers) ready to go, and I just need to install it!

Thanks for your help!

 - Tomkin

---

### Post by bmartin on 2007-08-11
If you can get a wired connection working, try [this thread]("http://ubuntuforums.org/showthread.php?t=405990&goto=newpost"). The program does all the work for you.

---

### Post by Tomkin on 2007-08-11
Yeah, but the problem is, I don't have wired internet, as I mentioned earlier. I'll put it in bold so it's easier to notice. :)

Thanks!

 - Tomkin

---

### Post by Jamie Jackson on 2007-08-11
I would recommend Feisty as opposed to Dapper. It's going to be harder and harder to get community support for it. Besides, Gutsy is on the horizon now....

Also, fwcutter will not give you your full bandwidth, AFAIK, whereas ndiswrapper will.

Anyway, you didn't mention which 43xx you have. If you have a *non*-BCM4318, [this particular post]("http://ubuntuforums.org/showpost.php?p=3022036&postcount=21") on [this forum thread]("http://ubuntuforums.org/showthread.php?t=475963") might give you what you need. If you have the 4318, you'll need to modify his instructions slightly for to accommodate for it (you should be able to get the drift by looking at the alternate 4318 instructions found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").

---

