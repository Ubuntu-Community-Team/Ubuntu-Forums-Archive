---
title: "Problem playing .mkv and video tearing"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by savvio on 2011-05-14
Hi, 
I`ve been using Ubuntu 10.04 LTS 32bit for the last 2 months on my Acer Extensa 5635ZG laptop(Intel Pentium Dual-Core T4300 2.10 Ghz , 3.00 GB RAM DDR2 , NVIDIA GeForce G105 M 512 MB). I`m unable to play HD Video (.mkv format) and i`ve tried many different video players but it`s still the same result - only sound with some pictures of the video :(( I`m using Windows 7 too and it`s not probelm to play 1080p videos.

My other problem is video tearing,unmeaning what video format i`m watching that happens > [http://img695.imageshack.us/img695/7877/tearingsimulated.png](http://img695.imageshack.us/img695/7877/tearingsimulated.png)

SORRY FOR THE BAD ENGLISH!

---

### Post by corrytonapple on 2011-05-14
Although I have not tried it, in the Ubuntu Software Center, you will find an application called GNOME MPlayer.  Try using that and see if it will play.  
Good luck and report back!

---

### Post by savvio on 2011-05-14
I tried GNOME MPlayer,but the problem remains :(

---

### Post by yetiman64 on 2011-05-14
For the screen tearing problem you can check [[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1390284[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1390284")

I have used the first post in the link to fix screen tearing here previously. Good luck.

---

### Post by corrytonapple on 2011-05-14
> **savvio said:**
> I tried GNOME MPlayer,but the problem remains :(
The tearing problem remains or you still cannot play the videos?  If you cannot play the videos, and they are not copywrited, you can try converting them to another format.  I have not used any video converters, so you could just search the Ubuntu Software Center for "Video Converter".  See what comes up and supports converting from .mkv to maybe .avi.  Install it and try playing the video in your favorite video player.  If it is copywrited, what video are you trying to play?  It kinda sounds like an iTunes format.

---

### Post by SeijiSensei on 2011-05-14
Have you installed the proprietary drivers for your NVIDIA card yet?  If not, find the "Additional Drivers" application and run it.  It should detect your card and propose to install drivers for it.  Let it do so and reboot.

Now run "sudo apt-get install smplayer" to install an excellent front-end for mplayer.  In the smplayer menus, pick Options > Preferences > General and click on the Video tab.  Pick "vdpau" from the driver options at the top and click OK.  Now open your video from the File menu and see if it plays more smoothly.

---

### Post by savvio on 2011-05-14
> **corrytonapple said:**
> The tearing problem remains or you still cannot play the videos?  If you cannot play the videos, and they are not copywrited, you can try converting them to another format.  I have not used any video converters, so you could just search the Ubuntu Software Center for "Video Converter".  See what comes up and supports converting from .mkv to maybe .avi.  Install it and try playing the video in your favorite video player.  If it is copywrited, what video are you trying to play?  It kinda sounds like an iTunes format.

The video is playing,it is not copywrited,but it`s still tearing and i think converting is not  a proper solution.Thanks for the help anyway.


> **SeijiSensei said:**
> Have you installed the proprietary drivers for your NVIDIA card yet?  If not, find the "Additional Drivers" application and run it.  It should detect your card and propose to install drivers for it.  Let it do so and reboot.

Now run "sudo apt-get install smplayer" to install an excellent front-end for mplayer.  In the smplayer menus, pick Options > Preferences > General and click on the Video tab.  Pick "vdpau" from the driver options at the top and click OK.  Now open your video from the File menu and see if it plays more smoothly.

I installed the drivers that way,the easiest i think :d i prefer using SMPLAYER and your information helped me very much,now .mkv videos play smooth except the tearing.

---

### Post by corrytonapple on 2011-05-14
I meant converting the videos so a video player could play them, not to remove the tearing. :P
Did you use the link that yetiman64 provided?  It solves the tearing problem.
Good luck

---

### Post by savvio on 2011-05-14
> **corrytonapple said:**
> I meant converting the videos so a video player could play them, not to remove the tearing. :P
Did you use the link that yetiman64 provided?  It solves the tearing problem.
Good luck


Now the SM player plays .mkv videos.SeijiSensei told me the solution.I used yetiman64`s link but this didn`t help.

---

### Post by akand074 on 2011-05-14
You could try to install the latest drivers via the NVidia website. Also you can try building an [svn Mplayer]("http://ubuntuforums.org/showthread.php?t=1542240") using SMPlayer as a front-end, which is what I have as a backup for anything VLC won't run.

---

### Post by corrytonapple on 2011-05-14
Here is another link, although it may be the same set of ideas.
[http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu/](http://www.omgubuntu.co.uk/2010/01/how-to-fix-video-tearing-in-videos-nvidia-ubuntu/)

---

### Post by jtarin on 2011-05-14
You haven't listed all players you have tried. VLC is my choice for .mkv

---

### Post by savvio on 2011-05-15
Hi,the problem is solved.
First i did that [http://ubuntuforums.org/showthread.php?t=1390284](http://ubuntuforums.org/showthread.php?t=1390284) with compiz , but this did`t help but i  kept the settings.
Second i unchecked [http://imageshack.us/f/40/screenshotnvidiaxserverz.png/](http://imageshack.us/f/40/screenshotnvidiaxserverz.png/)
Force Full GPU Scaling ,then made these setting for SMplayer and VLC,output driver set to VDPAU >[http://imageshack.us/f/692/screenshotsmplayerprefe.png/](http://imageshack.us/f/692/screenshotsmplayerprefe.png/) for SMlpayer.For VLC i did this > [http://imageshack.us/f/834/screenshotpreferences.png/](http://imageshack.us/f/834/screenshotpreferences.png/)

checked "Use GPU acceleration" and "Skip H.264 in-loop deblocking filter" set to "All"
Everything run smooth and without tearing.
Thanks for the help. ;)

---

### Post by corrytonapple on 2011-05-15
You are welcome.  :)
Since your thread is solved, please go up to "Thread Tools" in the top right hand corner of this page and then click "Marked As Solved".
Happy Ubuntu-ing!

---

