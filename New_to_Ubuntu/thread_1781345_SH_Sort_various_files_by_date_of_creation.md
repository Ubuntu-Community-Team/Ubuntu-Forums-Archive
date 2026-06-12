---
title: "SH: Sort various files by date of creation?"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by honeybear on 2011-06-13
Hello,

I would like to sort a list of given file by date of last modification or date of creation. How could it simply be possible under SH/DASH?
 
list.txt
```
 
/usr/bin/
/usr/bin/akonadi_mbox_resource
/usr/bin/unzipsfx
/usr/bin/aumix
/usr/bin/smime_keys
/usr/bin/wish-default
/usr/bin/dpkg-maintscript-helper
/usr/bin/composite
/usr/bin/xdg-email
/usr/bin/whatis
/usr/bin/tv_grab_it
/usr/bin/i486-linux-gnu-cpp-4.4
/usr/bin/lessfile
/usr/bin/ionice
/usr/bin/hp-timedate
/usr/bin/dh_installdefoma
/usr/bin/size
/usr/bin/akonaditray
/usr/bin/scrollkeeper-install
/usr/bin/rarian-sk-preinstall
/usr/bin/xscreensaver-getimage-file
/usr/bin/infobrowser
/usr/bin/pyview
/usr/bin/rvim
/usr/bin/dotlockfile
```

I was thinking something like: 
```

cat list.txt | while read i ; do 
           sort "$i"
done

```
but of course it is not working and good solution.

Any help would be appreciated.

---

### Post by gmargo on 2011-06-13
One simple method to sort a list of files by last modification time (create time is not stored):
```

ls -t $(cat list.txt)

```If the list is very long, you might need a fancier solution, such as:
```

cat list.txt | xargs -d '\n' stat --format="%Y %n" | sort -nr | cut -d ' ' -f 2-

```

---

### Post by kaibob on 2011-06-13
Gmargo has already answered your question, but I thought I would mention one item. Your list of files contains a directory, and because of that gmargo's first solution may not work as you want. This can easily be dealt with or instead use the second solution.

---

### Post by honeybear on 2011-06-14
> **gmargo said:**
> One simple method to sort a list of files by last modification time (create time is not stored):
```

ls -t $(cat list.txt)

```If the list is very long, you might need a fancier solution, such as:
```

cat list.txt | xargs -d '\n' stat --format="%Y %n" | sort -nr | cut -d ' ' -f 2-

```

thanks a lot ... som e progresses, a little

```
clear ; cat /home/companies.log  | xargs -d '\n' stat --format="%Y %n" | sort -nr | cut -d ' ' -f 2-   | while read i  ; do     [ -f "$i"  ] && echo "$i    `du -hs "$i"  | cut -f 1`     `date -r "$i" +%Y%m%d-%H%M%S`  " ;  done 
```


I tried this, but it is NOT working :( :


> 


if  [ "$1" = "" ] ; then
        echo "Input needed"
        exit
        exit
fi


find   "$1"   -iname "*$2*" > "/tmp/search.log"

clear ; cat "/tmp/search.log"   | xargs -d '\n' stat --format="%Y %n" | sort -nr | cut -d ' ' -f 2-   | while read i  ; do     [ -f "$i"  ] && echo "$i    `du -hs "$i"  | cut -f 1`     `date -r "$i" +%Y%m%d-%H%M%S`  " ;  done 







---

### Post by gmargo on 2011-06-15
I'm not exactly sure what output format you're looking for, but the following might help get there.  I tossed in a few hopefully self-explanatory tricks.
```

#!/bin/sh

# Parse arguments if any.
if [ $# -ne 2 ]; then
    echo "Two arguments required"
    exit 1
fi

# Set up temp file and trap to remove it at end.
TMP=/tmp/search.$$
trap 'rm -f "$TMP" ; exit 0' 0 1 2 3 15

# Perform the find
find "$1" -iname "*$2*" > "$TMP"

# In case this is 'bash' instead of 'dash',
# make bash's echo interpret escape characters by default.
if [ "$BASH" ] ; then
    shopt -s xpg_echo
fi

# Pretty-print results
cat "$TMP" | xargs -d '\n' stat --format="%Y %n" | sort -nr | cut -d ' ' -f 2- | \
while read NAME ; do
    if [ -f "$NAME" ] ; then
        SIZE=$(du -hs "$NAME" | awk '{print $1}')
        DATE=$(date -r "$NAME" +"%Y%m%d-%H%M%S")
        #echo "NAME=$NAME"
        #echo "SIZE=$SIZE"
        #echo "DATE=$DATE"

        # What is the desired output format?
        echo "${NAME}\t${SIZE}\t${DATE}"
    fi
done

```

---

