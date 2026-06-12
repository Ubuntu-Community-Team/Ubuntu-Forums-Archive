---
title: "nautilus_scripts and terminal"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by weamdemonkey on 2009-02-01
Hi all, I'm a beginner at making bash scripts and am trying to make a script to convert wma files to mp3 using ffmpeg.

so far to keep it simple iv just got a script that finds every wma file in the current directory and outputs the file name with .mp3 instead of .wma, this was just to prepare the output file parameter for ffmpeg.

I'd like the script to open a terminal window and run the command just so i can see whats going on and deal with any prompts.

so far i have :
```
#!/bin/bash
gnome-terminal -x bash -c "for i in *.wma
do
NEWFILE=$(basename \"$i\" .wma)
NEWFILE=$NEWFILE.mp3
echo $NEWFILE
done
read -n1"
```

but running this from a terminal or from right clicking and selecting the script just echos blank lines (depending on however many wma files there are in the directory)

if i type :
```
for i in *.wma
do
NEWFILE=$(basename "$i" .wma)
NEWFILE=$NEWFILE.mp3
echo $NEWFILE
done
```

straight into a terminal then it works fine and outputs each file name with a .mp3 extension and no .wma
I would guess that means that section is ok, so am i opening the terminal window incorrectly? 
It looks like its finding the files fine but the "for i in *.wma" isnt putting the file names in $i

I've made a loop that opens a terminal window and converts the files individually but then i end up with several terminals open crowding the screen and trying to run all at once, I'd like to convert each file one after the other in the same window.

thanks for any help, Martin

---

### Post by blueridgedog on 2009-02-01
This might get you moving in a different direction:

```
#!/bin/bash
for i in *.wma
do
NEWFILE=$(basename $i .wma)
NEWFILE=$NEWFILE.mp3
gdialog --title "New Name" --msgbox $NEWFILE 200 450
done
```

I saved this as test.sh in the scripts directory and make it executable.

What i changed in yours was not trying to bring up a terminal and then run a command and to display the output you are getting with gdialog.  This is very rough, but it works.

---

### Post by weamdemonkey on 2009-02-01
Hi blueridgedog,

I tried the code you gave and i think i have made a step in the right direction. iv currently got :
```
#!/bin/bash
for i in *.wma
do
NEWFILE=$(basename "$i" .wma)
NEWFILE=$NEWFILE.mp3
gdialog --title "New Name" --msgbox $(ffmpeg -i "$i" -ab 128K "$NEWFILE") 200 450
done
```

this converts a file then pops up the gdialog box (although at the moment all it says is 200) and doesn't start converting the next file till i click ok so I think I'm half way there.

I hoped using --msgbox $(command) would work like the NEWFILE=$(basename "$i" .wma) and would display the output of the command like a variable but this didn't seem to work. as i said it just gives a box saying 200.

The reason i wanted the output was in case there's a problem like the name of the output file is an already existing file so ffmpeg will prompt either a y or n to overwrite or stop(at the moment when that happens it just pops up the 200 again).

looking at the gdialog documentation I don't think i can respond like this using the yesno box or any of the options.

I think now I'll have a look at the ffmpeg documentation though. I guess i should be able to choose the output to use instead of stdout if there's an error message. Or maybe there's a way I can just pipe the entire output to a gdialog box.

thanks for your help, Martin

---

### Post by blueridgedog on 2009-02-01
I don't have any wma files to try this on, so it may choke:

```
#!/bin/bash
for i in *.wma
do
NEWFILE=$(basename "$i" .wma)
NEWFILE=$NEWFILE.mp3
if gdialog --yesno "Create $NEWFILE ?" 200 450
	then ffmpeg -i "$i" -ab 128K $NEWFILE
	else gdialog --msgbox "Action Canceled"
fi
done
```

---

### Post by mc4man on 2009-02-01
Note: this isn't any suggestion for a nautilus script, (I'd actually tried in the past but being more of a trial and error person could only get either the terminal to open at the proper prompt but the command wasn't run or a 'failed to execute child process'

