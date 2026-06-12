---
title: "More Open Office Problems"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-04-29
I created a layout using a table and inserted all the data I needed into the table.

I saved the layout with the extension .doc

Just to be on the safe side I saved it to 2 partitions and to a flash drive before closing Open Office.

I then decided to check the document before emailing it to people. Guess what? A BLANK DOCUMENT!! All the table and data had gone from all the saved documents.

I labouriously re-did the document re-entering all the data before again saving it into three locations as a .doc document.

Just for the hell of it I also saved it as a .odt document.

Guess what - everything disappeared from the .doc document but I do still have the .odt document.

As the people to whom the document has to be sent all use Windoze, how do I get it to them in a format that they will be able to open??

I opened the .odt document in Abiword then saved it as a .doc document.

I then tried viewing it in Open Office.......it worked!

So it would seem that if I want to create a document in Open Office that can be viewed in M$ Word I must save it as an .odt from Open Office then open it in Abiword and save it as a .doc document.

I wonder if using M$ Word might be easier?!?!?

---

### Post by llamabr on 2009-04-29
shouldn't you save it as xls?

---

### Post by kerry_s on 2009-04-29
why didn't you just do it in abiword in the first place and save it as a .doc, instead of ooowriter> .odt> abiword> .doc ?

---

### Post by Captain Legless on 2009-04-29
> **llamabr said:**
> shouldn't you save it as xls?

I created the document in "Writer".
There's no option to save it as an .xls file.

---

### Post by Captain Legless on 2009-04-29
> **kerry_s said:**
> why didn't you just do it in abiword in the first place and save it as a .doc, instead of ooowriter> .odt> abiword> .doc ?

Had I known that I was going to have these problems I might just have done that - hindsight is a wonderful thing.

---

### Post by Captain Legless on 2009-04-29
Nobody got any suggestions? :(

---

### Post by Captain Legless on 2009-04-29
Bump!

---

### Post by Big_astur on 2009-04-29
Can't you upload the file here?

I could check if it's only a problem on your side or if it happens also here.

Just the layout, no need to add the info to the table, or just add some false one.

Sorry but it's the only thing i can help you with.

---

### Post by Captain Legless on 2009-04-29
I can upload it in it's basic layout as an .odt
Thanks.

---

### Post by alphacrucis2 on 2009-04-29
> **Captain Legless said:**
> I can upload it in it's basic layout as an .odt
Thanks.

I tried it and can confirm the problem. The doc file isn't actually empty but displays as blank when reading it back in. Have you actually tried openning it in word? The problem could either be in the conversion to doc or the import conversion back into OO writer.

---

### Post by Big_astur on 2009-04-29
I guess i found the problem.

When i saved it as .doc i had the same problem as you described. 

Then i thought that it might be a layout problem and tried one thing. In your table, the left side it is "outside" of the page. I mean that if you move a bit to the right the left border line then it works. I just moved it a bit, till the line you see as reference, when moving it, coincides with the page delimitation border.

EDIT: If you need a picture to show you what i did just tell me. I'm sorry I'm Spanish and maybe i don't express myself so well.

---

### Post by alphacrucis2 on 2009-04-29
I just tried copying the saved .doc file over to my old windows PC and opened the file in Word 97 and it displays blank apart from a double vertical line at the right hand margin. Definitely looks like a bug the OO output conversion. Should be reported on launchpad.

---

### Post by brunogirin on 2009-04-29
I can confirm the problem too. As a temporary workaround, you can export it to PDF so that Windows users can open it.

---

### Post by Big_astur on 2009-04-29
Please read my previous post to find the solution.

---

### Post by Captain Legless on 2009-04-29
Thanks for the quick attention and reply.

No I haven't tried opening it in Word, haven't been using Windoze actually and just assumed that as it appeared blank that there was nothing to open.

I'll take your word for what you say about the conversion process. It seems a strange anomaly to contend with if I want to continue to use OO to edit documents intended for use in M$ Word. :?

---

### Post by alphacrucis2 on 2009-04-29
> **Big_astur said:**
> I guess i found the problem.

When i saved it as .doc i had the same problem as you described. 

Then i thought that it might be a layout problem and tried one thing. In your table, the left side it is "outside" of the page. I mean that if you move a bit to the right the left border line then it works. I just moved it a bit, till the line you see as reference, when moving it, coincides with the page delimitation border.

EDIT: If you need a picture to show you what i did just tell me. I'm sorry I'm Spanish and maybe i don't express myself so well.

Well spotted! Your solution worked for me.

---

### Post by lavinog on 2009-04-29
Another thing you can do is if you know the recipents need to just view the document, export it to pdf.
Also open office is free and cross platform. Windows users can install open office.

---

### Post by Captain Legless on 2009-04-29
> **Big_astur said:**
> I guess i found the problem.

When i saved it as .doc i had the same problem as you described. 

Then i thought that it might be a layout problem and tried one thing. In your table, the left side it is "outside" of the page. I mean that if you move a bit to the right the left border line then it works. I just moved it a bit, till the line you see as reference, when moving it, coincides with the page delimitation border.

EDIT: If you need a picture to show you what i did just tell me. I'm sorry I'm Spanish and maybe i don't express myself so well.

Sorry - I missed your reply initially, there are many replies coming in very quickly and I missed a couple.

Anyway - YOUR RIGHT!! 

I did what you said and it fixed the problem straight away.
Where were you at midnight last night, (my time), when I was trying to sort the problem out!:P

Thanks for you attention guys - mark this one solved :KS

---

### Post by brunogirin on 2009-04-29
> **alphacrucis2 said:**
> Well spotted! Your solution worked for me.

Big_astur's workaround worked for me too. Anyway, I'm off to Lauchpad to file a bug on the subject, with the details of the workaround. I'll post the link when I'm done so that you can subscribe to it.

---

### Post by Captain Legless on 2009-04-29
> **brunogirin said:**
> Big_astur's workaround worked for me too. Anyway, I'm off to Lauchpad to file a bug on the subject, with the details of the workaround. I'll post the link when I'm done so that you can subscribe to it.

Well Done - It might help somebody else with the same problem. ;)

