---
title: "Joining MP3 Tracks into a Single MP3"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by SillySod on 2009-03-25
Hello - can anyone suggest a way I can join several tracks from a CD which I have extracted as MP3 files into a single MP3 file?

I used to be able to do this on Windows Movie Maker by selecting them all and dragging them in.

I can't seem to find a way to do this now.  I tried Audacity, but it just loaded all the files underneath each other instead of putting them one after another in the time line.

Many thanks.

---

### Post by ashwat on 2009-03-25
In Audacity Import file1. Import file 2. Cut Track of file 2. Place cursor at end of track1. Paste track 2. Repeat process for all songs.

---

### Post by MrWES on 2009-03-25
> **SillySod said:**
> Hello - can anyone suggest a way I can join several tracks from a CD which I have extracted as MP3 files into a single MP3 file?

I used to be able to do this on Windows Movie Maker by selecting them all and dragging them in.

I can't seem to find a way to do this now.  I tried Audacity, but it just loaded all the files underneath each other instead of putting them one after another in the time line.

Many thanks.

This the quickest way!!!

Open a terminal Applications | Accessories | Terminal
and cd into the directory where your mp3 files are. type this command:

```
cat *.mp3 > joined.mp3
```

That will join all your mp3's in that directory into one mp3 file called joined.mp3.

Bill

---

### Post by starcannon on 2009-03-25
+1 for Audacity, you can splice seamlessly, or fade in out, etc... etc... and with a nice GUI.

GL

---

### Post by linuxguymarshall on 2009-03-25
> **MrWES said:**
> This the quickest way!!!

Open a terminal Applications | Accessories | Terminal
and cd into the directory where your mp3 files are. type this command:

```
cat *.mp3 > joined.mp3
```That will join all your mp3's in that directory into one mp3 file called joined.mp3.

Bill

I am a true Audacity fan but if this works then I may be doing this from now on.

---

### Post by MrWES on 2009-03-25
> **linuxguymarshall said:**
> I am a true Audacity fan but if this works then I may be doing this from now on.

Believe me, it works :)

Bill

---

### Post by SillySod on 2009-03-26
Thanks for the suggestions, I will try the terminal idea.  Ideally I want something which will join the tracks together without any gaps, even a fraction of a second, because I am working with audio books rather than music CDs, so if there a gap there is a jump in the background music which doesn't happen when playing from CD.

I worked out that you could import files into Audacity individually, one after another, but I this is a bit time consuming given that there are sometimes 20 or 30 tracks per finished file.

---

### Post by logos34 on 2009-03-26
> **SillySod said:**
> I will try the terminal idea.  Ideally I want something which will join the tracks together without any gaps, even a fraction of a second, because I am working with audio books rather than music CDs, so if there a gap there is a jump in the background music which doesn't happen when playing from CD.

