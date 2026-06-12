---
title: "No sound in Amarok"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by PFN on 2009-08-29
I recentely installed Amarok.
But when Iam starting the program it showing an error message like:

"The audio playback device INTEL ICH7 with ALC655(Intel ICH7) does not work.Falling back to default."

It scans the collection properly and showing all the music files.
But on playing any file no sound output at all.Also the progress bar does not show any progress.
All other media players (Totem, Rhythmbox, VLC and Exaile) working properly.
I tried by changing the sound devices and sound themes but no result.
Can anybody help me?
Thanks in advance.

---

### Post by szadek_ on 2009-08-29
> **PFN said:**
> I recentely installed Amarok.
But when Iam starting the program it showing an error message like:

"The audio playback device INTEL ICH7 with ALC655(Intel ICH7) does not work.Falling back to default."

It scans the collection properly and showing all the music files.
But on playing any file no sound output at all.Also the progress bar does not show any progress.
All other media players (Totem, Rhythmbox, VLC and Exaile) working properly.
I tried by changing the sound devices and sound themes but no result.
Can anybody help me?
Thanks in advance.

Try to install phonon-backend-gstreamer , then , in the configuration dialong from amarok , you should have a sound settings button to acess the configuration , choose gstreamer , and then reboot .

But this is for amarok 2.xx , you should advice first which version you are using , settings are different whith different versions of the same application .

Have fun =)

---

### Post by PFN on 2009-08-29
Thanks szadek for your reply. I have phonon-backend-gstreamer is already installed. 
My Amarok version is 2.0.2

I could not find any sound settings in Amarok configuration.

---

### Post by sandyd on 2009-08-29
amarok 2's sound config is now tied into the KDE sound config.
which makes me wonder whats going on here.....

---

### Post by MyR on 2009-08-29
I for one recommend Amarok 1.4

The new version is simply awful. Did some people out to destroy Linux/FOSS take over the project and turn it into garbage, or am I missing something?

---

### Post by PFN on 2009-08-30
After trying so much to find a way to hear the sound of Amarok, and failed,I am finally decided to try the 1.4 version.
Thanks MyR and carlee.
Most people I contacted advised the same.

---

### Post by PFN on 2009-08-30
I just Removed Amarok-2 and installed version-1.4, and it is working well straight from the box without any configuration to be changed. And it is surely the player I am searching for- great performance.

---

### Post by CadetD on 2010-03-20
I had the phonon-backend installed as well and no sound in Amarok. 

The solution was to install phonon-backend-xine. 

Version 2.2.0
Using KDE 4.3.2 (KDE 4.3.2)

---

### Post by kostasiour on 2010-11-04
szadek solution works   just fine as i use ubuntu 9.04 on amaroK 2.3 therefore no need to go back to 1.4 !
install phonon-backend-gstreamer then go to amaroK>Setting>Configure amarok>playback>configure Phonon>Backend > prefer Gstreamer

---

### Post by MyR on 2010-11-04
> **kostasiour said:**
> szadek solution works   just fine as i use ubuntu 9.04 on amaroK 2.3 therefore no need to go back to 1.4 !

Yes, it may work but is the new 2.3 better than 1.4? Or is it still crap?

---

### Post by danthemanvsq on 2010-11-26
> **CadetD said:**
> I had the phonon-backend installed as well and no sound in Amarok. 

The solution was to install phonon-backend-xine. 

Version 2.2.0
Using KDE 4.3.2 (KDE 4.3.2)
This worked for me. Good job! I just opened a terminal and typed in 
sudo apt-get install phonon-backend-xine

---

### Post by ihqtzup on 2011-03-17
> **kostasiour said:**
> szadek solution works   just fine as i use ubuntu 9.04 on amaroK 2.3 therefore no need to go back to 1.4 !
install phonon-backend-gstreamer then go to amaroK>Setting>Configure amarok>playback>configure Phonon>Backend > prefer Gstreamer

Thanks alot! that worked for Ubuntu 10.10 & Amarok 2.3.2

---

