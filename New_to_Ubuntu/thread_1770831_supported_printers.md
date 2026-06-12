---
title: "supported printers"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by mkornig on 2011-05-29
Is there a list (published somewhere on the Internet) of well supported printers for a given Ubuntu version? By *well supported* I mean:

[LIST]
[*]recognized automatically
[*]ready to print within 5 minutes, without any fancy uploading from the Internet
[*]fully fonctional under that given Ubuntu version, i.e. printing of test pages, ink level display, fax, scanning, etc. if present
[/LIST]

---

### Post by wolfen69 on 2011-05-29
9 times out of 10, HP printers will work 100% out of the box. They have great linux support.

---

### Post by mkornig on 2011-05-29
Thanks wolfen for your reply.

My question remains: do such lists exist? And where can I find them?

---

### Post by bennachie on 2011-05-29
There are such lists (check Google), but they tend to go out of date very quickly because of very rapid model turnover. Ubuntu is really very good at sorting out automatically how to support particular printers with the drivers and printer descriptions available. The earlier advice in this thread about HP printers is accurate but, in many ways, your best approach would be to choose a printer and, prior to purchase, check back here to see if anyone has had prior experience with that specific model.

---

### Post by wolfen69 on 2011-05-29
Also, all the newest Lexmark printers have linux drivers. They even put a tux logo on the box now.
[IMG]http://www.phoronix.net/image.php?id=lexmark_linux&image=lexmark_pro905_linux1_med[/IMG]

---

### Post by Rex Bouwense on 2011-05-29
Lexmark finally is coming around.  I had to get rid or a Lexmark printer because I couldn't get it to work.  When I think about all of the bad words that I called Lexmark, now I'll have to take them all back.

---

### Post by walt.smith1960 on 2011-05-29
All Lexmark, or just the "business class" machines?  It seems the business class machines have had Linux support for a while, the $39 specials at Walmart or Staples have been another matter.  it'd be good to see another manufacturer devoting more than token efforts to supporting Linux.

---

### Post by mkornig on 2011-05-30
> **wolfen69 said:**
> Also, all the newest Lexmark printers have linux drivers.
I've had an unpleasant and lengthy experience with a Lexmark printer recently: [http://ubuntuforums.org/showthread.php?t=1766342](http://ubuntuforums.org/showthread.php?t=1766342)
(And the vendor praised this printer as very Linux friendly.)

---

### Post by jtarin on 2011-05-30
There is a [list]("http://www.openprinting.org/printers") for Linux in general. You must remember Ubuntu is only a distro of Linux.I think the advice given previously about looking for information about a particular printer and doing your homework by learning how to use CUPS will make setting up a printer a breeze. The first time is the learning experience.Just like the first time for anything.

---

