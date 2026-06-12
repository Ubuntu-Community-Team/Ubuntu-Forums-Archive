---
title: "ubuntu 9.04 screen resolution greater than 800x600 not possible"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by joe2005 on 2009-11-02
I have installed ubuntu 9.04 along with windows in mutiboot.How ever my screen resolution  cannot be increased greater than 800x600.THis problem not felt in ubuntu 9.04.HOw do I go about to solve this?

---

### Post by g160689 on 2009-11-02
what graphics driver do you use?
accordingly install the suitable package.

---

### Post by Sarai the Geek on 2009-11-02
> **joe2005 said:**
> I have installed ubuntu 9.04 along with windows in mutiboot.How ever my screen resolution  cannot be increased greater than 800x600.THis problem not felt in ubuntu 9.04.HOw do I go about to solve this?

Are you using 9.10 or 9.04? Your message says 9.04 but you go on to say that you didn't have the problem in 9.04 so...


In any case, this is almost certainly a graphics card driver issue. Go to System>Hardware Drivers and look for an item on the list that says something like "nvidia", "ati", "graphics card driver" etc. If there's nothing there, paste this bit of text into a terminal and post the output here:
```
lspci | grep VGA
```

---

### Post by joe2005 on 2009-11-02
My mistake in typing 9.04 instead of 9.10.changed from 9.04 to 9.10. sorry
Pasted as desired
joe@joe-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)

---

### Post by Sarai the Geek on 2009-11-02
You're in luck- 9.04 had some issues with Intel graphics cards that they're saying are resolved with this driver. Run this command:

```
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel
```

Once it's done, reboot and try changing your resolution again.

---

### Post by joe2005 on 2009-11-02
Thanks for the response.But no joy.
My terminal says this
xserver-xorg-video-intel is already the newest version.

any further clues please?

---

### Post by Sarai the Geek on 2009-11-02
> **joe2005 said:**
> Thanks for the response.But no joy.
My terminal says this
xserver-xorg-video-intel is already the newest version.

any further clues please?

```
gedit /etc/x11/xorg.conf
```

And paste that document here.

---

### Post by joe2005 on 2009-11-02
I suppose the code to be written in terminal.Did the same am getting a blank gedit page.hope i did ok.

---

### Post by bkratz on 2009-11-02
> **joe2005 said:**
> I suppose the code to be written in terminal.Did the same am getting a blank gedit page.hope i did ok.



I'm not totally sure but I think you have to preface that with gksudo

"gksudo gedit /etc/X11/xorg.conf"

---

### Post by halitech on 2009-11-02
actually the proper location is /etc/X11/xorg.conf so the command would be
```
gksudo gedit /etc/X11/xorg.conf
```

linux is case sensitive so x11 is not the same as X11

---

### Post by joe2005 on 2009-11-02
I am getting blank gedit page.Searching for files found there is a zip file named xorg.conf.5.gz in folder  /usr/share/man/man5.

---

### Post by bkratz on 2009-11-02
> **joe2005 said:**
> I am getting blank gedit page.Searching for files found there is a zip file named xorg.conf.5.gz in folder  /usr/share/man/man5.



I ran into the same problem since xorg has bee deprecated and had to create a blank one with the following command before editing the horizontal and vertical refresh rates with the rates for the monitor used.

sudo dpkg -reconfigure -phigh xserver-xorg

This creates a minimal configuration if one does not exist.     Then get the correct rates and insert them appropriately.  Give me a few minutes first so I can verify the command before doing!

---

### Post by Roger Allott on 2009-11-02
You're having the same problem that I had. Look at [this thread]("http://ubuntuforums.org/showthread.php?t=1287287").

The root cause of the problem is that 9.10 relies upon ubuntu autodetecting your hardware. Versions up to 9.04 used a configuration file called xorg.conf that was found in your /etc/X11/ folder, but 9.10 doesn't do that. However, 9.10 **will** use the settings in that file/location if it exists.

