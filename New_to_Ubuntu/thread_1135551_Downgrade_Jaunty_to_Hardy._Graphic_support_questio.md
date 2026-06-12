---
title: "Downgrade Jaunty to Hardy. Graphic support questions for the future."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Mortus Pryde on 2009-04-24
Alright tried Jaunty but my graphics subsystem (ATI Radeon Mobility 9600 RV350/M10) on my IBM Thinkpad T42 is no longer supported under the proprietary or restricted drivers. I tried tweaking the open source drivers but could not get more than a few frames per second out of OpenLife which requires a fair amount of OpenGL performance that I was able to reasonably achieve with the Catalyst 9.3 drivers on Intrepid. All graphics tweaks are done in xorg.conf right? There is no where else?

So... Baring a revelation on tweaking the open source drivers to get me in the 20ish frames a second on low range (Now at 1.5 to 3) in Jaunty. I will be downgrading to Hardy (Unless I can still run Intrepid?) so that I can continue to use the proprietary drivers till the open source ones can catch up or exceed the proprietary ones. 

On that note, looking forward to the end of support for Hardy, how often is support for older cards dropped from the open source drivers? Am I likely to find by the end of Hardy support there will be no 3D Graphics support for my laptop?

This will really determine the roadmap for my laptop as really my goals are simple, internet use, playing MP3s, and reasonably functionallity on OpenLife with for me 20ish frames a second is adiquite. My hope is that the roadmap will lead from Hardy to 10.10 and beyond, however I fear it may lead from Hardy back to XP where I actually get better graphics performance but would prefer to run Linux as I have liked what I have seen from it.

As a thought I should add that OpenLife is a third party alternative virtual world grid to the origional and better known SecondLife.

---

### Post by cmnorton on 2009-04-26
As a general rule, I wait a while before upgrading. 8.04 would not run properly on my T61p, but the July interim releases installed fine. I would look on ThinkWiki, and also post this as a bug on launchpad.

---

### Post by Mark Phelps on 2009-04-27
Share a similar concern about future support in the Linux world.

I have a tablet PC that works great under Hardy, but attempting to upgrade to Intrepid or Jaunty produces the situation where the special keys on the table simply are not "seen" anymore --- xev shows no codes whatsoever.  Which means, that if I want to retain use of those keys (which I need when in tablet mode), I can NOT upgrade.  Have posted on this in the forums and received no replies that fix it.

For me, how well the tablet PC work under Windows Seven will play a large part in continuing to rely on Linux on a daily basis.  The tablet has full functionality under Vista, as it does under Hardy. Will have to see if anything is lost with a Seven upgrade.

It would be sad to have to go back to MS Windows because of lost functionality in Linux due entirely to upgrades.

---

### Post by labrekke on 2009-05-08
I share the same concern as you guys. I'm using an IBM Thinkpad T42 and one of the reasons for using Ubuntu 8.10 on it was - of course - that it worked! After upgrading to 9.04 I have disappointing graphics and it ruins the whole Ubuntu experience for me. :(

It would be really nice if someone from Ubuntu (or ATI) could confirm whether support for my graphics card will be continued in the future or not. I will have to consider re-installing 8.10 again or evaluate other OS'es if it won't be supported. That would be sad since I've grown to love Ubuntu and have recommended it to my friends... :o

---

### Post by oldrocker99 on 2009-05-08
I have a Toshiba L305d-S5895 I bought 5 months ago. Now I have found that ATI will no longer support the X1200 chip in my laptop. And, 9.04 does NOT support ATI's fglrx drivers.

I went back to good old Intrepid, and, using the ATI 9.01 drivers (the last ones that support my chip), I have nice OpenGL and compiz works great. I can't believe that the new Xorg version doesn't support so many Linux users.

I also know that I'll never buy a machine that doesn't have nVidia graphics.

:guitar:

---

### Post by connorh123 on 2009-05-08
I'm using an IBM Thinkpad with an ATI Radeon 7500. Everything seems to be fine.
What's wrong with yours?

---

### Post by labrekke on 2009-05-08
It works (I'm using 9.04 right now), but the graphics are not as good as they were in 8.10. Right after the upgrade to 9.04 from 8.10 I was thinking that it was just something I imagined, but after using my laptop for a few hours pictures and craphics clearly don't look as good as before, they seem to have a lower resolution.

I've read somewhere that the open source drivers might support my ATI card in 9.10, but I'm not sure I can wait so long... Maybe others with the same problem should post here as well to express their feelings. It would be interesting to see if this is a problem for many of us or just a small group that can (should) be neglected. ;)

