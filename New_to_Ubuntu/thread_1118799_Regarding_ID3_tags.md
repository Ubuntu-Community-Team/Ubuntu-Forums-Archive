---
title: "Regarding ID3 tags"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by GepettoBR on 2009-04-07
I have a very extensive music collection stored on my computer. I use both Amarok and Rhythmbox to play back, organize and manage this collection, as well as for syncing my iPod. They both do a wonderful job, but seem to regard ID3 tags as read-only.

In either player, I can edit the track information for any given file (be it MP3, FLAC, AAC, OGG Vorbis, Monkey's Audio or even the odd WAV that I've yet to compress) without problems, but the other player will not recognize the change. I know that Amarok uses a SQL database to manage the colelction. Does it store metadata on that database as well instead of writing to the tags, and does Rhythmbox display a similar behavior? Or is the problem related to a cache of some sort that I need to empty?

Dealing with over 14000 songs is tiresome, but having to make every change twice whenever I find an error in a tag or want to add in, say, a missing album year, is just dumb. ID3v2 has been around for a long time, and this apparent lack of support from the most popular media players from GNOME and KDE seems very odd. I haven't tried other players like Exaile or Banshee, but this used to work fine under Windows, where changes I made with Winamp were picked up by every other media player immediately.

Thanks in advance for all replies.

Cheers,
Paulo

---

### Post by bluelamp999 on 2009-04-07
Hi,

I've noticed the same thing with most media players...

