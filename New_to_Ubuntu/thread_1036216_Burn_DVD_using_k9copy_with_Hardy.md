---
title: "Burn DVD using k9copy with Hardy"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-01-10
I am trying to burn a DVD copy using k9copy, DVD drive to same in Hardy. I receive the same error (posted). I remember that I was able to change the recording speed to a low setting of 4.7 in a drop down option window. I tried to change the speed manually, as the only option after this install was 'default'. I get the same thing after trying to re-installing k9copy. The DVD player plays the DVD original fine. I assume all the correct codecs are installed... Any Ideas how to get this to work?

---

### Post by wolfen69 on 2009-01-10
this happens when you insert a blank dvd? try another one.

btw, reinstalling does not do much unless you do
```
sudo apt-get clean && sudo apt-get autoremove
``` 
right after uninstalling an app.
*then* reinstall.

---

### Post by namdung on 2009-01-10
Seems like an application error.

Are u trying to convert DVD9 to DVD5? In that case try DVD95 converter.

If just burning a DVD, then try Brasero, K3B etc

Which Ubuntu Version?
Which K9Copy version?

---

### Post by CoCoKnots on 2009-01-10
> **namdung said:**
> Seems like an application error.

Are u trying to convert DVD9 to DVD5? In that case try DVD95 converter.

If just burning a DVD, then try Brasero, K3B etc

Which Ubuntu Version?
Which K9Copy version?

Hardy 8.04.1
k9copy 1.2.3. using KDE 3.5.10

I had this all working at one time... Then I needed to re-install ubuntu from scratch (due to an error) going back to 7.10 then upgrade again to 8.04. I never had this problem before though.:confused:

---

### Post by CoCoKnots on 2009-01-10
> **wolfen69 said:**
> this happens when you insert a blank dvd? try another one.

btw, reinstalling does not do much unless you do
```
sudo apt-get clean && sudo apt-get autoremove
``` 
right after uninstalling an app.
*then* reinstall.

No Luck... I did this & re-booted. I ran k9copy & it looked like it was going to work. When it finished the burn process, it came back as a 'Blank Disc'. I really don't understand what is going on here???

---

### Post by CoCoKnots on 2009-01-10
Could this problem be related to something happening between the download & that of the 8.04 ?... Perhaps a folder or file missing?

---

### Post by CoCoKnots on 2009-01-10
I installed K3B & used K9Copy to copy to iso file & K3B to burn DVD without success. I have also tried K9Copy to Copy & burn on the same DVD. That didn't work either. Does anyone else have thoughts about what I could try ?

---

### Post by wolfen69 on 2009-01-11
> **CoCoKnots said:**
> I installed K3B & used K9Copy to copy to iso file & K3B to burn DVD without success. I have also tried K9Copy to Copy & burn on the same DVD. That didn't work either. Does anyone else have thoughts about what I could try ?

perhaps try intrepid ibex? sometimes certain operating systems just will not work no matter what you try. if it works (8.10) it's worth doing. just remember to do all updates before any configuring.

---

### Post by TransitMan on 2009-01-11
Are your setting set to burn to a disc in your burner, or is it set to a file on your drive?
If the later, then that is why you are getting "blank disc" burnes.
Check your settings to make sure k9copy is going to burn to the designated burner with a blank disc in the drive.

---

### Post by CoCoKnots on 2009-01-11
> **TransitMan said:**
> Are your setting set to burn to a disc in your burner, or is it set to a file on your drive?
If the later, then that is why you are getting "blank disc" burnes.
Check your settings to make sure k9copy is going to burn to the designated burner with a blank disc in the drive.

I used k9copy 'DVD drive to DVD drive' first & it failed to write after indicating  it had processed the entire copy procedure. I then tried k9copy again writing to an ISO file on the hard drive in the video file, (where it still resides). I then tried to burn it to a DVD using K3B... & again it shows that it moves slowly through the entire burning process then returns a blank disc. However, even though it says it is blank, it has an error if I try to re-use the disc a second time.

