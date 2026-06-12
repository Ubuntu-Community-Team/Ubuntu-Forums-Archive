---
title: "Help with a Terminal Commands"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by sharathpaps on 2008-12-15
Hello,
           I'm brand new to Linux & I am trying to learn my way through the Command Line. I have a few things that I can't figure out..

I used 'man <command>' but didn't find what I wanted. (By the way, once I finish using the manual for a command, How do I exit the manual? Do I have to open a new terminal each time?)

1.) When using the 'cd' command to change directories, how do I go to a folder with a space in the file name? 

For eg. To navigate to a folder called 'My Games'

         ~$ cd My Games does not work. Is there an abbreviation that I have to use?

2. The same problem arisies with the 'file' command

For eg. To view information about a file called 'Screenshot 1.png'

         ~$ file Screenshot 1.png yields no results.

Please point me in the right direction.

Thank You

---

### Post by howefield on 2008-12-15
Try enclosing the folder/file name with the space in quotes.

---

### Post by hyper_ch on 2008-12-15
quitting the man pages is done with "q".

as for filenames and paths, use TAB complete. Press TAB once to auto-complete, if it doesn't work, then there are more than just 1 options available. Press then TAB again to see all remaining possibilities.

```

cd /
cd ho

```
and now press TAB --> it will complete to "cd home"

---

### Post by Joeb454 on 2008-12-15
To exit the man pages press the 'Q' key :)

And to cd into places with names, you can do one of the following ```
cd My\ Games
file Screenshot\ 1.png
``` Which "escapes" the spaces in the name :)

OR

You can do as suggested above and run ```
cd "My Games"
file "Screenshot 1.png"
```

---

### Post by sharathpaps on 2008-12-15
It Works!!!!

Thank You for the amazingly blazingly fast replies...

:-D

---

### Post by js_fr on 2008-12-15
Bash has a completion mechanism, let say you are in the directory /tmp and you have there a folder called "Test Folder" which you want to enter. If you type ```
cd Te
``` and hit the Tab key, then bash completes this to ```
cd Test\ Folder/
``` (in case there is no other folder there starting with "Te") and you can just hit return to enter the folder.

If you want to know more about commands possible with man type:
```
man man
```

---

### Post by Dedoimedo on 2008-12-15
Hello,

Other useful things you may want to know: find and locate. These two commands allow you to search for files and folders on your system.

For locate, you first update its database:

```

sudo updatedb

```

Then, look for what you desire:
```

locate <whatever>

```

find works similarly, but it takes more arguments when writing the command. For example, used with flag -type d will only look for directories, -type f will only look for files etc.

Example:

```

find . -name my-file -type f

```

This will look for a file named my-file in your current directory (that's the dot).

Furthermore:

```

cd

```

This will take you back yo your home directory. Other ways to navigate back to it are either:

```

cd ~your-username

```

```

cd /home/your-username

```

This can help you narrow down your searches...

Dedoimedo

---

### Post by Vantrax on 2008-12-15
I highly recommend trying this bash tutorial:
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

Its very useful to build an understanding of bash and of file permissions.

---

