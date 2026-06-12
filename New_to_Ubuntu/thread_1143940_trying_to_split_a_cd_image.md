---
title: "trying to split a cd image"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by camaron1 on 2009-04-30
I've been trying to find out how to to split an audio cd image (a single track) into its original tracks by using the CUE file. In this forums I was directed [to this blog]("http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/") which uses some comand-line tools (cuebreakpoints, etc). I've not been able to do anything with this, probably because I just don't know how to use the command line (I've probably introduced some sintaxis mistake, but couldn't tell).

My questions are;

-Is there a GUI for this programs or any other programs with GUI a could use?
-Is anyone out there that could explain me how to use [I]cuebreakpoints
[/I] in the terminal?
-(worst case scenario): anyone knows of free software to do this in Windows?

Thanks for your help

---

### Post by camaron1 on 2009-04-30
I know it isn't very exciting but maybe someone knows something....?

---

### Post by logos34 on 2009-04-30
> **camaron1 said:**
> 

-Is there a GUI for this programs or any other programs with GUI a could use?


I think I just responded to your previous post [edit: wrong--I was thinking of [this one]("http://ubuntuforums.org/showthread.php?t=1111859&highlight=mp3"), by another poster], but forgot to mention k3b, which can read .cue sheets. (but since it's a kde app you'll need to install some qtlibs along with it.

You might also try foobar2000 (on Wine).  great app

Are you sure it's not a problem with the cue sheet itself?  Have you looked for the cd [here]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fregeert.nl%2Fcuesheet%2F&ei=4Nz5Sfe-AZnKMs-R3K0E&usg=AFQjCNFyuuPG2wE9aE8xBIIs-MTHvfsc3g")?

---

### Post by Niniel on 2009-04-30
Burn and rip - you would have been done by now. :)

---

