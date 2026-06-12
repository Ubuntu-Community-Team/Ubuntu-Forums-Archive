---
title: "Adobe Flash Problems"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by PathVx on 2010-06-30
Hi All :D,

Recently, I have experienced Adobe Flash Player problems. I cannot seem to find a solution, but it appears to have only started after one of the updates.
My symptoms are:

[LIST]
[*]Full screen flash crashes
[*]Some flash content is covered with a grayish box
[*]Only affects Firefox and Midori. Chromium seems to work fine..
[*]I can only hear audio o_O
[*]Can't see the settings menu.. when I right clicked and press settings
[*]Trying to purge/remove the flash plugin via Synaptic package manager and reinstalling the flash plugin does not solve this issue
[*]Flash aid (the firefox addon) is also ineffective
[*]Tried to use an older version of flash... did not solve the problem
[*]Installing ubuntu-restricted-extras... did not solve the problem
[/LIST]
Oh, and I use the proprietary Nvidia drivers.
Flash version 10.1 r53.
Thanks for your help!

---

### Post by Deadite81 on 2010-06-30
What you have described is exactly what I am experiencing after updating to FF 3.6.6.  I have do everything PathVx mentioned, no effect.  At first I had nothing at all, just a gray box instead of a video.  No sound either.  Then I uninstalled IcedTea (open source Java) and installed Sun Java.  Now I am where PathVx is - a gray box on YouTube with sound. 

However, I can now view videos on Metacafe.  I still cannot view digital comics on Marvel.com, which is really making me mad as I've been trying to fix this all day.  I've searched and searched to no avail.

Trying to force the FF 3.6.6 package back to 3.6.3 breaks Synaptic.  It tells me I have broken packages.  I understand that I can uninstall 3.6.6 and reinstall 3.6.3 and hold the version there, but I really feel like I shouldn't have to do that.

Flash works in Liferea, Chromium and Opera.  It also does not work in Thunderbird.  Just Mozilla stuff is broken.

Flash Aid does not help.  Nothing helps.  What's the deal?  Anyone?

---

### Post by Deadite81 on 2010-06-30
I have also tried Firefox in safe mode with all extensions disabled.  No love.  32bit Ubuntu 10.04, btw.

---

### Post by PathVx on 2010-07-01
Oh got it! Apparently, you have to disable RGBA because RGBA is not compatible with XUL applications. 
I used 
```
sudo gedit /etc/profile.d/gtkrgba.sh
```and added to the list midori
Now, Midori loads flash!
Yay. But, I still haven't figured out why firefox doesn't work even when it's on the list.


Hmm. I can't get the process name right .. so I just commented all of the lines in that file with a # in each line.
This effectively disables RGBA for all applications, but meh, it works.

---

### Post by hugo.tyson on 2010-07-01
I have exactly the same after yesterday's auto update of firefox.  Even after the fight with FF2 was fixed.  Every single flash object goes to "the flash plugin has crashed".  Detecting this nicely is of course great, but not as nice as having it work! ;-)
This is with whatever the default flash is, 9.0r32 it sez 'ere.

I looked for this but that dir is empty on my machine.
/etc/profile.d/gtkrgba.sh

---

### Post by Deadite81 on 2010-07-01
Ok, I have solved my problem, it was in fact the RGBA transparency.

If you are experiencing these problems and have rgba, unfortunately the only fix I found is...annoying.

 Firstly, this command to start Firefox worked for me 2 out of 3 times with my rgba enabled as I had it:
```

XLIB_SKIP_ARGB_VISUALS=1 firefox
```
If this works for you great, if not continue reading...

If you completely remove the package "gtk2-module-rgba" flash will begin working immediately for all sites as normal (restart FF if it is running at the time of removal).

If you want to keep rgba, just excluding FF and exe from using transparency is apparently not enough.

Don't even bother mucking up the file in /etc.  Open the file ~/.profile in your favorite text editor.

If you already had something like this in .profile:

```


export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:\
Audacity:\
autokey-gtk:\
Banshee:\
bitmeter:\
celtx-bin:\


```

and it's a bunch more, just comment it out rather than erasing it all (I'm sure a fix will come along soon) by putting a # in front of every line.

Unfortunately the "allbut" filter would not work for me.  I had to do this:

```

export GTK_MODULES=rgba
export GTK_RGBA_APPS=mygtkmenu:nautilus:rhythmbox:avant-window-navigator

```
Instead of excluding (allbut) I have to Include, that is, specify Exactly which programs I want to use rgba one by one.

