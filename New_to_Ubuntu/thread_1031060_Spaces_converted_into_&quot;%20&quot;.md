---
title: "Spaces converted into &quot;%20&quot;"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by TheSe7enthSin on 2009-01-05
I am running Ubuntu 8.10

I wanted to know if anyone can help me with this issue. It's probably not an issue with the system, but more of an annoyance I would like to correct.

I have a dialogue box or website asking me to "Browse" for a file, and I have an open folder containing the file. If I were to drag the file from the folder TO the "Browse" box, any spaces in the path will be changed to a %20.

(example: /home/me/pictures/at the beach/image1.jpg will change to /home/me/pictures/at%20the%20beach/image1.jpg)

If I click "Browse" & locate the file(s) I want, the path in the box shows a space.

Anyone know if there is a way I can make it so the spaces wont get changed to a %20?

---

### Post by acreech on 2009-01-05
> **TheSe7enthSin said:**
> 

(example: /home/me/pictures/at the beach/image1.jpg will change to /home/me/pictures/at%20the%20beach/image1.jpg)

If I click "Browse" & locate the file(s) I want, the path in the box shows a space.

Anyone know if there is a way I can make it so the spaces wont get changed to a %20?

Rename your files with underscores instead of spaces. /home/me/pictures/at_the_beach/image1.jpg

Linux does not recognize the spaces. if you name your files in this manner it makes them easier to deal with.

---

### Post by TheSe7enthSin on 2009-01-05
This problem didn't exist for me with 8.04. I used to drag & drop files onto "Browse" boxes (in Gmail attachments) all the time.

---

### Post by Kareeser on 2009-01-05
> **acreech said:**
> Linux does not recognize the spaces.

Linux recognizes spaces just fine. Simply use quotes, or the escape character to use them.

---

### Post by Tony Flury on 2009-01-05
The %20 is the standard enconding used on the internet for spaces within URIs - it is a consquence of you using spaces in the file name. You can't "fix" it, because it is meant to work that way.

---

### Post by TheSe7enthSin on 2009-01-05
Why does it happen within the system as well? It's not just on internet URL's.

If I were to drag a file (with spaces in the name/folder path) onto the "location bar" of another *folder*, the spaces convert to %20.

---

### Post by Tony Flury on 2009-01-05
What file browser are you using when you drag and drop ? That might explain it.

Also : You might not realise that in a web browser all local files have URIs - just like web pages - the only difference is they start with file:// (and not [http://)](http://)) - If you are using a web browser to display local files, then I would expect that the browser will encode all uris in the same way and spaces will be converted to %20.

The fact that under certain cases the encoded name is shown, and sometimes it shows the unencoded one is a bit odd to be honest, and I would not worry about the file names showing %20 instead of spaces - it is still the same file.

---

### Post by TheSe7enthSin on 2009-01-05
> **Tony Flury said:**
> What file browser are you using when you drag and drop ? That might explain it.

I would not worry about the file names showing %20 instead of spaces - it is still the same file.

 I am using Firefox for my internet browser.  I don't mind the names showing up with %20. It's just that when the name is in %20 format, the system does not find it.

---

### Post by stchman on 2009-01-05
20 is ASCII for a space so that is normal.  I always use underscores instead of spaces.

---

