---
title: "need to search multiple .doc files for specific text"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by stinger30au on 2010-05-19
i have a directory full of .doc files that were created over the years by open office


theres a specifice number im trying to find in the files, the number is 185523


i have searched and found a program called "searchmonkey" and it is installed like this

sudo apt-get install searchmonkey


when i point it to to directory and tell it to search in files and type this number it wont find anything


if i click places, search for files, click more options and in the "contains text" i type in 185523

it also says there is no file that contains this number


*HOWEVER*

if i share the directory across the network via samba and i then use windows xp and i map this as a network drive and i use the windows search it will search the files for the specific number of 185523 and it even finds the file

the file is not hidden

so i dont understand why ubuntu 10.04 is having such a hard time trying to find it on my pc


any ideas?

(i dont know if it makes any difference or not, but the file names have spaces in them)

---

### Post by stinger30au on 2010-05-20
well how silly is this


i have spent all day since i posted this trying to find and answer

dont get me wrong, theres plenty of answers around that say to fire up shell and run the command "grep" and it will find the string of numbers i want


well for the life of me it wont find the string i want


*HOWEVER*

i have just had a break thru and found if i install wine and then a windows program called

agent ransack
[http://www.mythicsoft.com/page.aspx?page=screenshots&type=agentransack](http://www.mythicsoft.com/page.aspx?page=screenshots&type=agentransack)

it will do *EXACTLY* what i want

crazyness

anyhow...hope this might help someone else

---

### Post by stinger30au on 2010-05-20
ah ha!!!

looks like grep doesnt like the format the files are in


if i fire up shell and cd to the directory where the files are and i do this

grep 1.8.5.5.2.3 *.doc

it works and finds the file!

mmmmmmmmmmm..... interesting

but if i type in

grep 185523 *.doc

it finds nuffin

or if i do 

grep "185523" *.doc

it also finds nuffin

---

### Post by stinger30au on 2010-05-20
i have just converted a ton of the .doc files to .odt files and no joy, still wont find it


however i did get a message from a clever linux person

if i fireup shell and type this


less myfile.doc

and ignore the binary warning, the words have extra characters added to them like "@" etc


apparently this means they are 16 bit words, thats why it works when i add the "." when i search with grep



interesting

---

### Post by jvector on 2010-05-20
OpenOffice stores its files by default in either its native 'open' .odt format, or in .doc format if you want to be able to pass the doc to Microsoft Word. 

Both .odt and .doc formats are binary formats that contain not just the text you wrote but also font encoding info etc. SO you can't generally use traditional Linux text-handling tools like grep, cat, etc. on a .doc or .odt file because the content is not just the plain Ascii text. That's why your attempts with 'grep 185223 *.doc' did not give you a result. [1]

*However*, there is a commandline tool called 'antiword' which will read a .doc file and give you the plain text content.

```
sudo apt-get install antiword
for i in *.doc; do
antiword $i | grep 185223 && echo Found in $i
done

``` 
(That code runs each .doc file through antiword, and seraches for your text 185223. If it's there, it shows you the text and tells you the file.)


[1] [Incidentally, the second thing you tried, 'grep "185223" *.doc', does not buy you anything. But if you had special characters in your search, say 'grep "$150,000.00" *.doc' then using the quotes would stop the shell 'interpreting' your dollar and period characters.]

---

