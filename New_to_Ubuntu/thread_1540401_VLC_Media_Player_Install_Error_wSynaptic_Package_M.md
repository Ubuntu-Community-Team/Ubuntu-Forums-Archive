---
title: "VLC Media Player Install Error w/Synaptic Package Manger"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Tisiphone on 2010-07-27
Right off the bat, I am going to apologize since I am totally green with Unbuntu 10.04 and its workings. In the process of following the instructions to setting up my VLC player, I received the following message that I have made a screen shot for your viewing pleasure. 

I have been a Windows slave for many a moon and I really am lost with in this change that I felt was necessary in trying to configure a set up that works for me. Any help with this error either via an earlier thread that I missed while researching or a link that can help is appreciated.

---

### Post by Tisiphone on 2010-07-27
I have solved this issue, but now I have sound with no video. I will continue my searching for an answer, but any guidance is appreciated from this n00b!

;)

---

### Post by OnlineBuddy on 2010-07-27
sound..no video....hmm!!
.
could you tell me which file type you are trying to play...
.
also if you are using synaptic there shoudn't be any problem..
.
**MY SUGGESTION-** install medibuntu repositories...then install mplayer...than install all(including non-free codecs)...all done now you should be able to run any format on earth!!:smile:

---

### Post by linux18 on 2010-07-27
Synaptic could use some cleaning, it could be breaking packages.

```

 sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"

```

then do the medibuntu

---

### Post by Tisiphone on 2010-07-27
Thank you for the suggestions. I have added Medibuntu and unfortunately I am still having video issues.

I am trying to run .avi files and I get wonderful sound, still a black screen. 

I tried mplayer and VLC, so am back to reading some more. 

:KS

---

### Post by sandyd on 2010-07-27
> **Tisiphone said:**
> Thank you for the suggestions. I have added Medibuntu and unfortunately I am still having video issues.

I am trying to run .avi files and I get wonderful sound, still a black screen. 

I tried mplayer and VLC, so am back to reading some more. 

:KS
a). What codec is the avi file in? (VLC -> Tools -> Codec Info)
b). installed video drivers? (System -> Adminsitration -> Hardware Drivers)
c). What video rendering options are on? (VLC -> Tools -> Prefrences -> Video). Try if setting the output to different values to get it running

---

### Post by 3rdalbum on 2010-07-27
> **Tisiphone said:**
> Thank you for the suggestions. I have added Medibuntu and unfortunately I am still having video issues.

Merely 'adding Medibuntu' doesn't actually do anything other than tell Ubuntu that it can get software from Medibuntu. Have you installed the 'non-free-codecs' package in Synaptic Package Manager? (it's provided by the Medibuntu repository).

---

### Post by Tisiphone on 2010-07-27
> **carlee said:**
> a). What codec is the avi file in? (VLC -> Tools -> Codec Info)
b). installed video drivers? (System -> Adminsitration -> Hardware Drivers)
c). What video rendering options are on? (VLC -> Tools -> Prefrences -> Video). Try if setting the output to different values to get it running

I have tried those options, but I believe that I have no video drivers installed that will do the trick. I have a Toshiba Satellite and I will have to find those. When I went to Hardware Drivers it said - "No proprietary driver are in use on this system" - so am going to work on that to see if that resolves the issue.

I thought I had them installed, but I am guessing that I might be what's wrong with this or that for some reason they are not being recognized.

Will keep folks posted!!

Thank you everyone, you have been a ton of help.;)

---

### Post by Tisiphone on 2010-07-27
> **3rdalbum said:**
> Merely 'adding Medibuntu' doesn't actually do anything other than tell Ubuntu that it can get software from Medibuntu. Have you installed the 'non-free-codecs' package in Synaptic Package Manager? (it's provided by the Medibuntu repository).


Yes, I went to the repository and have added codecs. I think that right now it's that either the video drivers are not being recognized or that I did not do a proper install after all.

---

### Post by sandyd on 2010-07-27
> **Tisiphone said:**
> Yes, I went to the repository and have added codecs. I think that right now it's that either the video drivers are not being recognized or that I did not do a proper install after all.
try the unstripped ffmpeg codecs then.

---

