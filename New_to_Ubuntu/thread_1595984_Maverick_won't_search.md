---
title: "Maverick won't search"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-10-13
Since the upgrade to Maverick I can't search for files. I can type guitar which I have hundreds of files and nothing or one file comes up. In Lucid I could quickly find any file. I also installed Tracker and same result. I really liked the search capability in Lucid but how did it get broken? When I navigate to a folder and hit the magnifying glass search it jumps back to nautilus and nothing is found.

---

### Post by jtarin on 2010-10-13
The GUI applications are fine in some instances but they don't compete with the commandline tools for finding files. One that I have used for years to find any file on my computer is "slocate" or "locate". First in the terminal enter ```
sudo updatedb
``` this will take a little time to run if you have never run it before then when itis finished enter ```
sudo locate <filename> 
```where <filename> is the name of the particular file you are looking for. If you come up with to many entries that fill the screen you can use the command ```
sudo locate <filename> |more 
```then use your Enter or down arrow key to navigate page at a time. See "man locate" (enter in terminal) for more information.

You can also use [Grep]("http://www.panix.com/~elflord/unix/grep.html") another commandline tool to locate particular strings of text within a file.

---

### Post by cmcanulty on 2010-10-14
I just want the regular file search back. There was a binoculars on left of every  folder toolbar and it worked great and fast. Now there is a magnifying glass and when you hit enter it jumps from folder I'm in to nautilus and shows no results for any search. I don't know what search app it was it just seemed to be built in.

---

### Post by jtarin on 2010-10-14
Binoculars are now a magnifying glass. If you feel the older version of Nautilus more to your liking I would imasgine you will have to revert to the older version.

---

### Post by migs73 on 2010-10-14
> **cmcanulty said:**
> I just want the regular file search back. There was a binoculars on left of every  folder toolbar and it worked great and fast. Now there is a magnifying glass and when you hit enter it jumps from folder I'm in to nautilus and shows no results for any search. I don't know what search app it was it just seemed to be built in.
In my system, when I follow your instructions I get the same results, but only if what I am searching for is not in the current folder. Then you must select a location form the drop down menu on the left of the search window (which will display the current folder to start with), change it to where you would like to search and then click, reload.
Have you tried this and still don't return any search hits?

---

### Post by cmcanulty on 2010-10-14
OK here are 4 screenshots the first is my guitar folder the second is what happens when I hit the search magnify icon it immediately jumps to nautilus the 3rd is the zippo results, I looked but find no dropdown box.The 4th is the results justs jumps to  another folder
New info if I go to places"search for file" it works but not from any folder is this a new and worse upgrade?

---

### Post by migs73 on 2010-10-14
Wow, have I just been on a journey. I tried to see why your nautilus looked so different to mine, found nautilus-elementary which I installed and tried.
My nautilus then looked very similar to yours (slider in bottom corner/buttons for list,icon views) and other things. When I tried to search in this I reproduced you problems. 
I then spent a good while (1 1/2 hrs)trying to undo what I did!!! Anyway done now.
So did you ever install Nautilus-elementary?

---

### Post by cmcanulty on 2010-10-14
Not that I know of maybe I'll try reinstalling nautilus or would that do a major breAK OF SYSTEM? Also is it possible?

---

### Post by beew on 2010-10-14
Go to Applications > System Tools > Configuration Editor*  Open it and then on the left panel choose apps > gnome-search-tool.  Then check "disable quick search" on  the right panel and it should work.

Don't ask me why, this seems rather counter intuitive. I think maybe "quick search" uses some kind of indexing and without that it would just search forever without finding anything.

* if you can't find Configuration Editor in the drop down menu just go to System > Preference > Main Menu, open it and choose System Tools on the left panel and you should see " Configuration Editor" on the right. Check the box and you will find it in the Applications > System Tools menu.

---

### Post by migs73 on 2010-10-15
> **beew said:**
> Go to Applications > System Tools > Configuration Editor*  Open it and then on the left panel choose apps > gnome-search-tool.  Then check "disable quick search" on  the right panel and it should work.

Don't ask me why, this seems rather counter intuitive. I think maybe "quick search" uses some kind of indexing and without that it would just search forever without finding anything.

* if you can't find Configuration Editor in the drop down menu just go to System > Preference > Main Menu, open it and choose System Tools on the left panel and you should see " Configuration Editor" on the right. Check the box and you will find it in the Applications > System Tools menu.

That sounds more plausible, why didn't you answer before I screwed up my Nautilus ;)

---

### Post by cmcanulty on 2010-10-15
Thanks I tried that but it didn't change anything any other ideas? This started with the 10.10 upgrade fine 2 days ago.

---

### Post by migs73 on 2010-10-15
> **migs73 said:**
> Wow, have I just been on a journey. I tried to see why your nautilus looked so different to mine, found nautilus-elementary which I installed and tried.


Can anybody explain this difference in appearance? (I'll post a screenshot of mine when I am on my Ubuntu Machine)

---

### Post by migs73 on 2010-10-15
Here is a screenshot of my Nautilus, no zoom slider, no buttons for selecting icon/list layout. BUT a working search function.

EDIT; BTW some of the music is my wifes !!! Honest!

---

### Post by cmcanulty on 2010-10-15
I sure hope I can get my search back, I tried several addon searches but want just the built in one.I would like to reinstall nautilus but am afraid to try that until someone tells me it won't crash my whole setup.
In case this helps I am putting a copy of my .nautilus-terminal.conf file below, is there something weird with it?

```
#Configuration written by Nautilus Terminal
#Please edit with caution

[GENERAL]
	starthidden = No
	showscrollbar = No
	defheight = 7
	command = "/bin/bash"
	cursor = 0

[COLOR]
	text = "#159007570757"
	background = "#f8ecf68ef68e"
	palettename = "Tango"
	palette = "#000000;#cc0000;#4e9a06;#c4a000;#3465a4;#75507b;#06989a;#d3d7cf;#555753;#ef2929;#8ae234;#fce94f;#729fcf;#ad7fa8;#34e2e2;#ffffff"

[FONT]
	name = "monospace 10"
	allowbold = Yes

[FOLDERS]
	showinall = No
	path = "/"

```

---

