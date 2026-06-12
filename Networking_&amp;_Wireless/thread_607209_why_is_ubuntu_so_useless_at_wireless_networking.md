---
title: "why is ubuntu so useless at wireless networking?"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by madjack on 2007-11-08
why, I'm finding it hard to believe that vista is better at basic stuff than ubuntu, since vista is so bad, but looks like it actually is.

---

### Post by stvmty on 2007-11-08
[http://www.bash.org/?152037](http://www.bash.org/?152037)

so, what's your trouble?

---

### Post by Sef on 2007-11-08
> why is ubuntu so useless at wireless networking?

Companies don't release GNU/Linux drivers for their products.   Sometimes the drivers can be reverse enginereed, if the company has not released them.  The only reason why it works in Vista is the company has released drivers for it.

---

### Post by madjack on 2007-11-08
:) exactly. 

Can't get network manager to work, and there's no documentation about it. In fact it's very frustrating because any search you do on network manager comes back with how wonderfull it is, but not how to actually run it. Anyway, I found out how to run it from this forum, and lo and behold, it doesn't work. Therefore ubuntu is crap at wireless networking.

It's typical with linux - I really beleaved all the hype about ubunto - but After the first five minutes, you can easily see it's not ready for prime time.

---

### Post by tashmooclam on 2007-11-08
Change your wireless card to Intel. Find it at Ebay. Intel firmware and drivers for its wireless cards is already in ubuntu 7.1 
If you are lucky, the wireless card can be accessed on the back of your laptop. 
If it's under the keyboard, maybe it's tricky to change it.
I changed to an Intel card for $24. I changed it in 10 minutes. 
Just remember to turn it ON. The brand new card must be turned on. My laptop has a key.

---

### Post by madjack on 2007-11-08
I have  lenovo t61 and it has an intel 4965AGN wireless card, so It should work I think. And anyway, that kind of proves my point about ubuntu not being ready for mainstream if you have to change your network card  on a mainstream laptop - who wants to do that ?

---

### Post by itsbradman on 2007-11-08
Run networkmanager  from terminal and post the output here so someone can help you.  Simply saying it doesn't work doesn't help anyone!

---

### Post by madjack on 2007-11-08
There is no output. I can't cut and paste it since the internet is not working on that computer, so I'll type it in for you:

chris@house-laptop:~$ nm-applet --sm-disable


that's it - it doesn't return, doesn't produce any output and there is no gui.

---

### Post by mpierce on 2007-11-08
Well, madjack - others and I have answered this previously. Do a search on posts under my name, mpierce and you'll find the answer as to how to configure your wireless card so it will work.

You have to tell the card some info:
   wireless-mode managed
   wireless-essid <name of router>
     and of course, you have to give it your WEP wireless-key
   wireless-key xxxxxxxxxxx

You then restart your network. 

Hope this helps...

---

### Post by SpiritIsReality on 2007-11-08
howdy
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)
[http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ndiswrapper&btnG=Google+Search&meta=)
hope'n all the best
trails

---

### Post by nu2lnx on 2007-11-08
Two nights ago I dumped a CentOS install I was working with on my laptop for two weeks.  I installed Ubuntu Gutsy Gibbon and, with the assistance of my XP laptop, was able to hunt around for the info I needed to get my BCM4306 card to work.  All things considered, it took me about 6 hours from starting the download to connecting to the internet.  This is my third post to the forums.  

I got into Linux recently because I wanted to learn a little about the family of OS's that the majority of the internet is served with.  I wanted to learn about networking from the ground level up.  I wanted to be able to configure my machine to do exactly what I want without the overhead that MS products require.  Most importantly, I wanted to be able to UNDERSTAND what my machine was doing and why.  

I do have advice - decide why you are looking into Linux.  Ubuntu is one of the most user friendly distros I have come across.  

I recommend patience and advise that you look at getting it running the way you want it to as a worthy educational goal.

Ubuntu doesn't "suck".  In fact, when you consider that few drivers are available for Linux I think it is pretty impressive, damn near amazing, that any of them are working at all, let alone the monstrosity I have in my machine.  Hang in there and listen to what these people have to say...

---

### Post by gilf on 2007-11-08
I keep trying to tell people this:

