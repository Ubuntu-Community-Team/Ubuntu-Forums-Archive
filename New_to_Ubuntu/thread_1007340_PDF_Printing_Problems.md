---
title: "PDF Printing Problems"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by chansen4 on 2008-12-10
Ubuntu 8.10

I wrote a document using AbiWord and printed it using the print to pdf setting. I then sent the document to someone on a Windows machine and they couldn't see the document. They were able to see the image that was in the document, but none of the text. I then installed cup-pdf and tried it using that method with almost the same result. Except this time the Windows user could see "ff" or "fl" in seemingly random places on the page.

Is there a solution for this? Or and I just not doing something right?

Thanks,
chansen4

---

### Post by albandy on 2008-12-10
Tell him to update to the last acrobat reader version. I've got a similar problem but generating pdf's with jasper reports, upgrading the acrobat reader in the windows machine worked.

---

### Post by chansen4 on 2008-12-10
I was able to reproduce this on a VM of Window XP.
I have the newest AR with the latest upgrades and it is still acting this way. I am using version 9.0.0 and it says there are no updates.

---

### Post by albandy on 2008-12-11
Could you generate a little pdf and upload it here?

---

### Post by chansen4 on 2008-12-11
I seemed to have solved it at least with Abiword. Instead of printing the document using the "print to file" option, I just did a "save as" pdf.

I don't know why they are different, but I am OK with just using "save as".

Thanks for your help.
Chad

---

### Post by halitech on 2008-12-11
I had the same issue where for some reason, some apps don't like printing to pdf but if you save as a pdf they open fine. No idea why the difference

---

