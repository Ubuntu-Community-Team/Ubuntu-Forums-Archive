---
title: "How can I download, then shut down? -Also, I can't get the &quot;at&quot; command to work"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-28
Hi. ( I have Ubuntu 10.10 32 bit version installed )

 I would like to be able to download some stuff from youtube, then after the items are downloaded, I want to completely shut down the computer. Is there a script that would do this? Would it be like a list of URL's to the youtube items with the shut down command in a script? or would I load up the download queue in Firefox, start downloading, and have a script that somehow knows when Firefox is done and then shuts down the computer?


 Also, I have tried to get the "at" command to work but can't.
For example:
 I open a terminal and type "at 1700"
  then I get a message "warning: commands will be executed using /bin/sh" then I get an "at>" prompt. I type "firefox" ( to use an example ) then hit return and I get another "at>" prompt.  Then I type control "d".  I wait until 1700 and nothing happens.

---

### Post by ShadowMage on 2010-12-28
Hi,

Are you downloading from the terminal or from your web browser? I ask because you can invoke the shutdown command to have the computer shutdown automatically.

Use this to power off the computer "now" (i.e. when the command gets executed):
```
sudo shutdown -P now
```So, you can either build a script that has that at the end, or if you  just need to download one file you also might want to consider just  chaining the commands into one like this:
```
sh -c 'command1 && command2'
```This will run command1 first, and then command2. So if command2 says to shutdown, it will only get executed after command1 is complete.

NOTE: The shutdown command requires superuser privileges (hence the sudo), so you may find that when you come back from afk, instead of the computer being shutdown, it'll be sitting there waiting for you to enter your password. You can work around this by using a root session instead of sudo, but I cannot recommend this on ubuntuforums because of the security risks involved in using a root session.

Hope this helps.

---

### Post by ShadowMage on 2010-12-28
Another alternative is if you know how long you need to wait until shutdown, you can specify the number of minutes for the shutdown command. For example, let's say you want to shutdown in 2 hours, you can forget my previous post and just enter the command

```
sudo shutdown -P +120
```And the command will get executed right away, but what it will do is it will wait 120 minutes and THEN shutdown. In the meantime, your operating system will be fully operational.

Hope this helps.

---

### Post by s1baker on 2010-12-28
thanks.
 I actually have been using an addon for Firefox called "download helper" to download stuff from youtube. I can go to youtube and click on the urls's of the stuff I want to download and while the first item is downloaded, the other items that I want to download will be placed in a download queue.
 That said, I guess the script would need to have to have some way of knowing when firefox is through downloading for the script to know when to shut down.

---

