---
title: "Can't get to the file I want to edit in the terminal"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Thebear on 2009-04-14
I have an apple tv and I use Filezilla to move files back and forth from my laptop to the Apple Tv - occasionally I have to modify some files on the apple tv and I was delighted to find that I could use the ubuntu terminal to modify most files. 

There is a boxee app call boxee@ca that I would like to load but I have to edit and xml sources files on the apple TV. 

 have transfered ctv feeds directory to ATV, now I am trying to update the sources file using my ubuntu terminal - can't seem to get to the proper directory, when I input

cd ([User]/Library/Application Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml)  I get the message "too many arguments"

I can get to Library but can't get past Applicaton Support

when I type "ls" application support is there but I can't get to it and therefore I can't get to the xml file.

Also once I get there I am not sure what editor to use.  I would probably have to load vi onto apple tv, but if there are alternatives

---

### Post by skymera on 2009-04-14
I believe you need :

cd [User]/Library/Application\ Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml

then it should work

---

### Post by Joeb454 on 2009-04-14
Try either ```
cd [User]/Library/Application\ Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml
```

or ```
cd "[User]/Library/Application Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml"
```

That should work :)

---

### Post by Thebear on 2009-04-14
> **skymera said:**
> I believe you need :

cd [User]/Library/Application\ Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml

then it should work

I feel I am getting closer but this time I get the following 

tcsh: [User]/Library/Application Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml: No match.

---

### Post by Thebear on 2009-04-14
> **Joeb454 said:**
> Try either ```
cd [User]/Library/Application\ Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml
```

or ```
cd "[User]/Library/Application Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml"
```

That should work :)

t

Here is what followed from the first example 

tcsh: [User]/Library/Application Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml: No match.

and this from the second with the quotes


tcsh: [User]/Library/Application Support/BOXEE/UserData/profiles/[boxeeUser]/sources.xml: No match.

Any clues?

---

### Post by Miljet on 2009-04-14
Leave off the sources.xml on the end?

That is assuming that sources.xml is the file that you want to edit and therefore not a directory.

---

### Post by Paqman on 2009-04-14
You have to use \ to escape any spaces or special characters. You might find you can use TAB autocompletion to help you. What happens if you just type App[TAB] instead of Application Support? It should autocomplete the address, complete with escaped spaces.

---

### Post by Thebear on 2009-04-16
> **Paqman said:**
> You have to use \ to escape any spaces or special characters. You might find you can use TAB autocompletion to help you. What happens if you just type App[TAB] instead of Application Support? It should autocomplete the address, complete with escaped spaces.

Thanks here is what I get\


[AppleTV:~/Library] root# ls
Application Support	Fonts			Logs
Autosave Information	Frameworks		PreferencePanes
Caches			Icons			Preferences
Cookies			Keychains
[AppleTV:~/Library] root# cd Application Support 
tcsh: cd: Too many arguments.
[AppleTV:~/Library] root# cd App[TAB]
tcsh: App[TAB]: No match.
[AppleTV:~/Library] root# 


The bear

---

### Post by Thebear on 2009-04-16
> **Thebear said:**
> Thanks here is what I get\


[AppleTV:~/Library] root# ls
Application Support	Fonts			Logs
Autosave Information	Frameworks		PreferencePanes
Caches			Icons			Preferences
Cookies			Keychains
[AppleTV:~/Library] root# cd Application Support 
tcsh: cd: Too many arguments.
[AppleTV:~/Library] root# cd App[TAB]
tcsh: App[TAB]: No match.
[AppleTV:~/Library] root# 


The bear


Okay I got it now, going carefully one directory at a time I finally got there, now can someone help me out with how to modify the file 

Do I have to install vi editor on my apple tv?

---

### Post by llamabr on 2009-04-16
I don't know anything about appletv, but if it's running linux, it already has vi.  I find that nano is more friendly of an editor for beginners, though.

---

### Post by Thebear on 2009-04-17
Thanks for the help everyone. In case anyone runs into this problem, it seems that nano is the resident text editor on Apple tv,  Similar to vi, not too difficult to use. 

and I learned about spaces in directory names and how to navigate a bit. 

Ubuntu forums definitely the place to learn almost anything,

What a great community.

---

