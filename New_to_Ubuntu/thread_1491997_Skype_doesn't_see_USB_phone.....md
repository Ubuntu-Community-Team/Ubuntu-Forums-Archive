---
title: "Skype doesn't see USB phone...."
date: 2010-05-24
forum: New to Ubuntu
---

### Post by simon0404 on 2010-05-24
Hello,

I can't get my USB phone to work in Skype....

When I go into Skype options, and into the Sound Devices menu, the only option it gives me is "PulseAudio (loca)l"

I have tried looking at USB devices in some other apps, and some do recognise that there is a USB audio device attached (the phone is a simple one with no keypad).....


I'd be most grateful for some assistance to get this working.

Many thanks,
Simon./

---

### Post by Chesamo on 2010-05-24
What are the details of this phone? Is it a telephone in the conventional sense, or simply a microphone and speaker?

---

### Post by simon0404 on 2010-05-24
> **Chesamo said:**
> What are the details of this phone? Is it a telephone in the conventional sense, or simply a microphone and speaker?


It is just a microphone and speaker, which is held like a telephone handset.... no keypad etc...

I used to use it in windows, and it didn't need any software to work....

It is detected in ubuntu, and If I use the volume control, there are settings shown.

---

### Post by simon0404 on 2010-05-25
nudge

---

### Post by michaelA1330 on 2010-05-25
give make and model of phone please ? 
:p

---

### Post by 3rdalbum on 2010-05-25
You need a utility called 'padevchooser'. Install it from Synaptic Package Manager, and then run it by pressing Alt-F2 and typing 'padevchooser'.

Start Skype and start the Test Call. The padevchooser icon in your notification area can be left-clicked, I believe, and then you can change the settings so that audio to and from Skype will go from your handset (which is an ordinary audio device).

All other programs will be unaffected, which I imagine is how you want it.

---

### Post by mikewhatever on 2010-05-25
System->references->Sounds. Is the usb device present in the input/output tabs?

---

### Post by simon0404 on 2010-05-26
> **3rdalbum said:**
> You need a utility called 'padevchooser'. Install it from Synaptic Package Manager, and then run it by pressing Alt-F2 and typing 'padevchooser'.

Start Skype and start the Test Call. The padevchooser icon in your notification area can be left-clicked, I believe, and then you can change the settings so that audio to and from Skype will go from your handset (which is an ordinary audio device).

All other programs will be unaffected, which I imagine is how you want it.

Inside padevchooser there is no option for Skype...... this does briefly flash up for half a second when I load Skype, but disappears again....

The telephone device is found in padevchooser though...

There is no "Sound" option in the preferences menu (I am running 10.04).

The handset does not show a make and model..... just some generic type...

---

### Post by mikewhatever on 2010-05-26
> **simon0404 said:**
> 

There is no "Sound" option in the preferences menu (I am running 10.04).



Whatever, click the speaker icon instead.

---

### Post by simon0404 on 2010-05-26
> **simon0404 said:**
> Inside padevchooser there is no option for Skype...... this does briefly flash up for half a second when I load Skype, but disappears again....

The telephone device is found in padevchooser though...

There is no "Sound" option in the preferences menu (I am running 10.04).

The handset does not show a make and model..... just some generic type...


Nevermind.... I have now managed to set the padevchooser to route the telephone via Skype, using the small logo next to the volume control, and it works fine...

Thanks again for the help,
Simon

---

### Post by astabeno on 2012-01-07
It seems that pdevchoose has been removed in 11.10 is there another way to do this.

---

