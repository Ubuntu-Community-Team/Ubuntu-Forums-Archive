---
title: "saving or recording from inet stream"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by squrl on 2011-07-19
xxx

---

### Post by Joris Donders on 2011-07-19
In Firefox you can install the "downloadhelper" add-on.

This way you can easily save video's and other stuff from the internet. 

Be carefull, it's easy this way to perform ILLEGAL actions ...... !!!! So think before you just download stuff. 

But for some sites it's a legal action.

---

### Post by jerrrys on 2011-07-20
i use a basic way, its a script.  just open a terminal and enter

&#65279;#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# [http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/](http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/)
#
#This script require sox
#sudo apt-get install sox

if [ -n "$1" ]; then
    OUTFILE="$1"
else
    TIME=$(date +%d-%b-%y_%H%M-%Z)
    OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh

when you want to stop recording, just close the terminal and don't forget to download "sox".

---

