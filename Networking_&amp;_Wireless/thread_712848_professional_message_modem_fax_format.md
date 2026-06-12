---
title: "professional message modem fax format"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by alenis on 2008-03-02
I have  an US Robotics Professional Message Modem, a rather old piece of hardware which nonetheless still works great and it is very useful in my small office: it can store incoming faxes in memory, letting you choose what you want actually printed on paper, and works as an answering machine too.
In windows you can read the memory of the modem and download faxes and voice messages with an utility called "Winphone". Unfortunately, it doesn't work with Wine. There are two small utilities desgined for linux:
a) KMSGmodem: when it works, it works fine. however, it often crashes and doesnt read the modem memory right;
b) tkusr: it never crashes and read the modem memory properly; however, fax downloaded with this utility are not readable. The attached picture shows the fax as it should be and the same fax as displayed by tkusr

[IMG]http://www.euridea.com/grafici/Immagine.jpg[/IMG]

Both tkusr and kmsgmodem seem no longer maintained by their authors, so I wonder if , looking at the picture, someone can help me identify the problem and suggest possibile solutions.

---

### Post by jeffus_il on 2008-03-02
Never used this software but it looks like a resolution problem. Can you adjust the resolution that tkusr displays the fax at? Can you download the fax from your modem and use a regular fax viewer like evince?

---

### Post by alenis on 2008-03-02
tkusr dispalys faxes at normal width or "width/2". The latter actually reduces the width but there are no improvements: the text is still not readable.
tkusr can also save faxes in g3 format. I tried to open them with KFaxView, but I got a reply " cannot open file ..." with the following detailed explanation: "This is not a TIFF FAX file"
KFax opens the file but the result is even more unreadable.
Eye of Gnome, F-Spot, gThumb refuse to open the file.
Imagemagick (display) says "unexpected end-of-file" and then displays the same unreadable text as Kfax...

---

### Post by alenis on 2008-03-02
I forgot to mention that evince doesn't work either: "impossible to open..."

---

### Post by jeffus_il on 2008-03-02
How about trying ImageMagick's```
 identify
``` to see what it understands the format of the file to be?

---

### Post by alenis on 2008-03-02
here it is 
```
alenis@alenis-desktop:~$ identify fax10.g3
fax10.g3 G3 2592x3505 PseudoClass 2c 86kb 
identify: Unexpected end-of-file `fax10.g3': Nessun file o directory.
alenis@alenis-desktop:~$ 

```

the unexpected end-of-file is bad, isn't it?

---

### Post by jeffus_il on 2008-03-02
I think it is bad, I believe ImageMagick is one of the better image handling tools, don't give up yet, did you try and open the file with the gimp? what is the file size?

---

### Post by alenis on 2008-03-02
The Gimp displays just a different kind of garbage. File size is 86,4 kB (88423 byte)

---

### Post by jeffus_il on 2008-03-02
This link to the tkusr site has a link to contact the developer, how about asking him if there is a solution to your problem.
[http://freshmeat.net/projects/tkusr/](http://freshmeat.net/projects/tkusr/)

---

