---
title: "Copying MP3"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by sudeepk on 2009-05-25
can any one tell me how to move all the mp3 files in my system into a folder.?

---

### Post by melrokz on 2009-05-25
open a terminal and type:
gnome-search-tool
this will give the search window where you enter
*.mp3
and select "file system" in the drop-down box below.
Press find to show you all the mp3 files on your system.
Press Ctrl-A to select all, Ctrl-C to copy and Ctrl-V to paste them into a folder.

---

### Post by kpkeerthi on 2009-05-25
Or with a shell script. Modify the pattern, search path and target folder to you needs.

```

search_pattern=*.mp3
search_path=~/Music
target_folder=~/Music/Copied

#### No changes beyond this point ####

echo -n "Copying"
find "$search_path" -iname "$search_pattern" | while read file; do
        echo -n .
        cp "$file" "$target_folder"
done
echo " done."

```

Save the script to a file **copyfiles** in your home folder, set permission to execute and run it like below:
```

./copyfiles 2> copy.errors.log

```

Copy errors, if any, will be sent to the file **copy.errors.log**

---

### Post by Mornedhel on 2009-05-25
kpkeerthi: what's wrong with the following ?```
find ~/Music -iname "*.mp3" -exec mv "{}" ~/Music/Copied \;
```

I have never used find with -exec mv something, but is there something that prevents it from working correctly ? Just curious.

---

### Post by kpkeerthi on 2009-05-25
Should work as well.

---

