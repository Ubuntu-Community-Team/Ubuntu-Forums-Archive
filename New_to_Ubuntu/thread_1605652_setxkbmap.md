---
title: "setxkbmap"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2010-10-25
Hi All,

I use a really cool utility called Auto Key to paste in phrases I often use, like my email address or home address.
The problem is that Auto Key doesn't recognize when I switch keyboard layouts using the panel applet. This results in the ä in my address, for example, being dropped.

I need to use setxkbmap

I can type setxkbmap us or setxkbmap se in a terminal window to change the layouts, but I'd realy like to have a hot key or launcher to do this.  How can I set up a hot key or launcher to run the setxkbmap command?

I know it involves a Bash file, but I'm lost as to the specifics.

I'd appreciate any help.

---

### Post by sisco311 on 2010-10-28
EDIT: fixed the scrip to handle the case when the current language is not in the list of languages.

Hi,

I wrote a little bash script for you:
```
#!/bin/bash

# List of languages, you can add more, e.g. LANGS=(en se hu ro)
**LANGS=(us se)**

# Set it to "true" to enable notification
# NOTE: libnotify-bin must be installed
**NOTIFY="false"**

# Path to the flag icons:
[b]ICONPATH="/home/sisco/.icons/flags/png"
[/b]
NOTIFYARGS="-h string:x-canonical-private-synchronous:true -h string:x-canonical-private-icon-only: \"notify\" "

CURRENT_LANG=$(setxkbmap -print | awk -F+ '/xkb_symbols/{print $2}')

i=0
while [[ $CURRENT_LANG != ${LANGS[$i]} ]] && [COLOR="Red"][[ $i < $((${#LANG[@]}-2)) ]][/COLOR]; do
    i=$((i+1))
done

if [[ $i = $((${#LANGS[@]}-1)) ]]; then
  NEWLANG=${LANGS[0]}
else
  NEWLANG=${LANGS[$((i+1))]}
fi

setxkbmap $NEWLANG

echo $NEWLANG
if [[ $NOTIFY = "true" ]]; then
  notify-send -i "$ICONPATH"/$NEWLANG.png $NOTIFYARGS
fi

```

Simply save it in a file and make it executable. 

If you want to enable notification, then install the libnotify-bin package, download the flags from: [http://www.famfamfam.com/lab/icons/flags/](http://www.famfamfam.com/lab/icons/flags/) , extract the zip file, adjust the **ICONPATH** variable to point to the png directory and set the value of **NOTIFY** to "true".

---

### Post by GrouchyGaijin on 2010-10-28
Thank You!!

---

### Post by ubunterooster on 2010-10-28
Add to panel>custom application launcher.
Name it "US keyboard" (or whatever you want) you want but put the following into the "command" entry```
setxkbmap us
```

Add a second but call it "SE keyboard" and set the command to ```
setxkbmap se
```

---

### Post by GrouchyGaijin on 2010-10-28
@sisco311 and ubunterooster,

Thank you guys so much.  Particularly you sisco311, it is so unbelievably cool of you to write that script for me.

I really appreciate it.:popcorn:

---

### Post by sisco311 on 2010-10-28
I used to use setxkbmap too, because I don't switch the keyboard layout too often. But I think, from now on, I will use my script. Already assigned a keyboard shortcut for it. 

So thanks for asking the question. :)

EDIT: Fixed the script.

---

