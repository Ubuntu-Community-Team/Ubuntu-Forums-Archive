---
title: "printer CUPS server error"
date: 2014-11-18
forum: Networking &amp; Wireless
---

### Post by Rrory on 2014-11-18
have my new Samsung monchrome laser printer, installed the linux drivers but when I try to print I get this message:

'print service not available'; 

when I press 'connect' I get this message: "there was a CUPS server error 'failed to connect to server'"

ugh what's going on? I didn't have a problem with my last Samsung printer....could it be 14.10 maybe?

---

### Post by launchpad-elicoten on 2015-01-05
I have this problem too - how did you solve it?

---

### Post by Rrory on 2015-01-05
I had to think about it but now I remember. I deleted the printer and then re-added it, Ubuntu looked for drivers which I then clicked to install and it connected and works great. Hope this is helpful.

---

### Post by launchpad-elicoten on 2015-01-05
Thanks for that. Hopefully that'll help someone else but unfortunately on my computer I can't add printers because of the problem - they don't even show up when I go to printers, instead I get an error message about the Printers service not running. I must be experiencing a different problem to you.

---

### Post by dhunt84971 on 2015-02-22
I just got the same error.  Have never seen it before.  I simply restarted the cups service and this seemed to fix it.

sudo /etc/init.d/cups restart

---

### Post by elicoten on 2015-02-22
To help anyone else who comes across this thread with the same problem I had - I [posted the solution that worked for me on Ask Ubuntu]("http://askubuntu.com/questions/574420/cups-service-not-working-cant-find-any-logs")

---

