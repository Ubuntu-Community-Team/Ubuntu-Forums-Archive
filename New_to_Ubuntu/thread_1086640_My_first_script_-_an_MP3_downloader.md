---
title: "My first script - an MP3 downloader"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Scubdup on 2009-03-04
wget -r -nc -k -np -U Mozilla/5.0 -A.mp3 -e robots=off -w 3 -l 7 --limit-rate=50k --random-wait --restrict-file-names=windows [http://www.website.com](http://www.website.com)

---

### Post by Scubdup on 2009-03-04
I want to download a load of free tunes from a website. The problem is they are scattered around the site and in different directories and some are in WMV format while most are in MP3.

I am new to any kind of programming and Ubuntu and Linux and this seems like a useful introduction task to learn more about Linux. I am trying to find out as much myself as possible but any assistance would be very gratefully appreciated.

I am reading through the Wget Manual and trying to find out how to automate as much as possible so it can all be run from a short command in the terminal.
-------------------------------------------------------------
My specifications are:

I want to automatically (preferably by clicking a button on the desk top or at most by running a short command in the terminal):-

1) Scour a website or directory recursively for files of (a) certain file type(s) ( &#8211; after typing the command I would like to asked to type in the URL.)

2) Create a folder in my home folder called the name of the website/directory

3) Download all files of the specified filetype to the newly created folder.

4) Rename each file with the path of the url where it was found (replacing the &#8220;\&#8221;s with &#8220;_&#8221;)

-------------------------------------------------------------

I need to investigate more about how to automatically create a folder with the name of the website.

I think I can use wget to scour a particular website for specific filetypes:

wget
--recursive \
--no-clobber \
--convert-links \
--no-parent \
--user-agent "Mozilla"
--restrict-file-names=windows \
--level=9 \
--limit-rate=20k \
--wait=3 \
--random-wait \
--accept acclist mp3, wmv \
[www.exampleurl.com/subdirectory/subdirectory/](www.exampleurl.com/subdirectory/subdirectory/)

Or in shorthand:-

wget -rncknp -UMozilla -restrict_file_names=windows &#8211;l9 -limit_rate=20k &#8211;w3 -random_wait=on amp3,wmv [www.exampleurl.com/subdirectory/subdirectory/](www.exampleurl.com/subdirectory/subdirectory/)

I think I can use --include file  possibly in conjunction with something else to automate the process for a list of a  few websites or directories. I need to look into how to incorporate this.

I&#8217;m not sure how to order the process to best rename the files.

I do not know how wget will order the downloads.

If it puts them in a similar directory tree to the website then possibly I can then follow it up with something similar to the code I have been assisted with previously:-

find -name "*.mp3" -print0 | xargs -0 -- rename -v 's|.*/([^/]+)/(.*)\.mp3|/path/to/Music/$1 - $2.mp3|'

-------------------------------------------------------------

As for my script I am very new to this so I am a bit lost to be honest.

Form a tutorial I gather I need to 

First open a terminal and type:
gedit mp3downloader.sh

This will open gedit with a blank file named samplescript.sh. In the file I think I need to type the following:

-------------------------------------------------------------
#!/bin/sh
echo &#8220;MP3 Downloader&#8221;
echo -n "Enter full URL address of website or website subdirectory > "
read text

cd ~
mkdir $text 
cd $text

wget -rncknp -UMozilla -restrict_file_names=windows &#8211;l9 -limit_rate=20k &#8211;w3 -random_wait=on amp3,wmv [URL of Website from Input Request]

find -name "*.mp3" -print0 | xargs -0 -- rename -v 's|.*/([^/]+)/(.*)\.mp3|/path/to/Music/$1 - $2.mp3|'
-------------------------------------------------------------

Then I need to save this file
Next I need to run this command to make the file executable:
chmod +x mp3downloader.sh

To run the script, I need to type this:
./mp3downloader.sh

I&#8217;d like to put a link on the desktop if possible.

---

### Post by Scubdup on 2009-03-04
Unabridged the wget options and added -erobots=off 

-------------------------------------------------------------
#!/bin/sh
echo &#8220;MP3 Downloader&#8221;
echo -n "Enter full URL address of website or website subdirectory > "
read text

cd ~
mkdir $text 
cd $text
```

wget -r -nc -k -np -U Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092416 Firefox/3.0.3 -restrict_file_names=windows &#8211;l9 -limit_rate=80k &#8211;w3 -random_wait=on -A.mp3,.ogg,.wma -erobots=off $text
```

find -name "*.mp3" -print0 | xargs -0 -- rename -v 's|.*/([^/]+)/(.*)\.mp3|/path/to/Music/$1 - $2.mp3|'
find -name "*.ogg" -print0 | xargs -0 -- rename -v 's|.*/([^/]+)/(.*)\.ogg|/path/to/Music/$1 - $2.ogg|'
find -name "*.wma" -print0 | xargs -0 -- rename -v 's|.*/([^/]+)/(.*)\.wma|/path/to/Music/$1 - $2.wma|'
-------------------------------------------------------------

---

### Post by Scubdup on 2009-03-04
> **Scubdup said:**
> I&#8217;d like to put a link on the desktop if possible.

Found [this]("http://ubuntuforums.org/showthread.php?t=348050") which should solve this aspect

[QUOTE=hal10000]A way to get it work may be to create a Desktop Icon:
1. Right click somewhere to your desktop
2. select New--->"Link to Program" (or something similar, translated from german)
3. Give a name you like, then go to "Application", under "Command" chose your shell script (INCLUDING PATH), then choose "Advanced Options" and mark "Run in Terminal", i guess this is the most important part because otherwise you won't be abls to see th output of your script. You may also choose "Do not close when command exits" to prevent the window from being closed immediately after your script ends.[/QUOTE]

---

