---
title: "want to back up 70 gig of data to dvd, how do i do it easily?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by stinger30au on 2009-07-20
i have a hard drive with 20 gig free and there is 70 gigabyte of data on it i want to back up to dvd

the file sizes vary but there is none that are bigger then 1.8 gig in size

i dont care how many dvds it uses to back up the data

but i would like to be able to read the data once it is written to dvd in both windows and ubuntu pc's so im not keen to compress the data, i have 150 blank dvds so blanks are not an issue


and i dont know if it makes any difference but the hdd in question is a slave hdd with assorted data and the main boot hdd that ubuntu 9.04 is loaded to has got 10 gig spare on it
this will be a once off backup and once the data is backed up from th hdd it will be removed from the hdd as he requirement for the data now is very small.

suggestions please

---

### Post by scrapmetal on 2009-07-20
I have done this before. Found the easy way was to have file manager open and DVD burn program open. Worked down the file tree until the next file added would not fit. That was the start of the next DVD. Labeled 1 to 40 something as I went. Copied boot section separately, in case it was needed. Was able to read DVD's on both operating systems.
Boring but works, even for the non computer literate persons to access.

---

### Post by stinger30au on 2009-07-20
yeah that would do the trick, not the answer i was looking for though

was kinda hoping there might be some magic bit of gear i can point at the directory and it will just keep burns data to the dvd till its all done automagically

---

### Post by presence1960 on 2009-07-20
that is not the most reliable or convenient way to back up data. I would invest in a USB drive and use rync or grsync to do the original backup and then continue to do incremental backups at least weekly. You really should have a backup scheme in place and stick to it. Anything can happen at any time and it usually does at the most inopportune times. **_Back up regularly!_**

---

### Post by stinger30au on 2009-07-20
> **presence1960 said:**
> that is not the most reliable or convenient way to back up data. I would invest in a USB drive and use rync or grsync to do the original backup and then continue to do incremental backups at least weekly. You really should have a backup scheme in place and stick to it. Anything can happen at any time and it usually does at the most inopportune times. **_Back up regularly!_**


the data i want is to be saved to dvd and then removed from hdd as it will be pretty rare to need to access the data the in the future

im sure i made his pretty clear in my original post

---

### Post by llamakc on 2009-07-20
> **stinger30au said:**
> the data i want is to be saved to dvd and then removed from hdd as it will be pretty rare to need to access the data the in the future

im sure i made his pretty clear in my original post

So why are you backing up on DVD's? Use something with a longer shelf life.

---

### Post by stinger30au on 2009-07-20
> **llamakc said:**
> So why are you backing up on DVD's? Use something with a longer shelf life.

i have a dvd burner and plenty of blanks, plus a budget of zero bucks to do it with, hence the reason to do it with dvds

i did a search with google and it looks like this question has been asked a number of times
  and it looks like theres not much round to do it


i did a google and i found a windows program that i will test in wine

[http://hcidesign.com/dvdspan/](http://hcidesign.com/dvdspan/)

this looks easy enough

---

### Post by stinger30au on 2009-07-20
this looks like the go 

[http://sourceforge.net/projects/discspan/](http://sourceforge.net/projects/discspan/)

---

### Post by BryanFRitt on 2009-07-20
I haven't tried it yet, but there is a program called dvdisaster that can help ensure data on dvds isn't lost.

---

### Post by presence1960 on 2009-07-20
> **stinger30au said:**
> the data i want is to be saved to dvd and then removed from hdd as it will be pretty rare to need to access the data the in the future

im sure i made his pretty clear in my original post

this is what you said :>  i dont care how many dvds it uses to back up the data

**but i would like to be able to read the data once it is written to dvd in both windows and ubuntu pc's** so im not keen to compress the data, i have 150 blank dvds so blanks are not an issue

DVD's are ok but they are easily susceptible to damage as well as data loss.

---

### Post by stinger30au on 2009-07-20
> **stinger30au said:**
> this looks like the go 

[http://sourceforge.net/projects/discspan/](http://sourceforge.net/projects/discspan/)

PERFECT!!!!

a bit more googleing and i found how to run it, it is a python script

so copy the script to the directory you want to burn to dvd and fire up shell and cd to the directory then type in

pyhton discspan.py 

it read my directory and after a while it has come up and said it will need 17 dvds to burn it to, im about to let it do it

fingers crossed it wont try and make 17 .iso files on my hdd before it tries to burn any of them

---

### Post by stinger30au on 2009-07-21
> **stinger30au said:**
> this looks like the go 

[http://sourceforge.net/projects/discspan/](http://sourceforge.net/projects/discspan/)


this little program kicks butt!!!

it will burn the data on the fly and not create an iso first so you can burn the data even if you have got zero free space left on your hdd!!

YIPPIE!!!

i wish more backup programs used this routine

---

### Post by mangurt on 2009-07-21
Wow!  Slick program!  I burn a lot of data to dvd for my friends that are deployed overseas (mythtv feeds, like football and other sports)  This will make life a lot easier!

---

### Post by presence1960 on 2009-07-21
stinger30au- that looks like a neat script. I back up files to DVD rarely, but that can come in handy for other situations. thanks for the link.

---

### Post by stinger30au on 2009-07-24
i have done some testing with the script and it does not like to run with dvd-rw discs

its a pitty this script wont work with it, i could use it on a zillion other things then too

i must make a note of the errors i get and let the author know

---

