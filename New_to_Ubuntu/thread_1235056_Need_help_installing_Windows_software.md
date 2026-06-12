---
title: "Need help installing Windows software"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by steigerjb on 2009-08-08
I am going to be taking a class online in the fall. I used my Windows dual boot for my class this summer but I figure I can use Ubuntu if I get the programs/software installed in my Ubuntu.

What I need is:

Internet Explorer
Microsoft Office 2007

I have tried installing IE before but didn't work. What is the best way to install IE and MS Office in Ubuntu?

*****************************************************************************

I'll go ahead and post other questions here.  

I have tried installing the Safari web browser a while back by downloading the exe for Windows and running it in Wine. However, I go to my Wine programs...it won't start.

Is there a way to install Windows Media Player in Ubuntu? The digital copy of the Dark Knight I got from the DVD only plays with Windows Movie Maker. :(

---

### Post by credobyte on 2009-08-08
Depends on your hardware ( CPU, RAM ) .. VirtualBox would be the best option for IE and MS Office 2007.

---

### Post by Zill on 2009-08-08
> **steigerjb said:**
> I am going to be taking a class online in the fall. I used my Windows dual boot for my class this summer but I figure I can use Ubuntu if I get the programs/software installed in my Ubuntu.

What I need is:

Internet Explorer
Microsoft Office 2007
I might be missing something here but if these two programs are *essential* to you then I suggest you are best off running Windows!

Linux can do all kinds of wonderful things but it isn't easy to run MS programs successfully.  Personally, I haven't used a Windows program for many years - Firefox and OpenOffice fully meet my requirements for browsing and office use.

---

### Post by donkyhotay on 2009-08-08
You may not need IE or office depending on the class. You have to be careful (it is your education after all) but I've taken classes online that stated they needed proprietary software including IE and office and I got by just fine using firefox and open office. I even had a teacher specifically state in the syllabus to not use open office, I used open office and just made certain I saved in .doc format and she never knew the difference (it was a writing class). Definitely have a backup plan (as mentioned a virtual manchine is one of the best backup options) but unless the online class software does't work in firefox (no way to know until you use it) or if the class is about learning the ins/outs of MSoffice you can probably get by with FOSS alternatives. As I said before though, this is your education and you don't want to mess it up so make certain you know all your options and a way of using what the teacher requests in case it doesn't work.

---

### Post by theozzlives on 2009-08-08
You can use the "User Agent Switcher" addon to get FireFox to emulate MSIE and save your Open Office document files in MS Office format.

---

### Post by credobyte on 2009-08-08
> **theozzlives said:**
> You can use the "User Agent Switcher" addon to get FireFox to emulate MSIE and save your Open Office document files in MS Office format.

I don't think that it's some kind of "We love Microsoft!" class ? Unless they have a reliable reason, go for open source ( in most cases, they will be happy to hear that you know something about it ) :)

---

### Post by presence1960 on 2009-08-08
> **steigerjb said:**
> I am going to be taking a class online in the fall. I used my Windows dual boot for my class this summer but I figure I can use Ubuntu if I get the programs/software installed in my Ubuntu.

What I need is:

Internet Explorer
Microsoft Office 2007

I have tried installing IE before but didn't work. What is the best way to install IE and MS Office in Ubuntu?

*****************************************************************************

I'll go ahead and post other questions here.  

I have tried installing the Safari web browser a while back by downloading the exe for Windows and running it in Wine. However, I go to my Wine programs...it won't start.

