---
title: "youtube video download...tmp folder"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by dragon1111 on 2011-02-11
Hi guys...until yesterday i used to download youtube videos by saving the flash files that appeared in the tmp folder...But then,all of a sudden the flash files have stopped showing up in the tmp folder...Any reason? Is there anyway i can rectify this....

---

### Post by Wtower on 2011-02-11
The tmp folder in Ubuntu empties on each reboot afaik and is not a proper place to store files for later use. I am afraid you have to find the videos and download them again this time on your personal folder.

---

### Post by treesurf on 2011-02-11
I recall reading that this is an issue with Firefox and the latest version of Flash.

---

### Post by dragon1111 on 2011-02-11
well...wat i meant was that i save the flash file from the temp folder onto my personal music folder...but all of a sudden the flash file doesnt show up in the tmp folder even as the youtube video is playing

---

### Post by dragon1111 on 2011-02-11
@treesurf - But then even yesterday i downloaded a few songs..it seems to be messing up only now

---

### Post by A_M_S on 2011-02-11
Try to pause your video until its completely downloaded to your disk.

I think the flash is erased after you finish the video visualization.

---

### Post by dragon1111 on 2011-02-11
@A_M_S - thats how i've been saving it all these days...the file just doesnt appear at all now

---

### Post by dragon1111 on 2011-02-11
So then...is there any other way i can download youtube videos

---

### Post by Wtower on 2011-02-11
You can try firefox add-ons like downloadhelper.

---

### Post by dragon1111 on 2011-02-11
will try that...thanks

---

### Post by mikewhatever on 2011-02-11
> **dragon1111 said:**
> So then...is there any other way i can download youtube videos

Simply check the Cache folder in your Firefox profile. :P

---

### Post by nick_goodfate on 2011-02-11
I still can see flash files in tmp folder.
Try an other browser...?

---

### Post by dragon1111 on 2011-02-11
@mikewhatevr - how do i find the cache folder...i'm an absolute noob so plz bear with me

---

### Post by mikewhatever on 2011-02-11
> **dragon1111 said:**
> @mikewhatevr - how do i find the cache folder...i'm an absolute noob so plz bear with me

Open the file browser (aka nautilus), press ctrl+l to switch to address bar. In the address bar, you should see something like '/home/your_user_name', add /.mozilla/firefox, then hit enter.

```
/home/your_user_name/.mozilla/firefox
```

That will take you just outside your firefox profile, which is a folder, usually named like this: something_randome.default. Inside that is the Cache folder.
;)

---

### Post by Hoopz on 2011-02-11
I have the same problem just recently I couldn't see the files in /tmp anymore and I am using Chrome

---

### Post by dragon1111 on 2011-02-11
@mikewhatevr - mate..you're not 'mikewhatever' ..you're "mike-the-genius"....thanks a lot...it worked...could you please look up my other thread as well ([http://ubuntuforums.org/showthread.php?t=1685164)...i've](http://ubuntuforums.org/showthread.php?t=1685164)...i've) put up screenshots of the map of my drive as well as sudo fdisk output...i wanna get rid of windows Xp without uninstalling ubuntu...somebody on that thread said my windows seems to have gone but i know for sure i installed ubuntu alongside windows and since then i've had 25GB of unaacounted space on my drive..it definitely must be windows Xp:

---

### Post by free10 on 2011-02-12
If you rename the video while it is loading it won't disappear at the end of loading and then you can just cut and paste to another folder later.

---

### Post by cipherboy_loc on 2011-02-12
I don't fully understand the problem, but you could use youtube-dl:

1) Set it up:
```

sudo apt-get install youtube-dl
sudo youtube-dl --update

```


2) Download the video:
```

cd /home/user/path/to/where/you/want/your/videos
youtube-dl "http://www.youtube.com/watch?v=8QmUW42ziGg"

```


Where [http://www.youtube.com/watch?v=8QmUW42ziGg](http://www.youtube.com/watch?v=8QmUW42ziGg) is the link to your youtube video.



Cipherboy

---

### Post by lisati on 2011-02-12
My radar must be malfunctioning: this thread has been around for at least a day.

I hope you guys realize that according to the Youtube terms of service, you *shouldn't* be downloading their content for later viewing independently of their officially sanctioned methods?

---

