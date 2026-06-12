---
title: "I want to make a script to save a file and open it in vuze"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Kedster on 2009-12-19
I would like to make a small shell script(sorry if that the wrong term, i think its is what I need) that I can tell firefox to use(with the FF file association so that it downloads torrent files to a certain directory and then open them with vuze.

the directory I would like to save the .torrent file to is
```
/home/kedster/Downloads/Torrent_files
```

and the location of where the vuze application is located(liket he file to start vuze)
```
/home/kedster/.vuze/azureus
```

Um I don't have any idea how to do this. Iv done basic things like scrpts to copy a file but i dont really remember how because it was a long time ago. But im going to try and then I hope you guys can help me complete it.
Also I do not know how firefox gives a file.

```
#bash!
echo "filename"
cp filename /home/kedster/Downloads/Torrent_files
run filename /home/kedster/.vuze/azureus
!

```

Ok I really just tryed what ever I could think of, I know it is wrong, One I don't know how to make the echo statement be the file and I don't know how to open a file with a program and umm its just totally pulled from my but and I probly have the opening wrong also.


PS please help me by like telling me terms and stuff needed for making scripts because I would really like to learn how to make scripts.

---

### Post by Barriehie on 2009-12-19
I'm not really knowledgeable about torrent files but **wget** may be the command you're looking for.  You haven't provided any url's but if you go to the terminal and enter 'man wget' you can see if that will work for you.  I use wget weekly in a script to download blacklist files and then the script process' them into my squid proxy server.

Barrie

Edit: I think your 'shebang' line may be off:  #!/bin/bash  :)

Here's the relevant parts of my script:
```

#!/bin/bash
#
# Script to automate blacklist download and squid incorporation.
# The 'blacklist' is downloaded from http://www.shallalist.de, please
# visit the site and read the usage policy.
#
# Usage: blupdate.sh
#


LFILE="/home/barrie/log/blacklist-logfile"
if [ -e $LFILE ]
then
    rm $LFILE
fi


WORKDIR="/home/barrie/squid"
cd $WORKDIR


echo "blacklist-updater $(date +%m)-$(date +%d)-$(date +%Y) $(date +%H%M)" "----- Starting -----" >> $LFILE
wget -t 25 -O /home/barrie/squid/shallalist.tar.gz http://www.shallalist.de/Downloads/shallalist.tar.gz 1>>$LFILE 2>>$LFILE


```

HTH!

---

### Post by Kedster on 2009-12-19
Well what I would like to do is
when I go download a .torrent file from a site on firefox that it will save the .torrent file to ```
/home/kedster/Downloads/Torrent_files
```
 and once downloaded open it with vuze(a bitorrent client i used to download the actual data) and it is 
```
/home/kedster/.vuze/azureus
```

One big problem is u dont know how firefox Gives the file to a program is anyone knows what i mean.

---

### Post by Barriehie on 2009-12-19
> **Kedster said:**
> Well what I would like to do is
when I go download a .torrent file from a site on firefox that it will save the .torrent file to ```
/home/kedster/Downloads/Torrent_files
```
 and once downloaded open it with vuze(a bitorrent client i used to download the actual data) and it is 
```
/home/kedster/.vuze/azureus
```

One big problem is u dont know how firefox Gives the file to a program is anyone knows what i mean.

Ahh, so what we need to do is check if a file exists in your dl directory and then open it with azureus.  I've got a bit of a hack of a boot daemon that does the same thing with dl'ed images.  Every so often it checks a dir. for *.jpg and then renames and moves the file.  Instead of renaming and moving you want it to move/open???  Would have to move it so it won't open multiple instances of the same file.

Barrie

---

### Post by Kedster on 2009-12-19
I think that it will work. I don't know how exactly (dont really know how deamons work) like I was hoping to set firefox to "Open With" my script which would make a copy of the file put it in the folder specified and then open it in vuze.

Because when u tell firefox to "open with" it saves a copy in the temp if i am correct and then opens it with with a program. Well i want a script that will then make a copy and then open it vuze. (i know its confusing I am just getting an understanding of what firefox does now though.

---

### Post by sgosnell on 2009-12-19
You can tell Firefox to open the torrent file with vuze easily enough, through Edit/Preferences/Applications.  It won't move the file, though, but you should be able to save it wherever you want from vuze.  If the point of the exercise is just to learn scripting, then you should be doing more studying.  Put "linux shell scripting tutorial" into a search engine and you'll find a number of tutorials on this.

---

### Post by Kedster on 2009-12-19
well the problem is that i would like to have a copy of the .torrent file(like the tracker file) so i can use it again. otherwise i would do that. I use a private torrent site that u need a certain ratio or u can not download anymore. and i wold like to have the torrent files to i can seed different things when needed. And to keep track of other stuff for personal records.

---

### Post by Kedster on 2009-12-19
I think iv figured out a more direct summery of what i need

I need a script that will open a file make a copy of that file in a certain directory and then open it in anther program

---

### Post by Barriehie on 2009-12-19
Okay, here's my script for checking for a dl'ed .jpg file and if found it renames it then moves it.  Remember I said this was a hack!  but, it works so I"m not inclined to 'fix it'! :)

Also, in regards to learning bash [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
```

#!/bin/bash

#touch /var/run/picsdaemond.pid
echo $$ > /var/run/picsdaemond.pid

#
#  Variable Setup
#
LOOPER="TRUE"
OLDDIR="/home/barrie/Desktop/temp/pics/"
NEWDIR="/home/barrie/Pictures/SS/tmp/"
declare -a CHARSARRAY=( 'a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9' )
declare -a CHARS
declare -i NUMBER=0
declare -i LOOPCOUNTER=0

cd $OLDDIR

while [ "$LOOPER" = "TRUE" ]
do

    find /home/barrie/Desktop/temp/pics/ -name *.jpg 1>/home/barrie/Desktop/temp/pics/go 2>/dev/null

   if [ -s $OLDDIRgo ]
   then

	rm /home/barrie/Desktop/temp/pics/go

	for file in *
	do
	    while [ $LOOPCOUNTER -lt 10 ]
	    do
		RANDOM=$(date +%N)
		NUMBER=$((RANDOM%62+1))
		CHARS[$LOOPCOUNTER]=${CHARSARRAY[$NUMBER]}
		LOOPCOUNTER+=1
	    done
	    LOOPCOUNTER=0         # ----------------------------- Reset name length counter
	    NEWFILENAME=${CHARS[0]}${CHARS[1]}${CHARS[2]}${CHARS[3]}${CHARS[4]}${CHARS[5]}${CHARS[6]}${CHARS[7]}${CHARS[8]}${CHARS[9]}.jpg

        mv $OLDDIR$file $NEWDIR$NEWFILENAME

        declare -a CHARS=  # ----------------------------- Reset CHARS array

	done               # ----------------------------- End of for file in
    else
	sleep 5
    fi
#
# Check for stop file
#
if [ -e /home/barrie/Desktop/temp/jobs/stopics ]
then
    rm /var/run/picsdaemond.pid
    rm /home/barrie/Desktop/temp/jobs/stopics
    exit 0
fi

sleep 60                   # ----------------------------- Pause, load break!

done                       # ----------------------------- Infinite loop, never exit

```

And the file that launches picsdaemond is picsdaemon.  This is located in /etc/init.d and the symlinks for starting it are created with update-rc.d

```

#!/bin/sh

#
# Start picsdaemond daemon that renames and moves
# downloaded .jpg files.
#


bash -c /home/barrie/bin/daemons/picsdaemond 1>/dev/null 2>/dev/null &

exit 0

```

Barrie

---

### Post by Barriehie on 2009-12-19
This should get you started, note that you didn't specify a dir to move the files to so right now with this script they are put in your home dir.
The marker for go file is put on the Desktop and it should spawn an instance of azureus when a file is detected, unfortunately it will do this for EVERY file it finds.  I don't know if azureus has any type of client/server scenario going on to eliminate this behavior.

You should go over the directories used carefully!  This WILL break if they are incorrect.

Barrie

```

#!/bin/bash

LOOPER="TRUE"
DLDIR="/home/kedster/Downloads/Torrent_files"
MAKECOPYDIR="/home/kedster/"                     # This dir wasn't specified in your posts

cd $DLIR

while [ "$LOOPER" = "TRUE" ]
do

    find $DLDIR *.torrent 1>/home/kedster/Desktop/go 2>/dev/null

   if [ -s /home/kedster/Desktop/go ]
   then
	rm /home/kedster/Desktop/go
	for file in *
	do
            mv $DLDIR$file $MAKECOPYDIR
            sh -c /home/kedster/.vuze/azureus $MAKECOPYDIR$file
	done                                     # End of for file in
    else
	sleep 5
    fi
#
# Check for stop file
#
if [ -e /home/kedster/Desktop/stopics ]
then
    rm /home/kedster/Desktop/stopics
    exit 0
fi

sleep 60                   # ----------------------------- Pause, load break!

done                       # ----------------------------- Infinite loop, never exit

```

Edit: Almost forgot!  If this works in a dry run then you can make a launcher file, like my prior post, that goes in /etc/init.d and that one calls this one.  Right now I *think* this file will run in a terminal, the & at the end of the line in the calling file will put this one in the background so the only way to 'see it' will be via *ps*, *top*, or the *system monitor*, or any other similiar utility.

---

### Post by Cheesemill on 2009-12-19
Can't you just tell Vuze where you want it to save a copy of the .torrent file?

This is an option in a lot of the clients I've used - Deluge, uTorrent, and more importantly I'm sure it was an option in Azeurus (the old Vuze).

I've never used Vuze myself so I couldn't tell you where to look (it's way too memory hungry and bloated for a torrent client IMHO).


Edit - First result: [http://lmgtfy.com/?q=vuze+save+.torrent+location](http://lmgtfy.com/?q=vuze+save+.torrent+location)

---

### Post by Kedster on 2009-12-19
I FEEL LIKE A REALLY BIG FOOL:( 
Im sorry everyone that helped me 
cheesemill is right and makes this so easlol 

and that site is pretty cool ill have to remember that one.

---

### Post by sgosnell on 2009-12-19
What's wrong with Transmission?  It has a nice GUI, lets you set the default destination folder among other things, and doesn't use crappy java.  Does vuze do something other than manage downloads?  I've never tried it, because I don't like using java, which is slow as molasses in January doing anything.  Transmission is the default bittorrent client, and should run automatically when you click on a torrent file.

---

### Post by Cheesemill on 2009-12-19
Personally I prefer Deluge, it's still lightweight but gives you much more control over your torrents than Transmission.

---

### Post by Barriehie on 2009-12-19
Glad you figured it out!

Barrie

---

