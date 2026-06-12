---
title: "[SOLVED] brick wall"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by garrydog on 2008-12-23
Hi
I have Ubuntu installed along with windows xp on my hard drive ,
when i boot in ubuntu all i get is a blank screen ,the only thing i can do is ,when i press escape i get a fast druming sound .
Can someone help .
Thanks David .

---

### Post by ibizatunes on 2008-12-23
How did you install ubuntu? Live cd or alternative? Did you check the cd after you burnt it? How much RAM do you have? What graphic card do you have?

---

### Post by ByteJuggler on 2008-12-23
This sounds like graphics driver problems... When you press ctrl-alt-f1, do you get to the text mode console?  If so, log in there, then try the following as a first port of call.  At the prompt type (and press enter after each command):

> sudo apt-get update
sudo apt-get upgrade
sudo dpkg-reconfigure xserver-xorg -phigh

Then try to reboot.  You can do that by entering:

> shutdown -r now

The idea here is that perhaps some updates since release might deal with this issue.  (The black screen issue was more common than would've been ideal, and occurred mostly as I recall on systems with ATI graphics.)

Note, you can also manually configure more of your graphics setup by leaving off the "-phigh" above, e.g.
> sudo dpkg-reconfigure xserver-xorg

This will allow you to pick alternate drivers (and as a fallback, "vesa" should always work but will probably be relatively slow and probably will get the optimal resolution for your screen wrong.)

For reference, see [here]("http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure").

Edit: Corrected mistake, changing "dpk-reconfigure" -> "dpkg-reconfigure".   Sorry about the error.

---

### Post by garrydog on 2008-12-23
I installed it from live cd ,alternative .
I checked the cd before install.
I have 1gb of ram .
How do i find out what the type the graphics card is .
David .

---

### Post by garrydog on 2008-12-23
looking at device manager i think my graphics card is ATI radeon hd 2400 pro .

---

### Post by garrydog on 2008-12-23
I preesed alt ctrl f1 and got the text mode consol .but can't log in ,i type my login in and press enter ,it asks for a password but it will not allow me to type anything for the password .

---

### Post by Duck2006 on 2008-12-23
> **garrydog said:**
> I preesed alt ctrl f1 and got the text mode consol .but can't log in ,i type my login in and press enter ,it asks for a password but it will not allow me to type anything for the password .

When you type the pass word it don't show any thing this is normal, just press enter.

---

### Post by garrydog on 2008-12-23
tryed the post of ByteJuggler,the computer downloaded a lot of updates .then i tryed the line (sudo dpk-reconfigure xserver-xorg-phigh)command not found .This is doing my head in ,will i ever get this thing to work .

---

### Post by Duck2006 on 2008-12-23
If this is what tou typed in,

sudo dpk-reconfigure xserver-xorg-phigh

Try

sudo dpk-reconfigure xserver-xorg -phigh

There is a space between xorg and -phigh

---

### Post by decoherence on 2008-12-23
you mean

sudo dpkg-reconfigure xserver-xorg -phigh

there is no 'dpk-reconfigure' command, at least that i know about

---

### Post by LowSky on 2008-12-23
Its ```

sudo dpkg-reconfigure xserver-xorg -phigh
```

Duck2006 you forgot a 'g'

---

### Post by garrydog on 2008-12-23
Tryed the line with the space between xorg and -phigh command not found .

---

### Post by Duck2006 on 2008-12-23
Try what "decoherence and LowSky" posted i forgot the g in dpkg

---

### Post by garrydog on 2008-12-23
Yes tryed it (xserver-xorg is not installed and no info available)

---

### Post by ByteJuggler on 2008-12-23
> **garrydog said:**
> Yes tryed it (xserver-xorg is not installed and no info available)

No, then you're somehow not entering the command right.  Make sure you keep the capitalisation and spacing *exactly* the same.  I repeat, it's:

```
sudo     dpkg-reconfigure     xserver-xorg     -phigh 
```

I've added extra spaces to make it obvious where the spaces are.  As I also mentioned, you can leave out the "-phigh" bit, to have the opportunity to manually configure what driver to use and several other things.  

Please, if you try a command and run into a problem, *post back the exact error message* that you got so we can help. 

Edit: Sorry I seem to have a block, I've typed "dpkg-reconfigure" in 2 different posts now as "dpk-reconfigure".  Apologies for that!

---

### Post by Elfy on 2008-12-23
Has that command been changed again?- I thought it stopped working for video on hardy and was only good for kbd.

Might better run xfix from the recovery menu.

Did you install a desktop with the alternative cd or did you install a server.

---

### Post by ByteJuggler on 2008-12-23
> **forestpixie said:**
> Has that command been changed again?- I thought it stopped working for video on hardy and was only good for kbd.

Might better run xfix from the recovery menu.

Did you install a desktop with the alternative cd or did you install a server.

The command works, I checked before I posted it.  There must be a mistake in copying it onto the command line...  However your xfix suggestion is also good.  :)

