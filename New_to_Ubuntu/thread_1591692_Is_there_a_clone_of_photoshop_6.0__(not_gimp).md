---
title: "Is there a clone of photoshop 6.0 ? (not gimp)"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-09
Hello,

I removed windows, and miss some apps, now full linux. Gimp is ok, fine to work, but photoshop was far better. Has someone made a pure identical clone ?

---

### Post by ronnielsen1 on 2010-10-09
If you have photoshop 6, you should be able to run it in wine. It's rated silver
> What works
I have PS6 up and running well under Wine 1.1.16 ,  pretty much as stated on this Web site. But under the latest Wine version available to me (1.1.42) on another machine, there seems to be some regression (see below). 
Almost everything seems to work however.


What does not
When opening a PhotoShop plug-in, those plug-ins which normally provide a preview of their adjustments, in the form of a detailed image, fail to do so now. Plug-ins which ship with PhotoShop, and which only provide a preview several pixels on edge, continue to provide this preview.
Even without the previews, it's possible to apply the effects of a plug-in without apparent problems, to the layer chosen within the image.
But if one can't see the preview, to apply plug-ins becomes guesswork, and affacts the feasibility of actually using the program.
I suspect that this is some kind of memory sharing issue. 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=88](http://appdb.winehq.org/objectManager.php?sClass=version&iId=88)

---

### Post by MattBD on 2010-10-09
Short answer: No
Long answer: Kind of... [GIMPShop]("http://www.gimpshop.com/") is basically a version of GIMP hacked around to work more like PhotoShop. I don't imagine it's an exact clone but it may be close enough for your needs.

It's not in the repositories, but they do offer a DEB package which should be easy enough to install in Ubuntu - once you've downloaded the package just right-click on it and select the option to open it using the GDebi package installer.

---

### Post by jcolyn on 2010-10-09
> **MattBD said:**
> Short answer: No
Long answer: Kind of... [GIMPShop]("http://www.gimpshop.com/") is basically a version of GIMP hacked around to work more like PhotoShop.


I wouldn't bother with GimpShop. Since it has not been very well maintained it has issues.

If the OP likes PhotoShop v6.0 and v7.0 will run fine in wine.

I would suggest copying the content of the install CD to a temp directory in his /home directory then cd to the directory and run ```
wine photoshop(version).exe
``` from there..

---

### Post by amjjawad on 2010-10-09
So only version 6.0 or 7.0? what about CS2??

---

### Post by MattBD on 2010-10-09
> **amjjawad said:**
> So only version 6.0 or 7.0? what about CS2??

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)

---

### Post by Mark Phelps on 2010-10-09
> **amjjawad said:**
> So only version 6.0 or 7.0? what about CS2??

Instead of asking, you should go look it up ...

Linked page is below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=17")

---

### Post by amjjawad on 2010-10-09
> **MattBD said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631)

> 
What does not
Image Ready


Great, I use them both at the same time so ... guess I have to keep WinXP ;)

---

### Post by amjjawad on 2010-10-09
> **Mark Phelps said:**
> Instead of asking, you should go look it up ...

Linked page is below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=17]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=17")

I didn't know ASKING is bad!

---

### Post by MattBD on 2010-10-09
> **amjjawad said:**
> I didn't know ASKING is bad!

It can be frowned on some Linux forums where someone asks a question that could be solved with a simple Google search. Ubuntu is one of the friendlier Linux forums, however - on some forums you'd just be told to google it, possibly with rude words included.

Nonetheless, if you have an issue with Ubuntu, doing a Google search is always a good idea before you ask a question as it's very often the quickest way to get an answer.

---

### Post by honeybear on 2010-10-09
wow guys, I hope this project will raise and replaace gimp in the repos to get it in our repos
> 
GIMPshop is a modification of the free/open source GNU Image Manipulation Program (GIMP), intended to replicate the feel of Adobe Photoshop. Its primary purpose is to make users of Photoshop feel comfortable using GIMP.

