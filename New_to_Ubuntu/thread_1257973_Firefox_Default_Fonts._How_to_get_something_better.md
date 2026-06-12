---
title: "Firefox Default Fonts. How to get something better?"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by mejohnsn on 2009-09-04
For some odd reason, the default fonts Firefox uses in Ubuntu look much worse than the default fonts in Firefox used in Windows. (Note that I am not saying the Windows defaults are so good either...).

In particular, characters do not appear crisp, their outlines look fuzzy and blurry.

So the question is: how do I fix this? Are there better fonts already available in the Ubuntu 8.10 distribution? Or do I have to find them somewhere else? If the latter, where? Which repositories, which fonts in them?

---

### Post by blackened on 2009-09-04
> **mejohnsn said:**
> So the question is: how do I fix this? Are there better fonts already available in the Ubuntu 8.10 distribution? Or do I have to find them somewhere else? If the latter, where? Which repositories, which fonts in them?

*Better* is a very subjective word. I personally prefer the default FF fonts in Ubuntu to those in Windows.

To install most of the basic fonts that come with XP use

```
sudo apt-get install msttcorefonts
```

You can then change the font behavior from within Firefox's preferences.

---

### Post by Ric_NYC on 2009-09-04
[B]Ubuntu restricted extras
[/B]

This package depends on some commonly used packages in the Ubuntu multiverse repository. 
Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback. Please note that this does not install libdvdcss2, and will not let you play encrypted DVDs. For more information, see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs). Please also note that packages from multiverse are restricted by copyright or legal issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for more information."


[B]sudo apt-get install ubuntu-restricted-extras
[/B]

**Half of the questions in this forum are solved** with that single command line or installation from the "Add-Remove Applications" in the "Applications" menu.

---

### Post by blackened on 2009-09-04
> **Ric_NYC said:**
> ...This package depends on some commonly used packages in the Ubuntu multiverse repository. 
Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback. Please note that this does not install libdvdcss2, and will not let you play encrypted DVDs. For more information, see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs). Please also note that packages from multiverse are restricted by copyright or legal issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for more information."
...

Which is why I didn't mention that package: the OP was about fonts so all of the other stuff that comes with restricted extras is not really relevant to the problem and is therefore unnecessary. It's like using a tank to kill a cockroach.

---

### Post by mejohnsn on 2009-09-04
> **blackened said:**
> Which is why I didn't mention that package: the OP was about fonts so all of the other stuff that comes with restricted extras is not really relevant to the problem and is therefore unnecessary. It's like using a tank to kill a cockroach.

You made the right decision. In addition, I did not want to have to concern myself about the intellectual property rights issues opened up by resorting to the multiverse.

---

### Post by blackened on 2009-09-04
> **mejohnsn said:**
> You made the right decision. In addition, I did not want to have to concern myself about the intellectual property rights issues opened up by resorting to the multiverse.

In that case, you could use the default fonts (or search synaptic for more) that come with Ubuntu to change your Firefox preferences. That's about the best I've got though.

---

### Post by philinux on 2009-09-04
> **mejohnsn said:**
> For some odd reason, the default fonts Firefox uses in Ubuntu look much worse than the default fonts in Firefox used in Windows. (Note that I am not saying the Windows defaults are so good either...).

In particular, characters do not appear crisp, their outlines look fuzzy and blurry.

So the question is: how do I fix this? Are there better fonts already available in the Ubuntu 8.10 distribution? Or do I have to find them somewhere else? If the latter, where? Which repositories, which fonts in them?

You might find a fiddle here might help.
System>prefs>appearance>Subpixel smoothing>details. Try different setting of hinting to suite your taste. I prefer slight.

---

### Post by mejohnsn on 2009-09-04
> **philinux said:**
> You might find a fiddle here might help.
System>prefs>appearance>Subpixel smoothing>details. Try different setting of hinting to suite your taste. I prefer slight.

Since I am on a laptop, I chose the option for LCD. Outside of FFox at least, this has made a vast improvement.

