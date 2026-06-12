---
title: "printer sharing - ubuntu"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by noworldorder on 2010-04-19
I have two Ubuntu computers.  One has a printer attached to it and the other does not.  Both are connected to a  router.  

I need to ba able to share the printer.  The computer I use most often does not have the printer.  So is it possible to network the computers and share the printer?

Thanks - chris

---

### Post by e4uforums on 2010-04-19
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by immoweichert on 2010-04-19
I just came across the same issue myself and when I checked the forum I found this thread. This was really easy to sort. Is there any way to change the icons for the printer in the menue ?

---

### Post by noworldorder on 2010-04-19
Thanks - it looks like a straight forward solution except...  Ubuntu doesn't have the driver for my Samsung ML-1915.

I downloaded the Linux driver but it doesn't work as Ubuntu wants a "postscript printer description" file.  Where would I find this?  And ideas.

Thanks - Chris

FYI I really appreciate all the help I have been given ever since I got hooked on Ubuntu a few weeks ago.

---

### Post by ubun2warrior on 2010-04-20
Its very simple. GO to System>Administration>Printing. A new window opens up. You will see your printer there(assuming that you have attached your printer to one of the systems and Ubuntu has detected it) Just right click on the printer select 'properties', a new window opens , then select 'policies' and there put a check mark on share printer.

Now on your other computer which is on the network again go to syetem>administration> printing. Now here you have to select Server from the menu bar> settings> put a chech mark on Publish shared printers by other systems. And that's it within a few seconds you will see the printer listed there.

---

### Post by noworldorder on 2010-04-20
Right but it doesn't have my driver.  It has other Samsung printers but not mine

---

### Post by noworldorder on 2010-04-20
I should mention that it recognizes my printer but does not have the driver for it

---

### Post by immoweichert on 2010-04-20
Have you had a look at the open printing forum:

[http://www.openprinting.org/driver/Postscript](http://www.openprinting.org/driver/Postscript)

You might also want to have a look at this link:

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting)

Your printer seems to be the one made by Samsung with the least info/support available, but you might check a similar printer by Samsung that requires the same driver (?ML-2525).

---

