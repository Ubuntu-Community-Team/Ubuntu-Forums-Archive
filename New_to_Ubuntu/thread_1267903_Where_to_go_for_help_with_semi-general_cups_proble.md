---
title: "Where to go for help with semi-general cups problem"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by pipping on 2009-09-16
I have the following issue with cups on a certain printer (I have no access to other printers):

My multiple-copies jobs are concatenated to a single file, and then handled as one job. This incorrectly handles duplex (odd sided jobs are not seperated by a page) and staples (the entire batch job is stapled together).
I have the latest driver for my printer from KonicaMinolta, and will problably not be able to get them to update their driver as they recently put our printer on "phased out models". Further, I can find sufficient mention of this problem when googling to be sure it is not a problem with the printer driver, or at least a general problem.

My problem, however, is that in googling the issue, I cannot find a good place to get help. I cannot even determine if I should label it a cups or ubuntu issue. One site suggested this was a problem with postscript.ppd, and that one should hack the postscript driver to make it turn off staples (and I assume duplex) when concatenating to make cups send the correct instructions. Ultimately suggesting it's a cups problem. 
Another site suggested that this used to work in Hardy or before, and is a regression in ubuntu.

So my question is, in brief: "To whom should I turn to get help?"

---

### Post by quixote on 2009-09-17
That sounds like a really irritating problem.  I don't know enough to offer a solution, but I can tell you that generally the ubuntu forums are the best place to get answers about *anything*, ubuntu, firefox, cups, windows, you name it. :D

Have you looked at the cups admin settings?  You access them by going to [http://localhost:631](http://localhost:631) in your browser.  Depending what you're trying to do, it may ask for your sudo password on that system.

---

