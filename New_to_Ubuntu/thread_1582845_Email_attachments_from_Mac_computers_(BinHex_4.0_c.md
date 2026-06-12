---
title: "Email attachments from Mac computers (BinHex 4.0 converter)"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by cheflo on 2010-09-27
Greetings,

Yesterday, I received an email attachment (a .doc file) from my professor in school. I tried to open it both in OpenOffice and in Google Documents (which redirected me to the pure HTML form of the document), but both just showed a mess of explanation marks and other symbols and the text "(This file must be converted with BinHex 4.0)" on top.

After some extensive googling I have understood that this document was send from a mac computer, which encrypts email attachments in a way that other operating systems can't handle (I have, however, managed to open email attachments from mac users before so I guess this is a setting somewhere in OS X). In order for me to read this document, I need to convert i back to its original encryption level and in order to do that I need a BinHex 4.0 converter. Problem: I can't find any for Ubuntu/Mint.

I found something called "Stuffit" for Windows users, but couldn't find a deb package for it. I tried downloading "Foundu", but when I typed "fondu [file name]" it prompted that I had the wrong type of file so I figured fondu is aimed towards the actual conversion of mac fonts to make them usable in Ubuntu/Mint and not the conversion of entire documents (maybe I just need to download the correct fonts and then I can read all documents, but how do I know which fonts that is?). I even installed some Debian libraries (libc5 & related) in order to try out "Mcvert", another command line tool which converts my files to something and puts them in the directory ".//", which I can't even browse to in Nautilus, but have to use the command line to open. Mcvert actually converts the file, but the output is not more readable than the original. I also tried a tool from the software manager called "libconvert-binhex-perl", but I don't know how to use that.

So, know I'm asking for HELP. If there is a simple, straight forward way (or any way at all) of reading this email attachment on my Mint 9 (Ubuntu 10.04) machine, would you be so kind and share it with me?


Regards,

Joel

---

### Post by jtarin on 2010-09-27
Ask your professor to resend in a cross-platform format.

[There's this.]("http://www.webutils.pl/BinHex")

---

### Post by cheflo on 2010-09-27
I would rather find a permanent solution to the problem than having to ask the sender to resend or borrowing a Mac computer when it reoccurs.

---

### Post by jtarin on 2010-09-27
[Here's a link to a download of Stuffit for Linux]("http://web.archive.org/web/20060205025441/http://www.stuffit.com/downloads/files/stuffit520.611linux-i386.tar.gz").....your on your own.

---

### Post by jtarin on 2010-09-27
> **cheflo said:**
> I would rather find a permanent solution to the problem than having to ask the sender to resend or borrowing a Mac computer when it reoccurs.I would think the sender would appreciate the fact that you told him that the world is not 100% Mac yet.:P

---

### Post by cheflo on 2010-09-27
Oh sry, I missed your "There's this"-link. I actually tried that website yesterday though, but then I just copied the text from the opened email attachment to the text box. Now I actually submitted the file and what do you know,** IT WORKS!!**

At the same time as I'm a bit annoyed that I could have saved two hours trying this yesterday I'm grateful that you got me to take a second look at the site.

As for Stuffit, I found a link to the tarball yesterday, but I'm not great at compiling so I rather don't mess to much with that on this computer, which I aim to keep as clean as possible (already annoyed that I installed those Debian packages).

Also, I have told my professor I can't read his documents, but as I said before, I would rather not depend on asking the sender to resend the document, especially not if it's urgent. If a person chooses to send it as such a stupid format from the beginning, I would guess he/she is not tech-savvy enough to know how to change it or just doesn't care enough to make sure it's accessible to everyone.

I hope that website is never taken down from the web or that the converter is made available for download somehow. Anyways, thank you for making me rediscover the website!

---

### Post by jtarin on 2010-09-27
email address of webmaster at the decoding [email]site.webutils@webutils.pl[/email]
Maybe he would be willing to share the script for offline work. Doesn't hurt to ask.

---

