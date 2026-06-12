---
title: "Sound issues making me go steadily nuts"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-17
Hi, I have tried everything. I simply cannot get any sound on ubuntu 8.10

The thing is that I have tinkered a lot with the settings - is there a way to sort of re-set the sound settings?

Any easy to understand tutorials would be gratefully received!!

thanks very much!

Lister :)

---

### Post by camaron1 on 2009-11-17
> **listerdl said:**
> Hi, I have tried everything. I simply cannot get any sound on ubuntu 8.10

The thing is that I have tinkered a lot with the settings - is there a way to sort of re-set the sound settings?

Any easy to understand tutorials would be gratefully received!!

thanks very much!

Lister :)
I don't know about resetting to defaults but maybe a bit more of information would be useful,

Did you ever have sound? only one soundcard or more? is it ubuntu 8.10 or 9.10?

---

### Post by listerdl on 2009-11-17
Hi thanks yes I used to have sound and then it disapeared. My system is Ubuntu/8.10 (intrepid).

Any assistance would be helpful - if there is a way to re-install the sound that would be ideal.

Should all sound come from ALSA?

---

### Post by camaron1 on 2009-11-17
> **listerdl said:**
> Hi thanks yes I used to have sound and then it disapeared. My system is Ubuntu/8.10 (intrepid).

Any assistance would be helpful - if there is a way to re-install the sound that would be ideal.

Should all sound come from ALSA?

The sound comes from alsa (so to speak) but is managed bu pulseaudio. Can you associate any event to your sound stopping working?

---

### Post by listerdl on 2009-11-17
Thanks.

The only event I can think of is trying to get skype to work - or, an upgrade....sorry that I cant be more specific - ideally I guess I am looking for a sort of clean re-install of just the sound if such an option was available...thanks again for all help!

---

### Post by camaron1 on 2009-11-17
> **listerdl said:**
> Thanks.

The only event I can think of is trying to get skype to work - or, an upgrade....sorry that I cant be more specific - ideally I guess I am looking for a sort of clean re-install of just the sound if such an option was available...thanks again for all help!

Could you install if already not installed GNOME-ALSA MIXER and PADEVCHOOSER? (This one will appear ander Sound and Video as PulseAudio Device Chooser). Open both and make sure you don't have anything muted, that your card is recongnized and the right one is chosen as default.... PulseAudio Device will appear on the top panel on the right. Click on Volume Control.

Tell us how you get on

---

### Post by listerdl on 2009-11-17
> **camaron1 said:**
> Could you install if already not installed GNOME-ALSA MIXER and PADEVCHOOSER? (This one will appear ander Sound and Video as PulseAudio Device Chooser). Open both and make sure you don't have anything muted, that your card is recongnized and the right one is chosen as default.... PulseAudio Device will appear on the top panel on the right. Click on Volume Control.

Tell us how you get on

Thanks for the advice - 

One question please...: you mention to install GNOME-ALSA MIXER and PADEVCHOOSER which I dont believe I have. How do I do this? Via terminal or via synaptic?

Thanks

---

### Post by camaron1 on 2009-11-17
> How do I do this? Via terminal or via synaptic?

Thanks 	

They are both the same.

On Terminal:

sudo apt-get install gnome-alsamixer padevchooser 

Or open Synaptic search for them, tick them and install them.

---

### Post by listerdl on 2009-11-17
> **camaron1 said:**
> They are both the same.

On Terminal:

sudo apt-get install gnome-alsamixer padevchooser 

Or open Synaptic search for them, tick them and install them.

thanks ill let you know how i got on - appreciate your help

---

### Post by Dermot Doyle on 2009-11-17
Hi, you may well get better and more learned advice than mine, but I had endless problems with sound on my Dell Inspiron pre-loaded with 8.04. Everything worked perfectly until I downloaded some updates, one of which (without me knowing) set my computer to open on the next available kernel by default. I spent days on this forum following every thread including someone with an identical computer and problem and never sorted it (nor did she). In the end someone suggested I download Start-up Manager and set my previous kernel as default and since then everything has worked as it should. You mentioned a possible upgrade as causing the problem so I thought I'd throw this in.
Good luck.

