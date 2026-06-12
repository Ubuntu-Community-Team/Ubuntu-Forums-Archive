---
title: "BBC iplayer downloads"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Brian_new_to_linux on 2010-10-21
Hello All

I am very new to Linux and have just installed Ubuntu 10.10 Netbook edition on a first gen Acer Aspire one.  

I downloaded BBC iplayer and it all seemed to work - even Adobe Air appeared to have installed. 

When I try to download programmes however the BBC desktop opens but the download does not start. I believe this may be an issue with Adobe Air, as when I looked at my applications Air is shown as an installer, which when selected looks for a file to run, ie it is looking for itself (software with an existential issue?).  Short of turning the webcam on & holding up a mirror, how do I get Air to work?

I would like to be able to watch content offline as wife+me are away next weekend with no guarantee of free wifi.

This may be a known issue but I can't find a solution in the forums recent postings so any previous fix may be out of date.

Thanks in advance for your help

Brian (noob)

---

### Post by migs73 on 2010-10-21
Didn't know it was available to linux.  :P

Tried to install it myself but kept getting Adobe download errors. Maybe there is a problem at their end. Try downloading/installing it again?

---

### Post by AngusH on 2010-10-21
> **migs73 said:**
> Didn't know it was available to linux.  :P

Tried to install it myself but kept getting Adobe download errors. Maybe there is a problem at their end. Try downloading/installing it again?

Just so you know for future reference it's an adobe air program. That makes it totally cross platform in theory (although they tend to run a bit better on windows because that's what their tested on).
Angus

---

### Post by migs73 on 2010-10-21
[http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux](http://iplayerhelp.external.bbc.co.uk/help/downloading/air_linux)

about half way down some info on making the .bin executable

Maybe this is what you need?

---

### Post by migs73 on 2010-10-21
> **AngusH said:**
> Just so you know for future reference it's an adobe air program. That makes it totally cross platform in theory (although they tend to run a bit better on windows because that's what their tested on).
Angus

I know it's just I'm sure last time I looked (2 years ago?), I think they were still working on it for Linux.
I can stream iplayerHD to my TV (A sony) and it looks amazing, as good (better?) as standard def via satellite, but still get the annoying spinning circles every 15mins or so. Now I know I can download, cool. 

Just need to get it working now!

---

### Post by AngusH on 2010-10-21
> **migs73 said:**
> I know it's just I'm sure last time I looked (2 years ago?), I think they were still working on it for Linux.
I can stream iplayerHD to my TV (A sony) and it looks amazing, as good (better?) as standard def via satellite, but still get the annoying spinning circles every 15mins or so. Now I know I can download, cool. 

Just need to get it working now!

Ah fair enough. I didn't know what linux was two years ago (apart from my hyper techy neighbor mentioning it every so often) but I know that the iplayer worked since 9.10 (it was one the the programs I absolutely had to have when I switched over).

---

### Post by Brian_new_to_linux on 2010-10-21
Hi folks

I did look at the bbc "help" page you directed me to, but I an a total noob and did not follow how to make Air work.  Do I type something into terminal mode? (never done this before). 
I am very puzzled that a public service broadcaster should tie itself to  proprietary software so tightly- Though they did also do this at the very beginning  with "listen again" needed realplayer of all things!
Anyone help me make sense of how to make "Air executable" ?

Thanks so far.

Brian

---

### Post by perrti-y02 on 2010-10-21
If you are willing to give it a go, get-iplayer is a fantastic program. It is command line, but I find it quite simple to use. I am fairly sure it is in the Ubuntu repositories. I would advise making sure you have ffmpeg installed as well.

Essentially is allows you to stream the files off iPlayer to a 'regular' video file (i.e. free from all the iPlayer limitations). I think it is an amazing program and it is the sole reason I have all the recent Dr Who series saved on my desktop...

---

### Post by migs73 on 2010-10-21
> **perrti-y02 said:**
> If you are willing to give it a go, get-iplayer is a fantastic program. It is command line, but I find it quite simple to use. I am fairly sure it is in the Ubuntu repositories. I would advise making sure you have ffmpeg installed as well.

Essentially is allows you to stream the files off iPlayer to a 'regular' video file (i.e. free from all the iPlayer limitations). I think it is an amazing program and it is the sole reason I have all the recent Dr Who series saved on my desktop...

I'll be checking that out! What file type does it save as?

---

### Post by migs73 on 2010-10-21
> **Brian_new_to_linux said:**
> Hi folks

I did look at the bbc "help" page you directed me to, but I an a total noob and did not follow how to make Air work.  Do I type something into terminal mode? (never done this before). 
I am very puzzled that a public service broadcaster should tie itself to  proprietary software so tightly- Though they did also do this at the very beginning  with "listen again" needed realplayer of all things!
Anyone help me make sense of how to make "Air executable" ?

Thanks so far.

Brian

Brian

I think what it is trying to say is open a terminal (Applications > Accessories > Terminal) and type in (or copy it from here, just highlight it and them put your mouse cursor on the terminal and do a middle click, which will probably be both left and right buttons together);

```
sudo chmod +x AdobeAIRInstaller.bin
```

enter your password when prompted (it will not show up at all on the screen, not even asterisks, this is normal)

Then if you double click the file it should run the installer (I think?).

---

### Post by Brian_new_to_linux on 2010-10-21
Thanks migs

I think this is just what I was looking for- I will try it tonight.

Cheers 

Brian

---

### Post by migs73 on 2010-10-21
> **Brian_new_to_linux said:**
> Thanks migs

I think this is just what I was looking for- I will try it tonight.

Cheers 

Brian

FYI I just tried get-iplayer, and it works too. I couldn't get onto the site where the docs were, but found a forums page with a 3 lines of commands that seem to be all you need!
Quote;
"Get a current listing of what's available, save it in home directory
get-iplayer >~/iplayer-listing.txt

Having found some interesting progs and noted the numbers in the left-hand column, download them:
get-iplayer --get 123 537

Get them with subtitles because I want to watch them very late at night with the volume down:
get-iplayer --subtitles --get 123 537

The first 2 commands probably cover more than 90% of users' needs."


Something else to look at if you can't get Air going

---

### Post by migs73 on 2010-10-27
Brian

Did you get your programs?
If not I can recommend get-iplayer. Having found the docs (site working now) I can now download in HD (where available) and the resultant file is excellent.

---

