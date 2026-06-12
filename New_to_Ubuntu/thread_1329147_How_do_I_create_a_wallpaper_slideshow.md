---
title: "How do I create a wallpaper slideshow?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by quinnten83 on 2009-11-17
I've looked for this on the internet and on the forums, but can not find a solution. So I am asking now. I've been around for a while, so not a noobie, I am not affraid of the more technical solutions.
How do I make a wallpaper slideshow for Karmic like the one that is installed by default? I would like to do this with my own pictures. I just can't seem to figure it out.
(<Rant>I am actually getting to a point of frustration, just can't get these little configuration things worked out in Karmic<end rant>).

---

### Post by ankspo71 on 2009-11-17
Hi,

I don't know how to make any scripts for what you want, but I know of a good wallpaper changer. It's called wallpaper-tray. You can search for it in synaptic package manager or use this code in your terminal...
```
sudo apt-get install wallpaper-tray
```Hope this helps,
James
P.S. After installing it, you will find it by right clicking on your panel and clicking on 'add to panel' then select wallpaper tray

---

### Post by emigrant on 2009-11-17
put all the images you want in the slide show into one folder.
open a notepad and past the below code there and replace all the image links with your own.
for ex: replace
```
/usr/share/background/cosmos/could.jpg
```

with the correct link of the image.

save the notepad file as .xml

finally go to the wallpaper chooser and select the .xml file.
it should work hopefully.

note: the below script is the default karmic one.

[PHP]
<background>
  <starttime>
    <year>2009</year>
    <month>08</month>
    <day>04</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/cloud.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/cloud.jpg</from>
    <to>/usr/share/backgrounds/cosmos/comet.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/comet.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/comet.jpg</from>
    <to>/usr/share/backgrounds/cosmos/earth-horizon.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/earth-horizon.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/earth-horizon.jpg</from>
    <to>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/blue-marble-west.jpg</from>
    <to>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/galaxy-ngc3370.jpg</from>
    <to>/usr/share/backgrounds/cosmos/helix-nebula.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/helix-nebula.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/helix-nebula.jpg</from>
    <to>/usr/share/backgrounds/cosmos/jupiter.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/jupiter.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/jupiter.jpg</from>
    <to>/usr/share/backgrounds/cosmos/sombrero.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/sombrero.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/sombrero.jpg</from>
    <to>/usr/share/backgrounds/cosmos/whirlpool.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/whirlpool.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/whirlpool.jpg</from>
    <to>/usr/share/backgrounds/cosmos/cloud.jpg</to>
  </transition>
</background>[/PHP]

---

### Post by quinnten83 on 2009-11-17
Tnx, guys, 
I will try them both.
I must say that I'm disappointed that canonical would give a slide show for the background, but not give you an option to create your own.
I don't mind editing the .xml files, but really was it so difficult to give a program that will create that by default?
This is a Major paper-cut, the kind that will let you bleed to death.
I really need to learn to program so I can start fixing these little niggles.....

---

### Post by emigrant on 2009-11-17
Man this is not a big deal. i bet U can do it in a min.

---

### Post by scared0o0rabbit on 2009-11-17
So the xml file method, if I only placed two backgrounds in the list, and removed all the others, would it just cycle back and forth between them, or does the script have to be restarted or something?

The wallpaper-tray method didn't work so well...

It wouldn't let me change the time for how often to change the wallpaper, so as soon as I hit apply, thinking it would let me then, it started changing my wallpaper every 0 seconds, which was a disaster lol.

---

### Post by quinnten83 on 2009-11-17
> **emigrant said:**
> Man this is not a big deal. i bet U can do it in a min.

I can, 
but that is not the point.
You can't offer an option like this and then expect non technical newcomers not to want to create their own. And when they do, not give them an easy way to do it.
It's as cruel as dangling a carrot in front of a hungry horse (or ***, which is what I feel like after this).

So it appears you can't say @$$ on the forum, even when you mean a donkey and not your buttocks.

---

### Post by Old *ix Geek on 2009-11-17
> **quinnten83 said:**
> I must say that I'm disappointed that canonical would give a slide show for the background, but not give you an option to create your own.
...
I really need to learn to program so I can start fixing these little niggles.....Switch to KDE. Problem solved. Nothing to add, nothing to fiddle with, nothing to program.  Just select the slideshow option from 'appearance settings,' choose the wallpapers you want, set various options, and you're good to go.

---

### Post by quinnten83 on 2009-11-17
> **Old *ix Geek said:**
> Switch to KDE. Problem solved. Nothing to add, nothing to fiddle with, nothing to program.  Just select the slideshow option from 'appearance settings,' choose the wallpapers you want, set various options, and you're good to go.

Aaaargh, KDE is deadly for my short attention span.
Btw, let's not change this into a KDE vs. Gnome discussion.... :p;):D:o:):P

---

### Post by RealG187 on 2009-11-17
> **ankspo71 said:**
> Hi,

I don't know how to make any scripts for what you want, but I know of a good wallpaper changer. It's called wallpaper-tray. You can search for it in synaptic package manager or use this code in your terminal...
```
sudo apt-get install wallpaper-tray
```Hope this helps,
James
P.S. After installing it, you will find it by right clicking on your panel and clicking on 'add to panel' then select wallpaper trayDoes it work in 9.04 and 9.10?

---

### Post by blueridgedog on 2009-11-17
[http://ubuntuforums.org/archive/index.php/t-2801.html](http://ubuntuforums.org/archive/index.php/t-2801.html)

---

### Post by Old *ix Geek on 2009-11-17
> **quinnten83 said:**
> Aaaargh, KDE is deadly for my short attention span.But it's so much fun with its absolutely ENDLESS customization possibilities. :)
> Btw, let's not change this into a KDE vs. Gnome discussion.... :p;):D:o:):PAgreed.

---

### Post by mwilsonemt on 2009-12-02
blueridgedog: How is that relivent?  It's few years old and not about the built in functions in 9.10.

---

### Post by nothingspecial on 2009-12-03
```
sudo apt-get install feh
```

Assuming your photos are in a ~/photos
```

cd 
feh -rzF -D 5 photos
```

-r will look for photos in all directories and subdirectories of your photos folder

-z will make it random

-F makes it fullscreen

-D 5 will make each image show for 5 seconds before the next one, change it for what you like.

---

### Post by longtom on 2009-12-03
I use [drapes](https://launchpad.net/drapes).

Easy and integrated as well as customisable.

But if you rather use code and scripts...

---

### Post by nothingspecial on 2009-12-03
But if you put an alias in your .bashrc eg

```
alias ss='feh -rzF -D 5 photos'
```

and have a key binding to open your terminal then its three keystrokes instead of all that mouse clicking.

---

### Post by pbrane on 2009-12-03
If you use GNOME, another way to do this is to create a directory with all the wallpaper images that you want to rotate and use this script:

```

#!/bin/bash
# script to rotate GNOME backgrounds
#
# Create a directory to hoid your favorite wallpapers.
# Running this script will choose a random image from
# the directory and change the GNOME background image
# in gconf.

# set delay time. see man sleep for details, default is 10 minutes
delay=10m

# set the wallpaper directory of your choice
**pixdir**=$HOME/Pictures/wallpaper/

# grab a random image
newbkgrnd="$(ls $pixdir | shuf -n1)"

# update the GNOME backgound
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$pixdir$newbkgrnd"

# sleep for the specified time
sleep $delay

# execute the script again!
exec $0

```

name the script and place it in the directory of your choice.

change the **pixdir** variable to match the directory you have your images in. 

make the script executable: **chmod u+x name_of_script**

run it in a terminal

add it to your startup applications in System->Preferences->Startup Applications

---

### Post by blueridgedog on 2009-12-03
> **mwilsonemt said:**
> blueridgedog: How is that relivent?  It's few years old and not about the built in functions in 9.10.

The script at the bottom of the link and the script posted in reply 17 to this thread should get you thinking about how to do it.  You are right, it is not a built-in function.

---

### Post by x C0MMAND0 x on 2009-12-03
Put all of the photos you want in one directory, then check out the following simple script I wrote

[http://ubuntuforums.org/showthread.php?t=1337658](http://ubuntuforums.org/showthread.php?t=1337658)

Works AMAZING!

---

### Post by ankspo71 on 2009-12-04
> **RealG187 said:**
> Does it work in 9.04 and 9.10?

Hi, It works for me in 9.04 and 9.10 quite well.

BTW, The time interval option is a dropdown list that is set on 0 minutes (with no other preset time intervals), but you just type in the time in you need right there in the box. I have mine set for 30 minutes. (see attachment)

BTW#2  After installing wallpaper-tray, it is found by right clicking on the panel, select add to panel, then scroll down to wallpaper-tray.

I'm interested in this where this thread goes though, because wallpaper-tray displays a wallpaper icon in the panel and I prefer it ran hidden instead.

Hope it helps
James

---

### Post by running_rabbit07 on 2010-01-11
> **RealG187 said:**
> Does it work in 9.04 and 9.10?

Installed in 9.10. That app is effed up. I went crazy and started adding pics from very folder on the dri except the one I told it to and it was changing pics every second. Of course with each pic it used, it added to the menu for choosing backgrounds. I'll stick with a single pic on Ubuntu just enjoy the changing background when running Windows 7.

---

### Post by tom.swartz07 on 2010-01-11
Try this: I havent tried it (i made my own with a custom xml file)
[http://www.omgubuntu.co.uk/2010/01/auto-change-wallpaper-gnome-ubuntu.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Reader](http://www.omgubuntu.co.uk/2010/01/auto-change-wallpaper-gnome-ubuntu.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Reader)



I believe that they are planning on releasing a tool to make your own background slideshows in the next version of Ubuntu. (if they dont go with gnome-shell, ick)

Anyway- this will help you get it running at least?

---

### Post by running_rabbit07 on 2010-01-11
> **tom.swartz07 said:**
> Try this: I havent tried it (i made my own with a custom xml file)
[http://www.omgubuntu.co.uk/2010/01/auto-change-wallpaper-gnome-ubuntu.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Reader]("http://www.omgubuntu.co.uk/2010/01/auto-change-wallpaper-gnome-ubuntu.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+%28Omg%21+Ubuntu%21%29&utm_content=Google+Reader")



I believe that they are planning on releasing a tool to make your own background slideshows in the next version of Ubuntu. (if they dont go with gnome-shell, ick)

Anyway- this will help you get it running at least?

Thanx, I'll give it a try when the [Screwdrivers]("http://www.idrink.com/v.html?id=652") ware off.

---

### Post by no_angst on 2010-03-03
> **ankspo71 said:**
> Hi,

I don't know how to make any scripts for what you want, but I know of a good wallpaper changer. It's called wallpaper-tray.

This (after editing the interval) and Drapes both worked well for me, but I preferred wallpaper-tray (can't remember why now, been a couple weeks ago).  
I even like the tiny mini-display of the background in my tray, as I can see which photo is being shown and do a quick Ctrl-Alt-D to "show desktop" if I want to see it full-screen.  I like the Pictures Folder screen saver as well (System > Preferences > Screensaver, then scroll down to Picture Folder).

Jim

---

### Post by paul8620 on 2010-03-07
I create a script for this all you need to do is place the script in the folder with all the pictures you want to add and then run the script. The scripts generate a slideshow.xml file witch you need to add to you backgrounds and that is all. 
BTW the script must be run from console has some problems if you run it from the interface.

```

echo "start in " $PWD 
filepath=$PWD'/'
ls -1 | grep -i "\.jpg" > dir.txt 
string="<background>\n <starttime>\n  <year>2010</year>\n  <month>03</month>\n  <day>03</day>\n  <hour>00</hour>\n  <minute>00</minute>\n  <seconds>00</seconds>\n </starttime>\n"
string2="</background>"
echo -e $string > slideshow.xml
filename=dir.txt
exec < $filename
transition=" <transition>\n  <duration>5.0</duration>\n"
endtrans=" </transition>\n\n"
static="  <static>\n  <duration>1000.0</duration>\n"
endstatic=" </static>\n\n"
read line
echo $line
linep=$filepath$line
echo $linep 
while read line; do 
echo -e $static "  <file>"$linep"</file>\n" $endstatic $transition "  <from>" $linep "</from>\n  <to>" $filepath$line "</to>\n" $endtrans >>slideshow.xml
linep=$filepath$line		
done 
echo $string2 >> slideshow.xml
rm dir.txt


```

---

### Post by rabiabidabi on 2010-04-15
Hello. I found these instructions, followed them and it works fine. It took me 10 minutes and I have no programming experience.

[http://goo.gl/oDAs](http://goo.gl/oDAs)

I copied the python script in gedit and saved it to my Desktop.

Like I typed, it works as advertised. My question is, can I delete the saved .py script from my desktop now?

Have fun,
Rab

---

### Post by csaket on 2010-04-15
The XML Slideshow Creator gives a user friendly gui to create such wallpaper stacks/slideshows.

[http://www.webupd8.org/2010/02/easily-create-xml-wallpapers-with-xml.html](http://www.webupd8.org/2010/02/easily-create-xml-wallpapers-with-xml.html)

---

### Post by mr0no on 2010-05-03
There's a cool application called Desktop Drapes. You can install it from Software Center if you are using ubuntu 10.04 lucid lynx. I don't know for older versions.

---

### Post by longtom on 2010-05-04
> **mr0no said:**
> There's a cool application called Desktop Drapes. You can install it from Software Center if you are using ubuntu 10.04 lucid lynx. I don't know for older versions.

I had it running under Hardy....:)

---

### Post by wingnux on 2010-05-05
Desktop Drapes (sudo aptitude install drapes) works like a charm!

---

### Post by chitowner2 on 2010-05-11
All good ideas folks. Here's another similar:  [https://launchpad.net/~ruben-verweij/+archive/wallpaper-stacks](https://launchpad.net/~ruben-verweij/+archive/wallpaper-stacks)


I'd like to take a turn here tho: In karmic I had each desktop use a different wallpaper. Really handy to know where you're at.  :-)  On lucid just but R-click on the desktop and choose "Desktop Activity Settings" Simple from there.

CT

---

### Post by blueridgedog on 2010-05-11
> **chitowner2 said:**
> All good ideas folks. Here's another similar:  [https://launchpad.net/~ruben-verweij/+archive/wallpaper-stacks](https://launchpad.net/~ruben-verweij/+archive/wallpaper-stacks)


I'd like to take a turn here tho: In karmic I had each desktop use a different wallpaper. Really handy to know where you're at.  :-)  On lucid just but R-click on the desktop and choose "Desktop Activity Settings" Simple from there.

CT

Must be Kubuntu.

---

### Post by mhgsys on 2010-05-11
You can use this script; just open up a editor;(f.e gedit / nano or vim)
copy past the script below, change the #directory containing pictures DIR to your own picture dir.

f.e I have a map called bcground located on my Desktop.
as you can see in the script. 

Save the script as any .sh you like to name it. 
Do a chmod a+x on the file, and run it with ./whateveryounamedthescript
.Or add it to startup applications,.if you want it to be started at boot.

 changing the sleep interval number at the bottom of the script will determine how long a background-picture is displayed
[SIZE="1"]
 note; I am not fully the creator of this script, a friend of mine just wanted to have a changing background, we downloaded multiple scripts, adjusted and mangled some code from other scripts we've found on the internet.
[/SIZE]

```
#!/bin/bash
until [ 1 -eq 2 ]; do

# Script to randomly set Background from files in a directory

# Directory Containing Pictures
DIR="/home/mhgsys/Desktop/bcground/"

# Command to Select a random jpg file from directory
# Delete the *.jpg to select any file but it may return a folder
PIC=$(ls $DIR/*.jpg | shuf -n1)

# Command to set Background Image
gconftool -t string -s /desktop/gnome/background/picture_filename $PIC

sleep 8s
done

```

---

### Post by x C0MMAND0 x on 2010-05-11
You can check out [my thread here]("http://ubuntuforums.org/showthread.php?t=1337658").  I wrote a very simple script.  Basically, you put all your photos you want it to cycle between in a directory.  Then you tell my script where that directory is.  Finally, you use crontab to run the script every hour/minute/day/whenever you want it to change.

Let me know if you have any questions.

---

### Post by longtom on 2010-05-12
Anybody tried [Wally](http://www.becrux.com/index.php?page=projects&name=wally)?

I have it running in PCLinux Gnome quite smoothly.  Probably not in the Ubuntu repos - but the debian packages on the web site might just do the trick.

---

### Post by Raghu1990 on 2010-06-08
Instead of editing xml code yourself, this nifty app generates the code for you.

[http://gnome-look.org/content/show.php/Wallpaper+Slideshow?content=125178]("http://gnome-look.org/content/show.php/Wallpaper+Slideshow?content=125178")

---

### Post by irv on 2010-06-08
We have a 47" monitor setup in the church where I run slide show on. It is so simple to do so I made a little video on how to do it. See it on youtube:
[http://www.youtube.com/watch?v=rifxRLsIl34]("http://www.youtube.com/watch?v=rifxRLsIl34")
The Image Viewer works great for this.

---

### Post by LoREZ on 2010-06-15
Ha!  I wish this thread had been around when I had to tackle this problem.  But I did solve it, to my surprise.  I'm no programmer (too much tedium for me), but I'm proud of this little snip of code anyway.  That's why I bothered naming it:

```
#!/bin/bash

#------------------------------------------------------------------------------#
# rWall was written by LoREZ (c) 2009, and is licensed under GPL v2.0.         #
# I hereby poke all users with the "NO WARRANTY, real or implied" stick.       #
# This script selects random images from the assigned directories and places   #
# them on the background. It is designed for use with GNOME or Openbox,        #
# although other window managers might be able to use rWall.                   #
# This script requires Feh (or gconftool for GNOME use); no monkeys were       #
# harmed during the testing of this script.  Koalas, perhaps, but no monkeys.  #
#------------------------------------------------------------------------------#

declare VERSION
declare INIT_DIR  # initial wallpaper directory
declare BGDIR     # result of wallpaper commandline argument test
declare WALLPAPER # result of wallpaper image selection

VERSION="v1.0 ""Ajax"" (c) 2009, by LoREZ"

INIT_DIR=$1

cd /

pix_dir()  # if first argument isn't a directory, assign default directory
{
if [ -d "$INIT_DIR" ]; then
                # commandline assigned directory
		BGDIR="$INIT_DIR"
	else
                # default directory, change as needed
		BGDIR="$HOME/Pictures/backgrounds"
fi
}

# options: only the "--verbose" option takes a directory argument
case $1 in 
	"-h"        ) echo "rwall [-h -v] | [--verbose] | DIRECTORY"; exit 0
        ;;
	"-v"        ) echo "$VERSION"; exit 0
        ;;
	"--verbose" ) set -v; shift 1; pix_dir
        ;;
	"redpill"   ) echo "Why oh why didn't I take the BLUE pill?"; exit 0
        ;;
	"bluepill"  ) echo "Never send a human to do a machine's job."; exit 0
        ;;
	*           ) pix_dir
esac

# Selects one random image from wallpaper directory.
WALLPAPER=$(find "$BGDIR" -regex ".*\.\(jpg\|jpeg\|png\)" | sort -R | \
head --lines=1)

#------------------------------------------------------------------------------#
# Feh stores background settings in $HOME/.fehbg.                              #
# Warning: Feh wallpaper hides GNOME desktop, icons, & right-click menu!       #
# Uncomment one of the following three lines to use Feh in a window manager:   #
#------------------------------------------------------------------------------#

#feh --bg-center "$WALLPAPER"
#feh --bg-scale "$WALLPAPER"
#feh --bg-tile "$WALLPAPER"

#------------------------------------------------------------------------------#
# gconftool prevents hiding of icons and desktop right-click menu in GNOME.    #
# Don't forget to commment-out the following line if you choose to use Feh!    #
#------------------------------------------------------------------------------#

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$WALLPAPER"

#This next option modifies how the wallpaper is displayed, like tiling etc.
#Values: "none", "wallpaper" (eg tiled), "centered", "scaled", "stretched"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "wallpaper"

exit 0
```

So, I was being very anal with this, just for learning purposes.  Yes, I declared variables in a bash script (ducks head).  And none of the lines are more than 80 characters across (ducks head again).  But rWall works very well.

It does a few things some of the others ignore (perhaps for good reason), like being able to switch between feh and gconftool-2.  It also accepts command line arguments to change the background directory, display help, or reveal admittedly cheesy Easter eggs (if you can call them that).  It does not provide for a delay as written, but that is easy enough to add, and is in one of the previous replies.  I just wish I'd known about the shuf command!  I had to suffer through a mini regex lesson, but it allowed me to truncate the results down to a few given file types.

I turned this into a panel launcher, because I don't like waiting if I get bored with my desktop.

Enjoy.

---

### Post by laithbsoul on 2010-06-28
> **csaket said:**
> The XML Slideshow Creator gives a user friendly gui to create such wallpaper stacks/slideshows.

[http://www.webupd8.org/2010/02/easily-create-xml-wallpapers-with-xml.html](http://www.webupd8.org/2010/02/easily-create-xml-wallpapers-with-xml.html)

Thanks! that helped out so much i didn't feel like editing the xml file myself as it's nearly 3am

---

### Post by k3lt01 on 2010-06-28
Check the link in my signature, all the hard work is done already.

---

### Post by abarabas on 2010-09-19
I've made a script that creates a background.xml file in your wallpaper's folder, all you have to do is to place the script in the folder containing all the pictures you want and it automatically sets it as your desktop wallpaper. You can modify the delay between pictures passing a number as the first argument like this:

To make 15 minutes delay:
./createSlideShow.sh 15

Hope it helps!

---

### Post by geishajunkie on 2010-09-21
I see what you are doing emigrant. This is a great xml sample because it allows anybody to create specific times for say like Christmas backgrounds to start and other holidays. This is a simple solution for anybody to develop a random wallpaper changer on their own especially when creating each collection as part of an array and then assigning them at random at startup.

Cheers

---

### Post by noughtypixy on 2010-11-18
had tried this and put the folder in usr/share/backgrounds
but when I right click and change background it dosent find the one I made

**edit** ok was being a div (not the space holding sort)
realized had to click on add then navigate to the folder where the images for my slideshow were
I did have to put the name of the .xml file in the location box tho as it wasn't visible with the images

---

### Post by williamts99 on 2010-11-27
I just tried Cortina [https://launchpad.net/cortina](https://launchpad.net/cortina) as a replacement for Drapes, might want to check it out.

---

### Post by wbar2 on 2010-12-12
Here's another bash script. All you do is put any .jpg files you want in a rotation into a folder. Run the script and select that folder. That's it! 
```

#!/bin/bash
# Author: Wes Barnett
# Date: 12/11/2010
# If you would like to use this script please leave this header in-tact.

# Bash script that creates an XML file of .jpg files in a folder and 
# sets them as a transitioning background on the desktop.

DURATION="3595"		# How long in seconds you want each image to be your background
TRANSITION="5.0"	# How long in seconds you want a transition to be between images

# DO NOT EDIT AFTER THIS POINT
DIRECTORY=$(zenity --file-selection --directory --title="Choose Directory")
FILE="$DIRECTORY/background.xml"	# Name of XML file created
cd $DIRECTORY
FILELIST=(`ls -F *.jpg`)		# Get all .jpg files in the folder

rm $FILE		# Remove any previous file made

# Create the XML file

# This header is necessary for the file for some reason. The date is arbitrary.
echo "<background><starttime><year>2010</year><month>01</month><day>01</day><hour>00</hour><minute>00</minute><second>00</second></starttime>" >> $FILE

# The for loop cycles through all the files and creates a static tag and transition tag for each one.
for ((i=0; i<${#FILELIST[*]}; i++))
	do

	echo "	<static><duration>$DURATION</duration><file>$DIRECTORY/${FILELIST[$i]}</file></static>
		<transition><duration>$TRANSITION</duration><from>$DIRECTORY/${FILELIST[$i]}</from>" >> $FILE

	if [ $i -lt $((${#FILELIST[*]} - 1)) ]; then
		echo "<to>$DIRECTORY/${FILELIST[$(($i+1))]}</to>" >> $FILE
	else
		echo "<to>$DIRECTORY/${FILELIST[0]}</to>" >> $FILE	# the last transition tag needs to start everything over
	fi

	echo "</transition>" >> $FILE

done

echo "</background>" >> $FILE

# End XML file creation

gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$FILE" # Set the XML file as current background

gnome-appearance-properties --show-page=background # Open up appearance properties to show the user
```

---

### Post by Omar11 on 2011-03-28
open a terminal and put

```
sudo add-apt-repsitory ppa:crebs/ppa
```
Then this should show:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A4273F3D409BC60E6C51EF75A28BE6E4EF0A4C44
gpg: requesting key EF0A4C44 from hkp server keyserver.ubuntu.com
gpg: key EF0A4C44: "Launchpad CreBS stable" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```
then type:  ```
sudo apt-get update
```
then: ```
sudo spt-get install crebs
```
after that go to **System->Preferences->Create Background Slideshow**
And make your slideshow! :D
Btw, I tried the xml way and it doesn't work for 10.04 and later. And if you are not a programmer guy, don't go to scripting.

---

### Post by k3lt01 on 2011-03-28
> **Omar11 said:**
> Btw, I tried the xml way and it doesn't work for 10.04 and later. And if you are not a programmer guy, don't go to scripting.The xml way (check my signature for how to do it with ease) is fullproof (or should I say foolproof). All you need to know is where your pictures are, what they are called, and how to use Gedit. If you can read and follow simple instructions you'll be fine.

---

### Post by Jechem on 2011-03-28
Try this one:
[http://ubuntuforums.org/showthread.php?t=1652518](http://ubuntuforums.org/showthread.php?t=1652518)

---

### Post by Omar11 on 2011-03-29
> **k3lt01 said:**
>  All you need to know is where your pictures are, what they are called, and how to use Gedit. 

gedit is a hacking script...

---

### Post by k3lt01 on 2011-03-30
> **Omar11 said:**
> gedit is a hacking script...Omar, gedit is a text editor, similar to Notepad and Wordpad in Windows.

---

### Post by Omar11 on 2011-04-01
yes, but gedit is different with other text editors because you can edit and save files made from the "root" owner> 1st os ownerwhile in notepad and abiword(e.t.c. can't do dat.

---

### Post by k3lt01 on 2011-04-02
> **Omar11 said:**
> yes, but gedit is different with other text editors because you can edit and save files made from the "root" ownerwhile in notepad and abiword(e.t.c. can't do dat.Unfortunately you are incorrect. You can edit any text file with a variety of editors if you know how to open it properly and the process for opening a system ("root") file is the same among editors.

Before you come back and tell me this is not correct I'll just add I've done it and if you don't believe me check my signature for the how to on this exact topic. I use Gedit simply because it has a much smaller footprint but you can, and I have, use any text editor you want to to do this.

---

### Post by milindaaruna on 2012-09-12
Here is the script that I have created to create the XML file. that is easy try it...

Here is the complete guide lines.

[http://milindapro.blogspot.com/2011/09/set-custom-pictures-for-slide-show-in.html](http://milindapro.blogspot.com/2011/09/set-custom-pictures-for-slide-show-in.html)

---

### Post by overdrank on 2012-09-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

