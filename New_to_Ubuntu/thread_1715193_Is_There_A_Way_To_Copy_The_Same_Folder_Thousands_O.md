---
title: "Is There A Way To Copy The Same Folder Thousands Of Times Easily?"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by giddyup306 on 2011-03-26
Here's the deal.  I have all my music backed up on a single drive.  Most of the albums also contain the artwork.  I want to use this drive with my CD player in my car, however, the cd player reads the first file that was written to the drive.  Sometimes this file is the album artwork, which it thinks is a movie.  It then tries playing it.  Once this happens, I loose the touch screen to skip it, and it stays at the same picture for about 30 seconds.  This is very annoying, especially if I have the entire liner notes for the album on there.  

Here's the plan...

My music is organized in a main folder called "Music", then two sub folders called artist and album.  What I want to do is create a third sub folder called "Artwork".  This way it won't try and "play" the image.  I could past the "Artwork" folder manually into every single folder, but if there was a way to copy said folder into ever folder in the artist folder, that would be great.  

I did some searching, and it looks like there is a way to do it in the terminal, but it confused me, and seems like a lot more work than just using Nautilus.

If someone can help me with this you're going to get a serious e-high 5. :P

---

### Post by hakermania on 2011-03-26
I am a bit experienced with such problems and terminal too, but, to be honest, I didn't get what you wanna do....
In simple english you want to...? (for the solution we don't care so much for the purpose :D, but make clear what you wanna do (e.g. copy each file from all subfolders in a main subfolder named Artwork?))

Sorry if it was clear and I was the one who didn't get it

---

### Post by VastOne on 2011-03-26
> **giddyup306 said:**
> Here's the deal.  I have all my music backed up on a single drive.  Most of the albums also contain the artwork.  I want to use this drive with my CD player in my car, however, the cd player reads the first file that was written to the drive.  Sometimes this file is the album artwork, which it thinks is a movie.  It then tries playing it.  Once this happens, I loose the touch screen to skip it, and it stays at the same picture for about 30 seconds.  This is very annoying, especially if I have the entire liner notes for the album on there.  

Here's the plan...

My music is organized in a main folder called "Music", then two sub folders called artist and album.  What I want to do is create a third sub folder called "Artwork".  This way it won't try and "play" the image.  I could past the "Artwork" folder manually into every single folder, but if there was a way to copy said folder into ever folder in the artist folder, that would be great.  

I did some searching, and it looks like there is a way to do it in the terminal, but it confused me, and seems like a lot more work than just using Nautilus.

If someone can help me with this you're going to get a serious e-high 5. :P

Check into Puddletag - it is in my sig line

It is a great tagging app, but also, like you I had some serious needs in organizing my music.

I went to the puddletag forums and the developer was very very helpful in showing me what was needed and how to do it

Of course you could go to the forum first and ask if what you need is possible, but I believe it will be..

[_[COLOR="Blue"]Puddletag Forum[/COLOR]_]("https://sourceforge.net/apps/phpbb/puddletag/")

I have not used another app for tagging since discovering Puddle

---

### Post by giddyup306 on 2011-03-26
> **hakermania said:**
> I am a bit experienced with such problems and terminal too, but, to be honest, I didn't get what you wanna do....
In simple english you want to...? (for the solution we don't care so much for the purpose :D, but make clear what you wanna do (e.g. copy each file from all subfolders in a main subfolder named Artwork?))

Sorry if it was clear and I was the one who didn't get it


Sorry about the confusion.  I'll use Slayer as an example since they are my favourite band (April will be the 5th time seeing them live :guitar:).  So in Music > Slayer I have more than a dozen album folders.  I want to put an exact copy of a new folder "Artwork" in every single folder, then move the artwork manually into said folder.  I then want to repeat this process over and over with every other artist.  You know how you can delete or move multiple items at one time?  Kind of along the same lines, but there is no option to paste into multiple folders.  See I've been collecting music for almost 20 years, and my music collection is megalithic.

---

### Post by giddyup306 on 2011-03-26
> **VastOne said:**
> Check into Puddletag - it is in my sig line

It is a great tagging app, but also, like you I had some serious needs in organizing my music.

I went to the puddletag forums and the developer was very very helpful in showing me what was needed and how to do it

Of course you could go to the forum first and ask if what you need is possible, but I believe it will be..

[_[COLOR=Blue]Puddletag Forum[/COLOR]_]("https://sourceforge.net/apps/phpbb/puddletag/")

I have not used another app for tagging since discovering Puddle

All the tracks are tagged.  I just want to move all the artwork into a separate folder so my CD player doesn't try and think they're a video.

---

### Post by VastOne on 2011-03-26
> **giddyup306 said:**
> All the tracks are tagged.  I just want to move all the artwork into a separate folder so my CD player doesn't try and think they're a video.

I understand that... The point is Puddletag is way more than a tag application

Think of it more as a complete music management application

---

### Post by conneco on 2011-03-26
you want to look at shell scripting theres load of tutorials theres loads on line, id help you with one but even after the second time of you explaining it I DONT GET IT :confused:

---

### Post by giddyup306 on 2011-03-26
> **conneco said:**
> you want to look at shell scripting theres load of tutorials theres loads on line, id help you with one but even after the second time of you explaining it I DONT GET IT :confused:
Okay I'll try again.  I'll use a specific example.  Let's say I want to listen to the album Reign In Blood.  When I hook up my drive to the CD player in my car I navigate From Music > Slayer > Reign In Blood.  The Reign In Blood folder contains 12 mp3's, and 2 .jpg's.  The CD player then puts all this in the music playlist. Sometimes it will open the jpg first, and try and "play" it thinking it is a video. Then the CD player locks up and freezes on the image rather than playing my music.  To get past this I want to create a folder named "Artwork" inside the folder "Reign In Blood", and place the two jpgs in there.  That way it won't try and play them unless I click on that folder itself.  But I don't want to do that in just that folder.  I want to do it in every folder that is in the folder Slayer.  I also want to do it in every folder that has an artist's name.  So, basically, I'd like to highlight all folders in the artist folder and past the same empty file named "artwork"  into every single one rather than right clicking and click on "paste into folder".  I'd like to past into *all *folders.  I have probably hundreds of different artists in the music folder, so this would save a lot of time.  Then I would go back into each album folder and move the .jpg into there (or if there's an easier way to do that as well).

---

### Post by giddyup306 on 2011-03-26
In other words, I want to do something like this (but this is windows).

[http://www.theutilityfactory.com/summaries/distribute-files-and-folders.htm](http://www.theutilityfactory.com/summaries/distribute-files-and-folders.htm)

---

### Post by hakermania on 2011-03-26
Oh, now it is clear, move, in each single folder, the *.jpg to a new folder, named Artwork....
Hmmm....ll
That will do the job. (In the example, /home/alex/a is the top directory of my hypothetical music, also, please continue the a/*/*/* after the top directory, for as many as subfolders exist.... (e.g. if exist a/b/c/d/e/f/g/music_and_jpgs_here the it should be a/*/*/*/*/*/*/* at least... :) )
```

for i in /home/alex/a/*/*; do if [ X"$(echo "$i" | grep .jpg)" != X"" ]; then mkdir -p "$(dirname "$i")"/Artwork;mv "$i" "$(dirname "$i")"/Artwork; fi; done
```tested, but I would suggest you to do a backup, who knows....:[http://uppix.net/a/c/a/f5e93e036bcb61ea9f6f8f5b0edf1.png](http://uppix.net/a/c/a/f5e93e036bcb61ea9f6f8f5b0edf1.png)

---

### Post by giddyup306 on 2011-03-26
> **hakermania said:**
> Oh, now it is clear, move, in each single folder, the *.jpg to a new folder, named Artwork....
Hmmm....ll
That will do the job. (In the example, /home/alex/a is the top directory of my hypothetical music, also, please continue the a/*/*/* after the top directory, for as many as subfolders exist.... (e.g. if exist a/b/c/d/e/f/g/music_and_jpgs_here the it should be a/*/*/*/*/*/*/* at least... :) )
```

for i in /home/alex/a/*/*; do if [ X"$(echo "$i" | grep .jpg)" != X"" ]; then mkdir -p "$(dirname "$i")"/Artwork;mv "$i" "$(dirname "$i")"/Artwork; fi; done
```tested, but I would suggest you to do a backup, who knows....:[http://uppix.net/a/c/a/f5e93e036bcb61ea9f6f8f5b0edf1.png](http://uppix.net/a/c/a/f5e93e036bcb61ea9f6f8f5b0edf1.png)


Thanks!  :D  It says it has about 3 1/2 hours left till it's done backing up.  I'll let you know how it turns out.  I got half way through the B's before I gave up doing it manually.  The program that I linked I did try, but it's not nearly as handy as I thought it would be (it has a free trial).

---

### Post by conneco on 2011-03-27
Looks right to me! nice work, but as hakermain says test it first!, i once wrote a script to clear out all old backups from our client backup server set it going live... lets just say no one was happy....

---

### Post by hakermania on 2011-03-27
> **conneco said:**
> Looks right to me! nice work, but as hakermain says test it first!, i once wrote a script to clear out all old backups from our client backup server set it going live... lets just say no one was happy....

I'm going on a trip this night, and I would like to now how the process went....
I only hope that the asker delays from posting here not because his PC crashed down because of my script haha:roll:

---

### Post by giddyup306 on 2011-03-27
It worked perfect!  Thank you!!!  This is one of the coolest things that I have seen in Linux yet!  

Would you mind if I did a tutorial on YouTube on it?  Of course, I'll give credit where it is do, and won't act like I wrote the script.  

If anyone is curious, it made 3,141 new folders, and took maybe 30 seconds.  

The only thing that was undesired was in the few folders that I had already created a folder named "Artwork".  So now I have Music > Artist > Album > Artwork > Artwork.  But really it's not an issue.  I just needed to move the files so it doesn't lock up my CD player.  

The left is the drive that I tested on.  The middle is the backup drive, and the right is the results after I ran the code.

---

### Post by hakermania on 2011-04-02
Oh cool, last night I returned from the school trip in Belgium (what a beer!), and I'm glad to know that everything worked (almost) perfect :D
If you liked so much this solution, then you should definitely learn some unix scripting, it's not so hard, after all :) You'll have the opportunity to do much more interesting things with it than this :)

I'm waiting for the tutorial xD

---

