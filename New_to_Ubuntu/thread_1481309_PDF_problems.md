---
title: "PDF problems"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by agberg on 2010-05-12
Greetings...

I've been trying to view a document from the psnh.com site and keep getting this:

/tmp/dn.........pdf could not be opened because the associated helper application doesn't exist. Change the association in your preferences.

I'm using Ubuntu 10.04 and have Adobe Reader 9 installed.

Could someone help me connect the dots?
Thanks.

---

### Post by Nxion on 2010-05-12
I have that error before on Firefox. after I restarted Firefox it went away. What you need to do is just save it to your desktop or where every you want to and then open the file. Don't try to open it with out saving it first. My issue went away after awhile, not exactly sure why.

---

### Post by cariboo on 2010-05-12
I don't use Firefox that often any more, but I just clicked on a pdf, and Firefox asked what to do with the file. In my case I told it to use the document viewer application to view it, If you want another application to open, click the browse button and navigate to /usr/bin/acroread, for acrobat.

---

### Post by almufadado on 2010-05-19
From my experience with the same error
Sometimes firefox or the site involved try to open the file with another user and the file is store with the worng permissions, the file is store in tmp but can not be acessed.

The solution is to save the document in the current user doc's directory and then open it.  

This can maybe the result of the root instalation of acrobat reader and not the current user.

Try foxit reader for linux.

---

### Post by gdonwallace on 2010-05-20
You also might want to check a couple other things.

Once you have saved the pdf, right click and go to preferences, there will be a tab labeled open with and make sure Document Viewer is listed (or whatever program you are using to view pdfs)  If it is not, below the box that will list the available programs will be an option for custom command with a browse button.  Click that and browse to /usr/bin/acroread and click on acroread to select acrobat as the default.

Second is to check Firefox and make sure there is a default set for pdfs.  For Ubuntu it should default to Document Viewer, but sometimes it is set to ask every time.  To check this click edit --> Preferences --> Applications. Type in PDF at the top and it will show you what program is associated with pdfs in Firefox.  To change, just click the down arrow and choose whatever is listed as available, or choose custom and do as above to select acrobat

Hope this helps.

---

### Post by -humanaut- on 2010-05-20
Adobe reader works fine in separate tabs for me. What version of Ubuntu are you running?

---

