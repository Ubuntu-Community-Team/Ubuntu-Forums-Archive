---
title: "looking for script to remove spaces from filenames"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by stinger30au on 2009-06-18
i dont know if it can be done, but im chasing a script that can read a directory and read the filenames and remove all the spaces and replace the spaces with a .

example

this file needs to be changed

this.file.needs.to.be.changed


can it be done??

thanks

---

### Post by Mornedhel on 2009-06-18
When in the directory :

```
rename -n 's/ /./g' *
```

Run it (it won't rename the files yet), check that it does what it's supposed to, then run it again without the -n so it actually renames the files.

---

### Post by stinger30au on 2009-06-18
awesome.thanks

---

### Post by Ms_Angel_D on 2009-06-18
Just fyi there is a gui for renaming in synaptic, just search for pyrenamer and install. I have found it quite handy. You can also [CLICK HERE]("apt://pyrenamer") to install it.

---

### Post by stinger30au on 2009-06-19
thanks for the info Angel;)

---

### Post by sisco311 on 2009-06-19
> **Mornedhel said:**
> When in the directory :

```
rename -n 's/ /./g' *
```

Run it (it won't rename the files yet), check that it does what it's supposed to, then run it again without the -n so it actually renames the files.

rename is not available everywhere.if you don't have it, a simple bash script should do the trick:

```

find */path/to/dir* -type f -iname "* *" | \
while read file; do \
**echo** mv "${file}" "${file// /.}"; \
done

```

(remove the **echo** command to actually rename the files)
NOTE: find will search for files in /path/to/dir recursively.  

gprename, pyrenamer, thunar (file manager) and krename are GUI renamer tools.

---

### Post by Mornedhel on 2009-06-19
> **sisco311 said:**
> rename is not available everywhere.

This is true, but it's been available out of the box in every Ubuntu since Dapper Drake at least.

---

### Post by MrWES on 2009-06-19
> **stinger30au said:**
> i dont know if it can be done, but im chasing a script that can read a directory and read the filenames and remove all the spaces and replace the spaces with a .

example

this file needs to be changed

this.file.needs.to.be.changed


can it be done??

thanks

You could also install purrr
```
sudo apt-get install purrr
```
it's a GUI batch renaming app.
[http://packages.ubuntu.com/hardy/utils/purrr]("http://packages.ubuntu.com/hardy/utils/purrr")
It's available in both Ibex and Jaunty.

Bill

---

### Post by stinger30au on 2009-06-19
thanks all that have responded

i have got the job done in a matter of seconds now.

i was dredding renaming a few thousand files by hand

---

### Post by ghostdog74 on 2009-06-19
if you have Python (2.4++), you can use the script i have (see my sig last link called File renamer)
usage
```

# python filerenamer.py -p " " -e "." -l "*"

```
remove the "-l" option to commit changes. use -h option to see more functions of the script.

---

### Post by RedRat on 2009-06-20
Well if you can live with a GUI, try Thunar file manager. It has a powerful renaming tool and is a good file manager, similar to Nautilus. There are a myriad of ways to rename files, eg.removing characters, replacing characters in either the name itself or in the suffix. 

All that being said, i would suggest that you not put a "dot" in the middle of the file names, I would suggest an underscore. The reason for this is that some Ubuntu programs seem to have a difficult time recognizing these names, e.g., DigiKam renaming tool.

---

### Post by stinger30au on 2009-06-20
i plan to *NOT* use the space bar when naming linux files and use the . instead


just busy converting a ton of data from windows to linux and the data will never see the light of windows ever again

<insert evil laugh here>

;)

---

### Post by dariem on 2010-06-02
Hello,

I'm very impressed regarding the answers.
Is it possible to limit the file name size at maximum 50 characters?

Thank you all,
Marius Darie

---

### Post by Vimmander on 2010-07-27
I'm slowly switching from Windows 7 to Lucid, and have been using SpaceRemover to change my files from having spaces to having underscores.  This naming scheme works in Solaris, which I use at college, so it should work in Ubuntu, right?  Also, does it matter if folders (directories) have spaces in them?  I've already added underscores to my folders in Windows that I want to transfer over, but I'd like to know anyway.

Thanks ^.^

Edit:  Whoops, I just saw that this thread was marked as solved.  Should I move it to a new thread?

---

