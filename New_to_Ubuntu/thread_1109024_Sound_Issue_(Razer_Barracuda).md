---
title: "Sound Issue (Razer Barracuda)"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by kurohoshi on 2009-03-28
Hello,
First I should mention that I am new... This is my first time using linux, and I think I will love it once I get sound to work...

I am using the Razer Barracuda AC-1 sound card and HP-1 Headphones.  I also have an on board sound card, but I do not have speakers or anything hooked to that.

I installed linux, and I have followed several guides to setup the audio sadly none of these worked.  I will admit I could have screwed up somewhere along the way (cause I really don't know what I am doing.)  

I have read that I should use Alsa drivers, but I can not get them to work at all.  I managed to get sound working for a few programs using the OSS drivers.  However with this method nothing in wine had sound, and I would only get sound from one program at a time.  (I would play music in a media player, a video in another and the first one would have sound the second would have nothing.)  I often listen to music or watch videos while I game... so this would be an issue for me :-k.

If anyone can give me help on this it would be much appricated.  I have spent over 15 hours pulling my hair out over this ](*,)

Thanks in advance.

---

### Post by 123456789123456789123456 on 2009-03-28
The AC-1 sound card, I admit I don't know much about this particular sound card.  Is it PCI?,  You mentioned that you have an onboard sound card.
One possibility could be interference.  Make sure the following is accuring, start the computer up, enter BIOS.  In BIOS, make sure that the onboard sound card is disabled.  and that the BIOS reconizes the AC-1 card as being connected and in use.

Some times, with windows machines, having both sound cards active, makes no difference, however, with both devices active, they do tend to interfear with the operation of each other.  Most BIOS chips, want to use the onboard card as the primary, and tend to cause problems with other devices.  Disabling the onboard card, forces the BIOS to use the other card as primary.  This may actually fix the problem.  Expecially if you don't use the onboard card.

I don't know about the computer itself, if the card is an ISA card, that would mean that ubuntu does not support those devices, but you said sound does work, but not all the time, and is sparitic.  this tends to lead me to beleave my first theory would be correct.

Try disabling the onboard device.  If that does not work, tell us.

---

### Post by kurohoshi on 2009-03-30
Thank you very much!!  That fixed it. :)  I can't believe it was that easy... 

Now as long as my games will play ok I am set to leave windows for good. [-o<

---

