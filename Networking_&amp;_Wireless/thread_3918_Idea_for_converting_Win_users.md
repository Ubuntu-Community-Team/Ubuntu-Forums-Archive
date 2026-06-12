---
title: "Idea for converting Win users"
date: 2004-11-10
forum: Networking &amp; Wireless
---

### Post by kwennemar on 2004-11-10
I have just installed ubuntu and the desktop is real slick!  I am really impressed with all of the attention to detail that has gone into this project.  It detected all of my hardware and runs flawlessly, but....

I do not have a network connection.  I use dial-up ppp.  It is good to remember that most of the internet users still are on 56k or slower connections.  A dialer gui would be the most intellegent application to add.

---

### Post by jdong on 2004-11-10
try **gnome-ppp**, in the Universe repository...

---

### Post by HungSquirrel on 2004-11-10
Shouldn't it be included in the default install?

---

### Post by wallijonn on 2004-11-10
Computer -> System Configuration -> Networking -> Add

---

### Post by jwenting on 2004-11-10
[QUOTE=HungSquirrel]Shouldn't it be included in the default install?[/QUOTE]
 no, why should it be?
One of the nice things about this distro is that it doesn't include a gazillion tools and other stuff many people will never want.

If we go down the path of including everything someone might like in the general distro soon we end up like Debian with 7 CDs for the core distro alone.

---

### Post by JonAtkinson on 2004-11-10
Debian doesn't come on "7 CD's for the core distro alone". Debian isn't even designed to be distributed on CD, it just so happens that when they do release an ISO set it's nearly the ENTIRE repository.

You can install a working Debian system from a 75MB business card ISO image.

--Jon

---

### Post by ulrich on 2004-11-11
a gui/easy-to-find-and-use-configuration-tool is **ESSENTIAL** for a distro.
its not a hoochie-poochie-somewhat-fancy thing to give people a way to connect easily to the internet.

as wallijonn mentioned thats already implemented though half-hearted.

you can set up dialup, but wvdial isnt installed by default.
and a nice gui for people who want/need PPPoE wouldnt hurt either.

yeah i know that pppoeconf is there but who (if its a new user) should know about it?

---

### Post by HiddenWolf on 2004-11-11
The argument against PPPoeconf is that most people who need it should just put a router between their dsl and their pc.

I know that for many cheap xdsl connections, at least here in the netherlands, users do not have that option. many isp's integrate their modems in a usb-stick, so you can only use one pc.

So, I believe pppoe is essential, and a graphical tool very very much needed to provide some ease of use.
Took me ages of asking directions in winblows and booting to ubuntu to get my pppoe working.

---

### Post by HungSquirrel on 2004-11-11
>  no, why should it be?
One of the nice things about this distro is that it doesn't include a gazillion tools and other stuff many people will never want.
It should be because not everyone has broadband, especially outside the US.  One of Ubuntu's aims is to be a good desktop OS choice for any country in any language.  If most people don't have broadband, making dialup setup as simple as possible is a good idea.

---

### Post by Quark on 2005-01-07
[QUOTE=HungSquirrel]It should be because not everyone has broadband, especially outside the US.  One of Ubuntu's aims is to be a good desktop OS choice for any country in any language.  If most people don't have broadband, making dialup setup as simple as possible is a good idea.[/QUOTE]
 I am a WinXP user and for the first time yesterday, installed the Warty Ubuntu4.10 release that arrived on CD. For the last 12 or so hours I have been struggling to find a way of connecting to the Internet to no avail.

I went to Tucows and d/l a ppp programe but then couldn't read it from my CD, I could see it but that was it.

I use Wireless Broadband 1Gb connection and under XP use a pppeo dialer from WinPoET that passes my user id & password via my EtherCard and I am on line.

Where do I find that in Ubuntu, and yes I agree it will make the prog much more attractive to absolute newbies who have only a novice users experience with MS OS 

Cheers,
Quark

---

### Post by wallijonn on 2005-01-07
Quark,

I think you should have opened it up under a different thread or started another thread just to address this problem. You will probably get better response by inserting it in the Hardare / Networking section.

---

### Post by jdong on 2005-01-07
Actually, this discussion is more appropriate on the Ubuntu developers' list. ([http://ubuntuforums.org/forumdisplay.php?f=29](http://ubuntuforums.org/forumdisplay.php?f=29)).

Since it's not really possible to move a thread into a mailing list (never tried, really DONT WANT TO know what'd happen!), please start a new discussion there.

Include a link to the new discussion here as a reply. Then, I'll probably close this thread.

---

