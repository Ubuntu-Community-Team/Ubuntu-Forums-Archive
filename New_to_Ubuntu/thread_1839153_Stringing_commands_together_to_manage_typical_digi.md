---
title: "Stringing commands together to manage typical digital photo operations"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by rocksockdoc on 2011-09-05
Can those more knowledgeable than I help me improve the to-be-written script described below?

My ten typical digital photo operations, in preparation for mailing to friends & family, which I presume are somewhat ubiquitous, are the following:

[LIST=1]
[*]I create an empty directory on the hard disk drive titled by date
[LIST]
[*]e.g., mkdir /data/pic/20110904
[*]Note: I should make this automatically figure out the date from the 'date' command.
[/LIST]
 
[*]I copy the flash card JPG contents to the hard disk drive
[LIST]
[*]e.g., mv /media/NIKON D5000/DCIM/100D5000 /data/pic/20110904/big
[*]Note: I'm not sure if the Nikon flash card folder will always be the same name or not.
[/LIST]
 
[*]I rotate the large JPG files according to EXIF orientation tags
[LIST]
[*]e.g., exiftran -ai *.JPG
[*]or, jhead -autorot *.JPG
[/LIST]
 
[*]I rename the large JPG files based on EXIF date & time data
[LIST]
[*]e.g., for i in $(ls *.JPG); do exiv2 -r '%Y%m%d-%H%M%S-:basename:' rename $i; done
[*]Note: This creates file names of the format: 20110904-141904-DSC_1001.JPG
[*]I should probably figure out how to get rid of the "DSC_" part as it adds no value.
[/LIST]
 
[*]I create a directory to hold the shrunken JPG files (suitable for mailing out)
[LIST]
[*]e.g., mkdir /data/pic/20110904/small
[/LIST]
 
[*]I shrink the JPG files to 640x480 pixels at any desired % quality (and/or to about 100KB in size)
[LIST]
[*]for f in *.JPG; do convert -resize 640x480 -quality 90 $f ../small/shrunk_$f; done
[*]This creates file names of the format: shrunk_20110904-141904-DSC_1001.JPG
[*]Note: I can't figure out how to ensure they will be smaller than a certain file size.
[/LIST]
 
[*]I add a white caption plate of about 100 pixels wide for later captioning
[LIST]
[*]e.g., for f in *.JPG; do convert $f -bordercolor white -gravity south -splice 0x100 $f; done
[*]Note: This bottom captioning plate must be added only after auto-rotation.
[/LIST]
 
[*]I create a common set of sub folders for mailing purposes
[LIST]
[*]e.g., mkdir 20110904/small/{family,friend}
[/LIST]
 
[*]I step through the small picture set selecting the best photos to copy to the to-be-emailed subfolders
[LIST]
[*]e.g., feh *.JPG -F --cycle-once --action1 "cp %f ./family/%n" --action2 "cp %f ./friend/%n" --action3 "cp %f ./family/%n; cp %f ./friend/%n"
[*]As I view each picture in turn:
[LIST]
[*]Space bar advances to the next photo
[*]Backspace repeats the previous photo
[*]1 copies the file to the 'family' subfolder
[*]2 copies the file to the 'friend' subfolder
[*]3 copies the file to both the friend and family subfolders
[*]Control + delete will delete the current file
[/LIST]
 
[/LIST]
 
[*]I caption the pictures, ad hoc, for that personal touch in the results.
[LIST]
[*]e.g., for f in *.JPG; do kolourpaint $f; done
[*]Note: I caption and annotate each picture, as needed, & then save the new file & close kolourpaint (whereupon the next file pops up in kolourpaint, to repeat the process).
[/LIST]
 
[/LIST]
I'm not a programmer so, before I string these ten commands into a single script, may I ask for advice from those of you more experienced than I in these scripting matters?

---

### Post by dethorpe on 2011-09-27
Looks like you've got most of what you need already. If all the individual commands are Ok from the command line just go for it and create a script, there are many general bash tutorials on the web that will help.
 
Just a few points:
 
Create some test driectories with just a few files for testing and use those until happy it all works OK and creat the script one step at a time, get that working then move on to the next step.
 
1. To get date: date=$(date +%Y%m%d)
Maybe test if directory already exists using [[ -d <dir> ]] if so exit so you can check and remove it
 
