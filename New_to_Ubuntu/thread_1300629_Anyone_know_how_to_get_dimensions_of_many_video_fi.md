---
title: "Anyone know how to get dimensions of many video files?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by hopelessone on 2009-10-25
Hi,

Anyone know how to get dimensions of lots of video files in a directory?

i.e. Width & Height resolution

thanks..

---

### Post by nikhilbhardwaj on 2009-10-25
ffmpeg 
oe mencoder
may have a way try reading their manual

---

### Post by hopelessone on 2009-10-25
OK thanks..will do..

---

### Post by hopelessone on 2009-10-25
still no go...any ideas...?

windows has it...why can't i view it in linux????

---

### Post by samh785 on 2009-10-25
this is a kind of rudimentary idea, but have you tried importing them in a video editor? Usually video editors have an output somewhere of the dimensions of video.

---

### Post by hopelessone on 2009-10-25
Hmmmmmm...not a bad idea i will try...which video editor is your flavor?

---

### Post by ramuk on 2009-10-25
Hope this helps. (in gnome OR U may try these Tips... in KDE TOO)

you may right-click on the video file and check the properties of the file as you do in windows. But I think it will work only if you selected one file.

(I never tried this(below) but You try and find it, if.. possible.)

It may work with multiple files if they have same resolution or similar properties.

Sorry, am not having UBUNTU in my HDD; to point you in the right direction so am giving you the possible Ways i may try. :popcorn:

---

### Post by samh785 on 2009-10-25
> **hopelessone said:**
> Hmmmmmm...not a bad idea i will try...which video editor is your flavor?
Open Shot is my favorite. :D

---

### Post by amauk on 2009-10-25
I use this to dump video metadata into a comma separated file

