---
title: "can't get sound from a power point presentation"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by RajaAjmal on 2009-04-10
hi there,
i've received a power point file (pps). when i run it on ubuntu, i can get only the pictures and animation, but no sound. but when i play it on windows, it does play the sound.
any help please.

---

### Post by Sef on 2009-04-10
1) What is your system specs, especially your sound card?

2) Is it just this power point presentation or others that you have problems with?

3) Have you downloaded the codecs for mp3 and others?

4) Do you have sound otherwise?

---

### Post by RajaAjmal on 2009-04-11
thanks for the reply sef.
i don't know my sound card's configuration.
i do have the mp3 codec. i listen to music, play movie and DVD. i do have sound on my ubuntu. 
i have received 2 power point presentation which play a music while it is being run. Just that when play it in ubuntu, i can get only the animation and pictures, but no music. i think the problem is not with ubuntu but with open office. i don't know how to make it play the music.
Please help.
by the Sef, sorry for this late reply.

---

### Post by bwallum on 2011-01-10
Did you ever resolve the issue? I'm trying to play Powerpoint files with embedded audio. VLC player plays the audio without images and OOo shows the presentation without audio.

---

### Post by David Oxland on 2011-04-27
Bump: same here

---

### Post by philip on 2013-03-30
I was going crazy with this over a *.ppt file I got sent. VLC would not even play the audio for me; nothing would.  LibreOffice ignored it entirely, so renaming the saved *.odp to *.zip was vain, in that no audio was contained therein.  In my case, running it as a presentation was not so critical as simply getting the sound out.  The *.ppt I was dealing with was the 2003 version, I believe.  In any event, opening it with vi showed an embedded RIFF @ WAV for each slide.  Finally, after reading several dozen web pages, I found a solution.  I installed the command-line program foremost and did:
[FONT=Courier New]foremost -v -t wav -i filename.ppt[/FONT]
and got a folder with a *.wav file for each slide.  I sure wish I had found out about this sooner.  Hope to save someone else the time!

---

### Post by oldos2er on 2013-03-30
Old thread closed.

---

