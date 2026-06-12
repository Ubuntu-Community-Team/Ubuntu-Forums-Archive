---
title: "[SOLVED] Is there an OpenOffice Spreadsheet Expert in the House???"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by suomalainen on 2008-12-11
Ubunteros,

This may not be the place for this post, and if it isn't, please advise where is.... Thanks

I got this problem. I have an Excel spreadsheet I imported into Ubuntu 8.04LTS. But for some strange reason it isn't correctly adding my numbers nor allowing me to MANUALLY enter "Item Categories" that explain certain credits and debits.

Is there an expert in the house that can check out my spreadsheet to see what is wrong?

Perhaps an OpenOffice spreadsheet calculation formula needs to be used which I don't know how to use?

If anyone can assist I can send the spreadsheet anyway you like. Including posting it here.

Thank you

---

### Post by gettinoriginal on 2008-12-11
Is this an actual Windows Excel that you imported, or is it Open Office ??  I am not an expert, but have set up and use spreadsheets at work and at home, so if interested, I would be willing to try to help you.

---

### Post by Therion on 2008-12-11
I live and die by Excel and Calc, though I wouldn't call myself an "expert".  But anyway, yeah...  Bring it on.  Emailing me the workbook would be the easiest thing so we're both looking at the same thing at the same time.  Also, if you use IM my Yahoo! ID is in my pro and I'm currently available.  Slow day at the office, dontcha know...

---

### Post by suomalainen on 2008-12-11
Fellow Ubunteros!

Thank you for offering me assistance.

Here is some background on the spreadsheet. Please let me know if anything is unclear.

Columns "C" to "L" will contain dollar values. These dollar values can be either positive or negative.

Each column has a heading and the heading may appear obvious. For the sake of avoiding avoid confusion, please ignore the names of each column. Just accept the fact that each row can contain only 1 negative or 1 positive dollar value but never both or more than one dollar value per row. Naturally, this excludes the balance total appearing to the right hand margin.

As the spreadsheet I attached shows, there is just and only one dollar value per a row. This dollar value is either added or subtracted from the balance which appears in the row above it to the right hand margin. As seen, the balance column appears on the right hand margin.

What needs to happen on this spreadsheet is that an "Item Description" is MANUALLY entered. No drop downs allowed. Then the dollar value is entered which in turn will either add to the balance or subtract from it.

I attached the spread sheet for your review. If I was unclear please say this to me and I will try to better clarify.

Thanks again for reaching out!

Look forward to your reply!

---

### Post by ubuntu27 on 2008-12-11
I am not an expert in OpenOffice.org Spreadsheets since I do not use it. (I only use Writer). Hope the others can help you in that.

I want to recommend you some websites that provide guides, tricks, and support for OpenOffice.org

Here are the links:
[LIST]
[*][URL="http://openoffice.blogs.com/openoffice/"]
[*]OpenOffice.org Training, Tips, and Ideas[/URL]
[/LIST]

> A web blog by OpenOffice.org and StarOffice instructor with a passion for showing how the software makes things easier.

[LIST]
[*][Plan B for OpenOffice.org]("http://plan-b-for-openoffice.org/index")
[/LIST]

> This is "Plan-B" for frustrated, non technical users of the Open Office productivity suite. A visual software manual with videos and a smart search engine. 
[LIST]
[*][Tutorials for OpenOffice]("http://www.tutorialsforopenoffice.org/")
[/LIST]

> FREE assistance to anyone learning, teaching or using OpenOffice.org.

---

### Post by suomalainen on 2008-12-11
Thank you everybody for the offers of asistance. I sent private messages to you regarding how to send the file. Apparently xls files are not allowed in the forum as attachments.

I also appreciate the additional "Study material" offered. It will be useful in learning OpenOffice better.

Thanks and I look forward to your replies.

---

### Post by LowSky on 2008-12-11
You might want to install OpenOffice 3.0 it has better Microsoft file support than ever before.
there is also IBM Symphony, which is based on OpenOffice and from what I hear pretty nice.

---

### Post by albinootje on 2008-12-11
As an alternative you can try gnumeric for spreadsheets. 
Last week i needed to edit some cvs file, and in that specific case it was much easier to edit it in gnumeric than in openoffice.

---

### Post by Bladeforger on 2008-12-11
Not sure if you're looking for a macro to enter the data (more complicated than you would want to write at this  point) or just help setting it up.  

I will throw in this general advice...  if you need to make sure that there aren't unwanted multiple entries in too many columns and/or not enough entries, then you can put in something like
 ```

=IF(COUNT(A7:Z7)=2;"OK";"Problem")

```
(Say in column AA)

This is an example from row 7 and you would change the "A" and "Z" to suit your purposes.  You simply copy the formula to all rows on the same column and it will pop up "Problem" on any rows with any number of numeric entries different from 2 (the number and the total).  Adjust to suit.  Hide column when you don't need it.  Good troubleshooting method.  Also see counta() if you want to check for text AND numbers.

Hope this helps some.

Keith

---

### Post by ubuntu27 on 2008-12-11
Also.. I forgot to mention that there is a Official OpenOffice.org forum. 
I think there are more experience users there:

[OpenOffice.org's Community Forum]("http://user.services.openoffice.org/en/forum/listforums.php")

And here is a non-official forum:

[OpenOffice.org Forum]("http://www.oooforum.org/")

---