### Post by camaron1 on 2009-04-30
> **logos34 said:**
> I think I just responded to your previous post, but forgot to mention k3b, which can read .cue sheets. (but since it's a kde app you'll need to install some qtlibs along with it.

You might also try foobar2000 (on Wine).  great app

Are you sure it's not a problem with the cue sheet itself?  Have you looked for the cd [here]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fregeert.nl%2Fcuesheet%2F&ei=4Nz5Sfe-AZnKMs-R3K0E&usg=AFQjCNFyuuPG2wE9aE8xBIIs-MTHvfsc3g")?

I just downloaded that, problem is: it seems that you need to burn the result to a Cd but i'm trying to do everything on the hard disk.

---

### Post by NightwishFan on 2009-04-30
posted by error

---

### Post by camaron1 on 2009-04-30
> **NightwishFan said:**
> nvm

I don't know what nvm is, it isn't in the repositories and a quick google search only show something for changing the name of the files, not sure if you are talking about that.

I discovered in Softpedia a programs called GCue2tracks which in the surface is just exactly what i'm looking for but for some reason doesn't seem to work. It just doesn't do anything. I wonder if anyone has used that program with any result

---

### Post by NightwishFan on 2009-04-30
My apologies!! I was distracted and responding poorly to this thread. So I did a quick "nevermind" and was going to clarify that I had nothing to offer and was sorry I posted! It was put quite out of my mind when I came back, and I never edited further.


:(:(

---

### Post by camaron1 on 2009-04-30
> **NightwishFan said:**
> My apologies!! I was distracted and responding poorly to this thread. So I did a quick "nevermind" and was going to clarify that I had nothing to offer and was sorry I posted! It was put quite out of my mind when I came back, and I never edited further.


:(:(

Never mind mate

---

### Post by logos34 on 2009-04-30
> **camaron1 said:**
> I just downloaded that, problem is: it seems that you need to burn the result to a Cd but i'm trying to do everything on the hard disk.

no you don't have to--just grab the .cue file, click 'convert' arrow and choose the format (same in this case) and output dir

but, again, maybe dl another cue sheet for that cd at the link I posted (if listed)

---

### Post by logos34 on 2009-04-30
> **camaron1 said:**
> GCue2tracks which in the surface is just exactly what i'm looking for but for some reason doesn't seem to work. It just doesn't do anything. I wonder if anyone has used that program with any result


you tried it using the example as a guide?

cue2tracks -h

-btw, I've used cuebreakpoints and shntools successfully in the past, following the very same link you posted (mainly to break up .ape cd images I got through torrents)

---

### Post by logos34 on 2009-04-30
I just tried out mp3splt...works fine for me:

> user@ubuntu:~/music2/1-new/Various-Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski$ [COLOR="Red"]mp3splt -c Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.cue Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.mp3 [/COLOR]
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
Warning: found Xing or Info header, mp3 may be VBR. Switching to Frame mode...
MPEG 1 Layer 3 - 44100 Hz - Joint Stereo - FRAME MODE - Total time: 71m.33s
Reading informations from Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.cue...
Tracks: 16 
Artist: Various
Album: Gloria Cheng Piano Music of S

   6 % -> Various - 01 - Stucky  Four Album Leaves Contemplativo, tempo rubato.mp3... OK
  12 % -> Various - 02 - Stucky  Four Album Leaves Meccanico.mp3... OK
  18 % -> Various - 03 - Stucky  Four Album Leaves Sereno, luminoso.mp3... OK
  25 % -> Various - 04 - Stucky  Four Album Leaves Presto giocoso.mp3... OK
  31 % -> Various - 05 - Lutoslawski  Sonata for Piano Allegro.mp3... OK
  37 % -> Various - 06 - Lutoslawski  Sonata for Piano Adagio ma non troppo.mp3... OK
  43 % -> Various - 07 - Lutoslawski  Sonata for Piano Andante - Allegretto.mp3... OK
  50 % -> Various - 08 - Salonen  Yta II.mp3... OK
  56 % -> Various - 09 - Salonen  Three Preludes Libellula Meccanica.mp3... OK
  62 % -> Various - 10 - Salonen  Three Preludes Chorale.mp3... OK
  68 % -> Various - 11 - Salonen  Three Preludes Invenzione.mp3... OK
  75 % -> Various - 12 - Salonen  Dichotomie Mecanisme.mp3... OK
  81 % -> Various - 13 - Salonen  Dichotomie Organisme.mp3... OK
  87 % -> Various - 14 - Stucky  Three Little Variations for David Giocoso.mp3... OK
  93 % -> Various - 15 - Stucky  Three Little Variations for David Sognando.mp3... OK
 100 % -> Various - 16 - Stucky  Three Little Variations for David Molto vivo.mp3... OK (EOF)

All files successfully splitted! Processed 164359 frames - Sync errors: 0

+-----------------------------------------------------------------------------+
|NOTE: When you use cddb/cue, splitted files might be not very precise due to:|
|1) Who extracts CD tracks might use "Remove silence" option. This means that |
|   the large mp3 file is shorter than CD Total time. Never use this option.  |
|2) Who burns CD might add extra pause seconds between tracks.  Never do it.  |
|3) Encoders might add some padding frames so  that  file is longer than CD.  |
|4) There are several entries of the same cd on CDDB, find the best for yours.|
|   Usually you can find the correct splitpoints for your mp3, so good luck!  |
+-----------------------------------------------------------------------------+
| TRY TO ADJUST SPLITS POINT WITH -a OPTION. Read man page for more details!  |
+-----------------------------------------------------------------------------+


---

### Post by camaron1 on 2009-04-30
> **logos34 said:**
> no you don't have to--just grab the .cue file, click 'convert' arrow and choose the format (same in this case) and output dir

but, again, maybe dl another cue sheet for that cd at the link I posted (if listed)

Thanks Logos34 for the interest. 

I honestly think I must be missing something. How do you "just grab the  .cue file and click convert" with K3b. I've been fiddling with it and just don't see how. I'd very much appreciate if you can tell me exactly how you do that. 

On the other -as weird as it might be- I don't use MP3 files. They seem to be better supported and everything but I only use lossless formats. Please, get back to me (or anyone else) as I'm sure there must be a way (by the waym, I know you can i use Audacity manually but really is a lot of hassle.

---

### Post by logos34 on 2009-04-30
here, try it this way:

in your file browser right click on the .cue file>open with>k3b

in k3b:

>Project>Convert tracks

if option not there, maybe you're missing a library or plugin

sudo apt-get install libk3b2-extracodecs sox

The only drawback is that I think it will split and re-encode to mp3 (the general rule is to avoid lossy-to-lossy conversion, but the diff probably won't be noticeable. Besides, nothing else seems to work!)

mp3splt, if only you could get it to work, is the ideal way (splits without decoding/encoding)

---

### Post by camaron1 on 2009-04-30
K3b doesn't give me the option to convert tracks even after installing the package you indicated, I don't really know what is going on. Just for the record i'm using version 3.5.10. On the other hand as I said I don't use lossy formats, not for classical music anyway, so an output in mp3 would't be much use.

I do belive cuebreakpoints is probably the answer. I wonder if you have some APE or FLAC image file that you could have a go to with cuebreakpoits, to see if it works for you. If it does maybe you could post what you typed in the terminal so i can make sense of it.

---

### Post by logos34 on 2009-04-30
3.5.1o here too...hmm, maybe k3b needs ffmpeg for convert, that's about all that's left :/ dunno

anyway, try this way:
> 
shnsplit -o wav -f sample.cue sample.wav

here's what I end up with (unfortunately it doesn't print out track names):

> user@ubuntu:~/music2/1-new/Various-Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski$ [COLOR="Red"]shnsplit -o wav -f Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.cue Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav [/COLOR]
shnsplit: warning: discarding initial zero-valued split point
shnsplit: warning: file 16 will not be cut on a sector boundary
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track01.wav] (2:56.25) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track02.wav] (1:12.72) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track03.wav] (2:05.18) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track04.wav] (1:38.61) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track05.wav] (10:31.34) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track06.wav] (7:40.37) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track07.wav] (8:30.52) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track08.wav] (6:54.54) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track09.wav] (3:29.70) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track10.wav] (3:03.30) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track11.wav] (2:34.66) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track12.wav] (9:23.04) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track13.wav] (8:00.00) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track14.wav] (0:55.49) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track15.wav] (1:52.04) : 100% OK
Splitting [Gloria_Cheng_Piano_Music_of_Salonen,_Stucky,_Lutoslawski.wav] (71:33.34) --> [split-track16.wav] (0:43.58) : 100% OK

