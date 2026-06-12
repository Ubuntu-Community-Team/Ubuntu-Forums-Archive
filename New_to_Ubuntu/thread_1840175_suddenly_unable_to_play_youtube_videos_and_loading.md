---
title: "suddenly unable to play youtube videos and loading facebook"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by drtejams on 2011-09-07
hi,
help me .. all of a sudden my browser both firefox6 and google chrome stopped playing youtube video and loading facebook.
 
for youtube videos --error occured please try again later, and for facebook --connection was reset please try again later.

i have no problem viewing other sites like twitter or google+ .i cleared the cache from the browser menu.. what else should i do 

i installed the following software
chromium -12.0.742.112 (90304) Ubuntu 11.04
mozilla firefox 6
flash version 10,3,183,5 installed

---

### Post by Bodsda on 2011-09-07
> **drtejams said:**
> hi,
help me .. all of a sudden my browser both firefox6 and google chrome stopped playing youtube video and loading facebook.
 
for youtube videos --error occured please try again later, and for facebook --connection was reset please try again later.
 
i have no problem viewing other sites like twitter or google+ .i cleared the cache from the browser menu.. what else should i do 
 
i installed the following software
chromium -12.0.742.112 (90304) Ubuntu 11.04
mozilla firefox 6
flash version 10,3,183,5 installed
 
Disable all plugins and extensions then try again, if that fails, try removing and reinsalling firefox with the purge option
```

sudo apt-get remove --purge firefox && sudo apt-get install firefox

```
 
Failing that try temoprarily removing the firefox settings directory, I forget its exact name but I think it is ~/.mozilla   rename this directory to .mozilla.old and then load firefox.

---

### Post by drtejams on 2011-09-07
should i do the same thing with chrome

---

### Post by Bodsda on 2011-09-07
> **drtejams said:**
> should i do the same thing with chrome
 
Not at the moment. Test this with firefox and you will then know whether it is a browser issue or something else.
 
Bodsda

---

### Post by drtejams on 2011-09-07
same error even after reinstalling firefox

---

### Post by Paul Crawford on 2011-09-07
Did you check the update manager?

My sister's machine lost its ability to use Flash as she turned it off while it was doing a security update in the background. As it was partially done, and no one bothers checking such stuff (hence it was on 'automatic'), it sat there until I took a look.

Even if you did not have an update fail, you might want to remove and re-install the flash player.

---

### Post by vasa1 on 2011-09-07
The odd thing is that OP has problems with Fx **and** Chrome. At least on MS Windows, Chrome comes with its own version of Flash and so a Chrome user has a choice of two Flash plug-ins. If I remember correctly, the modded Flash has a higher run priority (or something like that) over the other plug-in (which is common to Chrome and Fx).

Another possibility could be that it's a shared computer and someone has played a prank?

Edit: Oops .. OP mentioned Chromium, not Chrome. I don't think Chromium comes with the modded Flash.

---

### Post by corncob on 2011-09-07
A couple of distributions ago the neighbor kid came over and said that she was unable to watch you-tube videos.  I didn't know what to say so I went over.  I followed the instructions at
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
and left her happily watching her idol on you-tube.  Thinking that link might be dated at this point I've been using the instructions at
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
to get my videos running, if necessary.  I don't know why yours suddenly stopped when it had been working.

---

### Post by Overcast32 on 2011-09-07
> **Paul Crawford said:**
> Did you check the update manager?

My sister's machine lost its ability to use Flash as she turned it off while it was doing a security update in the background. As it was partially done, and no one bothers checking such stuff (hence it was on 'automatic'), it sat there until I took a look.

Even if you did not have an update fail, you might want to remove and re-install the flash player.

I had an issue with no sound on YouTube - re-installing Flash fixed it. Good thing to try.. :)

---

### Post by drtejams on 2011-09-09
thanks for the reply guys.. but my problem is not solved and most of my time i use facebook and youtube .... maybe i should reinstall os or can u give me anyother suggestion

---