If you're using rgba this should fix the problem.  I have not been to the developer's launchpad page yet, but there were some complaints about it on his Gnome-Look page here.
I will file a bug if one hasn't already been posted.
 
Hope this helps!

---

### Post by Deadite81 on 2010-07-01
@hugo.tyson:
RGBA transparency is not installed by default.  You will not have that file if you did not install the rgba testing ppa.  You would know if you did!  I recommend trying the Flash Aid add-on fo FF.  You can get it [here]("https://addons.mozilla.org/en-US/firefox/addon/161939/").

---

### Post by lkjoel on 2010-07-01
Did you try Flash-Aid?
It is an extension for Firefox. 
The title describes it.
It fixes Flash.

---

### Post by b00kw0rm on 2010-07-01
I was also getting the gray box instead of video after upgrading Firefox to v3.6.6.  The fix that worked for me was a combination of the suggestions posted by QIII and Dennis N in the thread [http://ubuntuforums.org/showthread.php?t=1521973&highlight=firefox](http://ubuntuforums.org/showthread.php?t=1521973&highlight=firefox)

I checked my plugins and found I was still using the old 9.0 r227 version of Shockwave Flash plugin.  I used synaptic to uninstall that and then install the new Shockwave Flash 10.1 r53.  Now I can play video through Firefox 3.6.6

FYI - I'm running 8.04 LTS

---

### Post by wonderingwhy on 2010-07-02
Thanks chaps for the info.  After the latest updates 'full screen flash' and ordinary flash on occasions was completely crashing. I'm using ubuntu 8.04 and firefox 3.6.6

I'm a nubie and a complete egit at this kind of stuff but Flash-Aid did the job.



So thanks flash-aid guy - your my hero :D

---

### Post by lovinglinux on 2010-07-02
> **wonderingwhy said:**
> So thanks flash-aid guy - your my hero :D

:) You are welcome.

---

### Post by wonderingwhy on 2010-07-03
Hi Lovinglinux

Did I mention that I'm an egit, so last night I got it all working according to your beautiful plugin and then this morning I got a bit ahead of myself.  I'm not sure how but I had a previous version of flash installed, and my husband couldn't see streetview on google maps - so I tried to upgrade to flash 10.1 and then it all went pear shaped.  So I did something - I honestly have no idea what but now I'm going round in circles, down loading flash-aid deletes flash 10.1, so I upload flash 10.1 and then need to install flash-aid again.

Can you help or is it terminal?

---

### Post by Yarui on 2010-07-03
I wouldn't be surprised if we start seeing a lot of people having issues with flash.  There was a (apparently very major) security flaw found recently.  The newest version of flash has fixed this security flaw but it must have been a pretty major overhaul of the code because adobe decided to stop making a 64 bit version of the flash player, which probably means they did something huge if they couldn't just make the same changes to both versions.  As a result we are probably going to see a lot of people having issues with flash in 64 bit OSs and if they made really major changes to the 32 bit version, there may be a lot of issues with that one too.

---

### Post by wonderingwhy on 2010-07-03
> Did I mention that I'm an egit, so last night I got it all working according to the beautiful flash-aid plugin and then this morning I got a bit ahead of myself. I'm not sure how but I had a previous version of flash installed, and my husband couldn't see streetview on google maps - so I tried to upgrade to flash 10.1 and then it all went pear shaped. So I did something - I honestly have no idea what but now I'm going round in circles, down loading flash-aid deletes flash 10.1, so I upload flash 10.1 and then need to install flash-aid again.

Can you help or is it terminal? 

So I've half fixed the problem.  I uninstalled all flash completely using synaptic, then installed an older version of flash and bingo Flash-Aid works yay for Flash-Aid.

But still no streetview on google maps and either related or not backgammon on facebook isn't working either so two of my husband's fav things kapute - anytakers...

Thanks again flash-aid guy:D

---

### Post by Yarui on 2010-07-03
> **wonderingwhy said:**
> But still no streetview on google maps and either related or not backgammon on facebook isn't working either so two of my husband's fav things kapute - anytakers...
Sorry for being off topic, but I didn't know there were actually people in this world who knew how to play backgammon.:p

---

### Post by v1ad on 2010-07-03
flash-aid ftw. it does install 10.01