I actually also have 8,10 on an older T41 and on that one graphcis look better. I first noticed the problem running Spotify on my T42, and the album covers suddently didn't look as good as before. :o

---

### Post by connorh123 on 2009-05-08
I also read that ATI is going out, and has been having graphics problems for some time now.

---

### Post by Zoowey on 2009-05-09
> **connorh123 said:**
> I also read that ATI is going out, and has been having graphics problems for some time now.

ATI isn't having any graphics issues. The problem is their new 9.4 driver doesn't support many of the older graphics cards. Usually a graphics card is supported officially by ATI for 3-4 years, after that they usually cut driver support. If they didn't you'd have a 900mb driver download. It's recommended you just stick with the old drivers, however 9.04 includes the new driver which has caused many problems for older computers/graphics cards.

---

### Post by kWahab on 2009-05-09
Same Dilemma. 
I have a Dell Inspiron 6400/E1505 with ATI X1400 (R5xx/M54). Upgraded to Jaunty and cannot use the Proprietary fglrx drivers as the catalyst9.3 is incompatible with the xorg server 1.6 (included with jaunty) and the newer catalyst9.4 which is compatible with xorg1.6 doesn't support my slightly older graphics card.

So now I'm using the open source radeonhd driver. Compiz works perfectly fine (after a few tweaks) but video playback shows tearing, Google Earth doesn't work and dual displays don't work very good. 

I'm thinking of downgrading to intrepid, but this really sucks that I cannot use the latest ubuntu version. 

I've followed every release since 6.10 but now I'm uncertain of the future.

---

### Post by pieguy on 2009-05-21
Yes, but HOW do you downgrade to ibex or hardy?  Jaunty is unacceptable because its performance has DIMINISHED not improved.

otherwise, I'm going to have to install fresh with ibex.

---

### Post by Mortus Pryde on 2009-05-22
For me it was easy as a clean reinstall. Jaunty flies on my tower, but yes falls well short on my lappy due to lacking and/or bugs in the open source support for ATI graphics.

---

### Post by benevolent on 2009-05-27
Hello there,

Another ati user here (x1650pro -- Desktop PC). I upgraded to jaunty as well, and 3D support isn't available of course... I am currently using the open source drivers. Compiz is working fine. GoogleEarth also is working without problems.. On the other hand, matlab's benchmark is low, cause on 2d and 3d my card (drivers actually) is weak, and diablo2 with wine isn't running smoothly (that means it isn't playable).


So, what shall we (non supported ati users) do? Is ati going to support us? Or damn my choice for saving 20euros and not buying nvidia :P

cheers =)

---

### Post by anthony_barker on 2009-05-31
Same problem on a IBM T42 - there is a work around where you edit your config files.

lspci | grep -i radeon
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

Found a partial solution here
[http://ubuntuforums.org/showthread.php?t=1108844&page=2](http://ubuntuforums.org/showthread.php?t=1108844&page=2)

and the bug report here
[https://bugs.launchpad.net/ubuntu/+s...ti/+bug/363238](https://bugs.launchpad.net/ubuntu/+s...ti/+bug/363238)

---

### Post by SunnyRabbiera on 2009-05-31
Well its not just ATI, my intel card seems to bev loosing out.
Pretty soon I probably wont be able to run desktop effects anymore.
Its not a terrible loss, after all if the computer still works then use it.
But it does kind of suck that effects dont work anymore for older cards, but that seems to happen eventually anyway no matter the OS.

---

### Post by jperakis on 2009-08-14
I found a solution that works for me, you may want to try this too!
I have a ThinkPad T42 running Ubuntu 9.04 - the Jaunty Jackalope - released in April 2009.
                
While Searching for the same problem on the forum, I have already found one setting that you can carefully try the following (NB: editing configuration files might corrupt your machine, if you have never done it, ask someone to help you!):

Add [INDENT]Option "MigrationHeuristic" "greedy"
[/INDENT]to  the Device section of /etc/X11/xorg.conf

This already gave me faster display without turning on the Visual Effects.

then I found additional settings at [http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

They worked great for me... better display quality and faster, I have even been able to turn on the full Visual Effects without impacting performance.

---

### Post by slakkie on 2009-08-14
To the actual question:

Downgrading is, while doable, not advised. You will see a whole lot of issues, which will consume time to fix and restore.

There are documents on the wiki which describe the process:
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

YMMV

---

