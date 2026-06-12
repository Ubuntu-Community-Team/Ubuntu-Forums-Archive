---
title: "Gmail and OpenOffice Mailmerge"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by danlembek on 2009-09-02
I found a thread where someone seems to have figured out a way to use Gmail with OpenOffice Mailmerge. However, it is above my head, can someone give me a more detailed explanation of this?


From : [http://user.services.openoffice.org/en/forum/viewtopic.php?f=30&t=1858](http://user.services.openoffice.org/en/forum/viewtopic.php?f=30&t=1858)

Re: [Issue] Mail Merge E-Mail setup

Postby pearj » Tue Mar 10, 2009 3:02 am
I got it working with Gmail.

If you patch mailmerge.py by hand with the attached patch file on this: Bug 76655....... [http://qa.openoffice.org/issues/show_bug.cgi?id=76655](http://qa.openoffice.org/issues/show_bug.cgi?id=76655)

Then I used port 587 and smtp.gmail.com

I also had to delete the mailmerge.pyc file that was in the same directory as mailmerge.py

---

### Post by danlembek on 2009-09-04
No one has responded yet, so I'll give an update on the situation. I found the mailmerge.py file in /usr/lib/openoffice/basis3.0/program. So I opened it in geedit and made the changes that were apparent in the patch. However, I don't have permission to save the changes. 

Also, I'm aware that the patch is available on Oo3.1, but I was having all sorts of trouble.

Any help with this would be appreciated.

---