I use Audio Tag Tool ([http://pwp.netcabo.pt/paol/tagtool/](http://pwp.netcabo.pt/paol/tagtool/)).

This is a very handy little utility that does exactly what it say on the box and all tags are saved within the media file.

Worth a look...

Cheers

---

### Post by Therion on 2009-04-07
Search Synaptic for either **Cowbell**:

[http://more-cowbell.org/index.php/Main_Page](http://more-cowbell.org/index.php/Main_Page)


Or **Easytag** (my choice for tag-management):

[http://easytag.sourceforge.net/](http://easytag.sourceforge.net/)

---

### Post by GepettoBR on 2009-04-07
bluelamp999, thank you for the quick reply.

Using this tool might be a good workaround, but I'd really like to know what is causing Amarok and Rhythmbox to not do something they're advertised as doing. I mostly notice flaws in tags during playback, and being able to fix them with just a few clicks is a lot quicker than opening a second application and navigating to where the files are located.

EDIT: Therion, thanks for your suggestions as well. I've used Easytag before and didn't like it, but this Cowbell is news to me.

---

### Post by BDNiner on 2009-04-07
I eventually had to retag my entire collection. Took about 4 hours but i got it done using EasyTag. But I only have 4000 or so songs in my collection. I wish Amarok or Rhythmbox would handle this for me but i guess not.

---

### Post by GepettoBR on 2009-04-07
> **BDNiner said:**
> I eventually had to retag my entire collection. Took about 4 hours but i got it done using EasyTag. But I only have 4000 or so songs in my collection. I wish Amarok or Rhythmbox would handle this for me but i guess not.

My problem exactly. I intend to append the album year to the beginning of the Album field in every track for easier sorting on my iPod, which lacks the option to sort by year, but I have almost 4 times as many unique tracks as you.

---

### Post by simtaalo on 2009-04-07
is there any tagging program that you can just feed in your whole collection and it can automatically tag it all?

---

### Post by blue_shift on 2009-04-07
1. You might want to take a look at Ex Falso for tagging.
2. If you can't write tags with Amarok etc. that is not normal. Are your files read-only (eg. on an external disk which is mounted as read-only)? Something is preventing the programme from writing to the file.

---

### Post by GepettoBR on 2009-04-07
> **blue_shift said:**
> 1. You might want to take a look at Ex Falso for tagging.
2. If you can't write tags with Amarok etc. that is not normal. Are your files read-only (eg. on an external disk which is mounted as read-only)? Something is preventing the programme from writing to the file.

I thought of that, but all the files are owned by me and have read-write permissions.

Amarok and Rhythmbox do not complain about any sort of error when I edit the metadata, but for some reason they only seem to change the information within their own databases and leave the actual tags unaltered.

> **simtaalo said:**
> is there any tagging program that you can just feed in your whole collection and it can automatically tag it all?

There might be some program that uses the MusicBrainz database to figure out and fill the tags, but a large portion of my collection is comprised of more obscure music that MB would tag incorrectly. Even my fairly mainstream The Who tracks from Woodstock are incorrectly identified.

---

### Post by Therion on 2009-04-07
> **GepettoBR said:**
> 

... Rhythmbox ... leave[s] the actual tags unaltered.
**S--T!**  

Are you serious???!!!  Oh dear gawd. I never... I never really *checked* that, I just assumed it was... I mean it LOOKS as if...

If you'll excuse me, I'm going to assume the fetal position in the corner now as I ponder the implications of this.

I could see this becoming a real business opportunity for someone willing to take up the task: "We'll tag your library!  *Ten cents a song!!"







/*No, I'm not offering to tag your library for ten cents a song.
//Or am I????

---

### Post by GepettoBR on 2009-04-07
> **Therion said:**
> **S--T!**  

Are you serious???!!!  Oh dear gawd. I never... I never really *checked* that, I just assumed it was... I mean it LOOKS as if...

If you'll excuse me, I'm going to assume the fetal position in the corner now as I ponder the implications of this.

I could see this becoming a real business opportunity for someone willing to take up the task: "We'll tag your library!  *Ten cents a song!!"






/*No, I'm not offering to tag your library for ten cents a song.
//Or am I????


This is only in my case. At least, I hope so. I hope it's some sort of bug or a package I'm missing, or something else, as I do believe that Rhythmbox is *supposed* to edit the tags directly. So, um... don't panic :lolflag:

---

### Post by BDNiner on 2009-04-07
Yes, rhythmbox and amarok do not actually alter the tags (at least not in may case). That is why i used Easytag.

@simtaalo: I wish there was a way to automate the process. even if you could feed a script into easy tag to work its way through a directory would be great.

---

### Post by Therion on 2009-04-07
> **BDNiner said:**
> 

Yes, rhythmbox and amarok do not actually alter the tags (at least not in may case). That is why i used Easytag.
You're killing me.  Please stop.  "Only" fifteen-hundred tracks or so, but still...

---

### Post by BDNiner on 2009-04-07
> **Therion said:**
> You're killing me.  Please stop.  "Only" fifteen-hundred tracks or so, but still...

I was under the impression that they did on my computer then i installed exaile and the tags were all messed up there. It would not let me change them either. it really hit home when i upgraded to the latest version of Amarok and instead of importing the MySQL settings from my previous install i had it create a new database and all the tags went back to their Windows Media Player defaults!!! So i decided to retag them using Easytag.

---

### Post by Simian Man on 2009-04-07
This is also a pet peeve of mine.  I spent an excruciatingly long time filling in the tags on Rhythmbox only to have them all lost during an upgrade.  Is there anything that can get the info automatically from the internet like what happens when you rip a CD in the first place?

---

### Post by GepettoBR on 2009-04-07
Dang, so neither of them actually support writing to ID3 tags? This is completely unexpected. It's been the de facto standard for storing audio metadata for at least ten years...

What would be the most efficient way for me to petition the developers of each player to add this feature?

---

### Post by ufugu on 2009-04-07
Rhythmbox WILL edit the tags in the actual file if you have the option to do so enabled.  It is a decent tag editor (although if you have a large library it is worth the learning curve to master EasyTag).

I've found tag reading pretty reliable between Rhythmbox, Quod Libet/Ex Falso, EasyTag and even iTunes, but have had mondo troubles with Amarok.  

Apparently Amarok uses a different version of ID3. It truncated several thousand of my tags when I tried it again last year (it doesn't like anything over 20 characters for example).  NO FUN.

As cool as Amarok is in many ways, its weaknesses dealing with tags is profound--just search through their forums and you will find dozens of topics about tag issues with no resolution.

---

### Post by BDNiner on 2009-04-07
> **ufugu said:**
> Rhythmbox WILL edit the tags in the actual file if you have the option to do so enabled.  It is a decent tag editor (although if you have a large library it is worth the learning curve to master EasyTag).

How do u enable editing tags in Rhythmbox? Can you also enable editing the file names too? This i think was the best feature of EasyTag since my music was ripped using various mp3 players over the years.

I am planning on going through my girl friend's library soon and correcting all the tags. It is on the windows PC though and i fear that itunes and WMP will undo all my work.

---

### Post by logos34 on 2009-04-07
I think the problem is they're reading and writing different versions of the tag -- id3v1.x and id3v2.x

---

### Post by Grifulkin on 2009-04-07
My only question here is why are you using both Amarok and Rhythmbox?

---

### Post by BDNiner on 2009-04-07
> **Grifulkin said:**
> My only question here is why are you using both Amarok and Rhythmbox?

Why not? There are things that i really like about Amarok like the MySQL backend but I have been using Rhythmbox for a number of years now and I have gone through and rated all my tracks and got it running the way i like it to. I want to switch to Amarok at some point if i can port all my user data over.

I constantly load playlists on my mp3 player that are for example all my 5 star tracks, or all my most listened to tracks. I don't want to start this over with Amarok just yet.

I also have Exaile and Banshee installed.

---

### Post by egalvan on 2009-04-07
> **logos34 said:**
> I think the problem is they're reading and writing 
**different versions of the tag -- id3v1.x and id3v2.x**

I agree with this...

i had a similar problem over in Windows-land a few years back.

I had used a dedicated mp3 tagger, and when I started using
MusicMatch found that the id3 versions were different.

Frustrating at the time with some 8,000 songs,
now that I have over 32,000 carefully archived songs,
it is devastating to have software that cannot agree on which version to use, or at least offer to display both, or offer to normalize them.

Yes, I own many, many LP, cassette, and CD albums.
All being digitized.
And yes, I have several back-ups. Four, at the moment.

---

### Post by GepettoBR on 2009-04-07
> **Grifulkin said:**
> My only question here is why are you using both Amarok and Rhythmbox?
They both have features that I like, and that the other lacks. Amarok's wiki-lyrics plugin fetches the lyrics for most of the songs I listen to, the OSD is really helpful when I'm doing something else and switch tracks though the global hotkeys and it's easier to manage playlists with. Rhythmbox loads and responds faster since I use GNOME, I can resize the window to get a great big picture of the album art, it finds newly added tracks without my having to click "Refresh Collection" and doesn't screw up the track order in my iPod like Amarok.

> **egalvan said:**
> I agree with this...

i had a similar problem over in Windows-land a few years back.

I had used a dedicated mp3 tagger, and when I started using
MusicMatch found that the id3 versions were different.

Frustrating at the time with some 8,000 songs,
now that I have over 32,000 carefully archived songs,
it is devastating to have software that cannot agree on which version to use, or at least offer to display both, or offer to normalize them.

Yes, I own many, many LP, cassette, and CD albums.
All being digitized.
And yes, I have several back-ups. Four, at the moment.

So... can this Easytag (or anything else) search my files for ones that don't have ID3v2 tags and copy over the content from the ID3v1 tags only in those cases? I haven't found the option and if I do it globally a lot of the songs with longer names will miss the end, since IIRC ID3v1 has a character limit per field.

Winamp does my music better, mostly. Too bad it won't run smoothly on Wine.

---

### Post by egalvan on 2009-04-08
> **GepettoBR said:**
> 

So... can this Easytag (or anything else) search my files for ones that don't have ID3v2 tags and copy over the content from the ID3v1 tags only in those cases? I haven't found the option and if I do it globally a lot of the songs with longer names will miss the end, since IIRC ID3v1 has a character limit per field.

Winamp does my music better, mostly. Too bad it won't run smoothly on Wine.

I used to use a program under Windows... but it's been a year at least, and I don't remember the name...

I'll try to look it up next time I boot XP...

ErnestG

---

### Post by kpkeerthi on 2009-04-08
Back in the days when I used GNOME, I tagged all my music (~10000 songs) using Audio Tag Tool. I had no problems having Rhythmbox/Exaile/Quodlibet read the tags.

I migrated to KDE4 and now use Amarok2. I have no problems having Amarok2 read the tags from the music files either. For new rips since KDE4 migration, I've been using KID3. Quite awesome stuff.  

Tag tools usually offer support to tag both ID3v1 and ID3v2. I usually tag using ID3v2 and copy the same as ID3v1 as well (for my car stereo can't recognize v2 tags).

---

