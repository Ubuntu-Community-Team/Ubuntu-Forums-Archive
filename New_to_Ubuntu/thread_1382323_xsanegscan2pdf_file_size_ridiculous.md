---
title: "xsane/gscan2pdf file size ridiculous"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Knacker on 2010-01-15
hi,
i've been struggling with this for the better part of an hour and it's driving me out of my mind. i've looked everywhere for an answer and i can't find it. 

i'm trying to scan documents to pdf files and whichever program i use, i end up with massive files (approx 1mb per page). 

i'm using a HP officejet J4500. i'm scanning in grey (black and white), have fiddled around with all different compressions, have dropped the scan resolution down to 200 (the lowest i can go without it becoming unreadable) and then downgraded the saved file to 70dpi (!) and the file is still 1mb/page. i'm trying to scan a document of 50 pages.

it can't be that this is so hard to figure out, so i'm guessing there's something fundamentally wrong here that i can't see. 

can someone please help me with this. 
thanks!

---

### Post by cbabbage on 2010-01-16
Clarify something for me - is it in fact the resulting .pdf file that is 1MB? What are you saving the scanned file as?

---

### Post by TennSeven on 2010-10-19
I have this same issue.  I will create a 1-page letter in OpenOffice and save it as a PDF with a 67.2KB file size.  I will print the letter, sign it and re-scan it with gscan2pdf at 300dpi; the resulting PDF file saved from gscan2pdf will have a 4MB file size.  Even turning off all of the cleanup filters (which I thought would give me a smaller file, since they default a lot of pixels to black or white instead of gray), my file that was 67KB when I created it is now 1MB after I have scanned it.

I understand that you cannot really compare a scanned image to an OpenOffice-produced PDF, but I used to do a lot of similar scanning on Windows-based systems and ended up with PDFs that were much, much smaller than what I am able to achieve here (final sizes around 60-70KB per page).  Is there some way to further compress these files, or some settings in gscan2pdf that will allow for a much smaller file size?

---

