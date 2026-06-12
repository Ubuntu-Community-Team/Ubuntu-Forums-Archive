---
title: "Urgent help : image editing Ubuntu"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by konsolelover on 2011-07-25
hello everyone, i have to upload a signature image(in jpeg format) to fill a recruitment form which says file-size must be of between 10-20 kb......i have scanned image which is of 9.5 kb.....tried to edit in shotwell photo manager....tried some random things in Adjust and crop menu but my little changes didn't work, it always shortened the file size......as i don't know anything about Image editing can someone tell me how can i increase the file size (>=10kb)
i also tried gnome-screenshot to take the screenshot of the image, but it also saved the new image smaller than 10kb....
can any other image editor can help....
Please help TIA

---

### Post by Snowboi on 2011-07-25
You can increase the quality or the size of the image...

---

### Post by konsolelover on 2011-07-25
tried to increase to quality but it didn't work....when i click save as option in Shotwell it gave me dialog box...i selected maximum quality 100% ,but it didn't work , should i try to increase the no of pixel....plz guide

---

### Post by Wim Sturkenboom on 2011-07-25
Open your image in the gimp

Menu *image -> scale image* and make values for the width and height bigger.
Menu *file -> save as* and save as jpeg. A new popup will show, set quality to 100% and select *best quality* under subsampling.

You might not gain much because it is compressed, but it might be enough to get to 10kB

PS
just tested it with a 8.1 kB piece of text (640x400); scaled 5 times (from 3200x2000) and the size is now 107kB, so you might gain more than I expected.

---

### Post by konsolelover on 2011-07-25
> **Wim Sturkenboom said:**
> Open your image in the gimp

Menu *image -> scale image* and make values for the width and height bigger.
Menu *file -> save as* and save as jpeg. A new popup will show, set quality to 100% and select *best quality* under subsampling.

You might not gain much because it is compressed, but it might be enough to get to 10kB

PS
just tested it with a 8.1 kB piece of text (640x400); scaled 5 times (from 3200x2000) and the size is now 107kB, so you might gain more than I expected.
installing gimp

---

### Post by konsolelover on 2011-07-25
thank you all 4 ur replies,
imagemagick did wonder 4 me :D

---

