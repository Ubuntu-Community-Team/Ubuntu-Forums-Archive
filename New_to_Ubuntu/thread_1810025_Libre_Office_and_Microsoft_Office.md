---
title: "Libre Office and Microsoft Office"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-07-22
I do not have Microsoft Office. When I save the files from Libre Office in Microsoft Office format eg: doc, docx, etc, there are compatibility issues like: sometimes the tab spaces disappear, sometimes animations from Impress disappear. Why is it so and how do I solve it?

---

### Post by Paddy Landau on 2011-07-22
> **RobikShrestha said:**
> Why is it so ...?
Because Microsoft is a closed format, so LibreOffice and OpenOffice have to guess how to convert. Naturally, there will be discrepancies.

Also, I have on occasion found that LibreOffice can do something that MS Office cannot, so obviously that cannot be retained.

> **RobikShrestha said:**
> ... how do I solve it?
Three solutions occur to me.

[LIST]
[*]Keep to simple formatting, using Styles as much as possible.
[*]Install MS Office onto Linux using PlayOnLinux (not perfect, but tolerable).
[*]Use Windows (either as dual-boot or, if your computer is powerful enough, in a [Virtual Box]("http://www.virtualbox.org/")).
[/LIST]
Of course, if you don't have to save in MS Office format, then save in Open Document Format instead. MS has promised to support Open Document Format, but I'll believe it when it happens.

---

### Post by Jacobonbuntu on 2011-07-22
> **RobikShrestha said:**
> I do not have Microsoft Office. When I save the files from Libre Office in Microsoft Office format eg: doc, docx, etc, there are compatibility issues like: sometimes the tab spaces disappear, sometimes animations from Impress disappear. Why is it so and how do I solve it?


  	 	 	 	 	 	  Hi RobikShrestha
 

 I am no specialist, but I talked about this with my oldest sun (and he *is* a specialist :)) some time. What he says is that Microsoft is rather messy in underlaying layout definitions, and not respecting general standards. For the same reason it is rather awful for designers of for example email-newsletters to guarantee that layout will be all right in Outlook.
 This is not a typical “Linux user's criticizing”, simply because he isn't using it.  
 I noticed in the installation of the latest MS Office-versions you can specifically choose for “odf-format-support”. I can imagine the compatibility will be better in that case.

---

### Post by Grenage on 2011-07-22
While you can never guarantee that documents will convert perfectly, you always have the option of saving a PDF copy.  It's not what you asked for, but if your situation involves documentation being merely readable in the correct format (CVs, etc), it's an option.

---

### Post by Jacobonbuntu on 2011-07-22
> **Paddy Landau said:**
>  MS has promised to support Open Document Format, but I'll believe it when it happens.
...as I said in my post, I noticed they kept their word....
good old Microsoft 8-)

---

### Post by Paddy Landau on 2011-07-22
> **Jacobonbuntu said:**
> ...as I said in my post, I noticed they kept their word....
good old Microsoft 8-)
And it works correctly? That's a new MS; I had read they were trying to derail the process. Well done to them.

---

### Post by Jacobonbuntu on 2011-07-22
> **Paddy Landau said:**
> And it works correctly? That's a new MS; I had read they were trying to derail the process. Well done to them.

...I must say I didn't check it thoroughly, as I switched to Linux shortly after I installed the latest version of MS Office :P. Furthermore, you have to choose for the odf- support-option on installation. Most people will choose not to do that I guess, keeping the compatibility poor in practice.

edit:
out of curiosity, I installed MS Office 10 on my Vbox W7. this is the message on startup.
in the helptext of MSOffice however, a lot of reservation is being made; no guarantee it works.
practice will prove if it is any good.

---

### Post by Hagar Delest on 2011-07-22
Better avoid the OOXML format anyway, have a look at: [MS Office 2007 OOXML file format (docx, xslx, pptx, ppsx)](http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=4542).

