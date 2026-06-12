---
title: "[SOLVED] Headphones connected but...."
date: 2008-12-29
forum: New to Ubuntu
---

### Post by kdm on 2008-12-29
I must have read about 100 threads one this but none of them seem to have the same answer, and none seem to be for ibex.

My problem is that when I connect my headphones sound still comes out of the speakers on my laptop. 

Does anyone know a quick fix?

The soundcard is a Realtek ALC883/888

Thanks

---

### Post by jimmy the saint on 2008-12-29
I have a solution, but its kind of a pain.  I have a cord with a male connector on one side and a female on the other plugged into the jack.  Essentially it is an extender.  I got it initially because the front jack was so polluted with system noise.  What I do now is swap the speaker and headphone cords when I want to use the headphones.  Its an extra step, but it works.  The problem is that that audio driver is not recognizing one output and disabling the other.  I am sure that some guru has a better software related hack, but mine worked instantly and requires no expertise!

---

### Post by kdm on 2008-12-29
Thanks jimmythesaint,

but I can't try this yet though as I have some how managed to balls up my sound by (mis-?)following another thread before you responded.  

My volume control on the panel is crossed out and when I click on it I get the following error...
**No volume control GStreamer plugins and/or devices found.**
Any idea what thats about ?

---

### Post by kdm on 2008-12-29
OK, by adding the following line ...
**> options snd-hda-intel model=3stack-6ch**using the following command...**> gksudo gedit /etc/modprobe.d/alsa-base** and then rebooting, my speakers are now muting when I plug in the headphones !!! :D
[COLOR="Red"]
[B]Unfortunately they are also staying muted when I remove the headphones.:(
Is there something obvious I am missing ?[/COLOR][/B]

---

### Post by mal_conductor on 2008-12-29
My laptop does the same thing, and I think it's great.

Double click on the little picture of a speaker at the top, next to the clock.

A window will pop up where you can control the volume of many components of your PC.  Like the speakers, the headphones, the mike... whatever else you have.  You can also mute the speakers or headphone.

Hope it helps

---

### Post by kdm on 2008-12-29
Thanks for the reply mal, 

but alas still no luck ! :(

I get all the options by double clicking the speaker icon, but no matter what setting(s) I try there is still no sound from the speakers.

---

### Post by mal_conductor on 2008-12-29
do you get any sound?

Did you get any sound at anypoint before?

Can you get any sound at all now?

---

### Post by kdm on 2008-12-29
Yip, I am getting sound through my headphones.

If I unplug my headphones though there is no sound through the speakers.  

it seems that my only options are...
To have working speakers which don't mute when I unplug the headphones.
OR
Having working headphones but no speakers.

---

### Post by mal_conductor on 2008-12-29
Any ways I have to go now, but try this:

- do not assume that you have tried all the settings possible.  There is a lot in there.

Open the Alsa Volume Control (i.e. double click the little speaker)

Now Click on "Edit" and the "Preferences"
check every box in there

Now in the playback tab.  Make sure none of the volume controls has a Red X at the bottom

Check that you have the right device showing:  Click on "File" then click on "Change device" and make sure the first button is selected (ALSA Mixer)

Also, go to Options tab and make sure that "Line Out" is selected for Headphone Jack Mode.

---

### Post by mal_conductor on 2008-12-29
> **kdm said:**
> Yip, I am getting sound through my headphones.

If I unplug my headphones though there is no sound through the speakers.  

it seems that my only options are...
To have working speakers which don't mute when I unplug the headphones.
OR
Having working headphones but no speakers.

Oh I see.  Yes this is correct.  You can have the speakers working or not working.  The speakers do not turn off by plugging the headphones in.

---

### Post by kdm on 2008-12-29
Ummm, something odd going on here, I don't have an "edit" 

I wonder does this differ according to the type of soundcard one is using ?

---

### Post by mal_conductor on 2008-12-29
> **kdm said:**
> Ummm, something odd going on here, I don't have an "edit" 

I wonder does this differ according to the type of soundcard one is using ?

This is what mine looks like:
[http://michaeleberhart.net/linux/ubuntu/8_04/alsa_mixer.png](http://michaeleberhart.net/linux/ubuntu/8_04/alsa_mixer.png) 

I don't think this changes according to sound card.  My other Ubuntu install looks the same.

Maybe you need to upgrade the ALSA Mixer to latest version.


There are different versions of ALSA but they seem to go according to the distribution you have.  Look at this:
[http://images.google.ca/images?q=ALSA%20mixer&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=N&tab=wi](http://images.google.ca/images?q=ALSA%20mixer&ie=utf-8&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&sa=N&tab=wi)

---

### Post by kdm on 2008-12-29
[COLOR="Red"]mal_conductor[/COLOR] thanks for all the help !

I think I have finally got this working by 'tricking' ubuntu. 


My Laptop is a Fujitsu Siemens Li1818.
But I have tricked ubuntu(8.10) into looking for the same sound card (HDA Intel : ALC883) by telling it that it is a acer-aspire.

For the possible future benefit of anyone facing the same problems with the same hardware here is how to do it...

Open a terminal and type...
**> gksudo gedit /etc/modprobe.d/alsa-base**
Then type your password (if prompted)

When the document opens up then add the following line to the end of the file...
[B]> # Fix for non-muting of headphones when speakers are present
options snd-hda-intel model=acer-aspire[/B]

Then save and close the file and reboot your computer.  

BingoBango you should then have a responsive headphone jack AND working speakers !!!
Hope this helps someone!  I have just spent the last few hours pulling my hair out !!:)

---

### Post by jimmy the saint on 2008-12-29
Excellent. Make sure to mark the thread as solved so that others with the same issue know there is a solution here.

---

### Post by MT01Neo on 2009-01-21
I've tried the above and it doesn't work on my Acer Apire running Ubuntu 8.1
The internal speakers still work when headphones are plugged in.

Neo

---

