---
title: "Getting Past System Check TurboTax FreeFile"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by jamesrl on 2009-01-21
I want to free file my (state and federal) taxes online.
According to: 
[http://www.tax.state.ny.us/elf/free_efile_info.htm](http://www.tax.state.ny.us/elf/free_efile_info.htm)
my one choice for free e-Filing is Turbotax (I'm over 25 and make less than $30k ... I'm a grad student), located at:
[http://www.taxfreedom.com](http://www.taxfreedom.com)
After going there and clicking I qualify in firefox3, I get sent to this nasty screen saying:

> 
Please make sure your computer meets the TurboTax Online system requirements.

To ensure you have the best possible experience using TurboTax Online, we recommend that your computer meet the following system requirements.

Minimum System Requirements:
The TurboTax Online service is optimized for:
Windows
Version 	Web Browser
Windows Vista 	AOL 9.0, Firefox 2.0, Internet Explorer 7.0, Netscape 9.0
Windows XP 	AOL 8.0, Firefox 2.0, Flock 2.0, Internet Explorer 6.0 (with Windows XP Service Pack 2 or higher), Netscape 9.0
Windows 2003 	Firefox 2.0, Internet Explorer 6.0, Netscape 9.0
Windows 2000 	AOL 8.0, Firefox 2.0, Flock 2.0, Netscape 9.0
Mac OS X
Mac OS X 	Web Browser
Mac OS X 10.5 (Leopard) 	Firefox 2.0, Flock 2.0, Safari 3.0
Mac OS X 10.4 (Tiger) 	Firefox 2.0, Safari 3.0
Mac OS X 10.3 (Panther) 	Firefox 2.0
Mac OS X 10.2 (Jaguar) 	Firefox 2.0
Download Supported Browsers

Now normally I would avoid this company like the plague for poor site design and deliberately trying to limit there business, but I don't feel like paying money to file my taxes (and prefer the convenience of e-filing).  I sincerely doubt that firefox3 on ubuntu is actually incompatible with their e-filing system.  I was wondering if anyone knows how to make firefox3 fake that its on windows or Mac and is version 2.0 or 3.0.  I've tried changing a few things in about:config and also tried epiphany but nothing worked yet.  
Specifically changed:
distribution.about: (from "Mozilla Firefox for Ubuntu" to "Mozilla Firefox")
general.useragent.vendor (from ubuntu to Firefox)
and finally:
general.useragent.extra.firefox (from Firefox/3.0.5 to Firefox/2.0.5)


[As a last resort, I do have a legal copy of windows lying around somewhere that came with an old laptop, but I'd rather not have to waste 30min or so to install windows inside virtualbox.]
Also I can't seem to find firefox-2.0 within 8.10 anymore.  Was it removed from the repo?

---

### Post by jamesrl on 2009-01-21
I installed the version of firefox-2 in the hardy repositories and it got stuck at the same system check page.

---

### Post by cariboo on 2009-01-21
IF it hasn't been already Firefox 2 has been EOLed. There is no need to install and older version as i won't help with your problem. Tax prgrams are one of the things that are really lacking in Linux. That is one of the few reasons I keep a computer running XP around. Free Tax Filing.

Jim

---

### Post by jimmy the saint on 2009-01-21
One of the things that the christian right got really good at doing in the US was bombarding agencies like the FCC and media corporations with massive ammounts of form letters, emails, and other forms of contacts to get what they wanted.  While the letters themselves were rarely compelling, the sheer amount became enough of a nuisance to get noticed.  

I think we Linux users could take a page from that playbook.  Whenever we hear a story like this, we should all take a couple of minutes to shoot an email, even if we aren't personally going to use the service.  The merits of linux, the growing adoption rate, the plain common sense of supporting (or in the case of a websit, not crippling) our OS have been made clear.  I think it is high time the squeaky wheel concept be applied to Linux.  If taxfreedom.com got 100,000 or so emails to sort through, I'd bet that next year (or next month) we would see that it is suddenly not crippled for linux clients.

Edit:  I just sent them one with a link to this thread

---

### Post by jamesrl on 2009-01-21
Changing general.useragent.vendor to:
Mozilla/6.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.17) Gecko/20080827 Firefox/3.0.5
Lets me get in and successfully file my Taxes.  This is unacceptable that they cripple their service to only Mac/Windows users (for no legitimate reason).

I filled out the long survey after filing my taxes with very negative reviews (will I recommend 0 on scale of 0-10, etc.) with reason put in as:

> The fact that despite using an approved browser (firefox 3.0) with a working versions of adobe acrobat and adobe flash player 10, my web browser didn't pass the 'compatibility test' as it is ubuntu (a very popular) version of linux.  Linux as of July 08 had a 4% market share of web users, and for your site to restrict them is poor judgment on your part.  I was able to file my tax return with no problem whatsoever, after telling my firefox webbrowser to pretend it was in a windows environment.  [Specifically go to about:config and changed general.useragent.vendor to "Mozilla/6.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.17) Gecko/20080827 Firefox/3.0.5") and it worked.]  This was quite frustrating to have to figure out, and if it wasn't my only option for a free NY state e-file (as I make under $30,000 and am over 25) I wouldn't have used it.  [And next year after grad school ends, I will probably use a competing service as opposed to navigating around it.] 

---

### Post by jamesrl on 2009-01-22
Hmmm ... I'd mark this as solved but it doesn't seem to be an option in thread tools any more.

---

### Post by anjilslaire on 2009-01-22
well done.

---