---

### Post by Elfy on 2008-12-23
<snip>

---

### Post by ByteJuggler on 2008-12-23
OK, here's an alternative, this will run the updates, then run the reconfigure command. 

1.) Log in as before, then enter:
```

wget [http://tinyurl.com/82pskd](http://tinyurl.com/82pskd)

```

This should output the following:
> Resolving tinyurl.com... 195.66.135.131
Connecting to tinyurl.com|195.66.135.131|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://oomclan.game-host.org/share/script.txt](http://oomclan.game-host.org/share/script.txt) [following]
--2008-12-23 20:57:46--  [http://oomclan.game-host.org/share/script.txt](http://oomclan.game-host.org/share/script.txt)
Resolving oomclan.game-host.org... 217.155.59.137
Connecting to oomclan.game-host.org|217.155.59.137|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 75 [text/plain]
Saving to: `script.txt'

100%[======================================================================>] 75          --.-K/s   in 0s      

2008-12-23 20:57:46 (12.2 MB/s) - `script.txt' saved [75/75]


2.) Now enter exactly as shown:

```
sudo sh script.txt
```

This should perform updates, then run the X reconfiguration.  If you still get any errors, please post back what and I'll try to help.

---

### Post by garrydog on 2008-12-23
hi
Did the wget [http://tinyurl.com/82pskd](http://tinyurl.com/82pskd) ,the updates worked .then the dpkg-reconfigure ,I theen got a lot of stuff about keyboard configuration,did that the best I could ,I then ended up with this ,

xserver-xorg postinst warning: overwrighting possibly-cusomised configuration.
file;backupin/etc/x11/xorg conf.20081223230407.then it wanted an input,did not know what to type .

---

### Post by ByteJuggler on 2008-12-23
> **garrydog said:**
> hi
Did the wget [http://tinyurl.com/82pskd](http://tinyurl.com/82pskd) ,the updates worked .then the dpkg-reconfigure ,I theen got a lot of stuff about keyboard configuration,did that the best I could ,I then ended up with this ,

xserver-xorg postinst warning: overwrighting possibly-cusomised configuration.
file;backupin/etc/x11/xorg conf.20081223230407.then it wanted an input,did not know what to type .

[I]**EDIT/UPDATE:** That's all s fine, that's it, that's what I was trying to do.  
However, I owe you an apology.  I was under the impression that you can still manually configure the driver to use using dpkg-reconfigure.  However, you actually cannot anymore (since 8.04/Hardy), since Ubuntu is relying more on autodetection these days, so the above instructions will not have the desired results, although they're otherwise harmless.  

So bottom line is we must do something else to try to get your graphics going.  I was trying to avoid manually editing your config file but we might end up having to do that as a last resort. But first I'll try something else. 
[/I]

OK try this:

1.) Boot, go to the text console (ctrl-alt-f1) and log in.
2.) Enter:
> sudo apt-get install envyng-core
The system should install "envyng", outputting something like:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  envyng-core
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 120kB of archives.
After this operation, 897kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe envyng-core 2.0.1 [120kB]
Fetched 120kB in 0s (271kB/s)   
Selecting previously deselected package envyng-core.
(Reading database ... 162807 files and directories currently installed.)
Unpacking envyng-core (from .../envyng-core_2.0.1_all.deb) ...
Processing triggers for man-db ...
Setting up envyng-core (2.0.1) ...

