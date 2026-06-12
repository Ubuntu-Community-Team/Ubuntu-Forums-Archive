---
title: "[SOLVED] itunes m4p files"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by capnthommo on 2008-12-16
hi.  does anybody know of an app that will decrypt itunes M4P (M4A) files for me so i can play them as eg mp3s on songbird or rhythmbox.  or do i have to burn them all to cd and then copy to my music player.   when i have my ipod connected i get "playback error - encrypted file. does not support decryption" type error or when not connected i get "playback error - resource not found"
this suggests to me that songbird is only reading data from the ipod and though the files seemed to transfer and are listed in the songbird library no actual data has come across with them, correct?
 i didnt have a lot of luck when i tried tune clone because it wouldnt copy track data so when i tried to copy the second cd it just tried to overwrite the first tracks and editing them manually didnt seem to make any difference - they still tried to overwrite.
sorry to keep niggling at this one, but it goes against the grain not to be able to play tunes i have paid for legitimately just cos i have, in effect, bought a new 'record player'.  back in the day buying a new hi-fi didnt mean you had to get a whole new record library.
thanks all
nigel

---

### Post by shifty_powers on 2008-12-16
friad that's illegal, and to tell you how to do so would be against the forum rules afaik.

anyways, it is notriously difficult to achieve...

---

### Post by jamesrl on 2008-12-16
As far as I know, there is no way in linux or in MAC OS X to decrypt m4p files, but there is within windows (I believe something like jhymn, fairplay, or the like will do the trick).  In linux you can't even play the files, because you don't have access to the account information necessary to decrypt them.  In windows, there is a memory flaw in either the OS or Itunes (not sure) that allows a program to access the unencrypted information when it plays.

By the way, I disagree with the previous poster about the legality of this.  This is no different then teaching someone how to play a store bought (encrypted) dvd within linux, or backup there dvds.  It is in violation of the itunes end user agreement, however.  

I highly recommend the amazon.com music store, which sells high quality mp3 without any copy protection.

---

### Post by markharding557 on 2008-12-16
What you are on about is fairplay drm,fortunatly ubuntu does not support it

---

### Post by shifty_powers on 2008-12-16
heh, was not trying to lecture believe me.

but it is a fine line with these things, and the question of whether it is illegal or not is still not set in stone.

as with dvd's, why do you think it is not included as standard, because in some territories it IS illegal.

but then i don't blame the op for trying to brake the drm. i HATE itunes, and i say that as a ipod user.

but then rockbox, well, rocks :D

---

### Post by balloooza on 2008-12-16
I sure hope it is legal, but you can open synaptic ( System > administration 
>synaptic package manager) and install the packages that have gstreamer

just search for "gsreamer" and start marking to install. if you hit all the fffmpeg (somthing like that) and a few others, you should be able to play those .m4a's. You can select more gstreamer plugins if you want to play those .wma.

I have not accualy tried it, but I have all the gstreamer plugins installed, and I have played every other format.

---

### Post by jamesrl on 2008-12-16
I guess I shouldn't have said it was illegal or not illegal, I think we both will agree that it is in questionable legal territory (esp as laws differ in different countries).  As we all saw back in the day with DeCSS there are many legal issues out there, but looking at the case of DVD Jon, (Norwegian Courts) found that since he only decrypted dvds he legally owned he was entitled to do so:
[http://en.wikipedia.org/wiki/Jon_Lech_Johansen](http://en.wikipedia.org/wiki/Jon_Lech_Johansen)

In my book, distributing copyrighted works == Illegal, decrypting works you paid for, so you can make backups or play on unsupported OSes != Illegal.  I have yet to hear of anyone being successfully prosecuted for decrypting works that they themselves purchased.

PS: I should add that the method of decrypting m4p, only works if you have the right to play those specific m4p's on the specific windows computer you are using.

---

### Post by jerome1232 on 2008-12-16
This is just a thought but can you use itunes to burn to cd (maybe a cd-rw so you can reuse the same disc) and then re-rip them as mp3. It's worth a shot at least.

---

### Post by capnthommo on 2008-12-16
thanks to all.  i am afraid i've just been a little stubborn about this one but i think i might just have to let it go.  it only means i have to use the family machine sometimes and cant have all my tunes on my laptop. i was only wanting to listen to my own tracks on my own machine.  life's far too short to get stressed about it anyway.
it will be tough but i shall try my hardest to let go - and if anybody sees me posting about this again, just gently remind me what i said.  thanks very much for the help
nigel
):P

---

### Post by jamesrl on 2008-12-16
**Balloooza** you are talking about something slightly different.

m4a = mp4 with no copy protection (DRM-free)
m4p = mp4 with copy protection (itunes specific DRM)

