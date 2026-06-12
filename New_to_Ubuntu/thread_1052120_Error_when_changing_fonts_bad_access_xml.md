---
title: "Error when changing fonts bad access xml"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-27
Well, I pretty much have Intrepid running well. Now I want to personalize it a bit. I tried to reset the font, using the code from the help manual, and got this.
```
daniel@GLENDA:~$ gconftool-2 --direct --config-source xml : readwrite : /etc/gconf/gconf .xml.mandatory --type string --set /desktop/gnome/interface/font_name "Sans 12"

(gconftool-2:8575): GConf-WARNING **: Failed to load source "xml": Couldn't resolve address for configuration source: Bad address `xml'
**
GConf:ERROR:gconftool.c:939:main: assertion failed: (err == NULL)
Aborted

```
Any help in correcting this will be appreciated. And I would appreciate an explanation rather than just "change this". Or point me in the direction of an explanation. One of these days I plan to be on the answer side of the table, instead of the question side.
[COLOR="White"]aa[/COLOR]

---

### Post by LowSky on 2009-01-27
What help manual told you to do it that way?

You can easily change the font from

system>Prefences>appearance

---

### Post by Lostin60's on 2009-01-27
> **LowSky said:**
> What help manual told you to do it that way?

You can easily change the font from

system>Prefences>appearance

The help manual that is accessed from the top panel. And I am aware that I can do it through the GUI, but that teaches me nothing, and the whole point of using Ubuntu is to learn all I can about running the system. All the other good stuff about using Ubuntu is just icing on the cake to me.  Also I don't believe I can set font colors there.
[COLOR="White"]aa[/COLOR]

---

### Post by unutbu on 2009-01-27
Thanks for cluing me in to the interesting Help documentation. It's quite interesting! How did you navigate to the page 
"GNOME Desktop System Administration Guide>Using GConf>To Set Preference Values"? I had to search for GConf...

Anyway, I think you have essentially the right command, but need to remove some spaces.

To change the default font_name for the current user:
```

gconftool-2 --type string --set /desktop/gnome/interface/font_name "Sans 12"
```

To change the default font_name for all users system-wide:
Reboot into Recovery Mode. Drop to a root shell. Then type:
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string --set /desktop/gnome/interface/font_name "Sans 12"

```
Note that the user can override the system-wide default.

To make the default font_name mandatory (and unchangable by normal users):
Reboot into Recovery Mode. Drop to a root shell. Then type:
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type string --set /desktop/gnome/interface/font_name "Sans 12"

```

---

### Post by Lostin60's on 2009-01-27
> **unutbu said:**
> Thanks for cluing me in to the interesting Help documentation. It's quite interesting! How did you navigate to the page 
"GNOME Desktop System Administration Guide>Using GConf>To Set Preference Values"? I had to search for GConf...

Anyway, I think you have essentially the right command, but need to remove some spaces.

To change the default font_name for the current user:
```

gconftool-2 --type string --set /desktop/gnome/interface/font_name "Sans 12"
```

To change the default font_name for all users system-wide:
Reboot into Recovery Mode. Drop to a root shell. Then type:
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string --set /desktop/gnome/interface/font_name "Sans 12"

```
Note that the user can override the system-wide default.

To make the default font_name mandatory (and unchangable by normal users):
Reboot into Recovery Mode. Drop to a root shell. Then type:
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type string --set /desktop/gnome/interface/font_name "Sans 12"

```

First off from the desktop top panel Help>type background in the search box>in next window click GNOME Desktop System Administration Guide>1.7.2 & 1.7.1 That is how I got to the info. I used background because I am going to use a Dali pic as my background (I hope). I am also changing fonts. Now I am going to follow your suggestion. (playing Jeopardy tune) I'm back. So, I rebooted into recovery and dropped to root, and entered.
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string --set /desktop/gnome/interface/font_name "Sans 12"
```
The return was Error parsing options  Unknown option (--set /desktop/gnome/interface/font_name). I tried using help, but the info I wanted scrolled off the screen. 
So, along with any ideas you may have, tell me how close this is..remember I am super-noob..lol. 
This coding says
 (gconftool-2 = open this tool) (--direct = I have no idea on this one) (\ = I am not done, so ignore <enter>) (config-source = config the following, which is a source) (xml = not sure, move or store data via xml?) (readwrite = my permissions) (/etc/gconf gconf.xml.defaults = the file to configure)(--type string = type or insert the the following string into /etc/gconf/gconf.xml.defaults) (--set = make the configuration permanent) (/desktop/gnome/interface/font_name "Sans 12" = the string to type) Also the ( -- and : ) I think the : is a delimiter but I have no idea on the --. I am trying to learn C++, and bash, and the eclipse environment all at once, and I can use all the help I can get. The bash is coming along, because I use point and click as little as possible. Well, let me know what you think.
[COLOR="White"]aa[/COLOR]

---

### Post by unutbu on 2009-01-27
Hm. I've tried the command I posted. It seems to work for me.

However, I just stumbled upon a different way to do this, which may be easier since it does not involve rebooting:
```

sudo gconftool-2 --shutdown
sudo gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string --set /desktop/gnome/interface/font_name "Sans 12"
sudo gconftool-2 --spawn

```
I don't get any errors when I issue these commands. After the second command, the file /etc/gconf/gconf.xml.defaults/%gconf-tree.xml should be created. 

The "--shutdown" and "--spawn" commands were found here:
[http://wiki.novell.com/images/8/8a/Quick_Reference_15_UNIX-Linux_GNOME_Administration.pdf](http://wiki.novell.com/images/8/8a/Quick_Reference_15_UNIX-Linux_GNOME_Administration.pdf)

The meaning of all the gconftool-2 options are also documented here:
```

man gconftool-2

```
However, the syntax "xml:readwrite:/etc/gconf/gconf.xml.defaults" is a little weird (to me) and not covered in the man page. This syntax is also mentioned in the Quick_Ref... pdf link above, as well as here: [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/).

You might also want to try 
```

gconftool-2 --type string --set /desktop/gnome/interface/font_name "Sans 12"
```

just to see if you can get it to work without any errors.

Finally, to change your background image, try this:
```

gconftool-2 -t string -s /desktop/gnome/background/picture_filename /path/to/image.jpg
gconftool-2 -t string -s /desktop/gnome/background/picture_options scaled

```

---

### Post by Lostin60's on 2009-01-30
I didn't try this in recovery again yet. I thought I would see what sudo did. I put in -v to see if I could see what the command was doing. I thought it would print the actions as they occured. OOPS. What it did give me is the code in red. Do you know what that means?

```
daniel@mypos:/$ sudo gconftool-2 [COLOR="Blue"]-v[/COLOR] --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/interface/font_name "Sans 12"
[COLOR="Red"]2.24.0[/COLOR]
```
[COLOR="White"]aa[/COLOR]

---

