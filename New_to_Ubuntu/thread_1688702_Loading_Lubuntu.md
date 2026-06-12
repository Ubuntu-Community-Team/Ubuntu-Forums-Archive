---
title: "Loading Lubuntu"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by Sandy0848 on 2011-02-15
I have downloaded lubuntu 10.10 and made a live CD.

Loaded into an old Dell ( otherwise on it's way to the scrapyard) it seems to work fine.

The dell still has a functioning Windows XP professional on board but all data has been removed long ago.

So I can see the Install Lubuntu icon and when I use it there is a little bit of activity from the CD but nomessages on the screen. After a while there is what appears to be a clock timer but now the Lubuntu pale blue scree is just sitting there with the little clock still sitting there and capable of being moved around by the mouse.

How long do I wait before giving up? Or should I be doing something?#

All help and advice greatly appreciated

Sandy

---

### Post by Mariane on 2011-02-15
I don't know about Lubuntu but Kubuntu has the option "Check disk" when you boot it from a CD. I would advise you to manually stop the computer, reboot it again from the CD and run this option instead of "Install". Re-try "Install" afterwards if the CD is fine. 

iso CDs often go wrong, either during download or during CD burn or afterwards. Maybe something is wrong with the disk. I had a perfectly good CD of Kubuntu 10.10 and today it was not functionning and I had to burn a new one. 

Mariane

---

### Post by Sandy0848 on 2011-02-16
Tried the 'Check' as suggested and tried to load  but still no success. For a while it looked as if I was getting somewhere but still finished up looking at the clock. Now proposing to clear out al traces of old Windows and make new partitions.

Sandy

---

### Post by Sandy0848 on 2011-02-17
I have installed GParted and set up two partitions. As far as I know all evidence of previous Windows installation has been removed.

Tried Lubuntu instal to hard drive again and after a positive start got to the stage where I had a pale blue patterned screen, no task bar, and a a small clock where the cursor had been.

Everything seemed to have stopped. Now i read that maybe something was still soldiering on.

How long should ( or could) this operation take.

Shall I leave it overnight? Is there some way of confirming that something is happening?

---

### Post by quadproc on 2011-02-17
> **Sandy0848 said:**
> 
Tried Lubuntu instal to hard drive again and after a positive start got to the stage where I had a pale blue patterned screen, no task bar, and a a small clock where the cursor had been.

I had a similar experience when I tried out Lubuntu in an old Dell GX110 with 256 MB RAM except that my cursor never did change to anything else and eventually (maybe 30 minutes later) I gave up on it.

On the other hand, I installed Puppy Linux on that same system and it works nicely.

quadproc

---

### Post by Kixtosh on 2011-02-17
I installed Lubuntu on an old Dell (PII 400MHz CPU and 256MB of RAM) alongside W2K and it worked admirably (until the laptop stopped altogether ... some sort of power supply issue, I think). In fact, boot times were just about one minute, and browsing with Chromium was quite acceptable. The presence of Windows does not cause problems, although you should defragment the Windows installation about three times beforehand if you don't want to "break" it.

Are you saying the LiveCD does not boot up, even if you want to just try Lubuntu first, without installing? I would simply try the Live version first, if I were you, just to make sure you are not wasting your time. Installation on very old machines, like mine was, does take quite some time.

Have you verified the "MD5 Checksum" of your downloaded ISO file before burning? This will check for errors.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have you made sure you are burning at slow speed when making the installation CD? I'd suggest 4X, or even 2X if you can just leave it alone to burn the disk.

If you have done all of this, you could either try an earlier version of Lubuntu, such as Karmic Koala (9.10) or even Puppy Linux, which runs only in RAM, without using the HDD. You can later save some tiny Puppy files to the HDD if you want, even within your Windows folders, to speed up subsequent boot times of Puppy. Honestly, if you're having trouble already, Puppy may be the fastest and simplest way to verify that your laptop is at least worth saving before trying a more "grown up" Linux such as Lubuntu.

[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

Release 431 is a recent, but older version of Puppy that worked very well for me (and it's lighter than the newer 501 etc.).

---

### Post by SteveDee on 2011-02-18
> **Sandy0848 said:**
> I have downloaded lubuntu 10.10 and made a live CD...
...Loaded into an old Dell ( otherwise on it's way to the scrapyard) it seems to work fine....


I take from this that Lubuntu runs OK from a LiveCD but won't install.
You may have a hard disk problem, so if you have a spare, try swapping it out.

Another possibility is a BIOS setting that is associated with your HDD/IDE/SATA or whatever. Try playing with these settings.

As already mentioned, Puppy Linux will probably work as it runs in RAM.

---

### Post by Sandy0848 on 2011-02-18
.The LiveCD of Lubuntu seemed to work fine though I never did confirm the checksum. It was burned at 10x which seemed to be the slowest that InfraRecorder would allow.

The intention _has_ to be get a Linux system running on the hard drive. It ws initially running Windows XP but that has now been removed.

The original CD drive has also been removed and I am using a different ( i.e. non installable) CD/DVD drive to provide the input capabilities.

BUT the aim is to have a hard drive booting OS and eventually I shall find a replacement and installable CD drive.

I just deplore throwing stuff in the bin and the Ubuntu exercise is keeping me occupied.

So thanks for the helpful suggestions. I shall be working my way through them

Sandy

---

### Post by quadproc on 2011-02-18
Sorry, redundant post due to keyboard fumble.  See post below.

quadproc

---

### Post by quadproc on 2011-02-18
> **Kixtosh said:**
> 
If you have done all of this, you could either try an earlier version of Lubuntu, such as Karmic Koala (9.10) or even Puppy Linux, which runs only in RAM, without using the HDD.

You can also run Puppy in the usual way, from disk.  My only complaint about Puppy Linux is that it is a single user system, and that user is necessarily root.

I have used Puppy Linux a few times when my larger system was out of order; it is very useful to be able to ssh into a fancier system whose graphics is not working!

quadproc

---

### Post by Kixtosh on 2011-02-18
If you were able to try the LiveCD properly, then it may be that you just gave up too soon. If the system properties are as old as what I mentioned earlier (PIII, 256MB), then it may take a long time to install (hours, instead of the usual fast installation of Ubuntu and other variants) and you may experience long periods where nothing much seems to be happening. I would even advise just leaving it overnight, if you have got past all the setup menus (including HDD partitions as well as your username and password).

For reference: a recent full version Ubuntu 10.04 installation I completed on an old, but still much newer laptop, with a 1.2 GHz Pentium M and 1.28 GB of RAM was much faster (and never really sat idle for any length of time during the process). I did also try Lubuntu on that machine, by the way, but it was not worth it since even with those modest specifications (by today's standards) Ubuntu was almost as fast as the lightweight distro. You may want to consider that if your laptop is not really ancient.

Also, since you mention you are not using the original CD drive, it may well be that this is greatly slowing down the start of the process. I've seen those symptoms before as well (with an external drive compared to a removable OEM drive inserted in a docking bay), but everything went smoothly in the end nonetheless.

Finally, there are several other lightweight versions you can try as well, including Peppermint. Just changing that might make something work that wasn't before. I would still check your MD5 Checksum value though, just so that you can rule that out as a source of problems.

---

### Post by whatthefunk on 2011-02-18
Oops...mis-post.  Apologies.

---

### Post by Dutch70 on 2011-02-18
I had the same exact issues installing Lubuntu onto an old machine. I think they are having trouble with their installer. I wouldn't waste another second on it. I tried it for over a week, and that's been about 2 wks ago.

If you have 512MiB of RAM, try Xubuntu - [[COLOR="Red"]Xubuntu[/COLOR] ]("http://www.xubuntu.org/")

Or...Peppermint OS is out of the buntu family, but one of my favorites for old machines. Runs on 192MB RAM and it's really fast.
Get it at their website... [[COLOR="Red"]*Peppermint OS*[/COLOR]]("http://peppermintos.com/") Or get it at [*[COLOR="Red"]DistroWatch[/COLOR]*]("http://distrowatch.com/table.php?distribution=peppermint")

---

### Post by whatthefunk on 2011-02-18
> **Dutch70 said:**
> I had the same exact issues installing Lubuntu onto an old machine. I think they are having trouble with their installer. I wouldn't waste another second on it. I tried it for over a week, and that's been about 2 wks ago.

If you have 512MiB of RAM, try Xubuntu - [[COLOR=Red]Xubuntu[/COLOR] ]("http://www.xubuntu.org/")

Or...Peppermint OS is out of the buntu family, but one of my favorites for old machines. Runs on 192MB RAM and it's really fast.
Just click... [[COLOR=Red]Peppermint OS[/COLOR]]("http://peppermintos.com/") Or get it [*[COLOR=Red]Here[/COLOR]*]("http://distrowatch.com/table.php?distribution=peppermint")

The problem is probably the graphic installer.  A lot of old machines cant handle it.  Use the Alternate Install CD.

---

### Post by JC Cheloven on 2011-02-18
Hi, I also like to bring back to life old, almost unused computers, usually gathered from friends. Here my 2p:

- Puppy is an excellent minimal distro, and there is SliTaz for the most extreme cases. But I really prefer Lubuntu if the hardware can handle it.

- It's known that in old hardware the installation may seem to hang, but it's simply working slow. Please see for example: 
[https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall)

- In an old hardware, installing from the graphical live cd, is a bit like asking for problems. Now there is an "lubuntu alternate cd". Details in the same link above.

- Even better IMO (because it's more "modular"): I usually use an ubuntu _alternate_ disk (not live cd), and install a command line system only. Then, with internet connection, I install the lubuntu-desktop related packages. The process is pretty well explained [here]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall").

Hope to be of help
JC

---

### Post by Sandy0848 on 2011-02-20
My thanks to everyone for their suggestions. i really did wait for hours with Lubuntu before deciding to move on.

Still want to get Linux onto the hard drive so loaded DSL. Followed the instructions and it worked so you could say 'Mission Acconplished'

I then decided that I still wanted to try some of the other live CDs that I had burned but here came another problem.

I had noticed wit DSL that it was only part way through the boot that I got USB and there fore my keyboard and mouse into operation.

So when I wanted toload a live CD I wanted to get into BIOS to put the CD into the boot order./

But every time I start the machine now I cant use the keyboard to get into BIOS because it is straightaway booting up DSL.

Now what do I do ???

Sandy

---

### Post by JC Cheloven on 2011-02-20
First of all: DSL was an extremely nice minimal distro. Unfortunately its maintenance and development sems to be stalled since quite a long time. I'd not recommend the use of a non maintaned distro. To get an idea:
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=8;t=20727](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?;act=ST;f=8;t=20727)
And have a look also around dsl forums in general, noticing the posting dates.

If you really want it that minimal, have a look at [SliTaz]("http://www.slitaz.org/en/") (as said), or [TinyCore]("http://tinycorelinux.com/") 

But most likely you don't want it that minimal. So please, forget about live cds for installing in scarce hardware, and go for alternate images, or a CLI as a starting point,  of ubuntu. You may think we say that by no reason, but it's out of experience: please try.

As for your last problem: I don't fully understand your wording, but doesn't matter: you shouldn't use dsl unless you had very special reasons to do it, and know very well what you're doing. The best help I can offer you already is in my previous post. Hope that helps.

[INDENT]EDIT: in a second read, it seems your keyboard isn't working?  Is it a usb keyboard, right? 
Old BIOSes don't manage usb, so a usb keyboard can't be used to setup the bios. You have to connect a ps2 keyboard or the like. 
By the way, could you please post your computer specs? (if it ran xp, should be able to run regular ubuntu)[/INDENT]

---

### Post by Dutch70 on 2011-02-20
> **JC Cheloven said:**
> 

[INDENT]EDIT: in a second read, it seems your keyboard isn't working?  Is it a usb keyboard, right? 
Old BIOSes don't manage usb, so a usb keyboard can't be used to setup the bios. You have to connect a ps2 keyboard or the like. 
By the way, could you please post your computer specs? **(if it ran xp, should be able to run regular ubuntu)**[/INDENT]

I'm not really sure about that JC. If you consider that what was acceptable for xp then, would not be acceptable now. I came to that conclusion when I put Ubuntu on an old (256MiB RAM) XP computer & it would run it, if you wanted to click firefox & go make a cup of coffee. Lubuntu was almost instant on it, the diff is amazing, but would not install. I went with Xubuntu which I think really needs at least 512MiB RAM. 

Sandy0848,
 as JC said, please post your pc specs & I'm confident we can help you find a distro that's perfect for you & your pc. Also, if you have a usb stick, you can try a lot of diff distro's w/o having to burn a cd & it's faster off the usb stick. You can use "start up disk creator" if you can get it on DSL. or Unetbootin if not, to make the live usb stick/flash drive.

---

### Post by Kixtosh on 2011-02-20
> **Dutch70 said:**
> I'm not really sure about that JC. If you consider that what was acceptable for xp then, would not be acceptable now. I came to that conclusion when I put Ubuntu on an old (256MiB RAM) XP computer & it would run it, if you wanted to click firefox & go make a cup of coffee. Lubuntu was almost instant on it, the diff is amazing, but would not install. I went with Xubuntu which I think really needs at least 512MiB RAM. ...I agree with this assessment, to a certain point. I put Lubuntu and Xubuntu on a couple of old laptops that would run XP with 256 MB of RAM. When first installed, XP would take about eighty seconds to boot up, but after a few months (of doing absolutely nothing shady whatsoever) XP would end up taking five whole minutes to start, and I'm not joking! My observations:

1) Ubuntu ran on both of these, but it did take over ninety seconds to boot. Browsing could be sluggish, but no worse than Firefox with XP.
2) Lubuntu or Peppermint were much better, at less than sixty seconds to boot up.
3) Xubuntu also ran well, but still required at least eighty seconds to boot up ... until I added the LXDE desktop environment from the Software Center, instead of XFCE. After that, Xubuntu was basically 90% as good as Lubuntu, and in some ways preferable (especially as an "official" distro, with an LTS release, which Lubuntu does not have yet).
4) Chromium is a significantly faster browser with these ancient lap-o-saurs, when compared to Firefox, in my opinion.
5) Puppy was easier to try than either Lubuntu or Xubuntu in many respects, but did not really yield any significant increase in performance that I could measure. It did have the advantage of not having to modify the Windows installation in any way at all.
6) The main difference I noticed with XP was no slowing whatsoever in boot times for Lubuntu or Xubuntu, even after many weeks or months of usage.