The biggest problem with wireless networking in Ubuntu is simply that the interface is non -intuitive. Therefore people don't know how to use it to connect.

No, you don't have to enter the ESSID normally. It is picked up automatically by NetworkManager and presented to you as a choice.

Try this (as I've said before):

Boot from the LiveCD (so any changes you've entered don't affect things).

Click on the NetworkManager icon in the taskbar in the upper right portion of the screen.

If you are near a wireless router, it should show you the Essid of that router with a bar graph.

Click on that bar graph essid line. It will open up a dialog asking for the WPA password if you use one.

That's all there is to it.

The biggest problem is that people don't relize that clicking on a signal strength bar graph opens up the WPA dialog -- or connects them if they don't need wWPA, automatically.

The bargraph is a non intuitive aspect of the program.

Now, if that doesn't work from the LiveCD then you do have a card recognition problem or you aren't near a router.

See my other posts if you are able to get access on the LiveCD, but not on your installed version of Ubuntu.

Hope this helps.

---

### Post by madjack on 2007-11-09
Great, thanks - at last I've found the network manager. That's all I was really asking, (how do you run the network manager). It's not at all intuitive, there is no reference anywhere on the desktop to "network manager" - when I click on about it says it is called "nm-applet".

So most of the problem here is that all of the help and advice starts off with "in the network manager, click on ..."), and none of it says - "to run on network manager, click on the icon in the top right of the screen which has two computers, one behind the other". 

I found the network manager on my work laptop anyway, I'll see if it's there on my home laptop when I get home, I don't remember seeing that icon, I think I checked all the icons, so for some reason it's missing. I think I'll do a new install and start again.

ubuntu should be better than this - I shouldn't be having these problems - I'm not a linux newbie either, I've been using linux at work and home for years.

thanks for all your help everyone, and credit to you all, no one's shouted at me yet, which was what I was expecting!

> **gilf said:**
> I keep trying to tell people this:

The biggest problem with wireless networking in Ubuntu is simply that the interface is non -intuitive. Therefore people don't know how to use it to connect.

No, you don't have to enter the ESSID normally. It is picked up automatically by NetworkManager and presented to you as a choice.

Try this (as I've said before):

Boot from the LiveCD (so any changes you've entered don't affect things).

Click on the NetworkManager icon in the taskbar in the upper right portion of the screen.

If you are near a wireless router, it should show you the Essid of that router with a bar graph.

Click on that bar graph essid line. It will open up a dialog asking for the WPA password if you use one.

That's all there is to it.

The biggest problem is that people don't relize that clicking on a signal strength bar graph opens up the WPA dialog -- or connects them if they don't need wWPA, automatically.

The bargraph is a non intuitive aspect of the program.

Now, if that doesn't work from the LiveCD then you do have a card recognition problem or you aren't near a router.

See my other posts if you are able to get access on the LiveCD, but not on your installed version of Ubuntu.

Hope this helps.

---

### Post by jfairy on 2007-11-09
Much sympathy Madjack, Ive been having the same kind of drama's, now solved with a new pcmcia card for the lappy (one that is supported 'out of the box' yay!)
I agree with gilf, its not terribly intuitive or obvious, but then again millions of dollars havent been spent on 'perfecting' the distro like some (ahem) other OS's. 
I put my new D-Link G-650 in earlier this week, had it working within 5 minutes of chucking it in (& Im not a linux geek, yet anyways), it pretty much did it itself, then a few days later nothing. No connection, I had no idea how to fix so I did a nuke & pave (ie reinstall). Pain in the **** but there you go, did that today & its all sweet again (hopefully I will not do the thing I did before to make it unwork, if I can only figure out what that was). 
Ah the vagaries of learning a new language (viva diversity!)

---

### Post by nu2lnx on 2007-11-10
"nuke and pave"...

I like that...

---

### Post by ElEdwards on 2007-11-10
Forwhat it's worth.....

With both Fiesty and Gutsy, my wireless card worked without any intervention on my part :)  It's a Linksys card..... and this same card gave me FITS in WinXP.

With the myriad of hardware combinations that programmers have to try and hit, it shouldn't be surprising that some of us will have a combination that takes some massaging to make it work :)

---

