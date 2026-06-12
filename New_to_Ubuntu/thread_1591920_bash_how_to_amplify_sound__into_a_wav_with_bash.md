---
title: "bash: how to amplify sound  into a wav with bash?"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-10
Hello,

I would like to amplify lot of files, for higher soudn volume. How could a command does that ? 
thanks

---

### Post by HermanAB on 2010-10-10
Howdy, 

Read the sox man page and google for some howtos on sox.

---

### Post by Jose Catre-Vandis on 2010-10-10
Something like this:
```
sox infile.wav outfile.wav vol 3 dB
```
adjust db level accordingly...

---

### Post by honeybear on 2010-10-11
> **Jose Catre-Vandis said:**
> Something like this:
```
sox infile.wav outfile.wav vol 3 dB
```
adjust db level accordingly...

wow i did not know sox. sox is amazing program, looks so siplme 

i believed to use mencoder; so very complex

---

### Post by Old_Man_Unix on 2010-10-11
This isn't the best way.  The **vol **effect in *sox* provides no clipping protection.  If you insist on using the **vol** effect, in order to ensure that you don't induce clipping,   it's imperative to do a **stat** on the input file first to determine the maximum level.  But I really suggest that you don't use **vol** at all.

If you simply want to "normalize" your file to zero dB  - or to any other arbitrary level - much better for your purposes would be the **gain -n** effect in *sox*.  The **gain -n** effect automatically guards against clipping. 

Foe example:

```
sox infile outfile gain -n
 
```normalizes  *outfile* to zero dB without clipping.  

 ```
sox infile outfile gain -n -3
```normalizes *outfile* to -3 dB without clipping.


Finally, until you are comfortable with using audio effects,  suggest you archive a copy of all your original audio files.   *sox* is a very powerful program but there is a learning curve if you are a beginner. 

Good luck.:guitar:

---

### Post by andrew.46 on 2010-10-14
Hi Old_Man,

> **Old_Man_Unix said:**
>  If you insist on using the **vol** effect, in order to ensure that you don't induce clipping,   it's imperative to do a **stat** on the input file first to determine the maximum level.  But I really suggest that you don't use **vol** at all.

I have used SoX to increase the volume of DVD audio for some time now, [see here]("http://www.andrews-corner.org/fist.html#audio") for a typical usage. Can I ask why you advise against its use? My understanding is that overzealous use of 'gain' can also result in clipping. I ask no because I doubt you but because I am a newish user of sox and quite frankly I have not used 'gain' before :).

Andrew

---

### Post by honeybear on 2010-10-15
thank you very much !!

--
air breathing? what 'did you mean ? :confused:

---

### Post by andrew.46 on 2010-10-15
Hi honeybear,

> **honeybear said:**
> --
air breathing? what 'did you mean ? :confused:

My signature quotes Morpheus speaking to Neo in the sparring scene in The Matrix :).

Andrew

---

### Post by Old_Man_Unix on 2010-10-16
> **andrew.46 said:**
> Hi Old_Man,



I have used SoX to increase the volume of DVD audio for some time now, [see here]("http://www.andrews-corner.org/fist.html#audio") for a typical usage. Can I ask why you advise against its use? My understanding is that overzealous use of 'gain' can also result in clipping. I ask no because I doubt you but because I am a newish user of sox and quite frankly I have not used 'gain' before :).

Andrew

I'll try to explain, but when talking about audio, verbal descriptions  sometimes don't cut it. So I hope this is understandable to you. 

In music and video soundtracks,  distortion of different kinds may be purposely part of the original audio.   Musicians sometimes call this "fuzz".  This is also sometimes called "analog clipping" although that is not accurate.  This  isn't what we are talking about here

  What we mean here is that the digital audio range *at some point* exceeds the range of the digital audio processor.   Since digital audio cannot exceed 0dB, those instances are simply truncated to 0 dB, resulting in the audible distortion that is called clipping. 

As I said, the **vol** effect does not protect against clipping.  It simply increase the level of the  digital audio by whatever factor you choose.  If the level *at any point* would be above 0dB, it simply gets truncated, just as any other digital audio  representation would be truncated in the same situation.  

 In sox, the **gain-n** effect protects against that. 

Very short instances of clipping, e.g., a drum hit, are effectively inaudible to a casual listener.  But continued clipping results in loss of dynamic range and what many listeners would consider harsh and fatiguing sound.  On the other hand, some people just don't hear clipping at all.  In fact, because of the current crappy practices in music and video soundtrack recording, a lot of people think that is the way it is supposed to sound.

---

### Post by Jose Catre-Vandis on 2010-10-17
Of course, if you are happy to do one file at a time with a GUI, use Audacity

---

