---
title: "Upgrading 64 bit to 32 bit Ubuntu!"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Kellemora on 2009-02-12
Hi Gang

No I didn't type it backwards!

I'm planning on UPGRADING my new Dual Core 64 bit Ubuntu machine back to the functioning 32 bit Ubuntu package.

The problems with 32 bit Ubuntu I thought moving to 64 bit would help, didn't.

Plus I have numerous new problems to contend with, with no resolution in sight.

Problem One:  No Adobe Reader or Firefox Plug-in for 64 bit, the ability to read PDF files is a MUST HAVE feature!
Problem Two:  No Java plug-in for Firefox, although I finally managed to get Java 6 installed, there are no Plug-ins and Iced Tea didn't work either.
Problem Three:  A MAJOR ONE, Rsync writes only folders, not files to the data file server.  MUST HAVE a way to SAVE DATA, copy and paste works, but that means 6 hours of wasted time per day!
Problem Four:  Files that can be read, written to, saved and copied in 32 bit Ubuntu are not even visible on the 64 bit Ubuntu.  You can check Properties on the folder and it counts them, but can't show them.
Problem Five:  Ongoing on all versions, Nautilus fails to display shares all the time on 32 bit, don't show shares at all on 64 bit.

I've owned this new computer over a week now and still cannot put it to daily use!  Unless I run the DOZE on it, then it works just fine!
I don't want to go back to the DOZE!
So I guess my ONLY ALTERNATIVE is to UPGRADE from 64 bit to 32 bit!

Unless some has some ideas on how to get around these serious problems!

TTUL
Gary

---

### Post by kanikilu on 2009-02-12
Sorry I can't offer constructive advice, but just thought I throw out there that I also "upgraded" from 64bit to 32, for the same problems as your first 2 listed.

If there comes a time in the future where I need to utilize my full 4GB of RAM, then I'd probably fight for it or live with the issues, but in my case, "losing" half a gig of memory was an acceptable compromise.

---

### Post by avtolle on 2009-02-12
Don't know if either of you are interested, but you might take a look at the 64-bit Linux Mint 6 release, which comes with the 64-bit Adobe and Sun Java plugins. See more details at [http://www.linuxmint.com/blog/?p=595](http://www.linuxmint.com/blog/?p=595)

I've had Mint installed since Mint5, and find it a good distro. Not for everyone's needs, but as Mint6 is based on Ubuntu 8.10, not a steep learning curve to overcome.

EDIT: Oops, sorry; you were talking about Adobe Reader, not Flash. My bad there, although one may install the "beta" 64-bit reader from Adobe.

---

### Post by Cope57 on 2009-02-12
Why not "upgrade" to 16 bit instead?
I heard that is what people did not want to leave when 32 bit came out.

Seriously though, I have been running 64 bit since 2003, and I am already waiting for 128 bit, why you wanting to go backwards is beyond me.

32 bit is way past its prime, and has been around since early 1980? It is time to move on. To bad 32 bit will probably lose support in a few years, but sure go ahead... and "upgrade" to it.
:popcorn:

**Edit:** I forgot to ask you about your so called 64 bit issues...
I am having no java, flash, or pdf issues with my operating system, maybe you are just getting ahead of yourself by not submitting bugs to the developers.
If you have submitted any bug reports, what have the developers told you about how to fix your issues with your hardware? The developers are not in here reading your post, so you should really send them a email.

---

### Post by oldos2er on 2009-02-12
You might want to read the stickies on the x86_64 bit User subforum.

---

### Post by cariboo on 2009-02-12
> Problem One: No Adobe Reader or Firefox Plug-in for 64 bit, the ability to read PDF files is a MUST HAVE feature!

You can get Adobe Acrobat in the Medibuntu repositories, go [here]("http://help.ubuntu.com/community/Medibuntu") to enable the repositories.

For the Adobe Flash 64 plugin look at this [howto]("http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+64"), it als tells you how to install the java 64bit plugin.