---

### Post by Sandy0848 on 2011-02-21
I do appreciate all these helpful suggestions as to what I should use on this old computer.

BTW it is a Dell Optiflex GX110

At the beginning of this exercise it becamme apparent that the CD drive wasn't going to play so I have removed it and substituted, externally, a more modern Cd/DVD drive. This has been seen to work fine.

However i had declared my purpose to get the machine running with an OS running on the hard drive and for better or worse went down the DSL track.

Now DSL is working on  the hard Drive so I could say 'mission accomplished'

However in the presence of so much advice I dercided to try some of the liveCds I had previously burned and used.

BUT


DSL wont give me the keyboard or mouse until it is well through it's booting sequence.

So I cant get into BIOS to change the boot sequence to CD.



SO the latest question is how do I unload DSL???


Happily this is a  long term vacation exercise so work only gets done in between other social activities. But it is interesting

Cheers  Sandy

---

### Post by Toafan on 2011-02-21
Here's what I would try:

[LIST=1]
[*]Remove the HDD from the laptop
[*]Boot again
[/LIST]
The idea here is that if you take out the HDD, it *can't* boot from it, so you will either be able to get at the BIOS or boot from a Live CD. Note that the BIOS "key" tends to appear very early in the boot process (eg,, almost immediately), so you may need to try several times.