---

### Post by halitech on 2009-01-11
well, I know you probably don't want to think about it but possibly your drive is on its way out the door or it doesn't like the media for some reason. Do you dual boot this computer? if you do, try burning something in windows. if not, do you have another machine you could swap it into to test?

---

### Post by CoCoKnots on 2009-01-11
> **halitech said:**
> well, I know you probably don't want to think about it but possibly your drive is on its way out the door or it doesn't like the media for some reason. Do you dual boot this computer? if you do, try burning something in windows. if not, do you have another machine you could swap it into to test?

I do not have another computer to test the DVD drive in. It burns photos OK & was copying movies fine until I upgraded to 8.04 this last time. I have gone thru 7.10 (worked fine) then 8.04 (worked fine) then 8.10 when I ran into an issue running a program I need for work, so & went back to 8.04 (where I am now) & now k9copy or K3B will not burn.

---

### Post by TransitMan on 2009-01-11
In K3b, are you burning the .iso as a Data file or Burn DVD ISO Image?
In K3b, what speed are you burning at? 
If faster than 4x or 8x, this may be where the problem lies. Try to burn at the slowest speed setting to see if it helps.

---

### Post by CoCoKnots on 2009-01-11
> **TransitMan said:**
> In K3b, are you burning the .iso as a Data file or Burn DVD ISO Image?
In K3b, what speed are you burning at? 
If faster than 4x or 8x, this may be where the problem lies. Try to burn at the slowest speed setting to see if it helps.

I'm burning as an IOS image at 2.4 speed. I was told once to burn as slow as possible. Another reason why this doesn't make since... I'm trying to do this correctly... Checking & double checking my settings.

---

### Post by TransitMan on 2009-01-11
Are you using a good brand of DVD blank discs?
Are they compatable with your burner? Note, some brands of burners are picky over what discs are used to burn with.

