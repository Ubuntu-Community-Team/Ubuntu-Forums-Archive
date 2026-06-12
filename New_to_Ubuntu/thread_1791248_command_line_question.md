---
title: "command line question"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-06-26
Is there an easy way to navigate to a file from the command line? When I try to use file tools from the command line it often invloves typing a very long file location and usually get file not found (I know to be in the path 1st). I would like a terminal option that would let me browse to a location to execute a task on for example epub to pdf conversion.

---

### Post by oldos2er on 2011-06-26
Use Tab completion to save yourself some typing, and avoid typos.

---

### Post by cmcanulty on 2011-06-26
Unfortuneately that isn't much help when I am dealing with a file nested through several directories.

---

### Post by oldos2er on 2011-06-26
Maybe I'm not understanding what you're looking for. Can you give an example?

---

### Post by cmcanulty on 2011-06-26
Like I want to use epb2pdf which involves running from the command line and I have to enter each files path and the output path, but the paths are so long every time I type one in it says file not found even when I check it carefully for typos case sensitive etc.

---

### Post by oldos2er on 2011-06-26
I'm not familiar with that program, hopefully someone else is.

---

### Post by Paqman on 2011-06-26
> **cmcanulty said:**
> Unfortuneately that isn't much help when I am dealing with a file nested through several directories.

Why would it not be?

For example, to reach a file located in /file/nested/within/loads/of/directories/ you could just type:

```
cd /fi<TAB>/ne<TAB>/wi<TAB>/lo<TAB>/of/di<TAB>
```

If it doesn't work, try double tapping tab. That makes it spit out all the folders at that level to see if you've got two with very similar names.

You can also drag and drop files from Nautilus into a terminal window and it will bring the whole path with it.

---

### Post by TeoBigusGeekus on 2011-06-26
Try nautilus scripts: right click->open terminal here.

---

### Post by Paqman on 2011-06-26
> **TeoBigusGeekus said:**
> Try nautilus scripts: right click->open terminal here.

Yeah, always install this one myself. The package is called [nautilus-open-terminal]("apt:nautilus-open-terminal").

---

### Post by mcduck on 2011-06-26
cd to source or target directory first to save typing at least one path. Use tab autocompletion and event & history designators to save even more typing. Or, if you work on a desktop, drag&drop files & directories to the terminal to autofill their paths.

If you need to repeat same action on multiple files, learn the basics of shell scripting and use a simple loop to handle all the files at once.

If that's not enough, use mc. It allows you to browse files and execute commands on them.

---

### Post by dFlyer on 2011-06-26
Why not just create a simple bash script and make it executable and place it in your home directory. IE :

cd /path to program
./programname
cd

---

### Post by dcsoldschool53 on 2011-06-26
> **cmcanulty said:**
> Is there an easy way to navigate to a file from the command line? When I try to use file tools from the command line it often invloves typing a very long file location and usually get file not found (I know to be in the path 1st). I would like a terminal option that would let me browse to a location to execute a task on for example epub to pdf conversion.

You can try the CDPATH command. The CDPATH command provides a list that the cd command can search in or through. Which means that , if you put all of the documents or pdf in one folder, you can use the cd command to change to that folder no matter where you are in the terminal. Also you will not need to type the entire path in the terminal just```
cd subfolder-name
```Then use the epb2pdf command to do what you need to do from there. 

Type```
echo $CDPATH
``` to see what in the cd path right now. Look at this web site:

