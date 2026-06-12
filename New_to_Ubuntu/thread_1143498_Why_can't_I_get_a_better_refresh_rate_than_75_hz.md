---
title: "Why can't I get a better refresh rate than 75 hz?"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by abben on 2009-04-30
Fresh off of a reinstall, the first thing I noticed is that, I think, the screen is more painful to look at than it used to be.

Another thing I noticed is that, whenever I do

```
sudo dpkg-reconfigure xserver-xorg
```, it configures nothing other than my keyboard. And in the xorg.conf file, it gives a generic "Configured Monitor" entry that is totally empty.

So I manually edited xorg.conf to include...

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option "DPMS"
        HorizSync 30-97
        VertRefresh 50-180
EndSection

Section "Screen"
        Identifier      "Generic Monitor"
        Monitor     "ViewSonic G810"
        DefaultDepth 16

        Subsection "Display"
                Depth       16
                Modes       "1280x1024" "1024x768" "800x600"
                ViewPort    0 0
        EndSubsection

        Subsection "Display"
                Depth       24
                Modes       "1600x1200" "1400x1050" "1280x1024" "1024x768" "800x600"
                ViewPort    0 0
        EndSubsection
EndSection
```

And, when I run xrandr, it gives me these choices:

```
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      75.0*    60.0  
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     70.0     65.0     60.0  
   1280x960       60.0  
   1280x800       60.0  
   1152x870       75.0  
   1152x864       75.0  
   1280x768       60.0  
   928x696        60.0  
   896x672        60.0  
   960x600        60.0  
   832x624        75.0  
   840x525        60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     60.0     59.0     73.0  
   640x400        60.0  
   576x432        75.0  
   640x384        60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0  
   320x240        75.0     73.0     60.0  

