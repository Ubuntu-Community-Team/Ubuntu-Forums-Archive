---
title: "How do you merge 2 avi files together???"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by suomalainen on 2009-01-14
Ubunteros,

Does anyone know how I can merge 2 avi files together?

The long way would be to create an iso image using both files then burn as a DVD then rip as avi but is there a simplier method???

Thanks

---

### Post by mikewhatever on 2009-01-14
Use avidemux from the repositories.

---

### Post by JohnLM_the_Ghost on 2009-01-14
Yeah If both avi files is the same format... with **avidemux** it is fast and easy as pie to attach them together.
Just open 1st one, then append 2nd one to it!

Besides burning to DVD and then ripping would make two recompression phases (making the process lossy)
Attaching with avidemux will be losseless (provided they are the same format)

---

### Post by taurus on 2009-01-14
Or use avimerge from a terminal.

```
sudo apt-get update
sudo apt-get install transcode
avimerge -o new_filename.avi -o first_file.avi second_file.avi
```

---

### Post by sathiskumarmsk on 2009-01-14
use kdenlive..this is a best app for video editing..

---

### Post by binbash on 2009-01-14
I prefer avidemux for this situation

---

### Post by MrWES on 2009-01-14
avimerge and avisplit both work very well.

---

### Post by halitech on 2009-01-14
open a terminal and do
```
cat filename1.avi filename2.avi > outputfile.avi
```

this will work as long as both video files are the smae in bitrate, frame rate, etc.

---

### Post by JohnLM_the_Ghost on 2009-01-14
> **halitech said:**
> open a terminal and do
```
cat filename1.avi filename2.avi > outputfile.avi
```

this will work as long as both video files are the smae in bitrate, frame rate, etc.

Sorry mate! This is not a good suggestion... both AVI files carry their Headers! While the output file may work, it might give off errors.

---

### Post by SushiR on 2009-01-14
+1 for avimerge

---

### Post by halitech on 2009-01-14
> **JohnLM_the_Ghost said:**
> Sorry mate! This is not a good suggestion... both AVI files carry their Headers! While the output file may work, it might give off errors.

never had a problem with using it myself on any of the files I've done but maybe I've gotten lucky.

---

