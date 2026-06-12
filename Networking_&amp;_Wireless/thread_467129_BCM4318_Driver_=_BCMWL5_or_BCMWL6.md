---
title: "BCM4318 Driver = BCMWL5 or BCMWL6?"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by plinydogg on 2007-06-07
Hi everyone,

All those who talk about using ndiswrapper with a Broadcom BCM4318 wireless card keep referring to the Windows driver as being BCMWL5 (.sys, .bin, and .inf). But on my Vista machine, the driver for the card is BCMWL6, and there is only the .sys file, not the .bin or .inf. 

Am I missing something? Will ndiswrapper work with only BCMWL6.sys?

Thanks!

---

### Post by esavato on 2007-06-07
If you were able to locate the driver on Vista, then use it.  Most of the howto's suggest downloading a "stock" l5 from one of the 4318 airforce pages.  I guess this ensures that it has a better chance of working if everyone has the same driver, however, it sounds like since you have newer hardware, you should just use the driver on your system that is known to work under windows.

---

### Post by duchovny on 2007-06-07
> **plinydogg said:**
> Hi everyone,

All those who talk about using ndiswrapper with a Broadcom BCM4318 wireless card keep referring to the Windows driver as being BCMWL5 (.sys, .bin, and .inf). But on my Vista machine, the driver for the card is BCMWL6, and there is only the .sys file, not the .bin or .inf. 

Am I missing something? Will ndiswrapper work with only BCMWL6.sys?

Thanks!

You have a Belkin wireless 54g+ card because that's what the BCMWL5 is a driver for the Belkin card... BCMWL6 is the updated driver for that card to make it Vista compliant. Ndiswrapper will work with it because I got my system to see the card and work. (originally I was using the firmware upgrade posted by DarkNoob, but it slowed my wireless connection down to 11Mb/s. Removing it and going back to ndiswrapper has my Belkin working (although the downside is Network Manager seems to take longer to connect to the network but when it connects it connects at the 125Mb/s speed that my card uses. (Although I guess all Broadcom cards use BCMWL in them, but I do know that the one with 6 in the number is for Vista. I upgraded the driver to 6 on my WinXP partition, but I must confess I'm not sure which driver Fiesty is using though).

