---
title: "convert"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by Aster Phoenix on 2010-04-16
i cant figure out how to convert an mkv file into an mp4 or something i wanna put it on my sony walkman but the last time i tried i failed it didnt work is there a SIMPLE way to do this im not to good with this system yet

---

### Post by wojox on 2010-04-16
I believe Handbrake can do that. It's in the repo's.

---

### Post by MrWES on 2010-04-16
> **Aster Phoenix said:**
> i cant figure out how to convert an mkv file into an mp4 or something i wanna put it on my sony walkman but the last time i tried i failed it didnt work is there a SIMPLE way to do this im not to good with this system yet

Simple? heh...that's a moving target. Anyhow, I'm not sure what file formats a sony walkman supports. But I have come across two methods that work for me in converting mkv files to play on my Sony PS3. The first and the preferred:

I have installed Wine; which will, in short, create a "Windows" operating environment enabling you to run some Windows programs. So install Wine first, and that is available via Synaptic Package Manager. Then you need to download and install mkv2vob:
[http://www.mkv2vob.com/forumdisplay.php?fid=10]("http://www.mkv2vob.com/forumdisplay.php?fid=10")

The vast advantage to using this method under Wine is you don't have to transcode the mkv file and it normally only takes minutes to complete. 

The second method uses a linux script which can be found here:
[http://blog.flexion.org/index.php/2009/08/27/mkv-to-mp4-conversion-script/comment-page-1/#comment-438]("http://blog.flexion.org/index.php/2009/08/27/mkv-to-mp4-conversion-script/comment-page-1/#comment-438")

If you're not familiar with using Linux scripts, you might find this method a bit overwhelming.

I forgot, before I started using mkv2vob, I used this method:

[http://ubuntuforums.org/archive/index.php/t-1064999.html]("http://ubuntuforums.org/archive/index.php/t-1064999.html")
Scroll down and read xaliqen's post. Worked well for me.

---

