---
title: "[SOLVED] Can Anyone Help Me Install yaWP (Yet Another Weather Plasmoid)"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Laysan_A on 2008-12-23
Hi, I've installed yawp a few times using the 64bit .deb file version and Gdebi. It never shows-up, and I don't know what file to call to try to start it manually....

I've also tried to install kweather, unsuccessfully,  and with some help, installed the weather plasmoid from cvs successfully. I'm really not too excited by the weather plasmoid. I like the look of yawp and there have been some really good things said about it on the download page. 

I've seen screenshots of yawp running on k-desktops with the oxygen theme, so some folks have done it. If you can help me I'd appreciate it very much.

---

### Post by zephyrcat on 2008-12-24
This is what you mean, right?

[http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106](http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106)

It looks like the .deb package is only for AMD 64-bit systems, which means you must have installed the 64-bit version of Ubuntu and have an AMD processor.

You might have better luck downloading the source package and following these instructions:

[http://www.kde-look.org/help/index.php?type=70&PHPSESSID=9b9cee06fa5f333a4794d4f74262b231](http://www.kde-look.org/help/index.php?type=70&PHPSESSID=9b9cee06fa5f333a4794d4f74262b231)

---

### Post by Laysan_A on 2008-12-25
Hi zephyrcat. Thanks for responding. Yep, that's it. I thought about installing the source from the terminal, but I'm so new to Linux that I can't tell or translate the differences in command structure between distros. I'd rather not screw something up by trying to install using instructions for suse (for instance) - that's what the developer uses. If you can verify that that proceedure corresponds to an ubuntu installation, I'll give it a go. 

(Oh, see my sig. below ;) )

---

### Post by Dedoimedo on 2008-12-25
Did you install by double-clicking or running from the command line. How about you try the command line:

```

dpkg -i name.deb

```

See if any errors comes up.

If none, next try the following commands to locate the binary for the yawp.

```

which yawp

```

Also type yawn in terminal and then tap the Tab button twice, it will show you all command completions for yawp. If nothing comes up, then it might not be in the path.

So we need to find the file.

Either locate or find:

```

sudo updatedb
locate yawp

```

```

cd /
find . -name yawp

```

See if this helps.

Dedoimedo

---

### Post by Laysan_A on 2008-12-25
Hi Dedoimedo, Thanks for the advice.

I reinstalled the .deb package as you said - no errors.
The "which" command turned-up nothing.
The "updatedb" "locate" turned-up a list of locations I'll attach, since I still don't know what to do with it...
The "find . " "-name" also turned-up nothing but a list of denied permissions.

Thanks again for your help.

---

### Post by Dedoimedo on 2008-12-25
Hmmm ... gimme some time, I'll test this.
Just give me the link to where you found this app and what it does.
Dedoimedo

---

### Post by zephyrcat on 2008-12-25
This is the plasmoid in question I believe: (you would have to ask op to be sure)

[http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106](http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106)

I tried the source install for 0.6 without luck. I get an error on the "make" command saying something about no rule to make target clean.

Using Kubuntu 8.10 in VirtualBox. (Ubuntu user myself.)

---

### Post by Laysan_A on 2008-12-25
Thanks to both of you. 
Sorry I've been away for a while...
I'm sure you'll have it sorted out in no time at all (just can't live without some kind of weather on my desktop :) )

---

### Post by Dedoimedo on 2008-12-26
I played with it for about 17 minutes. It requires cmake to work. But then throws a few errors here and there. Looks broken ... I'd say try a different widget/app... :(
Dedoimedo

---

### Post by Laysan_A on 2008-12-26
Thanks Dedoimedo, I will. I think someone has gotten liquid weather to work on kubuntu 8.10. I'll give that a go. Appreciate all your help.

---

### Post by zephyrcat on 2008-12-26
I would have to agree. Don't they test these things in a VM?

I have not gotten Weatherforecast to work either, but there is a deb package (again for AMD 64) hrere:

[http://debian.unixcod.org/binary/weatherforecast-0.4_amd64.deb](http://debian.unixcod.org/binary/weatherforecast-0.4_amd64.deb)

[http://www.kde-look.org/content/show.php/weatherforecast?content=92149](http://www.kde-look.org/content/show.php/weatherforecast?content=92149)

Another options appears to be SuperKaramba with the kweather-karamba theme:

[http://netdragon.sourceforge.net/ssuperkaramba.html](http://netdragon.sourceforge.net/ssuperkaramba.html)

[http://www.kde-look.org/content/show.php/kweather-karamba?content=19211](http://www.kde-look.org/content/show.php/kweather-karamba?content=19211)

Testing that now.

Update: Here is what I have found so far for SuperKaramba:

sudo apt-get install kdebase-dev

(There are more unsatisfied dependencies, but I have not figured them out yet.)

Follow these instructions:

[http://netdragon.sourceforge.net/scompiling.html](http://netdragon.sourceforge.net/scompiling.html)

Then for kweather-karamba, follow these:

[http://www.kde-look.org/help/index.php?type=38](http://www.kde-look.org/help/index.php?type=38)

---

### Post by Laysan_A on 2009-01-06
Hi Zephyrcat. Did you get any of these to work? I tried to install kweather once before and it just never showed-up on the desktop. I tried to use liquid weather, and it has some dependency issues (likes to believe PyQt isn't installed), but after doing the work-around it installed and showed-up. It won't update, though, without killing and restarting it, and the maps and webcams don't work either.

Sorry I took so long to get back...I haven't been checking my email lately.

---

