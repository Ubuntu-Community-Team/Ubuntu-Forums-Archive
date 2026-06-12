---
title: "Delete all files but one"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Faudyen on 2009-10-18
Hello,

Hope all is well with everyone

I have a folder named Faud1 - lets say
I want to delete everything in that folder minus one specific file - Faudnoob.txt lets say

So I CD to the Faud1 folder and I type

```
[FONT=monospace]rm -r*
```[/FONT]
[FONT=monospace][/FONT]
and that deletes everything in the folder that I am CD'd into.  Is there a way to make it not delete Faudnoob.txt but delete everything else?

Thanks in advance

---

### Post by coldReactive on 2009-10-18
This thread may help: [http://ubuntuforums.org/showthread.php?t=513195](http://ubuntuforums.org/showthread.php?t=513195)

---

### Post by Faudyen on 2009-10-18
So ```

find ! -regex '.*\.\(tex\)' -exec rm {} \;


```Would delete everything but the .tex files?

Could I change this to ```
 find ! -regex '-*\Faudnoob.txt ' -exec rm {} \;
``` ?

Thank you in advance

---

### Post by ikt on 2009-10-18
could always just move that 1 file into a different location, and then deleting all the files, and then moving it back again.. but that's technically lazy :(

---

### Post by coldReactive on 2009-10-18
> **Faudyen said:**
> So ```

find ! -regex '.*\.\(tex\)' -exec rm {} \;


```Would delete everything but the .tex files?

That would find everything but tex files, then remove everything, including tex files. Or am I being a newbie at arrays?

---

### Post by benj1 on 2009-10-18
im on a bit of an awk binge at the mo so:
```
awk '!/filetokeep/ {system("rm "$0)}'
```

---

### Post by Faudyen on 2009-10-18
> **benj1 said:**
> im on a bit of an awk binge at the mo so:
```
awk '!/filetokeep/ {system("rm "$0)}'
```

That will only delete the files that are in folder I am currently CD'd into correct? It wont like wipe out my system minus one file.

---

### Post by Joeb454 on 2009-10-18
> **ikt said:**
> could always just move that 1 file into a different location, and then deleting all the files, and then moving it back again.. but that's technically lazy :(

Conveniently put together in a string of commands like so: ```
mv Faudnoob.txt ~/ && rm -r ./* && mv ~/Faudnoob.txt ./
```

Simple really :)

---

### Post by benj1 on 2009-10-18
> **Faudyen said:**
> That will only delete the files that are in folder I am currently CD'd into correct? It wont like wipe out my system minus one file.
blonde moment :confused:


```
ls | awk '!/filetokeep/ {system("rm "$0)}'
```

if you want to be really safe 

```
ls | awk '!/filetokeep/ {system("rm /full/path/to/files/"$0)}'
```

then at worst it will come up with an error saying file doesnt exist

the exclamation mark inverts the regex ie '/file/' would match 'file' '!/file/' would match anything but 'file'
you may want to be more specific ie '/file/' will also match 'afile1'
so you may want to specify '/^file$/' which specify the start and end of the word respectively.

you can always check what will be deleted with
```
ls | awk '!/filetokeep/ '
```
will print out what files will be deleted (ie sent to rm)
```
ls | awk '/filetokeep/ '
```
will print out what is kept

---

### Post by stinger30au on 2009-10-18
> **Faudyen said:**
> Hello,

Hope all is well with everyone

I have a folder named Faud1 - lets say
I want to delete everything in that folder minus one specific file - Faudnoob.txt lets say

So I CD to the Faud1 folder and I type

```
[FONT=monospace]rm -r*[/FONT]
```

and that deletes everything in the folder that I am CD'd into.  Is there a way to make it not delete Faudnoob.txt but delete everything else?

Thanks in advance


rather then cd to it navigate to it with nautilus

go edit select all

then hold the control key and click on the file you want to keep

all other files will still be highlighted

now hit delete key on keybaord

works in ubuntu and windows

---

### Post by Faudyen on 2009-10-18
> **Joeb454 said:**
> Conveniently put together in a string of commands like so: ```
mv Faudnoob.txt ~/ && rm -r ./* && mv ~/Faudnoob.txt ./
```Simple really :)
 Thank you Joeb454. I wasn't able to make it work on one command line so I just did
```

mv Faudnoob.txt /Faud2
rm -r *
cd /Faud2
mv Faudnoob.txt /Faud1

```It may be the long way for now but I think in time I will figure out how to shorten it:)

---

### Post by sisco311 on 2009-10-18
```
rm -r !(Faudnoob.txt)
```

```
man bash | less -p "\!\(pattern-list)"
```

---

### Post by longtom on 2009-10-18
> **stinger30au said:**
> rather then cd to it navigate to it with nautilus

go edit select all

then hold the control key and click on the file you want to keep

all other files will still be highlighted

now hit delete key on keybaord

works in ubuntu and windows

Now - were is your sense for adventure...

---

### Post by benj1 on 2009-10-18
i think sisco311 get the prize :)

---

### Post by ghostdog74 on 2009-10-18
> **sisco311 said:**
> ```
rm -r !(Faudnoob.txt)
```

```
man bash | less -p "\!\(pattern-list)"
```

before that, if extglob is not set, then have to set it
```

shopt -s extglob

```

---

### Post by stinger30au on 2009-10-19
> **longtom said:**
> Now - were is your sense for adventure...


lol!!!

i keep forgetting

your not allowed to do it the easy way in linux! :P:P

(running for cover)

lol!

---