It shares all GIMP's advantages, including the long feature list and customisability, while addressing some common criticisms regarding the program's interface: GIMPshop modifies the menu structure to closely match Photoshop's, adjusts the program's terminology to match Adobe's, and, in the Windows version, uses a plugin called 'Deweirdifier' to combine the application's numerous windows in a similar manner to the MDI system used by most Windows graphics packages. While GIMPshop does not support Photoshop plugins, all GIMP's own plugins, filters, brushes, etc. remain available

---

### Post by Vaphell on 2010-10-09
and most likely google will point to a thread on ubuntuforums that covers the topic extensively :)

about the gimpshop: i don't see how pretending to be something else is so cool. Maybe by the same logic ubuntu should have a look&feel of windows?

---

### Post by DogMatix on 2010-10-09
Although its not exactly a Photoshop clone there is the browser based Pixlr which is available here [Pixlr]("http://pixlr.com/editor/")

Although, as a professional user of Photoshop. I started using GIMP on my travels on a Ubuntu lappy for photo editing and recently fully edited a set of holiday photographs using it with admirable results. It does take a bit of getting used to though. But the price is great!

---

### Post by amjjawad on 2010-10-09
> **MattBD said:**
> It can be frowned on some Linux forums where someone asks a question that could be solved with a simple Google search. Ubuntu is one of the friendlier Linux forums, however - on some forums you'd just be told to google it, possibly with rude words included.

Nonetheless, if you have an issue with Ubuntu, doing a Google search is always a good idea before you ask a question as it's very often the quickest way to get an answer.

This is NOT the first time that someone here reply with a rude manner/words.
Anyway, just to be clear, this forum is my HOMEPAGE on both Chrome and Firefox on each and every OS I install because I love it and the reason why I'm so much attached now to Linux is because of this forum. If this place is not that much friendly as I thought, I might take your advice and change my homepage to google :)

Thank you!

P.S.
I have no issue with Ubuntu, I love it but sometimes people forget that at some point, there were newbies!

---

### Post by jcolyn on 2010-10-09
> **honeybear said:**
> Hello,

Gimp is ok, fine to work, but photoshop was far better.

If you get to know Gimp you would change your mind.

Gimp + UFRaw is far better than PhotoShop + ACR when working with camera raw files. In addition Gimp + UFRaw does not have the bloat that PhotoShop + ACR has.

---

### Post by jtarin on 2010-10-09
> **amjjawad said:**
> This is NOT the first time that someone here reply with a rude manner/words.
Anyway, just to be clear, this forum is my HOMEPAGE on both Chrome and Firefox on each and every OS I install because I love it and the reason why I'm so much attached now to Linux is because of this forum. If this place is not that much friendly as I thought, I might take your advice and change my homepage to google :)

Thank you!

P.S.
I have no issue with Ubuntu, I love it but sometimes people forget that at some point, there were newbies!He did not reply with rude manner or words....what he stated is commonly known on the internet and in Linux forums. It follows the old adage of "Give a man a fish he eats for a day...Teach a man to fish and he eats for life". Using [www.google.com/linux](www.google.com/linux) is one of the most powerful tools you have in Linux. I attribute my knowledge of Linux more to google than a direct forum request, with google I never had to wait for hours,days or never to find a solution. Try not to be offended as manner does is not always interpreted correctly across the internet and from culture to culture.In times past a newbie was told to "RTFM". Now you have someone reading it for you.:)

---

### Post by MattBD on 2010-10-09
> **amjjawad said:**
> This is NOT the first time that someone here reply with a rude manner/words.
Anyway, just to be clear, this forum is my HOMEPAGE on both Chrome and Firefox on each and every OS I install because I love it and the reason why I'm so much attached now to Linux is because of this forum. If this place is not that much friendly as I thought, I might take your advice and change my homepage to google :)

By and large the Ubuntu Forums are a friendly place - certainly compared to some of the other Linux forums. However, as with any forum the same questions will arise time and time again, so it's always worth trying a Google search first.