2. Should by cp not mv, unless you want to delete the files from your flash card, but i wouldn't do that until happy all the copying and converting has worked at the end of the script. Can check source directory exists and prompt for it if not using if [[ -d "dir name" ]], although generally i think the name will stay the same.
 
4. Don't use ls to get file names let bash do it same as you've done later, and quote filename variables to handle any with spaces in:
for i in *.JPG; do exiv2 -r '%Y%m%d-%H%M%S-:basename:' rename "$i"; done 
 
6. Quote variables containing filenames, same as 4
 
7. Quote variables containing filenames, same as 4
 
10. Quote variables containing filenames, same as 4
 
In general add error checking for directories existing and commands failing where approbriate.
 
Good luck, post any specific problems with actual code samples, error messages and description of directory layout/contents and you should get plenty of help.

---

### Post by rocksockdoc on 2011-10-28
> **dethorpe said:**
> Just a few points

Thanks for your advice. I kept trying a script but it kept screwing up so I put that on hold and I still do the work manually. Sigh. I have to get back on that project.

BTW, I've added the ability to create animated GIFs out of the JPEG files:
```
convert -delay 100 -loop 0 image*.jpg animation.gif
```

And, I've installed a graphical program to make panoramic images out of the photos:
```
sudo apt-get install hugin
```

---

### Post by rocksockdoc on 2011-11-03
Here is my dumb (for now) strung-together sequence:

```

**# The Nikon card directory is always called "DCIM" ... **
cd DCIM
**# We don't want to mess with the originals other than to rename and re-orient them ... **
# One bug here is that the directory won't always be called 100D5000, it may be 101D5000, 102D5000, etc., depending on the # of photos on the flash card.
mv 100D5000 big
cd ./big
**# We orient the originals based on the EXIF orientation tag ... **
jhead -autorot *.JPG
**# We rename the originals based on EXIF date (would like a shorter unique basename) ...**
for i in $(ls *.JPG); do exiv2 -r '%Y%m%d.%H%M%S.:basename:' rename $i; done
**# Now it's time to make smaller editable copies for sending to friends & family ... **
mkdir ../{small,print}
for f in $(ls *.JPG); do convert -resize 640x480 -quality 90 $f ../small/$f; done
cd ../small
**# Add a white border to provide an area to caption for friends & family to enjoy ... **
# Note: We resized BEFORE we added the caption so that the visible photo remains at 640x480 pixels
for f in *.JPG ; do convert $f -bordercolor white -gravity south -splice 0x100 $f; done
mkdir -p email/{family,friend,junk}
** # First pass, look at each photo, & copy to specific directories for further action ... **
# [1] = To be considered for sending to family
# [2] = To be considered for sending to friends (I never use plural directory names)
# [3] = Consider for both friends and for family
# [4] = Save to be printed later (actually to be reconciled with the original for printing of the original)
# [5] = Delete as junk 
feh *.JPG -F --cycle-once --action1 "cp %f ./email/family/%n" --action2 "cp %f ./email/friend/%n" --action3 "cp %f ./email/family/%n; cp %f ./email/friend/%ns" --action5 "mv %f ./junk/%n" --action4 "cp %f ../print/%n"
** # For each intention, it's now time to cull down the photos to the bare minimum**
# [DEL] = the delete key will delete the copy and remove it from consideration
# [SPACE] = this will allow you to move back and forth between similar photos to further cull out similar photos
# [BACKSPACE] = this will allow you to move back and forth between similar photos to further cull out 
cd ./email/family
feh *.JPG -F --cycle-once
cd ../friend
feh *.JPG -F --cycle-once
**# Now it's time to add the captions to the short set of photos for emailing out**
# Note: Kolourpaint has the easiest captioning of the freeware photo editing tools.
cd ./email/family
for f in *.JPG ; do kolourpaint $f; done
cd ./email/friend
for f in *.JPG ; do kolourpaint $f; done
# OK. Mail away!
mail -s "Photos of the kids" family_alias < ./email/family/*.JPG
mail -s "Photos of the kids" friend_alias < ./email/friend/*.JPG
# Exit gracefully
exit 0

```

---

### Post by WasMeHere on 2011-11-03
Hi rocksockdoc,

I am following your progress, and when I have the time, I will try to help you with some debugging and/or tips.

Have fun finding out :-)
Olle

---

### Post by nothingspecial on 2011-11-03
Well, you've got bash pitfalls #1 and #2 in there.

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