### Post by JD2 on 2005-01-07
Do yourself a favor and go with Mandrake. Ubunut on the hw side is not ready yet. I'm also a dialup user and I would gladly download however many disks it takes to have my ubunut linux work with my hw out of the box. I would gladly do it to prevent the hassle I had trying to get my modem working in ubuntu. Some people here think that a past window user should actually become a linux admin. Can you believe that? It's ridiculous and Mandrake is actually doing something to make the linux experience better and it's the reason why they're #1 on distrowatch.com and have been for some time. You see, you must have someone in your organization who understands the problems and then goes and solves them rather than dumping the problems onto their users like ubuntu does. Until you have this special person in your group nothing will get done and all other work is useless no matter how great it is. Priorities count, hw first apps second.

---

### Post by Quark on 2005-01-07
[QUOTE=wallijonn]Quark,

I think you should have opened it up under a different thread or started another thread just to address this problem. You will probably get better response by inserting it in the Hardare / Networking section.[/QUOTE]
 OK thanks.

Quark

---

### Post by machiner on 2005-01-08
What was that I saw during Ubuntu installation -- aaaah! that's right - the installer asks you if you want to set up networking and the default that I saw was for a ppp (modem) connection.

Now, if you're using a winmodem (unless you have an old ISA modem or a zoom modem the chances are terrific that you ARE) you're basically SOL. Those modems use windows to operate, that's why they cost $5.

good luck.

---

### Post by JD2 on 2005-01-08
machiner, I have a zoom pci modem that has a driver on the internet but not in ubuntu distro. There is also a problem of getting it to work correctly after a every reboot. Ubuntu detected my modem hw but failed to install the driver. Surely, you would be ticked off if a driver for your favorite hw wasn't in the distro. Say your network card driver? For me they're all useless, why does ubuntu even bother including high speed internet network drivers since rest of the world still lives on dialup? And it's the 3rd world countries that need linux the most. You see my reasoning? Either include all drivers or none. That way it's fair to everyone. No hw is prefered over another.

---

### Post by machiner on 2005-01-08
You are correct - I'd be pretty pissed.  I have tried other distros as well that make it difficult to connect to the web...for my needs ubuntu and pppoeconf worked fine.

I am sorry that I sounded so sarcastic - no offense intended and I hope some of the helpful folks here can help you -- I haven't run linux with a modem in years...why do you need zoom drivers? Can't you just let ubuntu see the hardware and load a necessary module?

You prolly already tried that - I know the fix for you is a simple one - I just cannot remember...

PS I DO NOT recommend Mandrake. It's got more bugs than aa screen door has holes.

If you want easy, quick, and pretty - go with fedora core 3. It's bleeding edge and a testbed for new RedHat releases, but it's pretty damned stable.

---

### Post by tiiim on 2005-01-08
[QUOTE=jdong]try **gnome-ppp**, in the Universe repository...[/QUOTE]
 great idea but say if someone cant get online who not dual booting it be hard to get online to get a program to get them online.

---

### Post by tiiim on 2005-01-08
[QUOTE=machiner]

PS I DO NOT recommend Mandrake. It's got more bugs than aa screen door has holes.

If you want easy, quick, and pretty - go with fedora core 3. It's bleeding edge and a testbed for new RedHat releases, but it's pretty damned stable.[/QUOTE]


Mandrake is great for user friendlyness but its trademake not exactly the most stable of all distro's which is a shame. Even though userfriendly the bugs may scare people back to windows so its a loose loose situation.

FD3 is a great distro the only thing i disagree that it is a testbed its not meant to be the next desktop distro its just a test enviorement so every realise they may add or take something away to try things out. If they ever made FC into a proper distro as it would be amazing but its seems like its only gonna be a testbed but when i installed it on my home pc it detected all my hardware better than mandrake and yes its rock solid.

Ubuntu though is prob the best distro i have tried, now remember this is Ubuntu first release! For a first release its pretty amazing, i think its shot up distrowatch charts very quickly, if it has this every release imagine where it be in a few more releases time. So thumbs up for a first release i am looking forward to Hoary and beyond....

if you look on distro watch Ubuntu doing well however what may suprise you if you click the drop down list for the last month... ubuntu jumps up!

---

### Post by JD2 on 2005-01-08
I agree, ubuntu as a desktop os is great. It's when your hardware doesn't work in ubuntu is when you have to climb a very steep hill and get down into linux internals. About my modem. It's a winmodem and it needs a module installed otherwise it won't work. I can either compile the module from sources found on the internet or find binary that someone compiled for both x86 and 386 asm instructions. If I decide to compile I have to learn a great deal about linux only to use this knowledge on one crazy modem. Ok, I'm sorry if I offended anyone, just venting my frustrations  :oops:

---

