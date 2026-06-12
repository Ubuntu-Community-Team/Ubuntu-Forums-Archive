---
title: "&quot;Paste from Word&quot; equivalent?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Isabelle100 on 2009-05-13
I've just started using Xubuntu in earnest instead of Windows and I really appreciate how much faster it is.  The reason I changed over is I volunteer to update an on-line magazine each week.  People send in Word docs containing interesting articles and usually dozens of links.  One essential task is to copy the text of each article and paste it into the content management system using the "Paste from Word" button.  This used to work fine using Word on Windows and I'd end up with some clean HTML with just a few paragraph tags and the essential hyperlinks.

Today I tried doing the same thing on Xubuntu using Open Office Writer.  It read the Word docs fine, but when I tried to paste into the website page (on Firefox) using the "Paste from Word" button, I got a pop up menu saying that I had to use Cntrl-V instead.  Of course when I did this it pasted complex HTML with many lines of <style> tags and so on.

Is there anyway of making "Paste from Word" buttons work with Open Office Writer? Or I would be grateful if anyone knows of a work around to get simplified html from the supplied Word docs so I can paste it into the web page.

---

### Post by ashmew2 on 2009-05-13
Hello Isabelle , Welcome to the community.

I dont know exactly how to fix the problem you're having may be more so because i havent used MS Office/Open Office that much..If you could provide an example doc file that you usually have to deal with , may be i could help you better :)

---

### Post by billgoldberg on 2009-05-13
> **Isabelle100 said:**
> I've just started using Xubuntu in earnest instead of Windows and I really appreciate how much faster it is.  The reason I changed over is I volunteer to update an on-line magazine each week.  People send in Word docs containing interesting articles and usually dozens of links.  One essential task is to copy the text of each article and paste it into the content management system using the "Paste from Word" button.  This used to work fine using Word on Windows and I'd end up with some clean HTML with just a few paragraph tags and the essential hyperlinks.

Today I tried doing the same thing on Xubuntu using Open Office Writer.  It read the Word docs fine, but when I tried to paste into the website page (on Firefox) using the "Paste from Word" button, I got a pop up menu saying that I had to use Cntrl-V instead.  Of course when I did this it pasted complex HTML with many lines of <style> tags and so on.

Is there anyway of making "Paste from Word" buttons work with Open Office Writer? Or I would be grateful if anyone knows of a work around to get simplified html from the supplied Word docs so I can paste it into the web page.

What CMS are you using?

If you use Abiword instead of Writer, does the problem remain?

---

### Post by ashmew2 on 2009-05-13
Does this link help you at all ? [http://openoffice.blogs.com/openoffice/2008/11/pasting-from-html-or-word-into-openoffice-writer-use-paste-special-unformatted-text.html?cid=140939608](http://openoffice.blogs.com/openoffice/2008/11/pasting-from-html-or-word-into-openoffice-writer-use-paste-special-unformatted-text.html?cid=140939608)

---

### Post by Isabelle100 on 2009-05-18
Thank you all for your suggestions.  I have tried Abiword as well as Open Office Writer now, unfortunately with the same result and also the Paste Special to Unformatted Text, but unfortunately this drops the hyperlinks of which there are quite a few.  

Through doing this I have realised that the crux of the problem is that Firefox won't allow any access to the Clipboard except through its own Paste function.  Their website says that this is for security reasons.  This means that the "Paste from Word" button on any website will always be blocked by Firefox, whatever format my text is in.

Do you think that another browser would allow use of the "Paste from Word" button and if so would this be a security risk that I should avoid?

---

### Post by Isabelle100 on 2009-05-18
On looking into it further, I've found that Firefox allows you to set preferences in the user profile file so that selected websites are allowed to use the clipboard.  They recommend this should be used with caution because of the security risks.  The details are here:

[http://kb.mozillazine.org/Granting_JavaScript_access_to_the_clipboard](http://kb.mozillazine.org/Granting_JavaScript_access_to_the_clipboard)  

I haven't tried this out yet, so we shall see...

---

