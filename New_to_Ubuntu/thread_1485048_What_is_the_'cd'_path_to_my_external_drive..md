---
title: "What is the 'cd' path to my external drive."
date: 2010-05-16
forum: New to Ubuntu
---

### Post by brawd on 2010-05-16
Hi all,

I want to copy files from my external drive to a directory on my hard drive.

By a bit of trial and error I now know how to set the path for the directory on the hard drive but I can't figure out the path for the external drive.

To see the external drive I can mouse my way to Places, then Computer and then I can see my external drive which is called DadExt1.

Now I could do a copy and paste using the mouse but that wouldn't let me learn anything more about Ubuntu. I reckon knowing how to move around my computer using paths is going to be fundamental in using Linux, and Ubuntu in particular.

Any advice would be greatly appreciated.

regards

brawd

---

### Post by cherva on 2010-05-16
probably it is ```
 cd /media/DadExt1
```

---

### Post by Ozymandias_117 on 2010-05-16
It's probably in /media/name_of_the_drive so ```
cd /media/DadExt1
```

---

### Post by mc4man on 2010-05-16
The path to  an external drive is typically /media/<volume label>

So in this case /media/DadExt1

---

### Post by oldos2er on 2010-05-16
You can drag and drop a folder from Nautilus into a terminal, and it will show you the path.

---

### Post by Ozymandias_117 on 2010-05-16
> **oldos2er said:**
> You can drag and drop a folder from Nautilus into a terminal, and it will show you the path.

That is awesome! I never knew that lol.

---

### Post by brawd on 2010-05-16
Wow - Thank you everybody.

So to do an all files transfer between my ext drive to hard drive would be:

sudo cp /media/DadExt1/Dad's stuff/fonts/* /usr/share/fonts/myfonts

Do I need a '/' at the end of myfonts in the above path?

The sudo is because root owns the fonts destination file.

regards,

brawd

---

### Post by Excedio on 2010-05-16
```
 
sudo cp /media/DadExt1/Dad's stuff/fonts/* /usr/share/fonts/myfonts

```
 
This wont work.
 
```
 
sudo cp /media/DadExt1/Dad's\ stuff/fonts/* /usr/share/fonts/myfonts

```
 
This will.
 
Note the "Dad's\ stuff"

---

### Post by John Bean on 2010-05-16
> **brawd said:**
> sudo cp /media/DadExt1/Dad's stuff/fonts/* /usr/share/fonts/myfonts

You need to handle the embedded space in "Dad's stuff", and the embedded apostrophe is less than helpful on the command line... :-(

In this case probably the easiest way is to "escape" the space and apostrophe with a backslash, so  "Dad's stuff" becomes "Dad\'s\ stuff".

---

### Post by oldos2er on 2010-05-16
> **brawd said:**
> sudo cp /media/DadExt1/Dad's stuff/fonts/* /usr/share/fonts/myfonts


If there's a space in the folder name, you'll need to either enclose the path in quotes (sudo cp "/media/DadExt1/Dad's stuff/fonts/*") or use a backslash (sudo cp /media/DadExt1/Dad's\ stuff/fonts/*"

I don't think you need a trailing forward slash.

---

### Post by brawd on 2010-05-16
First off I forgot to put in the path after media/DadExt1 and it tried to transfer 120 Gigs to my 80 Gig harddrive.
It didn't complain either. I couldn't stop the command - didn't know how - so I had to press reset.

I thought it might not like that name so I changed it to Dad_stuff and Fonts to newfonts. So put in
sudo cp /media/DadExt1/Dad_stuff/newfonts/* /usr/share/fonts/myfonts and it told me too many parameters.

So I cd'd to the newfonts and tried 

sudo cp * /usr/share/fonts/myfonts and that did it.

A little bit trickier than I thought but straight forward(ish) when it's done. A puzzle about 'too many parameters' but I can play with that and see what my limitations are.

Thank you all for your help.

brawd.

---

