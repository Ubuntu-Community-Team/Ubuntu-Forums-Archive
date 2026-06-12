---
title: "Ubuntu for small office use"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-06
Apologies for redundancy...

My uncle called me the other day and asked me to get Windows XP/Vista for his 2 PC based office,where he runs his business. He uses PCs for accounting,internet,printing,documents etc, typical MS-Office stuff (outlook not needed).

I started Ubuntu since yesterday on my dual-boot laptop with Vista and wondering if I can recommend Ubuntu to him, which also saves money on Vista licenses.

I think I can install Ubuntu on the PCs,either with partition or inside Windows etc
and educate the users on openoffice,firefox,thunderbird as am a techie, by profession.

[http://ubuntuforums.org/showthread.php?t=793206](http://ubuntuforums.org/showthread.php?t=793206)

This thread gave a lot of input and raised my confidence level on recommending Ubuntu, for small office setup and beware/caution details, but what do you think?

I'm not yet familiar with Fedora or Kubuntu,if that's what you'd recommend...

TIA

---

### Post by nhasian on 2009-05-06
ideally you want to install ubuntu on its own partition.  you can use wubi to install it inside of windows, but it will be slower :(

---

### Post by robertron76 on 2009-05-06
> **nhasian said:**
> ideally you want to install ubuntu on its own partition.  you can use wubi to install it inside of windows, but it will be slower :(

Yep, am definitely planning on installing Ubuntu on a separate partition, if Ubuntu is decided.That's the setup I have on my notebook and it makes my life easier.

the other basic question is, if there's any loss of data or Ubuntu system crash,am afraid I'll be the "Sys Admin" for them to recover?

honestly, what's the crash frequency of Ubuntu 8.04 LTS, Desktop/Server? better or less than Windows XP/Vista? that's the concern.

Or would they be better off with Windows, instead of Ubuntu?

---

### Post by Didius Falco on 2009-05-06
I think Ubuntu would be an easier transition for most Windows users.

Kubuntu desktop is nice, but it's really focused on the flashier side of things - animated windows, desktop effects, etc. Probably things your Uncle wouldn't be as interested in for his office.

The first thing I'd suggest is, just to be positive, check the Ubuntu hardware compatibility list and make sure everything on his two systems will work:

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

You might also consider getting the last LTS (Long Term Support) Which would be Ubuntu  8.04 Hardy Heron. That version will be supported until April of next year, when the next LTS version will come out.

With you being a techie, and this forum a great resource, you should be fine. 

Of course, if the combination of your tech knowledge, this forum and the wealth of information on the net isn't enough, Canonical does sell support contracts. 

I was just in a thread with a librarian from Alabama that is converting the 5 computers in her library over to Ubuntu. She's no techie - yet, but with about 24 hours she was getting the hang of it.

By the time your Uncle adds up all the money he'll save on the o/s and all the software, he should be well pleased.

---

### Post by el.norman on 2009-05-06
If you dont want to use wubi, the use a virtual machine in the windows system to boot in ubuntu

---

### Post by robertron76 on 2009-05-06
> **Didius Falco said:**
> I think Ubuntu would be an easier transition for most Windows users.

Kubuntu desktop is nice, but it's really focused on the flashier side of things - animated windows, desktop effects, etc. Probably things your Uncle wouldn't be as interested in for his office.

I was just in a thread with a librarian from Alabama that is converting the 5 computers in her library over to Ubuntu. She's no techie - yet, but with about 24 hours she was getting the hang of it.

By the time your Uncle adds up all the money he'll save on the o/s and all the software, he should be well pleased.

Didius Falco, your reference on Library Setup in Alabama, is a real boost on my efforts, and my uncle knows PCs, more than an average person,so am relived.

am a pessimist, by birth/nature, hence the FUD, sorry about that :-)

I mentioned Kubuntu/Fedora, because in the thread, I quoted in my OP, it was mentioned (or I understood) that they are of more industrial strength than Ubuntu, hence I asked.

The only thing, I need to do is the back-up strategy of my uncle's business data, and if that's formed, then no worreis,I guess, because, am starting to think Ubunut as "piece of cake".... :-)

---

### Post by Didius Falco on 2009-05-06
> **robertron76 said:**
> Yep, am definitely planning on installing Ubuntu on a separate partition, if Ubuntu is decided.That's the setup I have on my notebook and it makes my life easier.

the other basic question is, if there's any loss of data or Ubuntu system crash,am afraid I'll be the "Sys Admin" for them to recover?

honestly, what's the crash frequency of Ubuntu 8.04 LTS, Desktop/Server? better or less than Windows XP/Vista? that's the concern.

Or would they be better off with Windows, instead of Ubuntu?

Once you get it set up for them, I'd say the chance of problems is pretty low, unless they like to tinker under the "hood" - just using Open Office and that kind of thing isn't likely to cause problems.

For a small office environment, I'd avoid server. It's really set up for just that purpose. It doesn't come with a desktop package, though you can install one.

The Ubuntu package comes with most of what you'd need right on the CD. BTW, Kubuntu is just Ubuntu, but with the KDE desktop environment instead of the Gnome desktop that comes stock with Ubuntu. You can install KDE in Ubuntu, or Gnome in Kubuntu. There a third one for older hardware called XFCE that comes with Xubuntu that you can install as well.

Thre are a lot of options for backups as well - you can use most Windows Imaging software, if your uncle already has some, there are a few Linux based ones FOSS ones, and there is a really nice little script written by one of the linux wizards right here called RemasterSys that make a bootable iso you can burn to CD or DVD that will install it back to the hard drive. That one is so easy that non-techies will pick it up in short order.

There are also incremental backup packages available as well.

I hope this helps...and in case your wondering, I don't work for Canonical. <G>

---

### Post by Sef on 2009-05-06
Ubuntu 8.04, hardy heron, is a long term stable release.   Kubuntu 8.04 is not.

---

### Post by eentonig on 2009-05-06
Before rushing in, make sure you check with your uncle what applications he uses and split them in 'must haves/business critical', 'frequent use', 'nice to haves' and see if you find alternatives for Ubuntu.

---

### Post by netwarriorwy on 2009-05-06
Also remember that in most offices they use a lot office programs, so as an advice I can tell you there are some bugs in Open Office 3.0.1 which make your tables crash so every time you open a .doc file saved in OpenOffice in Word it looks like crap. Install OpenOffice 3.0.0 it should be ok. 

Something I use also is converting my .doc files to .pdf when sending them...if the person who receives it has no need to edit it.

Adobe Acrobat Reader 8 is available for Ubuntu, so they can be more familiarized.

If they do some picture editing when making presentations try installing Kolourpaint is the most Paint like program I've found.

If they work with Access or Visio try installing Open Office Base and Draw.

If they need something like MS Project the Planner should help you. There is no program as good as Project right now, but for practical purposes Planner does its job.

Install the Device Manager using Aplications->Add/Remove...this may help you if you need to find your drivers in the future.

Hope that helps! :guitar:

---

