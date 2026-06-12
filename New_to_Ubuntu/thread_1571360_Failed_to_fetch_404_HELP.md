---
title: "Failed to fetch 404 HELP"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Frau_Munitz on 2010-09-09
Hi, I'm new to Ubuntu and I LOVE it, but since yesterday I keep getting theses error messages every time the update manager tries to look for updates. How can I fix this?

Failed to fetch [http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Also, today my mail and volume icons dissapeared from the panel. I tried the "add panel" option but there isn't any volume or mail button.

Thanks for your help in advance :)
-VM

---

### Post by beew on 2010-09-09
Don't worry about the 404, it is probably some problems with the server's end or that you have a poor internet connection. Try it later. That happens to me all the time. It usually works in a few days if not a few hours. Since this is most likely not a problem at your end there is nothing you can do except wait.

To get the mail and volume icons back, right click on the panel, choose add to panel and then add the indicator applet.

---

### Post by Frau_Munitz on 2010-09-09
> **beew said:**
> Don't worry about the 404, it is probably some problems with the server's end or that you have a poor internet connection. Try it later. That happens to me all the time. It usually works in a few days if not a few hours. Since this is most likely not a problem at your end there is nothing you can do except wait.

To get the mail and volume icons back, right click on the panel, choose add to panel and then add the indicator applet.

Beew, thanks for the icons it helped a lot :p

With the 404 i tried changing the servers and it didn't work, i have an ethernet connection so i dont think its related to a network problem :(

---

### Post by marl30 on 2010-09-09
Here is a scrip for restoring the panel to default, if you find it difficult to get it back to how it was. Simply open gedit. Copy and paste the script into it. Then save it as PanelRestore.sh. Save it to your desktop or whichever folder you want to be placed. Close it, then right click on the saved gedit document. Go to properties, select permissions, and tick allow executing file as program. All you do from there on is double click, then choose to open in terminal. Next, follow the instructions given to restore your panel to default. 
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

### Post by beew on 2010-09-09
How did you change the server? You are using a ppa from launchpad, it is not in any of the Ubuntu servers.

---

### Post by coffeecat on 2010-09-09
@Frau_Munitz, if you click on the url for your first 'Failed to fetch...' in Firefox, you get a 404 and...

> The requested URL /user/ppa-nameppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz was not found on this server.... and your full url is

> [h t t p://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz]("http://ppa.launchpad.net/user/ppa-nameppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz")That is not a valid URL. (I've has to put spaces in http to stop the forum software truncating it.)

Where did you get the instructions for setting up your PPA repository? It looks as though you copied and pasted from a howto url and the /user/ppa-nameppa/ bit was meant to be changed to the PPA that you were trying to setting up. If you post more detail of how you tried to set up a PPA repository and which PPA you were wanting, someone will put you right.

---

### Post by Frau_Munitz on 2010-09-09
> **coffeecat said:**
> @Frau_Munitz, if you click on the url for your first 'Failed to fetch...' in Firefox, you get a 404 and...

... and your full url is

That is not a valid URL. (I've has to put spaces in http to stop the forum software truncating it.)

Where did you get the instructions for setting up your PPA repository? It looks as though you copied and pasted from a howto url and the /user/ppa-nameppa/ bit was meant to be changed to the PPA that you were trying to setting up. If you post more detail of how you tried to set up a PPA repository and which PPA you were wanting, someone will put you right.

Hi!
the only thing that i remember doing with the terminal i think was when i tried to install dvd, mp3, mp4, avi etc playback...
could that be the reason?
:sad:

when i go to "software sources" i see this
[IMG]http://i5.photobucket.com/albums/y168/lechuguita/softwaresources.png[/IMG]

---

### Post by coffeecat on 2010-09-10
> **Frau_Munitz said:**
> the only thing that i remember doing with the terminal i think was when i tried to install dvd, mp3, mp4, avi etc playback...
could that be the reason?
Possibly. There might have been a command in that which added the PPA with the non-existent URL. Do you remember where you found the instructions for adding those things? Can you post a link? Then we can see what was intended and put you right for the correct PPA.

In the meantime, simply uncheck the two boxes against the launchpad URLs with 'user/ppa-nameppa' in them in Software Sources. That will stop those 404 errors. Leave the other Launchpad (banshee-team) ticked. Since you have one PPA, the instructions you were following must have included two (or three) PPAs, and one was correct.

As a general thought. PPAs are useful but most people don't need them for the sort of multimedia stuff you listed. PPAs are really for experimental things and the latest versions (often Beta) of software not yet in the repositories. I wouldn't be surprised if the instructions you found were from some enthusiast's blog on the net somwhere. You're much better off with the Ubuntu documentation for this sort of thing. I'll find a link for you and add this to my post as soon as I've found it.

**Edit:** here are some links for you, all from [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/). It's worth searching that for Ubuntu-related stuff.

Multimedia : [https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

Restricted formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Frau_Munitz on 2010-09-11
> **coffeecat said:**
> Possibly. There might have been a command in that which added the PPA with the non-existent URL. Do you remember where you found the instructions for adding those things? Can you post a link? Then we can see what was intended and put you right for the correct PPA.

In the meantime, simply uncheck the two boxes against the launchpad URLs with 'user/ppa-nameppa' in them in Software Sources. That will stop those 404 errors. Leave the other Launchpad (banshee-team) ticked. Since you have one PPA, the instructions you were following must have included two (or three) PPAs, and one was correct.

As a general thought. PPAs are useful but most people don't need them for the sort of multimedia stuff you listed. PPAs are really for experimental things and the latest versions (often Beta) of software not yet in the repositories. I wouldn't be surprised if the instructions you found were from some enthusiast's blog on the net somwhere. You're much better off with the Ubuntu documentation for this sort of thing. I'll find a link for you and add this to my post as soon as I've found it.

**Edit:** here are some links for you, all from [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/). It's worth searching that for Ubuntu-related stuff.

Multimedia : [https://help.ubuntu.com/community/Multimedia](https://help.ubuntu.com/community/Multimedia)

Restricted formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Coffee cat, thanks a lot for your help /I unmarked all the 'ppa-name' that appeared in the Software Sources and I no longer have the 404 problem. Thanks for the links, I'll bookmark them for further reference.
:)
:D

---

