---
title: "Shell script to resize jpg and subfolders"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by jmumby on 2011-01-06
I use the following to resize images in a folder 

```

for file in `ls -l`
do
name=`echo $file | cut -f1 -d.`
convert -strip  -quiet -geometry 1024x768 -quality 80 $file /path/to/pictures/{name}_email.jpg
done

```

Which works great. Every time I put a memory stick or camera card in my PC Shotwell imports them and saves them to my NAS in folders and subfolders which is also great. So the subfolder depth can vary. I would like to clone this structure but with all the images resized to 1024x768 with a cron job. Lazy eh. 

Would it be possible to do this, automatically duplicate the file structure and resize the images into a completely different folder? In this case Dropbox. Whilst not recreating images already resized. 

Best place to start?

Thx

---

### Post by DaithiF on 2011-01-07
I would suggest a 2-step process ... (1) using rsync to mirror the directory structure, and (2) using find in a loop to do the converting ... you could combine both but that would complicate things a little.

something like the below.  (try it out on a test sample first before unleashing it on the real thing!).
```
#!/bin/bash 

# set the source & dest directories -- (update to reflect your locations)
src=/media/nas/pictures
dest=/home/you/picturesclone

# sync the directory structure using rsync ... this uses rsync filter rules to 
# ignore all files and only work on directories
cd "$src" || { echo "Failed to cd to $src, exiting..."; exit 1; }
rsync -a -f "+ */" -f "- *" . "$dest"

# find all jpg files, check if equivalent file exists in parallel directory, 
# if not, create it
find . -iname '*.jpg' | while read file
do
    other_file="$dest/${file#./}" 
    if [[ ! -e "$other_file" ]]; then
        echo "Converting $file to $other_file" 
        convert -strip  -quiet -geometry 1024x768 -quality 80 "$file" "$other_fi
le"
        [[ $? -ne 0 ]] && { echo "Failed to create file $other_file, exiting"; e
xit 1; }
    else
        echo "Skipping $file as it already exists at $other_file"
    fi
done

```

---

