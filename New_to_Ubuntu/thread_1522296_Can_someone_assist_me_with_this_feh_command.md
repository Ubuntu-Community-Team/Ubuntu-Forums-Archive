---
title: "Can someone assist me with this feh command?"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by ankspo71 on 2010-07-02
Hi, 
This is a command borrowed from "man feh". 
> **feh -rswidth -a 'mv %f ~/images/%n´ /opt/images**
View  all  the  images  in /opt/images and below, sorted by width (smallest first) and move the image to  ~/images/image_name  when enter is pressed.
What I would like to know is, why is the destination directory shown before the source directory? Wouldn't that confuse Ubuntu as much as it does me? ;)

In other words, why isn't it written something like this?
**feh -rswidth -a /opt/images 'mv %f ~/images/%n´**

By the way, I'm not trying to accomplish anything but learn something new about commands tonight. thanks.

---

### Post by marshmallow1304 on 2010-07-02
I'll do my best to explain.  This is the first time I've ever even looked at feh, so my apologies if there are any inaccuracies.


First the command as it should be (you missed a couple capitalizations and the man page has an odd character at the end).

```
feh -rSwidth -A 'mv %f ~/images/%n' /opt/images
```

-rSwidth sorts by width in reverse order (i.e. smallest to largest).
-A specifies that an action should be taken when the Enter key is pressed.
'mv %f ~/images/%n' is the action that is taken wherein:
[INDENT]%f is is the path and filename of the current image.
%n is the filename of the current image.[/INDENT]
/opt/images is the location where feh looks for images.


So, feh opens images in /opt/images in order from smallest width to largest, then performs the action of moving each one from its current path to ~/images/filename.  If there are two images in /opt/images: mudkip.png (128x172) and kitteh.jpg (214x463), feh will do this:

1. Display mudkip.png.
2. User presses Enter.
3. Run command 'mv /opt/images/mudkip.png ~/images/mudkip.png'.
4. Display kitteh.jpg.
5. User presses Enter.
6. Run command `mv /opt/images/kitteh.jpg ~/images/kitteh.jpg'.
7. Exit.


To help understand, remember that the part after -A is an argument, in this case a command run by feh, but not a part of feh itself.  The same command can also be written
```
feh /opt/images -rSwidth -A 'mv %f ~/images/%n'
```
which is quite a bit easier to understand.

---

### Post by ankspo71 on 2010-07-02
Hi,
Ahh I get it now. Thank you so much. I totally missed what -A meant and the command's layout just didn't seem right because of that. I can see -A now in the man page for feh. The capitalization error was because I had a copy paste mishap and I edited the command by hand to realign the post to be readable... a clumsy mistake on my part. 

I was looking through the man page tonight because I used feh to find some 800x600 wallpapers in a folder of 1600x900 wallpapers and it worked like a charm, so I wanted to see what else it could do (other than display images and draw backgrounds). Impressive little program. :)
Thanks

---

