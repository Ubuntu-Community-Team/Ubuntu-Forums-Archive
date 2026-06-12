---
title: "Kmail Won't Automatically Open PDF Files"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Ron Carson on 2010-06-08
For some reason, my Kmail won't open PDF files when I click on the attachment. I always get a dialogue asking which program to use, even though I check for it to remember my selection.

Any suggestions on how to correct this annoyance?

Thanks

---

### Post by Autodave on 2010-06-08
> **Ron Carson said:**
> For some reason, my Kmail won't open PDF files when I click on the attachment. I always get a dialogue asking which program to use, even though I check for it to remember my selection.

Any suggestions on how to correct this annoyance?

Thanks

Since no one else is taking a stab here, let me try.  I had problems with PDF files not opening at all even with Adobe installed.  Someone here suggested that I try XPDF from the repos.  I did install that and have not had any problems since.  Might be worth a shot: the worst that could happen is it doesn't work and you can just uninstall it.

---

### Post by Ron Carson on 2010-06-08
Thanks for answering.  My problem is a little different in that I can readily open PDF's every where but from Kmail.   I've tried several different PDF readers, including the one you suggest, but I still can not get Kmail to automatically open a PDF when I click on the attachment.

I just can't figure this out and I've searched this forum and the Internet...... help......

---

### Post by ellgor on 2010-06-10
Hi,

Not sure but this works for other settings so here goes:

Click on "Settings" and choose "Configure Filters" (in kmail of course)when the new window appears click on the drop down beneath "Match all...." select "complete message" the next box "contains" and click in the last box and enter in ".pdf" in the lower section where it says "please select an action" from the drop down select "Execute command" click in the box to the right and enter in "evince" (without the quotes) or whatever reader you have or prefer, save it and try it, hope it helps.

Regards, Ellgor.

---

