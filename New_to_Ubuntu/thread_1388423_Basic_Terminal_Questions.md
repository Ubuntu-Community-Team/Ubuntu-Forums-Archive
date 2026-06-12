---
title: "Basic Terminal Questions"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by n125 on 2010-01-23
Hi, I have a few simple questions about Terminal.

1) Is there any way to manipulate multiple files simultaneously? Say I want to copy a pdf, a txt, and a html file (all with different names) to a folder. Is my only option to do

> $ cp filename.pdf PATH/Destination && cp filename.txt PATH/Destination && cp filename.html PATH/Destinationor is there an easier way?

2) If I wanted to start, say, Open Office in Terminal, I'd have to type in "ooffice". The thing is, how do I *know* that "ooffice" = Open Office? The same applies to, say, Eye of Gnome, where I'd have to enter "eog", which by itself isn't really indicative of which program it refers to. How do I find these names out and which programs they refer to? Is there a command that will print out all of the installed programs alongside their executable names?

3) Do I have to install anything in particular to be able to compile programs downloaded as source files? The read me files that come with these downloads usually tell me to do something along the lines of

a) Navigate to the directory containing the source;
b) Type make;
c) Type install.

This never really works for me; usually it tells me something about the target file not being found. (I don't really remember off-hand.)

Thanks!

---

### Post by acho on 2010-01-23
In ubuntu desktop.... It's simple to do everything. in u'r case

1. Try drag n drop like u had use windows :)
2. Open Office is already installed....:popcorn:
3. Don't try rpm or bin installation if u can't understand how it works... if u try it u must to know the system u have... like what C++ and phython on your system, for execution....
 Solution for u is try get debian package, use synaptic program for installation or or Add/remove program Applications..

I hope it can help u to try Ubuntu Desktop, It's simple to use it... cheers!!

---

### Post by d3v1150m471c on 2010-01-23
```

cp /path/to/file /path/to/copy && cp /path/to/file /path/to/copy && cp /path/to/file /path/to/copy

```rightclick your menu and go to edit. click the application you want to know the command for and click properties. It will display the command for it. **do not use graphical applications as root with _sudo_. instead use _gksudo._**

No, you don't need anything special to download source code but you may have to check the box in your system > administration > software sources.

to navigate to a directory
```

cd /path/to/fileordirectory

```

Note- make and make install is typically something done with tar balls. This won't work for all of them. Open the tar ball and check for a txt file with instructions and possible needed dependencies that will need to be installed with it.

---

### Post by nitstorm on 2010-01-23
Was a little slow in typing, the post above me answers it all. Cheers :)

---

### Post by John Bean on 2010-01-23
1. ```
$ cp filename.pdf PATH/Destination filename.txt PATH/Destination filename.html PATH/Destination
``` Please use "man cp" to discover more about cp. 

2. To find the filename of a GUI program just look at its properties in the menu item or launcher. The "command" field will contain the name of the program file.

3. With respect, one step at a time is my advice. We all had to start somewhere so I'm not being condescending, but your first two questions ring alarm bells when followed by the third one.

---

### Post by DaithiF on 2010-01-23
> **n125 said:**
> 
1) Is there any way to manipulate multiple files simultaneously? Say I want to copy a pdf, a txt, and a html file (all with different names) to a folder. Is my only option to do

or is there an easier way?

Hi,
```
cp -t /destination/folder file1.pdf file2.txt file3.html
```

and as a previous poster said, 
```
man cp
```
to learn more about the cp command.

---

### Post by anaconda on 2010-01-23
2.  An alternate way to open files from terminal is:
```
xdg-open filename.pdf
```
if will open the file/picture/movie/etc.. with the default application...

no need to remember programnames..

---

### Post by nothingspecial on 2010-01-23
You can use curly brackets -

cp {file.pdf,file.txt,file3.doc} destination/

---

### Post by VCoolio on 2010-01-23
> **anaconda said:**
> 2.  An alternate way to open files from terminal is:
```
xdg-open filename.pdf
```
if will open the file/picture/movie/etc.. with the default application...

no need to remember programnames..

xdg-open will look at default apps specified with alternatives (install galternatives for a graphical and easier tool); in ubuntu you can use gnome-open (kde-open on kubuntu). gnome-open for example will use for urls the default browser specified in system > preferences > default / preferred apps, while xdg-open will use the browser set as x-www-browser. These can be different.

