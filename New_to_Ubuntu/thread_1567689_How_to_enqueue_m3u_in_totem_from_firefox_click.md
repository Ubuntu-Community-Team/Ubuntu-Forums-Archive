---
title: "How to enqueue m3u in totem from firefox click"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by InuY4sha on 2010-09-04
Just a hint:

create a bash script "totem-enqueue.sh" in /usr/bin and paste this content in that:

```
#!/bin/bash
cat "$1" > /tmp/log
/usr/bin/totem --enqueue "$1"
```

Now make it executable and from firefox, Edit->Preferences -> filter by "mp3" and "use other..." -> select the above mentioned script and you're done! :D

Tchuess..
R

---

### Post by stoian on 2012-01-22
here is a script to enqueue all audio files in totem.
you can use it directly in the command window, or you can copy the executable script in your ~/.gnome2/nautilus-scripts folder and then you'll be able to execute it by right clicking in a current folder in nautilus.

```

#!/bin/bash
#

# replace the default delimiter/spacer
old_IFS=${IFS}
IFS='
'

# when running from nautilus-scripts, it useful to find the current folder
base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"
if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi

if [ "$dir" != "" ]; then
  cd "$dir"
fi

# get the list of files, sorted, one on each line
FILES=`find . -type f -regex '^.+\.\(mp3\|flac\|wav\|ogg\|wma\|m4a\)$' | sort`
allfiles=""
for FILE in ${FILES}
do
  fn=$(readlink -f "$FILE")
  #echo $fn
  allfiles="${allfiles}$fn${IFS}"
done
#echo "all files = ${IFS}$allfiles"
totem --enqueue $allfiles
# restore the original default delimiter/spacer
IFS=${old_IFS}


```

In case you want to use audacious, replace this line:
```
totem --enqueue $allfiles
```
with this one:
```
audacious -e $allfiles
```

Enjoy!

---

