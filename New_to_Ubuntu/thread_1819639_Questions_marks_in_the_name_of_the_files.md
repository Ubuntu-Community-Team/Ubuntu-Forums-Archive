---
title: "Questions marks in the name of the files"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-08-06
I downloaded some mp3 files from Internet! After the extract the rar file i noticed that there are question marks in the name of the files! I am not able to play them, copy,cut or rename them! Please help

I am uploading the snapshot of the files whose file names has question marks

---

### Post by Redblade20XX on 2011-08-06
Can you check the properties of those files for there permissions?

---

### Post by 1991sudarshan on 2011-08-06
> **Redblade20XX said:**
> Can you check the properties of those files for there permissions?


the permissions are already checked it shows read and write but when i tried to rename it show an error  that no such file exits in that directory!

---

### Post by 1991sudarshan on 2011-08-06
> **Redblade20XX said:**
> Can you check the properties of those files for there permissions?


 p, li { white-space: pre-wrap; }  The file or folder /home/kevin/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2/Concerto N&#65533;8 en sol majeur, RV 299 - 06 - III. Allegro.mp3 does not exist.

---

### Post by 1991sudarshan on 2011-08-06
kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$ ls -l
total 125796
-rw-r--r-- 1 kevin kevin  8113352 2009-10-09 01:47 Concerto N?10 en fa majeur, RV 294a - 10 - I. Allegro.mp3
-rw-r--r-- 1 kevin kevin  5235044 2009-10-09 01:47 Concerto N?10 en fa majeur, RV 294a - 11 - II. Adagio.mp3
-rw-r--r-- 1 kevin kevin  8232370 2009-10-09 01:47 Concerto N?10 en fa majeur, RV 294a - 12 - III. Allegro.mp3
-rw-r--r-- 1 kevin kevin 11829992 2009-10-09 01:48 Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3
-rw-r--r-- 1 kevin kevin  5275759 2009-10-09 01:48 Concerto N?11 en r? majeur, RV 208a - 14 - II. Grave.mp3
-rw-r--r-- 1 kevin kevin  9351538 2009-10-09 01:48 Concerto N?11 en r? majeur, RV 208a - 15 - III. Allegro.mp3
-rw-r--r-- 1 kevin kevin  6034747 2009-10-09 01:48 Concerto N?12 en r? majeur, RV 214 - 16 - I. Allegro.mp3
-rw-r--r-- 1 kevin kevin  5954364 2009-10-09 01:48 Concerto N?12 en r? majeur, RV 214 - 17 - II. Grave assai.mp3
-rw-r--r-- 1 kevin kevin  5549289 2009-10-09 01:49 Concerto N?12 en r? majeur, RV 214 - 18 - III. Allegro.mp3
-rw-r--r-- 1 kevin kevin  6714395 2009-10-09 01:43 Concerto N?7 en si b?mol majeur, RV 464 - 01 - I. Allegro.mp3
-rw-r--r-- 1 kevin kevin  4556446 2009-10-09 01:44 Concerto N?7 en si b?mol majeur, RV 464 - 02 - II. Largo.mp3
-rw-r--r-- 1 kevin kevin  5394781 2009-10-09 01:44 Concerto N?7 en si b?mol majeur, RV 464 - 03 - III. Allegro.mp3
-rw-r--r-- 1 kevin kevin  5674572 2009-10-09 01:44 Concerto N?8 en sol majeur, RV 299 - 04 - I. Allegro assai.mp3
-rw-r--r-- 1 kevin kevin  7433715 2009-10-09 01:45 Concerto N?8 en sol majeur, RV 299 - 05 - II. Largo cantabile.mp3
-rw-r--r-- 1 kevin kevin  5595224 2009-10-09 01:45 Concerto N?8 en sol majeur, RV 299 - 06 - III. Allegro.mp3
-rw-r--r-- 1 kevin kevin  8991359 2009-10-09 01:45 Concerto N?9 en si b?mol majeur, RV 373 - 07 - I. Allegro.mp3
-rw-r--r-- 1 kevin kevin  8832670 2009-10-09 01:46 Concerto N?9 en si b?mol majeur, RV 373 - 08 - II. Grave.mp3
-rw-r--r-- 1 kevin kevin  9951844 2009-10-09 01:46 Concerto N?9 en si b?mol majeur, RV 373 - 09 - III. Alla breve.mp3
kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$