> Problem Three: A MAJOR ONE, Rsync writes only folders, not files to the data file server. MUST HAVE a way to SAVE DATA, copy and paste works, but that means 6 hours of wasted time per day!

Check your file ownership and permissions. I use grsync to back up my home directory, it about an hour the first time, then it only updates if there are new files.

> Problem Four: Files that can be read, written to, saved and copied in 32 bit Ubuntu are not even visible on the 64 bit Ubuntu. You can check Properties on the folder and it counts them, but can't show them.

Again check ownership and permissions and wierd file names.

> Problem Five: Ongoing on all versions, Nautilus fails to display shares all the time on 32 bit, don't show shares at all on 64 bit.

Are you in the same workgroup as the rest of the computers? Ubuntu defaults to WORKGROUP, depending on the Windows version it could be MSHOME or WORKGROUP.

Jim

---

### Post by Kellemora on 2009-02-12
Hi Guys

Regarding Problem ONE:  There is a workaround which I have to use with e-mails of PDF documents.  Create a direct link on the desktop to the folder they download to, then use EVINCE to read them.  Unfortunately, one cannot do that with Firefox PDF unless you download the document to the desktop first, then go there to open it.  I know, Adobe has nothing to do with Ubuntu.  But how about a plug-in for Evince then?????

Regarding Problem TWO:  I downloaded Java jre-6u12-linux-x64.bin and installed it.  It explodes to the 1.6 version.  It has no plug-in for Firefox, they say to use Ice Tea instead.  Tried that, no go!  Then I found somewhere else where it said to create a symlink to a particular /lib file, tried that and CRASH.
After I installed Mozplugger a few Java web sites partially work, but not very well, most of the boxes are still gray.  But at least I could get to the most necessary screens.

Regarding Problem THREE:  I went back to using Rsync the way I did when I first started using Ubuntu.  By running it in Reverse.  In fact, we had a RULE in the Office here that NO ONE tries to PUT anything onto the server, let the server FETCH their work at the scheduled times.  We built a new file server and everything was working great UNTIL I got this blasted new computer, now even the LAN is back to working in Manual Mode!

Regarding Problem FOUR:  We are slowly converting our files, one at a time, for a SECOND TIME, to make them viewable on the 64 bit version.  We converted more than twice that many from .doc to .odt after I chose to go with Ubuntu for the office.  Since they were viewable in 32 bit Ubuntu I never dreamed 64 bit would have anything at all to do with how filename are read and displayed.  Had I known 64 bit was a DOWNGRADE from 32 bits abilities, I would have bought more used computers instead of new ones.
It will take months to convert the files over to filenames the 64 bit Ubuntu can read!  I just hope we get it done before they DOWNGRADE 32 bit with an Update that makes it BLIND too!

Regarding Problem FIVE:  This problem has been ongoing in Ubuntu now for over 3 years.  The problem appears to be directly related to Nautilus!  And yes I've filed bug reports regarding this problem the way it affects us and how.  Others have filed also but didn't have any correlations or reasons why it might be happening.  Nautilus blames Samba and Samba works perfectly, so fixing the problem with Nautilus apparently just got shelved.

I didn't mention other problems that have arisen which we have already learned to live with.  Like the REQUIREMENT of having a fully functional Windows Computer in order to use Ubuntu.  The DOZE is one of Ubuntu's DEPENDENCIES to make it function!  Again, NOT Ubuntu's fault, since Ubuntu don't write the drivers used in Ubuntu for various hardware and devices.  They come from 3rd party vendors!  Some of these 3rd party drivers are much better than the OEM drivers in many ways.  But often something very serious is overlooked.
For example:  The printer driver for my color laser printer is totally Awesome, can do handsprings around the OEM driver.  But it has one major flaw that REQUIRES keeping a DOZE machine nearby.  The programmers who wrote the drivers apparently have a source for toner cartridges that never run out, meaning they NEVER need to change a toner cartridge EVER.
If they did, they would have included in the driver a method to change out empty toner cartridges.  Since they didn't, one can only assume THEIR toner cartridges never need replacing!  So, once again, a DOZE machine is a REQUIRED DEPENDENCY in order to use UBUNTU!