---

### Post by camaron1 on 2009-11-17
> Hi, you may well get better and more learned advice than mine, but I had endless problems with sound on my Dell Inspiron pre-loaded with 8.04. Everything worked perfectly until I downloaded some updates, one of which (without me knowing) set my computer to open on the next available kernel by default. I spent days on this forum following every thread including someone with an identical computer and problem and never sorted it (nor did she). In the end someone suggested I download Start-up Manager and set my previous kernel as default and since then everything has worked as it should. You mentioned a possible upgrade as causing the problem so I thought I'd throw this in.
Good luck.     Sure, try this too, it'll take you two minutes.

---

### Post by sandyd on 2009-11-17
> **listerdl said:**
> Thanks.

The only event I can think of is trying to get skype to work - or, an upgrade....sorry that I cant be more specific - ideally I guess I am looking for a sort of clean re-install of just the sound if such an option was available...thanks again for all help!
have you tried using pure alsa? (not through pulseaudio)

---

### Post by listerdl on 2009-11-17
I have done this: > instal GNOME-ALSA MIXER and PADEVCHOOSER (This one will appear ander Sound and Video as PulseAudio Device Chooser). Open both and make sure you don't have anything muted, that your card is recongnized and the right one is chosen as default.... PulseAudio Device will appear on the top panel on the right. Click on Volume Control.

How is the above accessible, do you mean System > Sounds ?

THANKS

---

### Post by listerdl on 2009-11-17
> **carlee said:**
> have you tried using pure alsa? (not through pulseaudio)

Yes, no joy.

I have I downloaded the Start-up Manager and as suggested I can try to set my previous kernel as default but I am worried that i will use my thunderbird emails and folders?

---

### Post by camaron1 on 2009-11-17
> **listerdl said:**
> I have done this: > instal GNOME-ALSA MIXER and PADEVCHOOSER (This one will appear ander Sound and Video as PulseAudio Device Chooser). Open both and make sure you don't have anything muted, that your card is recongnized and the right one is chosen as default.... PulseAudio Device will appear on the top panel on the right. Click on Volume Control.

How is the above accessible, do you mean System > Sounds ?

THANKS

You'll find them under APPLICATIONS>SOUND AND VIDEO. Remember Pulseaudio Device Chooser won't open directly. Look for the icon on the top panel on the right. What you are looking for is: 
-confirmation that your soundcard is there.
-confirmation that your soundcard is chosen as default.
-confirmation that the volume is not muted.

Tell us how you get on

---

### Post by camaron1 on 2009-11-17
> **listerdl said:**
> Yes, no joy.

I have I downloaded the Start-up Manager and as suggested I can try to set my previous kernel as default but I am worried that i will use my thunderbird emails and folders?

No, what he suggested is that the older kernel might already be set as default by mistake and if so you should change back to the most recent one.

---

### Post by listerdl on 2009-11-17
> **camaron1 said:**
> You'll find them under APPLICATIONS>SOUND AND VIDEO. Remember Pulseaudio Device Chooser won't open directly. Look for the icon on the top panel on the right. What you are looking for is: 
-confirmation that your soundcard is there.
-confirmation that your soundcard is chosen as default.
-confirmation that the volume is not muted.

Tell us how you get on

OK, I did the above and the jack lead wire appeared on the top right....and this is what happened:

Default Server: nothing checked
Default Sink: nothing checked
Default Source: nothing checked

Pulse Audio Manager is all greyed out.

The volume control simply refuses to open and it is all greyed out with the message in a pop-up - connection failed: connection refused

The same message applies for all other options.....

:confused:

------------------ ALSO ---------------------------------



I found this on the internet that might apply to me. Basically it seems that Pulse Adio just doesnt work for me or that it has become corrupt somewhere along the way. "By default Ubuntu 8.10 comes with Pulse Audio and most users start complaining about pulse audio so if you don&#8217;t want to use Pulse Audio you can remove using the following procedure.