*edit*
depends on "extract" (it's in the repos)
```
sudo apt-get install extract
```

```
#!/bin/bash

TOP_DIR="/media/raid5/media/Films/"
ASPECT_RATIOS=( 1.33 1.50 1.78 1.85 2.39 )

IFS=$'\n'
MIL_SECS=1
SECS=1000
FILES=`find "$TOP_DIR" -type f | sort`

# Col headers
echo "\"Directory\",\"File Name\",\"Extension\",\"Width\",\"Height\",\"Definition\",\"Aspect Ratio\",\"Closest AR\",\"Closest AR (Human)\",\"Run Time\""

for FILE in $FILES
do
    FILENAME=`basename "$FILE" | sed 's|\(.*\)\.\(.*\)|\1|'`
    FILEEXT=`basename "$FILE" | sed 's|\(.*\)\.\(.*\)|\2|'`
    FILEDIR=`echo "$FILE" | sed "s|${TOP_DIR}||" | sed "s|${FILENAME}\.${FILEEXT}||" | sed 's|/$||'`

    METADATA=`extract "$FILE"`
    if [ -n "$METADATA" ]; then

        # Dimensions, Aspect Ratios, etc.
        VID_DIMS=`echo "$METADATA" | grep -o '[0-9]\+x[0-9]\+'`
        if [ -n "$VID_DIMS" ]; then
            VID_WIDTH=`echo "$VID_DIMS" | grep -o '^[0-9]\+'`
            VID_HEIGHT=`echo "$VID_DIMS" | grep -o '[0-9]\+$'`
            VID_ASPECT_RATIO=`echo $VID_WIDTH $VID_HEIGHT | awk '{ printf("%.2f", $1/$2 ) }'`

            # Hi-Def or Standard Def
            if [ "$VID_WIDTH" -gt 720 ]; then
                VID_DEF="HD"
            else
                VID_DEF="SD"
            fi

            # Find closest AR from 'common' film AR's
            CLOSEST_AR_INDEX=""
            for ((i=0; i<${#ASPECT_RATIOS[@]}; i++))
            do
                HOW_CLOSE=`echo "scale=2; $VID_ASPECT_RATIO - ${ASPECT_RATIOS[$i]}" | bc -l`
                CLOSEST_AR_INDEX=`echo -e "${CLOSEST_AR_INDEX}\n${HOW_CLOSE}:${i}"`
            done
            CLOSEST_AR_INDEX=`echo "$CLOSEST_AR_INDEX" | sed 's/^-//;s/^\./0./' | sort -n | grep -o ':.*$' | sed 's/^://' | head -1`
            CLOSEST_AR=${ASPECT_RATIOS[$CLOSEST_AR_INDEX]}

            # Get human readable AR (x:y)
            MULTIPLE=1
            BREAK=0
            while [ $BREAK -eq 0 ]; do
                RATIO_INT=`echo "scale=2; $CLOSEST_AR * $MULTIPLE" | bc -l`
                if [[ $RATIO_INT =~ ^[0-9]+\.0[0-4]$ ]]; then
                    RATIO_INT=`echo "$RATIO_INT" | grep -o '^[0-9]\+'`
                    BREAK=1
                elif [[ $RATIO_INT =~ ^[0-9]+\.9[5-9]$ ]]; then
                    RATIO_INT=`echo "$RATIO_INT" | grep -o '^[0-9]\+'`
                    RATIO_INT=`expr $RATIO_INT + 1`
                    BREAK=1
                else
                    MULTIPLE=`expr $MULTIPLE + 1`
                fi
            done
            RATIO_HUMAN="${RATIO_INT}:${MULTIPLE}"
        else
            VID_WIDTH=0
            VID_HEIGHT=0
            VID_DEF="N/A"
            VID_ASPECT_RATIO=0.00
            CLOSEST_AR=0.00
            RATIO_HUMAN="N/A"
        fi

        # Runtime calcs
        RUNTIME_RAW=`echo "$METADATA" | grep -o '[0-9]\+ \?m\?s'`
        if [ -n "$RUNTIME_RAW" ]; then
            RUNTIME_DIGITS=`echo "$RUNTIME_RAW" | grep -o '^[0-9]\+'`
            TIME_UNIT=`echo "$RUNTIME_RAW" | grep -o '[a-z]\+$'`
            if [ "$TIME_UNIT" == "ms" ]; then
                RUNTIME_MS="$RUNTIME_DIGITS"
            elif [ "$TIME_UNIT" == "s" ]; then
                RUNTIME_MS=`expr $RUNTIME_DIGITS \* $SECS`
            fi
            RUNTIME_S=`expr $RUNTIME_DIGITS / 1000`

            while [ "$RUNTIME_S" -gt 59 ]; do
                RUNTIME_M=`expr $RUNTIME_S / 60`
                RUNTIME_SUB=`expr $RUNTIME_M \* 60`
                RUNTIME_S=`expr $RUNTIME_S - $RUNTIME_SUB`
            done
            while [ "$RUNTIME_M" -gt 59 ]; do
                RUNTIME_H=`expr $RUNTIME_M / 60`
                RUNTIME_SUB=`expr $RUNTIME_H \* 60`
                RUNTIME_M=`expr $RUNTIME_M - $RUNTIME_SUB`
            done
            if [ "$RUNTIME_S" -lt 10 ]; then
                RUNTIME_S="0${RUNTIME_S}"
                RUNTIME_S=`echo "$RUNTIME_S" | sed 's|^0\+|0|;s|^0$|00|'`
            fi
            if [ "$RUNTIME_M" -lt 10 ]; then
                RUNTIME_M="0${RUNTIME_M}"
                RUNTIME_M=`echo "$RUNTIME_M" | sed 's|^0\+|0|;s|^0$|00|'`
            fi
            if [ "$RUNTIME_H" -lt 10 ]; then
                RUNTIME_H="0${RUNTIME_H}"
                RUNTIME_H=`echo "$RUNTIME_H" | sed 's|^0\+|0|;s|^0$|00|'`
            fi
            RUNTIME_NICE="${RUNTIME_H}:${RUNTIME_M}:${RUNTIME_S}"
        else
            RUNTIME_NICE="N/A"
        fi

        echo "\"${FILEDIR}\",\"${FILENAME}\",\"${FILEEXT}\",${VID_WIDTH},${VID_HEIGHT},\"${VID_DEF}\",${VID_ASPECT_RATIO},${CLOSEST_AR},\"${RATIO_HUMAN}\",\"${RUNTIME_NICE}\""
    fi
done
```

---

### Post by screwbunt2 on 2010-07-02
AMAUK:

Thanks for the helpful tip. Any chance you can tell us **which version of extract** you're using?

I tried it in Cygwin for grins and it doesn't work.

Thanks! ;)