If cat leaves any gaps, there is **mp3wrap** which I believe will do gapless (I think)
> 
Description: Utility for MP3 wrapping (rolling multiple MP3s into one)
 Command-line utility that wraps multiple MP3 files into a a single, playable
 MP3, without losing filenames or ID3 information, and without reencoding. Also
 supports archiving non-audio data such as playlists, info files, and cover
 images inside the MP3. These files can be unpacked later (using mp3splt, e.g.);
 ordinary MP3 decoders can play the entire audio stream as one long track.
 .
 This is a free, independent alternative to AlbumWrap:
 [http://www.infamus.com/albumwrap/](http://www.infamus.com/albumwrap/)
 .
 Homepage: [http://mp3wrap.sourceforge.net/](http://mp3wrap.sourceforge.net/)
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

apt-cache show mp3wrap

sudo apt-get install mp3wrap

man mp3wrap


EDIT: actually I'm not even sure mp3wrap can do gapless.  Not having much success myself right now with it...

---

### Post by logos34 on 2009-03-26
Well, that's interesting...I just tried cat and mp3wrap, and neither does gapless (I used tracks from live albums for testing)...The only way I can get gapless is to rip the cd again using lame with **--nogap** option. The downside is that it screws up the track length/time info header so mp3 players can't read it correctly, and you can't fast forward within each track (it effectively creates a single long file for ff and rr purposes).

---

### Post by mikechant on 2009-03-27
I wouldn't have thought using 'cat' was a good idea. Don't you end up with id3 tags scattered through the file? I expect properly written decoders would deal with this by discarding the invalid information, but a poorly written decoder (maybe on a cheap mp3 player) might crash or produce a horrible noise when it hit one.
Also the correctly placed id3 tag at the start of the track would contain invalid data (only relating to the first part of the combined track).

---

### Post by kanikilu on 2009-03-27
It's been a while since I've used Audacity, but couldn't you do something like record like 3 seconds of "nothing" and splice that in between each track to create a gap?

---

### Post by logos34 on 2009-03-27
> **mikechant said:**
> I wouldn't have thought using 'cat' was a good idea. Don't you end up with id3 tags scattered through the file? I expect properly written decoders would deal with this by discarding the invalid information, but a poorly written decoder (maybe on a cheap mp3 player) might crash or produce a horrible noise when it hit one.
Also the correctly placed id3 tag at the start of the track would contain invalid data (only relating to the first part of the combined track).

This method fixes the tag info and potential playback problem:

[http://lyncd.com/2009/02/how-to-merge-mp3-files/](http://lyncd.com/2009/02/how-to-merge-mp3-files/)

But that doesn't solve the gap problem...unless that is sillysod wants to settle for less.  Which I think is necessary in this case, because other than the time-consuming method of Audacity there doesn't seem to be a way to get gapless short of re-ripping with nogap option

---

### Post by MrWES on 2009-03-27
Been using cat *.mp3 > joined.mp3 for a long time, never had one play back issue -- and the gapless wasn't an issue for me.

Bill

---

### Post by freak42 on 2009-03-27
I am pretty sure that 'cat'ing mp3 files will not produces standard compliant mp3 files, this doesn't mean they work perferct in some apps and okay in others, but I'm sure it will cause some problems in some players at least.

---

### Post by RH9R on 2009-03-27
I have successfully joined 6 files into one using audacity but find a strange and undesirable result - the resulting file is almost 50% larger than the size of the total of the individual files before joining.
 
I joined by opening file one, open file 2, cut, past, export.
 
Anyone know how to avoid the bloat?
Many Thanks.

---

### Post by starcannon on 2009-03-27
> **RH9R said:**
> I have successfully joined 6 files into one using audacity but find a strange and undesirable result - the resulting file is almost 50% larger than the size of the total of the individual files before joining.
 
I joined by opening file one, open file 2, cut, past, export.
 
Anyone know how to avoid the bloat?
Many Thanks.

1: Click File
2: Click Export
3: Choose MP3 Files
4: Click Options
5: Set Quality to a lower bitrate, default is 128kbps
6: Click OK
7: Click Save

My guess is the files were at a lower bitrate or of various bitrates, and then were saved at 128 which may have caused one or more of the pieces to be decompressed and made your file a bit larger; just a guess though.

GL and have fun.

---

### Post by RH9R on 2009-03-28
Starcannon Thank You! I appreciate your kind help. I'll bet that's it!

---

### Post by produnis on 2009-08-14
If one search for "merge" and "mp3" within the repository, one find "mpgtx" and "mp3wrapper". But using these programs will leave a file like "joined.mp3" which has a wrong file header. To way to solve this comes with ffmpeg and *libid3-3.8.3-dev*

Here is the way how I merge mp3-files using Ubuntu ([thx to lyncd]("http://lyncd.com/2009/02/how-to-merge-mp3-files/")):

1) Open a terminal

2) If you have not done that yet, install ffmpeg and [I]libid3-3.8.3-dev
[/I][php]sudo apt-get install ffmpeg libid3-3.8.3-dev[/php]3) cd /to/folder/with/mp3files

4) Type in:
[php]cat file1.mp3 file2.mp file3.mp3 > joined.mp3 [/php]This will create a "joined.mp3" with broken file-header (just like mp3wrapper and mpgtx would do)

5) Therefore, type in:
[php]ffmpeg -i joined.mp3 -acodec copy output.mp3[/php]This will "repaire" the broken file and save the "new good one" to output.mp3

6) Remove joined.mp3 (as we don't need it any longer)
[php]rm joined.mp3[/php]7) You might want to transfer the ID3-Tag of e.g. file1.mp3 to output.mp3. You can do that with:
[php]id3cp file1.mp3 output.mp3[/php]Now output.mp3 has the same ID3-tags as file1.mp3

8) You are done. output.mp3 is ready for you music library

9) If you would like to have a graphical zenity-script, create a file named "mp3join.sh" and give it the content you find in the[ German Ubuntuusers-Wiki]("http://wiki.ubuntuusers.de/Skripte/MP3_Zusammenf%C3%BChren#zenity-Script"). Make it executable:
[php]chmod a+x mp3join.sh[/php]and start it by typing in:
[php]./mp3join.sh[/php]The script will ask you for the files to join and save the merged file as "**mp3Join-Ziel.mp3**" at your desktop.

