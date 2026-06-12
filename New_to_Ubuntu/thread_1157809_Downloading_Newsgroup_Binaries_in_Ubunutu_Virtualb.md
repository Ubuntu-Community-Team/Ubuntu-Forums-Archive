---
title: "Downloading Newsgroup Binaries in Ubunutu Virtualbox Using MS Vista"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by mikodo on 2009-05-13
Hello Everyone,

I expect to get "Blasted" for this thread, but being a greener than green Newbie to Ubuntu and Nix environments, I hope you can cut me a little slack. I have never downloaded newsgroups in any OS. I own a copy of Windows Vista. I do not yet know how to use any thing like Hellanzb, for lack of understanding of command line encounters to attempt to use it for newsgroups. I have friends who are well versed in newsgroup downloading, who would readily walk me through the process of setting up binary downloading in MS. Please don't get me wrong; I intend to slowly keep on honing my skills in Ubuntu Hardy as it is the only operating system I use.

But,,,. I would like to try Usenet and I wonder if in the interim, until I can find the time to learn Linux better, if the Virtualbox available in Ubuntu repositories could be used to place Vista in it as a virtual OS, so as to allow my friends to set up Usenet downloading for me in Windows? I am the only person within my group of friends who uses Linux and I am encouraging them to try Ubuntu, especially the ones how are very tired of the many issues they have with security and propriety issues within MS, that they complain about frequently. 

I am in my late 50's and have had very little experience with computers, and am learning really slow, so it seems,

So, if these questions are not too distasteful for some of you in "Nix" land, can you tell me if the virtual OS with Vista would be fast enough for binary downloadings?

I use a HP Quad with 32 bit microprocessor.

Thanks

---

### Post by alphacrucis2 on 2009-05-13
> **mikodo said:**
> Hello Everyone,

I expect to get "Blasted" for this thread, but being a greener than green Newbie to Ubuntu and Nix environments, I hope you can cut me a little slack. I have never downloaded newsgroups in any OS. I own a copy of Windows Vista. I do not yet know how to use any thing like Hellanzb, for lack of understanding of command line encounters to attempt to use it for newsgroups. I have friends who are well versed in newsgroup downloading, who would readily walk me through the process of setting up binary downloading in MS. Please don't get me wrong; I intend to slowly keep on honing my skills in Ubuntu Hardy as it is the only operating system I use.

But,,,. I would like to try Usenet and I wonder if in the interim, until I can find the time to learn Linux better, if the Virtualbox available in Ubuntu repositories could be used to place Vista in it as a virtual OS, so as to allow my friends to set up Usenet downloading for me in Windows? I am the only person within my group of friends who uses Linux and I am encouraging them to try Ubuntu, especially the ones how are very tired of the many issues they have with security and propriety issues within MS, that they complain about frequently. 

I am in my late 50's and have had very little experience with computers, and am learning really slow, so it seems,

So, if these questions are not too distasteful for some of you in "Nix" land, can you tell me if the virtual OS with Vista would be fast enough for binary downloadings?

I use a HP Quad with 32 bit microprocessor.

Thanks

Get yourself a good newsreader program. 'Agent' is a good one for Windows. I haven't accessed usenet/newsgroups for some time as the groups I used to subscribe to were overrun by trolls and nutcases. I used a program called xnews in those days which was freeware. It worked well but had a slightly eccentric interface. For Linux I have heard 'knode' well spoken of by I can neither confirm nor deny.

---

### Post by mikodo on 2009-05-13
Thanks for the reply. I am still left wondering:

"if the virtual OS with Vista would be fast enough for binary downloadings?"

---

### Post by alphacrucis2 on 2009-05-13
> **mikodo said:**
> Thanks for the reply. I am still left wondering 

if the virtual OS with Vista would be fast enough for binary downloadings?

I don't see why not. Moving files over a network connection shouldn't be particularly cpu intensive.

---

### Post by mikodo on 2009-05-13
Thanks

Mikodo

---

### Post by MJWitter on 2009-05-13
I know you haven't asked for it, but at some stage you may like to take a look at a program called SABNZBD plus. If you are using Ubuntu 9.04 then it is in the repository and as far as i know all changes are made through a web interface.

---

### Post by mikodo on 2009-05-13
> **MJWitter said:**
> I know you haven't asked for it, but at some stage you may like to take a look at a program called SABNZBD plus. If you are using Ubuntu 9.04 then it is in the repository and as far as i know all changes are made through a web interface.

Thanks, I will.

Mikodo

Canada

---

### Post by alphacrucis2 on 2009-05-13
> **mikodo said:**
> Thanks, I will.

Mikodo

Canada

Another Linux program to check out is called pan.