link for flash-aid [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

adobes website. You have version 10,1,53,64 installed

---

### Post by lkjoel on 2010-07-03
> **wonderingwhy said:**
> So I've half fixed the problem.  I uninstalled all flash completely using synaptic, then installed an older version of flash and bingo Flash-Aid works yay for Flash-Aid.

But still no streetview on google maps and either related or not backgammon on facebook isn't working either so two of my husband's fav things kapute - anytakers...

Thanks again flash-aid guy:D
Sometimes the newest version of flash does not support all things.

Download the archives of flash 10.
I used 10.0.22, and everything worked.
Once there will be an update to flash 10.1, install it.

---

### Post by Yarui on 2010-07-03
> **lkjoel said:**
> Sometimes the newest version of flash does not support all things.

Download the archives of flash 10.
I used 10.0.22, and everything worked.
Once there will be an update to flash 10.1, install it.
Right now it's probably not a good idea to use an old version of flash.  Like I said in a previous post, all versions before 10.1.53.64 have a major vulnerability that is now well known.  Installing any earlier version could be risky.

---

### Post by lkjoel on 2010-07-03
10.0.22 is not earlier, unless Adobe is mixed up.

---

### Post by wonderingwhy on 2010-07-03
> **v1ad said:**
> flash-aid ftw. it does install 10.01

link for flash-aid [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

adobes website. You have version 10,1,53,64 installed

Hi v1ad

this is the link I used to download flash-aid.  When I download flash 10.1 it saves it as adobe-flashplugin, when I install flash aid it has the command [HTML]sudo apt-get purge adobe-flashplugin[/HTML], so it uninstalls it.  I've tried renaming the file but - I'm useless at coding and my code is probably wrong and nothing changes.

Thanks for the suggestion though

(p.s. yep Yarui there are backgammon players out there 8-) )

---

### Post by wonderingwhy on 2010-07-04
So I fixed my problems, and those I haven't at least now I know what the problem is.

I was using Ubuntu 8.04 and so I did a total upgrade to Ubuntu 10.04 after totally removing flash, and then did a brand new down load of flash via synaptic after the upgrade and then ran flash-aid and bingo - it's all working, no full screen crash of videos and google maps is aworking. 

(The backgammon on facebook issue is a java thing - in case anyone else is wondering.)

So thanks guys for all your help - it is mucho appreciated.:D

---

### Post by lovinglinux on 2010-07-04
> **wonderingwhy said:**
> Hi v1ad

this is the link I used to download flash-aid.  When I download flash 10.1 it saves it as adobe-flashplugin, when I install flash aid it has the command [HTML]sudo apt-get purge adobe-flashplugin[/HTML], so it uninstalls it.  I've tried renaming the file but - I'm useless at coding and my code is probably wrong and nothing changes.

Thanks for the suggestion though

(p.s. yep Yarui there are backgammon players out there 8-) )

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

What version of Ubuntu you are using?

FLASH-AID will try to remove all flash plugins, then will install the version from the repositories. If you need a different version, disable FLASH-AID or don't run it when asked to do so.

I need to improve the next version of the extension, because not all Ubuntu versions have the latest flash. Nevertheless, FLASH-AID says it will install flash 10.1.53. That is true for Lucid, but not for Hardy for example.

---

### Post by lkjoel on 2010-07-05
LovingLinux, wouldn't it work with a shell script instead of a Firefox extension?

---

### Post by lovinglinux on 2010-07-05
> **lkjoel said:**
> LovingLinux, wouldn't it work with a shell script instead of a Firefox extension?

The extension is in fact a shell script launcher. The advantage is that it can be easily installed and updated, through Firefox add-ons manager. For instance, when Adobe stopped providing support for the 64bit and when the security vulnerability was discovered, I immediately released a new version of my extension. FLASH-AID users were prompted to run the new script, which removed the 64bit installed manually and installed the new 32bit version from the repositories. The same will happen when abode releases a new 64bit version.

So the extension is convenient, but you can do the same thing it does from command-line.

---

### Post by lkjoel on 2010-07-05
Maybe an updater?
```
#!/bin/bash
wget http://www.something.com/latest.sh
```

---

### Post by lovinglinux on 2010-07-05
> **lkjoel said:**
> Maybe an updater?
```
#!/bin/bash
wget http://www.something.com/latest.sh
```

Too complicated to distribute. A Firefox add-on is so much easier for me and for the user. You can install it automatically and Firefox will keep it updated.

---

### Post by lkjoel on 2010-07-05
> **lovinglinux said:**
> Too complicated to distribute. A Firefox add-on is so much easier for me and for the user. You can install it automatically and Firefox will keep it updated.
Ok, my hopes with making a shell script is so that people with other browsers could enjoy it as well.

---

### Post by lovinglinux on 2010-07-05
> **lkjoel said:**
> Ok, my hopes with making a shell script is so that people with other browsers could enjoy it as well.

