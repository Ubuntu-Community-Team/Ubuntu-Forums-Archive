---
title: "Evolution mail Gmail style"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by jermza on 2010-01-11
Not sure where to ask this, but I'm running Evolution Mail and it is synced to my Gmail. 

Two small issues:

- Evolution doesn't mark my Gmail messages as read (or am I missing something?);

- Evolution has a slight "bug": in Gmail, when I reply to an email that I've sent, it intuitively replies to the recipient (rather than myself).  However, if I reply to a sent email in Evolution, it replies to myself (which, really, is not too intuitive).  Is there a plugin / setting to alter this?

---

### Post by jermza on 2010-01-11
Also, unless I'm doing something wrong, Evolution's HTML / CSS support seems to be wanting when compared to Gmail.  For example, if I receive an email notification that someone is following me on Twitter, Gmail lays out the message, I would guess, in the way that Twitter designed it.

Evolution seems to leave out parts of the aesthetics, rendering the full HTML message slightly mediocre.

Is there a way to rectify this?  Setting or plugin, perhaps?

---

### Post by SirBismuth on 2010-01-11
> **jermza said:**
> Not sure where to ask this, but I'm running Evolution Mail and it is synced to my Gmail. 

Two small issues:

- Evolution doesn't mark my Gmail messages as read (or am I missing something?);

- Evolution has a slight "bug": in Gmail, when I reply to an email that I've sent, it intuitively replies to the recipient (rather than myself).  However, if I reply to a sent email in Evolution, it replies to myself (which, really, is not too intuitive).  Is there a plugin / setting to alter this?

Issue #1:  No idea, I access Gmail via the web when I am not at home, so mark the emails as read then.  When I get home, I just download the mails, including ones that I've sent, which are then removed from Gmail's servers

Issue #2:  I do this often in Evolution, to reply to an email that you have sent, say from your Sent folder, use "Reply to All", instead of "Reply".  Then Evolution will bring up a message which have included any recipients you sent the message to, but not yourself.  I am currently using Evolution 2.28.1, but have done the same in all previous versions that were included since Ubuntu 8.04.

HTH

B

---

### Post by jermza on 2010-01-11
> **SirBismuth said:**
> Issue #2:  I do this often in Evolution, to reply to an email that you have sent, say from your Sent folder, use "Reply to All", instead of "Reply".  Then Evolution will bring up a message which have included any recipients you sent the message to, but not yourself.  I am currently using Evolution 2.28.1, but have done the same in all previous versions that were included since Ubuntu 8.04.

HTH

B
Thanks for that.  I'm wondering if I should use Gmail as a standalone app rather...

---

### Post by jermza on 2010-01-11
It's a pity that Evolution's HTML formatting is funky, because it's such a nice app over all.  Gmail clearly leads the way where email / HTML formatting is concerned.

Hopefully, Evolution will be updated soon.

---

### Post by Temposs on 2010-01-11
> **jermza said:**
> Also, unless I'm doing something wrong, Evolution's HTML / CSS support seems to be wanting when compared to Gmail.  For example, if I receive an email notification that someone is following me on Twitter, Gmail lays out the message, I would guess, in the way that Twitter designed it.

Evolution seems to leave out parts of the aesthetics, rendering the full HTML message slightly mediocre.

Is there a way to rectify this?  Setting or plugin, perhaps?

Could it be that you have evolution blocking images in HTML messages?

---

### Post by jermza on 2010-01-11
> **Temposs said:**
> Could it be that you have evolution blocking images in HTML messages?

Not at all.  I'm a big fan of HTML emails / RSS feeds etc, so I made sure I checked the relevant options.

What's interesting is that, in Gmail, inline images and text are spaced correctly.  In Evo, the same email seems to double space the line breaks and create a generally funky email.

---

### Post by jermza on 2010-01-11
I've just received a Facebook friend request,and the HTML formatting is also a bit odd.  I've opened Gmail and can see exactly how it's supposed to appear.  Evolution has more or less got it right, but it's clearly incorrect.

Not sure if there's a fix for this?...

---

### Post by jermza on 2010-01-11
> **jermza said:**
> 
- Evolution doesn't mark my Gmail messages as read (or am I missing something?);


This is solved.  I was using POP instead of IMAP.

---

### Post by J V on 2010-01-11
> **jermza said:**
> I've just received a Facebook friend request,and the HTML formatting is also a bit odd.  I've opened Gmail and can see exactly how it's supposed to appear.  Evolution has more or less got it right, but it's clearly incorrect.

Not sure if there's a fix for this?...Is it displaying the HTML code, or just looks wierd?

Chances are because GMAIL is actually *on* the internet, there are certain CSS files that are loaded on the website...

Evolution can't know where or which CSS files it has to download...

Perhaps theres a plugin to manually download CSS files?

---

### Post by jermza on 2010-01-12
This is why Gmail leads the way.  They make their stuff work the way it was intended.  An email gets made to look a certain way, and that's how it arrives in Gmail.  (You can, of course, choose plain text.  But you have the choice.)

Which is a pity.  Open source - especially Ubuntu - should be on par.

I'll hunt around for plugins.  Thanks.

---

### Post by SirBismuth on 2010-01-12
I view emails in text by default in Evolution, but often when I receive an email that is meant to be viewed in HTML format, there is an attached called "attachment.html".  If I open this file, in Evolution, I can view the email as it was intended by the sender, and is correctly formatted.

At least this has been my experience.

B

---

### Post by audiomick on 2010-01-12
> **jermza said:**
> This is why Gmail leads the way.  They make their stuff work the way it was intended.  An email gets made to look a certain way, and that's how it arrives in Gmail.  (You can, of course, choose plain text.  But you have the choice.)

Which is a pity.  Open source - especially Ubuntu - should be on par.

I'll hunt around for plugins.  Thanks.

You could see this the other way around as well. It is a pity gmail doesn't stick rigidly to open standards instead of cooking their own brew.;)

---

### Post by jermza on 2010-01-12
> **audiomick said:**
> You could see this the other way around as well. It is a pity gmail doesn't stick rigidly to open standards instead of cooking their own brew.;)

Really?

Gmail's and Evolution's version of the same email (from comics.com) attached.

If you ask me, I'd say Gmail's "own brew" (that "doesn't stick rigidly to open standards") is preferable...

---