lemme see if there's another way to get track titles

---

### Post by camaron1 on 2009-04-30
logos 34:

You are a star mate,it did work indeed, and even if it doesn't keep the track names is a huge step forward for me. I still need to see if it works the same way with compressed files (other wise I'll have to convert them to wav and back again).

I'll have a look at this tomorrow and let you know. I'll give this as sorted anyway.

Good effort. Thanks a lot

---

### Post by camaron1 on 2009-04-30
How on hearth you mark this as solved? I can't find it....

---

### Post by logos34 on 2009-04-30
can't mark threads 'solved' anymore...they removed that option (?)

I've never figured out the direct cuebreakpoints command--it converts the flac into individual wavs (??):

using this cue sheet:
[ATTACH]111887[/ATTACH]

I get:
> 
$ cuebreakpoints Ga_Ga_Ga_Ga_Ga.cue | shnsplit Ga_Ga_Ga_Ga_Ga.flac
bad character 'F'
bad character 'L'
bad character 'A'
bad character 'C'
4: syntax error
4: no file specified for track
7: no file specified for track
10: no file specified for track
13: no file specified for track
16: no file specified for track
19: no file specified for track
22: no file specified for track
25: no file specified for track
28: no file specified for track
31: no file specified for track
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track01.wav] (3:55.68) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track02.wav] (3:34.55) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track03.wav] (3:08.48) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track04.wav] (3:36.46) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track05.wav] (3:30.64) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track06.wav] (3:39.68) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track07.wav] (3:42.24) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track08.wav] (3:03.51) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track09.wav] (4:54.56) : 100% OK
Splitting [Ga_Ga_Ga_Ga_Ga.flac] (36:33.22) --> [split-track10.wav] (3:25.67) : 100% OK


why is it outputting wav?  hmm...

Here's a cheat sheet I compiled way back to help with ape to flac convert:

maybe with a few tweaks you can get it to work like you want
[ATTACH]111888[/ATTACH]

hope that helps

---

### Post by logos34 on 2009-05-01
no wonder it was complaining--typo in the .cue. 

format should be 

'FILE "sample.flac" [COLOR="Red"]WAVE[/COLOR]'

not

'FILE "sample.flac" FLAC'

duh

So here's an .ape image split with the cuebreakpoints command (same result - no titles):

using this .cue sheet:

> PERFORMER "Debussy - CO - Boulez"
TITLE "Debussy - La Mer, Nocturnes"
**FILE "CDimage ape normal.ape" WAVE**
  TRACK 01 AUDIO
    TITLE "Debussy - Nocturnes - I. Nuages"
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "II. Fetes"
    INDEX 01 06:15:00
TRACK 03 AUDIO
    TITLE "III. Sirenes [with Cleveland Orchestra Chorus]"
    INDEX 01 12:46:00
...