3.) Next enter:
> envyng  -t
A text mode menu should be displayed, something like this:
```
 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

```
Press 3 and press enter, and follow the prompts, as appropriate.  When finished, reboot with option 6.  Report back whether that works.

---

### Post by garrydog on 2008-12-24
Hi
Well well I was begining to lose hope ,but you have cracked it ,at present i am running wired to my router ,can i use my wireless adapter or not .
Also how do i resize my disply ,desktop ,acording to the moniter it is 800 by 600,and the optimum is 1280 by 1024 .
Thank you very much David .

---

### Post by Elfy on 2008-12-24
If you have an nvidia - run ```
gksu nvidia-settings
``` to set resolution, not at all sure with ATI

---

### Post by ByteJuggler on 2008-12-24
> **garrydog said:**
> Hi
Well well I was begining to lose hope ,but you have cracked it ,at present i am running wired to my router ,can i use my wireless adapter or not .
Also how do i resize my disply ,desktop ,acording to the moniter it is 800 by 600,and the optimum is 1280 by 1024 .
Thank you very much David .

Right, now you have some form of GUI display, we need to try and sort out why the resolution isn't coming up properly by default.  (You've been very unlucky so far I must say, but keep at it, we'll get there I'm sure.) 

Firstly, the normal way to deal with changing the resolution would be via the GUI administration applet.  (If using the proprietary driver, there's usually also the manufacturer's applet, as pointed out by the previous poster but lets' just see if the normal admin applet works.) Try the following:  Go into System (top menu) -> Preferences -> Screen resolution.  There you should be able to adjust the resultion.  Now, sometimes not all the valid resolutions are offered depending on whether the system was able to correctly identify from the screen what resolutions it supports, and/or depending on the video driver in use  Please firstly have a look there and tell me whether you can adjust the resolution and/or whether you can see your screen's native resolution.

As for your wireless question:  It depends, Ubuntu is pretty good with wireless these days, but when it doesn't work automatically it can be a pain (a bit like the graphics which works well for the most part but can be a pain if you do run into trouble.)  You really should however post this as a seperate question in a seperate thread, so I'll comment there when you post a new thread for it.  Please include what wireless adapter make and model you have.

---

### Post by garrydog on 2009-01-03
Hi Bytejuggler
May i start by wishing you a very happy new year ,sorry about the delay been away for the new year .I have now put the ubuntu on a sperate hard drive on my computer ,so i am starting from scratch.I have been into the screen res as you advised ,only 800x600 and 640x480 are on the panel ,and the box is marked unknown .

---

### Post by madsmaddad on 2009-01-03
I have been following this conversation because i have a similar problem. My screen works but keeps flashing off and on again. 

so far I have learned about the xrandr  command that displays the scan size capabilities, and from another post, I edited my xorg.conf to add the line as below, which 'fixed' my screen size.

"Section "Monitor"
        Identifire "configured Monitor"
        option        "DisplaySize" "270 203 # 96 DPI @ 1024x768"   <------
EndSection

Don't forget the sudo before you edit (I use kate to edit) or else it will not save the result. 

Good luck.

---

### Post by madsmaddad on 2009-01-03
Regarding an earlier post that gives a link to the magazine article on running dpkg-reconfigure, I just did that and it only set up my keyboard. It didn't take me through any other setup. Is that new in Intrepid?


MMD

---