Also, compiling is a lot less risky if you use something like [checkinstall]("https://help.ubuntu.com/community/CheckInstall") instead of sudo make install (it creates a .deb. which is easy to undo / remove).

---

### Post by Mornedhel on 2010-01-23
cp works like this:

```
# Copy file "file1" to file "file2", clobbering file2 if it exists
$ cp file1 file2
# Copy file "file1" to folder "folder", clobbering a file called "file1" if it already exists in "folder"
$ cp file1 folder/
# Copy several files to folder "folder", same as above
$ cp file1 file2 file3 folder/
```

The slash is optional. Many options exist, I refer you to the man page for further explanations.

Note that "cp file1 file2 file3" will fail if "file3" is not a directory. Also be careful of spaces in filenames.

> **nothingspecial said:**
> You can use curly brackets -

cp {file.pdf,file.txt,file3.doc} destination/

That's The Wrong Way (tm) to use curly brackets. The Right Way (also tm) would be something like "cp file.{pdf,txt} file3.doc destination/".

---

### Post by nothingspecial on 2010-01-23
> **Mornedhel said:**
> 
That's The Wrong Way (tm) to use curly brackets. The Right Way (also tm) would be something like "cp file.{pdf,txt} file3.doc destination/".

Depends on the situation and what you want to accomplish.

---

### Post by Mornedhel on 2010-01-23
> **nothingspecial said:**
> Depends on the situation and what you want to accomplish.

Yes, but in this situation your use of curly braces accomplishes nothing. If you replace the commas with spaces and remove the braces you get the exact same effect.

Think as I might, I can't find a use for curly braces with no prefix or suffix.

---

### Post by Dougie187 on 2010-01-23
> **n125 said:**
> 1) Is there any way to manipulate multiple files simultaneously? Say I want to copy a pdf, a txt, and a html file (all with different names) to a folder. Is my only option to do
or is there an easier way?

As people have mentioned in this post already,
```

cp filename.txt filename.pdf filename.html Path/.

```
Will work, also, if the filenames are all the same
```

cp filename* Path/.

```


> **n125 said:**
> 
2) If I wanted to start, say, Open Office in Terminal, I'd have to type in "ooffice". The thing is, how do I *know* that "ooffice" = Open Office? The same applies to, say, Eye of Gnome, where I'd have to enter "eog", which by itself isn't really indicative of which program it refers to. How do I find these names out and which programs they refer to? Is there a command that will print out all of the installed programs alongside their executable names?

The easiest way I have found to get the executable name, is to right click on the applications menu, and go to edit menu. Then navigate to the launcher (in the menu) that you are looking for, and see what command is executed. In addition to this, you could set up aliases ```
man alias
``` for the programs you are interested in, and then get names you like and know to run the programs you want to run.

One other thing you can do, is use ```
man -k
```

This lets you search for programs that do a certain thing. like for instance, ```
man -k openoffice
``` will return a list of executables and descriptions for all of the openoffice suite.

> **n125 said:**
> 
3) Do I have to install anything in particular to be able to compile programs downloaded as source files? The read me files that come with these downloads usually tell me to do something along the lines of

a) Navigate to the directory containing the source;
b) Type make;
c) Type install.

This never really works for me; usually it tells me something about the target file not being found. (I don't really remember off-hand.)


```
sudo apt-get install build-essential
```
That should set it up so you can compile stuff from source. That is basically all you have to do to compile stuff (the make, make install stuff). Sometimes you have to do this though
```
 cd Path
./configure
make
(sudo) make install
```

Hope this helps some.

---

### Post by nothingspecial on 2010-01-23
> **Mornedhel said:**
> Yes, but in this situation your use of curly braces accomplishes nothing. If you replace the commas with spaces and remove the braces you get the exact same effect.

Think as I might, I can't find a use for curly braces with no prefix or suffix.

The original question was 


> 1) Is there any way to manipulate multiple files simultaneously?

My answer was that you could use curly brackets.

The example was just the example used.

>  Say I want to copy a pdf, a txt, and a html file (all with different names) to a folder.

Read it as simply

Q Is there a way to manipulate multiple files simultaneously?

A Yes, you can use curly brackets.

---

