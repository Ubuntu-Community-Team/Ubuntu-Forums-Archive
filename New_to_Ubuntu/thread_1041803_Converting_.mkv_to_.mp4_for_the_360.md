---
title: "Converting .mkv to .mp4 for the 360"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by h8uthemost on 2009-01-16
Anyone know of an app that can convert .mkv's into .mp4's for the 360? I found avidemux, but it is confusing has hell. And I can't find a tutorial that shows step by step how to convert .mkv to .mp4.

So if anyone knows of what I'm looking for, I would really appreciate it.

Thanks.

---

### Post by talsemgeest on 2009-01-16
Do you now what codec the 360 reads? mp4 is just a container, you can have almost any type of video codec in it. For example, you could have an mp4 containing xvid video and mp3 audio.

---

### Post by talsemgeest on 2009-01-16
Ok, from what I have found out it would seem that the 360 uses x264 video and aac audio.

You can follow the tutorial [here](http://ubuntuforums.org/showthread.php?t=634463), or use the script at the bottom of the page.

---

### Post by h8uthemost on 2009-01-17
Thank you talse. I'm definitely going to check the link out.

But I did a little reading, and I'm interested in this Remuxing, as it takes much less time than converting. So I came across this link:

[http://www.linuxlove.info/site/17/converting-remuxing-a-mkv-for-playback-on-the-xbox-360/](http://www.linuxlove.info/site/17/converting-remuxing-a-mkv-for-playback-on-the-xbox-360/)

And I got every single thing installed that it says to install. Then if you read down about half way, it says for files under 4GB(which mine is), simply type in the command:

happy360s <filename>

So, the file I'm wanting to convert(or remux) is: lakeview.terrace-vin.mkv

So I open Terminal, and type happy360s lakeview.terrace-vin.mkv. But I get the error:

bash: happy360s: command not found

Anyone happen to know why I'm getting this error?

Thanks.

EDIT: By the way, the link you gave me talse, I have a simple question. Under Converting Video, it says cd /path/to/your/videos/.

So, say I have my video on my Desktop. Would I type in Terminal:

cd/Desktop/lakeview.terrace-vin.mkv/...the I copy/paste all the other code underneath this? Or, since my computer is named scott, would I type cd/scott/Desktop/lakeview.terrace-vin.mkv/?

Thanks.

^ I have no idea why there is a http: before the word cd.

---

### Post by talsemgeest on 2009-01-17
As for the demuxing, for an mkv it *should* work. It assumes that the mkv has x264 video (which it usually does), but it might not work. 

Once you have gone through the tutorial and get to the command that is not found, instead try this: ```
./happy360s lakeview.terrace-vin.mkv
``` and maybe that will work.

For the second part of your question, you need to know what the command "cd" does. It stands for "change directory", so if you type "cd Desktop", it is similar to double clicking the "Desktop" folder icon. 

So basically, you would type ```
cd /home/scott/Desktop
``` if your username is scott, or just in case you are unsure, this should also work: ```
cd ~/Desktop
```

---

### Post by h8uthemost on 2009-01-17
Thank you so much. You are very helpful. Unforunately though, the command you gave me didn't work either. I get this error now:

bash: ./happy360s: Permission denied

I'll try the one for cd'ing. I hardly EVER have any luck getting any of type of Terminal work to go correctly in Linux. To me Linux is probably the best OS, but very, very, hard to install programs and to run scripts. So there's an advantage and disadvantage for me using Linux.

Luckily though, I'm dual booting Windows(which is a horrible and slow OS, but everything is so freakin' easy on it, wish the devs could have made Linux as easy on certain aspects). And I found this for Windows:

[http://xenonmkv.ev98.net/](http://xenonmkv.ev98.net/)

Which this xenonmkv looks like it does this remuxing. And it looks very extrememly easy to operate. So if I can't get any of this to work in Linux, then I'm just going to hop over to Windows everytime I want to convert and HD movie or show to watch on the 360.

Thank you again for your help.

EDIT: Yeah, so I tried the cd'ing thing. Then after that input that other text into Terminal, and I get this error:

INPUTVIDEO.AVI: no such file or directory


Which I don't know why .avi is in there, I'm trying to convert a .mkv not a .avi. But whatever. Looks like i'm just going to have to hop onto Windows to get this stuff done.

---

### Post by talsemgeest on 2009-01-17
Well, to be quite honest, avidemux would actually be the easiest way to remux. I will see if I can download it and walk you through what you have to do. Have to go away for about half an hour first so I will see if I can do it then.

---

### Post by fenian on 2009-01-17
Use Handbrake,you can download a[ Deb here]("http://handbrake.fr/?article=download").

To use it to convert a mkv....
Go to the file menu and choose source
select your .mkv file
in the right hand presets menu under Gaming Consoles there is a preset for Xbox 360.Choose that.
Click start and it will encode the video to H.264

---

### Post by talsemgeest on 2009-01-17
> **fenian said:**
> Use Handbrake,you can download a[ Deb here]("http://handbrake.fr/?article=download").

To use it to convert a mkv....
Go to the file menu and choose source
select your .mkv file
in the right hand presets menu under Gaming Consoles there is a preset for Xbox 360.Choose that.
Click start and it will encode the video to H.264
I believe the OP wants to remux, not convert.

OK, using avidemux, you first click open and find your video file. In the box on the left that says "Format", change the drop-down box to "mp4". Now on the top menu, click "Save", choose where you want to save it, and give it a name ending in ".mp4", eg "myvideo.mp4". If remuxing will work, this will do it.

---

### Post by fenian on 2009-01-17
Because of it's unique track structure remuxing .mkv files is not as straight forward as other containers.If you want to remux you will have to extract the audio/video tracks (using mkvextract), then you need to use Mplayer to make an audio dump,then you need to noralise the audio dump,then you may need to convert the audio to AAC,and then you remux it into mp4.

---

