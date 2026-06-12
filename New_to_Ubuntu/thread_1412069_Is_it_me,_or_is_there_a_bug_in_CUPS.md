---
title: "Is it me, or is there a bug in CUPS?"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Vignesh S on 2010-02-20
I have a Epson CX3900 printer. Now, for some reason, even when the computer is on, Ubuntu 9.10 simply will not come up with the menu that asks me if I want to install a driver for it. Strange thing is, it did ask me quite a long while ago when I freshly installed 9.10. How would I get that menu to come up again, so I can finally install the driver for the printer?

And most of all: is this a major bug in CUPS?

---

### Post by cariboo on 2010-02-20
Have you tried System-> Administration->Printing, or [http://localhost:631]("http://localhost:631")?

---

### Post by Vignesh S on 2010-02-20
Yes, and neither want to work for some reason :(.

I tried installing .deb driver from [here]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do"), though that didn't work either :(

I am beginning to think CUPS isn't working as it should... maybe the most recent version doesn't want to work...

---

### Post by tgalati4 on 2010-02-21
What's in the log files? /var/log/cups

---

### Post by ellgor on 2010-02-21
Hi,

Open up Printers, either delete any existing references to a printer (remove it completely) or add new printer, in the latter it should mention detecting printers etc and when found, will offer the driver menu.

Regards, Ellgor.

---

### Post by Vignesh S on 2010-02-27
Sorry about the delay, I've really been overloaded in work this week, and the next week will probably be no different either :)

The attached .tar file has the logs that were contained in the directory /var/log/cups. Judging by the amount of error logs in it, it isn't looking too good :?

---

### Post by Vignesh S on 2010-02-27
Anyone got any ideas as to what's goin' on? Not being able to use the printer in Linux is a major drawback for me :(

---

### Post by gordintoronto on 2010-02-28
Did you read the post from Ellgor?

---

### Post by Vignesh S on 2010-02-28
Yep, and there wasn't any printer in there whatsoever :(.

---

### Post by Vignesh S on 2010-02-28
Oh wait, I remember when I cut back all those services and I also cut out the printer applet. Well, I re-enabled it, but that printer driver install thing still won't come up :(. Well, I tried starting up cups from the command line, and it came up with this: 

cupsd: Child exited on signal 15!

Nasty, and it happened while the printer was plugged in. Can anyone make head or tail of the error logs? Or don't they tell anything of significance?

---

### Post by Vignesh S on 2010-03-01
Hmmm.... This isn't looking too good...

---

