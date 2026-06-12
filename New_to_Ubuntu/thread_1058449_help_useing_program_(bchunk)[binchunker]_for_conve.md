---
title: "help useing program (bchunk)[binchunker] for converting old psx games"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by JohnsShadow on 2009-02-02
hey guys im trying to convert my old psx games into iso's from there bin/cue format

i discovered a program called binchunker but its not in my program lists.
now im a little new to running programs from the terminal and i would appreciate the help

i am under the understanding that bchunk has a psx mode which makes the program ideal

cant wait to play ffIX again :D
or anthology or chronicles or origins or tactics or FFVII or FFVIII

i just hope they play on my xbox, after all this converting

willing to share games :D

EDIT: if somebody knows of a better program im all ears

---

### Post by JohnsShadow on 2009-02-02
well for starters type bchunk into a terminal, you should get this out put back 
```
root@username:/home/username# bchunk
binchunker for Unix, version 1.2.0 by Heikki Hannikainen <hessu@hes.iki.fi>
	Created with the kind help of Bob Marietta <marietrg@SLU.EDU>,
	partly based on his Pascal (Delphi) implementation.
	Support for MODE2/2352 ISO tracks thanks to input from
	Godmar Back <gback@cs.utah.edu>, Colas Nahaboo <Colas@Nahaboo.com>
	and Matthew Green <mrg@eterna.com.au>.
	Released under the GNU GPL, version 2 or later (at your option).

Usage: bchunk [-v] [-r] [-p (PSX)] [-w (wav)] [-s (swabaudio)]
         <image.bin> <image.cue> <basename>
Example: bchunk foo.bin foo.cue foo
  -v  Verbose mode
  -r  Raw mode for MODE2/2352: write all 2352 bytes from offset 0 (VCD/MPEG)
  -p  PSX mode for MODE2/2352: write 2336 bytes from offset 24
      (default MODE2/2352 mode writes 2048 bytes from offset 24)
  -w  Output audio files in WAV format
  -s  swabaudio: swap byte order in audio tracks

```

but no matter what selection i make it just says
```
bash: [-p]: command not found
```

and you know i want PSX
i tryed: -p, [-p], [-p PSX] 
i know ther is a right way to do this, i will ether figure this out or somebody will save me

i really thought this would work
```
root@jsx-evil-jsx:/home/jsx# bchunk [-p] <Final Fantasy Anthology - CD1.bin> <Final Fantasy Anthology - CD1.cue> <FFA>
```
the files are in the :home/JsX/ directory

got this error
```
bash: syntax error near unexpected token `<'
```

---

### Post by JohnsShadow on 2009-02-03
I got it working, 
first put the bin/cue files in your home/username directory
rename the files somthing short (preferably without spaces) make shure the names are the same between the bin/cue files

```
bchunk filename.bin filename.cue nameofnewfile.iso
```

and it works

---

