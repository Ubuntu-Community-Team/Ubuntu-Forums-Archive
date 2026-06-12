---
title: "Can't print PDF files - Help"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by crjackson on 2010-05-15
Here's my problem.

Every time I try to print PDF files using either evince OR Acrobat Reader 9, only the 1st & 2nd page will print.

It throws an error (see attachments).

I've tried changing every setting I can think of to no avail.  I didn't used to get these errors, but every version of Ubuntu after 8.04 forces me to load windows just to print PDF files painlessly.

The printer is a Dell 5100cn (Color / Laser / Network) connected directly by USB cable.  I comes with Linux printing drivers.  It works perfectly with every other printing task.  I can even open the PDF file using OpenOffice (with the PDF plugin) and it will print fine, but what a PIA that is on a long PDF file (read: ebook).

**Can someone help with this please?**

---

### Post by XCan on 2010-05-15
I have had that error as well, but only while using Adobe Reader. If it now happens both in Reader and Evince, that's a major reason not to upgrade to Lucid for me.

---

### Post by Paddy Landau on 2010-05-15
I had a similar problem with 9.04 some time ago. If I remember correctly, I uninstalled the printer and reinstalled it, and that fixed it.

I upgraded to Lucid recently and the problem has not recurred.

---

### Post by crjackson on 2010-05-15
> **Paddy Landau said:**
> I had a similar problem with 9.04 some time ago. If I remember correctly, I uninstalled the printer and reinstalled it, and that fixed it.

I upgraded to Lucid recently and the problem has not recurred.

I'll give that a try and see what happens.  It's been plaguing me for several versions now so I'm not very optimistic about it helping.

---

### Post by crjackson on 2010-05-15
> **Paddy Landau said:**
> I had a similar problem with 9.04 some time ago. If I remember correctly, I uninstalled the printer and reinstalled it, and that fixed it.

I upgraded to Lucid recently and the problem has not recurred.

Okay, that didn't work.

Anything else to try?

---

### Post by Paddy Landau on 2010-05-15
I just Googled this. Look at [the results]("http://www.google.com/search?hl=&q=ubuntu+%22print+error%22+%22there+was+a+problem+processing+document%22&sourceid=navclient-ff&rlz=1B3GGGL_enGB285GB285&ie=UTF-8"). I think it may be a bug come to life again.

I suggest that you search for a [bug report]("https://launchpad.net/"), and if not reported, then report it.