### Post by Mornedhel on 2010-01-23
> **nothingspecial said:**
> Q Is there a way to manipulate multiple files simultaneously?

A Yes, you can use curly brackets.

Well, yes, with curly brackets you can manipulate multiple files simultaneously. I believe, however, that the OP just didn't realize that cp could take more than one filename as argument. Curly brackets achieve this (through, well, curly bracket expansion), but there are other possibilities (another poster mentioned globs), all of which result after various expansion mechanisms in multiple filenames.

I think the most correct answer would have been "you can use multiple filenames, and you can do this by hand, with globs, or with curly braces". As it is, your answer can lead the OP to believe that you *need* curly braces to enter more than one filename.

---

### Post by John Bean on 2010-01-23
> **nothingspecial said:**
> My answer was that you could use curly brackets

There are lots of things you can do that work but are unnecessary. The simplest solution is usually the best and the braces in this example just add unnecessary syntactical complexity when the OP was asking for simplicity.

---

### Post by nothingspecial on 2010-01-23
I`ll shut up then.

@OP [SIZE="3"][COLOR="Red"]DO NOT USE CURLY BRACKETS - THEY ONLY OVERCOMPLICATE THINGS[/COLOR][/SIZE]
[SIZE="1"][COLOR="Magenta"]
- or you could read about what is known as bash brace expansion and do some really groovy stuff. [/COLOR][/SIZE]

:-$ [SIZE="1"]don`t say it was me who told you[/SIZE]

---

### Post by olanrewajux@gmail.com on 2011-01-16
pls how can i copy this pdf file "how to program in java .pdf" using ubuntu terminal

---

### Post by VCoolio on 2011-01-16
> **olanrewajux@gmail.com said:**
> pls how can i copy this pdf file "how to program in java .pdf" using ubuntu terminal

I guess you have problems with the spaces in the filename. So type: 
cp how[now press tab to let it autocomplete] /path/to/destination
or escape the spaces with a backslash:
cp how\ to\ program\ in\ java.pdf /path/to/destination
or put between "" to make clear these words are one file:
cp "how to program in java.pdf" /path/to/destination

---

### Post by The Cog on 2011-01-16
VCoolio has pretty-much covered it. If a filename has spaces, use a backslash in front of each space, or put the whole filename in quotes.

You must specify a destination. If you give a filename, it will copy to that name. If you give a folder name, it will copy to that folder and use the sources's file name. 

If you want to copy a file from elsewhere to the current directory, just use a dot as the destination. Dot "." means "this directory" (and ".." means parent directory).


You would be better off starting a new thread for your questions rather than resurrecting other people's conversations that ended a year ago.

---

### Post by wolffu on 2011-01-16
1) If you are copying all of the files to the same destination you can use: ```
 cp filename.pdf filename.txt filename.html PATH/Destination 
```  2) I am not aware of any way to list the package along with the executable file name. I would start looking around in 'dpkg-query' for the information. But, if you knew you were looking for the "Terminal" executable for example you could select:   System->Preferences->Main Menu   Select Accessories in the Left list   Select Terminal in the Right List   Click on Properties   In the message box the line listed for "Command" would be the terminal command to use.  3) If you are attempting to compile an application from source code, the instructions for each application can be different, and the individual instructions should be found on the website/documentation, however, many projects use a configure, make, make install procedure. I believe that most of these tools are found in the "build-essential" package. From the terminal line: ```
 sudo apt-get install build-essential 
```  Hope this info is helps. Tony

---

### Post by wolffu on 2011-01-16
1) If you are copying all of the files to the same destination you can use: ```
 cp filename.pdf filename.txt filename.html PATH/Destination 
```  2) I am not aware of any way to list the package along with the executable file name. I would start looking around in 'dpkg-query' for the information. But, if you knew you were looking for the "Terminal" executable for example you could select:   System->Preferences->Main Menu   Select Accessories in the Left list   Select Terminal in the Right List   Click on Properties   In the message box the line listed for "Command" would be the terminal command to use.  3) If you are attempting to compile an application from source code, the instructions for each application can be different, and the individual instructions should be found on the website/documentation, however, many projects use a configure, make, make install procedure. I believe that most of these tools are found in the "build-essential" package. From the terminal line: ```
 sudo apt-get install build-essential 
```  Hope this info is helps. Tony

---

