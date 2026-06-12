---
title: "Is there a command to make a ist of all the artists that make up my music collection"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Kedster on 2009-04-10
So what i want to do is make a list of all the artists in my music collection, i want to take the info from id3 tags and take out the duplicates and save it to a file.

Alright, I know its possible, Iv done it before actually. I thought i had a thread that told me how to do this but i can not find it these days and now i thought i would me a new thread. 
ok so all my music is in one folder and all my id3 tags are correct(well enough to do this) if i remember correctly I had to install a terminal program that worked from the command line to read id3 tags and then  used on long command to tell that program to output all the artists and then take out duplicates and then take that output and save ti to a .txt file.

I don't remember much else, i thought i started the thread but i cant find it in my treads so it must be someone elses that i read it from

---

### Post by lfaraone on 2009-04-11
Not sure the answer to your spesific question, but you can see what you've typed for the last couple 100 commands by looking in your .bash_history file:
```
gedit ~/.bash_history
```

---

### Post by Xispa on 2009-04-11
May be easyTAG could help you.

---

### Post by hyper_ch on 2009-04-11
have a look in synaptic... there are many hits with regard to id3....

---

### Post by Kedster on 2009-04-11
Alright so iwent into synaptic and found a program called 
id3v2 
and  this is its help thing
```
ketterer@Ketterer-linux:~/Indestructible[BonusDVD]$ id3v2 -help
Usage: id3v2 [OPTION]... [FILE]...
Adds/Modifies/Removes/Views id3v2 tags, modifies/converts/lists id3v1 tags

  -h,  --help               Display this help and exit
  -f,  --list-frames        Display all possible frames for id3v2
  -L,  --list-genres        Lists all id3v1 genres
  -v,  --version            Display version information and exit
  -l,  --list               Lists the tag(s) on the file(s)
  -R,  --list-rfc822        Lists using an rfc822-style format for output
  -d,  --delete-v2          Deletes id3v2 tags
  -s,  --delete-v1          Deletes id3v1 tags
  -D,  --delete-all         Deletes both id3v1 and id3v2 tags
  -C,  --convert            Converts id3v1 tag to id3v2
  -1,  --id3v1-only         Writes only id3v1 tag
  -2,  --id3v2-only         Writes only id3v2 tag
  -a,  --artist  "ARTIST"   Set the artist information
  -A,  --album   "ALBUM"    Set the album title information
  -t,  --song    "SONG"     Set the song title information
  -c,  --comment "DESCRIPTION":"COMMENT":"LANGUAGE"  
                            Set the comment information (both
                             description and language optional)
  -g,  --genre   num        Set the genre number
  -y,  --year    num        Set the year
  -T,  --track   num/num    Set the track number/(optional) total tracks

You can set the value for any id3v2 frame by using '--' and then frame id
For example: 
        id3v2 --TIT3 "Monkey!" file.mp3
would set the "Subtitle/Description" frame to "Monkey!". 

```

im not sure this is what i used before but it might work if i knew how to use it, does anyone know how to do what i want

---

### Post by t0p on 2009-04-11
> **Kedster said:**
> 
im not sure this is what i used before but it might work if i knew how to use it, does anyone know how to do what i want

I think I know what you need to do.  First of all: learn how to write bash scripts. Personally, I've found the **Advanced Bash Scripting Guide** helpful - to install it, type into the terminal:

```
sudo apt-get install abs-guide
```

It will install to **/usr/share/doc/abs-guide** as html files you can read with firefox (or your favourite browser).  Work your way through this and you should do just fine.

---

### Post by Kedster on 2009-04-13
Im sorry, i dont really understand that guide and iv also do not think that this program has that capabilitie, there is no function to just list artists

---

