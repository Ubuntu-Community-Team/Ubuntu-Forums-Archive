---
title: "Girlfriend problems"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Edge92 on 2009-01-30
Here is my problem, I just downloaded Ubuntu, and I can't wait to install it.  But my girlfriend just trashed her computer, so she is going to be using my computer until she gets a new one.  The first problem is that she is really starting to like mine.  THe up shot is that she will no longer complain about the thousands of dollars i have spent putting it togeather.  The bad thing is that she does not want me to install Ubuntu on it, she likes Windows.  Can I set it up so she can still have Windows, and I can use Ubuntu?

---

### Post by cmnorton on 2009-01-30
dual-boot it.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by diwas on 2009-01-30
Yes, you can dual boot.

---

### Post by sandyd on 2009-01-30
its called a "dual boot"

you can have two Operating Systems on one hard disk

look at guide here

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by LowSky on 2009-01-30
its called dual boot or virtual box
if you spent all that money you should know that
Personally just do a fresh install of windows on her machine, dont make a crappy compromise

---

### Post by taurus on 2009-01-30
You need to resize your harddrive, making room to install Ubuntu on it if you want to install Ubuntu on a separate partition.  Then you can edit /boot/grub/menu.lst and have it boot into windows after 3 seconds (or whatever amount of time you want) from GRUB menu so she doesn't have to do anything when she turns on the machine.

Otherwise, you can use wubi.

[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)

---

### Post by Edge92 on 2009-01-30
> **LowSky said:**
> its called dual boot or virtual box
if you spent all that money you should know that
Personally just do a fresh install of windows on her machine, dont make a crappy compromise

I know I should...I can do the hardware in my sleep, the software on the other hand I just don't get.  In fact I really struggle with it.

---

### Post by megamania on 2009-01-30
> **Edge92 said:**
> The bad thing is that she does not want me to install Ubuntu on it, she likes Windows.
It's called "explain your girlfriend that it is your computer". But wait... it's much easier to dual boot than to talk your girlfriend into it. :-)

---

### Post by DGortze380 on 2009-01-30
> **Edge92 said:**
> Here is my problem, I just downloaded Ubuntu, and I can't wait to install it.  But my girlfriend just trashed her computer, so she is going to be using my computer until she gets a new one.  The first problem is that she is really starting to like mine.  THe up shot is that she will no longer complain about the thousands of dollars i have spent putting it togeather.  The bad thing is that she does not want me to install Ubuntu on it, she likes Windows.  Can I set it up so she can still have Windows, and I can use Ubuntu?

Dual Boot...


... or ... it's your computer, tell her tough sh!t and do what you want.

---

### Post by avtolle on 2009-01-30
> **megamania said:**
> It's called "explain your girlfriend that it is your computer". But wait... it's much easier to dual boot than to talk your girlfriend into it. :-)
+1

