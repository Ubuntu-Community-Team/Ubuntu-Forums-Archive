---
title: "Downloads taking over system"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by Scunnered on 2009-01-21
I am in need of guidance as I am unsure what is the best action to take.

I have downloaded GNU backgammon game from the add / remove section only to find that after playing say 3 or 4 games that there comes a point where the game totally freezes up everything. The only way that I could access everything else was to remove the game.

I had requested assistance to play music on a random basis and I was told that Audacious would meet my needs so I downloaded this via Synaptic.  In this instance I found that yes it would do as I wanted but having closed the file down I was unable to access my documents  What was happening was that when I clicked Places > My Documents Audacious started up playing  again and again.  As before I had to remove this to enable me to revert to my documents.

I may be able to live without being continually beaten by the computer at backgammon but as I much prefer to listem to music as background noise rather than TV I really need Audacious working properly (or an alternative)

Do I totally remove everything and start again or what is the alternative.  It took me a lot of messing about to establish my Wireless broadband connection and I would not like to repeat the experience if possible.

Thanking you in anticipation

---

### Post by cmnorton on 2009-01-22
What;s your connection speed?

---

### Post by Scunnered on 2009-01-22
I am on an 8MB broadband connection with Virgin Media via cable.

---

### Post by cmnorton on 2009-01-22
do you have a fast enough processor and ram? Clearly it is not due to your broadband throughput.

---

### Post by Scunnered on 2009-01-22
I can only assume that this is the case.  I purchased this laptop at the year end as  a Lunux specific system and it was pre-installed with 8.10. With a GIG of RAM there should be no problems for downloads.

I am at a loss as to why these programmes will not properly perform and end up completely negating everything on the system.

---

### Post by Nepherte on 2009-01-22
Perhaps there's a process taking up all recourses. Check
```
top
```
and see if there's a process with high cpu or memory usage.

---

### Post by Scunnered on 2009-01-22
Nepherte

Many thanks for your reply.

As you may have guessed I am somewhat new to this.  I followed your suggestion but could not properly follow what was displayed. 

top - 17:35:53 up  2:16,  2 users,  load average: 1.10, 1.16, 1.11
Tasks: 129 total,   2 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 39.4%us, 11.6%sy,  0.0%ni, 48.9%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   1025084k total,  1006984k used,    18100k free,    30872k buffers
Swap:  3004112k total,        4k used,  3004108k free,   422624k cached
B
 7036 ian       20   0  167m 106m  16m S    0 10.6   0:43.61 opera                                                           
 5013 citadel   20   0 21316 4804 2672 S    0  0.5   0:01.43 citserver                                                       
    1 root      20   0  3056 1888  564 S    0  0.2   0:01.46 init                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration

after this point it followed the earlier examples of 1 & 2 root.

I am confused about the 2 users as I and I alone use the system and can only assume that this was based on the fact that I had your post open while I was seeking the answer to top.

I hope this means something to you and that you can offer a solution.

---

### Post by Paqman on 2009-01-22
> **Scunnered said:**
> I really need Audacious working properly (or an alternative)


Try totally removing Audacious (go to Synaptic and click on "remove completely" for Audacious)

There are a ton of different music players available. Try going to Applications > Add/Remove and looking in the Sound & Video category.

---

### Post by Scunnered on 2009-01-22
Paqman

Thanks for your reply.

I am interested in listening to FLAC files and wish to be able to play tracks on a random basis.  I have a very varied selection of CDs and wish to be able to listen to these using something that will randomise play.

Can you offer something that will meet my needs?

---

### Post by mlentink on 2009-01-22
> **Scunnered said:**
> Can you offer something that will meet my needs?

Banshee will do this, but so will Rythmbox, which should be already installed

---

### Post by KIAaze on 2009-01-22
Almost every music player has an option to play files randomly. I don't think this is a problem.

As for flac support, I have no idea, since I don't have use it, but here's a review of 15 players:
[http://www.smashingdownloads.com/2008/10/19/15-linux-music-players-download-your-favorite/](http://www.smashingdownloads.com/2008/10/19/15-linux-music-players-download-your-favorite/)
(My personal favourite is Amarok)

And a discussion about flac support:
[http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/61116-music-manager-supports-flac.html](http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/61116-music-manager-supports-flac.html)
Flac capable media players: [http://flac.sourceforge.net/links.html#software](http://flac.sourceforge.net/links.html#software)

You may also want to try xmms, which is similar to audacious (winamp-clone).

---

### Post by Scunnered on 2009-01-22
mlentink & KIAaze

Many thanks for your assistance.

I had looked at Rhythmbox earlier and was a bit puzzled by the way tracks were displayed.  On your suggestion I revisited it and if I ignore the display found that it will do what I want.

I will work with this initially but will have a good look at what KIAaze suggests.  Fron the look of his post there should be lots of good reading there.

Again my sincere thanks

---

### Post by cariboo on 2009-01-22
I would check Synaptic to see if the ubuntu-restricted-extras package is in stalled, as this meta package provides all the codecs you need to play most types od audio/video media. It also provides flash, java and mscorefonts.

Jim

---

### Post by Scunnered on 2009-01-22
cariboo907

Many thanks, I have checked and this was installed  OK.

Looks very much like that I will forget playing backgammon and follow through on the other music playing options to see what I better understand.

---

