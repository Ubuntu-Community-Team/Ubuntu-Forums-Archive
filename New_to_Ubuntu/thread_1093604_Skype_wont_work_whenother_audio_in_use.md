---
title: "Skype wont work whenother audio in use"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by capnthommo on 2009-03-11
hi everybody.  
i have gotten Skype to work but using the static-OSS version when i have Pulse audio installed.  the only hitch is that it only works when other audio devices are not in use. that means actually closed - so i cant listen to music and receive calls at the same time.
what will happen is that the notifier pops up as normal when a call is received but i cant accept the call - it goes to voice mail.  and i cant just pause the music or whatever player, as you would,  it has to be fully closed when the call comes in or it will go to voice mail/rejects.
i've tried using the other versions of skype (standard, static etc) but the OSS version is the only one that will actually function without telling me 'playback problems'.
does anyone know a way round this?  it seems like skype only wants to work in oss even though i am set up with pulse audio (alsa) and so should be using the normal 'static' version (so i thought)-  it just dont seem right.

---

### Post by Troll_the_Great on 2009-03-11
I had kind of a similar problem with pulse audio and I solved it using this tutorial:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I'm using Hardy, so I hope it will work for you too.
Cheers!

---

### Post by capnthommo on 2009-03-11
hi troll and thanks.  that's the how to i have been using too, but i am on intrepid.  i think i will have to check back and make sure i got everything, because it doesnt seem right that it only works with the 'wrong' skype version.  it just seems to me that i should at least be able to pause a music track whilst i take a call.
cheers
nigel

---

### Post by capnthommo on 2009-03-11
yep, all sorted.  it was the part i missed.  works fine now.
so this is all solved now

---

### Post by Troll_the_Great on 2009-03-12
> **capnthommo said:**
> yep, all sorted.  it was the part i missed.  works fine now.
so this is all solved now

Glad to hear you are up and running. You could explain how you fixed your issues, so others with similar problems may solve them easily.
Cheers!

---

### Post by capnthommo on 2009-03-12
hi again,
yes, i missed the part related to skype in _Appendix C_ of the how to at > [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


when i reinstalled skype using the normal static version, not the static OSS version and made sure that i had included the instructions in the section quoted below

> Appendix C: Application Compatibility Guide
This appendix will explain how to configure specific applications that may require manual configuration to work with PulseAudio.

OSS applications: You need to launch the application using the "padsp" wrapper. For more information, see "man padsp".
[COLOR="Purple"]Skype: Open Skype's Options, then go to Sound Devices. You need to set "Sound Out" and "Ringing" to the "pulse" device, and set "Sound In" to the hardware definition of your microphone.[/COLOR] For example, my laptop's microphone is defined as "plughw:I82801DBICH4,0".

i found it all worked fine.  eg at the same time as other audio devices and allowing calls instead of sending to vmail.
cheers
nigel

---