In the meantime, print only two pages at a time. :(

Good luck.

---

### Post by crjackson on 2010-05-15
> **Paddy Landau said:**
> I just Googled this. Look at [the results]("http://www.google.com/search?hl=&q=ubuntu+%22print+error%22+%22there+was+a+problem+processing+document%22&sourceid=navclient-ff&rlz=1B3GGGL_enGB285GB285&ie=UTF-8"). I think it may be a bug come to life again.

I suggest that you search for a [bug report]("https://launchpad.net/"), and if not reported, then report it.

In the meantime, print only two pages at a time. :(

Good luck.

I hate to say it, but I guess I'll boot to windows for printing of PDF's.  When a document is 200 pages, you can't just print 2 pages at a time.

---

### Post by crjackson on 2010-05-15
> **Paddy Landau said:**
> I just Googled this. Look at [the results]("http://www.google.com/search?hl=&q=ubuntu+%22print+error%22+%22there+was+a+problem+processing+document%22&sourceid=navclient-ff&rlz=1B3GGGL_enGB285GB285&ie=UTF-8"). I think it may be a bug come to life again.

I suggest that you search for a [bug report]("https://launchpad.net/"), and if not reported, then report it.

In the meantime, print only two pages at a time. :(

Good luck.

Looks like there has been bug reports file against this for years and it's ignored.

I guess MS Windows is my only option.  It's the little crap like this that turns people away from Ubuntu.

I try to Never use windows but lets face it, sometimes when you need something to WORK PROPERLY right now, you have to boot windows.

I HATE THAT!

---

### Post by bennachie on 2010-05-15
I can't replicate this bug on any of the four machines that I have running Lucid, either with Evince or Acrobat Reader. I have, however, had similar problems in the past, and worked around them successfully by running Print Preview, then printing the document from that environment. YMMV!

I can only agree that to have this problem arise again, long after it seemed to have been resolved, is disappointing and surprising.

---

### Post by crjackson on 2010-05-15
> **bennachie said:**
> I can't replicate this bug on any of the four machines that I have running Lucid, either with Evince or Acrobat Reader. I have, however, had similar problems in the past, and worked around them successfully by running Print Preview, then printing the document from that environment. YMMV!

I can only agree that to have this problem arise again, long after it seemed to have been resolved, is disappointing and surprising.

I'll give it a try, but I'm not feeling too lucky about this right now.  It's really starting to **** me off.

---

### Post by crjackson on 2010-05-15
That didn't work either.

---

### Post by bennachie on 2010-05-15
Sorry to have wasted your time.

---

### Post by adalal on 2010-05-15
did you try reinstalling cups-pdf?

---

### Post by crjackson on 2010-05-15
> **bennachie said:**
> Sorry to have wasted your time.

Nothing is a waste of time when troubleshooting.  Thanks for your help.

---

### Post by crjackson on 2010-05-15
> **adalal said:**
> did you try reinstalling cups-pdf?

No. I didn't even know there was a package called cups-pdf.  I'll give it a shot next.

---

### Post by crjackson on 2010-05-15
> **adalal said:**
> did you try reinstalling cups-pdf?

That package wasn't installed.  I think that is just a virtual print drive so you can print to a pdf file.

None the less, I installed it and it didn't make any difference.

---

### Post by Paddy Landau on 2010-05-16
Bearing in mind the situation, try reporting this bug (again), in the hope that its frequency will get it noticed.

Can you print more than two pages from any other program, e.g. from a browser or from Open Office?

---

### Post by redbook4574 on 2010-05-16
> **crjackson said:**
> That package wasn't installed.  I think that is just a virtual print drive so you can print to a pdf file.

None the less, I installed it and it didn't make any difference.

I had this problem, I take it you are printing postage labels?? I used cups-pdf, printed to that, then reopened the file with acroread and hey presto it prints, no idea why but it worked.Also you have the bonus of a permanent copy in case you screw up the printing.

---

### Post by HermanAB on 2010-05-16
Since it is a PDF, you can send the file straight to the printer.  You don't need to run a special program to print it.

If the printer is attached to the local machine:
$ lpr -H localhost test.pdf

or if it is attached to another machine:
$ lpr -H 192.168.1.10 test.pdf

---

### Post by crjackson on 2010-05-16
> **Paddy Landau said:**
> Bearing in mind the situation, try reporting this bug (again), in the hope that its frequency will get it noticed.

Can you print more than two pages from any other program, e.g. from a browser or from Open Office?

Everything else prints just fine.  If I use the openoffice extension and import the PDF I can even print it all from there.  I would do this but it takes a lot of effort to make sure things are formatted correctly if imported.  It easier to boot to windows and click print.

I'll file another bug report.

---

### Post by crjackson on 2010-05-16
> **HermanAB said:**
> Since it is a PDF, you can send the file straight to the printer.  You don't need to run a special program to print it.

If the printer is attached to the local machine:
$ lpr -H localhost test.pdf

or if it is attached to another machine:
$ lpr -H 192.168.1.10 test.pdf

Cool, I'll try that.  So if I'm understanding correctly.

I could place the *.PDF on my Desktop, open a terminal and navigate to my Desktop, then run the command in the terminal.

---

### Post by Paddy Landau on 2010-05-16
> **crjackson said:**
> I could place the *.PDF on my Desktop, open a terminal and navigate to my Desktop, then run the command in the terminal.
That is correct.

Have you uninstalled Adobe Reader and then reinstalled from the repositories or directly from the [Adobe website]("http://www.adobe.com/")?

---

### Post by crjackson on 2010-05-16
> **Paddy Landau said:**
> That is correct.

Have you uninstalled Adobe Reader and then reinstalled from the repositories or directly from the [Adobe website]("http://www.adobe.com/")?

I got it from the repositories, I haven't tried to reinstall it.

---

### Post by crjackson on 2010-05-16
Okay, it seems the problem is the old Dell / Linux printer driver that came with it.

I purged it and selected one of the foomatic drivers (Dell M5200) which seems to print everything, but doesn't support the advanced features like the Dell driver does.

I can live with it but for some reason this driver defaults to only black/white printouts.  If you want to print a color document in open office for instance, you have to change the properties to color each time.

PDF's print in color every time.

Is there a setting in a text file somewhere that I can edit to change the driver to default to color?

There is not specific settings in the System>Administration>Printing properties that lets me do this like the old driver did.

Any suggestions on this.  I'm almost where I need to be but not quite.

I know that xerox actually makes some of the dell printers.  If I knew who made this one and what model it corresponded to, I could possibly select a better driver that would get the job done.  I've googled and I can't figure out who makes this one.

---

### Post by Paddy Landau on 2010-05-17
I'm glad you got that fixed. Please mark the thread Solved so that others with the same problem can find it.

> **crjackson said:**
> ... I could possibly select a better driver...
Not all manufacturers support Linux well. I know HP does, but I don't know about Xerox or Dell.

---

### Post by crjackson on 2010-05-26
It seems I spoke too soon.  Once again it won't print PDF files and I have to switch to windows to print off homework. I've tried 2 different machines at the house and each of them on a different printer.  Same damn issue.  Reboot to windows and presto.

I really hate this crap. I have to boot to windows in secrecy to keep from being humiliated after singing all the songs of Ubuntu for the few years.  This really sucks.

I didn't used to have this problem a couple of years back on older versions.  I guess I need to find out what version of Ubuntu / Acroread worked and go back to that.

---

### Post by alphacrucis2 on 2010-05-26
> **crjackson said:**
> It seems I spoke too soon.  Once again it won't print PDF files and I have to switch to windows to print off homework. I've tried 2 different machines at the house and each of them on a different printer.  Same damn issue.  Reboot to windows and presto.

I really hate this crap. I have to boot to windows in secrecy to keep from being humiliated after singing all the songs of Ubuntu for the few years.  This really sucks.

I didn't used to have this problem a couple of years back on older versions.  I guess I need to find out what version of Ubuntu / Acroread worked and go back to that.

I noticed a weird problem a couple of weeks ago with a Canon laser printer printing from Adobe reader where the file would print ok from Ubuntu but incredibly slowly. The printer would cogitate for as long as five minutes on each page whereas printing the same pdf file from the same version of Adobe reader in Windows, the printer would churn the pages through at its' normal speed. I didn't really experiment further as I don't often need to print pdf's but I might do some tests. (BTW the same printer works at normal speed when printing quite complicated docs from Open Office and other Linux apps.

---

### Post by Paddy Landau on 2010-05-26
> **crjackson said:**
> I really hate this crap. I have to boot to windows in secrecy to keep from being humiliated after singing all the songs of Ubuntu for the few years.  This really sucks.
<Laughing> Like Windows, Ubuntu is created by humans and does have its limitations. Don't be afraid to acknowledge its deficiencies. That Ubuntu works as well as it does is testimony to the many developers, as it's in competition Windows and Mac with their billions of dollars.

I sorry to hear that you have this problem again. You said you tried different printers. What makes did you try?

Did you try the suggestion in [post 19]("http://ubuntuforums.org/showthread.php?p=9308132#post9308132")? If it works (it probably won't), you have a workaround at least.

Whatever you did to [install the old drivers]("http://ubuntuforums.org/showthread.php?p=9312343#post9312343"), do it again. It may be that your good work, somehow, was undone.

---

### Post by Paddy Landau on 2010-05-26
> **alphacrucis2 said:**
> I noticed a weird problem a couple of weeks ago...
The confounding problem here is that the OP gets this problem not only with Adobe but also with Evince.

That indicates that the printer's drivers may be having a problem with Postscript (I believe that PDF's are in Postscript; please correct me if wrong).

That could explain the OP's (temporary) success when changing the drivers.

When you have Windows, you buy printers designed for use on Windows. Ditto Mac. I would suggest that when you have Linux, you buy printers designed for use on Linux. HP has an excellent reputation in that regard; I don't believe that Canon does (again, correct me if wrong).

---

### Post by alphacrucis2 on 2010-05-26
> **Paddy Landau said:**
> The confounding problem here is that the OP gets this problem not only with Adobe but also with Evince.

That indicates that the printer's drivers may be having a problem with Postscript (I believe that PDF's are in Postscript; please correct me if wrong).

That could explain the OP's (temporary) success when changing the drivers.

When you have Windows, you buy printers designed for use on Windows. Ditto Mac. I would suggest that when you have Linux, you buy printers designed for use on Linux. HP has an excellent reputation in that regard; I don't believe that Canon does (again, correct me if wrong).

I don't know for sure. I was quite impressed when Cups seemed to identify the printer itself and suggested a driver for it. So far I have only noticed an issue with Adobe printing but I will spend some time testing tomorrow. I didn't have any choice in selecting the printer as it isn't mine :).

---

### Post by Paddy Landau on 2010-05-26
The last few posts gave me an idea.

Please try an experiment.

When you ask to print from Adobe, select the "Advanced" button at the bottom of the dialogue.

You'll get an Advanced Print Setup dialogue. See the attachment.

Experiment with the various settings on that dialogue. In particular, if old drivers are causing the problem, experiment with *Language*, *Convert TrueType to Type 1* and *Emit CIDFontType2 as CIDFontType2*. If none of those works separately or in combination, try *Print as image*.

HTH

---

### Post by crjackson on 2010-05-26
> **Paddy Landau said:**
> I sorry to hear that you have this problem again. You said you tried different printers. What makes did you try?

I have a Dell 5100cn & a Dell 1600n - Both are connected via USB to different desktops running Lucid.

> **Paddy Landau said:**
> Did you try the suggestion in [post 19]("http://ubuntuforums.org/showthread.php?p=9308132#post9308132")? If it works (it probably won't), you have a workaround at least.

Yes, I tried and it didn't work.  It loads the document into the printing applet queue and says processing.  After several minutes, it just goes away.

> **Paddy Landau said:**
> Whatever you did to [install the old drivers]("http://ubuntuforums.org/showthread.php?p=9312343#post9312343"), do it again. It may be that your good work, somehow, was undone.

I don't think so.  It still prints the original PDF file I was having problems with.  It's a different PDF that won't print this time. Obviously something is different about the files but I don't think it's broken since it prints quickly when windows is loaded but I could be wrong.

---

### Post by crjackson on 2010-05-26
> **Paddy Landau said:**
> The last few posts gave me an idea.

Please try an experiment.

When you ask to print from Adobe, select the "Advanced" button at the bottom of the dialogue.

You'll get an Advanced Print Setup dialogue. See the attachment.

Experiment with the various settings on that dialogue. In particular, if old drivers are causing the problem, experiment with *Language*, *Convert TrueType to Type 1* and *Emit CIDFontType2 as CIDFontType2*. If none of those works separately or in combination, try *Print as image*.

HTH

Tried all that this morning again.  Same result no matter what the setting.

---

### Post by crjackson on 2010-05-26
> **Paddy Landau said:**
> 

When you have Windows, you buy printers designed for use on Windows. Ditto Mac. I would suggest that when you have Linux, you buy printers designed for use on Linux. HP has an excellent reputation in that regard; I don't believe that Canon does (again, correct me if wrong).

The printer was designed to work with Linux and comes with drivers on CD. I changed to one recommended by the printer installer applet in Ubuntu and that one worked better (I thought). It seems I was wrong however.

I tried removing the driver, logged off, logged on and then reinstalled the driver. Still not working. The problem is VERY specific to PDF files only. All other documents print quickly and perfectly every time.

I don't find the Portable Document Format to be very PORTABLE at all.

---

### Post by Paddy Landau on 2010-05-26
> **crjackson said:**
> I don't find the Portable Document Format to be very PORTABLE at all.
:lol:

Have you contacted Dell support? The company may have an answer (but probably won't).

If I were you, I'd check [Launchpad for bugs]("https://bugs.launchpad.net/"), and if there isn't an open bug for this, then create one. Describe the problem precisely; refer to this thread in the bug; and when you've created the bug, post its URL in this thread.

---

### Post by crjackson on 2010-05-26
> **Paddy Landau said:**
> :lol:

Have you contacted Dell support? The company may have an answer (but probably won't).

If I were you, I'd check [Launchpad for bugs]("https://bugs.launchpad.net/"), and if there isn't an open bug for this, then create one. Describe the problem precisely; refer to this thread in the bug; and when you've created the bug, post its URL in this thread.

Dell is no help. They want me to buy a newer printer model. This model is no longer supported, I got it in 2006.

What package do I file the bug report against?

---

### Post by Paddy Landau on 2010-05-26
> **crjackson said:**
> This model is no longer supported
Ah. That may be a problem then. It could be a product deficiency rather than a Lucid deficiency.

> **crjackson said:**
> What package do I file the bug report against?
Good question. Sorry, I'm really not sure. Try CUPS; or maybe someone here can give a better answer.

---

### Post by crjackson on 2010-05-26
> **Paddy Landau said:**
> Ah. That may be a problem then. It could be a product deficiency rather than a Lucid deficiency.


Good question. Sorry, I'm really not sure. Try CUPS; or maybe someone here can give a better answer.

I wouldn't really call it a product deficiency since it's only Linux printing that doesn't work.  I've found MANY posts and bugs regarding CUPS not printing PDF's on many printers.

I'll file the report against CUPS.

---

### Post by cloyd on 2010-05-26
Just to add a little information . . . which may or may not be relevant. A short while back, my new HP Photosmart plus simply quit printing PDF's from evince. It had been printing them, but it just stopped. In fact, it quit printing anything from evince.  I switched to Adobe reader, and it everything works fine.  I hated to go to a proprietary program, but it worked. I haven't tried to print more than a few pages, though.  I do have to say that PDF's frequently are displayed much better in Adobe Reader than evince.

---

### Post by crjackson on 2010-05-26
Here's the bug report.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/585882]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/585882")

If anyone here has a similar issue, please read the bug report and confirm it so someone will POSSIBLY have a look.

---

### Post by crjackson on 2010-05-26
> **cloyd said:**
> Just to add a little information . . . which may or may not be relevant. A short while back, my new HP Photosmart plus simply quit printing PDF's from evince. It had been printing them, but it just stopped. In fact, it quit printing anything from evince.  I switched to Adobe reader, and it everything works fine.  I hated to go to a proprietary program, but it worked. I haven't tried to print more than a few pages, though.  I do have to say that PDF's frequently are displayed much better in Adobe Reader than evince.

It won't print with evince

It won't print with Acroread

It won't print with lpr -H localhost filename.pdf

---

### Post by cloyd on 2010-05-26
> **crjackson said:**
> It won't print with evince

It won't print with Acroread

It won't print with lpr -H localhost filename.pdf


Yeah, I hear. I didn't think I had a solution for you, just thought that the information may be relevant.  I don't want to distract you or hijack the thread.

---

### Post by crjackson on 2010-05-26
> **cloyd said:**
> Yeah, I hear. I didn't think I had a solution for you, just thought that the information may be relevant.  I don't want to distract you or hijack the thread.

No problem and thanks for the information.

---

### Post by alphacrucis2 on 2010-05-26
Ok. I have been playing around with printing pdf's from Adobe reader to the Canon printer I mentioned up thread. It turns out that I have fixed my problem of pathetic print speed just by changing drivers. The printer is a C2550i but I noticed the driver in use was C2570i. There was no driver available for C2550i but there is a C2550. I tried the postscript version of this driver and the printer is now printing pdf's correctly at full speed. This doesn't help the OP but maybe it does confirm that it is a print driver issue rather than anything wrong with Adobe Reader itself (apart from the fact that it is horribly bloated piece of software :P).

---

### Post by crjackson on 2010-05-26
> **alphacrucis2 said:**
> Ok. I have been playing around with printing pdf's from Adobe reader to the Canon printer I mentioned up thread. It turns out that I have fixed my problem of pathetic print speed just by changing drivers. The printer is a C2550i but I noticed the driver in use was C2570i. There was no driver available for C2550i but there is a C2550. I tried the postscript version of this driver and the printer is now printing pdf's correctly at full speed. This doesn't help the OP but maybe it does confirm that it is a print driver issue rather than anything wrong with Adobe Reader itself (apart from the fact that it is horribly bloated piece of software :P).

Thanks for the info.  I've already eliminated all external software by printing directly to the printer with terminal commands.

The problem is in CUPS or the driver it's self.  A few posts back you will see a link to my bug report.  If you get a chance to read the report you will see that one of the CUPS developers are working with me to find a solution.

---

### Post by crjackson on 2010-05-28
Okay, so here's an update.  It is a bug after all.  It has to do with PDF files that contain JPG images.  Images that are PNG and other work just fine, but if the embeded image is a PDF it doesn't expand it properly or some such.  A fix is on the way, however it may not get here until Maverick if I'm understanding the chatter between the developers.

This message was for me from the developer that was assisting.

> Till Kamppeter  wrote 30 minutes ago:  	  #16

crjackson, no more information is needed. Looks like that Cairo and Poppler need to get updated. See comment #119 in bug 419143.

---

### Post by goniomdq on 2011-03-02
I know this thread is a bit old, but the problem was not fixed on 10.04.
I'm running 10.04 and still can't print some pdf (I assume that this have JPG images, but I don't know how to check that)
Cheers,
(BUMP)

---

