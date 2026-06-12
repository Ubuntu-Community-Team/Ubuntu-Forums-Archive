---
title: "Import album art into Banshee"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by nifty542 on 2011-06-06
Hi, all
I have imported "Continuum", by John Mayer. Unfortunately, Banshee doesn't fetch track information.
I realise it's not important, really, but I guess I am picky. I can't find a way to import the album art. I have saved the art in Gimp as a jpeg, but can't find a way to put it into Banshee.
Can anyone help, please?
By the way, love Lubuntu on my ageing computer!

Thanks, in anticipation
Nifty

---

### Post by coffeecat on 2011-06-06
What format are the music files? If mp3 and  you've saved the album art as a jpeg you could use EasyTag (it's in the repos) to add the jpeg to the track tag metadata for each mp3. Banshee will then see it.

---

### Post by nifty542 on 2011-06-06
Hi
Many thanks for the reply.
I have simply right clicked on the cd in Banshee, and clicked on import. So, I guess, the format id Ogg vorbis?
Anyway, I'll have a look. Thank you
Regards
Nifty

---

### Post by coffeecat on 2011-06-06
You'll be fine with ogg files with Easytag. I've just checked. :)

---

### Post by AlphaLexman on 2011-06-06
**MOST**, but maybe not all, Linux audio players will automatically look for a file named '**cover.jpg**' in the same directory as the audio files and assume it is the album art for the music in that directory.

---

### Post by nifty542 on 2011-06-07
Hi
Many thanks for the replies.
I have tried both these methods, but can't seem to get the desired result.
When I browse to the cover art using Easy Tag, the file is greyed out.
If I use "cover.jpeg" does it need to be within the folder for the music, or the folder which names the artist?
Thanks, in advance

---

### Post by nothingspecial on 2011-06-07
> **nifty542 said:**
> 
If I use "cover.jpeg" does it need to be within the folder for the music, or the folder which names the artist?
Thanks, in advance

It needs to be in the album folder, for example

```
/music/flac/Pink Floyd/The Dark Side of the Moon$ ls
01 - Speak to Me - Breathe.flac  04 - The Great Gig in the Sky.flac  07 - Any Colour You Like.flac [COLOR="Red"] cover.jpg[/COLOR]
02 - On the Run.flac             05 - Money.flac                     08 - Brain Damage.flac
03 - Time.flac                   06 - Us and Them.flac               09 - Eclipse.flac
```

---

### Post by AlphaLexman on 2011-06-07
The cover.jpg needs to be in the same directory as the mp3's or ogg's.

Here is an example:
```
[alphalexman@ubuntu:~/Music] ls -1 Radiohead/1995.The_Bends/

01.Planet_Telex.192.mp3
02.The_Bends.192.mp3
03.High_and_Dry.192.mp3
04.Fake_Plastic_Trees.192.mp3
05.Bones.192.mp3
06.Nice_Dream.192.mp3
07.Just.192.mp3
08.My_Iron_Lung.192.mp3
09.Bullet_Proof_I_Wish_I_Was.192.mp3
10.Black_Star.192.mp3
11.Sulk.192.mp3
12.Street_Spirit_Fade_Out.192.mp3
[COLOR="Red"]cover.jpg[/COLOR]


```

EDIT: nothingspecial beat me. Dude, why do you have spaces in your filenames ;)

---

### Post by nifty542 on 2011-06-07
Hi, all
Thanks for the replies. OK, I have tried that and it still doesn't work for me! I guess I must be doing something wrong, but don't know what.
I'll keep trying- would it make and difference if I imported the cd again, with the album art already there?
Regards
Nifty

---

### Post by nothingspecial on 2011-06-07
> **AlphaLexman said:**
> 

EDIT: nothingspecial beat me. Dude, why do you have spaces in your filenames ;)

Because I know how to quote a variable ;)

---

### Post by coffeecat on 2011-06-07
> **nifty542 said:**
> When I browse to the cover art using Easy Tag, the file is greyed out.

I'm not sure I follow that. Don't browse to the folder where the album art is. Use easytag to open the folder where your album(s) is/are. Then in the left pane, click on the folder for just one album - you'll see all the tracks listed in the middle pane. The right pane is where you edit the tags. Open the Pictures tab and simply drag and drop your album cover jpeg in. Repeat for each track. Now select all in the middle pane and click on the drive icon (save files) in the toolbar.

---

### Post by nifty542 on 2011-06-07
Hi, all
Well, thanks for the replies. It seems I was wrong!
Once I imported the artwork, nothing happened. But, when I restarted, all was ok.
Thank you, all. 
Regards
Nifty

---

