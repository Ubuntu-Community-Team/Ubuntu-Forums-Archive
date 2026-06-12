---
title: "Problem with streaming and gstream codec"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Wanda on 2009-03-18
[FONT="Garamond"][SIZE="5"][FONT="Garamond"][SIZE="5"]
Greetings,

I am a newB (idiot), last Feb I installed ubuntu 8.10 and proceeded to do well until a series of things started to fail, the worst being that the resolution on my freecycled CRT went wacko and I was un-able to reconfigure to an entire page. I tried playing with the tab key to enter new settings which were not visible, but that eventually killed the screen and in a way I was glad because I had had problems with other features, Wine would not remove totally and there was this codec problem... that seemed flaky. I thought a re-install would be a tad easier, and it has been;)!

I do think the world Linux and there is no looking back to funding the coffers of Gates & Jobbs. I am even considering doing a class ot two in Linux and ubuntu to get me up to speed. I would like to be able to at least answer my simple questions posted to the forums... writing code is a different story... I have just begun to switch over from crossword pass times to SuDuKo... I am a man of letters, ¿sabe Ud.? and searching through reams of code is not a pass time, at least not yet.

I digress, so I reformated the old machine and started adding the old back up stuff and some of the stuff that I had lost like radio stations that I listen to on Rhythm box, which in some cases requires or relies on different codec's according to the station desired to install.  Presently I am listening to U. of Puerto Rico, and often listen to Columbia U., Boston College, some of the pre-packaged Norwegian radio stations while I work on the computer. (It has been just dropping and I have had to reload it this morning, which is not such a big deal.) However, when I am trying to watch a film say on internet archive.org, and the stream fails, and starts this weird slow down in both audio and visual, I'm only left with the option of restarting it from the begining. This slow down reverberation also occures in audio as well. (I should add here that I connect to the Inet via slow DSL.) There has been in the past a station that I like, Javieriana Universidad in Colombia, (yet another Jesuit institution like Boston College) that has great clasic latin and general programing. When I went to the Bogotá site it gives two options: one for MS player and the other for Winamp in order for it to stream. It also  demanded in a pop up that I down load some gstream codec's for the station to stream correctly. This I did and again I ended up with the problem of a slowed audio and video response.  It starts out fine but then turns into a bad acid trip. (Naturally there are more than half a dozen gstream codec's listed in the Synaptic package management section, not just the gstreamer 0.10 schroedinger. So this in not a simple add-on / remove problem. Now I am not only having problems listening to audio but also watching free legal public domain films ([http://www.archive.org/index.php](http://www.archive.org/index.php)) another great feature that I hope will only expand.
I would be very greatful for any ideas as to how to fix this problem.  

In my searching for this question I came across mention of Navidia graphic card a lot. I have no idea what kind of graphic card my machine runs as it once was a computer (tank) that was run in a series for a server and has never seen either a MS or Mac OS piece of softwear, so I can only assume that the graphics card was of minimal quality, but still does have ample power as it was used as a work horse. It is very heavy metal and the fan whirs. Still it was the right price, donate free:)

I would like to avoid reformating anew, and just giving up on the university station running out of Bogotá, Universidad Javieriana, but if it means better opperation so be it. Eventually I will buy a cheapish laptop with many more features so that I will be able to do a lot more.  But for now I would like to address fix this issue.[/FONT]

TIA,
Wanda

P.S. this post might be better off in the chat cafe, but I do have a real problem and wanted to get it all worded correctly. I'll be checking back for possible solutions periodically and will post about out comes. [/SIZE][/FONT][/SIZE][/FONT]

---

### Post by carml on 2009-03-18
What's your urgent problems?:confused::confused::confused:
I red all your post,but I missed your problems:
a problem at once and less boundary explications please,so everyone can understand;);what software are you using,what is the problem with the codecs?

---

### Post by teunispeters on 2009-03-18
If you could include the URLs of any example radio stations - that would probably help with testing.

It sounds like streaming audio is breaking down - possibly connection quality - but also that the connection itself is not being cached correctly.  gstreamer does sound like where to look...

as for video problems - there's a chance video card can't handle the video very well.   Try turning down effects in your system (System->Preferences->Appearances; Effects tab, turn down to minimal).  I have to do this on my laptop to play videos properly.

---

### Post by Bleskojd on 2009-03-18
Yes. What is your problem? This seemed more like introduction to me. Please do not use such big letters. :)

---

### Post by Wanda on 2009-03-18
The problem is sound and video slow down, with the sound it is like a reverberation and with video/audio it slows the motion of the graphic and does the reverb. Just after posting this AM, I tried: 

[http://www.filmschatten.org/](http://www.filmschatten.org/)
and 
[http://www.archive.org/details/moviesandfilms](http://www.archive.org/details/moviesandfilms)

both these sites did not function at all.

Sorry about the big letters but I use reading glasses. Is it so bad that I use a bigger type face? i mean it's not like i'm writing all in caps, right?

The request for the radio station urls which throuout the day have not only dropped but also gone into that sound distortion, Some that I have listen to are:

[http://kanga.college.columbia.edu:8000/listen.pls](http://kanga.college.columbia.edu:8000/listen.pls)

[http://www.radiouniversidad.pr/hifi.m3u](http://www.radiouniversidad.pr/hifi.m3u)

[http://media.hiof.no/streams/m3u/nrk-alltid-klassisk-172.ogg.m3u](http://media.hiof.no/streams/m3u/nrk-alltid-klassisk-172.ogg.m3u)

[http://www.wbur.org/listen/feed/ogg.m3u](http://www.wbur.org/listen/feed/ogg.m3u)

All of these have done the reverb distortion.

The radio station in Bogotá that asked for the gstream codec's was:
Javeriana Estéreo 91.9 FM Bogotá | [www.javerianaestereo.com](www.javerianaestereo.com)

And yes I would like to get to the point where I could help others like myself with ubuntu and Linux.

I do appreciate the time and effort. Thanks.

---