```
Remove the required packages

    sudo apt-get remove pulseaudio

    sudo apt-get install esound

Now remove the 70pulseaudio file

Before removing make a backup of this file

    sudo cp /etc/X11/Xsession.d/70pulseaudio /etc/X11/Xsession.d/70pulseaudio.back

    sudo rm /etc/X11/Xsession.d/70pulseaudio

Gnome Preferences

Now go to System -> Preferences -> Sound

Make sure they are all set to &#8216;Autodetect&#8217;.

The only one you will have to set manually to ALSA is &#8216;Sound Capture&#8217; under &#8216;Audio Conferencing&#8217;.

Note:-At this point Pulseaudio is now nolonger an option under these drop menus.

Gnome Sessions

Go to System -> Preferences -> Sessions

Deselected or Remove the Pulseaudio Manager

Finally Your asoundrc&#8217;s under your Home Directory are still configured for Pulse.

Go to your home directory using the following command

cd ~

cp .asound* yourfilename

    rm .asound*

One this is done your back to ALSA&#8217;s default configuration.
```

Does that sound like a plan?

---

### Post by camaron1 on 2009-11-17
```
OK, I did the above and the jack lead wire appeared on the top right....and this is what happened:

Default Server: nothing checked
Default Sink: nothing checked
Default Source: nothing checked

Pulse Audio Manager is all greyed out.

The volume control simply refuses to open and it is all greyed out with the message in a pop-up - connection failed: connection refused

The same message applies for all other options.....
```

Uff, that sounds pretty serious...

It seems that pulseaudio is totally screwed. My sugestion here would be to get rid of pulseaudio and and use ALSA direcly as sugested before. Before you do this (if you want to do it) you might want to reboot and and check that it is all the same again...

---

### Post by listerdl on 2009-11-17
I have now removed Pulse Audio - but have got stuck at this stage: ".........Finally Your asoundrc&#8217;s under your Home Directory are still configured for Pulse.......Go to your home directory using the following command cd ~ cp .asound* yourfilename     rm .asound* One this is done your back to ALSA&#8217;s default configuration...."

Can someone explain this please "Go to your home directory using the following command cd ~ cp .asound*"

thanks!

---

### Post by 5mattyb5 on 2009-11-17
Do you have weak hardware?  I'm only asking because there have been many advancements from intrepid to karmic especially with pulseaudio, maybe a system upgrade is in order.  If you have the system for it, however it runs on a significantly small system.

Maybe try "killall pulseaudio" this will simply restart it.

Another option is to load a live disc and see if you have sound there, maybe you actually have hardwae issues, I know it seems unlikely but worth a try.

otherwise yes purging pulse audio will likely help as I remember I had to revert to esound in intrepid.

---

### Post by camaron1 on 2009-11-17
mistake...

---

### Post by listerdl on 2009-11-17
to be honest this is a real drag and certainly a reason to get fustrated!!

why is it soooo difficult...??

if i re-install will that solve the issue or is it back to windows and vista for sound? Sad i know but I cant spend months fixing this issue....,thanks!

do you think that all options are now over and it is time for a re-install?

---

### Post by camaron1 on 2009-11-17
Copy and paste this on a terminal: 
sudo gedit /etc/pulse/default.pa

On the text editor go to preferences and choose to display line numbers. On line 45-46 you should probably see:
45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove the sign **#** from both. Save the document and reboot. Tell us what happens.

How did you set ALSA by the way?

---

### Post by camaron1 on 2009-11-17
Some thoughts:

-Your sound worked before so it should work again. 
-If sound is the only reason to go back to Windows persevere because there is always a solution. (From own experience you are totally right, sound is a pain in linux, but when it works -and it can work- works great)
-If you are going to reinstall in the end the last version of ubuntu is 9.10 which I'm afraid to say has failed many people with the sound (myself included again) but that can usually be resolved by removing pulseaudio or more cleanly by changing the two config. lines I just gave you.