You can get it [here](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

---

### Post by lkjoel on 2010-07-05
Ok, lovinglinux, If it is okay with you, I will create a way to download the newest version of FLASH-AID, and use it without a browser.

---

### Post by lovinglinux on 2010-07-05
> **lkjoel said:**
> Ok, lovinglinux, If it is okay with you, I will create a way to download the newest version of FLASH-AID, and use it without a browser.

No problem, but there is already [Adobe Tools](http://ubuntuforums.org/showthread.php?t=1414595), that does more than that.

---

### Post by lkjoel on 2010-07-05
What I am saying is that they only need to download my app, then they download FLASH-AID, and put it on my app, which will extract it, then run it.
So then, when you make an update, my app will still work. (Unless you change the filenames)

---

### Post by lovinglinux on 2010-07-05
> **lkjoel said:**
> What I am saying is that they only need to download my app, then they download FLASH-AID, and put it on my app, which will extract it, then run it.
So then, when you make an update, my app will still work. (Unless you change the filenames)

It doesn't work like that. It doesn't have a pre-made script that you can extract an run. The extension creates the script on-the-fly, based on browser architecture, user choices and current availability of flash. This script is saved temporarily in the extension directory before execution and is deleted after running it.

---

### Post by lkjoel on 2010-07-06
> **lovinglinux said:**
> It doesn't work like that. It doesn't have a pre-made script that you can extract an run. The extension creates the script on-the-fly, based on browser architecture, user choices and current availability of flash. This script is saved temporarily in the extension directory before execution and is deleted after running it.
So then I will create the script, and it will detect everything.
I know that Firefox extensions are nice, but not everyone has Firefox.

---

### Post by garyedwardjohnston on 2010-09-02
> **lkjoel said:**
> Did you try Flash-Aid?
It is an extension for Firefox. 
The title describes it.
It fixes Flash.

didnt work

---

### Post by lovinglinux on 2010-09-02
> **garyedwardjohnston said:**
> didnt work

What version of FLASH-AID did you use? What doesn't work?

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Tsu jan on 2010-10-11
With the latest versions of Flash (from the Adobe site) and Firefox, the best workaround is at [http://www.madurax86.com/hrgbaflas/](http://www.madurax86.com/hrgbaflas/) (also see [http://ubuntuforums.org/showthread.php?p=9953736#post9953736](http://ubuntuforums.org/showthread.php?p=9953736#post9953736)). Just add <unknown> to the exception list in '~/.profile' BUT BE SURE TO PUT THE EXCEPTION LIST IN QUOTES, OTHERWISE THE GNOME SESSION WOULD NOT START! For example, use something like this (quoted from the above site):

export GTK_RGBA_APPS="allbut:firefox-bin:gnome-mplayer:totem:soffice:<unknown>:exe"

Here, <unknown> and exe are both for Flash, the first one being for FF.

Adding <unknown> to .profile has other advantages too (for Qt and Java applications).

---

### Post by dennis1200 on 2011-02-23
I did quite a bit of fiddling with transparency and I've got a setup that I like a lot (though I inadvertently made everything invisible a couple of times while figuring it out!)

RGBA PPA is installed and fully operational. I included firefox in the /.profile exceptions list for RGBA, but that didn't fix flash, so I changed my default browser (in Preferred Applications) and the link on my AWN panel to: ```
env XLIB_SKIP_ARGB_VISUALS=1 firefox %s
```
I'd read a comment on some forum somewhere that someone wanted to know how to make that global - that's how (so when you click a link in Thunderbird/Evolution, for example, that instance of firefox will fun Flash videos properly).

I've also added this line in Compiz Opacity/Sat/Brightness:
```
(dropdownmenu | popupmenu | notification | utility) & title=Firefox
```
with a value of 80. 'utility' affects the address bar if you open it to view recent history or do a search, etc. I have Blur Windows enabled with Gaussian blur at a radius of 5, and that works underneath the transparent firefox menus also.

Running Firefox 4 Beta is nice, too, since they've added some nice gradient opacity on the tabs and around the address bar. All in all, the transparency looks awesome and you hardly notice that Firefox doesn't have true RGBA transparency with the menus. I hope this helps!

This is on 10.10 (I sadly lost 802.11n support on the upgrade with my Intel 4965, but I really like the improvements that were made, and I'm looking forward to 11.04!)

---

### Post by The Nutcrackin' Squirrel on 2011-02-23
Since yesterday I can't watch Flash videos anymore. the videoscreen simply stays black. Any suggestions?

E: I can watch other Flash videos and some embedded YT videos. Only the videos on the YT page have a black screen.

---

