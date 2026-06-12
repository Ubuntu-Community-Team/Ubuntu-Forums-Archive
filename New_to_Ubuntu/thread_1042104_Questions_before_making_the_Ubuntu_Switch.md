---
title: "Questions before making the Ubuntu Switch"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by TopKnot1 on 2009-01-17
I am going to install Ubuntu on a computer soon.  I have done this twice already but sometimes life gets in the way.  Now my life is more stable, I'm ready to make a commitment to learning and hopefully switching over to Ubuntu. 

The setup:
1.  Ubuntu will be installed on an older computer and I will KVM it.
2.  I must be able to network 2 Vista machine with this Ubuntu machine.
3.  I would like free access to the files on the two Vista machine via my home network.
4.  I have a personal website on a shared hosting plan.  I use an FTP program, DreamWeaver and Photoshop quite often.
5.  I have a http test server on my local Vista machine running XAMPP.

Some questions for the experts
1.  What version of Ubuntu do you recommend for my described uses?
2.  Is it hard to put Ubuntu on a local home network...remember I'm using MS Vista and it will remain the computer that has management responsibility for my network.  The Ubuntu machine will be a wireless connection.
3.  Is it possible to have full access to the files on all networked computers.  In that I would like to be able to grab a document or video or graphics from shared Vista directories and open them on the Ubuntu machine using whatever open source program to open/edit the file.
4.  Is there a semi-good alternative to DreamWeaver and PhotoShop available on Ubuntu?
5.  I assume that LAMP and webmin would be a good Ubuntu alternative to XAMPP?

Any help in answering these 5 questions would be helpful.

---

### Post by eilios on 2009-01-17
> **TopKnot1 said:**
> 
4.  Is there a semi-good alternative to DreamWeaver and PhotoShop available on Ubuntu?

Any help in answering these 5 questions would be helpful.
Well, GIMP is an excellent replacement to Photoshop. And i'm almost 100% sure Dreamweaver runs flawlessly with WINE.

---

### Post by mrbiggbrain on 2009-01-17
welocme back to ubuntu then!

i belive the program that is used for acessing windows networks is "samba" or "samaba share" i dont know if it comes preinstalled with any of the ubuntu's (i just dont use it for what i do) but it cant be hard to get from repositorys.

