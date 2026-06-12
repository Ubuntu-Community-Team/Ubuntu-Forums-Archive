---
title: "DVD cannot be read although libdvdcss2 is installed"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by sdim on 2009-09-11
Hi,everyone.
After installing 9.04,and having already installed all the necessary codecs to play dvd's (I think),I still get the message about libdvdcss2 not being installed.I have installed libdvdread4 through the command line,but the dvd still can't play.
Any ideas?

---

### Post by dearingj on 2009-09-11
1) Which programs have you tried to play this dvd with? Sometimes a different program will give you a more useful error message.
2) Are you sure you have libdvdcss2 installed, and not just libdvdread4?

---

### Post by sdim on 2009-09-11
Thanks for the answer.
I'm talking about Totem Xine.

---

### Post by dearingj on 2009-09-11
Try VLC. It's a capable media player, and as I said earlier, it may give a more useful error message.

```
sudo apt-get install vlc
```

---

### Post by arochester on 2009-09-11
1) The most versatile player is Vlc. Not very pretty in it's raw state, but it can be skinned.

2) To get libdvdcss2 you must install the Medibuntu Repository

---

### Post by dearingj on 2009-09-11
> **arochester said:**
> 
2) To get libdvdcss2 you must install the Medibuntu Repository

If for some reason you don't want to add the whole repository, or if the computer in question does not have Internet access,
you can download individual packages by searching for them at [http://packages.medibuntu.org/](http://packages.medibuntu.org/)
libdvdcss2 can be downloaded from here: [http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)

---

### Post by sdim on 2009-09-11
I have the Medibuntu repo installed,I also installed VLC,I even manually installed libdvdcss2 as suggested,but still,I get errors trying to play a region 2 dvd (my region).Unprotected dvd's play fine.
What's up with dvd playback...?

---

### Post by philinux on 2009-09-11
Run vlc or totem from the terminal. Try and play a dvd and note any error that pop up in the terminal.

---

### Post by mc4man on 2009-09-11
It could be a region isn't set on the drive. 
If you wanted you could produce some libdvdcss debugging. To do so put a dvd in the drive and close out any player that that opens.

Then go into home folder and **delete the .dvdcss folder** (hidden

In terminal
```
export DVDCSS_VERBOSE=2
```

Then if you only have 1 drive or dvd is in the default drive use this
```
vlc dvd:// > css_output 2>&1
```

or just this, then open the disc as usual from media -> open disc
```
vlc  > css_output 2>&1
```

Totem-xine can be substituted for vlc if desired

After the command, close the player and then look in home folder for debug file css_output

(( I'd check your region setting
Install regionset and with a disk in the drive run regionset, look for the line Type: 
It should say "SET"

---

### Post by sdim on 2009-09-11
```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 3
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:
```
I ran regionset,and that's what it says...
P.S. This is a region 2 dvd I'm trying to play.

```
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/sd/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00070079
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00070b10
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0008350e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000e0956
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000e271d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003efccc
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003f2426
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003f243e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003f5c18
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[00000408] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdread: Invalid title IFO (VTS_03_0.IFO).
[00000408] dvdread demux error: fatal error in vts ifo
[00000408] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[00000411] main access error: no access module matched "dvd"
[00000407] main input error: open of `dvd:///cdrom' failed: could not create access: no access module matched "dvd"
```
That's what I get in the terminal when running VLC.

---

### Post by dearingj on 2009-09-11
> **sdim said:**
> ```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 3
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:
```
I ran regionset,and that's what it says...
P.S. This is a region 2 dvd I'm trying to play.


Sounds like you've found your problem. Your drive is set to play region 1 dvds.

---

### Post by sdim on 2009-09-11
These are the codecs installed.Could there be a conflict,somewhere?

---

### Post by philinux on 2009-09-11
Your dvd player may not be multiregional. If it's set to region 1 it will not play region2 period.

Unless someone knows of a way.

---

### Post by mc4man on 2009-09-11
normally what region your drive is set to doesn't matter in linux, players and most drives ignore region settings.

One notable exception is matshita drives which will not allow access to encrypted sectors when there is a region mismatch

To ck. your drive run 
```
sudo lshw -C disk
```

If it is a matshita then set region to what the region of the majority of your titles are and forget playing any other regions.

**Do not keep switching regions**, after 5 resets from the orig. the drive will forever be locked at the 5th reset.

Do delete the .dvdcss folder whether you have a matshita or not

---

### Post by sdim on 2009-09-11
```
One notable exception is matshita drives which will not allow access to encrypted sectors when there is a region mismatch
```
Yes,it is a Matshita drive on a Toshiba Satellite notebook.
That explains it.
Now,as far as region 2 is concerned,I set it to "2" using regionset,but still I get "static",like in the screenshot.
Regarding the drive,now,it played everything I threw at it under Vista (Power DVD was used,but MPC as well).
I really don't understand this...
I also knew that Linux can play all dvd's regardless of region...isn't that right? I've never had to use regionset in the past.:confused:

---

### Post by mc4man on 2009-09-11
As mentioned, did you go into your home folder and delete the .dvdcss folder. ( a hidden folder

That folder contains the keys previously extracted, most players will check there first and if a folder is found matching the volume label of the disc will use those keys whether they are correct or not, complete or incomplete.

By deleting the folder then libdvdcss will be forced to re-acquire the keys, hopefully now the correct and complete set

To give eX.
with existing matching folder in .dvdcss/
> libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdcss debug: opening target `/dev/scd0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key [COLOR="Blue"]<removed>[/COLOR]
libdvdcss debug: trying player key [COLOR="Blue"]<removed>[/COLOR]
libdvdcss debug: decrypted disc key is [COLOR="Blue"]<removed>[/COLOR]
libdvdcss debug: using CSS key cache dir: /home/doug/.dvdcss/HOMICIDE_SERIES_3_VOLUME_1-2003082812073500-3677cb3a7a/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000123
libdvdcss debug: [COLOR="Red"]title key found in cache[/COLOR] [COLOR="Blue"]<removed>[/COLOR]
libdvdread: Elapsed time 0

After deleting .dvdcss

> libdvdcss debug: opening target `/dev/scd0'
libdvdcss debug: using libc for access
libdvdcss debug: disc is scrambled
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: decrypting disc key [COLOR="Blue"]<removed>[/COLOR]
libdvdcss debug: trying player key [COLOR="Blue"]<removed>[/COLOR]
libdvdcss debug: decrypted disc key is [COLOR="Blue"]<removed>[/COLOR]
libdvdcss debug: using CSS key cache dir: /home/doug/.dvdcss/HOMICIDE_SERIES_3_VOLUME_1-2003082812073500-3677cb3a7a/

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000123
libdvdcss debug: [COLOR="Red"]getting title key at block 291 the classic way[/COLOR]

removed actual keys, not inclined to post keys w/ title name

---

### Post by sdim on 2009-09-11
I just did,mc4man,and they all play perfectly.Well,not entirely,since I get a slight tearing effect during playback,but I have an ATI card (drivers enabled,though),so I can't complain much.
Many thanks to all the friends who helped.I appreciate it.

---

### Post by mc4man on 2009-09-11
> Unless someone knows of a way.
With matshita laotop drives there is no way, Panasonic has chosen to exceed the RCE requirements for reasons only known to them, the same might apply to their 'name' choice.
 ( the 1 exception is for some matshita drives shipped on macbooks, for them a rc1 firmware is available.

For most drives and players a region mismatch shouldn't be a problem. What can occur is that not all of the titles on a disc can be extracted properly when there is a region mismatch.

There is usually no issue there with the main movie title, the size to sample will allow 'brute forcing' the keys successfully.

extra's can be an issue and sometimes can't be decrypted.

In any case, if the proper set of keys can be aquired for the disk in question, then placing them in the title's folder in .dvdcss will allow full and proper decryption.

The means for acquiring can range from an extra drive set to proper region to a 'freind' who has the same title and drive set to proper region

edit
 the other thing one could try  on none matshita drives or if libdvdcss is having problems with a disc, is to change from the default method of decrypting (disc/player key) to a title key method.
Can be done on a temp basis by any of these (remove dvd:// if not on default drive
```
export DVDCSS_METHOD=title && vlc dvd://
export DVDCSS_METHOD=title && totem-xine dvd://
```

---

### Post by sdim on 2009-09-12
Many thanks,mc4man.
You've been most enlightening.

---