---

### Post by brunogirin on 2009-04-29
The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/369290](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/369290)

I would appreciate if you guys could read it and tell me if I missed anything. In particular, try to go through the steps I detail to see if they make sense. Also, if anybody can test with OO.o on Windows and confirm whether the same problem occurs, that may help the triage and debug process.

But be patient, Launchpad seems to be slightly unstable today so you may have to try several times before you get to the bug report.

---

### Post by Captain Legless on 2009-04-29
I checked out launchpad and went through the steps you provided.
Well done - all looks OK.

DOn't know when I'll be booting into Windoze but when I do I'll check it out.

Thanks again for your help.

---

### Post by raydeen on 2009-04-29
I replicated the problem and solution with the Mac versions of OOo (3.0.1) and Office (Word 2004) as well.

---

### Post by whakim on 2009-04-29
Actually my issues are far more serious. The temporary fix suggested does work, but when I save the file as a Word 97/XP document and then reopen it, the table itself is missing. It simply disappears. I have replicated this many times in the last few minutes itself.

---

### Post by whakim on 2009-04-29
As a follow-up, when I open the document in Abiword I can see the table, though for some reason the numbers are covered in black. I have attached a screen capture. 

When I open this same file in OpenOffice, the table is simply missing. All I see is the header.

---

### Post by brunogirin on 2009-04-29
@whakim: does the temporary workaround suggested by Big_astur work in your case?

If yes, it's probably another manifestation of the same bug. In any case, don't hesitate to add more information to the bug report.

---

### Post by whakim on 2009-04-29
It works but only for the session. If I save the file, close it, & reopen, things are back at square one. 

For now working in .odt format instead of .doc seems to work. But I am working on this document along with co-authors who use Word & need to be able to edit it. I'm really not sure what the solution is. 

Also, saving as Word 2003 xml results in a completely blank file.

---

### Post by brunogirin on 2009-04-30
> **whakim said:**
> It works but only for the session. If I save the file, close it, & reopen, things are back at square one. 

For now working in .odt format instead of .doc seems to work. But I am working on this document along with co-authors who use Word & need to be able to edit it. I'm really not sure what the solution is. 

Also, saving as Word 2003 xml results in a completely blank file.

Can you post your file here? Or a simplified version of it that exhibits the bug. I'll then try to reproduce and if need be create a different bug report.

---

### Post by whakim on 2009-04-30
Which bug? It won't allow me to upload the xml file, saying it's an invalid file. The odt & doc files are too large. I don't know about reproducing the error because it seems really random. The document has 12 tables & each time I do this, a different one vanishes. 

If Launchpad allows larger files I can upload them there. 

In the meantime, does anyone know of a way to get OpenOffice 2.4 or 3.0.0 for Jaunty from the repositories? I tried installing the debs but it won't work, it just crashes. I'm kind of desperate because I'm bumping up against a deadline & I simply cannot get my work done like this. I can't even move to a Windows machine because I don't have a functioning doc file. Panic is slowly setting in.

---

### Post by brunogirin on 2009-04-30
If you remove some of the tables, can you create a small test file that shows the behaviour you describe? Or does it only appear with large files?

In terms of your deadline, what about using an alternative such as AbiWord for the time being?

---

### Post by whakim on 2009-04-30
Abiword doesn't handle graphics. Woe is me. Lotus Symphony handles graphics but not equations. Even more woe is me. The file has lots of both. 

I cut all the text & graphics out of the file to meet the size limits. So of course it behaves a little differently from when all that stuff was in there. If you go to Page 7 & further, Tables 9, 10, & 11 are missing in OO. When you open the file in Abiword, they are visible but seriously weird-looking. Not blacked-out like before (& that is the difference). I have attached a screen capture so you see what I mean.

---

### Post by Captain Legless on 2009-05-14
Looks like you've got 'em stumped with this one!

---

### Post by jemjem on 2009-06-16
> **Big_astur said:**
> I guess i found the problem.

When i saved it as .doc i had the same problem as you described. 

Then i thought that it might be a layout problem and tried one thing. In your table, the left side it is "outside" of the page. I mean that if you move a bit to the right the left border line then it works. I just moved it a bit, till the line you see as reference, when moving it, coincides with the page delimitation border.

EDIT: If you need a picture to show you what i did just tell me. I'm sorry I'm Spanish and maybe i don't express myself so well.

It worked for me, too.
But I have lots lots of documents that has lots of problem.
So is there a bacth mode or something else ?

Anyway, it saved my life a bit. Thanks.

---

### Post by jemjem on 2009-06-17
> **jemjem said:**
> It worked for me, too.
But I have lots lots of documents that has lots of problem.
So is there a bacth mode or something else ?

Anyway, it saved my life a bit. Thanks.

I have found a program for windows to convert odt to doc, doc to odt. May be this post helps someone in the future. 

[http://www.abadev.com/doc_conv/index.html](http://www.abadev.com/doc_conv/index.html)

---

### Post by Captain Legless on 2009-06-17
All well and good but that program is $60!

---

### Post by lavinog on 2009-06-17
Also what if it is no better than the current conversion built in to oo

---

