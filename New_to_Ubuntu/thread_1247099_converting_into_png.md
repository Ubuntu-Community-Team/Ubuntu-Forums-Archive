---
title: "converting into png"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-08-22
how do I convert all the picture files in a said folder entirely to png from command line?

---

### Post by joey-elijah on 2009-08-22
To do it via the command line then do it with a simple

# convert input.jpg output.jpg

This article may help :) 

[http://www.ibm.com/developerworks/linux/library/l-graf/](http://www.ibm.com/developerworks/linux/library/l-graf/)

---

### Post by nhasian on 2009-08-22
actually the command is just

```

convert
```

for more info see

```
man convert
```

---

### Post by LunaticHiatus on 2009-08-22
I'm trying to get used to command line. How do you specify that you want to convert all the files in said folder. I remember in dos it was *.*

---

### Post by nhasian on 2009-08-22
make sure you are in the folder that contains the images you want to convert

then do:

```
convert *.jpg *.png
```

---

### Post by LunaticHiatus on 2009-08-22
ah, alright, thats all I needed to know. Thanks

---

### Post by Penguin Guy on 2009-08-22
> **nhasian said:**
> make sure you are in the folder that contains the images you want to convert

then do:

```
convert *.jpg *.png
```
That will only convert all the .jpgs to .pngs, not (as he asked for) all pictures. Also, I don't think wildcards work in the output.
It would be better to write a short script for it:

```
#!/bin/sh
FOLDER="$1"
TO=".png"

OLD_IFS="$IFS"
IFS='
'
for pic in `find $FOLDER -type f`
do
	echo "Converting '$pic' to $TO."
	convert $pic $pic$TO
done
IFS="$OLD_IFS"

exit 0
```

Copy and paste into a text editor, then save. Navigate to the directory with the script in and type [COLOR="Green"]chmod +x <Script Name>[/COLOR] to make it executable. And finally run it by typing [COLOR="Green"]./<Script Name> "</path/to/picture/folder>"[/COLOR].

---

### Post by LunaticHiatus on 2009-08-22
many thanks penguin guy. Yeah, Convert didn't work quite in the manner I liked. Thanks for the script.

---

### Post by BackwardsDown on 2009-08-22
Or just open it in the gimp and select file->save as.

I think its almost just as fast as digging the file up in the commandline.

---

### Post by lavinog on 2009-08-22
> **BackwardsDown said:**
> Or just open it in the gimp and select file->save as.

I think its almost just as fast as digging the file up in the commandline.

The op wants to convert all the pics though.
The convert script can do this much quicker than manually converting each one.

---

