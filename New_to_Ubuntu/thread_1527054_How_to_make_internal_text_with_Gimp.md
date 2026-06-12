---
title: "How to make internal text with Gimp?"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-08
It's a nice type of text written on other image or paper, i wonder how to do it with Gimp 
if some one knows please tell how, there attached image

---

### Post by gzarkadas on 2010-07-10
Your image is small and I can't see very clear what is the effect that you want to achieve, but if it is a bottom white line on each letter, as if the text is carved, then you can do it as follows:

1. Create your text with the desired size and color.
2. Make a copy of the text as another layer
3. Change text color of the copy to white (or a lighter version of the original color). You can use the fill tool and click each letter for this.
4. Raise the layer of the original text to be above (in z-order) from the white text.
5. Place the two texts one on top of the other with a small replacement (equal to the width of the line, usually 1-3 pixels).

The same procedure can be done with 3 or more layers of text to achieve more complex effects (for example add a black layer to show shadows as well, see attached image).

[IMG]http://ubuntuforums.org/picture.php?pictureid=6506&albumid=1938&dl=1278744202&thumb=1[/IMG]
 
If the text created that way is jaggy you can slightly blur it afterwards to better blend the colors.

You can also try the ready-made logos created by selecting an item from the menu `File|Create|Logos' and customize the resulting image. There are some nice effects there.

---