---

### Post by dniMretsaM on 2011-08-06
Try rebooting. I know this sounds stupid, but I've had issues like that and a reboot fixed it. Other than that, I don't know.

---

### Post by anewguy on 2011-08-06
I suppose you are quoting the name when you try to access it?  I would quote the file name in a command line copy to a file without the spaces and what ever the special character is (apparently it's not a "?" but some sort of binary character, as witnessed by the error you got).

So, I would try this in a command line copy statement:

cp "Concerto N"?"10 en fa majeur, RV 294a - 10 - I. Allegro.mp3" somefile.mp3

Notice the file name is quoted both sides of the "?".  This leaves the "?" to act as a wildcard single character match.  As an example:

cp Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3 somefile.mp3

becomes quoted:

cp "Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3" somefile.mp3

then quote the question marks:

cp "Concerto N"?"11 en r"?" majeur, RV 208a - 13 - I. Allegro.mp3" somefile.mp3

This last 1 is the syntax you need to follow when multiple question marks are showing in the file name.  Since the character is binary, it's replaced with a "?" when you list it.  Quoting the entire file name insures that the whole file name, spaces and all, will be recognized.  However, the "?"'s will be taken as a literal "?" so it won't match.  Adding the quotes around each "?" means that the "?"'s are seen as wildcards so any character matches - in this case binary characters your default character set can't display.

EDIT:  I should add that on the other file names where there is more than 1 "?", you need to quote around the "?" again so it acts as a wildcard there as well.  Remember: quote the file name, with quotes around each "?" you find in the file name.  

Dave ;)

---

### Post by Old_Grey_Wolf on 2011-08-06
I have seen that &#65533; before. The server hosting my website didn't know about the German letters containing umlauts. I am guessing that those you are seeing are number sign, the music symbol for sharp, or music symbol for flat.

What anewguy wrote should work for naming the files to something readable.

Edit: I Googled and found this 
Concerto N°3 en ré majeur, RV 428 ''Le chardonneret'' 

That would look like 
Concerto N&#65533;3 en r&#65533; majeur, RV 428 ''Le chardonneret'' 
on your computer.

I also found that b&#65533;mol is bémol.

---

### Post by 1991sudarshan on 2011-08-07
> **anewguy said:**
> I suppose you are quoting the name when you try to access it?  I would quote the file name in a command line copy to a file without the spaces and what ever the special character is (apparently it's not a "?" but some sort of binary character, as witnessed by the error you got).

So, I would try this in a command line copy statement:

cp "Concerto N"?"10 en fa majeur, RV 294a - 10 - I. Allegro.mp3" somefile.mp3

Notice the file name is quoted both sides of the "?".  This leaves the "?" to act as a wildcard single character match.  As an example:

cp Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3 somefile.mp3

becomes quoted:

cp "Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3" somefile.mp3

then quote the question marks:

cp "Concerto N"?"11 en r"?" majeur, RV 208a - 13 - I. Allegro.mp3" somefile.mp3

This last 1 is the syntax you need to follow when multiple question marks are showing in the file name.  Since the character is binary, it's replaced with a "?" when you list it.  Quoting the entire file name insures that the whole file name, spaces and all, will be recognized.  However, the "?"'s will be taken as a literal "?" so it won't match.  Adding the quotes around each "?" means that the "?"'s are seen as wildcards so any character matches - in this case binary characters your default character set can't display.

EDIT:  I should add that on the other file names where there is more than 1 "?", you need to quote around the "?" again so it acts as a wildcard there as well.  Remember: quote the file name, with quotes around each "?" you find in the file name.  

Dave ;)