HAVE FUN!

---

### Post by MrWES on 2009-08-14
Dast ist sehr gut script -- in German :)

---

### Post by andrew.46 on 2009-08-15
Hi,

I was going to champion my favourite piece of audio software SoX for appending mp3s:

```
sox -S file1.mp3 file2.mp3 file3.mp3 new_joined_file.mp3
```

which works beautifully when I noticed that bitrate of the new output file is always set to 128k and for the life of me I cannot see an option to match the bitrate of the input files. Does anybody have a solution for this one?

Andrew

---

### Post by Don1500 on 2009-08-15
> **SillySod said:**
> Hello - can anyone suggest a way I can join several tracks from a CD which I have extracted as MP3 files into a single MP3 file?

OK, for the life of me I can't think of one good reason to do this. You end up with a file that might as well be a Vinyl record. You hear the same songs in the same order over and over. I record from the i-net radio and then split the recording up, just the opposite of your job.:guitar:

---

### Post by egalvan on 2009-08-15
> **Don1500 said:**
> OK, for the life of me** I can't think of one good reason to do this**.
 You end up with a file that might as well be a Vinyl record.
 You hear the same songs in the same order over and over.
 I record from the i-net radio and then split the recording up, just the opposite of your job.:guitar:

Well, it seems the OP has one good reason... :P

> **SillySod said:**
> ** because I am working with audio books rather than music CDs,**
 so if there a gap there is a jump in the background music which doesn't happen when playing from CD.

---

### Post by MrWES on 2009-08-15
> **andrew.46 said:**
> Hi,

I was going to champion my favourite piece of audio software SoX for appending mp3s:

```
sox -S file1.mp3 file2.mp3 file3.mp3 new_joined_file.mp3
```

which works beautifully when I noticed that bitrate of the new output file is always set to 128k and for the life of me I cannot see an option to match the bitrate of the input files. Does anybody have a solution for this one?

Andrew


I thought the default version of sox was not compiled with mp3 support, at least that's what I'm seeing on my box.

Bill

---

### Post by andrew.46 on 2009-08-15
Hi Bill,

Good to see you again!

> **MrWES said:**
> I thought the default version of sox was not compiled with mp3 support, at least that's what I'm seeing on my box.

I believe you have caught me out there using my own compiled copy of sox, for which my apologies. Looks like the Jaunty version even when it is installed with the sox-libfmt-all package can still only *read* mp3s but not *encode* to mp3. A lamentable omission IMHO but I am aware of the constraints placed on devs by patent restrictions :(.

Andrew

---

### Post by MrWES on 2009-08-15
> **andrew.46 said:**
> Hi Bill,

Good to see you again!



I believe you have caught me out there using my own compiled copy of sox, for which my apologies. Looks like the Jaunty version even when it is installed with the sox-libfmt-all package can still only *read* mp3s but not *encode* to mp3. A lamentable omission IMHO but I am aware of the constraints placed on devs by patent restrictions :(.

Andrew

Has anyone compiled it with lame output support in a .deb package?

Bill

P.S. It's impossible to catch you at anything! -- I always make it a point to read your worthy input :)

---

### Post by Bartender on 2009-08-15
> **Don1500 said:**
> OK, for the life of me I can't think of one good reason to do this. 

I've got one for you.  The typical non-mp3 audiobook has between 30 and 99 separate tracks, some of them lasting less than a minute.  I just started ripping audiobooks for my wife's Fuze.  When she's dealing with the Fuze's little screen and navigation wheel, one 70-minute track is much more convenient than 90 one-minute tracks.

---

### Post by andrew.46 on 2009-08-15
Hi Bill,

> **MrWES said:**
> Has anyone compiled it with lame output support in a .deb package?

I am not aware of any such deb file or PPA unfortunately. Hmmmm..... I sense yet another small guide that might be helpful... **Edit**: I see that this work has already been done:

HowTo: Compiling SoX with read/write MP3 support in Ubuntu
[http://a0u.xanga.com/700438974/howto-sox-installation/](http://a0u.xanga.com/700438974/howto-sox-installation/)

> It's impossible to catch you at anything! -- I always make it a point to read your worthy input :)

Even when I am a little confused as to which distro, partition, virtual machine or software version I am using? :-).

Andrew

---

### Post by MrWES on 2009-08-15
Perfect, thanks for the link.

Just keep posting the good stuff!

Thanks again,

Bill

---

