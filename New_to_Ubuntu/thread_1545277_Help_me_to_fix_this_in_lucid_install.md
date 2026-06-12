---
title: "Help me to fix this in lucid install"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by neilms on 2010-08-03
Hello comrades. I want you to get into the right mood to help me. Imagine we were all on a spaceship that has landed on Mars. Our ship has an on board computer which runs Ubuntu lucid 10.5. Unfortunately when we came in for landing there was a short circuit and we had no computer for a time. 
Before we can start the journey home we need to get our computer up and running. We have re installed ubuntu but there is one problem that must be fixed, namely the sound. There is no sound and we need it to hear things like mission control.
We have 24 hours to fix this problem else we will move into another orbit and it will be impossible to get home.
Come on guys, let us work the problem together and get our ship home.

---

### Post by StewartM on 2010-08-03
I haven't upgraded to Lucid (yet) but have you started to look here?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It would probably help to post any details on the system you're having problems with.

StewartM

---

### Post by corrytonapple on 2010-08-03
No sound out of speakers or headphones? Is it laptop or desktop?

---

### Post by Norm24 on 2010-08-03
No help but to comment on the avatar.Kelly's Hereos is a great movie and Oddball was one hell of a character!

---

### Post by neilms on 2010-08-03
> **corrytonapple said:**
> No sound out of speakers or headphones? Is it laptop or desktop?

Its a desktop and I want the speakers to work

---

### Post by neilms on 2010-08-03
> **Norm24 said:**
> No help but to comment on the avatar.Kelly's Hereos is a great movie and Oddball was one hell of a character!

Kelly's Heroes is one of my favourite movies. I bet Oddball could fix this pile of junk!

---

### Post by li(fe)sp on 2010-08-03
try
preferences >> sound >> hardware

you should be able to see your speakers listed ( if u had connected them properly)...mine shows 'Logitech z5 speakers'

choose it and make sure the profile is "analog stereo output"

then click on the output tab and make sure the device is selected and not muted..
for more help consult the below link
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by cpcpcp on 2010-08-03
Fixed the same problem whe I first installed things by going  Preference>Sound and un-ticking the mute button.. No idea why it was ticked but un-ticking it brought relief and music to my ears.

Did it fix for you?

---

### Post by neilms on 2010-08-03
> **cpcpcp said:**
> Fixed the same problem whe I first installed things by going  Preference>Sound and un-ticking the mute button.. No idea why it was ticked but un-ticking it brought relief and music to my ears.

Did it fix for you?

no dude. I have not fixed it yet. This is driving me crazy

---

### Post by neilms on 2010-08-03
> **li(fe)sp said:**
> try
preferences >> sound >> hardware

you should be able to see your speakers listed ( if u had connected them properly)...mine shows 'Logitech z5 speakers'

choose it and make sure the profile is "analog stereo output"

then click on the output tab and make sure the device is selected and not muted..
for more help consult the below link
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Thanks - this has changed the icon but still no sound. It is not clear about how to find information in the git database - thats where i got confused, but like i say, the icon on the panel has changed like its volume is turned up.

Can you help?
{I have to get some sleep now but i will check back at 09.00HRS...this is urgent guys}

---

### Post by neilms on 2010-08-03
If anyone can help i would be grateful:
System details.

The soundcard (Intel 82801FB, Packard Bell device which is a chipset of the ICH6 family) is built into the motherboard (which is a GIGABYTE GA-81915PM)

thanks.

---

### Post by neilms on 2010-08-03
The soundcard is built into the motherboard. I think that it is an Audio device: Intel corporation 82801FB Packard Bell device belonging to the ICH6 chipset family.

The motherboard is a gigabyte GA-81915PM.

The computer is a Packard Bell machine and its around 5 years old.

---

### Post by corrytonapple on 2010-08-04
Just some silly basic things to try:
Make sure they are plugged in
See if they work on a different computer
Test headphones to see if that works.

---

### Post by li(fe)sp on 2010-08-04
```
lspci | grep Audio
```

I assume u did this already...but just to be sure your integrated audio card is listed..

and then again...volume icon >> sound prefernces >> output

and make sure your device is selected...there is nothing much I can think of ...

follow the instructions in the below link
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

### Post by anchorschmidt on 2010-08-04
Run "alsamixer" without the quotation marks in terminal. Maybe you can adjust more volume levels there.

---

### Post by Barleb on 2010-08-04
3 more hours and we will stick to thus suckin planet ,

maybe the problem is from the speakers :S

---

