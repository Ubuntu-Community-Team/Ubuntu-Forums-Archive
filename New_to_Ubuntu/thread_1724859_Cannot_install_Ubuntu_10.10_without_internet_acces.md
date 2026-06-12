---
title: "Cannot install Ubuntu 10.10 without internet access?"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-08
I tried to install Ubuntu 10.10 without internet access, but it just froze up mid-install.

Ubuntu cannot be installed without internet access? Is that true?

---

### Post by Bucky Ball on 2011-04-08
No you must have some other problem. ;)

---

### Post by Rasa1111 on 2011-04-08
as Bucky said..
 No, it's not true.

I've installed Ubuntu on many machines that were not online.

---

### Post by Learning Linux 2011 on 2011-04-08
Well, I tried installing it again later WITH internet access and it worked, then I tried installing again WITHOUT internet access to see what would happen, and it froze up again, so clearly the internet access has something to do with something.
It froze up when it got to the point where it downloads stuff during the installation phase.

---

### Post by LostFarmer on 2011-04-08
> but it just froze up mid-install  can you explain more ?   Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) , go down to#4 'install it' and click on show me, how far do you get ?


Edit:
Disregard , I see you posted right be for me.

---

### Post by Learning Linux 2011 on 2011-04-08
> **LostFarmer said:**
> can you explain more ?   Go to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) , go down to#4 'install it' and click on show me, how far do you get ?


Edit:
Disregard , I see you posted right be for me.


Around step #6, it asks you to type in the city where you are located.  I tried to type mine in, and I think I figured out that it then looks for a list of cities, but since I wasn't connected to the internet, it must have gotten confused and froze up at that point.  I only typed one letter of the city before it froze.

---

### Post by Rasa1111 on 2011-04-08
> **Learning Linux 2011 said:**
> Around step #6, it asks you to type in the city where you are located.  I tried to type mine in, and I think I figured out that it then looks for a list of cities, but since I wasn't connected to the internet, it must have gotten confused and froze up at that point.  I only typed one letter of the city before it froze.

Well that can't be it. 
As Ive said..
I have installed Ubuntu on machines with no internet access, with no problems.

 a city is not required for an install.
Only a time zone.. which your PC should already be "attuned" to,
therefor, the correct timezone should already be selected, online or not.  

 No "typing in" of any city is required,
If the "map" is not already on your time zone, (which it always has been in my experience)
you just have to click on the map, wherever you happen to be,
and your time zone will be set. 

 Perhaps keep an eye on the "download updates while installing",
seen here~ [IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_02_medium.jpg[/IMG] and make sure it is Un-checked before going any further.

Don't know if that has any effect on your problem or not..
But after 40+ Ubuntu installs on machines of all kinds...
I know for a fact that one does not need internet access to install it.

---

### Post by Bucky Ball on 2011-04-08
As Rasa says, make sure you have not ticked anything that requires you to download packages during the install. 

You can install whether on or offline. If on you'll get your updates as part of the process, if off you can pick them up later. Easy.

---

### Post by Learning Linux 2011 on 2011-04-09
Ahh, ok, thanks all.  I think what happened is that I chose to download updates during the install, but didn't have the network cable plugged in, so the installation froze up during that download phase.

I tried it again today making sure not to check the download options and the install went through.

---

### Post by Learning Linux 2011 on 2011-04-09
Incidentally, does anyone know if the "install third party software" option requires internet access?
i.e. is the third party software downloaded, or is it on the CD?

---

### Post by Rasa1111 on 2011-04-09
> **Learning Linux 2011 said:**
> Incidentally, does anyone know if the "install third party software" option requires internet access?
i.e. is the third party software downloaded, or is it on the CD?

Glad ya figured it out. :)

Re: 3rd party software..
I honestly am not sure what that does, 
I have chosen both options in the past..
To install 3rd party software while installing, 
and to not install it..
and honestly.. Ive never seen a difference. lol

 If I recall correctly..
That 3rd party software is supposed to get you certain codecs to play mp3's, etc.. 

However,
 The times I have installed it,
I have found that I still need to install ubuntu-restricted-extras to play my music/video files..

So, Now I usually do not even bother checking that option. 

Not sure if it has to download it, or if it's on the disc..
But going on what I do know about 3rd party software...
It probably has to be downloaded, and probably is not on the disc itself. 

 Though I could be wrong. lol

---

### Post by Learning Linux 2011 on 2011-04-09
> **Rasa1111 said:**
> Glad ya figured it out. :)

Re: 3rd party software..
I honestly am not sure what that does, 
I have chosen both options in the past..
To install 3rd party software while installing, 
and to not install it..
and honestly.. Ive never seen a difference. lol

 If I recall correctly..
That 3rd party software is supposed to get you certain codecs to play mp3's, etc.. 

However,
 The times I have installed it,
I have found that I still need to install ubuntu-restricted-extras to play my music/video files..

So, Now I usually do not even bother checking that option. 

Not sure if it has to download it, or if it's on the disc..
But going on what I do know about 3rd party software...
It probably has to be downloaded, and probably is not on the disc itself. 

 Though I could be wrong. lol

Yeah, that seems to be my experience too.  That option doesn't seem to do much.  You still need to update after install and explicitly install the restricted extras it seems.

---

