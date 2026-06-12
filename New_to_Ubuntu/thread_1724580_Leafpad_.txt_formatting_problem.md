---
title: "Leafpad *.txt formatting problem"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by wheel_walker on 2011-04-08
I'm using Leafpad now, but I encountered the same problem with Gedit.  It's easier to show than tell.

[http://www.verve-fanworks.com/SMF/index.php?topic=409.0](http://www.verve-fanworks.com/SMF/index.php?topic=409.0)
^This is an item guide I'm working on for SaGa Frontier.

When I open it with leafpad on my laptop, it looks like this:
[http://www.verve-fanworks.com/SMF/index ... attach=483]("http://www.verve-fanworks.com/SMF/index.php?action=dlattach;topic=333.0;attach=483")

But after I upload it to a forum and then download it to check that it worked, it looks like this:
[http://www.verve-fanworks.com/SMF/index ... attach=485]("http://www.verve-fanworks.com/SMF/index.php?action=dlattach;topic=333.0;attach=485")

It's like it doubled every press of the Return key.

I haven't tried escaping the carriage returns, because I really don't know what that is, and a google search is inconclusive.

---

### Post by earthpigg on 2011-04-08
it opens with double-return-key shenanegans no matter what i use to open it.

-leafpad
-gedit
-cat
-firefox
-nano

it may be that forum itself doing something wonky - "helping" you by adding Windows carriage returns to the existing unix carriage returns or similar. 

suggestions:
-try e-mailing the original file to yourself and opening it from there. 
-upload it to this forum as an attachment, see if it is wonky there.
-remove the .txt from the end of the file, so the forum doesn't try to 'help' you format it when you upload.


if you don't want to actually solve the problem and just want to share your work - an alternative method you could use would be not to use a text file at all, and instead use something like [pastebin]("http://pastebin.com/"). (registration not required)

---

### Post by wheel_walker on 2011-04-08
Could I save it using another type of character encoding, perhaps  windows encoding, and avoid this problem with all future uploads?

It's currently saved as:
UTF-8 CR+LF

---

### Post by CharlesA on 2011-04-08
Looks fine to me (on a windows box, at least)

Haven't had a chance to check it on a linux box.

---

### Post by rudihawk on 2011-04-08
Looks fine to me too :) 

Ubuntu 10.04 - gEdit.

---

### Post by wheel_walker on 2011-04-08
Above posters, could you specify which upload looked fine?  This forum or Verve Fanworks?

---

### Post by rudihawk on 2011-04-08
> **wheel_walker said:**
> Above posters, could you specify which upload looked fine?  This forum or Verve Fanworks?

I used the forum one. 

The attachment from [this]("http://ubuntuforums.org/showpost.php?p=10653824&postcount=3") post.

Hope this helps :)

---

### Post by earthpigg on 2011-04-08
> **wheel_walker said:**
> Above posters, could you specify which upload looked fine?  This forum or Verve Fanworks?

this forum. meaning, the other forum is putting it's sticky fingers in your file when you upload it there. regardless of if we find a solution to this problem or not, i would let the forum admins over there know what is up. point them to this thread.

edit - here, i put it on pastebin for you: [http://pastebin.com/WhPtdxMm](http://pastebin.com/WhPtdxMm)

edit2 - ya, try saving it as ASCII.

---

### Post by wheel_walker on 2011-04-08
> **earthpigg said:**
> this forum. meaning, the other forum is putting it's sticky fingers in your file when you upload it there. regardless of if we find a solution to this problem or not, i would let the forum admins over there know what is up. point them to this thread.
Will do.

> edit2 - ya, try saving it as ASCII.
I don't think I have that option, but I won't disallow it until someone else with more expertise tries it.
ISO - 8859 - 1
ISO - 8859 - 15
CP1252
Other codeset... (Opens a text box where I can manually type the codeset)

And

LF
CR + LF
CR

---

### Post by earthpigg on 2011-04-08
> **wheel_walker said:**
> 
And

LF
CR + LF
CR

play with those options, while leaving the default UTF-8 in place. that is the carriage return setting.

i don't think anyone else here is registered on that other forum, so we can't test it for you. try all 3, see what works, file it away for future reference, and be sure to share that knowledge over at the other forum if you see anyone else have similar issues. :)

edit: i think i have foggy recollection of folks programming for windows on unix/linux machines having problems similar to yours. i want to say there is some big and unnecessarily dramatic 20-30 year old debate between Microsoft and The World that hasn't finished playing out yet, but don't quote me on that.

---

### Post by rudihawk on 2011-04-08
> **earthpigg said:**
> )

edit: i think i have foggy recollection of folks programming for windows on unix/linux machines having problems similar to yours. i want to say there is some big and unnecessarily dramatic 20-30 year old debate between Microsoft and The World that hasn't finished playing out yet, but don't quote me on that.

That sounds interesting! 

*Goes to find out more*

---

### Post by earthpigg on 2011-04-08
let me know if my foggy recollection was correct :)

---