[http://pan.rebelbase.com/]("http://pan.rebelbase.com/")

---

### Post by mikodo on 2009-05-13
> **MJWitter said:**
> I know you haven't asked for it, but at some stage you may like to take a look at a program called SABNZBD plus. If you are using Ubuntu 9.04 then it is in the repository and as far as i know all changes are made through a web interface.

Yes this looks like something I might be able to handle. Your right though, from the sites I visited, it appears the reincarnated version of this is only available for Jaunty. Too bad, but hey, going back to the Virtualbox thing, maybe I could learn something about it by using it and installing Jaunty into it and then trying SABnzbd. 

Thanks guys,

Solved

---

### Post by scottuss on 2009-05-13
LottaNZB, the best front end for HellaNZB, gives it a graphical user interface so it's not as scary, it's easy to set up too. Any one can do it

---

### Post by MJWitter on 2009-05-13
> **mikodo said:**
> Yes this looks like something I might be able to handle. Your right though, from the sites I visited, it appears the reincarnated version of this is only available for Jaunty. Too bad, but hey, going back to the Virtualbox thing, maybe I could learn something about it by using it and installing Jaunty into it and then trying SABnzbd. 

Thanks guys,

Solved

There is also a ppa for older versions of Ubuntu. 
[http://forums.sabnzbd.org/index.php?topic=387.0](http://forums.sabnzbd.org/index.php?topic=387.0) Has easy directions on how to install it on earlier editions, which will also keep it up to date with new releases.

Good luck!

---

### Post by Kapurnicus on 2009-05-13
Not to knock your methods, but it seems incredibly inefficent to run a virtual machine for that (if you must you must however) mainly because of the hard drive space wasted with a vista install (mine is 15 gigs out of the box). What I did (since I as well came from windows and was very well versed in binary newsgroup downloads) moved my program over with Wine. I used Alt.Binz on windows and loved it, had every feature I needed. After installing wine (sudo apt-get install wine) I just downloaded the Alt.Binz 0.25 installer.exe and double clicked on it. Wine walked me through the install and everything was peachy keen from then on. Haven't run into a single bug.

What I'm saying basically is try to install one of the programs your friends use in Win and if it works they can help you set it up there (since it will have the same config menus and use the internet the same way). Wine requires no configuration in most cases for simple applications like this, so you shouldn't have any issues.

Good luck :)

---

### Post by scottuss on 2009-05-13
> **Kapurnicus said:**
> Not to knock your methods, but it seems incredibly inefficent to run a virtual machine for that (if you must you must however) mainly because of the hard drive space wasted with a vista install (mine is 15 gigs out of the box). What I did (since I as well came from windows and was very well versed in binary newsgroup downloads) moved my program over with Wine. I used Alt.Binz on windows and loved it, had every feature I needed. After installing wine (sudo apt-get install wine) I just downloaded the Alt.Binz 0.25 installer.exe and double clicked on it. Wine walked me through the install and everything was peachy keen from then on. Haven't run into a single bug.

What I'm saying basically is try to install one of the programs your friends use in Win and if it works they can help you set it up there (since it will have the same config menus and use the internet the same way). Wine requires no configuration in most cases for simple applications like this, so you shouldn't have any issues.

Good luck :)

Whilst I do agree with you, what could be simpler than downloading 1 deb file, double clicking it and having HellaNZB and LottaNZB installed for you, ready to roll?

But I agree, if you must use Windows apps, Wine is the better way to do it

---

### Post by mikodo on 2009-05-13
> **scottuss said:**
> LottaNZB, the best front end for HellaNZB, gives it a graphical user interface so it's not as scary, it's easy to set up too. Any one can do it

I've read into HellaNZB extensively,and know how to get it from the repositories, so SABnzbd plus; LottaNZB or using Wine with "Other Programs" all sound really promising for me. I'll look into them all!

Thanks guys,

Mikodo

Canada

---

### Post by The Cog on 2009-05-13
How about using Mozilla thunderbird? It's available for both Windows and Linux.

---

### Post by Tweak42 on 2009-05-13
> **The Cog said:**
> How about using Mozilla thunderbird? It's available for both Windows and Linux.

Mikodo was asking about binary newsreaders, that which Thunderbird is really not suited to do.

Regarding your Virtualbox question, I wouldn't use Vista if you can help it.  A stripped down version of XP install would work just fine until you can migrate using wine or native linux binary newsreader.

Newsleecher, one of the top windows binary readers has a thread on getting it running under wine.
[http://www.newsleecher.com/forum/viewtopic.php?t=13822](http://www.newsleecher.com/forum/viewtopic.php?t=13822)

---

### Post by mikodo on 2009-05-13
> **Tweak42 said:**
> Mikodo was asking about binary newsreaders, that which Thunderbird is really not suited to do.

Regarding your Virtualbox question, I wouldn't use Vista if you can help it.  A stripped down version of XP install would work just fine until you can migrate using wine or native linux binary newsreader.

Newsleecher, one of the top windows binary readers has a thread on getting it running under wine.
[http://www.newsleecher.com/forum/viewtopic.php?t=13822](http://www.newsleecher.com/forum/viewtopic.php?t=13822)

Thanks for the post and the link to newsleacher under wine.

Mikodo

---

### Post by scottuss on 2009-05-16
I don't get it. I really don't. I appreciate that Free Software means choice, but surely using native apps is a much better option all round than running WINE.

WINE is meant for those applications that do not have a good native equivalent. It should not be advised that people run software in WINE unless they really have to, i.e Photoshop etc.

The native Usenet clients ARE NOT difficult to set up, they ARE as good (if not better) than Windows ones, and SHOULD be recommended above Windows clients on WINE.

The Free Software world's reliance on WINE needs to be lowered, it is an interim solution NOT an integral part of every Linux installation, let's keep it that way!

</rant>

---

### Post by Tweak42 on 2009-05-16
> **scottuss said:**
> 

The native Usenet clients ARE NOT difficult to set up, they ARE as good (if not better) than Windows ones, and SHOULD be recommended above Windows clients on WINE.

The Free Software world's reliance on WINE needs to be lowered, it is an interim solution NOT an integral part of every Linux installation, let's keep it that way!

</rant>

Really the decision on whither the native clients are "superior" to the windows one should be left to the user.  As you stated it's about more choices and options, which is what Wine does give..

---

