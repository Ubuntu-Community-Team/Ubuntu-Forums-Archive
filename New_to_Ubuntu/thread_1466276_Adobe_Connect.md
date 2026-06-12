---
title: "Adobe Connect"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by beanco on 2010-04-30
Anybody have any experience with Adobe Connect in Ubuntu?

1. How can I get it from the CL?

2. Pros and Cons of this over other web conferecing apps?

Thanks

Robi

---

### Post by GrouchyGaijin on 2010-10-16
I'm curious too.  I signed up for a class taught via distance learning and I think they use Adobe Connect?  Does this run under Ubuntu?

---

### Post by xzxt1q on 2011-02-09
Yes it does. I had a 1.5 hour class on 8 Feb 2011. Worked great as a participant. (Ubuntu 10.04-LTS on P4/1.8Ghz)

---

### Post by beanco on 2011-02-12
> **xzxt1q said:**
> Yes it does. I had a 1.5 hour class on 8 Feb 2011. Worked great as a participant. (Ubuntu 10.04-LTS on P4/1.8Ghz)

OK, great to know it works... how to install it from the CL?

Thanks.

Robi

---

### Post by evanleibovitch on 2011-03-08
I've had major problems with trying to run AC under Ubuntu. It would always freeze while the screen "Connecting..." displayed.

Today, with the help of Adobe support, I was able to use AC under Linux for the first time ever.

Software environment:

[LIST]
[*]An up-to-date installation of Ubuntu or Kubuntu 10.10 (tested on both)
[*]Firefox 3.6.16 or Google Chrome 10.0.648.127 (tested on both)
[*]The Ubuntu package  "flashplugin-installer" 10.2.152.27ubuntu0.10.10.1 (from Ubuntu's "maverick-updates" repository)
[*]The Ubuntu package "connectaddin" 9.4.60.0 ([downloaded from Adobe]("http://na3cps.adobeconnect.com/common/addin/ConnectAddin.deb"), see [http://na3cps.adobeconnect.com/common/help/en/support/downloads.htm](http://na3cps.adobeconnect.com/common/help/en/support/downloads.htm))
[/LIST]
Procedures done:
[LIST]
[*]Go to this page on Adobe's website, which is actually an interface to the end-user computer's own Flash configuration
[*]Under "Global Security Settings", select "allways allow"
[*]At this point, I have had to a "complete removal" uninstall and reinstall of the "flashplugin-installer" package
[*]The browser's cache needs to be cleared
[/LIST]
There may be more optimal ways to do this, but the above software and procedures now give me working Adobe Connect under Linux, for the first time *ever* after years of trying.

---

### Post by astroclast on 2012-08-22
> **evanleibovitch said:**
> 
Procedures done:

[LIST]
Go to this page on Adobe's website, which is actually an interface to the end-user computer's own Flash configuration [/LIST]


I've been trying to make AC work on my 10.04.  Just run on this thread, and found the page referred to by evanleibovitch under here:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html)


The entire discussion is here:

[http://forums.adobe.com/message/3497365](http://forums.adobe.com/message/3497365)

I hope this helps a little.



PS: Turns out you can access that page by right clicking on a flash window and selecting 'global settings'...  Oh, well...

---

### Post by astroclast on 2012-08-23
Complete instructions may also be found on Adobe's site:

[http://helpx.adobe.com/adobe-connect/kb/install-connect-meeting-add-ubuntu.html](http://helpx.adobe.com/adobe-connect/kb/install-connect-meeting-add-ubuntu.html)


I've followed them, and yet when I test my connection it fails...

---