I've learned to live without Shockwave!  Although the charities that benefitted from my using it are not to happy.
If 32 bit is on the way out!  And Ubuntu 64 bit can't do the job yet!
Sad, but, Ubuntu will become Windows 7's best salesperson!

TTUL
Gary

---

### Post by presence1960 on 2009-02-12
Install adobe reader > sudo apt-get install acroread

Install adobe reader plugin for firefox > sudo apt-get install mozilla-acroread

make sure you install adobe reader 1st then the adobe plugin. when I did it the other way around adobe reader wiped out the firefox plugin. If you do as oldos2er says and go to the stickies in the x86-64 bit forum you will get flash and java working. My personal experience is that after reading a lot of Kilz's posts I decided to not listen to the naysayers and give 64 bit a try. I got it all working the first time on Kubuntu 8.10 and also on Linux Mint 5. My machine is fairly new, built it last february. 64 bit works great, will never go back to 32 bit unless I had no choice but to use Windows.

---

### Post by cariboo on 2009-02-12
I'm not sure if you are reading the suggestions posted here, or just going by what someone has told you. The Flash and java plugins are both beta, I've been using them for a couple of months and haven't had any problems. I've attached the scripts from the page I linked to, just extract them and run them in a terminal and the plugins will be installed automagically.

Jim

---