I got this output in the terminal when i tried to copy of these files


[B]kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$[SIZE=3] ls[/SIZE]
Concerto N?10 en fa majeur, RV 294a - 10 - I. Allegro.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 01 - I. Allegro.mp3
Concerto N?10 en fa majeur, RV 294a - 11 - II. Adagio.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 02 - II. Largo.mp3
Concerto N?10 en fa majeur, RV 294a - 12 - III. Allegro.mp3    Concerto N?7 en si b?mol majeur, RV 464 - 03 - III. Allegro.mp3
Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3      Concerto N?8 en sol majeur, RV 299 - 04 - I. Allegro assai.mp3
Concerto N?11 en r? majeur, RV 208a - 14 - II. Grave.mp3       Concerto N?8 en sol majeur, RV 299 - 05 - II. Largo cantabile.mp3
Concerto N?11 en r? majeur, RV 208a - 15 - III. Allegro.mp3    Concerto N?8 en sol majeur, RV 299 - 06 - III. Allegro.mp3
Concerto N?12 en r? majeur, RV 214 - 16 - I. Allegro.mp3       Concerto N?9 en si b?mol majeur, RV 373 - 07 - I. Allegro.mp3
Concerto N?12 en r? majeur, RV 214 - 17 - II. Grave assai.mp3  Concerto N?9 en si b?mol majeur, RV 373 - 08 - II. Grave.mp3
Concerto N?12 en r? majeur, RV 214 - 18 - III. Allegro.mp3     Concerto N?9 en si b?mol majeur, RV 373 - 09 - III. Alla breve.mp3

kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$ cp "Concerto N?10 en fa majeur, RV 294a - 10 - I. Allegro.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 01 - I. Allegro.mp3" /home/kevin

cp: cannot stat `Concerto N?10 en fa majeur, RV 294a - 10 - I. Allegro.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 01 - I. Allegro.mp3': No such file or directory
kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$


[/B]The problem is not about copying, but these files are not being detected and recognized by any music players! Please tell me a way to solve this issue!

---

### Post by 1991sudarshan on 2011-08-07
This is the error message which i got which i tried to copy in the dolphin 

[http://img825.imageshack.us/img825/6058/snapshot10q.png](http://img825.imageshack.us/img825/6058/snapshot10q.png)

---

### Post by 1991sudarshan on 2011-08-07
This is the errror message which i got!

---

### Post by Wim Sturkenboom on 2011-08-07
> **1991sudarshan said:**
> The problem is not about copying, but these files are not being detected and recognized by any music players! Please tell me a way to solve this issue!

The problem is about the copying; it shows the 'same' behaviour as what a music player will. The file can not be 'stat'ed.

It's a bit of work but the follwoing might work

do an ls in a terminal; select the filename and copy it (the name)
next 
```

cp _*paste name here*_ newfilename.mp3

```
repeat for the other files

If it works for one, you can use *mv* instead of *cp*; will save you the hassles later of deleting the originals.

---

### Post by babakott on 2011-08-07
Ok, I see some unique identifiers in each file. Try to do this
```
ls *RV 294a - 12 - III*
```
If it lists the song, then you can fix this by mv the file to a new file name.

```
mv *RV 294a - 12 -III* myfile.mp3
```

This should fix your problems.

---

### Post by 1991sudarshan on 2011-08-07
> **babakott said:**
> Ok, I see some unique identifiers in each file. Try to do this
```
ls *RV 294a - 12 - III*
```If it lists the song, then you can fix this by mv the file to a new file name.

```
mv *RV 294a - 12 -III* myfile.mp3
```This should fix your problems.


the** ls** command did not list any files 

[B]kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$ ls *RV 294a - 12 - III*
ls: cannot access *RV: No such file or directory
ls: cannot access 294a: No such file or directory
ls: cannot access -: No such file or directory
ls: cannot access 12: No such file or directory
ls: cannot access -: No such file or directory
ls: cannot access III*: No such file or directory
kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$ [/B]

---

### Post by 1991sudarshan on 2011-08-07
> **Wim Sturkenboom said:**
> The problem is about the copying; it shows the 'same' behaviour as what a music player will. The file can not be 'stat'ed.

It's a bit of work but the follwoing might work

do an ls in a terminal; select the filename and copy it (the name)
next 
```

