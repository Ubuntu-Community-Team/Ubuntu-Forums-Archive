---
title: "subtitles won't work??"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by RotorRick on 2011-09-06
Ubuntu 10.04 LTS 

I'm trying to use the subtitles in VLC player, and I think I'm doing something wrong!

the video is an .avi

the subtitles folder contains a .rar 

the .rar contains a .idx file

First issue: did I screw up by unzipping the .rar file? And do I need to bother moving the file?

Second issue: when I point VLC player to the file in question, I go:

VLC > video > subtitles track > open file

and then I click on the .idx file. It doesn't seem to play the subtitles, and I'm not sure why. Intstead, it displays this:

>  p, li { white-space: pre-wrap; } [COLOR=#FF0000]VLC can't recognize the input's format:[/COLOR]
 [COLOR=#000000]The format of '/home/rick/Desktop/Link to 2011/TV/MOVIES MOVIES MOVIES MOVIES MOVIES/OSS.117.Lost.In.Rio.2009.DVDRip.XviD-VoMiT/Subs/vmt-oss117rio-xvid.idx' cannot be detected. Have a look at the log for details.[/COLOR]


So I looked at the VLC help page:
> **VLC doesn't display all subtitles**

 If VLC has autodetected your subtitles file, or if you opened it  manually, but VLC only diplays some subtitles from time to time, you  will need to change the subtitles file encoding.
  Go to *Preferences -> Input / Codecs -> Other codecs -> Subtitles*, and set *Subtitle text encoding* to the right one. 
 See this reference: [ISO Standard for various characters sets]("http://alis.isoc.org/codage/iso8859/jeuxiso.en.htm"). 
Problem is, mine doesn't show ANY subtitles at all. And I tried to muck about with the path mentioned, but nothing. I tried following their advice on changing the codecs, but that didn't seem to work, but maybe I missed something? Maybe what I need is a quick tutorial if there's any?

I'm looking for  English subtitles for a French show. I could sort of follow the French, but I'm out of practice and need the subtitles as a crutch these days! Maybe with more shows it'll come back to me! :D Also, I'd like to be able to do this for other languages too, the world produces all sorts of movies and tv that's worthwhile! ;) 

Thanks!

---

### Post by TeoBigusGeekus on 2011-09-06
The rar file contains raw subtitles from a dvd movie.
Unpack it - it should contain an idx and an sub file.

---

### Post by papibe on 2011-09-06
> **TeoBigusGeekus said:**
> The rar file contains raw subtitles from a dvd movie.
Unpack it - it should contain an idx and an sub file.
+1

If all files have the same filename and they are in the same directory, VLC will recognize them by default, e.g.:
```
movie.avi
movie.sub
movie.idx
movie.srt
```
Regards.

---

### Post by RotorRick on 2011-09-06
> **papibe said:**
> +1

If all files have the same filename and they are in the same directory, VLC will recognize them by default, e.g.:
```
movie.avi
movie.sub
movie.idx
movie.srt
```Regards.

I have .avi

I have -subs.sfv which I renamed to .sub

I have .idx

but there is no .srt...

Tried with the .avi, .sfv and .idx in the main folder, didn't seem to work...

:confused:

---

### Post by TeoBigusGeekus on 2011-09-06
Then try to create the srt file with avidemux.
Firstly, rename the file again so that it has its original extension (.subs.sfv)
Then, open avidemux, if you don't have it, install it
```
sudo apt-get install avidemux
```
Then go to Tools>OCR(VobSUb->Srt). Select your idx file and select an output srt file.
If the subtitles are correct (I think there should be a sub file), you will be directed to the OCR recognition stage: for every character (glyph) that avidemux shows you, you press the correct key (letter). After it's learnt enough to carry the conversion by itself, the srt file will be ready.

---

### Post by jtarin on 2011-09-06
Post a link to the subtitle file you downloaded.....or the movie name and I'll find a subtitle for you. Specify language. Subtitles are made with a specific copy of a movie and sometimes can be a little difficult to find one that syncs, so give the full name of the movie as you received it.

---