All the best (time for bed now...);)

PD. Again, if you are going to re-install do a separate partition for your root and home folder (i've you've not done so yet).Apart from protecting your data it will make future installs very easy and fast. Lots of guides around on how to do this.

---

### Post by listerdl on 2009-11-18
> **camaron1 said:**
> Copy and paste this on a terminal: 
sudo gedit /etc/pulse/default.pa

On the text editor go to preferences and choose to display line numbers. On line 45-46 you should probably see:
45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove the sign **#** from both. Save the document and reboot. Tell us what happens.

How did you set ALSA by the way?

Changing the # as instructed did nothing after reboot - still no sound. Even the PulseAudio Applet did nothing.

Setting everything to ASLA - likewise - nothing happened.

Is there a way to re-install PulseAudio? I think that I might have changed the settings.

thanks

---

### Post by camaron1 on 2009-11-18
> Changing the # as instructed did nothing after reboot - still no sound. Even the PulseAudio Applet did nothing.

Setting everything to ASLA - likewise - nothing happened.

Is there a way to re-install PulseAudio? I think that I might have changed the settings.


Just install it again via Synaptic

---

### Post by listerdl on 2009-11-18
I have re-installed and still nothing.

I think we have reached the end of the road here....

Probably best to simply re-install. It is a shame that it is so difficult!!

---

### Post by camaron1 on 2009-11-18
> **listerdl said:**
> I have re-installed and still nothing.

I think we have reached the end of the road here....

Probably best to simply re-install. It is a shame that it is so difficult!!

Sorry, I tried my best... there are so many variables with bloody sound in linux.
Do you have a separate home partition to make the re-install faster and safer?

---

### Post by listerdl on 2009-11-18
Thanks a lot for your help. I think this is what I will do - I will firstly re-install windows, (simply because I need some windows programs that work better in a windows environment).

After having installed windows, I will also install the latest version of ubuntu 9.10 and hope that it works with my machine.

So, basically, with a dual boot, if the sound issue continues then at least I will have windows I guess....

Let me ask you two final questions if I may:

1. Will a clean re-isntall give me a 'clean-slate' - i.e. a completey new 'factory' settings? (I guess I will find out by trying but its good to know beforehand!)

2. If the above is correct then I imagine it might be better to fix my sound problems since there is a platform to work from?....My current set-up is probably so messed up that there is no place to really start....

Thanks again for your help!

---

### Post by camaron1 on 2009-11-18
> **listerdl said:**
> Thanks a lot for your help. I think this is what I will do - I will firstly re-install windows, (simply because I need some windows programs that work better in a windows environment).

After having installed windows, I will also install the latest version of ubuntu 9.10 and hope that it works with my machine.

So, basically, with a dual boot, if the sound issue continues then at least I will have windows I guess....

Let me ask you two final questions if I may:

1. Will a clean re-isntall give me a 'clean-slate' - i.e. a completey new 'factory' settings? (I guess I will find out by trying but its good to know beforehand!)

2. If the above is correct then I imagine it might be better to fix my sound problems since there is a platform to work from?....My current set-up is probably so messed up that there is no place to really start....

Thanks again for your help!
1- Yes it will
2- you're probably right there

A couple of observations: as I said before 9.10 has broken the sound to quite a few people so be prepare for a possible new battle. If this happens my suggestion to do (in this order are:
a-Check the volume apple on the top right as it seems that by default it is muted.
b-Change the two configuragion lines I gave you and reboot
c and last-Completely remove Pulseaudio and reboot.

Also, at danger of being repetitive go for a separate home partition. If you don't know how to do this there is tons of documentation on the internet or theses forums, or just start a new thread on this. Other than that you are right: install windows first (If you have the option go for Windows 7 which -I'm afraid to say- it is true is the best Windows so far) and then Ubuntu.

Good luck

---

### Post by listerdl on 2009-11-26
............and after all that I discovered that it was a hardware issue.....the actual sound board was damaged...

aahhh...

the countless hours...

thanks anyway!

---