You can do lossless decryption of m4p to m4a within windows.  It is legal to install the codecs that play the m4a files.

---

### Post by jamesrl on 2008-12-16
And for the record, you currently have to use (within a Windows machine that Itunes can open the files within)
MyFairTunes [http://sourceforge.net/projects/myfairtunes](http://sourceforge.net/projects/myfairtunes)
or QTFairUse [http://en.wikipedia.org/wiki/QTFairUse6](http://en.wikipedia.org/wiki/QTFairUse6)

---

### Post by capnthommo on 2008-12-16
hi jerome, yes that looks like being the only way but as i said earlier, the data doesnt always come across and then the player only sees 'track one, track two' etc and so when it comes to the next cd it tries to overwrite the first set.  and i haven't figured out a way to stop this happenning yet.  editing the titles and so on doesnt seem to make a difference.  i think the GSTreamer options will be worth a shot too.  but that;s the last, positively.  no, honest, i mean it this time.  thanks again to everyone

---

### Post by shifty_powers on 2008-12-16
> **jamesrl said:**
> I guess I shouldn't have said it was illegal or not illegal, I think we both will agree that it is in questionable legal territory (esp as laws differ in different countries).  As we all saw back in the day with DeCSS there are many legal issues out there, but looking at the case of DVD Jon, (Norwegian Courts) found that since he only decrypted dvds he legally owned he was entitled to do so:
[http://en.wikipedia.org/wiki/Jon_Lech_Johansen](http://en.wikipedia.org/wiki/Jon_Lech_Johansen)

In my book, distributing copyrighted works == Illegal, decrypting works you paid for, so you can make backups or play on unsupported OSes != Illegal.  I have yet to hear of anyone being successfully prosecuted for decrypting works that they themselves purchased.

PS: I should add that the method of decrypting m4p, only works if you have the right to play those specific m4p's on the specific windows computer you are using.

well dvd jon only applies to norwegian law.

but yes, it is all questionable, and between you me and the four walls had a crack at this myself once upon a time and found it to be a monumental pain in the ***...

---

### Post by johnfrlv on 2009-03-11
> **capnthommo said:**
> hi jerome, yes that looks like being the only way but as i said earlier, the data doesnt always come across and then the player only sees 'track one, track two' etc and so when it comes to the next cd it tries to overwrite the first set.  and i haven't figured out a way to stop this happenning yet.  editing the titles and so on doesnt seem to make a difference.  i think the GSTreamer options will be worth a shot too.  but that;s the last, positively.  no, honest, i mean it this time.  thanks again to everyone

I found you have to go into the music file and rename each "track" before loading the next CD to keep them from being replaced. Yes it takes a while but haven't found an easier alternative yet.

---

### Post by LowSky on 2009-03-11
You do know that Itunes just released almost everything in their library form DRM, you pay $0.30 a song to upgrade it to DRM free. Stupid and annoying as now im thinking of spend the $50-60 on upgrading my library so Its one less thing for me to dual-boot for. Sure its only like 200 songs compared to my 15000 songs I have (I dont really purchase much songs on iTunes) in my library, but to have them all would be great.

---

### Post by capnthommo on 2009-03-19
hi johnfriv and lowsky.  thanks for the update.  i have actually given up on this one.  i use my ipod as is to play anything under DRM that i cant play any other way and just make sure anything i get now is in cd or mp3 format.  can't say i have really noticed any great sense of loss, once i got my head around it.  
i have since found a cool replacement for Itunes too, at
 [http://www.emusic.com](http://www.emusic.com) 
 it has loads of tracks and all in DRM free mp3 format, including most of the artistes i like.  ok there are some that aren't available, but i can always get the cd for those few.  i pay a monthly fee for a set number of tracks and if i should happen to lose one i can redownload it free.  and when i've bought it i can put it on whatever i want - not restricted to their branded player.  and no, it's not a subscription so they don't disappear if i decide not to continue.
it works out at about 30pence a track as opposed to itunes 79pence, and whoohoo! they are actually mine, like i bought the record.
sorry, i came over a bit evangelically then, didn't i?  i'm not advocating it but others might find it useful too.
cheers
nigel

---

### Post by thisnamestoolong on 2009-05-04
Hey I'm jumping into this a bit late in the game, but I actually found a pretty easy workaround for playing iTunes files in Linux. All I had to do was install Quicktime and the Windoze version of Songbird (with the Quicktime plugin) through Wine, and my protected iTunes files work fine. If anyone has any ideas for ways to strip the DRM from iTunes 8 files though (other than the burning to CD method, it is far too time consuming and reduces the quality quite noticeably), I would still be interested...

---

