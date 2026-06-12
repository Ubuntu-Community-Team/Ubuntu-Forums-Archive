---
title: "How to batch-convert jpg to gif with command line or GUI?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by kramer65 on 2009-09-02
Hello,

I've got a folder of a couple hundred jpg's which need to be converted to gifs. Does anybody have any idea how to do this in an easy way? Some kind of command line thing, or possibly a graphical thing which can help out?

Thanks in advance!

---

### Post by NoaHall on 2009-09-02
using *.jpg to do it... eg :
```

cd /home/noah
for a in *.JPG;do echo $a && convert $a $a.gif; done

```

note -  it will give .JPG.gif on the end (acts as a .gif)
Will try and fix it for you - got to go now though.

Hope I helped.

---

### Post by kramer65 on 2009-09-02
That already works great!

If you can make it that the .JPG is gone as well that would even be better!  :)

ps. and one more thing. Some of the jpg's are *.jpg and some are *.JPG (some with higher case letters and some with lower..).

---

### Post by Nepherte on 2009-09-02
This should get rid of the jpg etension:
```
#!/bin/bash
IFS="
"
for i in `ls *.jpg`; do
     convert $i ${i%.jpg}.gif
done
```
If the extension ends in JPG rather than jpg, you might want to change the script as everything is case-sensitive.

---

### Post by akiratheoni on 2009-09-02
Imagemagick can do that, too. It can also change the sizes of images and all that good stuff. It can be installed through the repositories. Here's a list of tools that Imagemagick comes with: [http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

---

### Post by kramer65 on 2009-09-02
@ Nepherte
Ok thanks... but when I copy and paste this into a terminal window it doesn't really do anything. Can a terminal thing handle multiple lines at a time..?


NEVERMIND! It works brilliantly!

Heel erg bedankt!

---

### Post by akiratheoni on 2009-09-02
> **kramer65 said:**
> Ok thanks... but when I copy and paste this into a terminal window it doesn't really do anything. Can a terminal thing handle multiple lines at a time..?
If you're talking about the code that Nepherte gave, you'll need to paste what he put into gedit.

Go to the terminal and navigate to the folder with the images that you want to change. Then type:
```
gedit script.sh
```

Gedit will pop up. Paste the code that Nepherte gave you. Then save and close it.

Go back to the command line and type:
```
chmod +x script.sh
```
(this is to make the script executable)

Then type:
```
./script.sh
```
This will run the script.

That should be it.

---

### Post by Nepherte on 2009-09-02
> **kramer65 said:**
> @ Nepherte
Ok thanks... but when I copy and paste this into a terminal window it doesn't really do anything. Can a terminal thing handle multiple lines at a time..?


NEVERMIND! It works brilliantly!

Heel erg bedankt!
Graag gedaan.

---

### Post by Cerin on 2010-08-17
> **Nepherte said:**
> This should get rid of the jpg etension:
```
#!/bin/bash
IFS="
"
for i in `ls *.jpg`; do
     convert $i ${i%.jpg}.gif
done
```
If the extension ends in JPG rather than jpg, you might want to change the script as everything is case-sensitive.

This doesn't work if the filename contains spaces. And yes, it's legal and common nowadays for filenames to contain spaces. We programmers need to accept this.

Otherwise, your solution is good, and an improvement would be:

```
for i in *.jpg; do convert "$i" "${i%.jpg}.gif"; done
```

---

### Post by DaithiF on 2010-08-17
@Cerin, just curious - why reply on a year-old thread?

in any case the original post mentioned a mix of jpg, JPG extensions, to do a case insensitive match for these:

```
#!/bin/bash
shopt -s nocaseglob
for i in *.jpg
do
  convert "$i" "${i%.*}.gif" 
done

```

---

### Post by Cerin on 2010-08-17
Is the age of the post relevant?

I had a problem matching the OP's problem, which the posted solutions didn't solve. I thought someone else who has a similar problem and stumbles across this page during a Google search would appreciate a slightly better answer.

---

### Post by verdomde on 2011-05-21
> **Cerin said:**
> Is the age of the post relevant?



just to back ye up. a year further on and i'm appreciating the additional advice :)

---

### Post by tonytraductor on 2011-12-28
One could just include

rename 's/.JPG/.jpg/g' *

before the convert line.

This would change all .JPG extensions to .jpg

---

