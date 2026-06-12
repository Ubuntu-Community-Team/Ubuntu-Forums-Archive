---
title: "Photorec recovered .jpgs as .pngs"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by amarumayo on 2009-08-20
Hi all,

I recently used photorec to recover jpgs lost on a hard drive that did not unmount properly.  Only problem is now they are all .png files and very poor quality (like icon size)
any ideas what may have happened or how I can recover the jpgs?

Thanks,
Chris

---

### Post by mcduck on 2009-08-20
that sounds like the images you recovered are not your actual image files, but only the thumbnails the file manager has automatically created when you have been browsing your image directories..

---

### Post by amarumayo on 2009-08-20
Yeah that is what I was thinking.  I cannot figure out how to recover the actual images.
Chris

---

### Post by bodhi.zazen on 2009-08-20
You have to manually examine the files you recover.

---

### Post by amarumayo on 2009-08-20
Could you please elaborate.  I am not very linux competent and I don't understand how to recover the jpgs.  Photorec just keeps recovering thumbnails.
Thanks
Chris

---

### Post by bodhi.zazen on 2009-08-20
Well, it sounds as mcduck indicated, you are not recovering the actual images.

This is an issue with Photrec , and if Photorec is not recovering the pictures they may be gone or you may need professional assistance.

The second issue, when you recover a file , it may not be called "your_photo.jpg"

It may be called "file_000" (I am not sure). The file itself may be corrupt. 

So you need to manually open and review each file, text with a text editor, and pictures with a picture viewer. You can then fix or save the file with a new name.

---

### Post by amarumayo on 2009-08-20
Thanks for all your help everyone.  

Just to clarify though, will all .jpgs still be restored with a .jpg extension?  I have a million txt files and I have no idea what they are

Thanks,
Chris

---

### Post by earthpigg on 2009-08-20
in a perfect world, they would be recovered as .jpg files. the world is imperfect, as is photorec. try renaming them to .jpg, see what happens.

further food for thought: i have found that using photorec from their website worked perfectly in one case where the not-so-up-to-date version in the repos failed.

---

### Post by bodhi.zazen on 2009-08-20
> **earthpigg said:**
> in a perfect world, they would be recovered as .jpg files. The world is imperfect, as is photorec. Try renaming them to .jpg, see what happens.

Further food for thought: I have found that using photorec from their website worked perfectly in one case where the not-so-up-to-date version in the repos failed.

+1

---

### Post by rbc on 2009-08-20
You could try foremost. It is in the repos also, although I have always had very good results with photorec and found it much easier to use. bodhi.zazen and earthpigg, correct me if I'm wrong, but I believe photorec and foremost are simply datacarvers. What I mean by that is this, if you open a .jpg file with a hex editor, you will notice that .jpgs begin with hex code DD F8 and end with DD F9, so photorec looks for those, and then carves the file out. .png files start with 89 50 and end with 60 82. Again, if my understanding is correct, photorec is not finding a .jpg and renaming it .png. Is photorec not finding any .jpg files or just not the ones you are interested in?

---

### Post by bodhi.zazen on 2009-08-21
I have not looked at that algorithms in photorec but basically yes, it looks for start and stop of potential files and tries to guess as to what they are. The algorithms are not perfect and, again last time I looked, you need to examine each file you recover. Then names and identification can be off.

Now if the name and file type is on, then you still need to make sure that the data within the file is intact.

Of course you should be working on an image and not the hard drive itself.

---

