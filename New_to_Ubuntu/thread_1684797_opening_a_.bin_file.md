---
title: "opening a .bin file"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2011-02-09
Hi,
First let me say I'm not to clever with computers, though I'm being forced to learn as I go on. Someone sent me what was supposed to be a simple text document, but it appeared as a .bin file in the email. I downloaded it, opened it and discovered three folders and a file. I unzipped them and they appeared on my desktop. I couldn't find anything I recognised by the name of the original file, but under 'word' I found 'document.xml
I couldn't open it so searched the net for an answer, but nothing worked. I finally opened it in 'Konqueror' and now have 2000+ words, completely unformatted and in one sentence.
Any advice on how to open it with its original format would be appreciated.
Thanks

---

### Post by ivanovnegro on 2011-02-09
Is this not a text file, I mean you could open it with OpenOffice?

---

### Post by Dermot Doyle on 2011-02-09
In open office it comes out unreadable with the text surrounded by symbols and commands, worse than the Konqueror one line.

---

### Post by Mark Phelps on 2011-02-09
Your PC ... your choice ... but personally, I would not open a "bin" file.  That's a form of executable and could contain nearly anything.

Have them resend it as a text or document file.

---

### Post by oldos2er on 2011-02-09
I would ask the person who sent it to you what program they created it with.

---

### Post by Dermot Doyle on 2011-02-09
Thanks for the advice. I already did ask him to resend it as some sort of text document, I was just wondering if there was a way round it. I have also already sent it on to a few other people. I was just assuming it was some sort of pc thing that I alone couln't read - I think I'm the only one in the group using Linux.

---

### Post by ivanovnegro on 2011-02-09
Im not sure what a type of .bin file is that what you have but normally .bin files are binary files, and yes you need a program to open it, what is it exactly? 
The friend that sent you this file, did he said for what it was?

---

### Post by Dermot Doyle on 2011-02-09
It should be simply text, nothing else. I am in a writing group and this is one of the pieces I have to send round to the rest of the group.

---

### Post by apmcd47 on 2011-02-09
If you were able to unzip this file, what are the names of the files inside? MS Office and OOo both use zipped XML files nowadays, but the files inside will be different. It sounds to me as thought the correct extension (.docx?) was replaced by this .bin extension somewhere during the mail transfer. If you were able to put the correct extension back OOo may be able to open it properly.

Unless you are expected to edit the document it should be sent as a PDF anyway.

Andrew

---

### Post by cgroza on 2011-02-09
As far as I know, bin files are used to install software. Just make it executable from the proprieties menu and open a  terminal, cd to the folder, and run ./bin_file_here.

---

### Post by Dermot Doyle on 2011-02-09
One folder called -rels including a file called .rels
One folder called docProps including app.xml, core.xml and thumbnail.jpeg (this seems to be a tiny photo of a formatted first page, but unreadably fuzzy if I try to enlarge it).
One folder called word including two folders: 
-rels including a file document.xml.rels
theme including a file theme1.xml
then 6 files:
document.xml
fontTable.xml
numbering.xml
settings.xml
styles.xml
WebSettings.xml

Does that make any sense?

---

### Post by 3rdalbum on 2011-02-09
It's a Microsoft Office document, using the latest OOXML format. I believe recent versions of Openoffice.org (and Libreoffice) can read this format; however the file needs to be intact and have a "docx" extension.

So, go back to your e-mail and save off the attachment again. Make sure the name ends in ".docx"; if it doesn't, then rename it. Start up Openoffice and use the Open function to open the file.

Final step: Tell the person who sent it to you NOT to use that format again; advise them to change the format in the Save dialog to "RTF" or even "Microsoft Word 2001". Otherwise they'll inconvenience a lot of people who don't have the latest MS Office.

---

### Post by Dermot Doyle on 2011-02-10
Hi,
When I download the attachment it is a zipped folder called Revised 48 hours 1. It does not end in .anything. Inside is a list of things as listed in my previous message. The actual document appears to be called document.xml but I can't rename this to finish with .docx, only the first word 'document'. 
Can you explain a little more clearly what I should be renaming and how? Thanks
By the way I am using 10.04. Should my version of OpenOffice be new enough?

---

### Post by apmcd47 on 2011-02-10
Try renaming the "Revised 48 hours 1" zip archive to have a .docx extension and see if your OOo/LibreOffice word processor can read it.

I'm guessing the originator of the file renamed it to get it through his/her email virus scanner.

Andrew

---

### Post by Dermot Doyle on 2011-02-10
Thanks everyone. apmcd47 you were right. as soon as I added .docx to the title of the folder it turned into a word document before I even tried to open it.
What a brilliant resource this forum is.

---

