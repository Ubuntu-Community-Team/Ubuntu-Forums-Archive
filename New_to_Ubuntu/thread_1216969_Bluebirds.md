---
title: "Bluebirds ???"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-18
i have 9.04 installed and it's doing fine except the normal set up woes... i bought the disc on ebay and it is 32 bit... the ebay listing said extra bonus program included...

the bonus is called "bluebirds"... when i look at it it only shows autorun.inf, bluebirds, drag & burn, and setup (all .exe's) and no readme or anything similar...

does anybody know what bluebirds is ???

thanks...

---

### Post by lisati on 2009-07-18
I don't think it's one of our feathered friends that has been left out in the cold or a [bluebird]("http://en.wikipedia.org/wiki/Bluebird").

There are quite a few possibilities.

I found [this]("http://mac.softpedia.com/get/Internet-Utilities/Bluebird.shtml"), but it's for OS X

I also found [this screensaver]("http://bluebirds.findmysoft.com/")

---

### Post by ad_267 on 2009-07-18
If they're all .exe's it sounds like it's a Windows application, not anything that will run on Ubuntu (unless you use Wine).

---

### Post by NOTAGEEK on 2009-07-18
> **lisati said:**
> I don't think it's one of our feathered friends that has been left out in the cold or a [bluebird]("http://en.wikipedia.org/wiki/Bluebird").

There are quite a few possibilities.

I found [this]("http://mac.softpedia.com/get/Internet-Utilities/Bluebird.shtml"), but it's for OS X

I also found [this screensaver]("http://bluebirds.findmysoft.com/")


no help with those but thanks... that drag and burn.exe has me thinking...

---

### Post by NOTAGEEK on 2009-07-18
> **ad_267 said:**
> If they're all .exe's it sounds like it's a Windows application, not anything that will run on Ubuntu (unless you use Wine).


yes, thats what i thought, but why would a distro put windows stuff on a 9.04 install disc ???

---

### Post by Didius Falco on 2009-07-18
See if this link helps:

[http://www.msfn.org/board/index.php?showtopic=135300&st=0](http://www.msfn.org/board/index.php?showtopic=135300&st=0)

Regards,

Didius

---

### Post by lisati on 2009-07-18
Found this: [http://lgknowledgebase.com/kb/index.php?View=entry&EntryID=6271](http://lgknowledgebase.com/kb/index.php?View=entry&EntryID=6271)
Seems to relate to the same thing that Didius Falco is referring to.

---

### Post by NOTAGEEK on 2009-07-18
> **Didius Falco said:**
> See if this link helps:

[http://www.msfn.org/board/index.php?showtopic=135300&st=0](http://www.msfn.org/board/index.php?showtopic=135300&st=0)

Regards,

Didius

hey---something tells me we might have a bingo !!! brand new pc with lg opti drive---hmmmmm...

thanks...

---

### Post by Didius Falco on 2009-07-18
Happy to help out!

Regards,

Didius

---

### Post by NOTAGEEK on 2009-07-18
> **lisati said:**
> Found this: [http://lgknowledgebase.com/kb/index.php?View=entry&EntryID=6271](http://lgknowledgebase.com/kb/index.php?View=entry&EntryID=6271)
Seems to relate to the same thing that Didius Falco is referring to.


yep---i kinda remember seeing that... i think its time to close this thread... 

thanks everyone...

---

### Post by wild_oscar on 2009-07-24
How does one proceed to install the new firmware on Linux, though? I only have Ubuntu installed on this machine!

---

### Post by caue.rego on 2009-07-31
Also found this: [http://www.tomshardware.com/forum/267609-31-solved-supply-sata-burners#t1960786](http://www.tomshardware.com/forum/267609-31-solved-supply-sata-burners#t1960786)

But I wish to disable that freaking thing! It keeps staring at me. o_O

---

### Post by wild_oscar on 2009-08-04
> **caue.rego said:**
> Also found this: [http://www.tomshardware.com/forum/267609-31-solved-supply-sata-burners#t1960786](http://www.tomshardware.com/forum/267609-31-solved-supply-sata-burners#t1960786)

But I wish to disable that freaking thing! It keeps staring at me. o_O

If I don't find a solution I'll probably return the damn drive...

---

### Post by NOTAGEEK on 2009-08-04
> **wild_oscar said:**
> If I don't find a solution I'll probably return the damn drive...


now that i have done more research on this i have read somewhere else (no link) that an email to lg complaining about the situation gets a free opti drive w/out bluebirds overnighted to you... worth a try huh ???

it must be a qualifing drive and mine qualifies...  mine is lg model # gh22ns30...

bottom line: if you find bluebirds you need to complain...

---

### Post by caue.rego on 2009-08-04
I forgot to linkback to a small patch that does not solve the problem, but make the bird disappear! From linux at least.

[http://ubuntuforums.org/showpost.php?p=7572445&postcount=4](http://ubuntuforums.org/showpost.php?p=7572445&postcount=4)

---

### Post by vexorian on 2009-08-29
> **wild_oscar said:**
> How does one proceed to install the new firmware on Linux, though? I only have Ubuntu installed on this machine!
Since this is probably the first google result for bluebirds and Linux:

so far all I know is this: [http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50](http://www.lge.com/us/support/product/support-product-profile.jsp?customerModelCode=GH22NS50)

It would work in windows. Tried in virtualbox by making it connect directly to the burner, but no dice, apparently virtualbox won't allow such 'unsafe' operations with devices such as updating firmware.

I've read reports of success for removing this from Linux using  kvm but I couldn't try it yet. If you have dual boot, better go through the humilliant step of booting windows. If you do not have windows, you'll probably need virtualization such as kvm (but not virtualbox, unfortunately)

---

### Post by new fool on 2009-10-21
Very new to Ubuntu and Linux in general. So far I love it. I too am grappling with the bluebirds issue and in my google research found that we are NOT alone. I was going to physically take my drive out and hook it up to a  Windows pc and get rid of the pesky bird that way using the LG fix. I am thinking of trying Wine or another "emulator" called Crossover so I am disappointed to learn that Wine was not effective. Was that attempted through the gui or the terminal at root?
If there is any question as to the nature of this beast, bluebirds is a firmware adware and it constantly attempted to contact its mother ship and allowed a poisonous portal much like a root kit to freely invite its insidious little virusy friends...and just when I thought I had shrugged off the shackles of technodomination. I love the Ubuntu community spirit and I look forward to the day when I can be a better contributor of solutions. Best of luck!
[COLOR=Blue]GOOD NEWS! I WAS ABLE TO[/COLOR] [COLOR=Blue]PLUCK THAT BLUEBIRDS CRAP OFF MY PC WITH A FEATURE SIMILAR TO WINE CALLED "CROSSOVER". ONCE I HAD CROSSOVER PROPERLY INSTALLED IT WAS A PIECE OF CAKE. IT ALLOWED ME TO USE THE WINDOWS FIX FROM THE lg SITE. THIS WAS A LOT OF TROUBLE AND LOST TIME FOR ME OVER THE LAST FEW WEEKS AND I'M SO GLAD TO BE ABLE TO SHARE A SOLUTION.[/COLOR]

---

### Post by wild_oscar on 2009-10-22
I'm glad to hear it worked.

I only tried (without luck) the wine approach. Maybe I'll try that when I find the time.

---

### Post by caue.rego on 2009-10-22
> **new fool said:**
> Very new to Ubuntu and Linux in general. So far I love it. I too am grappling with the bluebirds issue and in my google research found that we are NOT alone. I was going to physically take my drive out and hook it up to a  Windows pc and get rid of the pesky bird that way using the LG fix. I am thinking of trying Wine or another "emulator" called Crossover so I am disappointed to learn that Wine was not effective. Was that attempted through the gui or the terminal at root?
If there is any question as to the nature of this beast, bluebirds is a firmware adware and it constantly attempted to contact its mother ship and allowed a poisonous portal much like a root kit to freely invite its insidious little virusy friends...and just when I thought I had shrugged off the shackles of technodomination. I love the Ubuntu community spirit and I look forward to the day when I can be a better contributor of solutions. Best of luck!
[COLOR=Blue]GOOD NEWS! I WAS ABLE TO[/COLOR] [COLOR=Blue]PLUCK THAT BLUEBIRDS CRAP OFF MY PC WITH A FEATURE SIMILAR TO WINE CALLED "CROSSOVER". ONCE I HAD CROSSOVER PROPERLY INSTALLED IT WAS A PIECE OF CAKE. IT ALLOWED ME TO USE THE WINDOWS FIX FROM THE lg SITE. THIS WAS A LOT OF TROUBLE AND LOST TIME FOR ME OVER THE LAST FEW WEEKS AND I'M SO GLAD TO BE ABLE TO SHARE A SOLUTION.[/COLOR]

Congrats!

And I wouldn't say it was a complete lost of time. At least now you have a nice emulator running, as it sounds, and you can run windows programs with ease. That oughta be good for something in the future. In some way.
Just remember there are few things on windows that are deeply connected with its kernel and its flaws that will never run in any linux kernel.

---

### Post by new fool on 2009-10-23
One more note on flashing through the use of crossover. The first time I flashed it just went dead...no lights no nothin. With little to lose I did it a second time and woo hoo...I'm up and running. Best of Luck
P.S. I really don't care about using windows programs anymore...I just needed a way to fix the drive. Thanks Linux!:KS

---

