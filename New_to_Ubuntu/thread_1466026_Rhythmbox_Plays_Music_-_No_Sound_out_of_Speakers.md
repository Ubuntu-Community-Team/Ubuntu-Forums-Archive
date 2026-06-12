---
title: "Rhythmbox Plays Music - No Sound out of Speakers"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Twitch04 on 2010-04-29
Hello, everyone. 

I'm having a slight problem with Rhythmbox. I run... well, now Ubuntu 10.04 on VirtualBox, but I did run 9.10 before, and I've had the same problem in both versions. When I go to play music in Rhythmbox [after I have to download some plugins because for some reason it doesn't come prepackaged being able to play MP3s... you'd think that'd be there already.], the music will play, as in the progress bar will move, but no sound comes out of my speakers.

My speakers work fine. The sound is all the way up for Ubuntu in general and for Rhythmbox. When I load Ubuntu, I hear the sounds that play. The drums, then the... whatever you want to call it, haha. 

Any idea what the problem could be, or any other information I should give?

---

### Post by Sealbhach on 2010-04-29
The plugins aren't included for legal reasons, Ubuntu could not be distributed for free if they were included.

When you're playing a song in Rhythmbox, click on the sound icon on the top panel and look in Sound Preferences to see if something is muted. Also open a terminal and type

```
alsamixer
```and make sure the volume is turned up on all of those.

Another thing to try is to install aumix-gtk and play with the volume controls in that.

.

---

### Post by Twitch04 on 2010-04-30
Alright, all the values seem to be up that need to be in alsamixer. I got aumix-gtk and it showed all of the relevant values up as well, turning everything up on it didn't work. And the sound button in Rhythmbox shows the volume up all the way, too. Still nothing.

---

### Post by Peter09 on 2010-04-30
Do you get any sound from the virtual machine, login sound etc. Just to confirm its not the virtual machine setup.

---

### Post by Twitch04 on 2010-04-30
> **Peter09 said:**
> Do you get any sound from the virtual machine, login sound etc. Just to confirm its not the virtual machine setup.

Yeah, I said that in my first post. When Ubuntu boots up I hear the bongo drum things when I get to the user-select screen, and when I type my password and actually log-in I hear the... little jingle music. It's only Rhythmbox that hasn't made any noise.

---

### Post by En_A on 2010-05-17
Hi

Im having the same problem too. Rythmbox suddenly does not produce any sound, while other apps do well. Im new to ubuntu also, but i found out it was caused by Rythmbox being muted individually.

Just go to Sound Preference -> Applications tab, see Rythmbox audio slider if it set to zero or muted. Hope helps :)

---

### Post by aashifcarbon on 2010-09-05
> **En_A said:**
> Hi

Im having the same problem too. Rythmbox suddenly does not produce any sound, while other apps do well. Im new to ubuntu also, but i found out it was caused by Rythmbox being muted individually.

Just go to Sound Preference -> Applications tab, see Rythmbox audio slider if it set to zero or muted. Hope helps :)

i was havin' the same problem until i went and checked the applications tab in sound preferences just as you have said. thank you very much En_A. you know what u r talking about ~Cheers

---

