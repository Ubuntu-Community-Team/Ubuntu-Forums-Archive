---
title: "PDF Form Creator Needed"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by matt-lisa on 2009-02-20
Good evening fellow Linuxians (Sorry, its a name that a mate gave to me because I crossed over to what he calls the darkside!...poor misguided fool)

I have a bit of a dilemma. As a volunteer Rural Fire Fighter, and 1st officer of a brigade, (in Queensland) I have to fill out a heap of forms after every incident, stubbed toe, requisition, membership application etc.

What I am trying to do is recreate the current paper forms into a .pdf or .doc or .odt format that can be filled out on a terminal and emailed to district office in the same look and feel as the paper forms and possibly have the ability to export the data to other applications.

We have this available in our incident management forms in a word format but it gets corrupted when I try to open it in open office (even though it understands most .doc files

I would really appreciate some help on this as I want to help drag the rural fire service kicking and screaming into the 21st century (and I hate filling out forms that could be so easily emailed immediately after an incident) but dont have the know how.....yet.

Thanks in advance

Matt

---

### Post by egalvan on 2009-02-20
> **matt-lisa said:**
> Good evening fellow Linuxians 

I have a bit of a dilemma. As a volunteer Rural Fire Fighter, and 1st officer of a brigade, (in Queensland)
 I have to fill out a heap of forms after every incident, stubbed toe, requisition, membership application etc.
Matt

Welcome indeed, Fellow Linuxian, :p
And Brother Fireman. ;)

As a Lieutenant in a company (one engine, one medic; similar to a brigade), I can sympathize with the paperwork mess.

I cannot help with this, but I too would like this information.

I have a computer and scanner ready to go.

ErnestG

---

### Post by Pollox on 2009-02-20
A quick web search for "openoffice form" turns up a number of tutorials on how to make forms in OpenOffice format, so it seems that you could make a form that way much the way you could in Word.  You could then fill out the forms, export it to pdf, and send it off to the district office, and they can open it with whatever pdf software they use and still have it look exactly the same as it did on your end.  If it still needs to be editable after you email it, I'm not sure what you could do other than have them install OpenOffice too.  I haven't actually tried this myself (making forms) but hopefully this gives you some ideas.

---

### Post by matt-lisa on 2009-02-20
As soon as I come up with something egalvan I'll let you know....life is too short to deal with unessesary paperwork. By the way, which fire brigade do you belong to and do you have a site? We're at [http://www.toogoomruralfire.webs.com]("http://www.toogoomruralfire.webs.com") 

Thanks Pollox, will give that a try today. I have heard of using OCR somewhere to basically scan the form and then create editable fields, but I think I maght just have to build this one from scratch.

---

### Post by The Cog on 2009-02-20
It may be worth uploading the .doc forms to google docs and then retrieving them in .odt format. I managed to get a good translation of a document that way - a document that openoffice itself couldn't convert.

Once it's in .odt format, you can use openoffice to export it to pdf if you want to.

---

### Post by Vadi on 2009-02-20
Would [Scribus]("http://www.scribus.net/") help?

[Click to install]("apt:scribus").

---

### Post by halitech on 2009-02-20
> **matt-lisa said:**
> Good evening fellow Linuxians (Sorry, its a name that a mate gave to me because I crossed over to what he calls the darkside!...poor misguided fool)

I have a bit of a dilemma. As a volunteer Rural Fire Fighter, and 1st officer of a brigade, (in Queensland) I have to fill out a heap of forms after every incident, stubbed toe, requisition, membership application etc.

What I am trying to do is recreate the current paper forms into a .pdf or .doc or .odt format that can be filled out on a terminal and emailed to district office in the same look and feel as the paper forms and possibly have the ability to export the data to other applications.

We have this available in our incident management forms in a word format but it gets corrupted when I try to open it in open office (even though it understands most .doc files

I would really appreciate some help on this as I want to help drag the rural fire service kicking and screaming into the 21st century (and I hate filling out forms that could be so easily emailed immediately after an incident) but dont have the know how.....yet.

Thanks in advance

Matt

Welcome from a former firefighter :)

there must be some kind of formatting issues with the original that is giving Open office issues when it tries to open it. Maybe as The Cog suggested, send it through google docs to get a version Open office will open.

> **matt-lisa said:**
> As soon as I come up with something egalvan I'll let you know....life is too short to deal with unessesary paperwork. By the way, which fire brigade do you belong to and do you have a site? We're at [http://www.toogoomruralfire.webs.com]("http://www.toogoomruralfire.webs.com") 

Thanks Pollox, will give that a try today. I have heard of using OCR somewhere to basically scan the form and then create editable fields, but I think I maght just have to build this one from scratch.

OCR is still hit or miss on the linux side (from what I've heard) so I think building from scratch is where you are going to have your best luck. What about creating a template with your info as a spreadsheet then as you enter fire info, you save each report with a date/time file name and also export it as a pdf that you can email to HQ? I'm guessing that HQ would have no reason to edit the info and they would simply want it for stats and archive purposes.

---

### Post by matt-lisa on 2009-02-25
Sorry all for the late reply. Thanks for all your suggestions and over the next few days (weeks) I'll be giving them all a shot. I'll post my results here if they are successful.

Cheers

---

### Post by HermanAB on 2009-02-25
When all else fails, I use The Gimp to edit PDF files.  It is a little awkward, but the Text tool can be used to overlay text anywhere you want.

Cheers,

Herman

---

### Post by dabuttman on 2010-02-16
From my experience at document creation, it is always easier to create from scratch.

There are some fancy-smancy apps out there that claim to OCR forms, but I have yet to use one that doesn't muddle up the forms to the point recreation is quicker then cleaning.

Vadi's suggestion appears to be the best solution for making pdf-forms outside of acrobat professional (not open-source, so not worth it).

If you are lucky and find a pdf form that is already created, but want to save your changes, this should work

```
pdftk input.pdf output output.pdf allow FillIn
```

---

