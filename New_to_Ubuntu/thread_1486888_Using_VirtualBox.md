---
title: "Using VirtualBox"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-18
I had 10.04 installed and operational but couldn't figure out VirtualBox and get it to work. I was doing something and caused a format of the hard drive so I'm back to ground zero. I've installed the Vista that came with my laptop but would rather go 10.04 solo but I do have a few things that require windows to operate properly so I need to use something to make that possible.

I checked out Wine but, according to the compatibility list, what I need to use is not compatible.

VirtualBox looks like the right alternative but the problem I was having was I was unable to do installation(s) of what I wanted access to. However, in my middle of the night brain spasms I had one that got me to thinking along this line:

I did install XP in the VBox then tried to install a couple of programs but VBox did not recognize that I had anything in the cd drive. My warped mind thought that I needed to install everything in the XP for it to be usable. Was that my mistake?
Do I just install all of the "stuff" in VBox, not _"in"_ XP in VBox, and it finds the XP to make it workable?

I've spent the last 3 days looking for an answer to this question, but to no avail. Not in the VBox manual, not in any of the forums I've visited, nowhere under Google. 

ANYbody use VBox able to answer me with the proper steps to take when installing programs like Sony Ericsson PC Suite or Magellan Explorist/MapSend TOPO?

](*,)

---

### Post by Chesamo on 2010-05-18
You can't install programs in VBox, it's just a virtual computing environment. You install the programs into the guest OS.

Did you make sure to mount the CD drive (your physical CD drive is located at /media/cdrom0) on the guest OS?

---

### Post by flyfishingphil on 2010-05-18
> **Chesamo said:**
> You can't install programs in VBox, it's just a virtual computing environment. You install the programs into the guest OS.

Did you make sure to mount the CD drive (your physical CD drive is located at /media/cdrom0) on the guest OS?
That may have been the problem. When I would put a cd in the disc it wouldn't show. I didn't see anything about mounting the cd. Where do I find the directions for that? (I'm printing everything I can find and building my own book. I may turn it into a "for Dummies" style file and offer it thru here for free.)

Another question along the same line. If I open up 10.04 for "trial" could I install the VBox in that, test it, then do an actual install and carry that with it. (Just trying to figure out the "easiest" way to test it before I do the total changeover.)

---

### Post by howefield on 2010-05-18
> **flyfishingphil said:**
> ...the proper steps to take when installing programs like Sony Ericsson PC Suite or Magellan Explorist/MapSend TOPO?

Installing software into your virtual guest is exactly the same as installing in a "real" system. I'd guess Chesamo is spot on with the CD drive not being mounted. 

There are a load of video tutorials on the Virtualbox website, might be worth viewing some.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

---

### Post by flyfishingphil on 2010-05-18
> **howefield said:**
> Installing software into your virtual guest is exactly the same as installing in a "real" system. I'd guess Chesamo is spot on with the CD drive not being mounted. 

There are a load of video tutorials on the Virtualbox website, might be worth viewing some.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)
I just ran and checked that one out howefield. First one looked good. Do you know if the additional that he added was from VirtualBox? I got the impression he was doing that from a disc. Is it advisable to download the VBox and set it to a disc before installing? Any particular format for that?

Finally! Getting answers and it looks much more appealing to go 10.04 solo OS!

---

### Post by howefield on 2010-05-18
> **flyfishingphil said:**
> Do you know if the additional that he added was from VirtualBox? I got the impression he was doing that from a disc. Is it advisable to download the VBox and set it to a disc before installing? Any particular format for that?


I'm sorry, I don't understand the question ?

---

### Post by flyfishingphil on 2010-05-18
> **howefield said:**
> I'm sorry, I don't understand the question ?
In the first video, on the site you recommended, as he goes thru the steps and gets towards the end, it appears that he is doing the VBox installation from a disc. He then makes some adjustments involving a disc, but nothing was said about using a disc for the installation he was doing.

Was wondering if I need to burn the VBox installation to a disc for better installation, or not.

Another question. Somewhere in my travels I saw something about "don't use the OSE version because it won't recognize USB use. Get PUEL instead if you want to do anything with USB". Are you aware of this? Both my cell phone and my GPS attach using USB. Not much gained if USB doesn't connect. If that's the case which version of VBox do I need? Is that at VBox, or some other site?

---

### Post by howefield on 2010-05-18
> **flyfishingphil said:**
> I saw something about "don't use the OSE version because it won't recognize USB use. Get PUEL instead if you want to do anything with USB".

I'll come back to the first question.

As for the different editions of Virtualbox, the version in the Ubuntu repository that you can download with Synaptic Package Manager is the OSE version, "Open Source Edition".

The version on the virtualbox website is the PUEL version, "Personal Use and Evaluation Licence" PUEL version includes closed source code which amongst other things give you the ability to use USB devices.

So yes, if you need USB connectivity in your guests, PUEL is the way to go.

Download the .deb package for your architecture and Ubuntu version from ...

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by flyfishingphil on 2010-05-18
OK, downloaded and put on cd so I'll have that handy when I install over to 10.04. Guess all that's left is to plug 10.04 in, get all of the updates, install the VBox and see what happens.

If you open another post from me, and there are red speckles all over the page, you'll know I messed up again and cut my head off. Be patient and maybe the next time I reply I'll be doing it from 10.04.:lol:

---

### Post by howefield on 2010-05-18
> **flyfishingphil said:**
> In the first video, on the site you recommended, as he goes thru the steps and gets towards the end, it appears that he is doing the VBox installation from a disc. He then makes some adjustments involving a disc, but nothing was said about using a disc for the installation he was doing.

Was wondering if I need to burn the VBox installation to a disc for better installation, or not.

I'm still not completely sure what you are asking.

The steps you'll need to take to install virtualbox and guest are as follows...

1. Download the relevant .deb package for your version of Ubuntu.
2. Double click the file to start virtualbox installation.
3. Create the environment/settings for your guest in Virtualbox.
4. Install guest pretty much as you would for a "real" install.

Does that help ?

---

### Post by flyfishingphil on 2010-05-18
> **howefield said:**
> I'm still not completely sure what you are asking.

The steps you'll need to take to install virtualbox and guest are as follows...

1. Download the relevant .deb package for your version of Ubuntu.
2. Double click the file to start virtualbox installation.
3. Create the environment/settings for your guest in Virtualbox.
4. Install guest pretty much as you would for a "real" install.

Does that help ?
Gues my last response didn't make it thru. Did the download and put the VBox, ver 3.1_3.1.8-61349 Ubuntu~Lucid~i386.deb, on a cd. Will try that now but this time I will take the time to read all the way thru the users manual before I do anything else. 

(If you suddenly see red spots all over this page you'll know it got to me and my head exploded. Limited room in there for knowledge!:popcorn:

EDIT: Got the XP installed in the VBox. Also added in both printers and the SE PC Suite for the cell but it doesn't connect via USB. Just wondering if I have to do that device/usb thing for that. Didn't have to do that for the HP printer. I'll check that out later. Haven't tried the Magellan yet, but used the manual and it wall went pretty easy.

Also figured out the part about the video and the disc he was using. This was a real DUH! As I progressed thru, following the steps, I realized what he actually had was the XP disc. Still a little unsure of what all I might need to do, but no rush there.

Now I'll go to work on bringing everything else up to speed in 10.04.

Thanks for the assists. Guess this one is SOLVED for now.

Phil:P

---