### Post by lazyart on 2009-02-12
Well, I personally have never solved Flash for 64 bit (it works for the day it's installed, then nothing).  But I do use Java to attach to other computers through LogMeIn.  Evince is cute, but I can never print from it (prints error messages instead of the actual document) so I just installed Acrobat and yes the plug in works just fine.

On top of all of that, I do need the RAM (I run 6 gigs for my desktop and virtual mail server and virtual web server, plus whatever distro I'm curious about).

Do what works for you. It's your equipment.

---

### Post by Kellemora on 2009-02-13
Hi Cariboo

Thanks for your info and Links, I surely will give them a try!

There are so many features of the 64 bit I like, I hate to go backwards!

As LONG as 64 bit has been out, one would think the most used features would have been finished, tested and included in the latest upgrades.

FWIW:  I have went to and read almost everything I could find and it gets confusing when one person says load this file, another says load that file.  I find them under the X86-64 listing and when I go to install them a warning comes up and says it's for i386 only and the installer closes.  WHY was it under the 64 bit downloads?

Naturally I checked the repositories FIRST, and DO HAVE medibuntu, I've never seen Adobe in there yet on the 64 bit, nor Java.  I do have AMD 64, I stay away from Intel as much as possible.  AMD has always been the proven winner around here!

Again, thanks for your input and advice!

TTUL
Gary

---

### Post by Kellemora on 2009-02-13
Hi presence

I installed both of the programs, the install went fine, no errors!

Haven't tested it yet since I'm still here in the forums.

But the point here is to say thanks for the info and that the install appears to have worked.

TTUL
Gary

---

### Post by Kellemora on 2009-02-13
Hi Cariboo

Well, with the files you provided, the install was a SNAP compared to how I was doing it before.

After exploding the files and installing them using terminal, I opened Firefox and went to a web site I KNEW would cause the "Install Missing Components" flag would pop-up!

A window opened that showed the following:
Adobe Flash Player
Swfdec player/macromedia flash
Gnash swf player.

You can only install one item at a time, but the web site was helpful in bringing up the "Install" window each time, so I was able to install all three.

Then after rebooting to make sure all was running right, I went back to the web site and I still get the "Install" window showing all three.
I selected each of them individually and get, "Already Installed", so are installed.

I DO KNOW that even on the 32 bit machines, none of the Shockwave stuff will work, but all of the Java stuff did.

So right now, the Java stuff still isn't working and the Install window still keeps popping up.

I'll tinker with it some more and see what happens!

TTUL
Gary

---

### Post by kaivalagi on 2009-02-13
Have you installed flashplugin-nonfree for frlash support in firefox? i.e.:

```
sudo apt-get install flashplugin-nonfree
```

I have zero issues with 64 bit, I use it to watch bbc news / iplyer content regularly, I develop using eclipse (java based app)...not a problem.

---

### Post by Kellemora on 2009-02-13
Hi kaiv

I tried and it said it was already installed.

I ran apt-get autoclean and also removed acroread-escript and then reinstalled the package you mentioned.

It appears Java is not starting or if it is starting it's not starting properly.  
Where I used to get a gray box, it's now white and says applet loading, but stops around 50 to 75% and doesn't move from there.

So we are getting there!

Cariboo gave me some pages to study, which will have to wait until later to try those things, have to get back to work here!  Makes the employees mad if they see me playing and they are working, hi hi.........

Thanks for all the tips everyone!

TTUL
Gary

---

### Post by stchman on 2009-02-13
> **Kellemora said:**
> Hi Gang

No I didn't type it backwards!

I'm planning on UPGRADING my new Dual Core 64 bit Ubuntu machine back to the functioning 32 bit Ubuntu package.

The problems with 32 bit Ubuntu I thought moving to 64 bit would help, didn't.

Plus I have numerous new problems to contend with, with no resolution in sight.

Problem One:  No Adobe Reader or Firefox Plug-in for 64 bit, the ability to read PDF files is a MUST HAVE feature!
Problem Two:  No Java plug-in for Firefox, although I finally managed to get Java 6 installed, there are no Plug-ins and Iced Tea didn't work either.
Problem Three:  A MAJOR ONE, Rsync writes only folders, not files to the data file server.  MUST HAVE a way to SAVE DATA, copy and paste works, but that means 6 hours of wasted time per day!
Problem Four:  Files that can be read, written to, saved and copied in 32 bit Ubuntu are not even visible on the 64 bit Ubuntu.  You can check Properties on the folder and it counts them, but can't show them.
Problem Five:  Ongoing on all versions, Nautilus fails to display shares all the time on 32 bit, don't show shares at all on 64 bit.

I've owned this new computer over a week now and still cannot put it to daily use!  Unless I run the DOZE on it, then it works just fine!
I don't want to go back to the DOZE!
So I guess my ONLY ALTERNATIVE is to UPGRADE from 64 bit to 32 bit!

Unless some has some ideas on how to get around these serious problems!

TTUL
Gary

I am going to assume you are running Hardy from your profile.

I run 64 bit Ubuntu on several machines with no problem.

1.  Ubuntu reads .pdf files OOB with Evince.  When I click on a link with a PDF Firefox uses Document Viewer to view it.  If all you need to do is read PDFs then Evince fits the bill.

2.  Use openJDK for 64 bit.
```

sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin

```

3.  Nautilus supports drag 'n' drop and copy 'n' paste.  Is this what you are talking about.

4.  Site some examples of files that have these properties.

5.  What sharing method are you using?  Samba or NFS.  I find that Ubuntu has problems seeing Windows shares, but easy to see NFS shares.

I will let the other forum members explain network sharing as it has always been hit or miss with me.

---

### Post by gn2 on 2009-02-13
[Simple 64-bit Adobe Flash how-to]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml")

Latest 64-bit flash [download link]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz").

Other things to consider doing are removing Pulse audio and the libflashsupport package.

---

### Post by egalvan on 2009-02-13
> **kanikilu said:**
> 
If there comes a time in the future where I need to** utilize my full 4GB of RAM,** then I'd probably fight for it or live with the issues, but in my case, "losing" half a gig of memory was an acceptable compromise.

Well, I utilize my full 8GB of RAM under 32bit Ubuntu...
Installed the Server Edition, then apt-get'd the DE I wanted.

a quote from the Official Ubuntu Documentation site...
[https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#id3023755](https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#id3023755)

(For all you nay-sayers out there concerning 32bit and 4G+ RAM,
especially note the last sentence...)



Quote:
[i]Server and Desktop Differences

There are a few differences between the Ubuntu Server Edition and the Ubuntu Desktop Edition.
 It should be noted that both editions use the same apt repositories.
 Making it just as easy to install a server application on the Desktop Edition as it is on the Server Edition.

The differences between the two editions are the lack of an X window environment in the Server Edition,
 the installation process, and different Kernel options.

Kernel Differences:

    *      The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.

    *      Preemption is turned off in the Server Edition.

    *      The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.

    *      The Server Edition is optimized for i686 processors while the Desktop Edition is optimized for both the i586 and i686.

    *      Virtualization is better supported in the Server Edition through the enabling of IPC namespaces, and the Xen hypervisor.

    *      Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.

    *      [B]For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to [COLOR="Red"]64GB[/COLOR] of memory
 while the Desktop Edition is configured for[COLOR="red"] 4GB.[/COLOR]
[/B]
[/i]

---

### Post by presence1960 on 2009-02-13
Gary, just doing what someone did for me. That's why this community is so awesome! Here is a link to the thread which I followed to install java and flash on my 64  bit kubuntu and mint. Kilz posted this : [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
Because of a lot of his posts I decided to ignore all the naysayers of 64 bit and give it a try. I was not diasppointed.

---

### Post by Kellemora on 2009-02-13
Hi Stchman

I just tried that, now everything that WAS working isn't.......

How do I uninstall it and revert back to how far along I was already?

TTUL
Gary

---

### Post by SunnyRabbiera on 2009-02-13
> **Cope57 said:**
> 
32 bit is way past its prime, and has been around since early 1980? It is time to move on. To bad 32 bit will probably lose support in a few years, but sure go ahead... and "upgrade" to it.
:popcorn:


32bit past is prime?
I dont think so, its still viable for moist of us.

---

### Post by egalvan on 2009-02-13
> **Cope57 said:**
> 
32 bit is way past its prime, and has been around since early 1980? It is time to move on. 


> **SunnyRabbiera said:**
> 32bit past is prime?
I don't think so, its still viable for most of us.

As someone who still has a couple of 16bit:!: machines running well in my house,
I have to agree, 32bit IS past it's prime.

But Sunny, this doesn't mean it NOT viable.

Prime means *best, top-of form*
Viable means *adequate to the job, can get it done*

A 386-class CPU is adequate for the job of routing packets,
or serving up files or printers.
But I doubt it would be the best to watch HiDef 1080P video.

Heck, I still fire up my old 8bit TRS-80 from time to time...
Mainly to remind me of how far we have come. :)
(I occasionally play that old text-based-scrolling-graphics StarWars X-Fighter game.)

---

### Post by gn2 on 2009-02-14
> **SunnyRabbiera said:**
> 32bit past is prime?
I dont think so, its still viable for moist of us.

Certainly not past it's prime, 32-bit only Atom CPU's are being churned out as fast as Intel can make them.

---

### Post by hyper_ch on 2009-02-14
> **Kellemora said:**
> As LONG as 64 bit has been out, one would think the most used features would have been finished, tested and included in the latest upgrades.
Flash and Java are proprietary products. Adobe did publish the 64bit flash only a few months ago and only for linux. There's no 64bit flash for Windows because nobody on windows runs 64bit because there are just no programs to run on. More or less the same goes for java.

---

### Post by Kellemora on 2009-02-14
Hi Hyper

I hear ya loud n clear on that one!!!!!

I've got enough machines around here that trying to do everything on one of them is actually self-defeating!

I have 4 computers on a KVM so I can quickly bounce between them, and a keyboard and mouse within reach when I need to use them on the machines on the KVM.  The monitor for those machines sits high, not inside the desk.

I did some major changing around last night, so the KVM now feeds the monitor in my desk, along with the keyboard and mouse at my desk, without reaching or looking up.  Had to change video drivers around a little since this monitor is a different brand.

So at least NOW I can do all of my work just by pressing a button for which computer runs which program the best.  And since I use a data file server for file storage, it really don't matter anymore WHICH computer I'm using.

Ever since switching to Ubuntu back in September of 08, I've only used Ubuntu 32 at my desk, and if I needed to do something else, I pulled down the keyboard and mouse that connects to the KVM and strained my neck to look up at the monitor up there.  But then too, Ubuntu 32 did nearly everything!

Since switching to Ubuntu 64, many of the things I do each day could no longer be done as they don't work on the 64 bit machine.
It was easy to move a few cables and place the KVM output to my desks normal peripherals and use the upper monitor only for some remaining Doze things.

In any case, I'm back to running at full production working this way!
I'll use the 64 bit machine for what works on it, and the 32 bit machine for everything else.

I should have bought an 8 bay KVM instead of a 4 bay though, hi hi......

I'll just bide my time until 64 bit things are available!

TTUL
Gary

---

### Post by stchman on 2009-02-15
> **Kellemora said:**
> Hi Stchman

I just tried that, now everything that WAS working isn't.......

How do I uninstall it and revert back to how far along I was already?

TTUL
Gary

What did you try?  All the stuff I talk about I have on (3) PCs running 64 bit Hardy,

---

### Post by Kellemora on 2009-02-15
Hi stch

This line of code of you gave me:
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

I removed it and went back to the two self-installing programs I installed earlier, at least most of the web sites work with those.  Probably just need a tad bit more tweaking is all.

I'm to elated to worry about it today though!
I finally solved a problem that has plagued me since August of 2008, ever since I first started using Ubuntu......

At first I chalked it up to inexperience!

Then later began studying bug reports and the like, with no luck there either.

Apparently I'm the only person who has had this problem and it affected all 6 of my Ubuntu machines, even the 64 bit machine.

NONE of them would play midi files from the web, even with timidity and mozplugger installed.  Even changing the pointer to mozplugger didn't help.  I found out the problme was Gnome mplayer or gecko media player actually.  I didn't know what would happen when I hit the uninstall button, but I tried it anyhow, first on this machine.  Midi's began working at all the web sites I hit with them on it.
Removed it from another machine, same result, things started working properly.  So I went through all of my machines deleting that mplayer and now all of my machines whistle a happy tune!

Because I have tried so many things on this new 64 bit, I spent yesterday evening wiping it and reformatting the HD and reloading it again from the CD and getting the updates offline.  That way I knew I was starting with a clean install.  Kept a list of the 18 things I knew I had to install and/or remove or change to get back to this point, sans garbage I've tried.

And as mentioned in my article above, changed a lot around here so my work goes much faster.  I can play today, but have to have everything up and humming perfectly for Monday morning.

TTUL
Gary

---

### Post by stchman on 2009-02-16
> **Kellemora said:**
> Hi stch

This line of code of you gave me:
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```

I removed it and went back to the two self-installing programs I installed earlier, at least most of the web sites work with those.  Probably just need a tad bit more tweaking is all.

I'm to elated to worry about it today though!
I finally solved a problem that has plagued me since August of 2008, ever since I first started using Ubuntu......

At first I chalked it up to inexperience!

Then later began studying bug reports and the like, with no luck there either.

Apparently I'm the only person who has had this problem and it affected all 6 of my Ubuntu machines, even the 64 bit machine.

NONE of them would play midi files from the web, even with timidity and mozplugger installed.  Even changing the pointer to mozplugger didn't help.  I found out the problme was Gnome mplayer or gecko media player actually.  I didn't know what would happen when I hit the uninstall button, but I tried it anyhow, first on this machine.  Midi's began working at all the web sites I hit with them on it.
Removed it from another machine, same result, things started working properly.  So I went through all of my machines deleting that mplayer and now all of my machines whistle a happy tune!

Because I have tried so many things on this new 64 bit, I spent yesterday evening wiping it and reformatting the HD and reloading it again from the CD and getting the updates offline.  That way I knew I was starting with a clean install.  Kept a list of the 18 things I knew I had to install and/or remove or change to get back to this point, sans garbage I've tried.

And as mentioned in my article above, changed a lot around here so my work goes much faster.  I can play today, but have to have everything up and humming perfectly for Monday morning.

TTUL
Gary

Sounds like you need 100% Java browser plugin capability.  The IcedTea plugin works but not for all Java enabled websites.

---