cp _*paste name here*_ newfilename.mp3

```repeat for the other files

If it works for one, you can use *mv* instead of *cp*; will save you the hassles later of deleting the originals.

i tried those commands and i got this output! the terminal says that no such files exists

---

### Post by bodhi.zazen on 2011-08-07
That is because bash (the command line) does not like spaces.

Either quote it or use tab completion or escape the spaces.

```
ls "File with spaces"
ls File\ with\ spaces
ls File<hit tab key>
```

---

### Post by scheibenlosen on 2011-08-07
> **1991sudarshan said:**
> i tried those commands and i got this output! the terminal says that no such files exists

I snooped around on Google, and came across this:

[http://www.kde-apps.org/CONTENT/content-files/102853-servicemenu_kde4_rm-special-char.tar.gz](http://www.kde-apps.org/CONTENT/content-files/102853-servicemenu_kde4_rm-special-char.tar.gz)

It's a Python script that looks like it just may be the answer to your question.

I hope it works for you.

---

### Post by 1991sudarshan on 2011-08-07
> **bodhi.zazen said:**
> That is because bash (the command line) does not like spaces.

Either quote it or use tab completion or escape the spaces.

```
ls "File with spaces"
ls File\ with\ spaces
ls File<hit tab key>
```


i suspect that the character encoding of the files name is creating such problems! The vlc is not playing those mp3 files even if the copying and moving of these file are achieved what about playing?

---

### Post by 1991sudarshan on 2011-08-07
> **scheibenlosen said:**
> I snooped around on Google, and came across this:

[http://www.kde-apps.org/CONTENT/content-files/102853-servicemenu_kde4_rm-special-char.tar.gz](http://www.kde-apps.org/CONTENT/content-files/102853-servicemenu_kde4_rm-special-char.tar.gz)

It's a Python script that looks like it just may be the answer to your question.

I hope it works for you.


what I have to do with that tar file??

---

### Post by 1991sudarshan on 2011-08-07
> **babakott said:**
> Ok, I see some unique identifiers in each file. Try to do this
```
ls *RV 294a - 12 - III*
```If it lists the song, then you can fix this by mv the file to a new file name.

```
mv *RV 294a - 12 -III* myfile.mp3
```This should fix your problems.


your idea  did not work pls tell some other way to solve this issue

---

### Post by Old_Grey_Wolf on 2011-08-07
Try ```
ls *"RV 294a - 12 - III"*
```

If it list a file then```
mv *"RV 294a - 12 -III"* [some filename].mp3
```

---

### Post by scheibenlosen on 2011-08-07
> **1991sudarshan said:**
> what I have to do with that tar file??

Unarchive it, possibly to your home directory and run the script that comes from the archive.

---

### Post by anewguy on 2011-08-07
> **1991sudarshan said:**
> I got this output in the terminal when i tried to copy of these files


[B]kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$[SIZE=3] ls[/SIZE]
Concerto N?10 en fa majeur, RV 294a - 10 - I. Allegro.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 01 - I. Allegro.mp3
Concerto N?10 en fa majeur, RV 294a - 11 - II. Adagio.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 02 - II. Largo.mp3
Concerto N?10 en fa majeur, RV 294a - 12 - III. Allegro.mp3    Concerto N?7 en si b?mol majeur, RV 464 - 03 - III. Allegro.mp3
Concerto N?11 en r? majeur, RV 208a - 13 - I. Allegro.mp3      Concerto N?8 en sol majeur, RV 299 - 04 - I. Allegro assai.mp3
Concerto N?11 en r? majeur, RV 208a - 14 - II. Grave.mp3       Concerto N?8 en sol majeur, RV 299 - 05 - II. Largo cantabile.mp3
Concerto N?11 en r? majeur, RV 208a - 15 - III. Allegro.mp3    Concerto N?8 en sol majeur, RV 299 - 06 - III. Allegro.mp3
Concerto N?12 en r? majeur, RV 214 - 16 - I. Allegro.mp3       Concerto N?9 en si b?mol majeur, RV 373 - 07 - I. Allegro.mp3
Concerto N?12 en r? majeur, RV 214 - 17 - II. Grave assai.mp3  Concerto N?9 en si b?mol majeur, RV 373 - 08 - II. Grave.mp3
Concerto N?12 en r? majeur, RV 214 - 18 - III. Allegro.mp3     Concerto N?9 en si b?mol majeur, RV 373 - 09 - III. Alla breve.mp3

kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$ cp "Concerto N[COLOR="Red"]"[/COLOR]?[COLOR="Red"]"[/COLOR]10 en fa majeur, RV 294a - 10 - I. Allegro.mp3[COLOR="Red"]"[/COLOR]    [COLOR="Red"]"[/COLOR] Concerto N[COLOR="Red"]"[/COLOR]?[COLOR="Red"]"[/COLOR]7 en si b[COLOR="Red"]"[/COLOR]?[COLOR="Red"]"[/COLOR]mol majeur, RV 464 - 01 - I. Allegro.mp3" [COLOR="Red"]DO THESE FILES ONE AT A TIME AND PUT A DIFFERENT NAME HERE THAT DOES NOT CONTAIN ANY SPACES OR SPECIAL CHARACTERS FOR THE OUTPUT FILE NAME[/COLOR]
cp: cannot stat `Concerto N?10 en fa majeur, RV 294a - 10 - I. Allegro.mp3      Concerto N?7 en si b?mol majeur, RV 464 - 01 - I. Allegro.mp3': No such file or directory[COLOR="Red"]THESE COPIES DID FAIL[/COLOR]
kevin@kevin-desktop:~/jdownloader/Antonio Vivaldi - 12 Concerti for Oboe and Violin op. 7/CD2$


