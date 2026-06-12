---
title: "PDF to JPEGs"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by ozbolt on 2009-02-14
Imageshack as much as I played with it doesn't have feature to export multiple pictures. So is there a way to convert PDF with 100 pages to 100 jpegs or pngs or whatever the format may be?

Thanks for help.

---

### Post by Temposs on 2009-02-14
The package called poppler-utils, which you can find in Synaptic, has a utility script called pdfimages, which will allow you to output a pdf into images.

---

### Post by Joleen on 2011-05-28
Goodmorning..
i am on ubuntu 11.04. I am having trouble using pdfimages...
Actually I have installed xpdf reader, (by the way, it does nothing when I command it to open a file), xdpf utils AND poppler utils. Then I am trying to convert an image inside a pdf to jpeg or whatever image format, using the terminal.
I have tried these commands:
maria@petit:~$ pdfimages pogrom_a3.pdf /tmp/image
Error: Couldn't open file 'pogrom_a3.pdf': No such file or directory.

maria@petit:~$ pdfimages /path/to/pogrom_a3.pdf /path/to/output/dir
Error: Couldn't open file '/path/to/pogrom_a3.pdf': No such file or directory.


maria@petit:~$ pdfimages pogrom_a3.pdf ./pogrom_a3image
Error: Couldn't open file 'pogrom_a3.pdf': No such file or directory.


maria@petit:~$ pdfimages la.pdf foo
Error: Couldn't open file 'la.pdf': No such file or directory.


As you can see, it cannot locate the files. What is wrong?
Note that evince function of just drugging the images to one's desktop is not working for me. I did it and the image is blacK. Can't I convert an image without downloading acrobate reader? and WHY xpdf does nothing?:(

---

### Post by grahammechanical on 2011-05-28
Hi Joleen. Good evening.

Where is the file pogrom_a3.pdf stored? The first command that you are using would require it to be in the same directory or folder as the program pdfimages. I think that I am correct. I am unfamiliar with this program. I think that it would be simpler if the images were in the same folder as the program.

As for the second command it is my guess that the terminal is seeing the path to the file as part of the file name. You could try this ./path/to/pogrom_a3.pdf. But I am not familiar with the codes used to identify paths in the Linux command line interface.

Regards.

---

### Post by AlphaLexman on 2011-05-28
> **Joleen said:**
> maria@petit:~$ pdfimages /path/to/pogrom_a3.pdf /path/to/output/dir
Error: Couldn't open file '/path/to/pogrom_a3.pdf': No such file or directory.
The second parameter should be a basename (without a path (I think)) so that you will get pics with 'basename-nnn.xxx' where 'nnn' is the picture number, and 'xxx' is the filetype extension.

Try it like this:
```
pdfimages pogrom_a3.pdf pogrom_a3images
```

---

### Post by Joleen on 2011-06-29
Thank you for your reponses, Grahammechanical and Alphalexman
I have not tried your suggestions yet, as I uninstalled xpdf because I was mad at it and now synaptic, software center and installations from terminal are not working. :lolflag:As soon as I fix these, I'll reinstall xpdf and give you a feedback.
Thanks again!
 > **AlphaLexman said:**
> The second parameter should be a basename (without a path (I think)) so that you will get pics with 'basename-nnn.xxx' where 'nnn' is the picture number, and 'xxx' is the filetype extension.

Try it like this:
```
pdfimages pogrom_a3.pdf pogrom_a3images
```

---

