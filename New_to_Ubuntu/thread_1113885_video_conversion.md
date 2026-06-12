---
title: "video conversion"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by championboxes on 2009-04-02
Ive been searching through the forums but haven't been able to find anything really good...

What im looking for is a good program that would convert any video (avi, mkv, wmv, etc) to any other type mainly mp4 or whatever the ipod format is... I would really like one with a gui if possible...

---

### Post by aeiah on 2009-04-02
winff

---

### Post by anaconda on 2009-04-02
Why do you want to change to ANY format.  I am happy with always changing to the same format. Which is xvid. But I use mencoder or ffmpeg, which are command-line programs.

Easy to use nevertheless, because I just copy-paste one of the same 3 commands every time. 
one is for backupping a DVD, another is for converting saved programs from TV, and the third is for converting from some strange format to xvid....

---

### Post by championboxes on 2009-04-02
really i dont need to convert to any format other than whatever Ipod/Itunes uses... winff seems to be what I need but I cant get it to work correctly... whenever I get everything set up i press convert and then it tries to open a terminal and then immediately closes... as for ffmpeg I tried to use it but really didnt know what I was doing

---

### Post by aeiah on 2009-04-02
ive never used winff so i dont know what the problem could be. perhaps you're missing a codec or two that its trying to call? does it spit out an error log or anything? try launching winff from the terminal and when something goes wrong, it should tell you in the terminal

---

### Post by logic++ on 2009-04-02
I need to convert videos to iphone/ipod formats too and I use avidemux. Give it a try

---

### Post by nothingspecial on 2009-04-02
It may be that you need libavcodec-unstripped-51 which you can install on it`s own or it is included in ubuntu-restricted-extras package.```


sudo apt-get install ubuntu-resrticted-extras
```

---

### Post by michaelzap on 2009-04-02
I use Avidemux or Handbrake, both of which are excellent GUI video conversion programs.

---

### Post by championboxes on 2009-04-02
Not really sure what is wrong with winff I tried to running in from the terminal but no errors showed up... on the other hand i tried avidemux and it seems to do what I need it to thanks everybody for all your help

---

### Post by Dedoimedo on 2009-04-02
Handbrake, DeVeDe.
Dedoimedo

---

### Post by paul.gevers on 2009-04-03
> **championboxes said:**
> winff seems to be what I need but I cant get it to work correctly... whenever I get everything set up i press convert and then it tries to open a terminal and then immediately closes... as for ffmpeg I tried to use it but really didnt know what I was doing

As maintainer of WinFF for Ubuntu I am really interested in your problem. What I would suggest at this moment is in the options to mark the "Pause on Finish" option, so that you can see what the terminal says. Please post the output here, so that we can help with fixing the issue.

Otherwise, you could try the "Display CMD Line" option. This will open a terminal with the ffmpeg command winff is going to send out (no convertion yet, with this option on). You could then try and use that command to see what and if something is going wrong with ffmpeg.

---

### Post by championboxes on 2009-04-04
> **paul.gevers said:**
> As maintainer of WinFF for Ubuntu I am really interested in your problem. What I would suggest at this moment is in the options to mark the "Pause on Finish" option, so that you can see what the terminal says. Please post the output here, so that we can help with fixing the issue.  
The Pause on Finish option was already marked when it would open a terminal and immediately close...

> **paul.gevers said:**
> Otherwise, you could try the "Display CMD Line" option. This will open a terminal with the ffmpeg command winff is going to send out (no convertion yet, with this option on). You could then try and use that command to see what and if something is going wrong with ffmpeg.

for this I got

```
libavcodec-unstripped-51 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Me@Me-laptop:~$ echo -n "\033]0; Converting 15 - "The Memory of Betrayal Is an Amber-Colored Smile (Part 1)".avi (1/1)\007"
bash: syntax error near unexpected token `('
Me@Me-laptop:~$ /usr/bin/ffmpeg -i "/media/EXTERNAL/Media/Videos/Anime/Darker Than Black 15 - 25 (Subs)/15 - "The Memory of Betrayal Is an Amber-Colored Smile (Part 1)".avi" -f mp4 -r 29.97 -vcodec libx264 -s 704x384 -b 1000kb -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me_method umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libfaac -ab 112kb -ar 48000 -ac 2 "/home/championboxes/15 - "The Memory of Betrayal Is an Amber-Colored Smile (Part 1)".mp4"
bash: syntax error near unexpected token `('
Me@Me-laptop:~$ read -p "Press Enter to Continue" dumbyvarPress Enter to Continue
Me@Me-laptop:~$
```

it says there is a syntax error with the ( but that shouldn't matter b/c its in the title right?

---

### Post by championboxes on 2009-04-04
Anyway just playing around with it i removed the () and tried the ffmpeg command and it didnt do anything it would let me press enter but I didnt see the process with top so idk ```
championboxes@championboxes-laptop:~$ echo -n "\033]0; Converting 23 - "God's in His Heaven".avi (1/1)\007"
> /usr/bin/ffmpeg -i "/media/EXTERNAL/Media/Videos/Anime/Darker Than Black 15 - 25 Subs/23 - "God's in His Heaven".avi" -f mp4 -r 29.97 -vcodec libx264 -s 704x384 -b 1000kb -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me_method umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libfaac -ab 112kb -ar 48000 -ac 2 "/home/championboxes/23 - "God's in His Heaven".mp4"
> read -p "Press Enter to Continue" dumbyvar
> rm "/home/championboxes/.winff/ff090404094435.sh"
> 
> 
> 

```

---

### Post by paul.gevers on 2009-04-05
> **championboxes said:**
> ```
Me@Me-laptop:~$ /usr/bin/ffmpeg -i "/media/EXTERNAL/Media/Videos/Anime/Darker Than Black 15 - 25 (Subs)/15 - "The Memory of Betrayal Is an Amber-Colored Smile (Part 1)".avi" -f mp4 -r 29.97 -vcodec libx264 -s 704x384 -b 1000kb -aspect 16:9 -flags +loop -cmp +chroma -deblockalpha 0 -deblockbeta 0 -b 1250k -maxrate 1500k -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me_method umh -me_range 16 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libfaac -ab 112kb -ar 48000 -ac 2 "/home/championboxes/15 - "The Memory of Betrayal Is an Amber-Colored Smile (Part 1)".mp4"
bash: syntax error near unexpected token `('
```

It is the quote's (") in the name of the file that trigger the problem. I will report this bug upstream.

Thanks for testing and reporting back.

---