[/B]The problem is not about copying, but these files are not being detected and recognized by any music players! Please tell me a way to solve this issue!

======================================
I added some red comments in the copy of your post above - please observe them.

[COLOR="Red"]I still see the copying failing, and you seem to be missing the point - the media players WON'T BE ABLE TO OPEN THOSE FILE NAMES AS-IS.  Why?? Because the "?" IS NOT A LITERAL "?" - it's a "special" character.  I also haven't tried opening a file name with spaces in it in a media player - maybe that part works, maybe it doesn't.  Just copy the files with the proper quoting to a file without any spaces or special characters (hint:  try something like test.mp3 just to test it).  Everyone needs to note here that there are characters not recognized by the current character set - that's what the "?" are telling you - you CAN'T try to match on the liternal "?".  You also have spaces, etc., imbedded in the file names.  There are 2 things I've tried to explain before, and have marked above:

[list]The entire file name must be quoted
Any "?" within the file name must be quoted separately[/list]

Quoting the entire file name ensures that the spaces, etc., are interpretted as part of the file name, NOT part of the copy command.  Within the file name, the "?" MUST be quoted to tell the shell to match ANY character here - since the "?" that is showing in the filename is a PLACEHOLDER, NOT THE REAL CHARACTER, using the wildcard will ensure it will match.

As an example:[/color]

if you use the following in the cp statement:

cp "Concerto N[COLOR="Red"]"[/COLOR]?[COLOR="Red"]"[/COLOR]10 en fa majeur, RV 294a - 10 - I. Allegro.mp3[COLOR="Red"]"[/COLOR]  test.mp3

