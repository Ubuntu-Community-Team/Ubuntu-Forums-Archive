---
title: "plz help want to clean a dir up in terminal"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by nexxis82 on 2010-08-27
Hello, iam super noob., just starting to learn the terminal, and i was wondering:

 I have a directory full of sub directories of ebooks, i was wondering if there was an easy way in the terminal to delete all the files in the sub directories that are not .pdf

thank you for your help in advance :D

---

### Post by LowSky on 2010-08-27
um... take a look at this, 
[http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/](http://www.cyberciti.biz/faq/linux-unix-how-to-find-and-remove-files/)

if these extra files all share similar extensions, like .jpg for example, you can use the *.jpg to remove those jpegs, while using the commands shown in the link


Just as an FYI positng the use of the 'rm' command isn't very well liked in this forum so use it at your own risk. You can delete your entire file system if you are not careful.

---

### Post by nexxis82 on 2010-08-27
ah the rm command would be the only way huh.. i wonder if i could jus move em else ware to dispose of them. there are 3 filetypes pdf .lit and .rtf i think is the last one... its just a pain as there are like 100 sub directories full of these files.. 

i agree i dont like the rm command sorta makes me nervous

---

### Post by DaithiF on 2010-08-27
Hi,
you can also use find to match files which do not match a pattern, so to match everything but PDFs you could do:
```
find . -type f -not -iname '*.pdf'

```to move the files rather than delete them, you could do:

```
mkdir junk
find . -type f -not -iname '*.pdf' -exec mv {} junk \;
```

---

### Post by nexxis82 on 2010-08-27
SWEETNESS!! thankyou DaithiF 

sounds good.. and even better it worked :D.. 

I know on my tag thing it says i joined in 2008 but i really dident last long, but i am back since my windows 7 on my new pc was junk i removed it and put ubuntu 10.o4 on here :D now i wanna learn everything properly.

so thank you to LowSky for letting me know of the dangers of the rm command :D

---

