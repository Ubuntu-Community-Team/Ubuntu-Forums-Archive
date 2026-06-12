---
title: "Canon MP980 printer wont print from Desktop."
date: 2011-01-05
forum: New to Ubuntu
---

### Post by pittstopp on 2011-01-05
I am a really new user of Ubuntu, I had it installed by my IT folks on my desktop to get away from windows, loving it so far. I have no idea about anything on the technical side of it at all. IT folk are on holidays until the end of the month and this is driving me up the wall.

My printer is a Canon MP980, I go to print, the PC says Printing, the Printer lights up and says it is coming.  The PC Says printing finished, but nothing happens.

I saw the CUPS page and it detects my printer ect shows the information, so to me that is saying, there is a connection, the printer is recognised. I tried the print test page from there too, and it does the same thing, tells me it is printing, but nothing happens & shows this huge list of completed jobs.

I can print fine from my laptop to the printer, so the lead and connections are all good.

I would really appreciate any help or ideas.

thanks in advance
Kathy

---

### Post by bazzer on 2011-01-06
Hi.
Can you 'print to file' ok? For example, in Firefox, go to File>Print... and select the top option, "Print to File". Save it as a PDF and then open the resulting file - this will tell you if it's trying to print something or a blank page.

Have you removed the printer and added it again? System>Administration>Printing, select the printer, right click and delete it, then click the 'Add' button and follow your nose. I sometimes have issues when CUPS disconnects then reconnects, and all my printers tend to just 'not work' unless I restart CUPS or remove and replace them...

Just a couple of starting points. :)

---

### Post by pittstopp on 2011-01-06
Thank you so much bazzer for your reply.
I did as you suggested, I tried the Print to File, saved as a PDF.  I opened the file and I could see what I had saved ok. 

I also removed the printer and added it again.

It is still doing the same thing.  

I have no idea what program is being used to print, when I was talking about CUPs, I mean the web page online.  I read about it some place.

Rather frustrated not being able to get something to work, when I know it should be lol

---

### Post by walt.smith1960 on 2011-01-07
I learned that Canon's Asia or Europe sites sometimes have Linux drivers that the North American site doesn't have.  Unfortunately The MP980 doesn't list Linux support, just Win & OSX.  

Here is one resource although it may not be up to date:

[http://www.openprinting.org/printers/manufacturer/Canon](http://www.openprinting.org/printers/manufacturer/Canon)

It appears that the Canon "business class" i.e. Imagerunner MFDs do have Linux support from Canon.  Here is a random example:

[http://support-my.canon-asia.com/P/search?model=iR2020i&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-my.canon-asia.com/P/search?model=iR2020i&menu=download&filter=0&tagname=g_os&g_os=Linux)

Even more random.  The Pixma MP600 series does have Linux support, the MP 700, 800 & 900 series appear to not be supported. When it comes to printing & scanning under Linux HP & Brother do a pretty good job of supporting Linux, HP especially.   I wish I could be of more help.

---

### Post by pittstopp on 2011-01-07
Hi Walt, so basically you are saying my Printer is not Linux compatible?

Could I run it in windows, as my computer has that via Sunbox.
Thanks for your reply.

---

### Post by walt.smith1960 on 2011-01-07
I'm not familiar with Sunbox; is it like virtualbox or VMware?  It may be possible but I would not have a *clue* how to go about it.  I have 2 (or more:)) installations of Ubuntu.  One that I don't molest and one for experimenting.  I use an image of the functional partition to create a separate experimental partition.  Then if I screw up the experimental partition, I can delete it and start again.  In your situation I'd probably install the MP600 software and see what happens.  It probably wouldn't work but what the hey, no harm done, just uninstall it.  But don't do that on a partition that you need for day to day work.

[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon)

EDIT:

Look what I found.  It looks like this was using virtualbox:
[http://ubuntuforums.org/showthread.php?t=1656799](http://ubuntuforums.org/showthread.php?t=1656799)
 
If he used vbox to make it work, that means that he installed Windows in  vbox, and then installed the printer in that Windows system, to be  shared with others. Once this is done, you can use the "vboxtools"  package to automatically run that vbox VM in background whenever you  boot, and can install the "Windows shared" printer in your Ubuntu host  where it will work just as if it had been installed direct into Ubuntu  itself.

You do this through the CUPS interface; browse to [http://localhost:631]("http://localhost:631/")  to get to CUPS, than add the printer. The first screen of the "add"  process gives a list of possible places to find the printer, and  "Windows shared" is at the bottom of that list. From there, follow the  prompts and use "browse" when uncertain what to fill into a text box...

I had to do this for one of my printers; although it had a Linux driver  (unlike Kodak), there was a USB conflict between my VMs (required so  that I can support Win-only customers) and the host that made the Linux  driver lock up in mid-job. By setting it up so that the Linux host  accessed the printer as a "Windows share" rather than directly, the  problem went away. Performance doesn't seem to be hurt by the change,  either.

You'll need to have the Windows VM and the host system on the same network connections for this to work.

---

### Post by pittstopp on 2011-01-07
The Subbox thingo (Im am soooo not up with this linux stuff lol) is where I can use Windows if i need to.

what you are saying, sort of makes sense to me, as the IT fellow who put linux on for me, showed how to install games for the children onto Windows but run it in Linux if I needed to.

I will go and have a look and see what I come up with.  Thanks Again Walt, much appreciated :)

---

