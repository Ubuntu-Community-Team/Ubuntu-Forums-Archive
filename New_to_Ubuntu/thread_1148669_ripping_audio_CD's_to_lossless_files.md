---
title: "ripping audio CD's to lossless files"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-05-04
Running Jaunty.  Had to remove CD extractor so that Nautilus would work.  Now I can't rip audio CD's easily.

What is the best program (or most popular) for ripping CD tracks to lossless files?

K3b is popular but I have had a real headache trying to install it.  I think it only stores in Mp3 format anyway.

I would like to use FLAC files but WAV would be all right if I had to have them.

Is cdparanoia difficul to install?

Thanks in advance!

---

### Post by llamabr on 2009-05-04
```
brock@hops:~$ apt-cache search flac rip
crip - terminal-based ripper/encoder/tagger tool
dir2ogg - audio file converter into ogg-vorbis format
distmp3 - A Perl client and daemon for distributed audio encoding
mp3burn - burn audio CDs directly from MP3, Ogg Vorbis, or FLAC files
mp3cd - Burns normalized audio CDs from lists of MP3s/WAVs/Oggs/FLACs
mybashburn - Burn data and create songs with interactive dialog box
nautilus-script-audio-convert - A nautilus audio converter script
ripit - Textbased audio cd ripper
ripperx - a GTK-based audio CD ripper/encoder
soundconvert - convert compressed sound formats
brock@hops:~$ 

```

---

### Post by logos34 on 2009-05-04
use one listed [here]("https://help.ubuntu.com/community/CDRipping#Other%20CD%20Ripping%20Software")--they are the best.

You could add Exact Audio Copy (THE best), but it runs on wine (not sure if you care about that)

> **raymondvillain said:**
> 
K3b is popular but I have had a real headache trying to install it.  I think it only stores in Mp3 format anyway.


no, actually k3b will do flac too just fine (-->Settings>configure k3b>plugins>k3b external audio encoder).  Here's my flac command line if you're interested:

> flac -8 -V -o %f --force-raw-format --endian=big --channels=2 --sample-rate=44100 --sign=signed --bps=16 -T ARTIST=%a -T TITLE=%t -T TRACKNUMBER=%n -T DATE=%y -T ALBUM=%m -

k3b is a really neat app and great cd/dvd burner.

hope that helps

---

### Post by andrew.46 on 2009-05-05
Hi raymondvillain,

I not on the page that logos34 mentioned my favourite ripper abcde gets an unusually brief mention:

[https://help.ubuntu.com/community/CDRipping#ABCDE](https://help.ubuntu.com/community/CDRipping#ABCDE)

If you ever travel that path you could try the following $HOME/.abcde.conf:

```

# -----------------$HOME/.abcde.conf----------------- #
# 
# A sample configuration file to convert music cds to 
#       FLAC using abcde version 2.3.99.6
# 
#       http://andrews-corner.org/abcde.html
# -------------------------------------------------- #

# Specify the encoder to use for FLAC. In this case
# flac is the only choice.
FLACENCODERSYNTAX=flac

# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/flac
FLAC=flac

# Specify your required encoding options here. Multiple options can
# be selected as '--best --another-option' etc.
FLACOPTS='--verify --best' 

# Output type for FLAC.
OUTPUTTYPE="flac"

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
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)

```

All the best,

Andrew

---

### Post by MrWES on 2009-05-05
Andrew,

+100 for ABDCE ripper -- and thanks for the conf files on your web page! I'm assuming you're the same Andrew.

[http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")



~Bill

---

### Post by andrew.46 on 2009-05-05
Hi MrWES,

> **MrWES said:**
> +100 for ABDCE ripper -- and thanks for the conf files on your web page! I'm assuming you're the same Andrew.

Yes that is me not so discreetly plugging my own page :-). I have added a bit recently with conf files for Speex and aac...

Andrew

---

### Post by MrWES on 2009-05-05
> **andrew.46 said:**
> Hi MrWES,



Yes that is me not so discreetly plugging my own page :-). I have added a bit recently with conf files for Speex and aac...

Andrew

Well deserved I might add. I always recommend ABCDE for ripping. It's especially fast when setting MAXPROCS=2.

~Bill

---

### Post by logos34 on 2009-05-05
> **MrWES said:**
> I always recommend ABCDE for ripping. It's especially fast when setting MAXPROCS=2.

The econding part, yes, but not the ripping, no way to speed that up, dual-core or not (unless you use burst mode/cdda2wav w/o error check).  The processor can only compress the tracks as fast as they are made available by the cdparanoia reads. You'll finish no sooner than the last track is ripped.  

That said, I still prefer abcde to Exact Audio copy, which can be maddingly slow on secure setting, except for scratched/damaged cds, where EAC will at least give you the assurance of a perfect copy

---

