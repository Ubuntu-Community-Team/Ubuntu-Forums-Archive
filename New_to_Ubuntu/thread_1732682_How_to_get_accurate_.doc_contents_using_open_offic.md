---
title: "How to get accurate .doc contents using open office"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by unloki9 on 2011-04-18
Hi im using Ubuntu 10.04 os in my laptop, and I'm always having problems with my open office word. People in my place use Microsoft word, my problem is how can I get accurate .doc contents using open office word? sometimes when I open .doc files in my open office indention and spacing would differ in my open office and MS word. Please help thanks.

P.S. Do I need to update my open office? I don't know how to see my installed Open office version:(

---

### Post by squenson on 2011-04-18
Sorry, you'll never get *exact* representation of Word documents in OOo. It will be very similar and in rare cases totally screwed up as some features of Word are not in Writer (and vice versa, by the way).

Using the latest version, 3.3.0, may minimize the differences but will in no way totally eliminate them.

---

### Post by sydbat on 2011-04-18
> **unloki9 said:**
> How to get accurate .doc contents using open officeYou don't. 

While there are published "standards" for MS Office compatibility, not all of them have been implemented in Open Office due to various programming issues. Of those that have been incorporated, some do not work in the same way as they would in MS Office.

---

### Post by crispy_420 on 2011-04-18
I've always had the same issue with documents and school, the formatting is just off for some reason. Do you coworkers just need to view the documents or do they have to edit? If it is just view, try exporting as a PDF. I know that is not a true solution but it has been a work around for me.

---

### Post by The Cog on 2011-04-18
You might get better compatibility using the latest LibreOffice, but perfect compatibility will probably not happen. Even MS Word isn't perfectly compatible. I believe that the same version of Word on 2 dfferent computers can render differently depending on which version of Windows or even which type of printer it has. So Word compatibility is something that can't even be perfectly defined or tested.

---

### Post by unloki9 on 2011-04-19
> **crispy_420 said:**
> I've always had the same issue with documents and school, the formatting is just off for some reason. Do you coworkers just need to view the documents or do they have to edit? If it is just view, try exporting as a PDF. I know that is not a true solution but it has been a work around for me.

we need to view, edit and print the file.. is it ok to convert it into pdf? 


Thanks for the replies guys.. any tips on how to upgrade my open office version? and to see the current installed version?

---

### Post by Anuovis on 2011-04-19
Not sure about the editing of pdf files but it is a bit more complicated than doc or other formats. Unless the new Ms Word supports such a function (and I don't think it does), you'll need to either copy the contents to a doc file first or use some pdf editing software. Neither of these is really a good way to accomplish this.

Unfortunately, there is not much to be done. You might try creating text documents with really simple formatting, the more complicated it gets the more likelihood that the file won't be read correctly by another application.

If it's really important to share doc files, I'd recommend running Ms Office through Wine. Or if you could both switch to Open Office. Using the same word processors could save a lot of headache.

Also, an easy way to check your Open Office version through graphical interface is launch any app and then go to Help -> About. It should show the version there. Ubuntu updates your software automatically and the newer version is not always the best (new bugs might creep in and such). Besides, it's unlikely that you can solve your problem that way.

---

### Post by migs73 on 2011-04-19
If the other users are using Office 2010 I believe it supports .ODF files, the native format for OOo. Being an open format I would think the rendering would be more consistent, but I have not tried it yet.

Mike :)

---

### Post by SeijiSensei on 2011-04-19
> **The Cog said:**
> or even which type of printer it has

I know that Word versions at least through 2003 would adjust a document's layout depending on the default printer driver that was installed on the computer.  I don't know if that's still true in more recent versions.  That always seemed a very strange design decision to me since, in networked office environments, the author may not know which printer will be used to generate a particular copy.  I might print drafts to a small desktop printer attached to my computer but print final copies to a large shared device.  Seems weird to have to worry whether what looked good in the draft might not appear identically on the networked printer.

---

