---
title: "cant scan with new hp deskjet f2210"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by unseenbeing on 2009-01-01
xsane doesnt see the scanner on my all-in-one printer

how can i get my scanner to work with my computer

---

### Post by expatCM on 2009-01-01
Do you know about this
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
I think it is also in the repositories

---

### Post by Kellemora on 2009-01-01
H usb

HP doesn't even support some of their Windows XP Scanners in all flavors of Windows XP that came in HP branded computers, so it's not odd that they have absolutely no support for Linux whatsoever.

They also will NOT release the information necessary for SANE to write drivers for them!

Some of HP's top selling scanners have not been solved/cracked by SANE to get them working on Linux.

Epson on the other hand IS releasing the necessary info to SANE so drivers can be written for Linux without the trial and error of cracking the codes the hard way.

Nonetheless, until a Manufacturer SUPPORTS Linux themselves, they won't be selling me any new hardware!
And in this economy, unless they WISE UP, they won't be around much longer to worry about them!

I for one would like to see HP's Home Division go under!
They fully support UNIX on all hi-end commercial stuff!  So they can't keep claiming they don't know how!  They just WON'T do it!
And after I found out HP does not support HP product on HP branded computers, NOTHING New with an HP logo will appear here ever again, unless they begin to fully support Linux!

I'm in the market for a new mid-range laser printer!
Just waiting and waiting until I find a Manufacturer that supports their OWN equipment is all!

TTUL
Gary

---

### Post by tashmooclam on 2009-01-01
Canoscan usb powered on ebay, problem solved. [http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=119&modelid=6623](http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&fcategoryid=119&modelid=6623)

---

### Post by tashmooclam on 2009-01-01
Complain and return the printer seek a refund. Mention that you use Linux. Tell them you simply cannot use this device. Not the response you were seeking, but these days they should be taking care of the customer or lose him/her.

---

### Post by eagle416 on 2009-01-01
I have a HP Deskjet all in one, and there's this neat program called HPLIP

Here's the link. You download and install (following installation instructions, there's CLI involved), and it tells Xsane how to do it.

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html")

-Edit- I had a similar problem, and that is how I solved it. Through my experiences, I feel that Tashmooclam is mistaken: HP is one of the best manufacturers to allow Linux compatability. Canon and Lexmark, I'v heard, are not so good.

---

### Post by unseenbeing on 2009-01-02
> **tashmooclam said:**
> Complain and return the printer seek a refund. Mention that you use Linux. Tell them you simply cannot use this device. Not the response you were seeking, but these days they should be taking care of the customer or lose him/her.

i received this as a christmas gift and wanted this printer.

> **eagle416 said:**
> I have a HP Deskjet all in one, and there's this neat program called HPLIP

Here's the link. You download and install (following installation instructions, there's CLI involved), and it tells Xsane how to do it.

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html]("http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html")



-Edit- I had a similar problem, and that is how I solved it. Through my experiences, I feel that Tashmooclam is mistaken: HP is one of the best manufacturers to allow Linux compatability. Canon and Lexmark, I'v heard, are not so good.
thank you for this reply   this was more along the lines of what i was looking for. i will give this a try

---

### Post by niteshifter on 2009-01-02
Hi,

You basically have three options:
1. Return / exchange the unit for one that will work.
2. Dual boot XP and Ubuntu.
3. Run XP as a virtual machine.

I have a Canoscan LiDE 70 - not supported in Linux. Grrrr. It was a gift, and like you I spec'd it to the giver (mistakenly thinking since the LiDE 30 works so would a 70).

I did #2 for a awhile - it sucks. You waste a lot of time re-booting.

I wound up doing #3 - running XP via VirtualBox. It's not the perfect solution, but it works OK - you can set things up so that XP will share a folder with Ubuntu.

---

### Post by forrestcupp on 2009-01-06
Boy, some of you guys need to think before you complain against companies like this.  Like others have already said, this printer works perfectly in Linux with HPLIP.  You don't need to take it back, and you don't need to whine to HP about not supporting Linux.  Just install the proper software, and it will work perfectly.

