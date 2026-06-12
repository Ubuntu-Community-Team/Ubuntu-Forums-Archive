---
title: "wmp54g v 4.1: Temporary Fix -- long non-technical post"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by dbarcena on 2007-08-17
Hello, all! 

first off, i want to say i have read many posts on this issue, and not found one that helps, but that is explained in the latter part of this post. I apologize for making a new post on an old subject, but i would love some 1-on-1 advice.

I think i have a semi-permanent (i hope) solution to my non-working wmp54g v4.1 card. 

i have no idea WHY it worked, so you know.

I have spent, literally, weeks trying to get this to work on Linux. I have tried ubuntu, gentoo (which included a broken installer and livecd! woot), pc Linux, and more; i like ubuntu studio the most, and therefore am on this forum.

i followed a mutt of installation techniques from Google, and it didn't work, but i guess last night before i passed out, i installed the linux-386 kernel, and i don't know how, but after i reinstalled the module, im online!

i know 386 is supposed to be the most stable, right? but wtf is with this card still being a beta-like issue? there are thousands of posts and comments, and no solution. this is hella-bad. its LINKSYS! they´re a HUGE company and advertised to be the most easily setup while maintaining professional abilities....i, an avid pc user and somewhat pro (but that was windows! lol) but when i came to this issue during my introduction to Linux, i was not only sent back to feeling like i was facing an apple II e, but it also felt like it was tellin yo momma jokes.

i almost punched a hole in my computer.

anyway. i know this wont get read, since it is so long, but i'd appreciate some sort of response as to what can be done, i now have carpal tunnel from working in this ghetto-rigged workstation in the guest bedroom of my house (where my fios router is). IT HURTS! 

any explanations? i dont wanna have to go through all this next time i update my friggen kernel. i 'd prefer to understand.

ahk, also, im getting a new pc soon, what 802.11 card is linux-compatible, and where do they sell em??


thanks reading, and this is not a WHINE post, i am very happy with linux, since i have spent so much time modifying windows and feeling like a criminal, its good to be using a software that understands the need for personalized software!

thanks again,
dave

---

### Post by Junglizer on 2007-08-17
First off, as a Gentoo person myself, I am curious as to which version you tried installing if you remember. I know that they've more recently switched to the GUI based installer, which, if I may be blunt absolutely stupid. I've not personally chosen to install anything with 2006.0 or newer versions. 2005.1 Forever. Or at least Knoppix install. Gentoo is a source distro and you always have the trade off, complexity with the bonus of adaptability versus ease of use with limitations. I tend to favor the former.  

For your Broadcom card: NDISWRAPPER
As far as Linksys/Cisco being a huge company, well, MS Windows still has the majority of the user base that they are marketing towards. Yes they probably could have sold a lot more cards if people were like "hey, this works in *nix, I'll take it." But some companies just don't think that way.

As far as a good compatible 802.11x card (not to be confused with 802.1x) but since you didn't list a specific band I'll notate it as it would be commonly seen. I would reccommend something that has an Atheros chipset, as these work exceptionally well with *nix. I'm a huge fan of the AR5112/5113 chipset, but its dual band 5Ghz/2.4Ghz so it maybe more then you need. You can check [The Atheros Product Search Page]("http://customerproducts.atheros.com/customerproducts/ResultsPageBasic.asp") to find out what chips are in specific cards. That or google search "product/model# chipset."

---

### Post by Junglizer on 2007-08-21
Bump for reply?

---

### Post by Het Irv on 2007-08-21
If you are going to use NDISWrapper (which works fine after you get it installed), you might want to look at this thread.  I was the one I was on when I was trying to get mine to work.

[http://ubuntuforums.org/showthread.php?t=499463](http://ubuntuforums.org/showthread.php?t=499463)

Wireless on Linux is a pain but it is possible.  Linksys is one of the few brands that does not work right off.  I do know that there is a list of compatible cards somewhere.  Sorry, but I cannot remember where.

---

