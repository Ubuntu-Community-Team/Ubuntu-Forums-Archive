---
title: "Maximum volume increase?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by 11010110 on 2008-12-12
Hi

The maximum volume on my computer since switching to linux is much much lower than it was with windows. I turn it all the way up and it seems to be less than a quarter the loudness the maximum volume was for windows on this same computer using the same hardware. I was wondering if there was a way to increase the volume maximum. I read in another post that the limit is due to the hardware but that cant be since i have seen this same hardware go MUCH louder. 


If anyone could help me out that would be greatly appriciated.

Thanks in advance

---

### Post by marshall.robert on 2008-12-12
double click on the sound icon in the panel and then go through all the options tickign everything and pulling all the sliders up (dont do this for recording sections) i sometiems find that there is some "sub section" volume control that has decided it doesnt want to be at full volume.

---

### Post by sneeks on 2008-12-12
i have this same problem myself,but have got used to it now,if i use puppy linux or anti-x i don't get this problem.
but look on the bright side,you wont deafen yourself  !!!!!!:lolflag:

---

### Post by 11010110 on 2008-12-12
yeah that didnt work lol i had tried that earlier and still nothing. there has to be some way to do it lol. Ill keep researching. And it is true not going deaf could be the glass is half full way of looking at it lol

---

### Post by markbuntu on 2008-12-12
I have a HDA on board sound chip ( ALC888 ), a PCI card ( C-Media 8768 ) and a usb headset dongle(Plantronics/C-Media). There is a huge difference in the output volume of these things. The HDA chip is about 1/2 volume of the C-Media PCI and the USB headset is far louder. With my Sony Headphones( the plantronics headphones are crap) I need to set the usb volume at 8%, the HDA at 100% and the C-Media at 70% to get comparable levels.

I have the two sound cards connected to my stereo with separate line outs and it is the same, HDA about 1/2 the volume of the C-Media card. I wonder if this is deliberate on the part of the driver writers since many people complained of distortion at 100% with previous drivers. 

Windoze also does some behind the scenes equalization/boost for the sound drivers so all those crappy audio chips sound better. Linux is more honest about sound reproduction.

---

### Post by 11010110 on 2008-12-13
now if only there was some way for me to get that behind the scenes boost as well lol.

---

### Post by 11010110 on 2008-12-16
Hi everyone, 

I have been searching thru google etc for a solution to this for days and i have found absolutely nothing... The problem is that the sound at max with ubuntu is less than a quarter of what the max was with vista (same machine).I have a laptop and everything even alsamixer is turned all the way up... also the sound goes from nothing to "loud" in the last quarter of the range... I have no idea what to do but from what i see this is a very common problem. stremaing media online (youtube etc...) is barely audible in a quiet room... This is one of the last things i need to work out in ubuntu before it is my main OS.

Thanks in advance and anything at all would be of great help!

---

### Post by starcannon on 2008-12-16
System>Preferences>Sound

Try setting everything to alsa, make sure your card is set on the **Default Mixer Tracks: ***Device*; and that may fix you up. If not try setting everything to pulse auido, bue sure to use the "Test" button for easy progress checking of settings.

GL

---

### Post by 11010110 on 2008-12-17
nope nothin yet... thanks for the shot but for some reason nothing i have tried or looked up has wored thus far... i have tried every setting available. the higest volume is set to 0 decibels and there is no way to change it. i know that it isnt a soundcard limitation because as previously stated i have run vista on this box without any problems. all of the drivers are in and runnin. any ideas on where to go from here?


thanks again for the help thusfar guys hopin' that we can find a solution!

---

### Post by starcannon on 2008-12-17
are the "Test" button sounds loud?
Someone earlier was getting loud system sounds, and low flash player sounds. They claimed solved after cranking all mixer settings to full and or adjusting the flash player volume level in the flash player ui(most flash players default to 50% volume)

---

### Post by 11010110 on 2008-12-17
they sound marginally loud but that is only when the volume is set to 100%. the mp3 player is still at casual level when the volume is cranked full. ill look into the flash settings though. thats just a right click on the flash that is running correct?

---

### Post by 11010110 on 2008-12-17
lol now i cant seem to find a volume control for flash lol (aside from the mic control)... oh the joys of being a noob. kinda fun though lol i was pretty advanced at windows so its nice to face a challenge.

EDIT: are you talking about the volume control located on the UI of the player itself? if so thats cranked up too and its still a whisper.

---

### Post by starcannon on 2008-12-17
> **11010110 said:**
> they sound marginally loud but that is only when the volume is set to 100%. the mp3 player is still at casual level when the volume is cranked full. ill look into the flash settings though. thats just a right click on the flash that is running correct?
Most flash players have a volume controller if they allow you to set the volume:
[IMG]http://img267.imageshack.us/img267/4835/flashvolumels6.png[/IMG]

---

### Post by 11010110 on 2008-12-17
yeah thats all the way up and still nothin. on some players when the volume is 100% its audible if im alone without ambient noise but with others its all but silent.

---

### Post by 11010110 on 2008-12-17
the easiest solution would be some program that pre-amped the outgoing sound globally and just sat itself in the tray unobtrusively but that (to my knowledge) doesnt exist. If only i was a programmer lol.


EDIT: i found that in VLC i can up the volume to 400% so that makes onboard vids a bit easier but the problem remains for the rest of the system. the max levels out at 0db (100% of norm) meaning that there is no increase over normal so all i can do is go lower than the recording of the song or what have you. hmmm...

---

### Post by 11010110 on 2008-12-17
i found that some of the settings were hidden in the mixer and the "front" was at 3/4 and now there is some improvement over where i was. still its not perfect but its doable. thanks a bunch and if anyone has any more thoughts theyd be welcome and appreciated! thanks all!

---

