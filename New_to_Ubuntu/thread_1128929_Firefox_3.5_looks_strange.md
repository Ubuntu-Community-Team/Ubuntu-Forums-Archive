---
title: "Firefox 3.5 looks strange"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by helino on 2009-04-18
**SOLVED** See last post

Hello,

I installed firefox 3.5 from the repos, and when I launched it I noticed that the fonts and colors doesn't looked like the ones in firefox 3.0.8.

I suspects that this might have something to do with the addon ubufox.

Does anyone know how to solve this problem?

Thanks for your time

---

### Post by juancarlospaco on 2009-04-18
Purge and Reinstall it?

---

### Post by Didius Falco on 2009-04-18
> **helino said:**
> Hello,

I installed firefox 3.5 from the repos, and when I launched it I noticed that the fonts and colors doesn't looked like the ones in firefox 3.0.8.

I suspects that this might have something to do with the addon ubufox.

Does anyone know how to solve this problem?

Thanks for your time

Try going to Tools/Addons, then to the Extensions tab, in Firefox. Scroll down to the Ubuntu Firefox Modifications extension and Disable it. Restart Firefox and see how it looks.

---

### Post by helino on 2009-04-18
Thanks for the answer!

The problem is that in Firefox 3.5 (Shiretoko), the "Ubuntu firefox modifications" addon is listed as "Not compatible". 

I'm guessing that the "Ubuntu firefox modifications" addon is responsible for setting the correct fonts, among other things?

To clarify the problem: 
In Firefox 3.0.8 everything looks great, and the addon "Ubuntu firefox modifications" is listed as compatible.

In Shiretoko (codename for Firefox 3.5b4), the interface fonts in the browser, and the fonts used by websites looks ugly. The addon "Ubuntu firefox modifications" is listed as not compatible. I've tried to disable compability checking, but it didn't help

---

### Post by Didius Falco on 2009-04-18
Were you able to disable it, and did that solve the problem?

---

### Post by helino on 2009-04-18
Yes, I've managed to disable compability checking, and no, that didn't help

---

### Post by Didius Falco on 2009-04-18
> **helino said:**
> Yes, I've managed to disable compability checking, and no, that didn't help

When you say you've managed to disable "compatibility checking", does that mean you are using the Nightly Testers Tool?

If so, all that will do is stop Firefox from complaining that it isn't compatible and force it to use it. To see if that extension (Ubuntu Firefox Modifications) is the one causing the problem, you should just disable it and restart Firefox.

If that fixes it, then I'd just uninstall it (or disable it) and wait until they release a compatible one, which probably won't happen until shortly after the official release of Firefox 3.5.

---

### Post by helino on 2009-04-18
Didius: First of all, thanks for helping me out!

What I *think* the problem is that the "Ubuntu firefox extensions" is **disabled** by compability checking. A solution could've been to enable it by using the Nightly Tester Tool, but unfortunately, that didn't work.

Does anyone else have this problem? Or am I all alone... :)

---

### Post by helino on 2009-04-18
After searching around on the internet, I found this post:

