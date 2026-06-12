---
title: "GIMP Script-Fu help (resizing and saving)"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by amount on 2010-12-04
Hello!

I'm not sure if this is the right place to be posting this question (sorry for being a total newb), but I was wondering if anyone could help with a *very* simple script for GIMP. After editing an image, I would like to be able to run a script that will do the following (in order):

1. Save a copy to a folder
2. Resize the image
3. Save a copy of the resized image to a different folder
4. Close the image

Seems simple enough, but without any background in scripting, I've been having a hard time. I've got the resizing part down. Here's what I've come up with:

```
(define (photoblog-resize-horizontal image drawable)
  (let* ((cur-width  (car (gimp-image-width image)))
         (cur-height  (car (gimp-image-height image)))
         (height (/ (* cur-height 800) cur-width))
        )
     
     (gimp-image-scale image 800 height)
  )
)


(script-fu-register "photoblog-resize-horizontal"
  _"Resize Horizontal"
  _"Resizes horizontal images for photoblog."
  "Andre Mount"
  "Andre Mount"
  "December 4, 2010"
  "*"
  SF-IMAGE       "image"          0
  SF-DRAWABLE    "drawable"       0
)

(script-fu-menu-register "photoblog-resize-horizontal"
                         "<Image>/Photoblog")
```

What I can't seem to figure out, however, is how to save copies of the open image. I've tried using "gimp-file-save" like this:

```
(gimp-file-save RUN-NONINTERACTIVE image drawable filename raw-filename)
```

...but I don't know what to use for the filename arguments. (I saw "file-jpeg-save" too, but that looks exceedingly complicated.)

Would anyone care to help? Or at least direct me to a better place to ask my question? Thanks!

---

### Post by AlphaLexman on 2010-12-04
Gimp **can** handle CLI image transformations, but IMO, ImageMagick is better from the command line or from a script.
See:
```
man ImageMagick
```

---

### Post by amount on 2010-12-04
Are you suggesting that I call ImageMagick from a script-fu script? Is that even possible? If so, would anyone care to give me some hints? I'd rather not have to do command-line stuff (the whole idea here is to save time).

A bit more info: I'm currently using Photoshop to do this exact task. It's easy to in Photoshop. I just use the action recorder. I'd much rather use GIMP, however. But it seems like it might be more trouble than it's worth.

Also, does anyone have any opinions about GIMP's resizing quality vs. Photoshop's? I've tried comparing output from both programs and I have to confess that I can't really see any difference.

---

### Post by conradin on 2010-12-05
Heres mine for resizing. pretty simple
if I want it in a sub folder i could change the $file to /subdir/$file

i want to know if you want a new folder every time or to place it in an existing folder?
_640x480 can be changed to whatever you need to help you identify your resized picture 

```

#!/bin/bash
# Use this script to batch resize all images in a folder.
# First open the folder and then use the script.
for file in `ls`
do
name=`echo $file | cut -f1 -d.`
convert -geometry 640x480 -quality 95 $file ${name}_640x480.jpg
done

```

---

### Post by amount on 2010-12-05
Thanks for the reply!

> **conradin said:**
> i want to know if you want a new folder every time or to place it in an existing folder?

I have two folders: one for archiving full-size versions of the processed photos and another for temporarily storing the resized images until I post them on my photoblog.

I think I figured out a script that will work. My problem was that I didn't really know how to deal with the various arguments following "gimp-file-save."

Anyway, here's what I came up with. If anyone can identify any problems with the code, I'd be very interested in hearing them!

```
(define (photoblog-resize-horizontal image drawable)
  (let* ((cur-width  (car (gimp-image-width image)))
         (cur-height  (car (gimp-image-height image)))
         (height (/ (* cur-height 850) cur-width))
         (fullsize-filename (string-append "/home/amount/Desktop/Temp Pictures/Resized for Photoblog/Archive/" (car (gimp-image-get-name image))))
         (resized-filename (string-append "/home/amount/Desktop/Temp Pictures/Resized for Photoblog/" (car (gimp-image-get-name image))))
        )
     (gimp-file-save RUN-NONINTERACTIVE image drawable fullsize-filename fullsize-filename)
     (gimp-image-scale image 850 height)
     (gimp-file-save RUN-NONINTERACTIVE image drawable resized-filename resized-filename)
  )
)


(script-fu-register "photoblog-resize-horizontal"
  _"Resize Horizontal"
  _"Resizes horizontal images for photoblog."
  "Andre Mount"
  "Andre Mount"
  "December 4, 2010"
  "*"
  SF-IMAGE       "image"          0
  SF-DRAWABLE    "drawable"       0
)

(script-fu-menu-register "photoblog-resize-horizontal" "<Image>/Photoblog")
```

---

### Post by Dabil on 2011-04-09
I also have a script-fu question. This is an additional question and has nothing to do with resizing and saving.

I recently accepted a role making "trophies" for an online gaming site  that I belong to as a volunteer. The person that did the job before me  wrote a script to automate this process. But the script was wrote for  gimp 2.2 and doesn't work in the current version. I believe the update  to gimp 2.6 broke the script because of the difference in script-fu from  previous versions. I would like to repair the script to get the trophy  generator script-fu working again but I am new to gimp and don't really  understand the language. 

Now I do have experience programming in C++ and Java so I have an idea  what is going on even if I don't understand the syntax of Gimps  language. 

When I run the script I get (2) errors:

! Error while executing script-fu-pdc-standard-trophy:
 Error: eval: unbound variable: string-upcase

This is the first error and the actual code in the script that I believe is causing it is:

(temp-search (string-append inPrefix (string-upcase inName)))

The problem as I am understanding it is that Gimp does not recognize the  sting function "string-upcase" and so is complaining about a variable  not being declared with the let function. 

So how do I fix this? My understanding of the script is that we want the  text in the variable "inName" to all be in Uppercase. What is the new  syntax or function that I should use to accomplish this? If gimp now  does not have an equivalent function, I can just remember to type that  field as all caps when I enter it in the form. 

Would the syntax for that then be:
(temp-search (string-append inPrefix (inName)))
Doing it this way gives me: Error: illegal function

so then I tried it this way: 

(temp-search (string-append inPrefix inName))
This gives me: Error: Procedure exection of gimp-gimprc-query failed

Now the second error I get reads:

! Gimp Message
Plug-In 'Standard' left image undo in inconsistent state, closing open undo groups

I really have no idea what this message is all about. I am just assuming  that it is caused because the first error crashed the script or did not  complete something that needed to thus causing this message. 

Any help would be greatly appreciated. Thanks!

---

### Post by Wolligog on 2011-04-09
[LEFT]ok, i might have missed the point of your question but surely it's easier to save the image using 'save as' then re-scale the image to the required size and save again in a different folder?  probably just as easy.
[/LEFT]

---