### Post by 3rdalbum on 2011-05-30
HP printers and multifunctions work well. The ink isn't cheap and you can't get generic ones (I don't think you can) but otherwise they all work on Linux. Just don't try to run a brand-new printer on an old distro or you'll have to manually update the hplip software.

---

### Post by mkornig on 2011-05-30
> **bennachie said:**
> There are such lists (check Google)...

Can you be more precise? Give the URL maybe?

> **bennachie said:**
> ...in many ways, your best approach would be to choose a  printer and, prior to purchase, check back here to see if anyone has had  prior experience with that specific model.

Check back here in the forum? Sorry, I don't think that's a very reliable approach. Mainly because user experience, user effort and user tolerance towards bugs vary a lot. What is "a straight forward installation" for one user may be "a complete nightmare" for another. I think a reliable, official list would be much better than a request that may (or may not) be answered in a few hours or days...

---

### Post by jtarin on 2011-05-30
> **mkornig said:**
> Can you be more precise? Give the URL maybe?



Check back here in the forum? Sorry, I don't think that's a very reliable approach. Mainly because user experience, user effort and user tolerance towards bugs vary a lot. What is "a straight forward installation" for one user may be "a complete nightmare" for another. I think a reliable, official list would be much better than a request that may (or may not) be answered in a few hours or days...What's my link? Chopped Liver? :p
Try reading my post again.

---

### Post by mkornig on 2011-05-30
> **jtarin said:**
> What's my link? Chopped Liver? :p
Try reading my post again.

Sorry jtarin. I must have overlooked the link in your earlier post: [http://www.openprinting.org/printers](http://www.openprinting.org/printers)
is an interesting source.

I wonder whether differences between Debian like distros and others are important? Personally I had a problem recently with a driver that was not suitable for a 64 bit architecture. You mention CUPS. What is that? You see there are a number of technical issues.

On the whole, I think installing a printer is too difficult for a Ubuntu newbe unless the printer is recognized automatically and the driver comes with the Ubuntu installation CD. Hence my request about specific Ubuntu lists.

And if experienced Ubuntu users don't want to use these lists that's fine with me. But for beginners I believe they would be very helpful.

---

### Post by migs73 on 2011-05-30
A list of linux compatible Brother printers is here;

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

Not exactly out the box drivers and setting it up can be a bit daunting, but asking on here gets simplified answers.

Mike

---

### Post by mkornig on 2011-05-30
Hi folks,

Thanks a lot for all those who posted on this topic, shared their thoughts and opinions.

Some 20 hours later, it seems to me that the lists I dreamt of and will keep dreaming of do not exist. Which is a pitty I believe. Canonical or who ever makes Ubuntu should have this information at hand. I don't really understand why they don't publish it on the net whenever they release a new version of Ubuntu, i.e. twice a year. It can't be an awful lot of work.

I will now declare this thread as "solved". Cheers

---

### Post by wolfen69 on 2011-05-30
If it makes you feel any more confident, I've have yet to see an HP printer that didn't work "out of the box" in ubuntu.

---

### Post by createdcreature on 2011-05-30
HP do HPLIP, which allows HP printers to work with all major Linux distros.

---

### Post by JKyleOKC on 2011-05-30
> **mkornig said:**
> Hi folks,

Thanks a lot for all those who posted on this topic, shared their thoughts and opinions.

Some 20 hours later, it seems to me that the lists I dreamt of and will keep dreaming of do not exist. Which is a pitty I believe. Canonical or who ever makes Ubuntu should have this information at hand. I don't really understand why they don't publish it on the net whenever they release a new version of Ubuntu, i.e. twice a year. It can't be an awful lot of work.

I will now declare this thread as "solved". CheersThe problem with publishing such a list as "official" is that by the time it's compiled and made available, many if not most of the printers listed will be obsolete and no longer available.

The earlier references to CUPS are, I believe, quite important. CUPS is the Common Unix Printing System, now owned by Apple but available for all to use at no cost. Most if not all versions of Ubuntu install the basic CUPS setup automatically by default, but they do not automatically install any specific printers. The system does include drivers that work, though, for many different printer models, so looking at the CUPS documentation and examining the driver collection is your best bet for getting anything official.

In my experience, the CUPS drivers work better for HP printers than does the HPLIP system; I've tried them both with my HP1320 laser printer and abandoned HPLIP. Epson also has a good collection of drivers that work with CUPS. I've not experimented with any other brands...

---

### Post by mkornig on 2011-05-30
> **wolfen69 said:**
> If it makes you feel any more confident, I've have yet to see an HP printer that didn't work "out of the box" in ubuntu.

Great! Great for or people who have an HP or plan to buy one.

The last two printers I had, a Samsung and a Lexmark, were hard to install on Linux systems. In both cases I struggled for many days if not weeks. :( But eventually succeeded with the help of friends/forums... I would not have purchased them if I had been able to foresee the hassle. Actually, the Lexmark was meant to be very Linux friendly (according to the vendor).

---

### Post by raziel09 on 2011-05-30
I have had both an Epson printer (very old C46) and my newer current printer which is an Lexmark s305.

The epson worked fantastic and was instantly recognised; my lexmark unfortunately wasn't instantly found but the lexmark site includes drivers for several versions of linux and once installed worked fine.

I can perform troubleshooting and check ink levels thanks to the lexmark toolbox which is installed along with the drivers. Took about 10 mins to set up.

My advice would be go for an older printer which suits your needs, like those available in supermarkets for around £40. The older an printer the more likely it will be supported.

I think i read on here once that the best printer for linux support are Epson.

---

### Post by mkornig on 2011-05-30
> **JKyleOKC said:**
> The problem with publishing such a list as "official" is that by the time it's compiled and made available, many if not most of the printers listed will be obsolete and no longer available.

Are you saying that by the time a new Ubuntu version is released the people who have compiled it don't know which printers are supported "out of the box"? I would hope these people know what they are doing. All I would like to see is this list of printers. It doesn't need to be updated after the release date. And then, six months later I would consult the new list. Don't tell me that the live time of printers is shorter than six months.

> **JKyleOKC said:**
> Most if not all versions of Ubuntu ... do not automatically  install any specific printers.

They don't? But still some printers work "out of the box", don't they? Kind of "plug and print". This is what is important. I don't really care how this is achieved. And I believe the average Ubuntu beginner doesn't care either.

---

### Post by wolfen69 on 2011-05-30
> **mkornig said:**
> Actually, the Lexmark was meant to be very Linux friendly (according to the vendor).

Lexmark now gives you a cd with linux drivers on it.

Do you have anything against HP?

---

### Post by mkornig on 2011-05-30
> **wolfen69 said:**
> Do you have anything against HP?

No, I don't. Why?

---

### Post by JKyleOKC on 2011-05-30
> **mkornig said:**
> Don't tell me that the live time of printers is shorter than six months.

(snipped)

But still some printers work "out of the box", don't they? Kind of "plug and print". This is what is important. I don't really care how this is achieved. And I believe the average Ubuntu beginner doesn't care either.To verify that all those printers work would have to be started well in advance of a release date, and most manufacturers seem to change printer model numbers at least a couple of times a year. Net result is that a list that began checking in April of 2011 might be ready to accompany a release by April of 2012, and by then most listed models would be difficult to find in the stores.

As for working "out of the box" I've had good results using CUPS. You access it by opening a browser and typing "http://localhost:631" in its address bar. This (which will work on any system on which CUPS is installed, since "localhost" always refers to your own machine and port 631 is where CUPS communicates) gets you its home page, and on the tab labeled "Printers" you can click "Add printer" to start a wizard that will locate all the printers on your system which the program can identify. From there it's just a matter of making the selection and clicking "next" to complete the installation.

---

### Post by jtarin on 2011-05-30
> **mkornig said:**
> Great! Great for or people who have an HP or plan to buy one.

The last two printers I had, a Samsung and a Lexmark, were hard to install on Linux systems. In both cases I struggled for many days if not weeks. :( But eventually succeeded with the help of friends/forums... I would not have purchased them if I had been able to foresee the hassle. Actually, the Lexmark was meant to be very Linux friendly (according to the vendor).Strange.....I have 3 different Samsungs and they all work under Linux and I believe my total struggle time was an accumulated 30 minutes for all 3.(with CUPS)

---

### Post by mkornig on 2011-05-30
> **JKyleOKC said:**
> 
and on the tab labeled "Printers" you can click "Add printer" to start a wizard that will locate all the printers on your system which the program can identify.

This is interesting, JKyleOKC. I guess CUPS checks all the ports to see whether there are printers connected to them. And then it tries to identify them. In the identification process it probably compares each printer with a local list/database. Am I right?

Assuming, nothing has been added since system installation, this list must be specific to the Ubuntu version installed on my computer. Right?

Well, can I display this list somehow? It seems I'm getting closer to my dream now.

I'd like to see these lists published on the internet for given Ubuntu versions. I guess that's all I'm asking for.

---

### Post by jtarin on 2011-05-30
[OpenPrinting CUPS Quick Start]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/cupsdocumentation")

---

### Post by mkornig on 2011-05-30
> **jtarin said:**
> Strange.....I have 3 different Samsungs and they all work under Linux and I believe my total struggle time was an accumulated 30 minutes for all 3.(with CUPS)

Well, I didn't say that I didn't get my Samsung printer print in the end. It took me about 2 weeks. And the last day I had a friend who helped a great deal.

10 minutes and 2 weeks. That's probably the difference between an experienced user (you) and a greenhorn (me).

---

### Post by jtarin on 2011-05-30
> **mkornig said:**
> Well, I didn't say that I didn't get my Samsung printer print in the end. It took me about 2 weeks. And the last day I had a friend who helped a great deal.

10 minutes and 2 weeks. That's probably the difference between an experienced user (you) and a greenhorn (me).I wasn't an experienced printer installer at the time. I just did research on the driver I would need. Tried two they didn't work and found one that was made specifically for my Samsung printers. What I would do if I were you is select several printers that you like and do the research before attempting an install. Using the CUPS [interface]("http://localhost:631/") makes installation easier. Become familiar.
[http://localhost:631/](http://localhost:631/)

---

### Post by dFlyer on 2011-05-30
> **mkornig said:**
> Is there a list (published somewhere on the Internet) of well supported printers for a given Ubuntu version? By *well supported* I mean:

[LIST]
[*]recognized automatically
[*]ready to print within 5 minutes, without any fancy uploading from the Internet
[*]fully fonctional under that given Ubuntu version, i.e. printing of test pages, ink level display, fax, scanning, etc. if present
[/LIST]

HP Printers with linux are plug and play mostly.

---

### Post by wolfen69 on 2011-05-30
> **JKyleOKC said:**
> 
As for working "out of the box" I've had good results using CUPS. You access it by opening a browser and typing "http://localhost:631" in its address bar. This (which will work on any system on which CUPS is installed, since "localhost" always refers to your own machine and port 631 is where CUPS communicates) gets you its home page, and on the tab labeled "Printers" you can click "Add printer" to start a wizard that will locate all the printers on your system which the program can identify. From there it's just a matter of making the selection and clicking "next" to complete the installation.

I've never had to do any of that with any HP printer I've had. I plugged it in and 4 seconds later it's installed and ready to go. And these were new off the shelf printers. There might be better printers than HP, I don't know, but I like having plug *n* play devices.

---

### Post by jtarin on 2011-05-30
> **wolfen69 said:**
> There might be better printers than HP, I don't know, but I like having plug *n* play devices.Yes there are.:p Now you know.:)

---

### Post by mkornig on 2011-05-31
Hi,

I've checked out the following two printer lists on the net:

(1) [http://www.openprinting.org/printers](http://www.openprinting.org/printers)
(2) [http://www.cups.org/ppd.php](http://www.cups.org/ppd.php)

[LEFT](1) is by The Linux Foundation. It was mentioned by jatrin earlier in this thread, I believe. You can select a printer (from a huge list) and then see specific information about it: Linux friendly or not? recommended driver(s), where to download, specific forums, user comments, etc.

(2) is the same thing for Postscript Printer Drivers (PPD). You can choose from more than 1200 printers. Most of these PPDs seem to be a few years old.

**Questions:** Are these two lists of any relevance to the question whether or not a given printer will work "out of the box" under a given Ubuntu version? Do Ubuntu systems use these two lists in any way? Are PPDs useful/used under Ubuntu at all?
[/LEFT]

---

### Post by jtarin on 2011-05-31
> **mkornig said:**
> Hi,

I've found the following two printer lists on the net:

(1) [http://www.openprinting.org/printers](http://www.openprinting.org/printers)
(2) [http://www.cups.org/ppd.php](http://www.cups.org/ppd.php)

[LEFT](1) is by The Linux Foundation. You can select a printer (from a huge list) and then see specific information about it: Linux friendly or not? recommended driver(s), where to download, specific forums, user comments, etc.

(2) is the same thing for Postscript Printer Drivers (PPD). You can choose more than 1200 printers. Most of these PPDs seem to be a few years old.

**Questions:** Are these two lists of any relevance to the question whether or not a given printer will work "out of the box" under a given Ubuntu version? Do Ubuntu systems use these two lists in any way? Are PPDs useful/used under Ubuntu at all?
[/LEFT]
first of all....those two links were given to you in this thread.....if you would have looked. Secondly what is your obsession with finding this list? Are you developing printer drivers or writing a book on them. If you want to buy a printer that is guaranteed to work in Linux....go to the store....choose several printers in the price range and features you want then do your research ask in the forums. Can you guarantee that every printer will work under Windows? I don't think so. We come to accept the fact that they will......but if you don't have the driver....it won't. It's not Ubuntu that controls printing....it's Linux and its underlying print mechanisms. CUPS is one.

---

### Post by mkornig on 2011-05-31
> **jtarin said:**
> first of all....those two links were given to you in this thread.....if you would have looked.

I recognize that and I appreciate your contributions, jtarin. I simply don't have the time to analyse and follow up everything. And there are things I don't understand right away and start to make sense the next day.

> **jtarin said:**
> Are you developing printer drivers or  writing a book on them.

No.

> **jtarin said:**
> If you want to buy a printer that is guaranteed  to work in Linux....go to the store....choose several printers in the  price range and features you want then do your research ask in the  forums.
  
Yes, that's my main interest. And I believe this research could be facilitated by a list of "easy to use printers" under a given Ubuntu version.

> **jtarin said:**
> It's not Ubuntu that controls  printing....it's Linux and its underlying print mechanisms. CUPS is  one.
   
Do you mean that installing a printer, finding a printer driver, automatic recognition of a printer etc. under Ubuntu are the same as under any other Linux system? And in this respect there are no major differences between the various distros?

---

### Post by jtarin on 2011-05-31
> **mkornig said:**
>    
Do you mean that installing a printer, finding a printer driver, automatic recognition of a printer etc. under Ubuntu are the same as under any other Linux system? And in this respect there are no major differences between the various distros?Yes.....but not exactly....Ubuntu holds your hand a little more.

---

### Post by QLee on 2011-05-31
Mkornig,
I know this issue is solved and I certainly can't speak for the person to whom you addressed these questions but I do want to make a couple of comments.

[QUOTE=mkornig]... And I believe this research could be facilitated by a list of "easy to use printers" under a given Ubuntu version.[/QUOTE]
I'd have to agree with that logic, certainly if someone else has done the work, it would be easier. The problem being that a lots of others are, like you, in the situation where they don't have time to research and compile such a list, ... and once people become proficient they often lose interest in doing it, they don't need it themselves any longer.
Add the complexity of the makers putting out new models constantly and the user base continually buying the newest/greatest and then needing to ask for help because their printer wasn't available when the list was compiled and they can't find one on the list to buy in their area and very few people have the resources to keep obtaining and testing new equipment so the list becomes out-of-date fairly quickly.
   

[QUOTE=mkornig]Do you mean that installing a printer, finding a printer driver, automatic recognition of a printer etc. under Ubuntu are the same as under any other Linux system? And in this respect there are no major differences between the various distros?[/QUOTE]

I can't say if that's what jtarin meant but I would basically agree with the statement, especially GNU/Linux systems in the context of CUPS. And, it's also correct that there are lots of printers that need drivers installed in order to work on Windows, so I would even extend the general statement to that OS.

Congratulations to you both for solving.

---

### Post by Dondermans on 2011-06-01
I own a HP printer and in the configuration process I came across the following link:

[http://hplipopensource.com/hplip-web/recommended.html](http://hplipopensource.com/hplip-web/recommended.html)

You might find it interesting if you are looking into buying a HP printer.

---

### Post by mkornig on 2011-06-01
Yes, interesting link, Dondermans. HP does seem to care about Linux, and there is an impressive number of printer models to choose from.

---

### Post by MyR on 2011-06-01
mkornig:  This site might interest you: [LinuxDeal.com]("http://linuxdeal.com/")

We are trying to build the *first* list of compatible printers available for purchase.  The other lists contain old data from printers no longer for sale, plus they don't allow users to compare printers like we do :KS

Peace

---

### Post by mikodo on 2011-06-02
> **3rdalbum said:**
> HP printers and multifunctions work well. The ink isn't cheap and you can't get generic ones (I don't think you can) but otherwise they all work on Linux. Just don't try to run a brand-new printer on an old distro or you'll have to manually update the hplip software.

I have seen sites advertising generic HP ink. 

OK, here's one, in the US for the OP:

[http://www.inkcloners.com/catalog/36/60/Ink-Cartridges/HP.html](http://www.inkcloners.com/catalog/36/60/Ink-Cartridges/HP.html)

---

### Post by crazybear on 2011-08-24
> **wolfen69 said:**
> If it makes you feel any more confident, I've have yet to see an HP printer that didn't work "out of the box" in ubuntu.

Only problem with HP printers is they are very expensive to buy and more expensive to supply with ink!!!! I have struggled for a year with my Canon Pixma MP540 and thought many times I had it working with Ubuntu..only to find if I told it to print something, it printed color when asked B&W, multiple pages when asked to print one and the image not centered on the page...and forget about ink levels. I too came here today looking for a GENERAL list of at least brands, if not models that are good with Linux, generally. I think HP is out of my budget...but will check again...and long had a brother, but didn't like it with Windoz, so can't imagine I'll like it with Linux.....for what its worth.

---

### Post by mringer on 2011-12-14
HP, Dell, Brother, Lexmark, Samsung, Xerox (and maybe others)
all claim to provide some sort of Linux support for some of their 
models. I do not know if these claims are true, but you should be
safe enough if you buy from a seller with a good reputation. I 
think that there now enough manufacturers who do claim to support 
Linux that you can simply reject any who do not.

One booby trap: I think I encountered an all-in-one that had Linux
support for printing but not scanning. Sorry, I cannot now remember
what model it was.

---