(and maybe +infinity if the person with 2 x chromosomes is your wife as opposed to just your girlfriend. :D

---

### Post by Montblanc_Kupo on 2009-01-30
> **LowSky said:**
> its called dual boot or virtual box
if you spent all that money you should know that
Personally just do a fresh install of windows on her machine, dont make a crappy compromise

Wow... that was certainly the most needlessly pedantic, unefficacious, and insipid post I've read all day.:rolleyes:

To the original poster... you might run into problems with an already installed windows since it doesn't like to repartition nicely. The Ubuntu install will help resize and repartition... but it's not guaranteed that you won't lose data in windows. This is windows fault. 

Actually doing the dual boot isn't terribly hard though. Just make sure you have a chunk set aside for windows at the start of the disk and a chunk set aside for linux after that (well... 2-3 chunks really). Or simply add another drive. Make sure windows is installed first for ease of dual booting. Then install linux, when it asks about partitioning, use the manual option or the guided available... just don't let it use the whole disk or you'll erase windows. Once it's done installing... it will put the boot loader on the machine automatically and it will have an option for windows at the bottom of the list.

Good luck.

---

### Post by Edge92 on 2009-01-30
> **DGortze380 said:**
> Dual Boot...


... or ... it's your computer, tell her tough sh!t and do what you want.

...Yeah...A: I have decided to get Wubi, and B: I don't what to sleep on the couch with my dog for the next week...he has bad breath...

---

### Post by Montblanc_Kupo on 2009-01-30
> **avtolle said:**
> +1

(and maybe +infinity if the person with 2 x chromosomes is your wife as opposed to just your girlfriend. :D

I got lucky... My gf had already used linux before she met Me... :D

---

### Post by avtolle on 2009-01-30
Yes, you did get lucky. My late wife was a computer person, and intrigued by use of Linux; we were working on conversion of her workplace to Linux from Windows (one would think that the opportunity to save substantial money by reducing/eliminating site licenses and by not being forced into upgrade of hardware in a school setting would be powerful arguments) when she died.

---

### Post by Captain_tux on 2009-01-30
> **Edge92 said:**
> ...and B: I don't what to sleep on the couch with my dog for the next week...he has bad breath...

Bada freaking bing... you, my friend, are a smart man!

---

### Post by harshpkaria on 2009-01-30
Just install Ubuntu, and ask her to use it..... Just ask her to use it for a week. 
The next week, she will ask u to install ubuntu on her comp... Worked with my girl friend.... She will actually fall in love with the OS, but will miss those viruses, trojans, and other dozens of things on the famous OS.

---

### Post by DGortze380 on 2009-01-30
> **Edge92 said:**
> ...Yeah...A: I have decided to get Wubi, and B: I don't what to sleep on the couch with my dog for the next week...he has bad breath...

LMAO... didn't say it was smart, just said you could do it.

---

### Post by LowSky on 2009-01-30
> **Montblanc_Kupo said:**
> Wow... that was certainly the most needlessly pedantic, unefficacious, and insipid post I've read all day.:rolleyes:

+1 on using a thesaurus on insulting me :popcorn:

Thank you for the pedantic compliment, being annoyed by someone's lack of ability to self-educate is often overlooked or handicapped by people who feel that every question should just be aswered or given to them, what ever happened to hardwork? The original poster whould have gained his answer by a simple search engine queary. Now calling me unefficacious and insipid is really just repeating yourself and showing that your vocabulary to so large that you must only have conversations with rather boring people who all went to boarding schools and read a thesaurus as a fun afternoon between polo and horn lessons. 

Generely I'm a nice person and glad to help, but I am amazed that people will ask such questions that could have been found on a site like Yahoo! Answers.

---

### Post by jpoRS on 2009-01-30
> **harshpkaria said:**
> Just install Ubuntu, and ask her to use it..... Just ask her to use it for a week. 
The next week, she will ask u to install ubuntu on her comp... Worked with my girl friend.... She will actually fall in love with the OS, but will miss those viruses, trojans, and other dozens of things on the famous OS.

+1 for that.  Talked my girlfriend into Ubuntu a few months ago and it has done wonders for our relationship.  Yeah, thats right, computer geekdom is helping my love life.  She no longer has to ask me to fix her computer because she got a virus/crashed it/installed Bonzi Buddy*, and she has a computer that works.  Win-win, right?

Good luck,
jim

*Ok, that part was a joke.  I would not affiliate with anyone that dumb.

---

### Post by hyperhopper on 2009-01-30
this topic is amazing *bookmarked*

> **megamania said:**
> It's called "explain your girlfriend that it is your computer". But wait... it's much easier to dual boot than to talk your girlfriend into it. :-)

just tell her use her own comp!


> **Edge92 said:**
> ...Yeah...A: I have decided to get Wubi, and B: I don't what to sleep on the couch with my dog for the next week...he has bad breath...

why would you have to sleep on the couch? i dont get it!

---

### Post by crjackson on 2009-01-30
I've got a wife and 6 kids using 12 machines in my house. They all would rather have windows if asked(they can't figure out how to infect and destroy Ubuntu and ruin my weekends).