Is there a way to install Windows Media Player in Ubuntu? The digital copy of the Dark Knight I got from the DVD only plays with Windows Movie Maker. :(

if your dual boot set up is working fine, then why mess with it? Leave well enough alone. Only use Windows for school and boot into Ubuntu for everything else. Hey i love to tinker and try things out, but this is one case where I will say "if it isn't broke don't fix it."

If it is bothering you that much then avoid wine, it is not very flexible and takes a lot of tinkering to get some things to work, while others flat out will not run. Use virtualbox to run a virtual Windows and install your software to the virtual machine.

---

### Post by steigerjb on 2009-08-09
> **presence1960 said:**
> if your dual boot set up is working fine, then why mess with it? Leave well enough alone. Only use Windows for school and boot into Ubuntu for everything else. Hey i love to tinker and try things out, but this is one case where I will say "if it isn't broke don't fix it."

If it is bothering you that much then avoid wine, it is not very flexible and takes a lot of tinkering to get some things to work, while others flat out will not run. Use virtualbox to run a virtual Windows and install your software to the virtual machine.

I thought it was possible to install them with Wine? 

I tried VirtualBox before. It annoyed me, wasn't working good.

And for you all saying just use OpenOffice. It's not that simple. The website used for exams requires IE.

---

### Post by HermanAB on 2009-08-09
Crossover (the leading version of WINE) is cheap and works really well with MS Office and IE.  So, head over to [http://codeweavers.com](http://codeweavers.com) and get it.

---

### Post by sydbat on 2009-08-09
> **donkyhotay said:**
> You may not need IE or office depending on the class. You have to be careful (it is your education after all) but I've taken classes online that stated they needed proprietary software including IE and office and I got by just fine using firefox and open office. I even had a teacher specifically state in the syllabus to not use open office, I used open office and just made certain I saved in .doc format and she never knew the difference (it was a writing class). Definitely have a backup plan (as mentioned a virtual manchine is one of the best backup options) but unless the online class software does't work in firefox (no way to know until you use it) or if the class is about learning the ins/outs of MSoffice you can probably get by with FOSS alternatives. As I said before though, this is your education and you don't want to mess it up so make certain you know all your options and a way of using what the teacher requests in case it doesn't work.Best answer.

> **steigerjb said:**
> I thought it was possible to install them with Wine? 

I tried VirtualBox before. It annoyed me, wasn't working good.

And for you all saying just use OpenOffice. It's not that simple. The website used for exams **requires IE**.Are you positive? As other discussions in this forum have pointed out, often something is "required" but turns out to not really be the case. For example, so-and-so website 'requires' IE to work, yet any other browser has no problem.

Also, if they really do need you to use IE to write exams, I would worry more about the hackability of their website for changing grades, etc. Who knows...you might think you answered everything correctly (and maybe even did) and still find out that you unexpectedly did not pass (or someone else was mysteriously elected)...

---

### Post by presence1960 on 2009-08-09
> **steigerjb said:**
> I thought it was possible to install them with Wine? 

I tried VirtualBox before. It annoyed me, wasn't working good.

And for you all saying just use OpenOffice. It's not that simple. The website used for exams requires IE.

then why fix something that isn't broken? you have a perfectly good dual boot set up that allows you to use IE & MS Office. So why all the problems? Don't let your ego or others view of you because you are using windows get in the way. That's the only reason I can come up with since you have provided no valid reason to not want to use your dual boot which will allow you to do your school work and still use Ubuntu for everything else. I just don't get it!

---

### Post by steigerjb on 2009-08-10
> **HermanAB said:**
> Crossover (the leading version of WINE) is cheap and works really well with MS Office and IE.  So, head over to [http://codeweavers.com](http://codeweavers.com) and get it.

hey, that could work. I could probably then get Window Media player and iTunes too. They digital copy in dvds won't play in Ubuntu. I have restart my computer...go into Windows, to watch a movie = hastle.

[QUOTE=CrossOver Linux Requirements]Linux distribution (32 bit, or 64 bit with 32 bit compatibility library installed)
Tested on

    * Ubuntu 8.04/8.10[/QUOTE]

hmm, anybody know if it works under 9.04 and 9.10?

---

### Post by Zill on 2009-08-10
steigerjb:  It seems to me that your primary requirement is to run Windows applications.  As you have apparently already paid the "Windows Tax" and bought Windows then why not just use it?

Linux is *not* Windows.  If you want to upgrade to Linux, and use Linux apps, then please go ahead, but just don't expect it to easily run Windows apps!

---

### Post by Paddy Landau on 2009-08-10
> **steigerjb said:**
> What I need is:

Internet Explorer
Microsoft Office 2007
...
Safari
...
Media Player
Those are Windows programs. Use Windows to run them. You'll just cause yourself grief trying to run them on Ubuntu.

---

### Post by Mark Phelps on 2009-08-12
You didn't say what version of IE the site demands.  If it's version 7, or worse, 8, you're most probably out of luck -- even with Crossover.

I downloaded their trial recently, specifically to check out IE7 and IE8 -- because I have a similar requirement.  IE7 hardly worked at all; IE8 didn't work, period.  I contacted CodeWeavers and they confirmed my experiences, saying that they were aware of the IE7 problems (but it would be MONTHS before they had a new version out that DID work), and that their product was not advertised as working with IE8.

So, as others have said, if you need to use MS Windows stuff, stick with dual boot.

---

### Post by Terl on 2009-08-12
Honestly, the best advice is: if you have to run windows software it is best to just run windows.  Since you already have windows I don't see the issue.  If the class requires you to use office 2007 you probably should do so and since it runs bewst under windows; just dual boot.

I use Ubuntu for lots of things but if I need a windows program (like a game for example) I just boot into windows.  I know it is a pain sometimes but, even as good as Wine and Cedega may be, a windows app performs best in windows.

I am not a windows fanboi, just pragmatic.

---