So, you need to create an xorg.conf file from scratch. The posts at the end of [the thread]("http://ubuntuforums.org/showthread.php?t=1287287") (and the pages linked from them) explain what you need to do.

---

### Post by travmanx on 2009-11-02
Edit my idea will not work with 9.10 since it uses autodetect features rather than xorg...

---

### Post by joe2005 on 2009-11-02
Somehow managed to create xorg.conf.but it sits on home.I do not know how to move this file to /etc/X11.help wanted

---

### Post by Sarai the Geek on 2009-11-03
> **joe2005 said:**
> Somehow managed to create xorg.conf.but it sits on home.I do not know how to move this file to /etc/X11.help wanted

Well, this bit of code should do it-

```
sudo mv ~/xorg.conf /etc/X11/
```

*However*, I don't think that it's supposed to be created in home to begin with, so if that part of creation went wrong it's possible something else did too. What did you do to create it?

---

### Post by joe2005 on 2009-11-03
as pointed out in [http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283), I went in to console shell and stopped x.
Then I found the file xorg.conf.new. in/home/joe
The contents of the file are as follows
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "record"
	Load  "glx"
	Load  "dri"
	Load  "dbe"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82G35 Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
You may please go through.If it is ok,tell me also how to put this file into /etc/X11
Waiting anxiously for your reply with bated breath.

---

### Post by Roger Allott on 2009-11-03
> **joe2005 said:**
> as pointed out in [http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283), I went in to console shell and stopped x.
Then I found the file xorg.conf.new. in/home/joe
The contents of the file are as follows

<snip>

You may please go through.If it is ok,tell me also how to put this file into /etc/X11
Waiting anxiously for your reply with bated breath.

The file that you've copied/pasted has indents (tab characters) that make it much easier to read, but we don't see them in plain html. If you paste the text into the textbox, please remember to put code tags around it, which preserves the indentation.

Highlight the text you paste from the xorg.conf.new file, and click the # symbol (third from right) immediately above the textbox to wrap code tags as needed.

---

### Post by joe2005 on 2009-11-03
I am somewhat unfamiliar with forum postings.However I have copied the xorg.cnf file under code.hope this is ok.thanks

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "record"
	Load  "glx"
	Load  "dri"
	Load  "dbe"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

SectionSection "Monitor"
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 31.5 - 50
    VertRefresh 50-110
EndSection
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82G35 Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection[CODE]
```[/CODE]

---

### Post by Roger Allott on 2009-11-03
You've amended that conf file, I presume, to insert code that I was told to insert when I had my similar problem. However, you should note that those settings were appropriate for **my** set-up, which is possibly quite considerably different to yours.

Also, you've now got 2 Screen sections in the file. My guess is that the second section over-rides the first one, but it's only a guess.

What screen size **should** your monitor display?

---

### Post by joe2005 on 2009-11-03
prefer 1024 by 768.Meanwhile I made mistake somewhere suddenly desktop disappeared and a black screen log in appeared.Since at my wits end reinstalled 9.10 and iin the bargain I lost the.conf file uploaded to the forum.Kindly guide me keeping in mind my misadventure.thanks

---

### Post by joe2005 on 2009-11-04
The problem screen resolution is yet to be resolved.
Suppose I install 9.04  and copy the xorg.conf and install back 9,10 duly putting the copied conf into /etc/x11 will it work? is it worth the effort?Request Gurus to consider and advise.thanks

---

### Post by joe2005 on 2009-11-08
I have reverted to ubuntu 9.04.Bye 9.10

---

### Post by joe2005 on 2009-11-20
With the help of an excellent guide vide [http://ubuntuforums.org/showthread.php?p=8302145#post8302145](http://ubuntuforums.org/showthread.php?p=8302145#post8302145) I configured my screen resolution  to 1028x and above.Thanks very much

---