> user@ubuntu:~$ cd Debussy\ -\ La\ Mer\ -\ Nocturnes\ -\ Boulez/
user@ubuntu:~/Debussy - La Mer - Nocturnes - Boulez$ ls
**CDimage ape normal.ape**  **CDimage ape normal (cue).cue**
user@ubuntu:~/Debussy - La Mer - Nocturnes - Boulez$ cuebreakpoints CDimage\ ape\ normal\ (cue).cue | shnsplit -o flac CDimage\ ape\ normal.ape 
bash: syntax error near unexpected token `('
user@ubuntu:~/Debussy - La Mer - Nocturnes - Boulez$ [COLOR="Red"]cuebreakpoints "CDimage ape normal (cue).cue" | shnsplit -o flac CDimage\ ape\ normal.ape [/COLOR]
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track01.flac] (6:15.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track02.flac] (6:31.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track03.flac] (9:47.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track04.flac] (8:42.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track05.flac] (16:06.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track06.flac] (8:47.15) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track07.flac] (7:08.68) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track08.flac] (7:40.56) : 100% OK



same for shnsplit command:

> $ shnsplit -o flac -f "CDimage ape normal (cue).cue" CDimage\ ape\ normal.ape
shnsplit: warning: discarding initial zero-valued split point
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track01.flac] (6:15.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track02.flac] (6:31.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track03.flac] (9:47.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track04.flac] (8:42.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track05.flac] (16:06.00) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track06.flac] (8:47.15) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track07.flac] (7:08.68) : 100% OK
Splitting [CDimage ape normal.ape] (70:57.64) --> [split-track08.flac] (7:40.56) : 100% OK

Happy splitting and/or converting!

---

### Post by jamesisin on 2009-11-19
I'm a little late to the party, but you might appreciate my post on doing just this:

[http://www.soundunreason.com/InkWell/?p=980](http://www.soundunreason.com/InkWell/?p=980)

---

### Post by camaron1 on 2009-12-22
> **jamesisin said:**
> I'm a little late to the party, but you might appreciate my post on doing just this:

[http://www.soundunreason.com/InkWell/?p=980](http://www.soundunreason.com/InkWell/?p=980)


Thanks for that (if again late..)

I have since discovered that **EAC** works fine under **wine** (aswell as ripping you can split ape files). **Medieval cuesplitter **works well under **wine** too and will split anything you throw at it (you always need the cue file obviously..)

---

### Post by jamesisin on 2009-12-22
Ah, yeah, I wrote an article on APE files as well:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

More or less the same.  Just an extra package.

I forgot to mention (in my posts) that EAC is repudiated to run under WINE without issues.  Excellent to note that you are seeing that true.

I suppose you ought to mark this thread as SOLVED.

---

### Post by camaron1 on 2009-12-23
> **jamesisin said:**
> Ah, yeah, I wrote an article on APE files as well:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

More or less the same.  Just an extra package.

I forgot to mention (in my posts) that EAC is repudiated to run under WINE without issues.  Excellent to note that you are seeing that true.

I suppose you ought to mark this thread as SOLVED.

Hi jamesisin, 

Very nice article, thanks for that.
A couple of things: the repository is not accepted by synaptic (not for Karmic anyway) and the link doesn't actually take me anywhere (maybe needs updating).
I've got a question: as things are now I can play and convert APE files (the last with **soundcoverter** but strangely no with **soundkonverter**) I suppose that means I've got the package installed?If not what extra functionality would it give?

Just for clarification: when you say **repudiated** do you mean **acknowledged**? (I'm not trying to by funny, English isn't my first language).

I'm marking the thread as solved
Thanks again

PD: When in the previous post I said you can split APE files with EAC I should've clarified: you first need to convert the file to WAV and then, in a text editor edit the cue file: where it says something like "name of file.ape" you make it "name of the file.wav" and save the change. You can then split the file with EAC and after convert it  to whatever (flac ideally...).

Regards

---

### Post by camaron1 on 2009-12-23
> the link doesn't actually take me anywhere

I do apologize, the link downloads the package
Regards

---

### Post by jamesisin on 2009-12-23
> **camaron1 said:**
> I've got a question: as things are now I can play and convert APE files (the last with **soundcoverter** but strangely no with **soundkonverter**) I suppose that means I've got the package installed?If not what extra functionality would it give?

Just for clarification: when you say **repudiated** do you mean **acknowledged**? (I'm not trying to by funny, English isn't my first language).

PD: When in the previous post I said you can split APE files with EAC I should've clarified: you first need to convert the file to WAV and then, in a text editor edit the cue file: where it says something like "name of file.ape" you make it "name of the file.wav" and save the change. You can then split the file with EAC and after convert it  to whatever (flac ideally...).

Regards


Yeah, I tried to come up with a very streamlined method for making the conversions.  I wanted it to be as non-hacky as possible.  Editing the cue file tends toward that hacky sort of solution.  Keep it simple for the users, basically.

If your machine can comprehend the ape files that seems to suggest you have the codec.  You can test this by one simple line of code:

```
which mac
```

If it shows a location, that's where the MAC (Monkey Audio Codec) is located.  If not, no.

In the case above, I understood by the reputation of EAC within the forum community that EAC was able to run under WINE&#8212;hence repudiated.  Acknowledged would be more like the makers of EAC admitting it would run under WINE (which they may or may not have ever done).

> **camaron1 said:**
> I do apologize, the link downloads the package
Regards


Glad to see you got that sorted out.

---