Two excellent pieces about getting answers to your questions are [https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers) and [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

Please don't be discouraged from using Ubuntu or participating in this forum - no-one wants to drive people away. But please also bear in mind that we like challenging, interesting questions where people have clearly done their best to solve the problem themselves. No-one wants to answer the same question over and over again when the answer's already out there.

---

### Post by MattBD on 2010-10-09
> **Vaphell said:**
> about the gimpshop: i don't see how pretending to be something else is so cool. Maybe by the same logic ubuntu should have a look&feel of windows?

In the case of Photoshop, I think many of the people who use it have done so for years and are so used to the way it works that learning to use something as radically different as GIMP can be a real uphill challenge because it disrupts their workflow. I imagine most people who use Photoshop and don't want to change to GIMP are power users who've invested a lot of time in it (after all, you don't shell out the rather high price for a legitimate copy of Photoshop unless you're at least halfway serious about using it), since GIMP will do perfectly fine for people who just want to swap people's heads round in a photo.

---

### Post by jtarin on 2010-10-09
I first used Photoshop and Gimp for Windows before coming to Linux (Gimp 0.097). While Photoshop has a learning curve as does the Gimp....I have spent more time now with the Gimp than I ever did with Photoshop and cannot see going back for the work that I do.

---

### Post by Vaphell on 2010-10-09
> **MattBD said:**
> In the case of Photoshop, I think many of the people who use it have done so for years and are so used to the way it works that learning to use something as radically different as GIMP can be a real uphill challenge because it disrupts their workflow. I imagine most people who use Photoshop and don't want to change to GIMP are power users who've invested a lot of time in it (after all, you don't shell out the rather high price for a legitimate copy of Photoshop unless you're at least halfway serious about using it), since GIMP will do perfectly fine for people who just want to swap people's heads round in a photo.

replace Photoshop with Windows and GIMP with linux and read it again
or replace PS with MSOffice and GIMP with OO.org
that text of yours doesn't become any less true

there is always someone unhappy about old habits not working after conversion and workflow being disrupted (at least temporarily) but being an inferior copy of a famous product doesn't do much good for the copycat, as it will be criticized so much more for every, even the tiniest deviation from the 'standard' (something like the uncanny valley effect of software)

---

### Post by MattBD on 2010-10-09
Yes, Windows power users are often the people who have the hardest time switching to Linux because they're set in their ways. Ditto people moving from MS Office to OpenOffice - if you only use Office to write the odd letter, you can more quickly make the transition than if you're an expert user who uses advanced features like macros and VBA.

---

### Post by iMisspell on 2010-10-09
> **honeybear said:**
> Hello,

I removed windows, and miss some apps, now full linux. Gimp is ok, fine to work, but photoshop was far better. Has someone made a pure identical clone ?

Maybe this will help you in the future:
_[http://linuxappfinder.com/alternatives?search_text=Photoshop](http://linuxappfinder.com/alternatives?search_text=Photoshop)_


_

---

### Post by ronnielsen1 on 2010-10-10
> It can be frowned on some Linux forums where someone asks a question that could be solved with a simple Google search. Ubuntu is one of the friendlier Linux forums, however - on some forums you'd just be told to google it, possibly with rude words included.

PCL anybody?

---

### Post by honeybear on 2010-10-11
> **ronnielsen1 said:**
> PCL anybody?

pcl?? what is it ?

---

### Post by MattBD on 2010-10-11
> **honeybear said:**
> pcl?? what is it ?

Probably PCLinuxOS - although I would have thought that as a relatively beginner-oriented distro, PCLinuxOS should be fairly friendly.

---

### Post by oldsoundguy on 2010-10-11
Yes, there is nothing that replaces image ready per se.

Just as there is absolutely NOTHING that comes close to Lightroom or Tiffen Filters plug in

But CS2 WILL work in Wine (including Adobe Bridge).. just remember that you are adding another operational layer when you do so, and with the absolute bloat of anything ADOBE .. do not expect it to be blazingly fast by ANY means .. I mean it is SLOW in Windows, so do NOT expect it to be FASTER running in Wine in Linux!!  Physical impossibility!

PERSONALLY .. Adobe and my huge stash of photography programs are the only reason I keep a SEPARATE Windows machine around!  Absolutely EVERYTHING else is done via Ubuntu!

---

### Post by scradock on 2010-10-11
> **honeybear said:**
> pcl?? what is it ?
politically-correct language, perhaps?

---

### Post by beew on 2010-10-11
> **Vaphell said:**
> replace Photoshop with Windows and GIMP with linux and read it again
or replace PS with MSOffice and GIMP with OO.org
that text of yours doesn't become any less true

there is always someone unhappy about old habits not working after conversion and workflow being disrupted (at least temporarily) but being an inferior copy of a famous product doesn't do much good for the copycat, as it will be criticized so much more for every, even the tiniest deviation from the 'standard' (something like the uncanny valley effect of software)

+ 100 to that. Take the words out of my mouth.

---

### Post by ronnielsen1 on 2010-10-14
> Probably PCLinuxOS - although I would have thought that as a relatively beginner-oriented distro, PCLinuxOS should be fairly friendly.

Not that the distro isn't user friendly but the forums seem to have a tendency to adopt the RTFM mentality

---

### Post by scottuss on 2010-10-14
> **honeybear said:**
> Hello,

I removed windows, and miss some apps, now full linux. Gimp is ok, fine to work, but photoshop was far better. Has someone made a pure identical clone ?

No.

---

### Post by nikstard on 2010-10-14
I assume that you had a working, legit (you're not a pirate, are you?) copies of Windows and Photoshop, which you decided to just uninstall, and now you are asking whether there is a clone of some program that you already had, but for some reason decide not to use. I have no idea why you would a) uninstall working programs or b) assume that there are clones of as complex software as Photoshop is.

---

### Post by honeybear on 2010-10-15
> **scottuss said:**
> No.

Actually Linux is serious about this concern. It touches a lot of persons, imagine that you can make gimpshop clone a great software ,you bring all around a huge amount of mac os x users to linux: Do you think that there is only 1 or 2 guys using photoshop? - no, its tremendous the number of photoshop users. 

I would recommend you to check: 
 
[http://www.gimpshop.com/](http://www.gimpshop.com/)

---

### Post by ElSlunko on 2010-10-17
GIMP sounds fine for your needs if you're willing to take time to learn it. I've been doing my photography work in Linux for a couple of years now. I can't speak for design though. Everytime I see a colleague working on design and very heavy post processing I'm not sure if the toolset available in Linux is up to par.

---

### Post by amjjawad on 2010-10-17
The day that people stop using Photoshop is the day when a better software is found and available. Until that day, Photoshop is and will remain the most powerful software in whatever it does and capable of.

---

### Post by Vaphell on 2010-10-17
pros who absolutely need specific tools are 1% of population and if they are making a big buck using the professional tools, they certainly can afford to pay their hefty price. It's a fair deal. We can only blame Adobe et consortes that they don't feel like porting their productivity software to linux.

---

### Post by jtarin on 2010-10-17
It's all dependent on specific usage.....you can use a hammer to crack walnuts or build a magnificent house. Tools in the hands of a worker are only as good as the skills of that worker. I can only think of one specific that Gimp doesn't have for my own personal usage and that is CMYK as it relates to printing, but there is support in the stream and improvments in the work. Other graphic fields have their own specific needs. To my mind ....Photoshop is a lumbering giant that I have used in the past until I learned how to use the Gimp for my needs.

---

### Post by amjjawad on 2010-10-18
> **jtarin said:**
> 
It's all dependent on specific usage.

Tools in the hands of a worker are only as good as the skills of that worker. 

Photoshop is a lumbering giant that I have used in the past until I learned how to use the Gimp for my needs.

I couldn't agree more :)

---

