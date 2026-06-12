---
title: "Can someone explain to me how the following script works?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Mortesins93 on 2011-05-19
```

#!/bin/bash

args=("$@")

args=`echo $args | sed 's/[/]$//'`

pids=`eval pgrep -f flashplayer`
for pid in $pids
do
    lsoutput=$(lsof -p $pid | grep '/tmp/Flash[^ ]*')
    
    IFS=$'\n'
    for line in $lsoutput; 
        do
        lsout1=`echo $line | awk '{print "/proc/" $2 "/fd/" $4}' | sed 's/[rwu]$//'`
        lsout2=`echo $line | awk '{print $9}' | awk -F '/' '{print $3}'`
    
        if [ -n "$args" ];
        then
            if [ -d $args ]; 
            then
                echo "Copying $lsout2 to $args/"
                eval "cp $lsout1 $args/$lsout2.flv"
            else
                echo "The directory \"$args\" doesn't exist"
                break
            fi
        else
            echo "Copying $lsout2"
            eval "cp $lsout1 $lsout2.flv"
        fi

        done
done

```
It works really great but I don't understand how.
Thanks in advance.

---

### Post by nothingspecial on 2011-05-19
It  downloads youtube videos that have buffered on your computer to your hard drive.

[-X

They used to just be in /tmp, but now they are in an unidentifiable place.

You can accomplish the same with this, but the result will be a number without a .flv suffix.

```
f="$(ls -l  /proc/$(pgrep -f flashplayer)/fd | grep deleted)" && f="${f##*:+([0-9]) }" && f="${f%% -*}" && cp /proc/$(pgrep -f flashplayer)/fd/"$f" .
```

To explain the script in full, would be a tutorial, not a reply in a forum. You have awk, sed, test and a whole host of other tools in there.



 Basically, it finds the inidentifiable place the video is buffered.  Strips out all the gobbldygook so you have something to copy, checks everything that is supposed to be there is there, then copies it.

But you are not supposed to. So don't. :)

---

### Post by Mortesins93 on 2011-05-20
Thanks, and I am sorry I forgot to say that I know a bit of bash script, what I didn't understand was args, awk, sed, print, but you are probably right by saying that a tutorial is needed. I'll try checking out what these commands mean and maybe I'll ask something more specific.
Thank you so much.

---