```
for i in $(ls *.JPG)
``` should just be ```
for i in *.JPG
```

and you need to quote your variables.

Read the pitfalls and also the guide

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

Keep us posted :)

---

### Post by rocksockdoc on 2011-11-20
> **nothingspecial said:**
> Well, you've got bash pitfalls #1 and #2 in there

Thanks for the advice.

I easily fixed bash pitfall #1 (i.e., for i in *.JPG).

But pitfall #2 (quoting the variables) is a bit tougher to resolve because of quotes inside of quotes in some of the command lines.

So, for now, since none of my files have spaces in them, I simply quoted the variables that were outside of quotes from the start. That's at least some improvement.

Now I'm working on the emailing part (the penultimate step below); and will try to improve little by little.

Here is the latest incarnation (commented for readability):
```
# The Nikon flash card top-level is apparently always titled "DCIM" ... 
cd DCIM
# We don't want to mess with the originals other than to rename & re-orient.
# Bug: The directory won't always be called 100D5000 (depends on # of pics).
mv 100D5000 big
cd ./big
# Auto-rotate the originals based on their EXIF orientation tag ... 
jhead -autorot *.JPG
# Rename the originals to unique names based on their EXIF time/date tag ...
# Bug: Need a shorter base given EXIF time/date tags aren't necessarily unique
for i in *.JPG; do exiv2 -r '%Y%m%d.%H%M%S.:basename:' rename "$i"; done
# Create a set of standard directories to place shrunken files in ... 
mkdir -p ../small/email/{family,friend}
# Shrink the files to a desired size & quality to place in the small directory
for i in *.JPG; do convert -resize 640x480 -quality 90 "$f" ../small/"$f"; done
cd ../small
# Add a bottom border to provide an area to caption for friends & family to read ... 
for f in *.JPG ; do convert "$f" -bordercolor white -gravity south -splice 0x100 "$f"; done
# Cycle thru the pictures to copy to relevant folders for further handling ... 
#  1 => copies files to be captioned for emailing to family
#  2 => copies files to be captioned for emailing to friends
#  3 => copies files to be captioned for emailing to both family & friends
# [DEL] = the delete key will delete the file & move to the next picture
# [SPACE] = will move to the next photo without further action upon the file
# [BACKSPACE] = will move to the prior file for reconsideration for action
feh *.JPG -F --cycle-once --action1 "cp %f ./email/family/%n" --action2 "cp %f ./email/friend/%n" --action3 "cp %f ./email/family/%n; cp %f ./email/friend/%n"
# Manually add captions using the text editing of the Kolourpaint pgm ...
for f in ./email/family/*.JPG ; do kolourpaint "$f"; done
for f in ./email/friend/*.JPG ; do kolourpaint "$f"; done
# Mail the entire set under each folder to family & friends 
# Bugs: Need to mimencode each JPEG & attach as separate inline JPEGs with the correct content-type so that the recipients mail user agent can easily decode the JPG files in line:
vi /tmp/family_email_body.txt
mutt -s "Photos of the kids" -a ./email/family/*.JPG family_alias < /tmp/family_email_body.txt
vi /tmp/friend_email_body.txt
mutt -s "Photos of the kids" -a ./email/friend/*.JPG friend_alias < /tmp/friend_email_body.txt
# Exit gracefully
exit 0

```

---

### Post by JKyleOKC on 2011-11-20
Does it work properly for both portrait and landscape oriented photos? I would do the resizing before the auto-rotate, expecting the resize to stretch the width to 640 and squash the height to 480 when the pic is portrait (vertical) rather than landscape (horizontal). I believe that the "convert" command has options that can deal with this, however, it might not be an issue.

To deal with quotes inside a quoted string, use \" instead of plain " and they won't conflict. The "\" will be stripped off when the outer string is parsed, so the quote will take effect on the next parsing. Also, I see at least one place where you quoted "$f" but not the preceding directory names in the path spec. It's safer to quote the entire string, even if only the "$f" part is likely to contain spaces.

Neither of these is a deal-killer; they're more like minor nits, but things to keep in mind as you're learning the art of scripting...

---

### Post by newbie-user on 2011-11-20
if you're going to be changing directories within the script, you'll probably want to source the script when running it.

to source the script, put a space between the . and / when running the script:

  . /script.sh

instead of simply running the script as:

  ./script.sh

---