How about trying using Nero for Linux to burn the .iso files. The download can be found here - [http://www.nero.com/enu/support-linux3.html](http://www.nero.com/enu/support-linux3.html)
Click on the 15 day trial link and see how it goes.

I have read on problems with K3b not working right, but I cannot offer any other work around other than what has been given.

If you want to continue trying K3b, go to Synaptic, search for K3b, and check remove completely. Once that is done, close Synaptic and open a console and type in ```
sudo apt-get autoremove
``` followed by your password. This clean out the dependancies for K3b.
The reopen Synaptic, once again search for K3b and do an install. It will install K3b and all dependencies needed for K3b. While not required in Linux, I would reboot and then try K3b again.

---

### Post by CoCoKnots on 2009-01-11
> **TransitMan said:**
> Are you using a good brand of DVD blank discs?
Are they compatable with your burner? Note, some brands of burners are picky over what discs are used to burn with.

How about trying using Nero for Linux to burn the .iso files. The download can be found here - [http://www.nero.com/enu/support-linux3.html](http://www.nero.com/enu/support-linux3.html)
Click on the 15 day trial link and see how it goes.

I have read on problems with K3b not working right, but I cannot offer any other work around other than what has been given.

If you want to continue trying K3b, go to Synaptic, search for K3b, and check remove completely. Once that is done, close Synaptic and open a console and type in {CODE]sudo apt-get autoremove[/CODE] followed by your password. This clean out the dependancies for K3b.
The reopen Synaptic, once again search for K3b and do an install. It will install K3b and all dependencies needed for K3b. While not required in Linux, I would reboot and then try K3b again.

Yes, I had heard this before about the quality of the disc. I remember something about an issue with Sony disc & a problem with copying. So I use Memorex as a rule. I just finished installing K3B yesterday as a work around this problem. Do you think it would do any good to delete it & start over ?

---

### Post by TransitMan on 2009-01-11
No. Leave K3b there and see if it works.
Also think about giving Nero a try. I keep it as a back-up to K3b, just-in-case.

---

### Post by CoCoKnots on 2009-01-11
> **TransitMan said:**
> No. Leave K3b there and see if it works.
Also think about giving Nero a try. I keep it as a back-up to K3b, just-in-case.

Thanks, I'll give that a try...

---

### Post by halitech on 2009-01-12
> **CoCoKnots said:**
> I do not have another computer to test the DVD drive in. It burns photos OK & was copying movies fine until I upgraded to 8.04 this last time. I have gone thru 7.10 (worked fine) then 8.04 (worked fine) then 8.10 when I ran into an issue running a program I need for work, so & went back to 8.04 (where I am now) & now k9copy or K3B will not burn.

when you are burning photos, are you burning them on cd or dvd? There are different lasers in use depending on what you are doing so just because it will write a cd doesn't mean the dvd side is still good. And it may just be a case of bad timing on the reinstall and drive going bad.

---

### Post by CoCoKnots on 2009-01-12
> **halitech said:**
> when you are burning photos, are you burning them on cd or dvd? There are different lasers in use depending on what you are doing so just because it will write a cd doesn't mean the dvd side is still good. And it may just be a case of bad timing on the reinstall and drive going bad.

Are you saying a better dest of the would be to try burning a photo on a DVD ? Will that automatically dictate the same lasers as those used to burn a movie ???

---

### Post by CoCoKnots on 2009-01-12
> **halitech said:**
> when you are burning photos, are you burning them on cd or dvd? There are different lasers in use depending on what you are doing so just because it will write a cd doesn't mean the dvd side is still good. And it may just be a case of bad timing on the reinstall and drive going bad.

Are you saying a better test would be to try burning a photo on a DVD ? Will that automatically dictate the same lasers as those used to burn a movie ???

---

### Post by TransitMan on 2009-01-12
> **CoCoKnots said:**
> Are you saying a better test would be to try burning a photo on a DVD ? Will that automatically dictate the same lasers as those used to burn a movie ???

It would indeed.
CD burning is one set of lasers, DVD burning is another.
Give it a go and see what happens.

---

### Post by CoCoKnots on 2009-01-12
> **TransitMan said:**
> It would indeed.
CD burning is one set of lasers, DVD burning is another.
Give it a go and see what happens.

If the set of lasers for the DVD were bad, would the drive still be able to play a movie?

---

### Post by TransitMan on 2009-01-12
> **CoCoKnots said:**
> If the set of lasers for the DVD were bad, would the drive still be able to play a movie?

Maybe, maybe not. 
The read laser is different from the burn, as far as intensity goes.
However, if the DVD portion has indeed died and the CD-ROM/RW portion remains, it may be time to get another drive.

---

### Post by halitech on 2009-01-14
> **CoCoKnots said:**
> Are you saying a better test would be to try burning a photo on a DVD ? Will that automatically dictate the same lasers as those used to burn a movie ???

> **TransitMan said:**
> It would indeed.
CD burning is one set of lasers, DVD burning is another.
Give it a go and see what happens.

> **CoCoKnots said:**
> If the set of lasers for the DVD were bad, would the drive still be able to play a movie?

> **TransitMan said:**
> Maybe, maybe not. 
The read laser is different from the burn, as far as intensity goes.
However, if the DVD portion has indeed died and the CD-ROM/RW portion remains, it may be time to get another drive.

As Transit man said, in a combo burner, there are 2 sets of lasers. When mine went bad, I could still burn cds, read cds and read dvd's but it would not burn a dvd. and it wasn;t just in linux as I had a dual boot and the same happened in windows. if you have room, you could always keep the current burner and add a new dvd burner and use the non burning dvd to read dvds and keep the new burner for burning only.

---

### Post by CoCoKnots on 2009-01-15
OK... I have not tried copying photos to a DVD before, only CD's. If it's correct to use the same procedure for the two, it looks like the lasers to burn the DVD are shot. It comes back with an error. Notebook R/W DVD drives look to be cheep enough. I guess that's the next step. Thanks guys... I never would have guessed the problem was in the drive when it appears to be reading OK.

---

