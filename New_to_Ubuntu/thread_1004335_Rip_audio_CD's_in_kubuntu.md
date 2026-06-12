---
title: "Rip audio CD's in kubuntu?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by tegnoto89 on 2008-12-07
I just started using kubuntu, and I'm not sure how to rip audio cd's to put them in my amarok collection.  Any help?

Thanks!!

---

### Post by PocketDog on 2008-12-07
Rip them with K3B ```
sudo apt-get install k3b
``` to rip CDs if you don't already have it installed. It's pretty simple to use so I don't need to do a step-by-step ;-)

---

### Post by jlc on 2008-12-09
You can also open Konqueror and type in **audiocd:/** If you want MP3 for example. Right click on MP3 and choose were you want to copy it to.

You can change the encoding settings in:

Kmenu > System Settings > Advanced > Audio CDs > MP3 Encoder

[https://help.ubuntu.com/community/CDRipping#Kubuntu Default CD Ripping Software]("https://help.ubuntu.com/community/CDRipping#Kubuntu Default CD Ripping Software")

---

### Post by igknighted on 2008-12-09
> **PocketDog said:**
> Rip them with K3B ```
sudo apt-get install k3b
``` to rip CDs if you don't already have it installed. It's pretty simple to use so I don't need to do a step-by-step ;-)

While this is an option, it isn't a great one.  There is no kde4/qt4 version of k3b, so you will pull in a lot of otherwise useless libraries just for this one app.  The konqueror (kioslave) option is good.  Also many audio apps can do this too.  I rip music off of CDs using Banshee, but I'm sure amarok can do this too?

---

### Post by andrew.46 on 2008-12-09
Hi,

Another choice is to use the commandline encoder abcde. The $HOME/.abcde.conf file that I usually use is:

```
# -----------------$HOME/abcde.conf------------------- #
# 
# A sample configuration file to convert music cds to 
#       MP3 format using abcde version 2.3.3.
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for MP3. In this case
# the alternatives are gogo, bladeenc, l3enc, xingmp3enc, mp3enc.
MP3ENCODERSYNTAX=lame 

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/lame
LAME=lame

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
LAMEOPTS='--preset extreme' 

# Output type for MP3.
OUTPUTTYPE="mp3"

# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"

# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/music/"               

# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'

# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}

# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
COMMENT='Encoded using abcde!'          # Add a comment to the meta-tags
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)
```

All the best,

  Andrew

---

### Post by sbennettgso on 2008-12-25
I've followed the guide above to use Konqueror to rip CDs.  The Vorbis encoder seems to work, but the MP3 encoder just gives white noise.  I've installed LAME and a few other things that I thought I might need, but no go so far.  Any ideas?

Thanks,
Scott

---

