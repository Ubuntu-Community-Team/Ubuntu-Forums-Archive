---
title: "Importing emails into Evolution on  Meerkat"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by grey1beard on 2010-10-17
Having spent some time reading archived threads on most peoples problems, the preferred route to get emails from outlook express into evolution seems to be to go via Thunderbird.
Is this still the best route, or is there another way that I have not yet found ?
I'd be very grateful for anyone who has recently succeeded to confirm this as the best(or only) route.:neutral:

John

EDIT It's probably not relevant but I'm running a AMD64 Desktop with 10.10 and xp as dual boots, but the OE7 is on a separate laptop, so I'd be importing via a pendrive.

---

### Post by grey1beard on 2010-10-17
Not a good start!
I've just downloaded Thunderbird onto the laptop, and it only shows emails prior to Dec 2008.
Have now removed it, and await any replies here before I try again - or not.
John

---

### Post by JackNocturne on 2010-10-17
Sorry i didn't understand quite,, do you mean you just want the emails forwarded to Evolution? or did you mean contacts?

---

### Post by michaelzap on 2010-10-17
Check the Evolution FAQ page:
[http://live.gnome.org/Evolution/FAQ#How_can_I_migrate_my_mail_from_Outlook_to_Evolution.3F](http://live.gnome.org/Evolution/FAQ#How_can_I_migrate_my_mail_from_Outlook_to_Evolution.3F)

I did this a long time ago using Thunderbird as a bridge, and it was as easy as copying the TB mail files over to Ubuntu. If you're having trouble reading all of the Outlook Express email in TB on Windows, you might need to convert your files to Outlook (not OE) first. Depending upon the versions, those two programs were very different (and both of them are damn quirky, especially in their proprietary file formats).

The last time that I had to do something like this, however, I took advantage of the opportunity to upload all of the email on the Windows machine to an IMAP account instead of converting the local files. Then any email program can just connect to that IMAP account and badda bing badda boom there's your email. If that would be an advantage for you as well, now would be a good time to do it.

---

### Post by grey1beard on 2010-10-17
> **JackNocturne said:**
> Sorry i didn't understand quite,, do you mean you just want the emails forwarded to Evolution? or did you mean contacts?

Just the emails - I've just finished rebuilding my contacts list :(

Still, it was an opportunity to weed out some unlikely addresses :)

michaelzap
Yes, I've read of using the IMAP route, so it looks like a new can of worms whichever way I go.
I had hoped that there might be an easy route by now, and perhaps that is the easiest.

"It's like doing jigsaw puzzles in the dark"

John

---

### Post by grey1beard on 2010-10-18
I've just worked out a method.

I've created a set of folders in Evolution, corresponding to those in my OE.
I then select an email in OE on my laptop, forward it to myself, and receive it in Evolution on the desktop pc, and move it to the correct folder.
If I send them one at a time, in the order they were originally received, the new time stamp will allow me to have some idea of the original order.

Could be a long process, but if I find a batch method I will loose that bit of information, so I'm still hoping I can improve the method.

At least it does mean that I don't have to install any other program.

---

### Post by TNT1 on 2010-10-18
Duuno about the new evo version, but the version in 10.04 can import a .pst file...

---

### Post by grey1beard on 2010-10-18
pst works in Outlook, but not from outlook express.

Google tells me that I could import pst into express, but not export it.
John

---

### Post by TNT1 on 2010-10-18
> **grey1beard said:**
> pst works in Outlook, but not from outlook express.

Google tells me that I could import pst into express, but not export it.
John

Sorry, didn't see it was outlook express.

---

### Post by michaelzap on 2010-10-18
That's a terrible way to do this, imho. You will lose all of the sender and timestamp info, and it will take as long (or longer) as any possible method. If I were you, I would either:
[LIST]
[*]install Office with Outlook, convert your OE email to Outlook, and then import the PST into Evolution, or
[*]set up an IMAP account, copy your email to it in OE, and just connect to that in Evolution.
[/LIST]
You're making this a lot harder than it needs to be, I think.

> **grey1beard said:**
> I've just worked out a method.

I've created a set of folders in Evolution, corresponding to those in my OE.
I then select an email in OE on my laptop, forward it to myself, and receive it in Evolution on the desktop pc, and move it to the correct folder.
If I send them one at a time, in the order they were originally received, the new time stamp will allow me to have some idea of the original order.

Could be a long process, but if I find a batch method I will loose that bit of information, so I'm still hoping I can improve the method.

At least it does mean that I don't have to install any other program.

---

### Post by TNT1 on 2010-10-18
> **michaelzap said:**
> That's a terrible way to do this, imho. You will lose all of the sender and timestamp info, and it will take as long (or longer) as any possible method. If I were you, I would either:
[LIST]
[*]install Office with Outlook, convert your OE email to Outlook, and then import the PST into Evolution, or
[*]set up an IMAP account, copy your email to it in OE, and just connect to that in Evolution.
[/LIST]
You're making this a lot harder than it needs to be, I think.

Yeah, I'd go option one.

---

### Post by grey1beard on 2010-10-18
> **michaelzap said:**
> 
You're making this a lot harder than it needs to be, I think.

Story of my life  ](*,)

Thanks guys. It'll be one or t'other. I'll try No.1 first.
Regards
John

---

