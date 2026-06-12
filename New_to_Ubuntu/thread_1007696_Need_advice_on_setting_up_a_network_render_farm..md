---
title: "Need advice on setting up a network render farm."
date: 2008-12-10
forum: New to Ubuntu
---

### Post by 3dz on 2008-12-10
I have been going back and forth on this for several months now.  I am disabled and on a limited income.
Hence the reason why I've decided on Linux.  Other operating systems charge you for a license for each node.

When I first started out, I was looking at Ubuntu Studio.  Then I looked at ArtistX.  I liked it, it worked great on live CD. To my understanding, ArtistX is used for customizing Debian.  Still learning about the Linux operating system.  I found out Ubuntu is Debian based. Makes things a little easier configuring with .deb files.
I am a Blender user, but I also like to model with Wings3D.  I used both the applications in Windows, but they work great in Linux. I find that blender takes advantage of multiple processors, and multiple cores. Wings3D has a simple interface, that I like to use for modeling Prims.  There are a few other applications that I would like to have.
 
1. Synergy: [http://synergy2.sourceforge.net]("http://synergy2.sourceforge.net")  it is an alternative to KVM switches.  My thinking on this is, to have four monitors setup for Blender's top view, front view, side view, and the camera view. 

2. Voodoo Motion Tracking: [Voodoo]("ftp://ftp.tnt.uni-hannover.de/pub/digilab/voodoo-x86Linux-0.9.4.tar.gz")
The only thing I can find is a tarball in Linux.  It worked good in Windows, but it's my understanding it works even better in Linux.  Here is a little sample what I have done in Windows: 
[Voodoo and Blender test.]("http://www.youtube.com/watch?v=B3cXPZzUIm4&feature=channel_page")

3. MakeHuman: [www.makehuman.org]("http://www.makehuman.org/blog/index.php")
It is an advanced 3d humanoid modeling program,
capable of parametrically modelling all variety of humanoids starting from a single model of universal mesh. 
Recently I have installed this program with a .deb file.  I still have to install the Aqsis render engines, which is proving difficult.  All in all though, it is working.  A little bit sluggish, but without the render engine.  It didn't work at all in Windows.

4. Aqsis 1.4: [Aqsis]("http://sourceforge.net/project/platformdownload.php?group_id=25264&sel_platform=9643")
Aqsis is a cross-platform photorealistic 3D rendering solution, based on the RenderMan interface standard defined by Pixar Animation Studios.

Voodoo and MakeHuman work well with the Blender.  I don't know how well Aqsis works with Blender, I've never tried it.  It makes a difference with MakeHuman responsiveness.

I had been looking at render management, and DrQueue is movie tested with Elephant Dreams.  When I visit their web site, there is a lot of confusion.  The way I understand it is: the source file is free, but the compiled version you have to purchase.  There was a Python script that looked interesting.  I'm guessing it was made in Ruby Rails.  It said something about being made for Blender.  When I clicked on a link to download it, I got an error.  Something about a security error.
Is there anything else, (preferably free.) I might want to look at?
Thank you, in advance for any advice.

---

### Post by lunoob on 2008-12-10
Hi 3dz!

I'm less familiar with 3D modeling and rendering than you seem to be, but I've done some modeling and animations and just got part way through a sequence editing tutorial.

Also, I've just made my first foray into compiling packages from source code.  I've successfully compiled a .deb of a recent development version of Inkscape, which has some really cool improvements!

I can't make any promises, but I'd be willing to do what I can to help you get a .deb binary for the packages you can't find as a .deb package.  I haven't yet tried compiling anything in Ubuntu, but it can't be too different.  Which Ubuntu are you using?

[EDIT:]  DrQueue is in the Debian repositories.  Just add the appropriate repository in Synaptic - Settings > Repositories

You might want to verify this, but I suspect you'll want to add the following in the 3 spaces in the bottom of that window:

[ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/)
lenny
main contrib non-free  

If you're using Ubuntu based on Etch, then put "Etch" where "Lenny" is.
[END EDIT]

It'd be great if I could help, and I'd be eager to learn some things from you if you have the time.  You may want to check out one of my favorite forums: 
[http://linuxgraphicsusers.com/index.php]("http://linuxgraphicsusers.com/index.php")

Meanwhile, I need to install the latest 'buntu and see what's shakin'.  ;)

---

### Post by 3dz on 2008-12-11
Wow, thanks. That sure is nice of you to make such an offer.  I went to the Linux graphic user web site and, you seem to have really good knowledge of texturing.  One of my weak areas.  It's nice to connect with a fellow Blender'er.<?  I've been working with 3d modeling for a few years now, but I have only been working with Blender for a few months.  I do tutorials from super3boy also.  Anything with particles and modifiers.  He seem young but, that's what I think makes him so easy to understand.  He translates things in layman's terms.  

Here's something I have been working on: 
[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/keepper.jpg[/IMG]
I did the top half in MakeHuman and, the bottom half in Wings3d.  Now I want to texture it, and rigg it, in Blender.

Thanks for link to Debian repositories.  I'm a newbie with Linux, and still trying to get my USB 727 wireless EVDO modem, to connect with Ubuntu.  I think I know what is wrong.  Ubuntu sees it as a mass storage device.  In one of the How To's, I found on this forum.  It directs you to insert the ministorage card, and enters some code in the terminal.  I need to order the ministorage card, for it.  This is something that I've been trying to do for months now.
I'm slows as a turtle but, I keep hammering at it.
I'm wondering if it would be easier, just to purchase a repository CD?  
A lot of things I've been wondering.  I've been wondering if I should go back to Ubuntu studio.  I had no problems with Blender in studio.  But, I read somewhere, that Ubuntu studio is having problems with multiple cores in their new release.

PS. Here is a good site for Blender video tutorials: [blenderunderground.com/video-tutorials/]("http://blenderunderground.com/video-tutorials/")

---

### Post by Kellemora on 2008-12-12
Hi 3DZ

I only understood about 1/100th of a % of what you were talking about.

But, considering the TYPE of work you are doing, have you thought about connecting a couple or a few of your computers together to make a Cluster computer?

From what I understand it only takes gigabyte ethernet cards (one in each machine) to achieve the speed you're after.  Plus a controlling program of course.  I think there is one in the repositories here too!

An audio/visual company back home (Maritz) that was heavy into advertising skits had like 8 computers all linked together in a cluster.  And on the weekend tours they often had, they had a top o the line single computer running the same program they were running in the cluster.
The cluster finished in only a few seconds and the single computer took an entire week if not longer.  Depending which display they had going on for that particular tour.

It was like finishing a game of Solitaire on Doze 3.0 vs XP-Pro.  Took about 3 minutes for the piles of cards to peel away on 3.0 and on XP it was so fast you didn't even see it happen, hi hi.............

TTUL
Gary

---

### Post by lunoob on 2008-12-13
> **3dz said:**
> I went to the Linux graphic user web site and, you seem to have really good knowledge of texturing.  One of my weak areas.  It's nice to connect with a fellow Blender'er.<?  

I'm not all that great with textures yet, but I've found that I can find the help I need over there (linuxgrphicsusers.com).  I have to keep going back to review what I've "learned" but failed to retain.


> **3dz said:**
> I've been working with 3d modeling for a few years now, but I have only been working with Blender for a few months.  I do tutorials from super3boy also.  Anything with particles and modifiers.  He seem young but, that's what I think makes him so easy to understand.  He translates things in layman's terms.

Yup. I agree wholeheartedly - at least for beginners like me. ;)  

> **3dz said:**
> Here's something I have been working on: 
[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/keepper.jpg[/IMG]
I did the top half in MakeHuman and, the bottom half in Wings3d.  Now I want to texture it, and rigg it, in Blender.

Holy smokes!! That's a pretty cool looking model.  I'd like to see a render. :)

Can you send me the file?  If I can figure out how to open it in Blender, I could play with textures.

If you bop over to LGU (linuxgraphicsusers), I'm pretty sure they (we) could help you get where you're going.  I'm also pretty sure everyone over there would be happy to hear from you.  I know I would.  

> **3dz said:**
> Thanks for link to Debian repositories.  I'm a newbie with Linux, and still trying to get my USB 727 wireless EVDO modem, to connect with Ubuntu.  I think I know what is wrong.  Ubuntu sees it as a mass storage device.  In one of the How To's, I found on this forum.  It directs you to insert the ministorage card, and enters some code in the terminal.  I need to order the ministorage card, for it.  This is something that I've been trying to do for months now.
I'm slows as a turtle but, I keep hammering at it.
I'm wondering if it would be easier, just to purchase a repository CD?  

I'm with you . . . I bump my head on all kinds of issues.  But I just got Ubuntu installed in a Virtual Machine, apparently with everything working except for sound.  Ah, well . . .

I like Intrepid as compared to Feisty, the last 'Buntu I installed.  And I like Ubuntu in general, but not enough to call it home.  Thus, I would recommend checking out the vast possibilities before committing to one flavour of Linux.  I would not recommend paying for a CD you can (did) download as an .iso file, unless you simply want to donate money to Ubuntu for whatever reasons you may have - unless they include some kind of 'magic' in the purchased CD.  But I haven't yet heard of that.

As I understand it, Mepis linux has excellent hardware detection, and a great community full of really smart geek-type folks willing to help with difficulties. 
 
> **3dz said:**
> A lot of things I've been wondering.  I've been wondering if I should go back to Ubuntu studio.  I had no problems with Blender in studio.  But, I read somewhere, that Ubuntu studio is having problems with multiple cores in their new release.

I'm clueless . . .

> **3dz said:**
> PS. Here is a good site for Blender video tutorials: [blenderunderground.com/video-tutorials/]("http://blenderunderground.com/video-tutorials/")

Yup . . . already had it bookmarked. :D

---

### Post by 3dz on 2008-12-13
Hi Kellemora
> An audio/visual company back home (Maritz) that was heavy into advertising skits had like 8 computers all linked together in a cluster. And on the weekend tours they often had, they had a top o the line single computer running the same program they were running in the cluster.
The cluster finished in only a few seconds and the single computer took an entire week if not longer. Depending which display they had going on for that particular tour.

That sounds exactly like what I want to do. Although I'd never heard it called clusters before.
What you explained, is connecting computers with NIC cards.  This is something I haven't really given much thought about.
My computer have, built-in lanes. Your suggestion, gave me an idea.  I could go wireless and, forget about running all those Cat5 cables.  One of those 802.11 G WiFi Lane.  
From what I understand, they process 54 MB per second. Then I could keep all the computers in a separate room.
Many thanks for the idea! :D

---

### Post by 3dz on 2008-12-13
> I'm not all that great with textures yet, but I've found that I can find the help I need over there (linuxgrphicsusers.com). I have to keep going back to review what I've "learned" but failed to retain

The story of my life.  But I've always found it easier the second time around.

> Can you send me the file? If I can figure out how to open it in Blender, I could play with textures.

If I send you a Wavefont (.obj). You can import it into Blender. I just need to swap the axes around, so it will import correctly.  As soon as I get it ready, I'll send it to you.

 > I would recommend checking out the vast possibilities before committing to one flavour of Linux.

I've been testing out flavors all summer long.  I probably went through about 16 to 18 distributions.  I've found that Ubuntu has the best community support.  I did go back, and took another look at Ubuntu studio.  I upgraded Blender to version 2.46. That's as far as I can upgrade it, in Gusty.  But it did work fine, with no problems.  

By the looks of it, it seems like I'm having a problem with the NVIDIA driver. Something about a glx.  I get this error, when I try to enable desktop visual effects.

[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/enable_driver.png[/IMG]
[IMG]http://www.geocities.com/siteandsound2000/online_pics/ubuntu/glx.png[/IMG]

Now I'm wondering if I upgrade to Ubuntu studio, Hardy Harrison.  Desktop effects might work.  I have the NVIDIA 7200 PCI express graphics card.  "Blender should look really good then."
What I'm thinking, I am just using a standard graphics driver.

Thank you for the invitation to the LGU. Sure, I would like to play with other artists. ):P

---

### Post by Kellemora on 2008-12-13
Hi 3dZ

I'm new to Linux and in my process of trying to learn things I downloaded Edubuntu onto one of my computers.  I liked that idea, except I don't need Thin clients with all the full blown computers around here, and I also found out I needed quite a bit of memory for each workstation.  Also that speed would suffer considerably as well.

So, in an attempt to learn even more, and remembering what I saw at Maritz, I did some searching on-line.  Took me FOREVER to find the RIGHT WORDS to use in the search engine, but once I stumbled across the word CLUSTER, wow, lots of web sites, from the most simple systems to highly complex 260 computers all clustered together came popping up.

The Beowolf Cluster is one of the largest I found, but was naturally more interested in small simple make your owns.
I do a lot of graphics work myself, but nothing like you are doing.  I published newsletters, pamphlets and on occasion a yearbook for a small school.  Cut most of this back to nil when I moved south, but still get requests, enough so it keeps me busy.

Just the difference a dual core processor makes is amazing.  So if I tied a couple of these together, the processing time should go up more than fourfold, based on the things I've read about it.

If you type simple computer cluster in a web browser, I think you will hit most of the same web sites I did, some even explain step by step how to put 2 and 4 computer systems together.  But at the time I was reading it, much of what was being said was still above my head.  I know it takes a controlling program to handle it and that I think it's here in our repositories for Ubuntu.

But, that's the extent of my knowledge, other than seeing some first hand and they DO make for Power Computers, that's for sure!
Also, I think that is how many businesses are going these days too, based on the number of computers I see lined up in the racks at places, even here in the sticks, hi hi.........

Oh, I looked up on line what you were talking about in your opening post.  That stuff is really powerful!  Neat too!

TTUL
Gary

---

### Post by 3dz on 2008-12-14
> I liked that idea, except I don't need Thin clients with all the full blown computers around here, and I also found out I needed quite a bit of memory for each workstation. 

My clients aren't full-blown computers.  I only have three client, the largest is a Pentium 4, 3 GHz processor with hyperthreading capability, that I built last year.  The smallest is a 1.8 GHz Pentium 4, that a friend built for me six or seven years ago.  The one in the middle is a 2.66 GHz Pentium 4, that I purchased on sale few years back.
This server will be the computer I'm using now, that I put together eight months ago. 

 My jaw dropped to the ground, when I found out how inexpensive memory was.  I just purchased CORSAIR TWIN2X4096-6400C5 4gb kit 2gb x 2 pc26400 800mhz matched pair 5-5-5-18 240-pin ddr2 dimm.  
After I send in the rebate, it only cost me $22.50.
A lot of people must of jumped on that deal.  I went back today, and they're sold out.

> Just the difference a dual core processor makes is amazing. So if I tied a couple of these together, the processing time should go up more than fourfold, based on the things I've read about it. 

I'm also using a dual core processor, I'm thinking the same thing.  And yes, I am amazed at the processing speed.

I just found out my motherboard can be upgraded to a EM64T quad core processor. This really got me excited!
But I'm wondering, if 32-bit and 64-bit, play well together?

> If you type simple computer cluster in a web browser, I think you will hit most of the same web sites I did, some even explain step by step how to put 2 and 4 computer systems together. But at the time I was reading it, much of what was being said was still above my head. I know it takes a controlling program to handle it and that I think it's here in our repositories for Ubuntu. 

I believe so.  I thought this site explained it well:
[URL="http://www.scl.ameslab.gov/Projects/parallel_computing/cluster_basics.html"]What is a Cluster Computer?
[/URL]
They have a four computer diagram that helps explain it.

Awhile ago I remember reading something called (repu), not sure on the name though.  Does that sound like the name of the controlling program? ):P

---

### Post by Kellemora on 2008-12-14
Hi 3dz

I think the names of the programs I was speaking of are
GNU Queue and Dr Queue.

I've been looking for the pages I stumbled across on low-cost simple Clusters using sometimes only two computers and haven't found it again.

I will take a look again after I get my work done here and post a few web sites you may be interested in.

One style of massive systems is the Beowulf Cluster, interesting read but unpractical for home use, hi hi........

But here is a page that explains some of the different types.
[http://ainkaboot.co.uk/cluster-architecture.php]("http://ainkaboot.co.uk/cluster-architecture.php")

I'll get back to you in about an hour, I hope!

TTUL
Gary

---

### Post by Kellemora on 2008-12-14
Hi 3dz

Still haven't found the particular web site I'm looking for, but stumbled across this one while searching and it fairly well highlights setting up a system, requirements, etc.

[http://www.mcsr.olemiss.edu/bookshelf/articles/how_to_build_a_cluster.html]("http://www.mcsr.olemiss.edu/bookshelf/articles/how_to_build_a_cluster.html")

And here is one using an AMD and an Intel two computers
[http://www.linuxjournal.com/article/5862]("http://www.linuxjournal.com/article/5862")

I don't know if I sent you this before, this fellow does a TV show that requires extensive rendering.  I know it's bigger and faster than what you may need, but there is a lot of tips along with his display on building his system that you might pick up on.
[http://helmer.sfe.se/]("http://helmer.sfe.se/")

I never did find the one the two boys built using 4 very old and very used computers they were going to toss out.  They used a more modern computer as the controller.  I think the 4 machines they used were old Windows 98 boxes ready for the trash pile.  But the controlling NODE, the main computer made good use of those antiques and made it possible for them to do on their machine something that would have otherwise been nearly impossible.  They were also serving a classroom of 23 geology students temporarily using this system with no lag time while the schools computer was being updated.

I phoned my brother as well, he's not into computers but knows pretty much stuff about the company next door to him.  They are running 16 Windows 2003 Servers clustered, using ONLY Micro$oft software for Cluster Server 2003.  They don't have anything fancy like Rack mounted equipment, it's just row after row after row of 4 stand alone HP PCs on each shelf, 4 tiers high.  Lot's of wires and cables, hi hi.
They have one monitor for each tier of 4 computers using a KVM switch to see each computer separately.
The company provides a small percentage of the video on demand shows piped through their local cable TV company, their primary contractor.  They also provide data storage for area businesses, which is how they first started out.  I think they were looking at becoming an ISP about the time they switched to distributing video and landed that contract.

I think you would know more about what you do and be able to hit the more appropriate web sites more in tune with what you do.

I started checking into it, only because I was studying Edubuntu and thin clients and could see how running a server and client system would really bog down without a powerful computer with tons of memory.
What interested me the most was I hit an article about a company that had standard computers at each desk, rather than workstations and a server.  They had a file server of course, but the work they were doing was intensive.  So they just beefed up the Network from 10/100 Ethernet to 1 gig Nic's and pulled the all together so that CPU's that were idling so to speak were put to use for the whole.  I didn't understand much of what they were talking about and was mainly just interested in the concept.
Because I have 8 computers in use here and a few sitting idle.  And only a couple of them are usually bogged down running programs that need a lot of CPU power.
But, as I said, it was still way over my head what they did!

But if you have time, just do some web surfing about clusters and pick n chose those that seem to be up your alley.  The info gleaned from each article, when put together for your purposes can possibly be very rewarding.

Good Luck my friend!

TTUL
Gary

---

### Post by 3dz on 2008-12-14
> I liked that idea, except I don't need Thin clients with all the full blown computers around here, and I also found out I needed quite a bit of memory for each workstation. Also that speed would suffer considerably as well. 

Oh, I think I see the confusion here.  Maybe this will help, IEEE 802.11g ..... The way I understand 802.11, it is a standart for WiFi frequency.  The g is for what version.  The way it was printed, it was misleading.  There is quite a bit of confusion about megabits and megabytes.  I was taught to abbreviate megabit like (Mb), and megabyte like (MB). That card only processes 54 Mb per second.  Considering there are 8 bit to 1 byte, the difference is considerable.  In this case, 378 bits. ](*,)

---

### Post by 3dz on 2008-12-14
> But here is a page that explains some of the different types.

No doubt in my mind, this is what I wanna do.  The render farm configuration is exactly the architecture I'm looking for.  Many thanks! :D

---

### Post by 3dz on 2008-12-14
> I don't know if I sent you this before, this fellow does a TV show that requires extensive rendering. I know it's bigger and faster than what you may need, but there is a lot of tips along with his display on building his system that you might pick up on.

Actually, this is what I would like to build up to.  A lot of good information.  Last time I got this excited looking at pictures, there was nudity. lol

I'm into building computers.
[IMG]http://www.geocities.com/siteandsound2000/online_pics/pc_stuff/start.jpg[/IMG]
[IMG]http://www.geocities.com/siteandsound2000/online_pics/pc_stuff/pc-before.jpg[/IMG]
[IMG]http://www.geocities.com/siteandsound2000/online_pics/pc_stuff/after.jpg[/IMG]

>  I never did find the one the two boys built using 4 very old and very used computers they were going to toss out. They used a more modern computer as the controller. I think the 4 machines they used were old Windows 98 boxes ready for the trash pile. But the controlling NODE, the main computer made good use of those antiques and made it possible for them to do on their machine something that would have otherwise been nearly impossible. They were also serving a classroom of 23 geology students temporarily using this system with no lag time while the schools computer was being updated. 

I like reading this kind of stuff.  I find that 90% of the computers that are being thrown out, just have a software problem.

> Lot's of wires and cables, hi hi.
They have one monitor for each tier of 4 computers using a KVM switch to see each computer separately. 

One word, Synergy.

[URL="http://www.youtube.com/watch?v=UdP1Rei2muw&feature=related"]How to use Synergy
[/URL][24 monitors]("http://www.youtube.com/watch?v=cqB01Cp_wPM&feature=related")
[URL="http://www.youtube.com/watch?v=Id3GHAruhAk&NR=1"]7 Screen Synergy w/ Mac/Windows/Linux
[/URL]
                        ):P

---

### Post by Kennedy Bushnell on 2008-12-14
I have been looking into making a server farm for some time for my company.  Alot easier to do than you would think.  I would really suggest going hard wired though, I hate wireless with a passion.  I think its only good use is in laptops.

But, regarding a previous post made by you about 32-bit and 64-bit processors.  You asked if they play together nicely and I read that as 'do 32-bit and 64-bit applications play together nicely'.  Yes, they do very well on Windows x64 editions, I am not sure if Linux has a good 32 bit emulator yet(I am a Windows guru, although not incredibly new to Linux).  I have an workstation that is x64 running XP that would be enough computer to do what you are wanting to do on its own. It only cost me $600 to make as well.

My suggest would be to wait and slowly buy the parts and build a PC.

My specs:

2xXeon 3.4ghz 64bit processors (HT, and dual core)
10gb RAM
3x32gb Raptor drives (RAID)
500gb storage drive
Firewire on board
Like 8 USB 2.0
Can't remember all the other stuff, this thing is loaded

Basically, just use Craigslist, eBay, Buy.com, Directron.com, Amazon.com and cycle through them constantly to find out where the deals are, slowly buy the pieces and when you get it done, you won't regret it, and the money you save will blow you away.

---

### Post by 3dz on 2008-12-16
Thank you, for the advice on bargain-hunting.  However thogh, I don't share your enthusiasm for windows.  
I will miss some creative programs, but I won't miss the corrupted files, missing dll's, and all those viruses.

):P

---

### Post by dmn_clown on 2009-01-08
> **Kellemora said:**
> I think the names of the programs I was speaking of are GNU Queue and Dr Queue.

GNU Queue is dead in the water unless someone else takes over development (no commits for 15 months with a resignation notice on its Savannah page[1]  ) Dr. Queue is actively developed free software you only need to pay if you want support.  I highly suggest building this from source to avoid the age and the bugs of the Debian package.

You can in theory use CUPS[2] however, as that article implies, it is not so great when you are using shadow, environment, or cube maps as there is no way to make a job depend on another job, as you can in Dr. Queue.

[1] [http://savannah.gnu.org/projects/gnu-queue/](http://savannah.gnu.org/projects/gnu-queue/)
[2] [http://rendermania.com/building-a-renderfarm-with-cups/](http://rendermania.com/building-a-renderfarm-with-cups/)

---

### Post by ajt on 2009-01-12
Hello,

I've started a new discussion, to try and bring together threads in different forums about Ubuntu clustering at:

[http://ubuntuforums.org/showthread.php?p=6495259]("http://ubuntuforums.org/showthread.php?p=6495259")

    Tony.

---

