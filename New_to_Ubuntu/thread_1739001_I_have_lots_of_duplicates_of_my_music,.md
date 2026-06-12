---
title: "I have lots of duplicates of my music,"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-04-25
Its definitely not something ive done myself but i have hundreds of my music files that have been duplicated, its very bizarre because the duplicates dont have the same name, its obviously a botched up attempt to automatically reorganize my music folder by a media player, (im using banshee btw, always have done, on natty), i wanted to jot up a command to delete all the duplicates automatically because there are too many to do manually, i notice that md5sum hashes for duplicates are the same despite the different name, so im thinking i need to recursively go down through the  directory tree starting at /home/mark/Music/ and run md5sum on each file, append the hash to a text file and if its already there to delete the 2nd file, 

Am i going completley off the rails here, im not sure if this is a good idea, has anyone any better ideas, if not then is there someone who could help me get the syntax correct for this because im only a beginner with bash

Thanks 
Mark

---

### Post by dearingj on 2011-04-25
I believe the program fdupes will work for you. You can install it using
```
sudo apt-get install fdupes
```
and run it using
```
fdupes -r -d /home/mark/Music
```

The -r option tells it to recurse through each directory inside Music, and -d makes it ask about deleting the duplicates.

---

### Post by CaptainMark on 2011-04-25
perfect, thank you, it seems this does almost exactly what i said,

---

### Post by CaptainMark on 2011-04-25
aaah, cancel the party. Still this done exactly what i asked but it seems not all the duplicates have the same hash, only some of them. It only detected 33 dupes which i deleted but i still have lots and they all have different md5sum's to the original.

Does anyone have any ideas that dont reply on md5sum's?

---

### Post by CaKiwi on 2011-04-25
How are the names of the duplicates related to the names of original files? Can you determine that a file is a duplicate just by looking at the name?

---

### Post by CaptainMark on 2011-04-26
Seemingly random also, ```
mark@mark-desktop:~$ md5sum ~/Music/Bassment\ Jaxx/Rooty/*
1553d4cecd853d2999d04445cf83a81e  /home/mark/Music/Bassment Jaxx/Rooty/Bassment Jaxx - Do your thing.mp3
29847bd5f533bbe6f5e20f3a58f39881  /home/mark/Music/Bassment Jaxx/Rooty/Do your thing.mp3

``` the band names have been added to the file name, but also sometimes so has the track number

---

### Post by CaKiwi on 2011-04-26
Do all duplicates and no originals have a dash in the filename? If so you could use **find** to get a list of the duplicates.```
find ~/Music -name "*-*"
```Then use find with the exec option to remove them, or pipe the list to a file and put **rm** in front of each name and execute the file as a script

---

### Post by hakermania on 2011-04-26
If they haven't got the same hash or name, this is gonna be a difficult solution if you want my opinion ;)

---

### Post by CaptainMark on 2011-04-26
this isnt an option as a lot of normal files are hyphenated, damn banshee, ill just have to be vigilent at removing them when i see i them and in about 6 years ill be dupe free

or whatever botched program decided to bless me with mulitple files

---

### Post by CaKiwi on 2011-04-26
Were all the duplicates created on a particular date or on a date after the originals?

---

### Post by CaptainMark on 2011-04-27
good thinking but the originals and the copeis all seem to have been given the same date stamp, :mad:

---

### Post by rosencrantz on 2011-04-27
If the original filename (just the song title, right?) is always a subset of the changed one, you could search for each file whether there's another one containing the file name (minus the .mp3 extension) as a substring. I can't give you the proper bash expressions OTOH though, I tend to chicken out to Python as soon as it gets more complicated.

---

### Post by tgalati4 on 2011-04-27
I use easytag and sort by name.  Duplicates will be more obvious, but you will still have to delete by hand.  The problem is the ID3 tags (several versions and where the data is stored) as well has the filenames.

sudo apt-get install easytag

---

