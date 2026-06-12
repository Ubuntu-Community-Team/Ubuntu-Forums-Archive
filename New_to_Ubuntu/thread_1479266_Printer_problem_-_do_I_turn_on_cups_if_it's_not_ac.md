---
title: "Printer problem - do I turn on cups if it's not active"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by b1llyboy on 2010-05-10
Hi folks. First post here, so apologies if this one has already been solved. I am trying to get my printer (HP Deskjet F380) working, but Ubuntu (10.04, 64 bit) will not recognise it as a printer.
The scanner part of it works fine, so there is clearly not a connection problem.
I tried System>Admin>Printing>Server>New>Printer, but find that the printer option is greyed out. I then tried the troubleshooter, which said CUPS was not running and to activate it via System>Admin>Services. But I can't see a "services", and I don't know how to start CUPS via the terminal.
Does anyone out there know what I should be doing?

Thanks,

Billy.

---

### Post by b1llyboy on 2010-05-10
Sorry, did another search and found the answer.

sudo service cups start
Seems to be working fine now.

Billy

---

### Post by norfair on 2010-08-20
Thank you, thank you, thank you! 

I was scouring the interwebs and this forum to the point of exhaustion. In 8.04 my Canon ip5000 was recognized right away. In 10.04, nothing. I tried bunches of things, and was pressed for time at that. I stumbled upon your post, pasted the command, and voila! Thanks again for not only inadvertently helping me, but for following up with a resolution to your original inquiry. :KS

(I probably shouldn't reply to a post from as far back as May, so forgive me, whomever, for this faux pas - if it even is one.)

---

### Post by jtarin on 2010-08-20
Learn to access CUPS through your browser at ```
[http://localhost:631/](http://localhost:631/)
``` for the easiest setup and troubleshooting.

---

### Post by Buzzygirl on 2010-10-25
Wow, thanks to the last poster re: online CUPS setup. I was pulling my hair out and that did the trick. My HP F380 printer worked fine until I upgraded to 10.04, then stopped. The online setup did the trick! 

This is a great community. Thank you again. :)

---