If people don't know what they're talking about, they should watch what they say.  HP is great for Linux.

---

### Post by sailor2001 on 2009-01-06
> **forrestcupp said:**
> Boy, some of you guys need to think before you complain against companies like this.  Like others have already said, this printer works perfectly in Linux with HPLIP.  You don't need to take it back, and you don't need to whine to HP about not supporting Linux.  Just install the proper software, and it will work perfectly.

If people don't know what they're talking about, they should watch what they say.  HP is great for Linux.

agree.......I have hp5610 all-in-one and have no trouble with it. hplip is in repositories

---

### Post by Captain_tux on 2009-01-06
> **forrestcupp said:**
> Boy, some of you guys need to think before you complain against companies like this.  Like others have already said, this printer works perfectly in Linux with HPLIP.  You don't need to take it back, and you don't need to whine to HP about not supporting Linux.  Just install the proper software, and it will work perfectly.

If people don't know what they're talking about, they should watch what they say.  HP is great for Linux.

+1 

I would add that, while sometimes a pain, people need to use the **Search** function... you'd be amazed at how similar, if not identical problems have already been solved, saving you time and frustration.

HPLIP worked wonders for me. Check out my post in another thread: [http://ubuntuforums.org/showthread.php?t=813149&highlight=5180](http://ubuntuforums.org/showthread.php?t=813149&highlight=5180)

---

### Post by richg on 2009-01-06
Ok, once again. 

Running Ubuntu 8.04 and updates are ok. New HP F2210 All in One printer. The printer portion installed just fine.
When I try to find a scanner using XSane I get a message, "No Devices Available".

**I searched the messages and found a solution someone used.**

It was suggested to use libsane-extras from Synaptic Package Manager which did not work.
I then saw a suggestion to use hpoj. That did it. 

Great scanner and printer for $29.95 US.

Rich

---

### Post by forrestcupp on 2009-01-06
> **richg said:**
> Ok, once again. 

Running Ubuntu 8.04 and updates are ok. New HP F2210 All in One printer. The printer portion installed just fine.
When I try to find a scanner using XSane I get a message, "No Devices Available".

**I searched the messages and found a solution someone used.**

It was suggested to use libsane-extras from Synaptic Package Manager which did not work.
I then saw a suggestion to use hpoj. That did it. 

Great scanner and printer for $29.95 US.

Rich
I wasn't complaining about you.  You did a good job.  You had a problem, found the solution, and posted that solution to help others with the same problem.  You did what was right, and your post is one thing that is helping me decide to buy that exact printer this week.

My complaint was against others in this thread who were bad mouthing HP and telling you to take it back and whine to HP about poor Linux support.  There's no reason for that attitude when there are plenty of solutions.  

Now Lexmark is a different story.  There aren't solutions for a lot of Lexmark printers.  They deserve to be badmouthed.  But HP is great for Linux.

---

### Post by reahjw6 on 2009-01-06
Hey i had same prob but as said above by sailor 2001 hplip works fine.
You will find it in the synaptic package mananger.
Reah

---

### Post by richg on 2009-01-06
It was not for you but the ones who are too lazy to search or are cluless. Anyone can make time to search and read. I guess if you are cluless, Linux is not for you. 

To be fair, there are people who love to Rant or want instant gratification.

I find answers for over 95 percent of my questions on many subjects by searching.

Opps, this turned into a Rant. :o

Rich

---

### Post by LIB53 on 2009-02-11
I have the exact same printer and I'm running Hardy. I got this to work by installing the latest HP Linux Toolbox with the automatic installer from their website. The one in the repositories is too old to support the scan function of the f2210 all-in-one. Apparently all version of HPLIP above 2.8.6 will work, so if you have intrepid, then i think it'll work.

here's a link: [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

I hope this helps anyone else with this problem.

---

### Post by Indian_Guy101 on 2009-02-11
All I can say is to check your connections and make sure that your all in one is turned on. I have the same printer and it recognized it from the start. I didn't have to install anything else

---