When you get to the BIOS, make sure that it tries to boot from CD before going to HDD - that way, this shouldn't happen again.

On newer Dell computers (the ones that I actually have experience with), right after the BIOS/setup key message there appears a message saying "press F12 for boot options". Also check if there's something like that.

If none of that works, the other thing I would consider trying would be to put the HDD in another machine (where it *won't* be the boot disk) and either boot from CD to install to it (prob. a BAD idea, actually) or wipe it before putting it back in the laptop and trying to install again.
Since you have the benefit of second opinions, however, I would encourage you to see what the others think before trying either of these last.

---

### Post by Kixtosh on 2011-02-22
> **Sandy0848 said:**
> ... BTW it is a Dell Optiflex GX110 ...

... DSL wont give me the keyboard or mouse until it is well through it's booting sequence.

So I cant get into BIOS to change the boot sequence to CD. ...That does seem to be quite an old computer (originally purchased prior to 2000, I would estimate). Can you be more specific about the model though?

- CPU model and speed
- RAM present
- HDD installed

Otherwise, are you using a USB keyboard? It seems very odd to me that a standard PS/2 keyboard would be shut out of BIOS, whether any operating system was functioning or not (indeed, whether or not a hard drive was even present) and desktops from that long ago would always have had a PS/2 keyboard and mouse, I would think.

[http://en.wikipedia.org/wiki/PS/2_connector](http://en.wikipedia.org/wiki/PS/2_connector)

If you don't have more than 128 MB of RAM, Puppy is probably your only decent (well supported, and easy to use) choice, and yes, it can be installed on the hard drive, even if it was not initially intended for that. I would estimate that even Lubuntu really needs 256 MB of RAM. You could, of course, explore options for purchasing very cheap RAM (from eBay, etc.), depending on what the maximum allowed for that model was. It looks like 512 MB was possible, which would be plenty for a decent lightweight distro.

[http://www.ec.kingston.com/ecom/configurator_new/modelsinfo_disc.asp?id=3&SysID=8633&mfr=Dell&model=OptiPlex+GX110+L/MT/SFF&root=us&LinkBack=http://www.kingston.com&Sys=8633-Dell-OptiPlex+GX110+L/MT/SFF&distributor=0&submit1=Search](http://www.ec.kingston.com/ecom/configurator_new/modelsinfo_disc.asp?id=3&SysID=8633&mfr=Dell&model=OptiPlex+GX110+L/MT/SFF&root=us&LinkBack=http://www.kingston.com&Sys=8633-Dell-OptiPlex+GX110+L/MT/SFF&distributor=0&submit1=Search)

---

### Post by Sandy0848 on 2011-02-24
Just a word to all of you who have offered their help in what has been a very interesting learning curve for me. Unfortunately I have to announce that the old computer appears to have worked it's last, at least in my hands.

So this machine is on its way to the scrapyard

Thanks again

Sandy

---

### Post by Kixtosh on 2011-02-24
It happens (so does **it!), as the saying goes. Just when I got my trusty old Dell CPi R400GT in my signature going with Lubuntu, it gave up the ghost too. Some sort of power issue (I couldn't even get the BIOS splash screen to show up, or the green "power" LED to light).

It was worth a try though, and everything did work for me for a while. Hopefully you'll get a chance to test something just slightly newer in the future. My Toshiba Portégé 3490CT (circa Y2K) is still working away happily with Xubuntu and the LXDE desktop, and my Portégé R205 boots up in 55 seconds, compared to two minutes when using a fresh intall of Win XP. The main difference is that with Win XP I had to constantly worry about updates and security issues as well as boot times gradually lengthening over six months until it took a whole five minutes. That's just way too long, so I just relied on using sleep mode most of the time instead of having to turn it on. With Ubuntu, boot times seem to remain constant from when first installed to several months later, and 55 seconds is quite acceptable for everyday use on five year old technology with a mere 1.2 GHz CPU, and 1.280 GB of RAM. The HDD spins at a modest 4,200 RPM, which doesn't help.

Interestingly enough, Lubuntu barely added any performance whatsoever to the R205. My point is that it doesn't take very fancy equipment to get a lot out of Ubuntu without even needing to use something designed for older equipment, like Lubuntu. 

If you ever get the chance to try an old machine with at least 512 MB of RAM and a 1 GHz CPU, or faster, you might just have some fun after everything you have learned through this experiment! Good luck!

---

### Post by Jared Norris on 2011-02-24
Sorry to have come in late to this discussion but I think I have a solution to your problem.

If you have a read of the release notes - available at [https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat) - I've seen that it states that it has dropped support for some older kernels. This then lead me to read the full Ubuntu release notes and the section - [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Linux%20kernel%202.6.35](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Linux%20kernel%202.6.35) - suggests to me that all i586 processors and i686 processors without cmov are now no longer supported even in mainstream Ubuntu.

From what I can tell this is a kernel related issue and as the suggestion on the Lubuntu release notes state the best fix is to install and run 10.04 which will be maintained as an LTS.

This appears to not be the fault of L/Ubuntu but rather updating the kernel. At least if you have these older processors there is a solution, install and run 10.04.

I hope this helps.

---

