---
title: "Scrambled Emails With Evolution"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by ChipRed87 on 2011-03-15
Hi all,

I'm new to the forums here and Ubuntu also for that matter.:D

I'm Enjoying using the Operating system so far, but I've ran in to a few quirks most of which are nothing major.

HOWEVER, one such issue that is a large problem is with the email client Evolution.
After adding support for Exchange 2010(via the Synaptic package manager), I can send and receive emails with my Company Email address.:D (Yay!) The problem that persists is I will occasionally compose and send an email, only to find out (via my sent items or a reply) that no one can read the darn thing, because its GIANT jumble of random characters!:(

I'm running 10.10 on a z200 HP workstation

I've attached an example of what I end up sending...

Can someone please clue me in on how to fix this before the entire organisation I work for thinks I'm insane.](*,)

Thanks in advance!

---

### Post by Sickpuppy87 on 2011-03-15
Just out of curiosity what format are you sending as html or plain text? 

When you are typing a new message go to format tab.

---

### Post by ChipRed87 on 2011-03-16
It is set to Plain text.

---

### Post by Old_Man_Unix on 2011-03-16
If this is your only problem with using Evolution as an Exchange 2010 client, consider yourself lucky.  Out-of-the-box, Evolution generally doesn't work with Exchange 2010 (thank you very much, Microsoft).  The current MAPI plugins - such as the ones you installed - are sometimes only partially successful.  Development of this interface in Evolution is an actively on-going project.

Insofar as your specific problem is concerned, I can only quote the Evolution documentation:

> If your recipients can’t read your messages, try selecting a different character set in the composer options dialog box. For some languages, such as Turkish or Korean, it might work best for you to select the language-specific character set. However, the best choice for most users is UTF-8, which offers the widest range of characters for the widest range of languages.
If this is a constant problem, I would try changing the character set.  

Perhaps the newer Exchange Web Services packages for Evolution - which may be ready some time in May - might solve this. 

You can also consult with your mail administrators to see if they know of a solution.  There is a version of Evolution for Windows, so perhaps they may know of one from that combo.  I would not expect it though -  IME most MS admins are woefully unaware of Linux applications.

---

