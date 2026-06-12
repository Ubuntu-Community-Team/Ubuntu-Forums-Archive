---
title: "In GIMP Image editor, how to cut an image fr one file and add to another file?"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by swarup on 2011-01-07
I just bought an airplane ticket, and they want me to print the front and back sides of my credit card and fax it to them. So I scanned the front and then back sides of the card into separate scans, and now just need to cut the image of the back of the card onto the file which has the front image, so it will print as one page. I have been playing with GIMP image editor which I've never used before, but can't seem to figure out how to cut the image of the back of the card from the one scan, and past it into the file which has the image of the front of the card. Silly I know! Can someone tell me how to do this?

---

### Post by Tom Collier on 2011-01-07
Both images have to be open in GIMP. Use the selection tool to outline the side of the credit card that you want to move. Copy. Active the other image, then "Paste as Layer".  Flatten. "Save as"...then you should have both sides on a single image.

---

### Post by Kenjitamura on 2011-01-07
If the scan of the front already has enough empty space at the bottom to fit in the back below or to the side of it you just open up both the front and back in gimp then use rectangle select on the image with the backside and select around it.  Go to Edit>Copy, then open up the scan of the front side and hit edit paste.  While it's still a floating selection if you mouse over the pasted back side you can move it down below or to the left/right of the front side to where you want it.  Then over in the layers dialog right click floating selection and anchor it.  If there's not enough space on the scan of the front or back already you'll have to open a new document with large enough dimensions to fit both of them and copy and paste them both into it.

---

### Post by swarup on 2011-01-07
> **Tom Collier said:**
> Both images have to be open in GIMP. Use the selection tool to outline the side of the credit card that you want to move. Copy. Active the other image, then "Paste as Layer".  Flatten. "Save as"...then you should have both sides on a single image.

I did all you suggested here, and got both images onto the same page as you describe, but after I finished what I ended up with was an extremely faded image, sort of greyed out. Don't know why? Perhaps you can tell me what I did wrong.

---

### Post by swarup on 2011-01-07
> **Kenjitamura said:**
> If the scan of the front already has enough empty space at the bottom to fit in the back below or to the side of it you just open up both the front and back in gimp then use rectangle select on the image with the backside and select around it.  Go to Edit>Copy, then open up the scan of the front side and hit edit paste.  While it's still a floating selection if you mouse over the pasted back side you can move it down below or to the left/right of the front side to where you want it.  Then over in the layers dialog right click floating selection and anchor it.  If there's not enough space on the scan of the front or back already you'll have to open a new document with large enough dimensions to fit both of them and copy and paste them both into it.

This worked perfectly! Thank you. :)

---

### Post by NJC on 2011-02-24
> **Tom Collier said:**
> Copy. Active the other image, then "Paste as Layer".  Flatten. "Save as"...then you should have both sides on a single image.
Thanks very much, I was having a similar problem and this helped. And I learned something new. :)

---

