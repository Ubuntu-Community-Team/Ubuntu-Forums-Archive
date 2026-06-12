---
title: "opening a .jnlp file"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by s1wood on 2010-07-20
I'm trying to install a connection program from one of my suppliers, it works through Java but the final install ends with the error message
 /My Properties/si2.properties  (Nosuch file or directory)
and I understand it is looking for that file on a windows C disk - is there any way round this? 
The shortcut that appeared on a previous attempt is marked as untrusted and won't launch.

If the answer to this involves using the terminal please spell out the instructions clearly - I have not yet used the terminal in Ubuntu and am not too sure of the procedure.

All suggestions gratefully received (including: Give up, it won't work)

Susan

---

### Post by gandaran on 2010-07-20
first does this program work in linux?
we would need to look at the install instructions to help you, can you post them.

---

### Post by s1wood on 2010-07-21
I have no actual installation instructions. the IT expert at the other end refuses to give any opinion on Linux but says that since it works through Java it may work.

I was given a link which can either be opened with  Java or saved (I have tried both)
but whatever I do I end up with the same error message, though at various stages. JRE is installed and up to date.


the last advice I was given is 
[SIZE=2]>[COLOR=#1F497D][FONT=&quot]There should be a  folder on the hard disk – what we would normally call “C drive”.  It should be called “My Properties”.   There should  also be another called “Temp”.[/FONT][/COLOR][/SIZE]   [SIZE=2][COLOR=#1F497D][FONT=&quot]In the “My Properties”  folder there should be a file called si2.properties.[/FONT][/COLOR][/SIZE]
   [SIZE=2][COLOR=#1F497D][FONT=&quot]  [/FONT][/COLOR][/SIZE]
   [SIZE=2][COLOR=#1F497D][FONT=&quot]The file needs to  contain the following lines[/FONT][/COLOR][/SIZE]
   [SIZE=2][COLOR=#1F497D][FONT=&quot]  [/FONT][/COLOR][/SIZE]
   [SIZE=2][COLOR=#1F497D][FONT=&quot]-- listing properties  --[/FONT][/COLOR][/SIZE]
   [SIZE=2][COLOR=#1F497D][FONT=&quot]location=/temp/si2 <
[/FONT][/COLOR][/SIZE]
    [COLOR=#1F497D][FONT=&quot]  
[/FONT][/COLOR]

The link is

[http://supplier.dunlops.com/connect/connect.jnlp](http://supplier.dunlops.com/connect/connect.jnlp)
If it starts properly there will be a point where one has to ring Dunlops for a password - if you try it and it gets that far that's fine, just tell me how you did it and I will attempt to go from there.  

regards,

Susan

---

### Post by mike555 on 2010-07-21
[http://www.downloadatoz.com/file-extensions/jnlp-file-extension.html](http://www.downloadatoz.com/file-extensions/jnlp-file-extension.html)

---

### Post by gandaran on 2010-07-21
well java applications can work both in windows and Linux, (I have one that does, it was programed to work on any platform!) but this one (the download install file only, the download launch file works okay) I think looks for windows paths which don't exist in Linux so unless someone can change the code I don't think you will be able to install or run it properly.

---

### Post by s1wood on 2010-07-21
That was rather what I suspected, thanks for trying.

Susan

---

### Post by eriktheblu on 2010-07-21
Hmmmmmm...... I wonder.....

It could be that it's just unable to create the needed directories. On this MS machine here at work, I don't have a "My Properties" folder so I assume it's a creation of this program.

Try this:
Copy (Ctrl + C) these lines, then paste (Ctrl + Shift + V) into your terminal. 

```
sudo mkdir "/My Properties"
```
You will be prompted for your password, enter your administrator password. The password will not display and there will be no placeholders, just hit enter.

This will create the proper folder. Next:
```
sudo chmod 777 "/My Properties"
```
This will set usable permissions to that folder.

```
gedit "/My Properties/si2.properties"
```
This will bring up a text editor. Paste in those 2 lines and save the file.

Note: I'm really just guessing here, it probably won't work.

---