[http://ubuntuforums.org/showpost.php?p=6986051&postcount=7](http://ubuntuforums.org/showpost.php?p=6986051&postcount=7)

mentioning that:
> 
firefox-3.5 takes its font hinting orders from fontconfig, instead of gnome's font settings


The question, how do I change fontconfig to use the same font as my gnome's font settings?

SOLVED: The following solved the font problem for me:

```

cd /etc/fonts/
sudo mv conf.d/10-hinting-slight.conf .
sudo ln -s conf.avail/10-hinting-slight.conf conf.d/
sudo mv conf.d/10-hinting.conf .
sudo ln -s conf.avail/10-hinting.conf conf.d/
sudo dpkg-reconfigure fontconfig

```

---

### Post by mutew on 2009-07-01
> **helino said:**
> 
SOLVED: The following solved the font problem for me:

```

cd /etc/fonts/
sudo mv conf.d/10-hinting-slight.conf .
sudo ln -s conf.avail/10-hinting-slight.conf conf.d/
sudo mv conf.d/10-hinting.conf .
sudo ln -s conf.avail/10-hinting.conf conf.d/
sudo dpkg-reconfigure fontconfig

```

Since the existing hinting files in conf.d are nothing more than soft links to the same filename under ../conf.avail I am assuming that by these commands you are disabling the soft link. I tried the same by renaming the soft link instead of pointing it to elsewhere, as you have done, but the browser still renders the fonts like before.

Here is a screenshot of Firefox 3.0.11 and Firefox 3.5

---

### Post by magnuseh on 2009-07-01
> **mutew said:**
> Since the existing hinting files in conf.d are nothing more than soft links to the same filename under ../conf.avail I am assuming that by these commands you are disabling the soft link. I tried the same by renaming the soft link instead of pointing it to elsewhere, as you have done, but the browser still renders the fonts like before.

Here is a screenshot of Firefox 3.0.11 and Firefox 3.5

I also experienced very different and strange-looking fonts in Firefox after upgrading to 3.5. Changing the default hinting from slight to medium in fontconfig solved the problem for me.

The following steps should to the trick:
```

cd /etc/fonts/conf.d
rm 10-hinting-slight.conf
ln -s ../conf.avail/10-hinting-medium.conf .

```

Then close all open instances of Firefox and restart it.

---

### Post by Vadi on 2009-07-01
Thanks, this helped.

---

### Post by mutew on 2009-07-01
> **magnuseh said:**
> I also experienced very different and strange-looking fonts in Firefox after upgrading to 3.5. Changing the default hinting from slight to medium in fontconfig solved the problem for me.

The following steps should to the trick:
```

cd /etc/fonts/conf.d
rm 10-hinting-slight.conf
ln -s ../conf.avail/10-hinting-medium.conf .

```

Did you make any further changes in /etc/fonts/conf.d or just this one?

---

### Post by ibuclaw on 2009-07-01
May I also note that the URL colours in the address bar are also different in the new firefox-3.5 version. (Blue and brownish black do not go very well with my eyes).

To fix.

Go into your ~/.mozilla/firefox-3.5/*/chrome directory, and create the following file:
```
userChrome.css
```

Then paste in the following:
```

    .ac-comment {
    font-size: 100%! important;
    color: #CCCCCC ! important;
    }

    .ac-comment[selected=”true”] { color: #FFFFFF !important; }

    .ac-url-text {
    font-size: 100% ! important;
    color: #999999 ! important;
    }

    .ac-url-text[selected=”true”] { color: #FFFFFF !important; }

```

This restores it to near enough expected behaviour (for me at least) that I get in Firefox 3.0

Feel free to play about with the colours.

Regards
Iain

---

### Post by EarthMind on 2009-07-01
Nothing works for me, the fonts still look ugly. The userChrome.css fix for the address dropdown list urls didn't work either...

---

### Post by ertayone on 2009-07-01
> **EarthMind said:**
> Nothing works for me, the fonts still look ugly. The userChrome.css fix for the address dropdown list urls didn't work either...

None of the workaround are working for me either.

What Ubuntu are you running? I'm using 64-bit Jaunty.

---

### Post by EarthMind on 2009-07-01
Ubuntu 9.04 Jaunty Jackalope 32bit

---

### Post by EarthMind on 2009-07-01
Ok the userchrome fix works now, I just had to put it in the ~/.mozilla/firefox and not in ~/.mozilla/firefox3.5 (probably because I manually install Firefox from firefox.com)

---

### Post by mohbana on 2009-07-01
> **mutew said:**
> Since the existing hinting files in conf.d are nothing more than soft links to the same filename under ../conf.avail I am assuming that by these commands you are disabling the soft link. I tried the same by renaming the soft link instead of pointing it to elsewhere, as you have done, but the browser still renders the fonts like before.

Here is a screenshot of Firefox 3.0.11 and Firefox 3.5

i actually prefer the FF 3.5 rendering.  anyhow, what desktop fonts are you using?

---

### Post by mutew on 2009-07-02
> **mohbana said:**
> i actually prefer the FF 3.5 rendering.  anyhow, what desktop fonts are you using?

I am using Tahoma(pt 8 ) as my desktop font and Terminus as the fixed width font. I hate anti-aliasing at small font sizes and so my ~/.fonts.conf has a lot of edits to handle improper looking fonts by replacing them with a better looking font. I also have Smoothing set to Subpixel(LCDs) and hinting set to full which gives me the sharp looking desktop font that you see in the attached pictures in my original post.

I setup the following in /etc/fonts/conf.d and ran 'dpkg reconfigure fontconfig' but the fonts in Firefox 3.5 still render the same.
```
10-autohint.conf
10-hinting-full.conf
10-sub-pixel-rgb.conf
```

---

### Post by cdekter on 2009-07-02
I found that my Firefox 3.5 fonts looked weird until I simply got rid of my ~/.fonts.conf file... looking good now.

---

### Post by SaintJules on 2009-07-02
> **helino said:**
> After searching around on the internet, I found this post:

[http://ubuntuforums.org/showpost.php?p=6986051&postcount=7](http://ubuntuforums.org/showpost.php?p=6986051&postcount=7)

mentioning that:


The question, how do I change fontconfig to use the same font as my gnome's font settings?

SOLVED: The following solved the font problem for me:

```

cd /etc/fonts/
sudo mv conf.d/10-hinting-slight.conf .
sudo ln -s conf.avail/10-hinting-slight.conf conf.d/
sudo mv conf.d/10-hinting.conf .
sudo ln -s conf.avail/10-hinting.conf conf.d/
sudo dpkg-reconfigure fontconfig

```

Hi everyone,
the above solved my problem in part, now I can't see shadows of color in the fonts anymore (if you know what I mean), so the black is black, but still can't get any anti aliasing effect and fonts appear too thin and not smooth..
Any suggestions?

---

### Post by Darkshade on 2009-07-02
> **helino said:**
> After searching around on the internet, I found this post:

[http://ubuntuforums.org/showpost.php?p=6986051&postcount=7](http://ubuntuforums.org/showpost.php?p=6986051&postcount=7)

mentioning that:


The question, how do I change fontconfig to use the same font as my gnome's font settings?

SOLVED: The following solved the font problem for me:

```

cd /etc/fonts/
sudo mv conf.d/10-hinting-slight.conf .
sudo ln -s conf.avail/10-hinting-slight.conf conf.d/
sudo mv conf.d/10-hinting.conf .
sudo ln -s conf.avail/10-hinting.conf conf.d/
sudo dpkg-reconfigure fontconfig

```

Thanks a lot, this one did the trick for me. A few more hours with the nasty rendering of 3.5 and I would be blind as a raccoon :D

---

### Post by SaintJules on 2009-07-03
Update: with the 3.5.1 version everything is fixed! Anyone else see this?

---

### Post by asac on 2009-07-03
> **SaintJules said:**
> Update: with the 3.5.1 version everything is fixed! Anyone else see this?

There is no 3.5.1 yet afaik.

Do you see the font problem with upstream builds or also with our karmic(jaunty) packages?

---

### Post by DASPRiD on 2009-07-03
> **asac said:**
> There is no 3.5.1 yet afaik.

Do you see the font problem with upstream builds or also with our karmic(jaunty) packages?

Well, in the mozilla daily PPA there is 3.5.1 minefield. I'm using it as well, but still have the font problem. I really hope that the universe package gets updated soon together with some ubuntu-related fixes for that.

---

### Post by rockorequin on 2009-07-04
To make FF 3.5 (installed from the repositories) use slight hinting instead of medium, I edited ~/.fonts.conf and changed the font hint entry from hintmedium to hintslight and restarted FF.

My .fonts.conf file looks like:

<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

---

### Post by ishmael2k on 2009-07-04
Well nothing has worked for me yet.

I am at the point of going back to .011 just to ease my eyes. 

Note: The problem I am having is specific, about 50% of the fonts are dark blue instead of black. I used ubuntuzilla to get and install 3.5. 

Any suggestions before I retreat?

Running Juanty 32

R

---

### Post by amn108 on 2009-07-04
> **helino said:**
> Didius: First of all, thanks for helping me out!

What I *think* the problem is that the "Ubuntu firefox extensions" is **disabled** by compability checking. A solution could've been to enable it by using the Nightly Tester Tool, but unfortunately, that didn't work.

Does anyone else have this problem? Or am I all alone... :)

You are not alone. I have the exact same problem on Ubuntu Jaunty with downloading official binary archive from mozilla.com and running it. It looks uglier than the rest of my Gnome desktop, because Firefox decided to use its own text renderer apparently, or just re-configure the system renderer. A lot of blue text also in history, for one reason or another.

---

### Post by dotkam on 2009-07-05
This should do the trick:
```
sudo vi ~/.fonts.conf
```
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>
```

---

### Post by ishmael2k on 2009-07-05
> **dotkam said:**
> This should do the trick:
```
sudo vi ~/.fonts.conf
```
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>
```

Success, I tried this one for the second time and it worked! I must have screwed it up the first time. Thanks to all!

---

### Post by Nirro on 2009-07-06
> **cdekter said:**
> I found that my Firefox 3.5 fonts looked weird until I simply got rid of my ~/.fonts.conf file... looking good now.
This was working for me. Thanks.

---

### Post by mgasparotto on 2009-07-07
Hi,

Don't work for me, this workaround break all fonts in my system and don't resolv the problem in firefox...

Any idea?


Thanks.

---

### Post by SnickyH on 2009-07-07
I haven't upgraded yet, those of you who have.... is it worth it?

---

### Post by chris.pappas on 2009-07-08
> **magnuseh said:**
> I also experienced very different and strange-looking fonts in Firefox after upgrading to 3.5. Changing the default hinting from slight to medium in fontconfig solved the problem for me.

The following steps should to the trick:
```

cd /etc/fonts/conf.d
rm 10-hinting-slight.conf
ln -s ../conf.avail/10-hinting-medium.conf .

```

Then close all open instances of Firefox and restart it.
This helped me fix the hinting problem as well. Font 'sizes' are now back to normal.

---

### Post by mikkelbg on 2009-07-12
> **SnickyH said:**
> I haven't upgraded yet, those of you who have.... is it worth it?

Use ubuntuzilla to update Firefox and helino's code to make the fonts look clear. This will make everything easy leaving no reason not to upgrade.

---

### Post by itsjareds on 2009-07-13
I had to modify DotKam's code a bit to get the fonts to look right on my computer:

~/.fonts.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<match target="font">
		<edit mode="assign" name="antialias">
			<bool>true</bool>
		</edit>
		<edit mode="assign" name="hinting">
			<bool>true</bool>
		</edit>
	</match>
</fontconfig>
```

This should look right to people who use "Best Contrast" under System > Preferences > Appearance > Fonts.

---

### Post by Julianz on 2009-07-14
Same problem here. Could not fix it with the suggestions. I migrated back to 3.0 and will wait for a while.

---

### Post by amn108 on 2009-07-14
Funny i just removed all /etc/files/conf.d/10-* and after that "dpkg-reconfigure fontconfig" and Firefox 3.5 started to obey my Gnome text rendering ways. That is all it took.

---

### Post by CamT on 2009-07-14
Removing ~/.fonts.conf corrected the font smoothing for me.

---

### Post by valvwen on 2009-07-14
The .fonts.conf method worked for me, but I had to modify several values. This is for people who selected "Best Shapes" in System> Preferences> Appearance, which has Smoothing "Grayscale" and Hinting "Medium".

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="lcdfilter" >
   <const>lcdnone</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>

```

---

### Post by Dave_Jackson on 2009-07-14
From personal experience, it seems to me that editing font config files is unnecessary to fix this problem. It may work, but there is a cleaner, simpler way to go about it. 

In a previous page of this thread, amn108 wrote: > Funny i just removed all /etc/files/conf.d/10-* and after that "dpkg-reconfigure fontconfig" and Firefox 3.5 started to obey my Gnome text rendering ways. That is all it took.

Although, in my case, the correct path was **/etc/fonts/conf.d** and I just deleted all files in that folder that had a 10 in their name. Should only be a few of them. After rebuilding the fonts cache with dpkg-reconfigure fontconfig, all was well with no ill effects. Firefox 3.5 font rendering now looked identical to my other applications in gnome.

Here's a link back to my thread if any of you should find it helpful:
[http://ubuntuforums.org/showthread.php?p=7616965#post7616965]("http://ubuntuforums.org/showthread.php?p=7616965#post7616965")

Thanks for sharing your solutions, as it helped me come to the right one.

---

### Post by hamidoo on 2009-07-15
> **dotkam said:**
> This should do the trick:
```
sudo vi ~/.fonts.conf
```
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>
```
SOLVED!
WOW! Zillions thx dude!
it worked lika a charm!
i was using 3.0.11 instead for the clear fonts, but now 3.5 fonts are clear again!

---

### Post by R_U_Q_R_U on 2009-07-15
> **Dave_Jackson said:**
> From personal experience, it seems to me that editing font config files is unnecessary to fix this problem. It may work, but there is a cleaner, simpler way to go about it. 

In a previous page of this thread, amn108 wrote: 

Although, in my case, the correct path was **/etc/fonts/conf.d** and I just deleted all files in that folder that had a 10 in their name. Should only be a few of them. After rebuilding the fonts cache with dpkg-reconfigure fontconfig, all was well with no ill effects. Firefox 3.5 font rendering now looked identical to my other applications in gnome.

Here's a link back to my thread if any of you should find it helpful:
[http://ubuntuforums.org/showthread.php?p=7616965#post7616965](http://ubuntuforums.org/showthread.php?p=7616965#post7616965)

Thanks for sharing your solutions, as it helped me come to the right one.

Thanks - worked fine and EASY!

---

### Post by itsjareds on 2009-07-15
Dave's fix worked for me, I had originally done a .fonts.conf workaround.

Here are the commands I ran (for anyone who needs help):
```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig
```

Then restart Firefox and you should be set.

---

### Post by majikshoe on 2009-07-17
> **itsjareds said:**
> Dave's fix worked for me, I had originally done a .fonts.conf workaround.

Here are the commands I ran (for anyone who needs help):
```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fonts-config
```

Then restart Firefox and you should be set.

Worked for me too, except the dpkg part didn't quite work for me - "fonts-config" was not on my system.  Here is what did work, if anyone else's setup is like mine:

```

sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig

```

Pity we need to mess around like this just to get fonts looking right though. Shouldn't things like this just work without having to resort to config file fiddling or font system reconfiguration?

---

### Post by itsjareds on 2009-07-18
I think the problem originated from the Ubufox addon not being compatible with 3.5.

Either way, I think I just put a typo, it should be fontconfig. Edited my previous post.

---

### Post by merlin666 on 2009-07-20
I have installed Firefox 3.5 and have no problems with fonts using this install code:

apt-get install firefox-3.5 firefox-3.5-gnome-support latex-xft-fonts

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by sshock on 2009-08-17
Dave's fix worked for me.

As for the userChrome.css mentioned by tinivole to fix the coolbar colors, I modified it slightly to
1. Use black text for comment, which I believe is closer to what firefox 3.0 had.
2. Use normal ASCII quotes so selected text will go white like it's supposed to (tinivole's post had Unicode right quotes, code point 0x201D).

```

.ac-comment {
font-size: 100%! important;
color: #000000 ! important;
}

.ac-comment[selected="true"] { color: #FFFFFF !important; }

.ac-url-text {
font-size: 100% ! important;
color: #999999 ! important;
}

.ac-url-text[selected="true"] { color: #FFFFFF !important; }

```

---

### Post by sshock on 2009-08-18
Something is still not right.  I'm using "best contrast" in my system font preferences, but bold fonts in FF are too dark and have jaggies like they're not being anti-aliased correctly.

Compare the screenshots.  The first is from Firefox 3.0 and looks good.  The second is FF 3.5.  Look at the "Re: (Score:3, Funny)".

I tried everything I could think of in my font preferences, but I still can't get it to look good like Firefox 3.0.

---

### Post by sshock on 2009-08-18
After some careful research, I realized that the difference between good.png and bad.png (first two screenshots) is actually that Firefox 3.5 supports text-shadow and 3.0 doesn't, and this website puts a 0-length black shadow on those words.

Having a text shadow is cool and all I suppose, but unfortunately it makes the text jaggedy on my computer, whereas using a darker color wouldn't have.  I don't know why they didn't just darken the color.

So now I am left wondering if this is still a font issue, or if this is a bug in FF specifically related to its implementation of text shadow, or if it is working as designed.  But I know on Windows the text shadow doesn't cause jaggies.

---

### Post by mgmiller on 2009-08-18
I first tried the:
```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig
```


but that didn't work for me.

I finally did the .fonts.conf workaround and that made it render exactly like 3.0.13.
Firefox 3.5 is now as clear as 3.0.x

Is there any reason either of these methods could create problems for me now, or later, when I upgrade to Karmic?

---

### Post by theLegend on 2009-08-22
I found a simpler solution than these, with the answer in the about:config of Firefox.

Type about:config in the address bar and after accepting that you'll make a mess of your firefox unless you know what you are doing, type in layout.css.dpi and put in a value other than -1. I put in 96 to match my dpi of my fonts.

Hope that is useful to you,

The Legend

---

### Post by mgmiller on 2009-08-22
> I found a simpler solution than these, with the answer in the about:config of Firefox.

I tried that.  I set my .fonts.conf back to the original one, and did the 96 dpi entry as you suggest, which also matches my fonts.  The result was back to the ugly skinny fonts I had before.

I reset the default to -1 and renabled the .fonts.conf work around and back to good fonts again.

---

### Post by mustang on 2009-08-23
> **dotkam said:**
> This should do the trick:
```
sudo vi ~/.fonts.conf
```
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>
```

Thank you!

---

### Post by ssri on 2009-08-29
> **mgmiller said:**
> I first tried the:
```
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig
```


but that didn't work for me.

I finally did the .fonts.conf workaround and that made it render exactly like 3.0.13.
Firefox 3.5 is now as clear as 3.0.x

Is there any reason either of these methods could create problems for me now, or later, when I upgrade to Karmic?

I can verify that this method worked for me, although I just moved the symbolic links to a new directory in /etc/fonts rather than outright deleting them.

Kubuntu Jaunty
KDE 4.3.00
QT 4.5.2

EDIT: Unfortunately, this method makes systemwide changes to the font rendering, making fonts in KDE menus harder on the eyes... :(

EDIT2: Tried almost all of the methods listed in this thread that mostly lead to global changes for font rendering in my kubuntu install.  Also tried to change the dpi in about:config per the suggestion of one blogger.  Too bad there is not a firefox specific fix.  I'll be reverting to Firefox 3.0.13.

---

### Post by rsilva4 on 2009-10-13
For those still struggling with this, my solution was using the file in this post [http://ubuntuforums.org/showthread.php?t=101352]("http://ubuntuforums.org/showthread.php?t=101352") thanks aok!:)

---

### Post by sleepingdragon on 2009-10-13
> **magnuseh said:**
> I also experienced very different and strange-looking fonts in Firefox after upgrading to 3.5. Changing the default hinting from slight to medium in fontconfig solved the problem for me.

The following steps should to the trick:
```

cd /etc/fonts/conf.d
rm 10-hinting-slight.conf
ln -s ../conf.avail/10-hinting-medium.conf .

```Then close all open instances of Firefox and restart it.

Thanks! That one worked for me. Me eyes were starting to bleed with the rough fonts.

---

### Post by brendanpiater on 2009-10-13
> **magnuseh said:**
> I also experienced very different and strange-looking fonts in Firefox after upgrading to 3.5. Changing the default hinting from slight to medium in fontconfig solved the problem for me.

The following steps should to the trick:
```

cd /etc/fonts/conf.d
rm 10-hinting-slight.conf
ln -s ../conf.avail/10-hinting-medium.conf .

```

Then close all open instances of Firefox and restart it.

I ran the above commands as sudo and worked 100% for me. 

Thanks.

---

### Post by trigoman05 on 2009-10-30
> **dotkam said:**
> This should do the trick:
```
sudo vi ~/.fonts.conf
```
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>false</bool>
  </edit>
 </match>
</fontconfig>
```

I can confirm that this did fix my fonts I did, however, remove the match that disables antialias.

Thank you.

---

### Post by mgmiller on 2009-10-31
I had a lot of problems with this until I looked at clean installs of both 8.04 and 9.10.  Neither of them had the file ~/.fonts.conf.  So I renamed mine .fonts.conf.backup and restarted Firefox.  Problem fixed.  

I don't know where that file came from, but it isn't needed any more.  

Take a look at my sig and you will see I probably have a lot of legacy cruft in my system.

---

### Post by cully on 2009-11-27
Not sure which it was, but one of these solutions worked for me:

Removed /etc/fonts/conf.d/10*

Removed ~/.fonts.conf


Cully

---

### Post by itsjareds on 2010-02-28
This problem seems to still be present in Lucid alpha3, but neither the .fonts.conf nor 'rm /etc/conf.d/10*' fixes seem to work. Has any method worked for any of the users here using a Lucid alpha?

---

### Post by dcstar on 2010-03-24
> **itsjareds said:**
> This problem seems to still be present in Lucid alpha3, but neither the .fonts.conf nor 'rm /etc/conf.d/10*' fixes seem to work. Has any method worked for any of the users here using a Lucid alpha?

In **about:config**, is this set to true?:

```
gfx.use_text_smoothing_setting
```

---

### Post by asaturn on 2010-04-09
> **dcstar said:**
> In **about:config**, is this set to true?:

```
gfx.use_text_smoothing_setting
```

[http://kb.mozillazine.org/Gfx.use_text_smoothing_setting](http://kb.mozillazine.org/Gfx.use_text_smoothing_setting)

> 
This preference only has an effect in OS X. 


---

### Post by arnab_das on 2010-04-09
if u have installed wine u might want to remove ttf-tahoma-replacement package from the synaptic.

---

