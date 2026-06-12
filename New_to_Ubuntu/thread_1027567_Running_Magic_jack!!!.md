---
title: "Running Magic jack!!!"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by suhasdude on 2009-01-01
Hi Guys,
I was interested in running MagicJack(VOIP) on Ubuntu...i tried finding for answers...but the reply was it is not supported on linux....if  anybody has successfully installed it...plz help me out with it.
Regards,
Suhas:(

---

### Post by xenolalia on 2009-01-02
Hi!

These might be of help:

[http://ubuntuforums.org/showthread.php?t=511689](http://ubuntuforums.org/showthread.php?t=511689)
[http://ubuntuforums.org/showthread.php?t=893755](http://ubuntuforums.org/showthread.php?t=893755)
[http://blog.laptopmag.com/magicjack-inventor-plans-linux-support-improved-customer-service-and-more](http://blog.laptopmag.com/magicjack-inventor-plans-linux-support-improved-customer-service-and-more)
[http://www.broadbandreports.com/forum/r20977358-Successfully-setup-Ubuntu-Linux-VMWare-XP-MagicJack](http://www.broadbandreports.com/forum/r20977358-Successfully-setup-Ubuntu-Linux-VMWare-XP-MagicJack)

Good luck!
Xenolalia

---

### Post by hifly1231 on 2009-01-06
For anyone who's interested, although they don't have a specific date yet, I spoke with MagicJack day before yesterday, and they are in the process of developing a Linux driver as we speak.  They said that it will be out sometime this year.

---

### Post by bone2006 on 2009-02-27
What's their phone number?  So more of us can call.

It all has to do with supply and demand and most people think there's not enough demand for Linux users.  If more people called or show they want it if there's Linux support than they would sell more and have the drivers for Linux.

I have a question on what I really would like to know.  I am curious if they release a linux driver, would or could you use that driver on a router that is flashed with dd-wrt?
Because I have a router that has a usb port and I would love to not have to turn on my computer to use magic jack and just put it in the router.  When I'm traveling, it's nice to just put magic jack in my pocket and go on a trip and plug it into a laptop running ubuntu.

---

### Post by kirkmeaux on 2009-02-27
would loveto get my majic jack on m ununtu....I'm getting tired fo running windows just to use my phone.

---

### Post by Old *ix Geek on 2009-02-27
Definitely call or write and let MagicJack know that you're interested in a Linux version.  As I always say, it's up to us to let companies know that there's a market for Linux stuff!

---

### Post by David.UCE.IMG on 2009-03-03
Ubuntu Hardy

tried virtual box= no success

Vmware with a striped down XP worked without and modifications.

one xp was installed I inserted the magic jack and a few windows came up telling me it would stop linux from using the " usb drive" and allowed xp to see the Magic Jack ran the MJ install and was using a cordless plugged in the MJ with no problems. I keep vmware minimized on on of my desktops and use my phone all day long.

,Dave IMG

---

### Post by djuke04 on 2009-04-27
> **bone2006 said:**
> 
I have a question on what I really would like to know.  I am curious if they release a linux driver, would or could you use that driver on a router that is flashed with dd-wrt?
Because I have a router that has a usb port and I would love to not have to turn on my computer to use magic jack and just put it in the router.  When I'm traveling, it's nice to just put magic jack in my pocket and go on a trip and plug it into a laptop running ubuntu.

MagicJack will most likely not be able to run directly plugged into the router because of the processing it requires.  While it has "low system overhead" because it requires low bandwidth from the data connection, it uses a pretty decent amount of processing power.

At current, the MagicJack device cannot even plug into a USB Hub because of this exact same reason.  If another device attached to the hub were to suddenly demand too large of a portion of the bandwidth for the hub, it would cause problems with the functioning of the device.  While it is "booting up," the device checks to make sure it has it's own dedicated USB connection to the south bridge to avoid this exact sort of issue. 

I forced the device to pass this step and boot regardless of having a dedicated connection or not, and sure enough after a data transfer from a hard drive also connected to the Hub during a phonecall, the device froze up, or shut down, but just stopped working.  I had to reflash the device and lost all the contacts and other data saved within it.  

Another neat little trick I tried that has worked, is that if you are experiencing low sound or overall call quality, you can open up the task manager, right click on the "magicjack.exe" process and increase the priority of the process.  Also "COICmanager.exe" will help as well.  When they're both on high priority I've had nothing but perfect call quality, no drops, great sound etc etc.  

As far as getting it working in Linux goes, I've been SOL as well.  The closest I've come was with VirtualBox, but still couldn't make calls.  The device was recognized after I added my virtual xp machine to the usb group.  I can browse and find the autorun app, but I cannot get it to start all the way.  It displays the "one minute of patience" or whatever message and when it changes it disappears.  

C'mon Dan! (Dan  Borislow, magicjack maker) You can do it! Save us the messing about!

---

### Post by jimmy the saint on 2009-04-27
I know it isn't the same product, but I use Voipo for voip service.  It's cheap, I haven't had any problems (except that tomato needs to be finessed for some reason) and it runs independent of the computer.  Most of the time, if something doesn't play nice with linux I just look for something else.  Maybe majicjack has something special that I am missing though.  I've never tried it.

---

### Post by Jim Darrough on 2009-04-28
Quoted from:

[http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010](http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010)

Linux compatibility: Mac and PC users have been using magicJack for some time now, but Linux has been left out in the cold–but not much longer. According to Borislow, Linux compatibility should be available “3rd quarter of this year.”  This addition will be available to both current and new magicJacks.

Looks like things may be looking up.

Regards, Jim

---

### Post by Jago6060 on 2009-07-30
> **suhasdude said:**
> Hi Guys,
I was interested in running MagicJack(VOIP) on Ubuntu...i tried finding for answers...but the reply was it is not supported on linux....if  anybody has successfully installed it...plz help me out with it.
Regards,
Suhas:(

[https://lists.ubuntu.com/archives/ubuntu-users/2009-May/183765.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-May/183765.html)

---

### Post by egalvan on 2009-07-30
> **Jago6060 said:**
> [https://lists.ubuntu.com/archives/ubuntu-users/2009-May/183765.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-May/183765.html)

He's running MagicJack on a VIRTUAL MACHINE running XP...

Useful, yes, BUT

NOT the same as running MagicJack on Linux.

---

### Post by HtmlGifted on 2009-08-12
> **kirkmeaux said:**
> would loveto get my majic jack on m ununtu....I'm getting tired fo running windows just to use my phone.

dude i feel ya... switched to ubuntu completely.. was tired of microsofts bs upgrades.... now just need to see what i can do to get my magic jack software stripped down to work.. on ubuntu... am going to see what i can mesh together for a gdi package installer for the application...   but .. not liking the fact that when plugged in to usb drive.. it does not appear on my ubuntu.. need to solve this first..

---

### Post by edwardtilbury on 2009-09-18
wow, I'm surprised they're actually going to release drivers later this year, way to go.

After the drivers are out, then all I need to do is buy a US Robotics linux usb modem and I'll try faxing again :)

I was able to mess about with the port speed and turned off error correction, so that I could finally get faxing to work with my MJ on vista.

It's cool to see companies jumping on the linux platform.. 
Nvidia, US Robotics, HP, Magic Jack, this is great. I'll keep my eyes peeled for the news... 

Once it's out I can finally put linux on my last windows box.

---

### Post by Floppyjoe on 2009-09-19
I have it working on an older version of Ubuntu running an older version of VMware inside a virtual machine that has windows xp installed on it.  

It seems to work pretty good. Sometimes it's a little choppy. I have a slower high speed light connection.  The MagicJack works best when I am not using other resources.  It did not install itself automatically the first time and I had to go to my computer and find the drives that are built into it and double click on one of them to get it running.

Sometimes it stops working and then i just unplug it and plug it back in again.

---

### Post by ChadBJX on 2009-09-21
Well, this thread started back in January and now it's late September. I just came from the Magic Jack web site and they are still saying that you can't use Magic Jack with Linux. 
 
Somebody mentioned that the release might be in the last quarter of the year. I was hoping to verify that or at least add my name to the list of Linux users interested in their product but I couldn't find an email link or a contact phone number. If anyone has their email address or service phone number please let the rest of us know.
Thank you,

---

### Post by Ms_Angel_D on 2009-09-21
I just went here and Searched Linux

[http://www.magicjack.com/techchat/](http://www.magicjack.com/techchat/)
> Not yet.

We expect to offer Linux support the first quarter of 2010.

So maybe the are just still working on it.

---

### Post by ChadBJX on 2009-09-21
> **Ms_Angel_D said:**
> I just went here and Searched Linux

[http://www.magicjack.com/techchat/](http://www.magicjack.com/techchat/)


So maybe the are just still working on it.

I hope so, when I checked yesterday by scanning through the FAQ the only answer I found to the Linux question was NO.

Thank you,

---

### Post by pcapazzi on 2009-09-24
I just noticed on the MagicJack web site that:

"We expect to offer Linux support the first quarter of 2010."

Maybe there's hope. :)

---

### Post by LowSky on 2009-09-24
Looks like they are running behind

---

### Post by MasterNetra on 2009-09-24
Actually I emailed "dan@magicjack.com" and I was emailed back saying there wasn't any going to be released. The email is supposed to be the creator's email. So Idk.

---

### Post by lyndaj70 on 2009-10-01
I have magicjack up and running on virtualbox with windows xp but the sound is choppy.  Didn't do anything special to it just installed it.

talked to my sister on it to test she says I sound like I'm on a cell with really bad reception.

One thing I have noticed is that on virtualbox the usb use light stays lit.. could that be a clue?  Too much bandwidth going through the usb bus for virtualbox to handle?

I'm going to keep tinkering with it.. If there are any ideas I'm willing to try..

Peace, 
Lynda

---

### Post by TheBuzzSaw on 2009-10-01
Caution:

[http://broadband-nation.blogspot.com/2008/10/real-problems-with-magic-jack-is-majic.html](http://broadband-nation.blogspot.com/2008/10/real-problems-with-magic-jack-is-majic.html)

---

### Post by LowSky on 2009-10-01
that cation might explain why a Linux version has not been created. Us linux geeks know too much about our computers

---

### Post by lyndaj70 on 2009-10-01
Thanks for the link. As always when using an inexpensive service there are caveats. by dedicating a virtual computer to magicjack there is only so much information they can get however...

Peace,
Lynda

> **TheBuzzSaw said:**
> Caution:

[http://broadband-nation.blogspot.com/2008/10/real-problems-with-magic-jack-is-majic.html](http://broadband-nation.blogspot.com/2008/10/real-problems-with-magic-jack-is-majic.html)

---

### Post by lyndaj70 on 2009-10-01
> **LowSky said:**
> that cation might explain why a Linux version has not been created. Us linux geeks know too much about our computers

You're probably right.

---

### Post by lyndaj70 on 2009-10-01
For those concerned the MJ may be spyware, check this out. Haven't read it yet myself but it's supposed to be a reply..

[http://askbobrankin.com/magic_jack_good_or_evil.html]("http://askbobrankin.com/magic_jack_good_or_evil.html")

---

### Post by LewRockwell on 2009-10-01
we've only heard bad things about Magic Jack

and we're not afraid to repeat that

repeatedly

also beware of Trex decking material as there are multiple class-action lawsuits against the company for their insanely poor product and their continuing refusal to remove it from the marketplace

Lowes and other retailers are on the hook for millions of dollars worth of this defective-by-design decking product

as always, your mileage may vary, buyer beware, and buyer be aware

.

---

### Post by lyndaj70 on 2009-10-01
It may be buyer-beware, but myself and everyone I know who has used MJ has had no issues and find it well worth the twenty dollars a year spent on it.  

As with all things, they must be taken with a grain of salt.  Considering that this is a linux forum, and the purpose of this thread is to get MJ working on linux, why waste everyone's time slamming it?  If you don't like it, don't use it but don't harrass others who choose to.

---

### Post by LewRockwell on 2009-10-01
> **lyndaj70 said:**
> It may be buyer-beware, but myself and everyone I know who has used MJ has had no issues and find it well worth the twenty dollars a year spent on it.  

As with all things, they must be taken with a grain of salt.  Considering that this is a linux forum, and the purpose of this thread is to get MJ working on linux, why waste everyone's time slamming it?  If you don't like it, don't use it but don't harrass others who choose to.

it should be pointed out that it is important for others to contribute to these threads and posts, regardless of the content and context of their input

for example:

someone might title a thread "Lyndaj70 is wonderful"

then someone else might tell the story of how you saved a whale

then someone else might relate something not so savory...


hey, don't blame the messenger...information wants to be free!

.

---

### Post by alienclone on 2009-10-01
my suggestion for Magic Jack it to install it on that older pc sitting in the corner that doesnt get used.

---

### Post by lyndaj70 on 2009-10-01
Point taken Lew. 

Information is free, and that is what makes this forum, and this operating system so wonderful.

---

### Post by lyndaj70 on 2009-10-01
> **alienclone said:**
> my suggestion for Magic Jack it to install it on that older pc sitting in the corner that doesnt get used.
 That's what I've been doing, actually.  Trying to save electricity and space however.

I've got it working a lot better by increasing the RAM to the virtual machine and increasing priority on the processes.  Considering that I let most calls go to voicemail and return them when convenient, I can always fire up another computer in a pinch.

The goal is to avoid that, however... :)

---

### Post by swallacertp on 2009-10-05
According to MagicJack's KB/FAQ support for Linux is coming in 1Q 2010.

MagicJack KB: 

[http://www.magicjack.com/1/faq/](http://www.magicjack.com/1/faq/)

Question - Will magicJack work with Linux?
Answer - Not yet. We expect to offer Linux support the first quarter of 2010.

Date - Sept 18, 2009

---

### Post by lyndaj70 on 2009-10-05
> **swallacertp said:**
> According to MagicJack's KB/FAQ support for Linux is coming in 1Q 2010.

MagicJack KB: 

[http://www.magicjack.com/1/faq/](http://www.magicjack.com/1/faq/)

Question - Will magicJack work with Linux?
Answer - Not yet. We expect to offer Linux support the first quarter of 2010.

Date - Sept 18, 2009

Hey Thanks for posting this!  I'd heard the third quarter of 2009 and figured they had given up.  This gives hope!

---

### Post by HtmlGifted on 2009-10-05
> **Ms_Angel_D said:**
> I just went here and Searched Linux

[http://www.magicjack.com/techchat/](http://www.magicjack.com/techchat/)


So maybe the are just still working on it.

Thats Bs... they should Stick to there deadlines more... They need to give users access to the project so they are able to advance it out and make it The top quality it was heading for.....   To bad...... Thought about it...... let see  phone's usually $50 a month average for 12 months comes to 600 hundred for a year **** ya.. magic jack is way cheaper...  By 580 dolors in comparison.... Ya.. come on...... 

Just saying..

---

### Post by lyndaj70 on 2009-10-05
I wish they would stick to their deadlines as well Gifted. That MJ is the only reason I have Windows at all on my boxes, but I can't pass up the savings, especially for a phone I don't use that often.

Hopefully they will keep their word this time..

---

### Post by LewRockwell on 2009-10-05
wheeee!

look at all the hits we're getting via searches for "magic jack"

superduper!

.

---

### Post by lyndaj70 on 2009-10-05
I know it Lew! Ain't it great :popcorn:

---

### Post by IrishWristwatch on 2009-10-24
Does anyone know if there are there any other MagicJack-like devices for Linux?  Something that you could plug into your computer, and be able to make and receive phone calls with a handset.

---

### Post by anewguy on 2009-10-24
> **IrishWristwatch said:**
> Does anyone know if there are there any other MagicJack-like devices for Linux?  Something that you could plug into your computer, and be able to make and receive phone calls with a handset.

Yes....and no.  There is a box made by Yealink amongst others (check EBay and look for b2k like devices) that plug into a USB port and let you use any phone.  The trick is that it works with Skype.  So, to make calls to regular landlines, you'd have to purchase SkypeOut, but it's still cheaper than the POTS.  Also, for these boxes to work in Linux, you need some special software - check sourceforge.net for kb2kskype and for the apci that goes with it.

Used it for a while and it wasn't bad.

Dave :)

---

### Post by skompier on 2009-10-24
I haven't tried this but others have. This is in the Linux Forum.

[http://www.magicjacksupport.com/linux-softphones-t739.html](http://www.magicjacksupport.com/linux-softphones-t739.html)

---

### Post by eoraptor on 2009-12-10
Okay :) 

So let's see here.. read through all the posts... also have a magic jack. Let's see if anyone shares my opinions or experiences about the product. Sadly, currently I have found NO methods of running magicjack on ubuntu except through an entire virtual machine, which really defeats the purpose of trying to run the thing on ubuntu at all by adding a few layers of complexity to an otherwise very simple and reliable device. If you want to load magicjack via vmware or some other sandbox client, feel free, just don't expect the ease of use the plug&play device provides in mac and windows natively as of late 2009.

**1.) what IS Magic jack?**
It's a soft phone VoIP device the operates on a small flash client which it downloads the first time you plug the device into a USB port on your windows or mac-intel computer.

when I plug in the jack, I am presented a flash drive totaling 17 mb (windohs recognizes it as two drives for some partitioning reason) representing the device, named Magicjack and basically containing the lil downloader and storing the phone numbers I have set up already on it and politely admonishing you NOT to use magicjack as a flash storage drive. 

I've checked over the small program it downloads to your pc (for windows, it's located in "*x*:\Documents and Settings\*user*\Application Data\mjusbsp" in XP, and "x:\users\*user*\Application Data\mjusbsp" in Vista/7 and it currently seems to be a simple mostly flash-driven platform with DLLs to drive the USB device and allow it to interface with *gasp* your pc hardware; nothing so sinister as purported in the ***Broadband Reports*** article. That article seems to be a compilation of lies and half-truths. The rebuttal argument spells all those out nicely if you wish to delve into it.

2.) **how does MagicJack work**
The device itself is simple, an actually kind of nifty. it contains a printed circuit with a very bright blue LED, a flash chip (17 mb in current models) and a simple set of MODEM hardware to convert RJ11 telephone signals into USB for the softphone program and the PC. As a softphone, it runs off of your computer's CPU in the same way a softmodem or other "dumb" hardware does. The physical devices acts only to MODEM with a physical telephone and to house the magicjack downloader and your stored numbers. the software won't let you run the service without the jack plugged in, even though the softphone is actually resident on your PC. (I imagine some industrious soul could hack around this)  

the flash drive on the chip contains a simple autorun program that prompts the jack to search your PC for an internet connection, and then download the proper OS for your machine (currently PC or Mac only) (older devices actually came with a CD containing the OS, but now it operates entirely from the flash drive to call the internet for the proper and most current software version, presumably a cost cutting measure) This is possibly one of the limiting factors on no linux support yet. (other possibilities listed below) it also contains an XML file which holds your phone numbers for the quickdial functions of the software, so that they stay with you if you take the jack to another pc. (those of us born before 1990 remember how many phone numbers and address you can actually save on 17 mb of space, yes?) NOTE: the softphone is coded to look for the hardware device before unlocking and operating. 

you don't HAVE to utilize a physical phone for the service, only the hardware usb device to unlock the softphone. it has an option to enable you to use a headset via your laptop or desktop's jacks if you prefer, and the soft phone will dial just as effectively as the keypad on a phone plugged into the device, and in fact you can use the softphone to tone-dial a hard phone plugged into it. Magicjack will not operate through an unpowered hub BECAUSE it needs the juice provided by your USB port to drive its MODEM hardware and a physical phone attached to the device. because of this, some netbooks and some laptops which have only half-powered usb buses may experience problems, in which case you may need to purchase a powered usb hub to drive the usb device. (this is spelled out in a lil flyer packaged in current generation magicjacks FYI) I have had no problems using an el-cheapo corded phone with the device on my Acer 5610z even when on battery. 

the VoIP program establishes a connection to magicjack's system of servers and interchanges in order to make it an instant-on telephone. this is actually no different than a landline phone's operation, except that the first step of the process takes place over ported internet servers instead of POTS hardware. (POTS is an industry acronym meaning Plain Old Telephone System) from there, it hooks into a magic jack (as opposed to legacy phone company) exchange and connects to the existing POTS infrastructure of the US (and canada I presume as they are the same system)  Because the VOIP requires an Always-on connection to the magicjack exchanges, it will not function over dialup or satellite internet, because dialup does not provide enough bandwidth, and satellite internet is a capped-usage service that drops a shiteload of packets at times.

3.) **How does Magicjack make money?**
*IE, why is it so cheap, will prices suddenly skyrocket, is it a scam that will autodebit me, suddenly dissappear etc... *Through two venues. magicjack's primary business model is to operate off of something called CLEC fees. this is an incredibly obtuse concept, which Ill leave it to you to learn about on your own, but basically, the federal government and large telco's subsidize small telcos with CLEC fees because small telcos cannot afford their own lines, interchanges, etc to serve rural and suburban areas that, like cable tv, cannot be profitably served otherwise. this is actually pretty much the business modle most VoIP providers in the US operate on to some extent. An exchange is what provides you your phone number, and connects you to the greater POTS system, and since MJ has limited exchanges, you may not get a phone number which is local to you, though for a fee, you can purchase a "soft" phone number with any digits you wish that their servers will convert to a hard exchange number via internet routing magic.

It supplements this with contextual advertisements displayed in the softphone client. As of late 2009, these are pretty much all either informational for magicjack itself, or encourage you to expand your service through add-ons such as a 5-year renewal of service, hardware insurance, or purchasing of hardware for other PC's you own/to give as gifts. as the government looks to rework some of the ~very~ antiquated CLEC laws in the changing telecom landscape, look for the contextual ads to begin to take up more of the funding load from the CLEC fees. (this may also cause your renewal prices to rise) 

This lack of funding from service fees (like separate fees for caller-ID like features, line insurance, state and local excise  and franchise fees, etc), and the current low-penetration of linux PC's is probably the primary cause of a lack of Linux versions of the softphone, though with the rise of both linux and chrome/android OSs in netbooks and presumably on tablets, I'd really look for this to change in 2010 as it will mean a larger chunk of market share needing an option.

4.)** Bugs with the Magicjack**
As I listed above, its USB device has some high voltage requirements. This is not a huge concern, unless your PC/laptop runs a low-powered USB bus, or you have lots of unpowered usb devices like flash-drives or bus-powered devices like cameras and scanners plugged in. This may cause the sound on any physical phone plugged in to be quieter than you are accustomed to as that voltage is what makes the phone work. you're better off using a corded landline without caller-id to minimize how much voltage is drawn from the USB bus, or using a plugged in, ac-powered cordless phone that doesn't rely on phone lines for its power if you are running magicjack from your desktop and not a laptop.

Call quality is largely based on your network and internet connection, as well as the load on your CPU. Doubly so if you are using a headset instead of a physical telephone with the device. Single core processors and small amounts of ram can hamper your call quality if you are multi-tasking and/or using a headset and onboard audio. 

Magicjack doesn't put much load on your local network in my experience.. no more than any other audio-streaming service might. So if you have three people trying to stream movies to their PC's, that might afflict your call quality; but otherwise, don't look to your router as the source of your difficulties unless you already suffer difficulties with it and steaming/torrenting (I'm looking at you linksys wrt54g) 

the main cause of call quality issues, though, is usually going to be either your gateway, or the local end of your internet connection (IE the "last mile" between you and your service provider) this can cause widely varying levels of call quality based on local traffic levels. Once you're passed your "last mile" area, there are no call quality problems in my experience. Once out into the great expanse of the greater internet, the packet stream that constitutes your magicjack call shoots directly to the nearest exchange location and then dives into the realm of copper wire telephone, which we all know is pretty damned robust in this country. now obviously if you live in BFE alaska and your packets have to travel 200 miles to the nearest exchange, your quality might drag a bit, but in general, call quality is not the problem of the service so much as *local internet conditions. *

Also, the windows version of the magicjack client seems to have some minor memory leaks. These can of course be cured by unplugging the device, which forces windows to unload the softphone. These aren't major, but I notice that in windows 7, at least, hat the client would chew up memory if left on all night. thus far, the problem doesn't seem as bad with XP,and it's possible my results were caused not by the magic jack, but by some virus I contracted around the same time from other sources. I notice a minor memory drain in the XP client, but noting major or systemic. While the client COULD be better written, and come with an uninstaller; I really don't have a major problem with it, and for the price I am paying for the service, it's as good as/better than one might expect on a cost/benefit basis. Again, some knowledgeable hacker might be able to write a smoother client that didn't require the hardware device or ran smoother, but for what it is and the profit margins they are working with, it's serviceable enough.

**BE AWARE:** some gateways are starting to try to block the ports on which magicjacks and other VOIP phones operate. this is common amongst hotel's and libraries which offer free internet, in the same way they might block torrent traffic or other connection-heavy connections like streaming media. unlike the telco level, which the FCC carefully regulates for service blocking (currently), private service providers like hotels and libraries, which are essentially reselling the service to you, are legally allowed to do this, so you're on your own when traveling with a magicjack and trying to use it from such places. 

> MagicJack/SIP (MJ softphone client) always uses **[COLOR=red]source port 5060[/COLOR]**  --> **[COLOR=blue]destination  port 5070[/COLOR]** (MagicJack server) for all  registrations/requests.  Basically, 
SIP client always uses port 5060 to communicate with SIP server at port  5070.  SIP server always uses port 5070 to communicate with SIP client  at port 5060.  RTP (real-time protocol) for actual VOIP call connection  uses a randomly assigned port between 10,000 and 65535. from [[http://www.magicjacksupport.com/what-tcp-ip-ports-does-mj-use-t813.html](http://www.magicjacksupport.com/what-tcp-ip-ports-does-mj-use-t813.html)]("http://www.magicjacksupport.com/what-tcp-ip-ports-does-mj-use-t813.html")of course, port 80 serves up the advertisements portion of the service.

---

### Post by TransitMan on 2009-12-11
Mind posting a link to the "**_*BROADBAND REPORTS*_**" article you are referring to.

---

### Post by bro brian on 2010-01-27
This is GREAT news! By the 3rd quarter of this year, magicJack should be coming out with a fix for Linux?. I'll look forward to this. I wonder if there will be some sort of download for it - Maybe in the Synaptic Package Manager or something?

---

### Post by bkratz on 2010-01-27
Seems like I remember seeing that same statement last year!

---

### Post by bro brian on 2010-02-20
> **bkratz said:**
> Seems like I remember seeing that same statement last year!
Well, I suppose you're right on that. Eventually, however, this MJ is gonna piss some hacker off just enough to where he/she will get down on it, and come up with a fix.
  May take another year.....

---

### Post by HtmlGifted on 2010-02-21
> **bro brian said:**
> Well, I suppose you're right on that. Eventually, however, this MJ is gonna piss some hacker off just enough to where he/she will get down on it, and come up with a fix.
  May take another year.....

I agree totally with you.. about some hacker getting pissed off...   All I know is that if it is able to run on vm ware and other virtual desktop[s.. why not make a gui usb loader that will auto run your usb device...  

I kay the changle down for any on e willing to except it.... I believe it might put Linux users on the right path to getting magic jack available to the gobs of Linux  users...

I figure 3 easy to do steps... 

1. Create a usb loader..

2. get wine compatible.  (best windows program operation. I found so far.) But have not played with vmware yet)

3. tap in to a voip client based on linux platform and alter it to match magic jack settings.. seems easy but could be a feet.. to accomplish..

This could be very easy... Just make a back up of your magic jack settings and load them in to your linix...  Then rip them apart to find the settings you need... Kinda a old hacker tick to get the information to improve the product. LoL..

---

### Post by gizmobay on 2010-02-21
MJs website says they're going to offer Linux support in Q1 of this year (2010) so hopefully in 5 weeks. I sure hope so as this is all I'm waiting on.

---

### Post by beckx020 on 2010-02-21
I hope they get the software out soon!  I need my MJ!

---

### Post by occams_beard on 2010-02-21
> **gizmobay said:**
> MJs website says they're going to offer Linux support in Q1 of this year (2010) so hopefully in 5 weeks. I sure hope so as this is all I'm waiting on.


I'll believe it when I see it.  Frankly, I think they're full of crap. Probably just have that on there to get Linux users to buy Magic Jacks, or just to keep interest up on the product. Before wasn't it supposed to be released in 2009?

It's all about supply and demand. Most consumer hardware companies couldn't care less about Linux, since it accounts for about 1% of the total market on the desktop. Sad but true.

---

### Post by masontgreen on 2010-02-23
[http://www.magicjack.com/6/faq/](http://www.magicjack.com/6/faq/)
It says Q1 2010, but that was last updated Sept. 18, 2009. Might just have to settle for cell phones for a while.:(

---

### Post by bone2006 on 2010-02-27
Saw this on their forum on how to get magic jack to run natively on Linux

[http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html](http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html)

---

### Post by hoopoo on 2010-03-07
magicjack on ubuntu 9.04  "VM" 3.1.4
I had magicjack running on a VM with windows xp pro
sort of but the sound was really choppy. 
after tweaking my network card to the max "not the VM card"
the sound got a lot better not as choppy and quite usable.

But my system seen magicjack as a default sound card
and  it took me three day of tinkering to get my audio back
and still no vlc player, all other players work.

I think if you can increase speed of your network card and
usb transfer speed of the VM  magicjack can be used
as for me I have magicjack runing on a old laptop now.

I hope this helps out someone.

---

### Post by go_beep_yourself on 2010-04-04
Magic Jack is not as great as it seems.

[http://broadband-nation.blogspot.com/2008/10/real-problems-with-magic-jack-is-majic.html](http://broadband-nation.blogspot.com/2008/10/real-problems-with-magic-jack-is-majic.html)

I was thinking about having a second computer running, no monitor to it to run xp with magic jack. This way I would not have to worry about magic jack working in Linux or spying on me.

---

### Post by conradin on 2010-04-05
in the windows, I use a firewall to log all the channges MJ makes. I have that someplace if anyone wants it. I still have had no luck running MJ in virtual box. the blue light turns on but still doesnt work.

A friend and i tried to decompile the software, but the level of obfuscation seems to be hardware deep. I like that it never actually checks to see if the phone is there. 

I also tried ripping the stream data, via ethereal. That was VERY interesting. 

what really needs to happen is some Uber geek makes an open source version of this thing.

---

### Post by efbatey on 2010-04-21
YEAR LATER since last post on MagicJack + Linux.  While back at SCALE 8X (2010) the PlugPC with Ubuntu showed up.  THOUGHT .. really neat IP telephone.  
 
SO Is Magic Jack or and other VOIP / IP Phone ware well ported to Ubuntu on very small PC?   Would really boost Ubuntu as well as the non-POTS phone wares accessibility.  
 
Hope someone still follows these older threads /  Everett efbatey AT gmail DOT com

---

### Post by mailman1175 on 2010-05-08
I just had a "live chat" tonight with "Jacob". He said their engineers are working on it "high priority". No timeline, though.

You'd think somebody in the linux community would come up with a similar solution...

---

### Post by kg4cna on 2010-05-09
> **mailman1175 said:**
> I just had a "live chat" tonight with "Jacob". He said their engineers are working on it "high priority". No timeline, though.

You'd think somebody in the linux community would come up with a similar solution...

Same here. I talked to "Eric" and he said exactly the same thing. Will be interesting to see if they actually go through with the linux version. I'd like to try it...but not going to put a Win 'puter in just for MJ.

A~

---

### Post by joeinbend on 2010-05-19
Hey guys I'm also very interested in MJ on Linux. My suspicion is that we will never see it, and here's why: MagicJack is $20/year because it is advertiser-supported. It doesn't take a lot of advanced calculations to figure out there's no way that the yearly subscription fees alone don't come anywhere near supporting their business; it's just not possible. They probably realize that once a software solution is released for Linux support, it won't take long for developers to quickly strip it down, wipe out their banner ads, and cause their advertising partners to cry foul and pull their advertising contracts.

They also realize there is a small community of folks who have successfully "sniffed" the SIP settings from the device/software so they can run it on a VoIP box such as the Linksys SPA-2102, thus circumventing all advertising. The Linux community is extremely savvy, and perhaps they decided if they give an obscure, "Yes we're working very hard on a Linux solution that will be available VERY soon!!", that will be enough to keep Linux dev's from putting the energy in to reverse-engineering their software and compiling a Linux driver compatible with any SIP software.

Just my two cents. I want to see Linux drivers too, but I strongly feel that it just wont happen, at least not underwritten by MagicJack.

My solution has been to take an old ultra-slim business desktop, install a stripped-down XP Pro, set it to auto login, set it to auto reboot every Sunday night (because we know freaking Windows has to do that... lame!). It sits quietly, headless, in my closet, works flawlessly, and I see no banner ads. A little QoS on my router ensures high quality calls even when my son is playing games or watching a Netflix Instant movie, and all is well.

---

### Post by luckylucky on 2010-05-25
I've been using voip exclusively for years; no POTS for me.  

I absolutely LOVE acanac, liked packet8, am anti vonage, and hate skype.  (based on price & features & quality)

MagicJack really caught my attention long ago, and again today after seeing an infomercial for it.  Sucks that I can't use it as I'm unwilling to run windoze just for this.

QUESTION

Is there something sorta-kinda like it that can run in ubuntu?  Cheap too?  


Another thing...  the post above was very interesting.  I speculate that you may be correct about the reasons for not releasing a linux version and keep teasing about it.  Perhaps it is time to just ignore their promises and delve into making our own version - wish I was a programmer to help on this.

---

### Post by darco on 2010-06-01
Question: I need a data jack only to upload information from a hand held scanner that my company requires me to do each nite.
With MJ, I am assuming I would just plug in the phone line from the scanner cradle and dial out and it should u/l the scanner info?
WHat is the actual cost for MJ? Is it just 19.99 per year and nothing else?
I have Mint 9 x64 and Win7 x64
thxs

---

### Post by joeinbend on 2010-06-01
Darco,
If you know someone who has MJ that you can test that configuration on before buying one, that would be ideal. MJ like a lot of the consumer-grade VoIP solutions aren't always Fax friendly, and although I realize what you are describing is not actually a Fax, the principals are similar.

MJ really is just $19.99 per year, and typically you buy the little USB device at Radio Shack, Walmart, Best Buy, etc, and it is $40, which includes 1 year of service.

I'm not familiar with "Mint", although I am guessing it is a Linux distro. MJ will not work with that (as you may have gathered if you have at least skimmed this thread), but it will work fine on Win7.

If you end up getting one, let us know how it goes.

---

### Post by coskierken on 2010-06-04
If you virtualize Win XX with VMWare Workstation, MagicJack works good.  I have did it with 9.10 and VM Workstation 6.5 and 7X running XP (tried it in Vista, but did not work as well).  I am going to test with Win7 in VMWare Player in the near future.  I might just load XP for this purpose and check, also.  It has worked with Virtualbox in the past, but not very well.  I will try to update post when I test. :popcorn:

---

### Post by joeinbend on 2010-06-05
Has anyone done this successfully with VMware Server or ESXi? I've never had good success with getting USB to pass thru in those environments.

---

### Post by deibu76 on 2010-06-05
I was able to get it to work fine in VMWare Player.

---

### Post by theOGRE on 2010-06-10
It's a real bummer that it doesn't work. I just talked my mom into letting me put Ubuntu on her system, so she could try linux. I planned on doing it this weekend actually. But if the MJ doesn't work it will be a deal breaker for her. I'll be watching this thread.

---

### Post by kraus3742 on 2010-06-13
I just spoke with a representative from MagicJack via Live chat and asked for a status update on their FAQ post about having Linux support in Q1 of this year.  I was told there was no more news and to watch the MJ website for updates.  Of course they understand our concerns and appreciated informing them. 

I would highly encourage all who have a MagicJack to contact them via live chat or however you can.  Let show them the growing Linux communities numbers and what type of market share they could potentially lose!  

I personally will reconsider using MagicJack after my year is up if they continue to resist supporting Linux!

---

### Post by deibu76 on 2010-06-20
> **kraus3742 said:**
> I personally will reconsider using MagicJack after my year is up if they continue to resist supporting Linux!

I've had the Magicjack for 2 yrs now, but I almost never use it.  They just auto-drafted me for a 3rd yr (they **DO NOT** bill you, so cancel before your year is up) so I guess I'm using it for another year.. LOL

I haven't used it in about 3 months... I haven't had a landline for 5 yrs so my cellphone is really all I need.  Also, I get good DL speeds (~12MBps/sec) but crap upload speeds with Time Warner Cable.  So, I can hear them w/o a problem, but they can only hear me clearly if I'm not using that bandwidth for anything else.

I'd cancel, but I do still find the Magicjack useful as a "backup plan" for those times when I need access to a phone and can't use my cell phone though...  

Over the past 2 years since I've gotten the Magicjack, it has come in handy a few times (battery dead, left the cellphone at a bar - called the bar w/ Magicjack the next day and they had it.. LOL!)  BUT, it really did come in handy last December when I was driving on I-26 to a client's office...  My engine started smoking, so I had to pull over to the shoulder.....  No cellphone that day (the speaker on it needed replacing, so I had left it at a Sprint store).  But, I DID have my laptop, and I brought my Magicjack and an old cheap crap Conair corded phone with me, just in case I needed it.  Luckily, there was wi-fi nearby, and I called a friend for help with the Magicjack!  

I don't keep Magicjack plugged in & I have to keep a WinXP box open most of the time anyway, for work-related apps, so the lack of a Linux driver isn't too much of an issue for me...  BUT, I'd still LIKE a Linux driver too; your suggestion to make our voices heard by contacting them via Livechat is a great idea - I'm planning to do that in just a moment!

---

### Post by joeinbend on 2010-06-20
Just to comment about your audio problems regarding the other end of your call not being able to hear your consistently: This is a QoS issue. SIP connections have a max overhead of about 80kb/sec, which even the slowest of connections can easily handle, but the issue comes in with packet prioritization. 

Even if you have a 4Mb/sec upstream, you will still experience call quality issues if you are moderately using your connection, because your  router does not "know" that certain packets need to be high priority. Most routers, even off-the-shelf Linksys routers, have such settings, and there are of course far more advanced traffic shaping options in high-end routers, and in the spirit of open-source, Linux-based homebuilt routers as well. 

In my personal use, I have a 5Mb down, 1Mb up connection, and without any traffic shaping, I only get good call quality with no internet activity at all. As soon as my son starts watching something on Hulu or playing his Xbox, call quality will start to degrade. With traffic shaping rules in place, I can be maxing out my connection in both directions with diverse traffic types, and calls never miss a beat, because the router is "told", anything matching "x" criteria gets absolute priority over anything else, both in allocated bandwidth, and (most importantly) transmission priority.

Not sure that this info will necessarily make you or anyone come running back to their MJ, but I thought I would pass this on, as it is a common issue with any VoIP / SIP traffic.

---

### Post by coskierken on 2010-06-22
Thanks for the update on working with VMPlayer.  I figured it would.  Next time I run by a store that carries them, I will pick one up.  I do use Skype (pay side to call regular phones) and have a balance left over, though.  ):P

---

### Post by frank cox on 2010-07-14
It seems that the best chance of ever getting it to work is with wine .When I tried it id did exactly what it did on Vista, ran and seemed to be installing and then flashed 
 "Warning must be Plugged into USB". I strongly suspect that the problem is the same . If I ever figure what the problem is in Vista I may be able to solve it on wine.
I have programs that run in wine better than they do in Windoze.

The fellow that figured our Esword in Ubuntu ,David zking I think his name is might be the one to ask. That is a much more complicated program than MJ and when he first started wine would not even try to run it so there is a head start with MJ.

---

### Post by powertower on 2010-08-28
Wanted to add my two cents. I'm using vmware esxi 4.1 with USB passthrough. Its unrecognized in ESXI so the device is not available for passthrough. 

My intentions are to buy a usb over ip adaper for 25 bucks. This may help others  trying to figure out how to get MJ working in older VM systems.

---

### Post by silverballer47 on 2010-09-15
Greetings everyone,

I got my MagicJack last week and have used VMWare Player on Lucid Lynx to get it working, which I have blogged about [here]("http://oracology.net/2010/09/magicjack-ubuntu-lucid-lynx-vmware-guide-and-a-rant/").

I've also written a note to MagicJack at the bottom of that post which describes my concern about GNU/Linux support as well as the awful documentation for the voicemail.

I'm happy to participate in a campaign to try and get these guys to accommodate us as real users of their product. If I knew how to get a hold of the inventor, I would send him my thoughts instead of blogging it and hoping he sees it...

Your thoughts appreciated.

---

### Post by jhanus10 on 2010-09-16
I have a question on what I really would like to know.  I am curious if they release a linux driver, would or could you use that driver on a router that is flashed with dd-wrt?
Because I have a router that has a usb port and I would love to not have to turn on my computer to use magic jack and just put it in the router.  When I'm traveling, it's nice to just put magic jack in my pocket and go on a trip and plug it into a laptop running ubuntu.[/QUOTE]

Now that would be awesome! It be smart of them to do so, but what about the monitor for contacts and such just forget about using it?

---

### Post by silverballer47 on 2010-09-16
I don't think it's going to work mate, simply because the MagicJack seems to require a fair amount of processing power from the host machine. I'm actually pleasantly surprised that I can have it running on a virtual machine with no slowdowns to my host Ubuntu system. I'm not sure a router would have the horsepower to run this thing. Or am I wrong?

The other problem is that it seems to be heavily tied into the software interface; of course we can get around this by building the appropriate software for GNU or dd-wrt or whatever, but till such time, it appears we're stuck using a virtual machine or using the MagicJack simply as a dongle to authenticate for softphones like Ekiga.

---

### Post by anewguy on 2010-09-16
Whille getting it running on a vm is commendable, nothing will be right until they truely release open drivers for Linux.

dave ;)

---

### Post by silverballer47 on 2010-09-16
Yes, precisely why I'm ready to join with people who want to take the fight to MagicJack to get the GNU drivers and software out.

---

### Post by kraus3742 on 2010-09-17
Well it appears magicjack isn't really concerned with Linux.  they posted one year ago that we could expect Linux drivers and support in Q1 of 2010 we that has con and gone.  

[http://service.liveperson.net/hc/s-61732089/cmd/kbresource/kb-8901354258023502064/view_question!PAGETYPE?sq=Linux&sf=101113&sg=1&st=914187&documentid=345414&action=view]("http://service.liveperson.net/hc/s-61732089/cmd/kbresource/kb-8901354258023502064/view_question%21PAGETYPE?sq=Linux&sf=101113&sg=1&st=914187&documentid=345414&action=view")

Disappointing is the only word.

---

### Post by Iwnda0 on 2010-10-15
> **kraus3742 said:**
> Well it appears magicjack isn't really concerned with Linux.  they posted one year ago that we could expect Linux drivers and support in Q1 of 2010 we that has con and gone.  

[http://service.liveperson.net/hc/s-61732089/cmd/kbresource/kb-8901354258023502064/view_question!PAGETYPE?sq=Linux&sf=101113&sg=1&st=914187&documentid=345414&action=view]("http://service.liveperson.net/hc/s-61732089/cmd/kbresource/kb-8901354258023502064/view_question%21PAGETYPE?sq=Linux&sf=101113&sg=1&st=914187&documentid=345414&action=view")

Disappointing is the only word.

This might make you all feel better about it...



Jaw: hi
Therese: Hello, how may I help you?
Jaw: Is Magic Jack Linux compatible yet?
Therese: No, as of the moment magicJack works with windows XP and higher and Intel MAC.
Jaw: Anything on the menu for linux in the future?
Therese: Further features and compatibility features with magicJack will be broadcasted once avialable.
Therese: That will be posted in our website.
Jaw: How long will we have to wait?
Therese: As of now we do not have word from our engineers for when this will be available, as of the moment we are also waiting news from them.
Jaw: K.
Jaw: Thanks.
Therese: You are welcome.
Therese: Is there anything else I may help you with today?
Jaw: My knee hurts.
Jaw: hi
Therese: Hello, how may I help you?
Jaw: Is Magic Jack Linux compatible yet?
Therese: No, as of the moment magicJack works with windows XP and higher and Intel MAC.
Jaw: Anything on the menu for linux in the future?
Therese: Further features and compatibility features with magicJack will be broadcasted once avialable.
Therese: That will be posted in our website.
Jaw: How long will we have to wait?
Therese: As of now we do not have word from our engineers for when this will be available, as of the moment we are also waiting news from them.
Jaw: K.
Jaw: Thanks.
Therese: You are welcome.
Therese: Is there anything else I may help you with today?
Jaw: My knee hurts.
Therese: This support channel is for magicJack issues only. May I know the exact nature of your problem with full details please?"
Jaw: Is magicjack myknee compatible?
Jaw: hi
Therese: Hello, how may I help you?
Jaw: Is Magic Jack Linux compatible yet?
Therese: No, as of the moment magicJack works with windows XP and higher and Intel MAC.
Jaw: Anything on the menu for linux in the future?
Therese: Further features and compatibility features with magicJack will be broadcasted once avialable.
Therese: That will be posted in our website.
Jaw: How long will we have to wait?
Therese: As of now we do not have word from our engineers for when this will be available, as of the moment we are also waiting news from them.
Jaw: K.
Jaw: Thanks.
Therese: You are welcome.
Therese: Is there anything else I may help you with today?
Jaw: My knee hurts.
Therese: This support channel is for magicJack issues only. May I know the exact nature of your problem with full details please?"
Jaw: Is magicjack myknee compatible?
Therese: MagicJack is only compatible with windows XP and Intel MAC 10.4.10
Jaw: I see you are abreast of the issue. Thank you!
Therese: You are welcome.
Therese: Have a nice day.
Jaw: Bye You as well.

---

### Post by wcdrotar on 2010-10-15
> **hifly1231 said:**
> For anyone who's interested, although they don't have a specific date yet, I spoke with MagicJack day before yesterday, and they are in the process of developing a Linux driver as we speak.  They said that it will be out sometime this year.

Yeah!  They had one coming out in a few months years ago.  They say that so Linux customers buy their products.  It's called lying.  

Does anyone know if Nettalk DUO works with Linux?

---

### Post by michael.l.burdett@gmail on 2010-10-16
**MagicJack contact (Voicemail) telephone number is:**
 
**_888-230-0060_**
 
-for those of you who want to add to the patrons of MagicJack that want to voice your desire and concerns for Linux-based VOIP use using MagicJack.
 
*_Additionally; you can voice your desires _*through the **_chat line @ MagicJack.com_**, _*too!*_
 
[EMAIL="michael.l.burdett@gmail.com"]michael.l.burdett@gmail.com[/EMAIL]

---

### Post by 3177 on 2010-10-18
I hope they get it done soon,
been waiting for almost 2 years now.

---

### Post by pinnacle65 on 2010-11-04
> **3177 said:**
> I hope they get it done soon,
been waiting for almost 2 years now.

I believe this site explains how? Doing whats on the article violates their TOS. I accept no responsibility if you lose your account  because you want to hack your Magicjack. The following is for  educational purposes only, and if you do this, you do so at your own  risk. 

[http://www.zimbio.com/Ubuntu+Linux/articles/2lPhOkJmRaW/How+Hack+MagicJack+Make+Calls+Any+SIP+Enabled](http://www.zimbio.com/Ubuntu+Linux/articles/2lPhOkJmRaW/How+Hack+MagicJack+Make+Calls+Any+SIP+Enabled)

---

### Post by CR4ZYC on 2011-02-11
As of now they still don't support Linux......   Maybe sometime this year...!:(

---

### Post by 1 d4 Nf6 on 2011-02-21
I too would like to use Magic Jack with Ubuntu. I left a message at Magic Jack's voicemail (888-230-0060) to let them know.

---

### Post by David2009 on 2011-03-28
I went to the Magic Jack website's FAQ today, and when asked if MJ works with linux they respond:

Not yet.

We expect to offer Linux support in the future.

---

### Post by parminides on 2011-04-07
> **wcdrotar said:**
> Yeah! They had one coming out in a few months years ago. They say that so Linux customers buy their products. It's called lying.

The do the same thing with number porting. It's been right around the corner for a long time.

---

### Post by regor210 on 2011-04-29
Im using Nettalk, its like MagicJack but it plugs in to my router. I gave up on waiting for MagicJack to support Ubuntu. Its portable, you can plug Nettalk into a computer if you like but I haven't tried it, I didn't see any software for Ubuntu GNU/Linux on there website. Works fine on my router and thats all I needed. 

[http://www.nettalk.com/](http://www.nettalk.com/)

---

### Post by beaucoder on 2011-06-16
Hi!!

Have you considered OOMA??  (ooma.com). I paid $169.00 for the VOIP hub (They discount it.) and pay $3.48 per month. Unlimited free long-distance in US. Your account is good for the life of the equipment. I estimate this will be 5-8 years. 

Works like a charm. Connect to modem and away we go. I use an old hand set. Fab voice quality. **Computer does NOT have to be on.** At my OOMA account I can see all activity on my voice mail. Or press a button to get voice mail via the hub. 

Get free cell phone service, too. I have an inverter which plugs into the car lighter. I hook up my modem, the OOMA hub and plug in my portable phone. *_**Bingo!!**_* Cell phone service. The portable is good for 100 to 300 feet from the car. (My CLEAR modem _has_ to have a cellphone tower in range. Otherwise, free cellular service. Pretty amazing.)

No luck with MagicJack so far. They still have not Linux drivers. This is June 2011. 

Super happy with OOMA.

beaucoder

---

### Post by rayred on 2011-07-17
Question from a newbie... is there a possibility that MagicJack can be run in a program such as WINE? 
I have read over this forum and I've yet to see if anyone has tried it (but I could have overlooked it).

Thanks!

---

### Post by wildmanne39 on 2011-07-17
> **rayred said:**
> Question from a newbie... is there a possibility that MagicJack can be run in a program such as WINE? 
I have read over this forum and I've yet to see if anyone has tried it (but I could have overlooked it).

Thanks!Hi, I have used it in virtualbox by installing windows in it then running it through windows on ubuntu. You will have to play with the settings to get good quality from it that way.

---

### Post by CR4ZYC on 2011-08-16
I tried wine... without any success. And Magicjack's website says that they do not support linux....

---

### Post by anewguy on 2011-08-16
About the only choices you have are running Windows in a virtual machine (+1 to virtualbox as mentioned by wildmanne39), dual-booting Windows so you have to be booted in Windows, or Windows with no Linux (some of us would prefer you at least have ubuntu! ;) ).  There is no native MagicJack for Linux, and I would say never will be given their "coming" to "not supported" support of Linux.  Wine would never be the method of choice for me at least.  I would use Linux as my OS, and run a virtual machine with Windows to run MagicJack.  That's IF your hardware is enough to really support a virtual machine - if not then dual boot with a very small Windows install just for MagicJack.

dave ;)

---

### Post by Detroit_Bad_Boy on 2011-08-18
> **wildmanne39 said:**
> Hi, I have used it in virtualbox by installing windows in it then running it through windows on ubuntu. You will have to play with the settings to get good quality from it that way.

Let's see if I have this right, install something in Ubuntu to run windows... hmmm. On my multi-boot system I can click windows (even tho I don't WANT to) and use magicjack.

Why not just put this issue on a shelf until enough of us ubuntu users send a message, en masse, to magicjack TELLING them to create a native driver??

---

### Post by anewguy on 2011-08-19
I personally was hoping that people wanting mj now would read this thread and realize there's no use in asking a question here - mj does not have a linux version.  While they previously indicated a Linux version would be coming, it is now down to linux not supported.  The chances of a linux version coming out are zero or less.  I believe a lot of users (though that's a relative term considering the installed base that actually wants mj in linux) have complained to mj - I think that's also why it says linux not supported.

---

### Post by anewguy on 2011-08-19
> **Detroit_Bad_Boy said:**
> Let's see if I have this right, install something in Ubuntu to run windows... hmmm. On my multi-boot system I can click windows (even tho I don't WANT to) and use magicjack.

Yeah, but with the VM in linux you don't have to reboot just to use something like MagicJack.  The VM is just another process running in Linux.

> Why not just put this issue on a shelf until enough of us ubuntu users send a message, en masse, to magicjack TELLING them to create a native driver??

See my previous post.  Pretty much this is a dead issue and people just need to move on to something other than MagicJack.  MagicJack requires a broadband connection to work worth a darn, so if you already have broadband why not try some of the other native linux apps for netphones?

---

### Post by Elfy on 2011-08-19
Closing thread.

Nothing appears to have changed in the life of this old thread.

When it does start a new thread.

---