an alternative to photoshop is Gimpshop (where gimp (gnu image maniplulation program) it dosnt have all the tools, but its verry good, from what iv used the best, and photoshop users should feel comftorble with it, especily if its for moderate use.

I know on this lobby alot of people have listed dreamweaver equivilents. so they are out there.

the version id sujest depends on your rolling out of the product.

x.04 comes out the 4th month of every year like clockwork, well x.10 comes out the 10th month of every year.

7.xx are all from year 2007, well 8.xx are all from 2008 (the 4th and 10th months respectibly)

Linux is not know for takeing up alot of ram, but that dosnt mean running the newest release is always needed. if its an older computer, maybe xubuntu would be your best shot, or even installing fluxbox might be a good choice. theres a fluxbuntu outside the "officialy" supported realm.

if your useing wifi, its likely youll need to spend at least a little time getting the drivers up and running, though the kernel or your distro may already have support for the version of wireless card/adapter your useing.

---

### Post by fuser312 on 2009-01-17
> regarding dreamwever and photoshop
well gimp is a pretty good alternative for photoshop
you could look at the blue fish, quanta plus or kompozer for web development.
although you do always have option of running them through Wine.

> which version to use
always go for the latest version which in this case is 8.10
you could always use "xfce" desktop environment if you have to work with less RAM.

> networking vista and ubuntu wirelessly
you could do it without much hiccups.
check this link
[http://michaelvisser.com.au/blog/connecting-windows-vista-network-share-to-ubuntu-intrepid/](http://michaelvisser.com.au/blog/connecting-windows-vista-network-share-to-ubuntu-intrepid/)

and i think lamp is better than xampp.
good luck!

---

### Post by earthpigg on 2009-01-17
> Some questions for the experts
i am not an expert. im answering anyways ;)

> 1.  What version of Ubuntu do you recommend for my described uses?

8.04 is long term support... so you wont have to worry about changing anything for 3 years from the _fourth_ month of 200_8_. (hence, 8.04.. clever, huh?)

8.10 is a regular release, so you have 18 months of support from the _10_th month of 200_8_.

if security and having the latest software is not a concern, it really doesn't matter which version you pick... there are still folks running 6.06 and doing just fine (guess when that was released? :) ).

> 2.  Is it hard to put Ubuntu on a local home network...remember I'm using MS Vista and it will remain the computer that has management responsibility for my network.  The Ubuntu machine will be a wireless connection.

8.10 supported my wireless card out of the box, 8.04 did not.

> 4.  Is there a semi-good alternative to DreamWeaver and PhotoShop available on Ubuntu?

GIMP is about as full-featured as photoshop, but different interface. _G_NU _I_mage _M_anipulation _P_rogram. more cleverness.

being a noob, that is all i can answer.

---

### Post by seagullplayer77 on 2009-01-17
**1. What version of Ubuntu do you recommend for my described uses?**

It sounds like regular old Ubuntu would work just fine, although if it's an older computer and it runs slow, you might want to give Xubuntu a try. It's specifically designed to run on slower machines, so it might be a better fit. If you're into image editing and that sort of thing, I suppose you could try Ubuntu Studio, which is specifically designed for image/video/audio editing, but that's totally up to you. I'm pretty sure you can upgrade to Studio from regular Ubuntu after you get Ubuntu installed.

**2. Is it hard to put Ubuntu on a local home network...remember I'm using MS Vista and it will remain the computer that has management responsibility for my network. The Ubuntu machine will be a wireless connection.**

I can access my Windows network easier with Ubuntu than I can with Windows (go figure), although I'm not using Vista---I'm using XP. That being said, I think it would just be a matter of using Samba to get to your Windows network. The wireless connection can be kind of dicey...I've heard of some Ubuntu installs where wireless works straight out of the box, while others (like my own) take a few months of tinkering before you can get it working.

**3. Is it possible to have full access to the files on all networked computers. In that I would like to be able to grab a document or video or graphics from shared Vista directories and open them on the Ubuntu machine using whatever open source program to open/edit the file.**

You should be able to access your Vista machines with Ubuntu, but I don't think it'll be reciprocal. That is, I doubt you'll be able to access your Ubuntu machines with an Microsoft OS.

**4. Is there a semi-good alternative to DreamWeaver and PhotoShop available on Ubuntu?**

Don't know about DreamWeaver, but for PhotoShop, the GIMP is an excellent replacement.

**5. I assume that LAMP and webmin would be a good Ubuntu alternative to XAMPP?**

Your assumption would be correct. I'm running a web server with the LAMP stack, Apache, and Joomla! installed, and it works great.

---

### Post by TopKnot1 on 2009-01-17
I want to thank everyone who responded to my questions.  I feel like this process should go smoothly with GIMP, Samba and Lamp.  I'll cross my fingers when hooking up wirelessly to my home network and if things don't go good on that side I'll ethernet it.

Thanks again and I'm sure I be back within a few hours of my install.  Now I get to grab my old computer out of the attic and get it running.

:popcorn:

---

### Post by anjilslaire on 2009-01-17
> **seagullplayer77 said:**
> You should be able to access your Vista machines with Ubuntu, but I don't think it'll be reciprocal. That is, I doubt you'll be able to access your Ubuntu machines with an Microsoft OS.



You can share your Ubuntu files with Windows also by using Samba as a server on your ubunu system.

---

### Post by SanjoEel on 2009-01-17
I don't think Gimp is anywhere near as good as Photoshop, but I have PS 6 running flawlessly under WINE in Ubuntu. GIMP _is_ a "semi-good" alternative, though! Inkscape is great and opensource, and it's vector.

You should not have a problem networking with a Windows machine, but if you want to access your Ubuntu files from Windows then you will need to have your Ubuntu partition formatted as FAT32. Windows pretends that ext3 partitions do not even exist, LOL. Gotta love MS....

---

### Post by cariboo on 2009-01-17
SanjoEel:

> You should not have a problem networking with a Windows machine, but if you want to access your Ubuntu files from Windows then you will need to have your Ubuntu partition formatted as FAT32. Windows pretends that ext3 partitions do not even exist, LOL. Gotta love MS....

Please do some research before answering question, the OP was asking about accessing the files on the ubuntu computer from Vista. Samba is what allows Windows to access any file type on the network. I have a file server with about 800Gb of storage space, and all of it is formatted as ext3, Windows can access it without any problems. 

Jim

---

### Post by timjohn7 on 2009-01-17
Some questions for the experts

4.  Is there a semi-good alternative to DreamWeaver and PhotoShop available on Ubuntu?

Any help in answering these 5 questions would be helpful.[/QUOTE]

GIMP will enable you to do all graphics work that the average user does in Photoshop.  If you require CMYK separations install the separate+ plugin.  The interface is different to Photoshop, but after some hands-on practice you will be flying.  Make sure you visit the gimpuser forum... plenty of templates, tutorials and advice.

Kompozer will satisfy most average WYSIWYG website design and editing.  Great interface and very user-friendly.  Bluefish, Quanta Plus and Seamonkey are all more advanced with less friendly interfaces and more HTML oriented.  Difficult to recommend one without knowing your skill level, requirements and personal preference.  They are all free, so download them all and try them out! :)

---

### Post by theozzlives on 2009-01-17
I run Ubuntu on a 333 and 500 MHz computers w/256 MB RAM (the 500 being my web "server"). Of course most work is done on my laptop, but they all serve their purpose. Samba will allow you full network access. Crap I forgot your other questions, bummer first time.

---

