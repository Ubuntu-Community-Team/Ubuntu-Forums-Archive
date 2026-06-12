---
title: "Is it possible to import pidgin chat logs to empathy?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by mvalviar on 2009-11-12
If so, how?

---

### Post by mvalviar on 2009-11-13
up

---

### Post by firfin on 2009-11-17
I haven't found a way yet. But should be possible. 
Then again importing your irc should be possible too (yes I have telepathy-idle installed :) )
If I get some spare time on my hands I might write a perl script which would convert pidgin logs to empathy compatible ones. Probably somewhere around 2013 :P

---

### Post by mvalviar on 2009-11-18
Ok. Maybe I'll work on a script too and hopefully finish it sooner. :) First things first: Where can I find empathy chat logs?

---

### Post by Yfrwlf on 2011-01-07
There's always this: [http://jalli.berlios.de/](http://jalli.berlios.de/)

It is supposed to have some bugs though, like issues with converting Facebook chat logs (which I don't have so I don't care), so of course make a backup of everything before doing anything with this Java program.

Empathy logs are in ~/.local/share/TpLogger


P.S.: Jalli didn't work for me, I got "There are no messages to convert!" with html Pidgin log files, and even with Pidgin's old txt log files I get:
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 11
	at Pidgin.readInputFileTXT(Pidgin.java:148)
	at Pidgin.readInputFile(Pidgin.java:86)
	at Jalli.main(Jalli.java:74)

---

### Post by Yfrwlf on 2011-01-07
I've begun writing a Bash shell script to get this all done.

---

### Post by Yfrwlf on 2011-01-10
One problem I've found is that Empathy for some reason uses unique identifier strings for every line of chat in their logs, not to mention just have really confusing info in general...
```
<message time='20110108T03:40:54' cm_id='51558532255bb6abbca087447ada6c0e25cfd793' id='UserAccountOnMyList' name='UserNickname' token='' isuser='false' type='normal'>Hehe</message>
```
No clue why "ususer=false" when they are a legitimate user on my account, or why token=blank for both me and the user, etc.  Most of this stuff may not be needed for just making logs that show up and are searchable in Empathy though.  I may be able to spoof the unique identifier string and have it work.

Anyway, here's just the scaffolding of the script without any actual conversion bits in yet:

```
#!/bin/bash

# If no arguments exist (number of arguments ($#) is less than 1), then print instructions and exit.
if [ $# -lt 1 ]
then
        echo "This script attempts to convert Pidgin TXT log files to Empathy log files."
	echo "Usage: $0 PATH"
	echo ""
	echo "		Examples:"
	echo "		This will find all \".txt\" files in the current directory as well as deeper ones:"
	echo "			$0 ."
	echo "		This example will only find the specified file mylog.txt in the current directory:"
	echo "			$0 mylog.txt"
	echo "		This example will search for all .txt files in your Pidgin log directory:"
	echo "			$0 ~/.purple/logs/"
	echo ""
	echo "All converted files will be stored in their proper directories inside the directory you specify."
	exit
fi

# Get and also count number of ".txt" files in log path specified in 1st argument.
echo "Searching for \".txt\" logs in \"$1\"."
txtlogfile=`find $1 -iname "*.txt" -type f -print`
txtlogcount=`find $1 -iname "*.txt" -type f -print | wc -l`

# If no log files found, exit.  Otherwise, ask for conversion.
if [ "$txtlogcount" = "0" ]
then
	echo "No \".txt\" files found."
	exit
else
	echo -n "$txtlogcount \".txt\" file(s) were found.  Convert? (y/n) "
fi

# If y or Y is entered, proceed.  Otherwise, exit.
read answer1
if [ "$answer1" = "y" ] || [ "$answer1" = "Y" ]
	then echo "Starting log file conversion."
	else echo "Exiting."; exit 0
fi

# Convert txt log files.
for logfile in $txtlogfile
do
	echo "Converting $logfile"
	
done

echo "All log files converted."
```

Any help with the actual conversion would be appreciated as I won't have much time to work on this over the next month.  One needs to be made for converting HTML Pidgin logs as well.  I don't even know if Pidgin still has the option to save as just "text" anymore, but in either case HTML is the default log format now for Pidgin.  Basically, each log file either needs to be copied and then altered with find/replace commands, or the key bits of data need to be found and then spit back out into a new file.  Something like that. :popcorn:

---