[http://embraceubuntu.com/2006/02/04/make-documentation-easier-to-read/]("http://embraceubuntu.com/category/snippets/page/2/")

**If this does not work, look at my next post. It worked for me.**
[ ]("http://embraceubuntu.com/category/snippets/page/2/")

---

### Post by shiman6 on 2011-06-26
I usually just cd and ls until I'm in the directory I want to be in, then run the program so I don't have to type in the full file path.

---

### Post by SeijiSensei on 2011-06-26
In KDE's dolphin, navigating to a directory and hitting Shift+F4 will open a terminal in that directory.  I think nautilus has a similar (or identical?) function.

---

### Post by cmcanulty on 2011-06-26
OK I need some time to try all those ides. More tomorrow I did install the nautilus open terminal but it doesn't seem to be  right click option or in any menu.Thanks all.OK I found a tip. I had to killall nautilus then reopened it and I have the option. I am trying to convert epub files to PDF using epub2pdf. The directions ared this, but I don't understand as when I try it I keep getting errors
```
chmod +x ./epub2pdf.sh 
./epub2pdf.sh <path-to-epub-file>
```

---

### Post by mcduck on 2011-06-26
> **cmcanulty said:**
> OK I need some time to try all those ides. More tomorrow I did install the nautilus open terminal but it doesn't seem to be  right click option or in any menu.Thanks all.

After installing it you need to log out and back again before it appears in the right-click menu.

---

### Post by Impute on 2011-06-26
Let me try a very simple walkthrough.
Start by going to the epub2pdf directory and running 

```
ls -l

total 160
-rw-r--r-- 1 you you 33740 2010-05-15 15:17 COPYING.epub2pdf
-rw-r--r-- 1 you you    37 2010-05-15 15:17 epub2pdf.bat
-rw-r--r-- 1 you you 92062 2010-05-15 15:17 epub2pdf.jar
-rw-r--r-- 1 you you  1258 2010-05-15 15:17 epub2pdf.properties
-rw-r--r-- 1 you you    39 2010-05-15 15:17 epub2pdf.sh
drwxr-xr-x 3 you you  4096 2010-05-15 15:17 etc
drwxr-xr-x 3 you you  4096 2010-05-15 15:17 lib
-rw-r--r-- 1 you you  5497 2010-05-15 15:17 README.epub2pdf

```

Now run
```
chmod +x epub2pdf.sh
``` 

This time you should get
```
ls -l
...
-rwxr-xr-x 1 you you    39 2010-05-15 15:17 epub2pdf.sh
...

```

The "x" means that now you can execute this script.

To actually test running it I have an epub book at
/home/you/Downloads/library/epub/vonnegut-2-b-r-0-2-b.epub

So in the simplest case I have to write:

```
./epub2pdf.sh /home/you/Downloads/library/epub/vonnegut-2-b-r-0-2-b.epub
```

However there are a few shortcuts:

The "/home/you/" part has a short form "~", the rest is fairly easy with tab completion, so I wrote:
  ./epub2pdf.sh ~/Dow[tab]
Which got turned into 
  ./epub2pdf.sh /home/you/Downloads/
then I wrote:
  l[tab]e[tab]von[tab]
Which got turned into 
  ./epub2pdf.sh /home/you/Downloads/library/
  ./epub2pdf.sh /home/you/Downloads/library/epub/
  ./epub2pdf.sh /home/you/Downloads/library/epub/vonnegut-2-b-r-0-2-b.epub

epub2pdf then produced the pdf in my home directory.

If I only had one other book I would hit the up arrow to bring the previous command then enter the next book title. But since I had several books instead I used:

```
./epub2pdf.sh /home/you/Downloads/library/epub/*.epub

```

To convert all of the books. (Now I'll try to figure out the epub2pdf options to use a smaller font so I can get more on a page.)

---

### Post by dcsoldschool53 on 2011-06-26
This works for me, open```
nautilus
```Goto the directory where your epubs are located. Right click on your .epub, click copy, and close nautilus. In the terminal, after you typed the command with a space after it.```
epub2pdf.sh
```Right click, and paste what you copied from nautilus to the command line. It will look something like this.```
epub2pdf.sh file:///home/your-user-name/epubs/Computer_part.epub
```Delete the file:// using the <- left arrow key, and then the delete key, so that your code will now look like this.```
epub2pdf.sh /home/your-user-name/epubs/Computer_part.epub
```Hit the ENTER key to generate your pdf.

---

### Post by RoyLongbottom on 2011-06-27
[FONT=Verdana][SIZE=2]I have been testing LANs and have paths such as /media/f816ec76-8bf2-4dd3-9e98-62934909a779. What I do is cd /media, ls to list files, type cd then mark required path name using mouse. Next press mouse centre button (wheel in my case). Required file appears after cd. You can also right click on marked name to copy it.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

### Post by 3rdalbum on 2011-06-27
Did you try dragging and dropping the files from the file browser into the terminal window, as was suggested earlier?

---

### Post by dcsoldschool53 on 2011-06-27
> **3rdalbum said:**
> Did you try dragging and dropping the files from the file browser into the terminal window, as was suggested earlier?

Thank you very much, dragging and dropping works very well, and I do not have to delete a thing.

---

### Post by cmcanulty on 2011-06-27
Here is the code results the 1st commands didn't seem to end so I entered the 2nd ones. Obviously I am not understasnding this at all, though I usually am prety good at terminal.

```
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ ls -l
total 156
-rw-r--r-- 1 cmcanulty cmcanulty 33740 2010-05-15 15:17 COPYING.epub2pdf
-rw-r--r-- 1 cmcanulty cmcanulty    37 2010-05-15 15:17 epub2pdf.bat
-rw-r--r-- 1 cmcanulty cmcanulty 92062 2010-05-15 15:17 epub2pdf.jar
-rw-r--r-- 1 cmcanulty cmcanulty  1258 2010-05-15 15:17 epub2pdf.properties
-rw-r--r-- 1 cmcanulty cmcanulty    39 2010-05-15 15:17 epub2pdf.sh
drwxr-xr-x 3 cmcanulty cmcanulty  4096 2011-06-24 12:49 etc
drwxr-xr-x 3 cmcanulty cmcanulty  4096 2011-06-24 12:49 lib
-rw-r--r-- 1 cmcanulty cmcanulty  5497 2010-05-15 15:17 README.epub2pdf
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ 
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ total 160
160: cannot open
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ -rw-r--r-- 1 you you 33740 2010-05-15 15:17 COPYING.epub2pdf
-rw-r--r--: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ -rw-r--r-- 1 you you    37 2010-05-15 15:17 epub2pdf.bat
-rw-r--r--: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ -rw-r--r-- 1 you you 92062 2010-05-15 15:17 epub2pdf.jar
-rw-r--r--: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ -rw-r--r-- 1 you you  1258 2010-05-15 15:17 epub2pdf.properties
-rw-r--r--: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ -rw-r--r-- 1 you you    39 2010-05-15 15:17 epub2pdf.sh
-rw-r--r--: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ drwxr-xr-x 3 you you  4096 2010-05-15 15:17 etc
drwxr-xr-x: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ drwxr-xr-x 3 you you  4096 2010-05-15 15:17 lib
drwxr-xr-x: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ -rw-r--r-- 1 you you  5497 2010-05-15 15:17 README.epub2pdf chmod +x epub2pdf.sh
-rw-r--r--: command not found
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ 
```

---

### Post by cmcanulty on 2011-06-27
Here are the results of another try
```
cmcanulty@HP:~/Documents/eBooks/new/ePub$ epub2pdf.sh
epub2pdf.sh: command not found
cmcanulty@HP:~/Documents/eBooks/new/ePub$ 

```

---

### Post by oldos2er on 2011-06-27
You need to provide the absolute path to epub2pdf.sh ```
~/Documents/eBook\ Reader/epub2pdf/epub2pdf.sh ~/Documents/eBooks/new/ePub/foo.epub
```

---

### Post by mcduck on 2011-06-28
> **cmcanulty said:**
> Here are the results of another try
```
cmcanulty@HP:~/Documents/eBooks/new/ePub$ epub2pdf.sh
epub2pdf.sh: command not found
cmcanulty@HP:~/Documents/eBooks/new/ePub$ 

```

current directory isn't included in the path in Linux, so you need to specifically tell the shell to look for the executable file in current directory:
```
./epub2pdf.sh

```

Also, you need to make the file executable first, at least based on the *ls* output, it isn't executable right now (that's why people told you to run *ls -l* to confirm the file's permissions)
```
chmod +x epub2pdf.sh
```

---

### Post by Drenriza on 2011-06-28
> **cmcanulty said:**
> Is there an easy way to navigate to a file from the command line? When I try to use file tools from the command line it often invloves typing a very long file location and usually get file not found (I know to be in the path 1st). I would like a terminal option that would let me browse to a location to execute a task on for example epub to pdf conversion.

use total command?

---

### Post by cmcanulty on 2011-06-28
OK here is another try. Is the problem maybe the spaces in the file name? I also copies the epub files into the epub2pdf folder to try and make it easier but neither location works.

```
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ ./epub2pdf.sh
epub2pdf v0.5 - Copyright (C) 2010  Brendan C. Lefebvre
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions.
See file 'COPYING' for full license and warranty details.

Usage: com.amphisoft.epub2pdf.Converter <path-to-epub>
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ chmod +x epub2pdf.sh
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ /The Internet is a Palyground
bash: /The: No such file or directory
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ /The Internet is a Playground
bash: /The: No such file or directory
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ ~/Documents/eBooks/new/ePub/The Internet is a Playground
bash: /home/cmcanulty/Documents/eBooks/new/ePub/The: No such file or directory
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ 

```

---

### Post by dcsoldschool53 on 2011-06-28
[quote=cmcanulty]cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ ~/Documents/eBooks/new/ePub/The Internet is a Playground[/quote]This would have worked, except you forgot to include the ./epub2pdf.sh command and the file extension .epub. Add ./epub2pdf.sh to the beginning of the line and add .epub to the end of Playground like this```
cmcanulty@HP:~/Documents/eBook Reader/epub2pdf$ ./epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
```Since you had spaces in the words "The Internet is a Playground" I added the \ and space to indicate the separations in the file. Also you can use the quotation marks to indicate separations in words "The Internet is a Playground".epub. If, on the other hand, the file does not have an .epub extension, leave it out.
 Hope this helps

---

### Post by oldos2er on 2011-06-28
> **cmcanulty said:**
> OK here is another try. Is the problem maybe the spaces in the file name? 

That's why using the Tab key is your friend, it avoids typos, and automatically "escapes" the spaces in file or folder names.

---

### Post by cmcanulty on 2011-06-28
Ok another try and I still get an error with different spacings 2 tries
```
cmcanulty@HP:~/epub2pdf$ epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$ epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$  epub2pdf.sh ~/Documents/eBooks/new/ePub/The\Internet\is\a\Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$ ^C
cmcanulty@HP:~/epub2pdf$
```

---

### Post by dcsoldschool53 on 2011-06-28
I had edited my last post, so I am putting a new entry here. ```
cmcanulty@hp: cd ~/Documents/eBook Reader/epub2pdf
```Next enter this code in the terminal.```
./epub2pdf.sh ~/Documents/eBooks/new/ePub/"The Internet is a Playground".epub
```Or, do what Oldos2er said using the tab key thing.
If the orginal file does not have an epub extension leave it out, but if it does, please put it at the end of Playground.

Sorry I had forgot to add ./ to epub2pdf in my last post that why it didn't work. I had changed it, if you go back and look at it now.

---

### Post by oldos2er on 2011-06-28
> **cmcanulty said:**
> Ok another try and I still get an error with different spacings 2 tries
```
cmcanulty@HP:~/epub2pdf$ epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$ epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$  epub2pdf.sh ~/Documents/eBooks/new/ePub/The\Internet\is\a\Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$ ^C
cmcanulty@HP:~/epub2pdf$
```

Again, you need to call epub2pdf.sh using the full path to the program ```
~/Documents/eBook\ Reader/epub2pdf/epub2pdf.sh /path/to/file.epub
``` or as dcsoldschool53 said, "cd" to the folder where epub2pdf.sh is first.

---

### Post by cmcanulty on 2011-06-28
OK here it is. I don't know what I am doing wrong!
```
[CODE]cmcanulty@HP:~/epub2pdf$ epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$ epub2pdf.sh ~/Documents/eBooks/new/ePub/The\ Internet\ is\ a\ Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$  epub2pdf.sh ~/Documents/eBooks/new/ePub/The\Internet\is\a\Playground.epub
epub2pdf.sh: command not found
cmcanulty@HP:~/epub2pdf$ ^C
cmcanulty@HP:~/epub2pdf$ ./epub2pdf.sh ~/Documents/eBooks/new/ePub/"The Internet is a Playground".epub
epub2pdf v0.5 - Copyright (C) 2010  Brendan C. Lefebvre
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions.
See file 'COPYING' for full license and warranty details.


Registered font families: courier, helvetica, symbol, times, times-roman, zapfdingbats
Default font set to helvetica
Default font base size set to 12.0pt
Default monospace font: courier
Monospace base size: 10.0pt
Default paragraph alignment: left
Margins (top right bottom left): 4.00mm 4.00mm 4.00mm 4.00mm 
Page size (w x h): 90.00mm x 115.00mm
Exception converting /home/cmcanulty/Documents/eBooks/new/ePub/The:
	IOException at:
		com.amphisoft.epub2pdf.Converter.convert

Default font set to helvetica
Default font base size set to 12.0pt
Default monospace font: courier
Monospace base size: 10.0pt
Default paragraph alignment: left
Margins (top right bottom left): 4.00mm 4.00mm 4.00mm 4.00mm 
Page size (w x h): 90.00mm x 115.00mm
Exception converting Internet:
	IOException at:
		com.amphisoft.epub2pdf.Converter.convert

Default font set to helvetica
Default font base size set to 12.0pt
Default monospace font: courier
Monospace base size: 10.0pt
Default paragraph alignment: left
Margins (top right bottom left): 4.00mm 4.00mm 4.00mm 4.00mm 
Page size (w x h): 90.00mm x 115.00mm
Exception converting is:
	IOException at:
		com.amphisoft.epub2pdf.Converter.convert

Default font set to helvetica
Default font base size set to 12.0pt
Default monospace font: courier
Monospace base size: 10.0pt
Default paragraph alignment: left
Margins (top right bottom left): 4.00mm 4.00mm 4.00mm 4.00mm 
Page size (w x h): 90.00mm x 115.00mm
Exception converting a:
	IOException at:
		com.amphisoft.epub2pdf.Converter.convert

Default font set to helvetica
Default font base size set to 12.0pt
Default monospace font: courier
Monospace base size: 10.0pt
Default paragraph alignment: left
Margins (top right bottom left): 4.00mm 4.00mm 4.00mm 4.00mm 
Page size (w x h): 90.00mm x 115.00mm
Exception converting Playground.epub:
	IOException at:
		com.amphisoft.epub2pdf.Converter.convert
cmcanulty@HP:~/epub2pdf$ 

```[/CODE]

---

### Post by dcsoldschool53 on 2011-06-28
ok now open nautilus and look in your home folder "cmcanulty" for the pdf file.

---

### Post by dcsoldschool53 on 2011-06-28
Actually your output said it was working. In your home folder, you should see the file The Internet is a Playground.pdf. If it is not there, open up epub2pdf.properties in the epub2pdf folder and look for this line output.dir: it should be at the bottom to see where your pdf are created.

---

### Post by dcsoldschool53 on 2011-06-28
If you see nothing on that line, type /home/your-user-name. This should do the trick

---

### Post by cmcanulty on 2011-06-28
No file anywhere and yes the properties file said it would go to home folder. I also looked in ebooks and epub and epub2pdf folder.

---

### Post by oldos2er on 2011-06-28
> Exception converting /home/cmcanulty/Documents/eBooks/new/ePub/The:     IOException at:         com.amphisoft.epub2pdf.Converter.convert

Looks like there was a problem with the space in the file name. I think if you rename both your "eBook Reader" folder and "The Internet is a Playground.epub" file so that they don't contain spaces, it would work. Linux file systems and apps don't really deal well with spaces in names.

---

### Post by dcsoldschool53 on 2011-06-29
If you are using an epub that you brought, it is not going to generate the file. Try creating your own .epub using calibre. and do it again.

---

### Post by cmcanulty on 2011-06-29
Well that is the problem then I have 3 I bought and wanted to convert for kindle but no luck with Calibre or anything else. I have tried pdf, mobi, and txt. Thanks all

---

### Post by dcsoldschool53 on 2011-06-29
I may have a solution for you, but right now I have to goto work. Can I PM you later with my answer.

---

### Post by cmcanulty on 2011-06-30
yes thank you

---

### Post by dcsoldschool53 on 2011-06-30
> **cmcanulty said:**
> yes thank you
I had tried a couple of things but they didn't work. I will keep trying until I find an answer.

---

### Post by musicisbest on 2011-07-24
I was getting the same error re: post #33 

IOException at:
		com.amphisoft.epub2pdf.Converter.convert

with no pdf in sight, and found this thread. As oldos2er mentioned, it was just a matter of getting rid of spaces in the epub filename, i.e.
 "This is an example.epub" to "ThisIsAnExample.epub" 

Works fine now.

Thanks

---

