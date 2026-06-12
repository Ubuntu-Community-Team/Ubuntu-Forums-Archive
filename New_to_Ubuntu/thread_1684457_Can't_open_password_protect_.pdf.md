---
title: "Can't open password protect .pdf"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by AkaChan83 on 2011-02-09
So, I'm trying to open a book for one of my university of phoenix classes but after I type in my username and password in the .pdf I can't hit the "Unlock" button to open the dang thing. :confused::confused::confused:

---

### Post by cipherboy_loc on 2011-02-09
Do you have access to a Windows computer? Open it up in Windows and see if you can save it without a password.

Post back if that doesn't work. I might know of something else that will work.

Cipherboy

---

### Post by Mark Phelps on 2011-02-09
Looks like you're trying to open it to make changes -- which you're NOT going to be able to do.  Preventing changes to documents is one of the primary reasons folks convert them to PDF in the first place.

However, you should be able to READ the PDF file.  Just don't try to open it in a document editor of any kind.

---

### Post by gdonwallace on 2011-02-09
I had some problems with password protected pdf's a while back.

Try using **foxit** I was able to open password protected files with it.

Good luck.

---

### Post by beew on 2011-02-09
Try this.[URL="http://www.ubuntugeek.com/howto-crack-pdf-file-password.html"]
http://www.ubuntugeek.com/howto-crack-pdf-file-password.html[/URL]

Edited: Once you figured out the password I think you can use evince (the document reader) to open the pdf and save an unencrypted copy.

---

### Post by Mark Phelps on 2011-02-10
Good Luck with that password cracking.  Unless the person who created the password was really STUPID and used something like "123" or "abc", the time that it will take to crack it will vary from HOURS, to DAYS, to WEEKS!

Unlike in the movies, real password crackers can't work on one character at a time.  All they can do is generate a password, try it, see if it works, and then do this over again.

Any reasonably complex password consisting of upper case letters, lower case letters, numbers, and special sumbols is going to general MILLIONS of combinations.  Even a very fast machine is going to take a long time to try all the combinations.

Think about it -- if it really was so simple that you could run of these password crackers and hack the file in just a few minutes, what would be the point of password protecting it in the first place?

---

### Post by HermanAB on 2011-02-10
Howdy,

Open the file with Xpdf.  It simply ignores all that cruft.

Alternatively, open the file with a programmer's editor and delete the password stanza (usually towards the end of the file).

---

### Post by AkaChan83 on 2011-02-21
I guess I forgot to subscribe to this thread (thought I had it set to do that automatically) so I didn't check back to see if anyone responded, oops! Anyway...

> **cipherboy_loc said:**
> Do you have access to a Windows computer? Open it up in Windows and see if you can save it without a password.

Post back if that doesn't work. I might know of something else that will work.

Cipherboy

Thank you for your response but I can't save it without the password :(

> **Mark Phelps said:**
> Looks like you're trying to open it to make changes -- which you're NOT going to be able to do.  Preventing changes to documents is one of the primary reasons folks convert them to PDF in the first place.

However, you should be able to READ the PDF file.  Just don't try to open it in a document editor of any kind.

That's the thing: I can't read the .pdf.  I don't want to make any changes to it, I just want to read it. 

> **gdonwallace said:**
> I had some problems with password protected pdf's a while back.

Try using **foxit** I was able to open password protected files with it.

Good luck.

Foxit doesn't even give me a place to enter a username and password :(

> **beew said:**
> Try this.[URL="http://www.ubuntugeek.com/howto-crack-pdf-file-password.html"]
http://www.ubuntugeek.com/howto-crack-pdf-file-password.html[/URL]

Edited: Once you figured out the password I think you can use evince (the document reader) to open the pdf and save an unencrypted copy.
Evince won't let me click on the "Unlock" button in the document :( 


> **HermanAB said:**
> Howdy,

Open the file with Xpdf.  It simply ignores all that cruft.

Alternatively, open the file with a programmer's editor and delete the password stanza (usually towards the end of the file).
Xpdf won't even let me enter the username and password :(

> **Mark Phelps said:**
> Good Luck with that password cracking.  Unless the person who created the password was really STUPID and used something like "123" or "abc", the time that it will take to crack it will vary from HOURS, to DAYS, to WEEKS!...

If you would have read the entire 30 or so words I posted you'd understand that I HAVE the username and password, I'm not trying to "crack" anything.  I have a degree in math and in less time than its taking me to respond to your condescending post, I could figure out exactly how many different combinations I'd have to try if I really wanted to do something as ridiculous as crack the password to an operations management book that I don't even really want to read in the first place but unfortunately have to as is required by the syllabus ;)

Thanks to all of you who offered help. This is really frustrating :mad:

Edit - I attached a screenshot so you can see what I'm talking about *sigh* (lol @ the "take screenshot" in the attachment..hey, i've never used the screenshot tool before :) )

---

### Post by grahammechanical on 2011-02-21
Can I join the list of those saying something stupid and adding to your frustration? From the screenshot you are at the first page of the book which has 827 pages. Have you tried hitting Next? I notice that the down arrow - Next button is available.

I am also wondering about the subject that you are studying. What is so special about it that the study books have to be password protected?

Regards.

---

### Post by AkaChan83 on 2011-02-22
> **grahammechanical said:**
> Have you tried hitting Next? ...

I am also wondering about the subject that you are studying. What is so special about it that the study books have to be password protected?

Regards.

Yes, I've tried hitting next. All of the rest of the pages just have the pdfprotector (or whatever it is) logo on it (when I open it using evince) and all of the pages are just black when I try it using, say, foxit. 

Nothing is so special about the subject.  University of Phoenix does this to ALL of their online books if you want to download the whole book (instead of reading individual chapters through your UOP homepage).

---

### Post by baha'a on 2011-02-28
Hi guys,
AkaChan83, I have the same problem you had, can I know what happened, could you open the text?
I found a bug report related
[https://bugs.launchpad.net/poppler/+bug/472538](https://bugs.launchpad.net/poppler/+bug/472538)
and seems that they didn't fix it yet, any help?

thanks.

---

### Post by gradinaruvasile on 2011-02-28
Hm. Did you try to open it in Adobe PDF reader (it has Linux version, it is even in the repos)? Because that should work...

---

### Post by Rokefuller on 2012-12-23
Has University of Phoenix help desk given you any recommendations concerning this issue?

---

### Post by IsaacJGL on 2012-12-24
I think you can just go to 'properties' and set it to read and write.

---

### Post by overdrank on 2012-12-24
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