---

### Post by Jacobonbuntu on 2011-07-22
> **Hagar de l'Est said:**
> Better avoid the OOXML format anyway, have a look at: [MS Office 2007 OOXML file format (docx, xslx, pptx, ppsx)]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=5&t=4542").
....interesting stuff. I guess Microsoft is not really interested in 1:1 compatibility as long as it has the biggest share.....\\:D/

---

### Post by RobikShrestha on 2011-07-22
Thanks for the reply.
If someone has already installed microsoft office w/o odf support, I can't do anything. So I save them in pdf format. I think, saving each document in odf, microsoft and pdf format is the best way to go. We won't lose anything after doing that.

---

### Post by Paddy Landau on 2011-07-23
> **Jacobonbuntu said:**
> out of curiosity, I installed MS Office 10 on my Vbox W7. this is the message on startup.
in the helptext of MSOffice however, a lot of reservation is being made; no guarantee it works.
That is so typical of MS. Making **in**compatibility the default. Can you imagine the outrage if OpenOffice or LibreOffice came with MS compatibility off by default?

---

### Post by The Cog on 2011-07-24
I have read (not tried personally) that MS have written their imlementation of .ods spreadsheets to remove all spreadsheet formulas and replace with fixed values if the spreadsheet wasn't actually created in MS office. I've seen the odd post asking "why has my formula disappeared", so I believe the reports to be true.

---

### Post by Jacobonbuntu on 2011-07-24
> **The Cog said:**
> I have read (not tried personally) that MS have written their imlementation of .ods spreadsheets to remove all spreadsheet formulas and replace with fixed values if the spreadsheet wasn't actually created in MS office. I've seen the odd post asking "why has my formula disappeared", so I believe the reports to be true.

I can say from my own experience that this is true!!!
as I read your post I remember having the same experience. I once opened a OO spreadsheet in MS Office, did a minor change, saved it and the next time, in OO, I had to redefine all formulas!!!

kind of sick isn't it...

---

### Post by Hagar Delest on 2011-07-24
See here for some links: [MS Office 2007 to support ODF in SP2](http://user.services.openoffice.org/en/forum/viewtopic.php?f=49&t=13334).

---

### Post by Paddy Landau on 2011-07-24
Is this really true? My word, I can just imagine the code:
```
if speadsheet created by Microsoft then
        save all formulae
else
        erase all formulae
```Have you fellows raised this as a bug with Microsoft and referred to it in its public forums?

---

### Post by Jacobonbuntu on 2011-07-24
I am afraid I don't come often on other fora... :)

to the OP (if he is still around) keeping three versions of everything might be a bit overdone :)
I run a small non-profit organization, with 5 co-workers. We work in a mixed combination of all possible OS -es. We use LibreOffice for all inside communication and shared documents, for outside communication we simply make a pdf, if necessary.

---

### Post by Hagar Delest on 2011-07-24
> **Paddy Landau said:**
> Have you fellows raised this as a bug with Microsoft and referred to it in its public forums?

:twisted:
What for? Do you think that MS will ever support correctly ODF? That would be firing a bullet in the foot!
MS can't live without the vendor lock-in policy.

But you can report it if you want. But as soon as it is fixed, you can be sure that there will be another problem elsewhere...

---

### Post by Paddy Landau on 2011-07-25
> **Hagar de l'Est said:**
> :twisted:
What for? Do you think that MS will ever support correctly ODF? That would be firing a bullet in the foot!
MS can't live without the vendor lock-in policy.

But you can report it if you want. But as soon as it is fixed, you can be sure that there will be another problem elsewhere...
Hagar, you are of course correct. However, making these reports brings it out into the open; with greater awareness, maybe reporters can pick up on it.

I would report it myself if I had MS Word and could test it.

---

### Post by Hagar Delest on 2011-07-25
I know, in fact it should be reported at least to show MS Office users that they can't really trust this application.

---