you are asking the shell to match the file name as follows:

Concerto N (must be an exact match)
=plus=
any single character
=plus=
10 en fa majeur, RV 294A - 10 -I.Allegro.mp3 (must be an exact match)

to a file called test.mp3


Now try opening test.mp3 in your media player.
[/COLOR]

---

### Post by bodhi.zazen on 2011-08-08
See my last post re: special characters .

tab completion is still the best ;)

```
bodhi@children-of-fedora: touch fil?e
zsh: no matches found: fil?e

bodhi@children-of-fedora: touch fil\?e\ .txt
bodhi@children-of-fedora: ls
fil?e .txt

bodhi@children-of-fedora: mv fil?e .txt file.txt
zsh: no matches found: fil?e

bodhi@children-of-fedora: ls
fil?e .txt

bodhi@children-of-fedora: mv fil\?e\ .txt file.txt
bodhi@children-of-fedora: ls 
file.txt

bodhi@children-of-fedora:
```

Type the first few letters of the file and then use the tab key ;)

Or use a bulk rename or script it with find.

---

### Post by anewguy on 2011-08-08
thanks for helping out here, bodhi.zazen!  I think the question mark is confusing some people, like the OP, into thinking it's really a question mark and not a place holder for an "unknown" if you will character.  To be honest, I thought about just posting a shell script to do it, but then I don't know enough myself with the shell yet to do it - in C it would be a snap, but I just don't know the shell scripting yet (gives me something real world to try it out on though!).

Dave ;)

---

### Post by 1991sudarshan on 2011-08-08
> **anewguy said:**
> ======================================
I added some red comments in the copy of your post above - please observe them.

[COLOR=Red]I still see the copying failing, and you seem to be missing the point - the media players WON'T BE ABLE TO OPEN THOSE FILE NAMES AS-IS.  Why?? Because the "?" IS NOT A LITERAL "?" - it's a "special" character.  I also haven't tried opening a file name with spaces in it in a media player - maybe that part works, maybe it doesn't.  Just copy the files with the proper quoting to a file without any spaces or special characters (hint:  try something like test.mp3 just to test it).  Everyone needs to note here that there are characters not recognized by the current character set - that's what the "?" are telling you - you CAN'T try to match on the liternal "?".  You also have spaces, etc., imbedded in the file names.  There are 2 things I've tried to explain before, and have marked above:

[LIST]
[*]The entire file name must be quoted
Any "?" within the file name must be quoted separately
[/LIST]

Quoting the entire file name ensures that the spaces, etc., are interpretted as part of the file name, NOT part of the copy command.  Within the file name, the "?" MUST be quoted to tell the shell to match ANY character here - since the "?" that is showing in the filename is a PLACEHOLDER, NOT THE REAL CHARACTER, using the wildcard will ensure it will match.

As an example:[/COLOR]

if you use the following in the cp statement:

cp "Concerto N[COLOR=Red]"[/COLOR]?[COLOR=Red]"[/COLOR]10 en fa majeur, RV 294a - 10 - I. Allegro.mp3[COLOR=Red]"[/COLOR]  test.mp3

you are asking the shell to match the file name as follows:

Concerto N (must be an exact match)
=plus=
any single character
=plus=
10 en fa majeur, RV 294A - 10 -I.Allegro.mp3 (must be an exact match)

to a file called test.mp3


Now try opening test.mp3 in your media player.
[/COLOR]


Thank you [anewguy]("http://ubuntuforums.org/member.php?u=331304") your post helped to solve the issue! I want to know whether i have install extra packages for correct character ending for the file name! This happened earlier but I was able to move those files

---

### Post by anewguy on 2011-08-08
Glad it was able to help you, and most importantly you can now do what you want.

If you are finished with this thread, please go to the top of the thread, chose thread tools, and marked the thread as solved.

Dave ;)

---