```

Why on earth is my max refresh rate 75 hz, when I clearly specified  higher thresholds in xorg.conf?

Thanks for any help.

---

### Post by Wiebelhaus on 2009-04-30
Watching thread...

---

### Post by abben on 2009-04-30
shameless bump

---

### Post by Wiebelhaus on 2009-04-30
> **abben said:**
> shameless bump

Someone's gonna yell at ya about that , A while back they started asking folks not to bump but every 24 hours , they have an "Unanswered post team" that starts at the back of the heap and work their way back.

---

### Post by abben on 2009-05-02
After much perusing of the internets I remain in the same situation. Would appreciate any advice.

---

### Post by overdrank on 2009-05-02
> **abben said:**
> After much perusing of the internets I remain in the same situation. Would appreciate any advice.

Ok I am no expert but, fresh reinstall of Ubuntu. What version?
Edit I see xfce, 8.10 or 9.04 is what I am asking.
What is the model of the graphics card?
Have you tried the xfix option when booting into recovery mode?

---

### Post by abben on 2009-05-03
> **overdrank said:**
> Ok I am no expert but, fresh reinstall of Ubuntu. What version?
Edit I see xfce, 8.10 or 9.04 is what I am asking.
What is the model of the graphics card?
Have you tried the xfix option when booting into recovery mode?

Thank you for the response, overdrank.

I just installed Xubuntu 8.10
The model of the graphics card in [Nvidia RIVA TNT2]("http://en.wikipedia.org/wiki/RIVA_TNT2") (pretty old, but it shows up when I "lspci -v")
And, yes, I did try the xfix option. Unfortunately it didn't appear to change anything. My xorg.conf got re-written to the same generic one that's produced by a dpkg-reconfigure xserver-xorg.

To be clear, my only objective is to increase the refesh rate of my monitor, so I don't have to tear up when I'm looking at the screen. Any trick whatsoever that might help me do this would be awesome. 

Can I, for instance, just force-feed a preferred refresh rate in the modeline of my xorg.conf file?

---

### Post by overdrank on 2009-05-03
Hi and I have seen many issues with the Nvidia RIVA TNT2 graphics with intrepid. I have no experience with that graphics but have seen where some users have added Hardy repos to the sources list to install displayconfig-gtk that has help. Sorry I could not help any more.

---

### Post by mister_pink on 2009-05-03
Are you 100% sure your hardware is capable of higher refresh rates? I know my screen won't let me go higher than that.

---

### Post by abben on 2009-05-03
> **overdrank said:**
> Hi and I have seen many issues with the Nvidia RIVA TNT2 graphics with intrepid. I have no experience with that graphics but have seen where some users have added Hardy repos to the sources list to install displayconfig-gtk that has help. Sorry I could not help any more.

I appreciate you taking the time to offer a suggestion. I did try display-config-gtk, but I met with dependency issues. When I --force-depends it, it installed, but wouldn't run.

However I was able fix the problem, thanks to the [this wiki page]("https://wiki.ubuntu.com/X/Config/Resolution"). Apparently, we aren't supposed to actually use dpkg-reconfigure xserver-xorg for screen resolutions anymore.

---

### Post by CatKiller on 2009-05-03
> **abben said:**
> Why on earth is my max refresh rate 75 hz, when I clearly specified  higher thresholds in xorg.conf?

Video bandwidth. number of pixels × refresh rate = bandwidth. If your monitor can't handle that bandwidth then you either need to decrease the refresh rate or the number of pixels. I'm not entirely sure why you imagined that an affordable monitor would be able to do 180 Hz at a large resolution.

As far as I can tell, the maximum refresh rate for that monitor at 1280×1024 is 85Hz.

---

### Post by Zoowey on 2009-05-03
Well my 1280x1024 19" LCD has a refresh rate of 60Hz so I don't think yours can go up much higher. If you force the Hz's higher then what the monitor supports you'll end up damaging it.

---

### Post by blackened on 2009-05-03
This isn't an LCD we're talking about. According to Tom's Hardware, it should be capable of much high refresh rates.
[http://www.tomshardware.com/reviews/comparison,497-10.html]("http://www.tomshardware.com/reviews/comparison,497-10.html")

[ATTACH]112261[/ATTACH]

> **abben said:**
> I appreciate you taking the time to offer a suggestion. I did try display-config-gtk, but I met with dependency issues. When I --force-depends it, it installed, but wouldn't run.

However I was able fix the problem, thanks to the [this wiki page]("https://wiki.ubuntu.com/X/Config/Resolution"). Apparently, we aren't supposed to actually use dpkg-reconfigure xserver-xorg for screen resolutions anymore.

Funny, that's my favourite go-to link for display issues, and just happens to be the direction I was gonna head you in. Glad you got it sorted out.

---

### Post by HappySmack on 2009-05-04
A couple of hours ago I lost my max resolution capability. I have a Nvidia TNT2 model 64 32meg. I just installed Opera and when I closed it, my resolution went to 800x600. I have tried installing Nvidia site drivers (NVIDIA-Linux-x86-71.86.09-pkg1), repo drivers, Envy's setup and some others. Nothing is getting me back to 'at least 1024x768'. I have attempted the procedure as noted earlier at : [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) . Still nothing.

  I am running Jaunty fresh install,NVIDIA RIVA TNT2 Model 64,HP Pavillion m70 monitor, 1.5 gig AMD, 1.25 gig ram and, ext4 filesystem. And currently all other drivers are uninstalled but the ones from Nvidia site (NVIDIA-Linux-x86-71.86.09-pkg1). I know that I can achieve higher resolution than this, I have had no problems with 8.10 and a resolution of up to 1280x???. If someone has this card and wants to post their xorg.conf , that would be most appreciated. Any help is appreciated.

---

### Post by blackened on 2009-05-04
> **HappySmack said:**
> A couple of hours ago I lost my max resolution capability. I have a Nvidia TNT2 model 64 32meg. I just installed Opera and when I closed it, my resolution went to 800x600. I have tried installing Nvidia site drivers (NVIDIA-Linux-x86-71.86.09-pkg1), repo drivers, Envy's setup and some others. Nothing is getting me back to 'at least 1024x768'. I have attempted the procedure as noted earlier at : [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) . Still nothing.

  I am running Jaunty fresh install,NVIDIA RIVA TNT2 Model 64,HP Pavillion m70 monitor, 1.5 gig AMD, 1.25 gig ram and, ext4 filesystem. And currently all other drivers are uninstalled but the ones from Nvidia site (NVIDIA-Linux-x86-71.86.09-pkg1). I know that I can achieve higher resolution than this, I have had no problems with 8.10 and a resolution of up to 1280x???. If someone has this card and wants to post their xorg.conf , that would be most appreciated. Any help is appreciated.

Start a new thread with a clear title and repost your problem there so that others may benefit from any help you receive. Thread hijacking is strongly discouraged.

---

