---
title: "vlc memory limit script"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by alayoyo on 2011-04-29
I think i found the source of this problem i had before:[http://ubuntuforums.org/showthread.php?t=1637565](http://ubuntuforums.org/showthread.php?t=1637565)
It is a vlc memory leak (once i hear it swapping, computer is 98% unresponsive and i have to hit reset button). Some threads mention this bug being related to KDE libraries (i do have kde desktop installed to try it out. [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) returned errors when i tried it.)

I found a sort-of solution here [http://www.andymillar.co.uk/blog/2010/03/17/limiting-vlc-memory-usage/](http://www.andymillar.co.uk/blog/2010/03/17/limiting-vlc-memory-usage/)

which says to use the script
```

[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Lucida Grande][COLOR=#110000][COLOR=#666666]*#!/bin/bash*[/COLOR] 
[COLOR=#7A0874]**source**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]profile 
[COLOR=#7A0874]**ulimit**[/COLOR] [COLOR=#660033]-v[/COLOR] [COLOR=#000000]1048576[/COLOR] 
vlc
[/COLOR]
```

[/FONT][/COLOR][/FONT][/COLOR]Could someone say how to 'use' this script? I would like this effect to be permanant and automatically apply to each time i run vlc (including clicking on a video file in nautilus)

or if there is a superior solution i am all ears

thanks.

---

### Post by Fanas on 2011-05-02
Yeah, I would like to know that too.

---

### Post by KIAaze on 2011-05-02
[LIST=1]
[*]Create a text file in your home directory named "vlc.sh" containing:
```
#!/bin/bash 
source /etc/profile 
ulimit -v 1048576 
vlc $@

```

[*]Move it to /usr/bin:
```

# mv is the move command
# -i makes it ask you for confirmation in case a file with the same name already exists
# -v makes it print out what it does
sudo mv -iv ~/vlc.sh /usr/bin/
```

[*]Make it executable:
```
sudo chmod +x /usr/bin/vlc.sh
```

[*]Associate your video files with the script:
-In nautilus, right-click on any video file, go to "open with->other application...".
-In custom command, type "/usr/bin/vlc.sh".
-make sure to select "remember this application for this type of file"

[*]Modify your vlc shortcuts:
-Right-click the application bar and choose "edit menus".
-Search for your VLC shortcut and double-click it.
-Replace the command "vlc %U" with "/usr/bin/vlc.sh %U".
[/LIST]

_Some instructional notes:_
1) You can of course give the script any other name and save it wherever you want, as long as you adapt the location of the binary accordingly, i.e. replace "/usr/bin/vlc.sh" with the appropriate path.
2) If placing the script in /usr/bin or any other location included in your PATH environment variable, it shouldn't be necessary to specify the full path in the shortcuts/file associations, i.e you could write vlc.sh instead of /usr/bin/vlc.sh
3) You could rename the vlc binary (/usr/bin/vlc) to something different like "vlc.bin", replace "vlc" in the script with the new name "vlc.bin" and name the script itself "/usr/bin/vlc". That way you don't have to fix all the shortcuts/file-associations. But I don't recommend this method since it will probably break during upgrades of vlc.

---

### Post by Fanas on 2011-05-03
Thank you. You sir, are a gentleman and a scholar.

---

### Post by Fanas on 2011-05-03
One more thing, that's driving me crazy.
Where is vlc emblem stored, I wish to assign it to the script.

---

### Post by KIAaze on 2011-05-03
```
/usr/share/icons/hicolor/48x48/apps/vlc.png
```
:)

The easiest way to find it, is simply to try to modify the icon of the original shortcut.

Two other ways to find icons:
1) Use locate to find files:
```
sudo updatedb
locate APPNAME.png

```
2) Search for paths containing "icon" in the list of contents of the package:
```
dpkg -L PACKAGENAME | grep icon
```

---

### Post by Fanas on 2011-05-04
Ok I assigned that emblem but it appears properly on the sidebar only when I run the script directly, if I open video file still the default appears.

---

### Post by KIAaze on 2011-05-08
Are you using unity? I still use Gnome classic at the moment, but I'll have a look once I have time.

---

### Post by Fanas on 2011-05-09
> **KIAaze said:**
> Are you using unity? I still use Gnome classic at the moment, but I'll have a look once I have time.

Yeah, I'm getting used to it. Might as well, if we are sticking with it.

---

### Post by pe1dnn on 2011-05-15
The setup can be even simpler so here is no need to associate video files with the scripts and everything keeps working, including the icon and references from Gnome or Unity.

Additional steps:

In /usr/bin rename vlc to vlc_exe

[FONT=Courier New]$ sudo mv vlc vlc_exe[/FONT]

Then rename the script to take its place

[FONT=Courier New]$ sudo mv vlc.sh vlc[/FONT]

Edit "vlc"  and change vlc $@ to vlc_exe "$@" (best do this already when creating the script...)

B.t.w. I've put quotes around the $@ otherwise it doesn't work for files and paths with spaces in the name.

Advantage: everyone starting vlc will now use the script, including the Unity's start application. Also the icon is still associated with vlc, which is now our script.
Disadvantage: package checking will find a md5sum mismatch for "/usr/bin/vlc" and update/reinstall of vlc will overwrite the script. This can however also be seen as an advantage, hopefully future vlc versions will address the issue. The only real drawback is that vlc_exe will be left as unused junk in that case. If vlc is not fixed (or work arround if the problem is not inside VLC itself) then the hack has to be applied again.

I hope VLC will come up with a workaround. Even if it is a pulse-audio problem, other players do not seem to have this problem. But VLC is better than the others (otherwise I would switch).

---