---

### Post by amauk on 2010-07-02
0.5.23
the one in the lucid repo

*edit*
wow, old thread

My script has changed since I wrote the above
I don't actually use extract anymore
instead, running everything through mplayer
(I found it's way more accurate, even able to show the "correct" aspect ratio for matroska files with a custom AR header)

```
#!/bin/bash

TOP_DIR="/media/raid5/media/Films/"
ASPECT_RATIOS=( 1.33 1.50 1.78 1.85 2.39 )

IFS=$'\n'
MIL_SECS=1
SECS=1000
FILES=`find "$TOP_DIR" -type f | sort`

# Col headers
echo "\"Directory\",\"File Name\",\"Extension\",\"Width\",\"Height\",\"Definition\",\"Aspect Ratio\",\"Closest AR\",\"Closest AR (Human)\",\"Run Time (Accuracy is codec dependant)\""

for FILE in $FILES
do
    FILENAME=`basename "$FILE" | sed 's|\(.*\)\.\(.*\)|\1|'`
    FILEEXT=`basename "$FILE" | sed 's|\(.*\)\.\(.*\)|\2|'`
    FILEDIR=`echo "$FILE" | sed "s|${TOP_DIR}||" | sed "s|${FILENAME}\.${FILEEXT}||" | sed 's|/$||'`

    METADATA=`mplayer -vo null -identify -frames 0 "$FILE" 2>/dev/null | grep '^ID_'`

    # Dimensions, Aspect Ratios, etc.
    VID_WIDTH=`echo "$METADATA" | grep 'ID_VIDEO_WIDTH' | grep -o '[0-9]\+$'`
    VID_HEIGHT=`echo "$METADATA" | grep 'ID_VIDEO_HEIGHT' | grep -o '[0-9]\+$'`
	if [ -n "$VID_WIDTH" -o -n "$VID_HEIGHT" ]; then
        VID_ASPECT_RATIO=`echo $VID_WIDTH $VID_HEIGHT | awk '{ printf("%.2f", $1/$2 ) }'`

        # Hi-Def or Standard Def
        if [ "$VID_WIDTH" -gt 720 ]; then
            VID_DEF="HD"
        else
            VID_DEF="SD"
        fi

        # Find closest AR from 'common' film AR's
        CLOSEST_AR_INDEX=""
        for ((i=0; i<${#ASPECT_RATIOS[@]}; i++))
        do
            HOW_CLOSE=`echo "scale=2; $VID_ASPECT_RATIO - ${ASPECT_RATIOS[$i]}" | bc -l`
            CLOSEST_AR_INDEX=`echo -e "${CLOSEST_AR_INDEX}\n${HOW_CLOSE}:${i}"`
        done
        CLOSEST_AR_INDEX=`echo "$CLOSEST_AR_INDEX" | sed 's/^-//;s/^\./0./' | sort -n | grep -o ':.*$' | sed 's/^://' | head -1`
        CLOSEST_AR=${ASPECT_RATIOS[$CLOSEST_AR_INDEX]}

        # Get human readable AR (x:y)
        MULTIPLE=1
        BREAK=0
        while [ $BREAK -eq 0 ]; do
            RATIO_INT=`echo "scale=2; $CLOSEST_AR * $MULTIPLE" | bc -l`
            if [[ $RATIO_INT =~ ^[0-9]+\.0[0-4]$ ]]; then
                RATIO_INT=`echo "$RATIO_INT" | grep -o '^[0-9]\+'`
                BREAK=1
            elif [[ $RATIO_INT =~ ^[0-9]+\.9[5-9]$ ]]; then
                RATIO_INT=`echo "$RATIO_INT" | grep -o '^[0-9]\+'`
                RATIO_INT=`expr $RATIO_INT + 1`
                BREAK=1
            else
                MULTIPLE=`expr $MULTIPLE + 1`
            fi
        done
        RATIO_HUMAN="${RATIO_INT}:${MULTIPLE}"
    else
        VID_WIDTH=0
        VID_HEIGHT=0
        VID_DEF="N/A"
        VID_ASPECT_RATIO=0.00
        CLOSEST_AR=0.00
        RATIO_HUMAN="N/A"

		if [ "$FILEEXT" == "mp4" ]; then
			# mp4 - give benefit of doubt, and label as HD
			VID_DEF="HD"
		fi
    fi

    # Runtime calcs
    RUNTIME_S=`echo "$METADATA" | grep 'ID_LENGTH' | sed 's|ID_LENGTH=\([0-9]\+\).*|\1|'`

	if [ -n "$RUNTIME_S" ]; then
        while [ "$RUNTIME_S" -gt 59 ]; do
            RUNTIME_M=`expr $RUNTIME_S / 60`
            RUNTIME_SUB=`expr $RUNTIME_M \* 60`
            RUNTIME_S=`expr $RUNTIME_S - $RUNTIME_SUB`
        done
        while [ "$RUNTIME_M" -gt 59 ]; do
            RUNTIME_H=`expr $RUNTIME_M / 60`
            RUNTIME_SUB=`expr $RUNTIME_H \* 60`
            RUNTIME_M=`expr $RUNTIME_M - $RUNTIME_SUB`
        done
        if [ "$RUNTIME_S" -lt 10 ]; then
            RUNTIME_S="0${RUNTIME_S}"
            RUNTIME_S=`echo "$RUNTIME_S" | sed 's|^0\+|0|;s|^0$|00|'`
        fi
        if [ "$RUNTIME_M" -lt 10 ]; then
            RUNTIME_M="0${RUNTIME_M}"
            RUNTIME_M=`echo "$RUNTIME_M" | sed 's|^0\+|0|;s|^0$|00|'`
        fi
        if [ "$RUNTIME_H" -lt 10 ]; then
            RUNTIME_H="0${RUNTIME_H}"
            RUNTIME_H=`echo "$RUNTIME_H" | sed 's|^0\+|0|;s|^0$|00|'`
        fi
        RUNTIME_NICE="${RUNTIME_H}:${RUNTIME_M}:${RUNTIME_S}"
	else
		RUNTIME_NICE="00:00:00"
	fi

    echo "\"${FILEDIR}\",\"${FILENAME}\",\"${FILEEXT}\",${VID_WIDTH},${VID_HEIGHT},\"${VID_DEF}\",${VID_ASPECT_RATIO},${CLOSEST_AR},\"${RATIO_HUMAN}\",\"${RUNTIME_NICE}\""
done

NUM_FILMS=$(echo "$(cat /home/tony/Desktop/meta.csv | wc -l) -1" | bc)
NUM_HD=$(cat /home/tony/Desktop/meta.csv | grep '"HD"' | wc -l)
HD_PERCENT=$(echo "scale=3; ($NUM_HD / $NUM_FILMS) * 100" | bc | sed 's|\.\?0*$|%|')
echo "$NUM_FILMS" >&2
echo "$NUM_HD" >&2
echo "$HD_PERCENT" >&2
```

*edit2*
sample output

```
"Directory","File Name","Extension","Width","Height","Definition","Aspect Ratio","Closest AR","Closest AR (Human)","Run Time (Accuracy is codec dependant)"
"Action & Drama","300","mp4",1280,544,"HD",2.35,2.39,"12:5","01:56:32"
"Action & Drama","A Few Good Men","mp4",1280,544,"HD",2.35,2.39,"12:5","02:18:01"
"Action & Drama","Air Force One","mp4",1280,528,"HD",2.42,2.39,"12:5","02:04:34"
"Action & Drama","Airheads","avi",640,352,"SD",1.82,1.85,"13:7","01:28:27"
"Action & Drama","Anaconda","avi",704,288,"SD",2.44,2.39,"12:5","01:25:43"
"Action & Drama","Angels & Demons","mp4",1280,544,"HD",2.35,2.39,"12:5","02:26:15"
"Action & Drama","Arthur And The Invisibles","avi",620,256,"SD",2.42,2.39,"12:5","01:33:35"
"Action & Drama/Bad Boys","01 Bad Boys","avi",672,368,"SD",1.83,1.85,"13:7","01:54:04"
"Action & Drama/Bad Boys","02 Bad Boys 2","avi",560,240,"SD",2.33,2.39,"12:5","02:20:46"
```

---

### Post by screwbunt2 on 2010-07-02
AMAUK:

Wow, thanks for the update and quick reply. It is an old thread, but still useful for me.

:D

---