Try here:
[http://ubuntuforums.org/showthread.php?p=2749951](http://ubuntuforums.org/showthread.php?p=2749951)

use the program listed there. It may help to install whichever driver will work.

---

### Post by RedSpade on 2007-09-20
I finally got my wireless working with Feisty using NDISWrapper and the BCMWL5 driver on a dual boot Vista/Feisty set up.  A week later while on the Windows side I was notified that there was a new driver available.  Knowing I had a dual boot situation I thought WTH let it install the update.  The driver install went into Vista with no problem.  An hour later I boot into Feisty and ..... my wireless was no longer working.   I've been working with Linux for a couple of years, but I'm very new to wireless.  Does anyone have any ideas on how to approach this.

This is also my first posting.  Please excuse me if I error in my protocol.

Thanks to all.  Youse guys/gals are awesome.

---

### Post by drumsandwires on 2007-11-01
> **plinydogg said:**
> Hi everyone,

All those who talk about using ndiswrapper with a Broadcom BCM4318 wireless card keep referring to the Windows driver as being BCMWL5 (.sys, .bin, and .inf). But on my Vista machine, the driver for the card is BCMWL6, and there is only the .sys file, not the .bin or .inf. 

Am I missing something? Will ndiswrapper work with only BCMWL6.sys?

Thanks!

I am having the exact same problem.  I have been running in circles following threads that all assume that you have an .INF file.  Meanwhile BCMWL6.sys sits on my computer mocking me.

Did you ever figure this out?

---

### Post by plinydogg on 2007-11-01
I did eventually get it working in Feisty but I don't remember how. I wrote it down so when I get home I can post back here and give you the exact procedure.

However, none of this was necessary in Gutsy. Are you using Gutsy or Feisty?

---

### Post by Ayuthia on 2007-11-01
> **drumsandwires said:**
> I am having the exact same problem.  I have been running in circles following threads that all assume that you have an .INF file.  Meanwhile BCMWL6.sys sits on my computer mocking me.

Did you ever figure this out?
According the the NDISwrapper website, Vista drivers (bcmwl6) are not supported as of yet.  So if you want to use NDISwrapper, you will need to find a bcmwl5 driver.

---

### Post by plinydogg on 2007-11-01
Did you get it working? If not, let me know what version of Ubuntu you use...

---

### Post by kevdog on 2007-11-01
As stated ndiswrapper does not work yet with Vista drivers so you will have to stay with bcmwl5.

---

### Post by plinydogg on 2007-11-02
But if you're using Gutsy, then you shouldn't need to manually configure anything (not really, anyway)

---

### Post by kevdog on 2007-11-02
> But if you're using Gutsy, then you shouldn't need to manually configure anything (not really, anyway)

Where did you get that impression?? This assumption would be FALSE.  Its not really a whole lot different than Feisty.

---

### Post by plinydogg on 2007-11-03
Ummm...I got that fact from not having to manually configure much in Gutsy...that's where. All I did was (1) enable the driver using the Restricted Drivers Manager; (2) uninstall Network Manager; and (3) Install WICD. 

So, it's not an "impression" or an "assumption." It's my experience, and it's not FALSE either. But way to be a jerk about it...

---

### Post by kevdog on 2007-11-03
Just keep using your system with the restricted drivers -- you will see what I mean.  And btw, was it about 3-4 months ago that I helped you get your wireless up and running after about 30 posts back and forth??? Way to say thanks!! Way to be a jerk about it!

---

### Post by RedSpade on 2007-11-03
Can someone explain to me what happened in my situation?  Dual boot Feisty/Vista on an HP Pavillion DV2210U.  I copied the windows drivers over to my home directory on Feisty and everything worked great.  Then the updated driver notice from HP came via email and I figured I could update only on the windows side, which I did and the windows side worked great (it was an automated package install).  But the first time I booted into Feisty after the driver change I couldn't connect to the wireless. ??? Separate drive files, separate systems (?), I thought I should be OK.  This makes no logical sense to me.  Could HP have sent a firmware update/upgrade with the new driver that it installed?  I can't use the older BCMWL5 driver.  Can someone explain this to me.

---

### Post by plinydogg on 2007-11-03
Kevdog: Yes, you were one of those who generously helped me get my wireless working a few months ago, which was one of the reasons I was surprised at your change of tone when smacking my advice to the original poster down. All I was trying to do was help the original poster like you helped me. I told him/her what worked for me and then you come along and say "no, that's not right," even though what I'm saying does work. If you want to suggest a better alternative (e.g., not using the restricted drivers manager, etc.) then that's great, I'd like to hear it and I'm sure others would too, but you don't have to accuse me of being wrong just because I do things a different way. The original poster wants to get his/her wireless working and I responded with a way that I got mine working. What else should I have done?

RedSpade: I'm sorry but I have no idea what's going on with your driver issue. Perhaps someone with more knowledge (e.g., KevDog) will chime in...

---

### Post by kevdog on 2007-11-03
> But if you're using Gutsy, then you shouldn't need to manually configure anything (not really, anyway)

Is this really a true statement???  bcmwl5 is always to be used with ndiswrapper, and there is no way to install ndiswrapper as far as I know without some manual intervention.  What does bcmwl5 have to do with the restricted drivers?  bcm43xx vs bcmwl5.  The bcm43xx driver may not require any manual intervention if you have an existing internet connection to download the firmware to complete the installation, however thats not what the title of the thread asked.

---

### Post by plinydogg on 2007-11-03
Agreed, installation of ndiswrapper requires manual intervention. And yes, the initial thread asks which version of the driver is needed. But so what? The guy is trying to get his wireless to work, I'm suggesting an easier way if he uses Gutsy. What's wrong with that? That's what these forums are for: questions, answers, alternative suggestions, etc. 

So the statement you've quoted above is true. If all you're trying to do is get your wireless working, it's a simple three steps (assuming, as you point out, that you have an Internet connection) to do so,

---

### Post by plinydogg on 2007-11-03
BTW, what's wrong with the restricted drivers?

---

### Post by kevdog on 2007-11-03
There is nothing wrong with the restricted drivers per se, however if you have been reading the forums a lot of people are hanging problems with frequent disconnects (which isnt always the driver's problem) and with range problems.  Also the theoretical loss of bandwidth the driver bugs some people.  According to these posters, the reverted to ndiswrapper and all problems were solved.  I haven't yet seen the reverse situation.  

The only achilles heel in my opinion for the restricted drives is that it requires an internet connection.  For many working on laptops that might not have an ethernet connection.

---

### Post by plinydogg on 2007-11-03
Good to know. I haven't experienced any drops in connectivity except when my fiance is online using her Windows XP laptop....she always gets a good signal but sometimes mine is virtually useless until she stops using it. Interesting. 

That's a good point about a lot of people not having an Internet connection...I used to have that problem when I first installed Feisty because my ethernet wouldn't work for some reason.

---

### Post by Bucky Ball on 2008-03-03
Hey all. I am having the same problem. But I can solve one of yours, PlinyDogg.

In Vista, goto c:\SwSetup and you will find the Windows bcmwl6.inf file in there. It is confusing because if you take note, some of the other things in there are also just called bcmwl6, but if you check the list on the right, they are text documents, NOT the driver. Go for the Setup Information file (but you probably knew that).

I am thinking of using the bcmwl5 driver myself as I am noticing that the bcmwl6 doesn't seem to be supported in fwcutter or ndiswrapper. ;(

Here's hoping for a solutions - it has taken me about a week or more to get here.

---

### Post by plinydogg on 2008-03-05
Bucky Ball: Thanks for the tip, but actually, since Gutsy was released, I haven't had to do this manually anymore. All I needed to do to get the card working was (1) enable the driver in the restricted drivers manager; and (2) install WICD (and uninstall Network Manager). 

Good luck moving forward!

---

### Post by Bucky Ball on 2008-03-05
[QUOTE=plinydogg;4457482]Bucky Ball: Thanks for the tip, but actually, since Gutsy was released, I haven't had to do this manually anymore. All I needed to do to get the card working was (1) enable the driver in the restricted drivers manager; and (2) install WICD (and uninstall Network Manager). 

... and thanks for your tip, Plinydogg! I download WICD with Synaptics Pack Man? I have never heard it but I learn something new about Ubuntu/Linux everyday so today no different. :)

I have spent hours on this and looks like you might have found the key. Will try this as soon as I get home from uni tonight and let you know how I went with it all.

---

### Post by Bucky Ball on 2008-03-08
Well, spent another day screwing around with the wireless. Downloaded Wicd via the instructions on their site. All went fine but having a few problems. Works with the wired setup fine, but I think my problems are starting before that as my wireless light is red anyhow. I figure I wouldn´t know if things are working unless that light was blue in the first place.
Which leads me to think that something is not installed or ... something is installed and is getting in the way of Wicd. Any ideas? I have been scouting for hours, as usual. :/

---

### Post by Bucky Ball on 2008-03-08
... just to add to that ...

Wicd has a menu list of drivers to use. I have tried the broadcom but wondering if something else might work.

Will continue to experiment (eth1 and eth0 were the wrong way around to begin and once I swapped them the wired connection was up ... ).

---

### Post by rustybronco on 2008-03-08
> **Bucky Ball said:**
> Well, spent another day screwing around with the wireless. Any ideas? I have been scouting for hours, as usual. :/See the link in Kevdog's signature about installing ndiswrapper.

---

### Post by imdano on 2008-03-08
> **Bucky Ball said:**
> Wicd has a menu list of drivers to use. I have tried the broadcom but wondering if something else might work.You should use wext.  Typically the only time you should use something else is if you're using an old version of a driver or (maybe) madwifi.  Also, that driver is only used with wpa_supplicant when connect to an encrypted network.

---

### Post by kevdog on 2008-03-08
If you really want to use the restricted drivers (if they support the model of your Broadcom chipset -- b/c they it only supports a handful of chipset revision numbers), I would use the hardy kernel that uses the b43 drivers rather than the bcm43xx.  I hear b43 works a lot better, but have no personal experience with the matter.  For me with broadcom its ndiswrapper -- I have other cards to do such as atheros chipsets if I want to do something fancy such as aircrack.

---

### Post by Syndrone on 2008-07-01
So basically if you have the upgraded driver on your vista boot you can't connect wirelessly via Ubuntu? I don't wanna have to use Vista I would rather use Ubuntu, there has to be a way to either downgrade to the bcmwl5 driver rather than to use the 6, and if there is a way can someone explain the method I would go about doing to accomplish that? Thanks!

---

### Post by Bucky Ball on 2008-07-02
Here's the go. After screwing around with one thing and another on and off for about 6 months and being stuck with Vista for half a year of uni, during the mid year break I have upgraded to Hardy. And guess what ... the B43 driver and all else required took over with the initial updates after install and the blue light came on, wireless working fine and no problem since.

Working fine for me 'out of the box' and haven't bothered with or needed the hassle of ndiswrapper. Windows Bcmwl5 or 6 redundant.

Love 8.04 and Ubuntu is finally what my laptop calls home! Trying out MuseScore for my notation and score writing and comparing with Sibelius ... so far ... pretty good! We will get there!

If you are having troubles with this card in Gutsy, I suggest upgrading to 8.04. All the best and good luck to you all and hope this works for you.

---

### Post by Bucky Ball on 2008-07-03
Bit absent of me ... I should add that I am using a HP dv6000 laptop, amd turion 64, 2Gb RAM and the card is a Broadcom BCMWL94311. Good luck and happy sailing.
:)

---

