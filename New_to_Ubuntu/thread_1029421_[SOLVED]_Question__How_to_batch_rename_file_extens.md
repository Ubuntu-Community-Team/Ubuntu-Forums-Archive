---
title: "[SOLVED] Question  How to batch rename file extensions.."
date: 2009-01-03
forum: New to Ubuntu
---

### Post by trooperchix on 2009-01-03
Related to posting: [http://ubuntuforums.org/showthread.php?t=1029398](http://ubuntuforums.org/showthread.php?t=1029398)

Since Amarok isn't supporting the .oga filetypes currently (will play but not index into collection, so it is as if the files do not exist) I need to know how to batch rename the file extensions in my music folder from .oga to .ogg as this is a known fix for this problem while Amarok figures out if this is a high priority fix or not. I'm a total noob, I need as much instruction as possible.

Thanks.

---

### Post by kaibob on 2009-01-03
One option is to use the command-line utility rename. To use this, open a terminal window, change to the directory containing the files, and enter:

```
rename -n 's/oga$/ogg/' *.oga
```

The -n option directs rename to do a dry run and report proposed changes. If all appears well, change -n to -v to actually rename the files.

---

### Post by pdtpatrick on 2009-01-03
write a for loop script that would check for instances of .oga and use sed to replace to the new extension. 

or create a regular script to scan your folder where you have these files and then have the result's extensions changed to what you like.

---

### Post by pdtpatrick on 2009-01-03
write a for loop script that would check for instances of .oga and use sed to replace to the new extension. 

or create a regular script to scan your folder where you have these files and then have the result's extensions changed to what you like.

---

### Post by pdtpatrick on 2009-01-03
wow didnt know that command.. i learned something new here as well :)

---

### Post by lavinog on 2009-01-03
```

for FILE in *.oga
do
mv -v "${FILE}" "${FILE%.oga}.ogg"
done

```

or for a one liner
```

for FILE in *.oga;do mv -v "${FILE}" "${FILE%.oga}.ogg";done

```

and if you want to test it out first:
```

for FILE in *.oga;do echo "${FILE}" "${FILE%.oga}.ogg";done

```

---

### Post by lavinog on 2009-01-03
> **kaibob said:**
> One option is to use the command-line utility rename. To use this, open a terminal window, change to the directory containing the files, and enter:

```
rename -n 's/oga$/ogg/' *.oga
```

The -n option directs rename to do a dry run and report proposed changes. If all appears well, change -n to -v to actually rename the files.

wouldn't you want to use 's/.oga$/.ogg/' instead?
just incase oga appears in the filename

---

### Post by kaibob on 2009-01-03
> **lavinog said:**
> wouldn't you want to use 's/.oga$/.ogg/' instead?
just incase oga appears in the filename

The dollar sign directs rename only to change oga if at the end of the file name. Thus, for example, a file with the name oga.txt would not be renamed, and a file with the name oga.oga would be renamed to oga.ogg. Still, it's probably a good idea to include the period.

---

### Post by trooperchix on 2009-01-03
> **kaibob said:**
> One option is to use the command-line utility rename. To use this, open a terminal window, change to the directory containing the files, and enter:

```
rename -n 's/oga$/ogg/' *.oga
```

The -n option directs rename to do a dry run and report proposed changes. If all appears well, change -n to -v to actually rename the files.

Now, how do I do that to change all files listed under my Music folder (keep in mind each artist has a folder and in each artist folder are other folders reflecting album names, and inside those are the .oga files...

For example

/home/eddie/Music/3 Doors Down/The Better Life  would be the artist 3 Doors Down and the album The Better Life, and inside that folder, all the oga songs...

---

### Post by lavinog on 2009-01-03
> **trooperchix said:**
> Now, how do I do that to change all files listed under my Music folder (keep in mind each artist has a folder and in each artist folder are other folders reflecting album names, and inside those are the .oga files...

For example

/home/eddie/Music/3 Doors Down/The Better Life  would be the artist 3 Doors Down and the album The Better Life, and inside that folder, all the oga songs...

try this:
```

find /home/eddie/Music/ -name *.oga -exec rename -n 's/oga$/ogg/' {} \;

```
remember what kaibob mentioned about removing the -n if the dry run worked

---

### Post by trooperchix on 2009-01-03
You rock.  That worked perfectly.  :)

---

### Post by DGortze380 on 2009-01-03
The more important issue here is overlooked... Linux does not use file extensions the same way windows does. While the extension may or may not matter for Amarok, it does not matter for the OS. There is information about the file type in the header that is used to determine file type. Not the extension.

---

### Post by lavinog on 2009-01-04
> **DGortze380 said:**
> The more important issue here is overlooked... Linux does not use file extensions the same way windows does. While the extension may or may not matter for Amarok, it does not matter for the OS. There is information about the file type in the header that is used to determine file type. Not the extension.

That may be true, but isn't it quicker to make a list of files that have a particular extension than to parse headers on every file on a system?
It is common for media files to have extensions anyway...this may seem like a windows thing, but it is handy to be able to quickly look at a directory listing and see which files are media files. Not only that, but many media player devices require proper extensions also.

---

### Post by DGortze380 on 2009-01-04
> **lavinog said:**
> That may be true, but isn't it quicker to make a list of files that have a particular extension than to parse headers on every file on a system?
It is common for media files to have extensions anyway...this may seem like a windows thing, but it is handy to be able to quickly look at a directory listing and see which files are media files. Not only that, but many media player devices require proper extensions also.

I'm not looking for an argument... I didn't say there was anything wrong with extensions, I use them all the time when programming. I tend to use custom ones on linux because it allows me that flexibility. But the fact remains, the operating system doesn't require them (most of the time), and (more often then not) doesn't utilize them.

---