But when I go back into FFox, I find the same problem: characters appear fuzzy, and the 'x' looks particularly bad. So I went back into FFox Preferences and realized I still had "allow pages to choose their own fonts" selected all this time:(

Now I have unchecked that, and can at least see my own choice of fonts in FFox pages, but I STILL see ugly character appearances, such as the 't' in "Default Fonts" in the title of this thread appearing with the bottom curve of the 't' way too thick.

Also, I followed the earlier suggestion of getting the msttcorefonts only to find that I am still missing Lucida, Lucida Sans and Lucida Sans Unicode. I am also missing Tahoma.

I have had all of these for so long on my Win95 partition I have always assumed they are standard with Win95. Yet they were not included in msttcorefonts. Why is that?

---

### Post by blackened on 2009-09-05
> **mejohnsn said:**
> ... find that I am still missing Lucida, Lucida Sans and Lucida Sans Unicode. I am also missing Tahoma.

I know that Tahoma is missing due to some EULA issues with the software it's being taken from. It's been an ongoing bug for quite some time.
[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529")

I don't know why the Lucida fonts aren't included. Couldn't find any additional info.

> I have had all of these for so long on my Win95 partition I have always assumed they are standard with Win95. Yet they were not included in msttcorefonts. Why is that?

It might be possible to use the missing fonts from your Windows 95 install, but I'm not sure that it jives with 95's EULA.

---

### Post by flux_user on 2009-09-29
Sorry to respond to this "solved" thread.  But here are my two cents worth of information.

First thing is first.  Getting jacked around by the site admin at the mozilla ezine forums kind of stinks.

[http://forums.mozillazine.org/viewtopic.php?f=38&t=1509165&p=7624615#p7624615](http://forums.mozillazine.org/viewtopic.php?f=38&t=1509165&p=7624615#p7624615)

There is an issue with the default font in Firefox's User interface.  Knowing the font; one can adjust the fonts via .fonts.conf.  I think the default font in Firefox UI is lucida; I am not sure.  However, I opted to force a change via **userChrome.css**.

If the file doesn't exist; create it.  Making this change will make the UI better (IMHO).

Putting this in the userChrome.css :

```
* {
font-family: "Deja Vu Sans" !important;
font-size: 10pt !important;
}
```

It will change the font to Deja Vu Sans and make the point size in the font a 10 in EVERYTHING.  There is something with Anti aliasing fonts a certain sizes that make the UI font fuzzy in Firefox.  Making the above change makes the whole UI better looking; as well as the changes below.

Also, I have certain over  rides in my **.fonts.conf** file.  Below is a  my configuration for fonts.
```

<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
    <match target="font" >
        <edit mode="assign" name="autohint" >
            <bool>true</bool>
        </edit>
    </match>
    <match target="font" >
        <edit mode="assign" name="rgba" >
            <const>rgb</const>
        </edit>
    </match>
    <match target="font" >
        <edit mode="assign" name="hinting" >
            <bool>false</bool>
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

    <!--- comments from here to:  
    <match target="font" >
        <edit mode="assign" name="dpi" >
            <double>75</double>
        </edit>
    </match>  -->

    <!-- reduce ringing ==> requires freetype2 'WITH_LCD_FILTERING=yes' changed lcdlight to lcddefault check lcdlegacy-->
    <match target="font" >
        <edit mode="assign" name="lcdfilter" >
            <const>lcddefault</const>
        </edit>
    </match>

   <!-- THIS IS NEW From [http://bugs.gentoo.org/show_bug.cgi?id=233729](http://bugs.gentoo.org/show_bug.cgi?id=233729) -->
   <match target="font">
     <test compare="eq" name="family">
       <string>Andale Mono</string>
     </test>
     <edit mode="assign" name="hintstyle">
       <const>hintfull</const>
     </edit>
     <test compare="less" name="weight">
       <const>medium</const>
     </test>
     <test compare="less_eq" name="pixelsize">
       <double>7</double>
     </test>
     <edit mode="assign" name="antialias">
       <bool>false</bool>
     </edit>
   </match>


   <!-- THIS IS NEW From [http://bugs.gentoo.org/show_bug.cgi?id=233729](http://bugs.gentoo.org/show_bug.cgi?id=233729) -->

    <!-- disable autohinting for bold fonts  
    <match target="font" >
        <test compare="more" name="weight" >
            <const>medium</const>
        </test>
        <edit mode="assign" name="autohint" >
            <bool>false</bool>
        </edit>
    </match> -->

    <!-- preferred aliases -->
    <alias>
        <family>serif</family>
        <prefer>
            <family>DejaVu Serif</family>
            <family>Bitstream Vera Serif</family>
        </prefer>
    </alias>
    <!-- preferred aliases -->
    <alias>
        <family>sans-serif</family>
        <prefer>
            <family>DejaVu Sans</family>
            <family>Bitstream Vera Sans</family>
            <family>Verdana</family>
            <family>Arial</family>
        </prefer>
    </alias>
    <!-- preferred aliases -->
    <alias>
        <family>monospace</family>
        <prefer>
            <family>DejaVu Sans Mono</family>
            <family>Bitstream Vera Sans Mono</family>
        </prefer>
    </alias>
    <!-- preferred aliases Font Package: ttf-freefont or freefont-ttf  -->
    <alias>
        <family>Helvetica</family>
        <prefer>
            <family>FreeSans</family>
        </prefer>
    </alias>
    <!-- preferred aliases Font Package: ttf-freefont or freefont-ttf  -->
    <alias>
        <family>Courier</family>
        <prefer>
            <family>FreeMono</family>
        </prefer>
    </alias>
</fontconfig>
```

Make sure you have all the fonts listed in the .fonts.conf file installed on your system.

Some additional information you may want to alter the behavior of the Andale Mono font.  That is the UI font used in OpenOffice interface.  This will clean up the font a bit.  This can also be put in your .fonts.conf file.


```
   <!-- From http://bugs.gentoo.org/show_bug.cgi?id=233729 -->
   <match target="font">
     <test compare="eq" name="family">
       <string>Andale Mono</string>
     </test>
     <edit mode="assign" name="hintstyle">
       <const>hintfull</const>
     </edit>
     <test compare="less" name="weight">
       <const>medium</const>
     </test>
     <test compare="less_eq" name="pixelsize">
       <double>7</double>
     </test>
     <edit mode="assign" name="antialias">
       <bool>false</bool>
     </edit>
   </match>
```

Personally I wish Ubuntu would would put some thing like this inside /etc/fonts/conf.d folder to fix OpenOffices UI.

Keep in mind that I have several alias' that change the fonts that I don't like for ones that I consider more visually appealing.  Feel free to change the alias.  Remember for the .fonts.conf file to take effect.  You have to kill xorg and restart it; or log out and back into the system.

Regards to all.  I hope this helps someone.

PS: Had to edit my post; it had hard links to certain font directories.

---