### Post by ShadowMage on 2010-12-28
Ok I see, makes sense. Unfortunately, I don't know how a script might be able to tell when firefox is through downloading. So if it were me, I'd probably just overshoot the estimated time (to avoid having a shutdown before it's actually done) and use the shutdown command.

One of the things I do is I sometimes use the shutdown command when listening to music before bed, but in this case I know exactly how long until the album will be finished. Since your download speed will vary, downloads are a bit tougher to estimate. So I wish I had a better solution but I hope I've been helpful and maybe someone else has a better solution.

Cheers.

---

### Post by s1baker on 2010-12-28
I wonder if I could use the command:
sh -c 'command1 && command2' to do this?

 I wonder, for instance, if 'command1' could be some Ubuntu command to download a file ( or in this case a link to a youtube url ) and then command2, same thing, until all the url's are listed as separate commands, and then the last command would be the 'shut down' command.

 It would seem that there should be a Linux command to download a file, without having to use Firefox ( or any browser for that matter )

---

### Post by ShadowMage on 2010-12-28
Yes, you can use the wget command to download a file from the web. But the URL you see at the top of your browser when watching a youtube video is not a URL to the video file itself, that's the thing. But let's say you know the URL of a file you wish to download, you can just supply it to wget like
```
wget http://www.somedomain.com/path/to/file
```You might also be interested in a package called "youtube-dl", which is in the repositories. It's for downloading youtube videos. I didn't have much luck with it when I tried it out in the past but maybe I can give it another whirl later and see how it goes.

---

### Post by s1baker on 2010-12-28
thanks, I will give it a shot

---

### Post by ShadowMage on 2010-12-28
Okay, so, for ordinary files, wget should do the trick. And I also noticed a way to only need your password at the beginning and still avoid using a root session. If you run the sh  command with sudo, the inner commands will also be executed as root. So it would look something like this:

```
sudo sh -c 'wget http://path/to/file1 && wget http://path/to/file2 && shutdown -P now'
```As for youtube-dl and youtube videos, youtube-dl supposedly accepts the page url but it doesn't seem to work.

The usage example given in the man pages is
*youtube-dl "http://www.youtube.com/watch?v=foobar"*

But when I try it with an actual video page, I get the error
*ERROR: format not available for video*

My guess is that youtube-dl hasn't been updated to download from the current youtube.

---

### Post by s1baker on 2010-12-28
The addon "download helper" that I have attached to Firefox will allow one to copy the url of a youtube video, but the url is super long.
 Here is an example of one url pulled off of youtube at random:

[http://v10.lscache8.c.youtube.com/videoplayback?ip=206.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=907605%2C901801%2C908602&algorithm=throttle-factor&itag=5&ipbits=8&burst=40&sver=3&expire=1293620400&key=yt1&signature=178C5DEFE7B968F116DEC1D01C3D0066F8B4514F.CD9345C0165E274385424DFE49FDA171BDE00C79&factor=1.25&id=a5df6e7cca173012](http://v10.lscache8.c.youtube.com/videoplayback?ip=206.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=907605%2C901801%2C908602&algorithm=throttle-factor&itag=5&ipbits=8&burst=40&sver=3&expire=1293620400&key=yt1&signature=178C5DEFE7B968F116DEC1D01C3D0066F8B4514F.CD9345C0165E274385424DFE49FDA171BDE00C79&factor=1.25&id=a5df6e7cca173012)
(in the preview of my post this file is 7 lines long) 

So I guess that this would have to be placed in a text file but something like this:

sh -c wget (super long url here) && wget (next super long url here) && shutdown 

Then somehow the terminal would run the text file holding these instructions.

Does that seem right?

One other problem is that when the file is saved it is saved as the name "videoplayback". It would appear that there would need to be some way of giving a name to each of the downloaded files so that the first file  might be called something like "file1", the next "file2" etc.
Any ideas?

---

### Post by s1baker on 2010-12-28
actually I should have put 

sudo sh -c at the beginning of the list 

and

shutdown -P now

at the end.

---

### Post by ShadowMage on 2010-12-29
Hi,

Don't forget the quotes also, see post [#9]("http://ubuntuforums.org/showpost.php?p=10290319&postcount=9"). But I think you will still have problems because I tried to wget the link you provided and I got an error. I'm not sure what magic the firefox addon does, because I think the URL becomes expired after or something (in any case it doesn't seem to work with wget).

In short, the only thing in the way of a perfect solution for you is that neither of us can download youtube videos from the terminal. I'm thinking you might want to open a separate thread on that, since you'll need someone else who might know how to do it (or if it can be done).

Good luck, and feel free to let me know how it goes or ask if you have more questions.

---

### Post by s1baker on 2010-12-29
I got this to work by taking the url of the youtube video that I got from using the addon "download helper" on Firefox and shrinking it down using [www.tinyurl.com](www.tinyurl.com).
 It seems that wget cannot work with that long of a url link from youtube.

 Anyway, I make a list of this links in a text editor, something like this:

sudo wget    tinyurl-link1-here  -O file1 &&
wget         tinyurl-link2-here  -O file2 &&
wget         tinyurl-link3-here  -O file3 &&
etc 
etc
shutdown -P now

and copied and pasted it into a terminal.

Thanks

---