I have Ubuntu on every machine (except my wife's shool laptop - MS Wares required for some classes).

My life has been much easier and complaints about not having windows fall into a black hole.

If my wife doesn't want to sleep in the same bed or room with me, she can enjoy one of the nice sophas in either the living room, den, or lounge.

That said, when she needs to get some real work done, she normally uses a Ubuntu machine and has recently asked me to put a dual boot setup on her laptop.

---

### Post by Casper Hansen on 2009-01-30
Nerds and girl friends lol.

- Well, is there a reason why she wouldn't use Ubuntu?

---

### Post by hyperhopper on 2009-01-30
WHAT IS WITH ALL YOU PEOPLE TALKING ABOUT SLEEPING ON COUCHES?

I dont get it.  3 references to this so far. Can anybody tell me what is going on?

---

### Post by crjackson on 2009-01-30
> **hyperhopper said:**
> WHAT IS WITH ALL YOU PEOPLE TALKING ABOUT SLEEPING ON COUCHES?

I dont get it.  3 references to this so far. Can anybody tell me what is going on?

If you really DON'T get the drift (which I doubt), then there's no point in telling you.

---

### Post by hyperhopper on 2009-01-30
why is there no point in telling me?

i have every right to know.

*makesconspiracytheory*

---

### Post by teh_yodeler on 2009-01-30
hyperhopper.... One would sleep on the couch because one would not be allowed in bed with the woman.

Basically it means that you're in trouble, so you have to sleep by yourself (or with the dog).

Now if you still don't get it, just give up! lol

---

### Post by lykwydchykyn on 2009-01-30
Install Ubuntu.  Delete windows.

If she is cool with that, she's the one.  

If not, it's over.

There is no better litmus test.

---

### Post by Captain_tux on 2009-01-30
> **LowSky said:**
> +1 on using a thesaurus on insulting me :popcorn:

Thank you for the pedantic compliment, being annoyed by someone's lack of ability to self-educate is often overlooked or handicapped by people who feel that every question should just be aswered or given to them, what ever happened to hardwork? The original poster whould have gained his answer by a simple search engine queary. Now calling me unefficacious and insipid is really just repeating yourself and showing that your vocabulary to so large that you must only have conversations with rather boring people who all went to boarding schools and read a thesaurus as a fun afternoon between polo and horn lessons. 

Generely I'm a nice person and glad to help, but I am amazed that people will ask such questions that could have been found on a site like Yahoo! Answers.

Oh, how I know what you mean!

[http://ubuntuforums.org/showthread.php?t=1050283](http://ubuntuforums.org/showthread.php?t=1050283)

---

### Post by linuxisevolution on 2009-01-30
> **avtolle said:**
> Yes, you did get lucky. My late wife was a computer person, and intrigued by use of Linux; we were working on conversion of her workplace to Linux from Windows (one would think that the opportunity to save substantial money by reducing/eliminating site licenses and by not being forced into upgrade of hardware in a school setting would be powerful arguments) when she died.

That's very sad :(

---

### Post by Gulyan on 2009-01-30
> **lykwydchykyn said:**
> Install Ubuntu.  Delete windows.

If she is cool with that, she's the one.  

If not, it's over.

There is no better litmus test.

You got that right :popcorn:

---

### Post by Revenged on 2009-01-30
> **lykwydchykyn said:**
> Install Ubuntu.  Delete windows.

If she is cool with that, she's the one.  

If not, it's over.

There is no better litmus test.

This is a wonderful point, and a great idea.

Hope you like the couch, :P

---

### Post by Captain_tux on 2009-01-30
> **linuxisevolution said:**
> That's very sad :(

It is indeed sad... but unfortunately an all too common occurrence. And often times it isn't for a perceived lack of functionality and usability, but rather by the familiarity the common computer user has with Windows.

---

### Post by albinootje on 2009-01-30
> **Revenged said:**
> This is a wonderful point, and a great idea.

Hope you like the couch, :P

I would rather use the alternative of going into space with her and Mr.Shuttleworth, Father Gnome, Orbit and Nautilus Jr., and see what she thinks about Ubuntu after getting back to ... earth!

---

### Post by andrew.mckevitt on 2009-01-30
I managed to solve the same problem by buying my g/friend a macbook. Got my pc back and lots of sex too.:D

---

### Post by Casper Hansen on 2009-01-30
> **andrew.mckevitt said:**
> I managed to solve the same problem by buying my g/friend a macbook. Got my pc back and lots of sex too.:D

At least you got sex...

---

### Post by linux6994 on 2009-01-30
Wait I have the answer! Send her here and she will not need to use your computer.

---

### Post by andrew.mckevitt on 2009-01-30
> **Casper Hansen said:**
> At least you got sex...

It's a real chore, but worth it to get my pc back

---

### Post by dj722000 on 2009-01-30
Ahhh man, never ask just do. Shouldn't of even told her. I thought my wife was gonna get bent when I dual booted UBUNTU on our machine. She came home and I was in playing around and she was like what the hell is that. I'm like its UBUNTU. She was like WHAT?? Yeah me too at first, then I showed her around, showed her how to play and install games. Now she gets miffed if I go back into WINDOWS. It's funny. Just do it or go and kick her comp. 

Just imagine what it will be like if "you" get married. WOW.

---

### Post by theozzlives on 2009-01-30
Just insert the CD with Windows running, and install it under Windows (WUBI)

---

### Post by Captain Legless on 2009-01-30
Explain to your girlfriend that UBUNTU is like a condom - keeps you safe and free from virus, (virusus, virii), and other unwanted surprises, whilst still allowing you to have maximum pleasure.

Windows is like a hooker where you're paying out an exorbitant amount of money to line someone else's pocket and you never know what you might get!!

I'm sure she'll understand. ):P

---

### Post by andrew.mckevitt on 2009-01-30
[QUOTE=dj722000;6647901]Ahhh man, never ask just do. Shouldn't of even told her. I thought my wife was gonna get bent when I dual booted UBUNTU on our machine. She came home and I was in playing around and she was like what the hell is that. I'm like its UBUNTU. She was like WHAT?? Yeah me too at first, then I showed her around, showed her how to play and install games. Now she gets miffed if I go back into WINDOWS. It's funny. Just do it or go and kick her comp. 

Sounds like she's into *nix more than you, sorry dude, your missus is way cooler than you, like!

---

### Post by kaptengu on 2009-01-30
dual-girlfriend

---

### Post by albinootje on 2009-01-30
This thread isn't getting very women friendly is my impression.
But to throw in an alternative for the condom comparison, here's a quote from Linus “My name is Linus, and I am your God.” Torvalds :

“Software is like sex: it's better when it's free.”

[http://en.wikiquote.org/wiki/Linus_Torvalds](http://en.wikiquote.org/wiki/Linus_Torvalds)

And, another alternative, some time ago i showed a very-MS-windows-minded colleague the Steve B. monkey dance. 
[http://video.google.com/videoplay?docid=-4860483760049380308](http://video.google.com/videoplay?docid=-4860483760049380308)
[http://www.ntk.net/ballmer/mirrors.html](http://www.ntk.net/ballmer/mirrors.html)
She said she was horrified by that video.

---

### Post by lykwydchykyn on 2009-01-30
> **Revenged said:**
> This is a wonderful point, and a great idea.

Hope you like the couch, :P

Nine years, four children, and six linux boxes later, she's still the one. :-)

---

### Post by Ducatiboy Stu on 2009-01-30
You could always set up KDE to like like windows...

---

### Post by anewguy on 2009-01-30
> **LowSky said:**
> +1 on using a thesaurus on insulting me :popcorn:

Thank you for the pedantic compliment, being annoyed by someone's lack of ability to self-educate is often overlooked or handicapped by people who feel that every question should just be aswered or given to them, what ever happened to hardwork? The original poster whould have gained his answer by a simple search engine queary. Now calling me unefficacious and insipid is really just repeating yourself and showing that your vocabulary to so large that you must only have conversations with rather boring people who all went to boarding schools and read a thesaurus as a fun afternoon between polo and horn lessons. 

Generely I'm a nice person and glad to help, but I am amazed that people will ask such questions that could have been found on a site like Yahoo! Answers.

Well, to scipt the lingo and go to something more basic, 
I agree with you in principal, but the fact remains there are people out there who, like this user, can throw the hardware together left and right, but don't really know much beyond that.  There are people who are ignorant to a Yahoo, Google, or even search within the forums.  However, since this is the Absolute Beginner Talk forum, we should expect and honor absolute beginner questions.  I still ask plenty of what I'm sure people call "dumb" questions out of ignorance, but I really appreciate it when the community still comes together and helps me out.  Sometimes it's just a how-to.  Sometimes it's a how-to with explanations of what each step is doing (more educational) and sometimes it is a polite "please see this/these posts for more information, then post back if you still have questions" (educational in more than 1 way, and still polite).

So, let's put our personal frustrations on the back burner when we answer a post in this forum - it is for absolute beginners - doesn't say "expect you've researched everything you possibly could so you're not a beginner forum".

It can be frustrating, but I remember being there, and I remember the people who treated me badly (few) and wish I could remember all the people who have treated me with kindness (many,many,many).

Just my thoughts, nothing personal intended!

Dave....:)

---

### Post by hyperhopper on 2009-01-31
> **teh_yodeler said:**
> hyperhopper.... One would sleep on the couch because one would not be allowed in bed with the woman.

Basically it means that you're in trouble, so you have to sleep by yourself (or with the dog).

Now if you still don't get it, just give up! lol

I guess i'm hopeless :(

> **andrew.mckevitt said:**
> I managed to solve the same problem by buying my g/friend a macbook. Got my pc back and lots of sex too.:D

macboocks are awesome (but too costly for me)

what is sex?

---

### Post by hyperhopper on 2009-01-31
YOU PEOPLE ARE WEIRD! SLEEPING ON COUCHES! and is sex a program she installed on your pc?

---

### Post by RAiN2M on 2009-01-31
> **avtolle said:**
> +1

(and maybe +infinity if the person with 2 x chromosomes is your wife as opposed to just your girlfriend. :D

hahahaha, yea... dual-boot, it's pretty easy.

---

### Post by johnjohn2 on 2009-01-31
Stick ubuntu on it and live with Madame Palm and her five lovely daughters for a day or two, possibly three, scrap that a month.
;)

---

### Post by sirebral on 2009-01-31
I'm with andrew's opinion here.  If she just scrapped her computer buy her one as a gift or something.  The little sub sized desktops are usually inexpensive for what you get.

---

### Post by andrew.mckevitt on 2009-02-01
> **sirebral said:**
> I'm with andrew's opinion here.  If she just scrapped her computer buy her one as a gift or something.  The little sub sized desktops are usually inexpensive for what you get.

If I was to buy my girlfriend a cheap little sh**y atom powered piece of junk, she'd think I was having an affair and while I was sleeping in the shed I'd be thinking - wouldn't the sofa be a lovely place to be, even with a smelly dog with bad breath!! Go buy her something she really wants, not want you think she needs.
Personally, I love these low powered pcs, my desktop is 8 years old with a 400MHz fsb pentium 4, my server is wasted (the only dual core i have) and my fave pc of all time is my li'll eeePC of which i use 99% of the time. I could try taking the mac off the missus, but I know deep down that I'd lose. Anyway, when you reach my age, you know that you will never be happy unless your woman's happy.
Must go, she's ringing the bell............

---

### Post by Paqman on 2009-02-01
Wow, some seriously misogynistic and immature advice going down in this thread!

My opinion: if she likes Windows let her use it. Dual-boot, but let it default to Ubuntu. That way if she wants to reboot into Windows she can, but otherwise it'll go straight to Ubuntu. In my experience if you do that people will give Ubuntu a go, and realise they can use it for most stuff.

Never force someone to change their OS. Linux is about choice, not twisting people's arms. If they happen to like Windows, tough. Trying to make them do something they don't want to do will just annoy them and give Linux a bad name.

---

### Post by GMachine_24 on 2009-02-01
I'm with the people who say dump your girlfriend, keep the computer

---

### Post by squeabs on 2009-02-01
Yes, dump her.
It's your computer, your OS choice. I don't understand why you listen when she tells you not to install Ubuntu on YOUR computer.
And if she's going to have you sleeping on the couch over a trivial matter like this, you'd better leave before it gets worse.

But aside from that, a fresh install of Windows on her computer will probably have it humming a little better than it was (being bogged down with whatever was there). As far as giving up yours and buying her a new one...no.

---

### Post by dj722000 on 2009-02-11
> andrew.mckevitt Sounds like she's into *nix more than you, sorry dude, your missus is way cooler than you, like!

Easy there, LOL There was a few things I had to go back for until I figured it out in UBUNTU. I don't go back cause of choice, almost a need to. But I also put it on her laptop for her too. (It's a learning thing) Where getting to a point where its all we use any more. I like it as does the misses. And its way better then WINDOWS. Unfortunately, I'M gonna have to wipe my whole hard drive soon cause we don't need windows for anything, now its just wasted space and I totally refuse to go upgrade for something that should be a SP to VISTA.

---

### Post by lil_kid1333 on 2009-02-11
> **hyperhopper said:**
> why is there no point in telling me?

i have every right to know.

*makesconspiracytheory*

You need jesus if you don't know >_> lol jk

Well i just broke up with my girlfriend so I don't gotta trip about her and my computers :D but im sad :'( 

anyways just let her know wuz up that your the man and shes the girl and its YOUR computer so yeah :)

---

### Post by sofasurfer on 2009-02-11
I'm sure that I should not be surprised that a person can spend thousands of dollars on a computer, but I want to know HOW that is done. Mine cost hundreds to build. It is a lower end system but still very adequete for anything I want to do. Where does "thousands of dollars" fit into the picture?

---

### Post by lkraemer on 2009-02-11
Edge92,
Ever wonder why the ladies always have to be changing things like
Curtains, Couches, Chairs, Carpet, and MEN?  Reading your post made
a COLD CHILL run up my spine.....

Take these words of Wisdom to Heart from some one who knows....

1. "NEVER, NEVER let a woman control YOUR MONEY".
2. "NEVER depend on a woman's income".
3. "NEVER feel sorry for a woman, but treat her NICE!"

And finally, I'll add the last one from my good friend.

4.  "SAVE Yourself a FIT"!
Don't tell her what you are going to do, because she will throw a FIT.
Then when you actually do it, SHE will throw another FIT.
So, save yourself a FIT, just go do it, and she will only throw one FIT.
You are saving ONE FIT.

I'll add a question you can pose to her.  Since she wants Windows,
and you want Ubuntu, ask her if you can have a second girlfriend.
I'll bet she won't like that idea either!

Good Luck.

lkraemer

---

### Post by AllRadioisDead on 2009-02-11
> **Casper Hansen said:**
> At least you got sex...
Ubuntu>Sex 
:P

---

### Post by Vaedrah on 2009-02-11
Moderators - can we keep topics here to Ubuntu / Technical

I don't care if the origin poster is a girl/guy/lesbian/gay/transvestite/transexual/space alien or whatever - can we please keep topics TECHNICAL.

I don't want to hear about some naive kids wet dreams or woman fantasies or bed positions or any matter of sex acts - can we keep these forums clean and TECHNICAL. Ubuntu forums should be to discuss TECHNICAL ISSUES not some lamer with a girlfriend.

I respect the Ubuntu community a great deal - and I learn a lot from these forums. However, reading about tarts and their conned up losers is not in place here.

Moderators, Please close this thread - it is only fit for lamers and has no place in a TECHNICAL FORUM.

---

### Post by AllRadioisDead on 2009-02-11
Just tell her to give it a try, make her try it for a week, if she doesn't like it, install windows.

---

### Post by jrusso2 on 2009-02-11
> **Vaedrah said:**
> Moderators - can we keep topics here to Ubuntu / Technical

I don't care if the origin poster is a girl/guy/lesbian/gay/transvestite/transexual/space alien or whatever - can we please keep topics TECHNICAL.

I don't want to hear about some naive kids wet dreams or woman fantasies or bed positions or any matter of sex acts - can we keep these forums clean and TECHNICAL. Ubuntu forums should be to discuss TECHNICAL ISSUES not some lamer with a girlfriend.

I respect the Ubuntu community a great deal - and I learn a lot from these forums. However, reading about tarts and their conned up losers is not in place here.

Moderators, Please close this thread - it is only fit for lamers and has no place in a TECHNICAL FORUM.

Why would you even read a thread called Girl Friend problems if you wanted technical issues.  Just skip right over it.

---

### Post by lil_kid1333 on 2009-02-11
> **lkraemer said:**
> Edge92,
Ever wonder why the ladies always have to be changing things like
Curtains, Couches, Chairs, Carpet, and MEN?  Reading your post made
a COLD CHILL run up my spine.....

Take these words of Wisdom to Heart from some one who knows....

1. "NEVER, NEVER let a woman control YOUR MONEY".
2. "NEVER depend on a woman's income".
3. "NEVER feel sorry for a woman, but treat her NICE!"

And finally, I'll add the last one from my good friend.

4.  "SAVE Yourself a FIT"!
Don't tell her what you are going to do, because she will throw a FIT.
Then when you actually do it, SHE will throw another FIT.
So, save yourself a FIT, just go do it, and she will only throw one FIT.
You are saving ONE FIT.

I'll add a question you can pose to her.  Since she wants Windows,
and you want Ubuntu, ask her if you can have a second girlfriend.
I'll bet she won't like that idea either!

Good Luck.

lkraemer

+5

lol you have a good point their about those damn "fits" and the second girlfriend!!

word of advice dont let her control you cause once she does you might as well dump her and get a new girl O.O

you should just stick with ubuntu she loves you she will understand and deal with it! I lost track of how many times I had it my way with my ex! she wouldnt like it oh well I would make her like it :) and why cause she loves me but the hell with her now >_> :'(

---

### Post by cjv8888 on 2009-02-11
```
sudo chown -R username:group /path/to/girlfriend
```

---

### Post by dj722000 on 2009-02-15
> sofasurfer
I'm sure that I should not be surprised that a person can spend thousands of dollars on a computer, but I want to know HOW that is done. Mine cost hundreds to build. It is a lower end system but still very adequete for anything I want to do. Where does "thousands of dollars" fit into the picture?

It's just the way some people want there systems built. Some people despise lag while playing games so they search for any hardware they can get so it doesnt. You have a low end computer. I have a low/medium computer, well 2 years ago it was. Some people like high end. Low end video card cost around 75.00 or less. Medium is around 140 - 300 . High end is up around 400 to 1000.  Some people suffice with 1 gig ram, others get up around 3 gig high speed ram. Thats some money right there. They also have high end motherboards and chips. Plus there coming out or are out with triple core processors. Chip alone last I looked was around 700. Not hard when you add it up. And yes they are blazingly fast. My system I built was around 800, you go to Walmart and see there price of 600. However, not even close to mine in speed, mine would beat there's in the ground. Plus your pretty much stuck on some of those cause you cant change the hardware. There's not even a comparison.

---

### Post by earthpigg on 2009-02-15
sudo apt-get remove girlfriend --purge && sudo apt-get update && sudo apt-get install girlfriend

---

### Post by Kareeser on 2009-02-15
> **Vaedrah said:**
> I don't want to hear about some naive kids wet dreams or woman fantasies or bed positions or any matter of sex acts

What forum have YOU been reading?!

---

### Post by kansasnoob on 2009-02-15
I didn't read every post, but I absolutely recommend a dual-boot!

It's particularly simple with only one hard drive:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

If you have a complex set-up (more than one hard drive, etc.) refer to the multi-boot bible:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I always recommend:
(1) Run the live CD, if anything doesn't work (especially hardware detection) find some answers before installing. Then run the live CD some more - make sure you like it! Try several different distros!
(2) Dual boot! Everyone has a learning curve and it's wonderful to be able to boot back into familiar stomping grounds and just relax!
(3) Realize that not everyone loves Linux! That's just the way it is! I still dual-boot with XP - if Vista were the only thing Windows had available I'd use no Windows! I really, really hate Vista! OTOH I have friends that love Vista.

---

