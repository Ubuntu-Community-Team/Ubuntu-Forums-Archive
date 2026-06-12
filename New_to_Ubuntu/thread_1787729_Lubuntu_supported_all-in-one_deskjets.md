---
title: "Lubuntu supported all-in-one deskjets?"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by nifty542 on 2011-06-21
Hi, all

I am looking to buy an all-in-one deskjet supported by Ubuntu/Lubuntu.
Much of the information I have seen lists devices which are now obsolete.
I am having a very bad experience with an HP Photosmart B109A, which I bought in February. It is listed as Linux supported, but have yet to get it to print in colour. The support staff have been less than helpful so far, so I am looking to cut my losses.
Does anyone have a recommendation? I would really like to be able to check ink levels, without having to use the terminal.
Thanks, in anticipation
Nifty

---

### Post by dFlyer on 2011-06-21
> **nifty542 said:**
> Hi, all

I am looking to buy an all-in-one deskjet supported by Ubuntu/Lubuntu.
Much of the information I have seen lists devices which are now obsolete.
I am having a very bad experience with an HP Photosmart B109A, which I bought in February. It is listed as Linux supported, but have yet to get it to print in colour. The support staff have been less than helpful so far, so I am looking to cut my losses.
Does anyone have a recommendation? I would really like to be able to check ink levels, without having to use the terminal.
Thanks, in anticipation
Nifty

Have you tried to install hplip-gui?

---

### Post by pqwoerituytrueiwoq on 2011-06-21
this got my deskjet 2050 working on lucid (this is for hp printers/scanners)

```
sudo apt-add-repository ppa:hplip-isv/ppa
sudo apt-get update
```run update manager

---

### Post by nifty542 on 2011-06-21
Hi

Thanks for the reply. Yes, I have installed HPLip and HP gui. But the device will not print in colour. I am so sick of calling HP at my own cost, that I feel ready to try with something else.
The software is not the problem, I think

Regards

Nifty

---

### Post by SoFl W on 2011-06-21
Are you sure it isn't just a settings issue?  I often change between color and B&W for GIMP and other programs.  Sometimes when using something else I wonder why it isn't in color.  It is usually because I changed something in the printer properties.  What programs don't print in color?

When you click print, there are tabs across the top "General-Page Setup-Job-color-advanced", are the selections in Color correct?
I don't have an HP but I am sure the set dialog box is the same.

Was [this link]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=2020&lc=en&cc=us&dlc=en&sw_lang=&product=3794621") able to help?

---

### Post by nifty542 on 2011-06-21
Hi, all

Thanks for the replies. Yes, I AM sure it's not a settings problem! It won't print in colour right from the reset, with the computer switched off.
I would just like someone to recommend an all-in-one which can report ink levels

Regards

Nifty

---

### Post by SoFl W on 2011-06-21
How about this:
[http://answers.yahoo.com/question/index?qid=20100409133634AAlEEFW](http://answers.yahoo.com/question/index?qid=20100409133634AAlEEFW)

---

### Post by cpatrick08 on 2011-06-21
> **dFlyer said:**
> Have you tried to install hplip-gui?
have you tried the driver from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by nifty542 on 2011-06-21
Hi, all

Thanks for the replies. Yes, I have tried all of the above. The printer wouldn't print in colour, from when I first switched it on, before I connected the USB cable.
The software is reporting it as printing in colour.
Can someone please recommend an all-in-one device that reports ink levels?
I have googled this problem extensively and tried many solutions before posting here

Regards

Nifty

---

### Post by nifty542 on 2011-06-21
Hi, all

So, does anyone have a solution? I have tried all of the above. I still can't get the printer to print in colour

Regards

Nifty

---

### Post by SoFl W on 2011-06-21
Ok, if you are fed up with HP, I have an Epson Workforce 610.  It is a wireless network all in one.  (printer/scanner/fax)  it has a USB option.  When I tired the various versions of 11.4 in virtual boxes, they found it, downloaded the correct drivers and and installed it.  Worked like a charm in my virtual machines.
With my 10.4 install, I manually installed everything, I don't think I tried letting it find everything on its own.

It displays the ink levels if I goto System->Admin-> Printers-> (select printer) -> Properties.  There was somewhere else that had a "level" display but that didn't work.

The cost is about (USD) $199.99 from various on-line shops. Last year I got really lucky, I had been looking at it for several days, and I think Amazon made a mistake, listed the wrong price. I picked it up for $99.99.  I checked the partner's website and checked the price the next day and it was back up to $199.

Here are parts of a review I wrote up about it:  

[I]I would recommend this printer. 

When I first got it I thought the warm up time for printer was a little long, but it doesn't bother me now.  It could be more of a computer/network/printer communication issue rather than the printer itself.
The printer is slow on high quality printing but good in standard and draft modes.
You can scan directly to a PDF and save it on a memory card,  it doesn't fax to a pdf.
The  display shows "ringing" when a call comes in, I wish it displayed caller-id.

[/I]Do a little research on the printer, if you have any questions I will try to answer.  (you might have to PM if I forget about this thread)

---

### Post by nifty542 on 2011-06-22
Hi

Many thanks for the reply. As far as I can tell so far, that printer isn't available in the UK. However, I know that sometimes the same model may just have a different name or number. I shall google further.
I have been on to HP Technical support today, and they have confirmed that, as far as they can tell, it is a hardware issue, since it won't even print a self-test page in colour, when first switched on after a reset.
Thanks for all the replies

Nifty

---

### Post by nifty542 on 2011-06-22
Hi, all

Well, a different HP technician, with a totally different attitude, and was able to establish a hardware fault with the Photosmart B109a. However, I would still welcome recommendations for other printers which can report ink levels in Ubuntu/Lubuntu, without resorting to the terminal

Thanks

Nifty

---