In any event with the r.click 'open in terminal' it was just as easy to put some scripts that do work in my home dir., and point to there from the terminal prompt. (~/scriptname

As far as any potential problems with duplicate names ffmpeg will by default stop and ask if it should overwrite if they're found, so no need to script for that.

This always worked fine for normal .wma (red is adjustable, the mv is optional

```
#!/bin/bash
for f in *.wma; do ffmpeg -i "$f" -acodec mp3 -ab [COLOR="Red"]256[/COLOR]k "${f%.wma}.mp3"; done
mv *.mp3 ~/Music/mp3
```

For lossless wma ffmpeg doesn't work so I'd convert to .wav first in mplayer
(maybe could be cleaned up , thru T&E it worked so I stopped there

```
#!/bin/bash
for f in *.wma; do mplayer -ao pcm:waveheader:file="${f%.wma}".wav "${f%.wav}"; done
```

Would be curious to see how you get either of these 2 conversions to work from a nautilus script

---

### Post by blueridgedog on 2009-02-01
I have also used the following:

```
mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader mysong.wma && lame -m s audiodump.wav -o mysong.mp3
```

Note that it lacks the for loop to process files automatically, but based on the concepts discussed, it could be added.  I was mostly helping to get the nautilus integration, but If I was to write it from scratch, I would use the above code with the variables and for loop we have been touching on.

Perhaps if we get something worked up, we can finalize it for others to use.

---

### Post by mc4man on 2009-02-01
i had noticed as a 'nautilus script' all the scripts would work if you r. clicked inside the directory. In that case though i could never find a way for a terminal to open, the process would just run in the background.

I actually wanted to be able to just r. click on the dir. itself and have it run in a visible terminal. (and so settled on opening a terminal at the dir. prompt and running the 'normal' script.

> ffmpeg will by default stop and ask
only when run in a visible terminal, when run in background will just skip, so then you'd need a pop up I gather

---

### Post by weamdemonkey on 2009-02-03
Hi mc4man and blueridgedog,
   Sorry for a slight delay in this reply but i think I've got everything up and running now thanks to your suggestions.
   Like mc4man suggested about using a script to open a terminal and then just point it to another script to run the commands I've now got ffmpeg running with all the necessary output/prompts going to the terminal window. it also loops through each file in 1 terminal instead of 1 terminal each which is just what i was aiming for.

   Here's the code i used

   In the ~/.gnome2/nautilus-scripts folder : 
```
#!/bin/bash
gnome-terminal -x bash -c "\"/***path to wherever you place the second script***/terminal convert all wma to mp3\""
```

   And then in the ***path to wherever you place the second script*** folder : 
(the first file references this under the name "terminal convert all wma to mp3")
```
#!/bin/bash
for i in *.wma
do
NEWFILE=$(basename "$i" .wma)
NEWFILE=$NEWFILE.mp3
echo $NEWFILE
ffmpeg -i "$i" -ab 128k "$NEWFILE"
done

```

   Also as blueridgedog suggested you could maybe put something together for other users.
   Having a look at the gdialog manuals/help it looked like its actually some kind of basic version of "zenity" which had the option to create a progress bar
   Its a bit basic at the moment but I've got a script that runs ffmpeg in the background. while its looping through each file it checks if it already exists and if it does then it prompts either yes or no to overwrite or if it doesn't exist just goes ahead without prompting.
   It also shows an overall progress bar (based on the number of files and number of files complete, not the progress of each file) and then pops up at the end when its finished.

I've commented what i thought might be necessary but i hope this comes in handy for other people, its certainly nicer looking than dumping everything to a terminal
```
#!/bin/bash

#calculate how many wma files
noofWMA=0
for i in *.wma
do
noofWMA=$(($noofWMA+1))
done

#workout how much progress bar should increase
#with each wma file converted
progressJump=$((100/$noofWMA))
currentProgress=0

#begin main loop to convert each file/update
#progress bar
(for i in *.wma
	do
	#create output file name
	NEWFILE=$(basename "$i" .wma)
	NEWFILE=$NEWFILE.mp3
	#if output file already exists prompt wether or
	#not to overwrite it and act accordingly
	if [ -f "$NEWFILE" ]
		then
		if gdialog --yesno "Overwrite $NEWFILE ?" 200 450
			then 
			ffmpeg -i "$i" -ab 128k -y "$NEWFILE"
			else 
			gdialog --msgbox "Action Canceled"
		fi
		else
		ffmpeg -i "$i" -ab 128k "$NEWFILE"
	fi
	#calculate current progress and update progress bar
	currentProgress=$(($currentProgress+$progressJump))
	echo $currentProgress
done) | zenity --progress  --text="Converting ..." --percentage=0

#let user know conversion is complete
gdialog --msgbox "File conversion complete" 200 450
```

   While looking at the zenity docs it looks like it has a few more options for the type of window to create and options for input/output. The next thing I think I'd try now is to have it pop up at the start asking for the input file type and output so you can choose between many. Like a basic GUI for music conversion in ffmpeg...but many thanks again to both of you for helping me solve this one.

---

### Post by blueridgedog on 2009-02-04
Excellent work.  I think most people wanting to integrate shell scripting with gnome will benefit from this thread.  I use something similar to your final product to convert audio books.

---

