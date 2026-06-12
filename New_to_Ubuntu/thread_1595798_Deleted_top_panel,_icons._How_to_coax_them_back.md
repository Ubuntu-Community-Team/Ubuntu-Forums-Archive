---
title: "Deleted top panel, icons. How to coax them back?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by becketma on 2010-10-13
I thought I had double icons on the top panel.  When I deleted the duplicate icon the entire top panel with all of the other icons disappeared.

How do I get the top panel with the icons back?

Best from Tucson
Bob

---

### Post by TeoBigusGeekus on 2010-10-13
Open terminal and type 
```
gnome-panel
```

---

### Post by spillage2 on 2010-10-13
Hi,

run this .sh file and if you make any changes use this to back up your panels just in case.
```

#!/bin/sh
#
# GNOME Panel Save / Restore
# Writen by PhrankDaChicken
#
# http://ubuntu.online02.com
#
#
# Updated to add restore defaults by jimjimovich
# http://www.starryhope.com
#
#


DIR=$(pwd)
TITLE="PanelRestore"

Main () {
    CHOICE=$(zenity --list --title "$TITLE" --hide-column 1 --text "What do you want to do?" --column "" --column "" \
"0" "Save Panel Settings" \
"1" "Restore Panel Settings" \
"2" "Restore Default Panel Settings")
    if [ $CHOICE = 0 ]; then
        Panel_Save
    fi
    if [ $CHOICE = 1 ]; then
        Panel_Restore
    fi
    if [ $CHOICE = 2 ]; then
        Panel_Defaults
    fi    
}

Panel_Restore () {
    FILE=$(zenity --title "$TITLE: Open File" --file-selection --file-filter "*.xml" )
    if [ -n "$FILE" ]; then 
        gconftool-2 --load "$FILE"
        killall gnome-panel
    fi
    Main
}

Panel_Save () {
    FILE=$(zenity --title "$TITLE: Save File" --file-selection --save --confirm-overwrite --filename "Gnome_Panel.xml" --file-filter "*.xml" )
    if [ -n "$FILE" ]; then 
        EXT=$(echo "$FILE" | grep "xml")
        if [ "$EXT" = "" ]; then
            FILE="$FILE.xml"
        fi
        gconftool-2 --dump /apps/panel > $FILE
        zenity --info --title "$TITLE: File Saved" --text "File saved as: \n $FILE"
    fi
    Main
}

Panel_Defaults () {
    zenity --question --text="Are you sure you want to restore the default top and bottom panels?"
    gconftool-2 --recursive-unset /apps/panel
    rm -rf ~/.gconf/apps/panel
    pkill gnome-panel
    exit
}

Main

# END OF Script
```

---

### Post by keroman on 2010-10-13
**Re: Top panel has gone missing !!!** 			
 			 			 		   		 		 		this is what I did to get panels back 
[http://www.watchingthenet.com/restor...-settings.html]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html")

if you do this you should have a backup on your desktop
[http://www.starryhope.com/linux/ubun...els-in-ubuntu/]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/")

---

### Post by yunone on 2010-10-13
> **keroman said:**
> **Re: Top panel has gone missing !!!** 			
 			 			 		   		 		 		this is what I did to get panels back 
[http://www.watchingthenet.com/restor...-settings.html]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html")

if you do this you should have a backup on your desktop
[http://www.starryhope.com/linux/ubun...els-in-ubuntu/]("http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/")

thank you!

---

