---
title: "safe to email this ???"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-16
i have not been able to watch a video on a website that i go to on occasion...

their customer support sent me a troubleshooting link and i am supposed to send them the info below for advice from them...

User-agent:         Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.11) Gecko/2009060308 Ubuntu/9.04 (jaunty) Firefox/3.0.11                   JavaScript enabled:                      no              yes                            Flash version:                      N/A              Shockwave Flash 9.0 r999         

what is this and is this safe to send to a website ???

thanks...

---

### Post by steveneddy on 2009-07-16
Looks like Javascript is not enabled.

Is this true?

Do you have noscript running?

Post a link to the website or the specific video.

---

### Post by NOTAGEEK on 2009-07-16
> **steveneddy said:**
> Looks like Javascript is not enabled.

Is this true?

Do you have noscript running?

Post a link to the website or the specific video.


what i copied said javascript enabled: yes...

---

### Post by lisati on 2009-07-16
> **NOTAGEEK said:**
> what i copied said javascript enabled: yes...
I'm confused
> **NOTAGEEK said:**
> 
User-agent:         Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.11) Gecko/2009060308 Ubuntu/9.04 (jaunty) Firefox/3.0.11                   JavaScript enabled:                      no              yes                            Flash version:                      N/A              Shockwave Flash 9.0 r999         



---

### Post by NOTAGEEK on 2009-07-16
> **steveneddy said:**
> Looks like Javascript is not enabled.

Is this true?

Do you have noscript running?

Post a link to the website or the specific video.



ooops i forgot---i do not have noscript selected...

---

### Post by The Cog on 2009-07-17
This is safe info to send to them. Your browser sends it every time you visit a web page anyway, which is how their support web site can show it back to you.

---

### Post by ~sHyLoCk~ on 2009-07-17
> **The Cog said:**
> This is safe info to send to them. Your browser sends it every time you visit a web page anyway, which is how their support web site can show it back to you.

That's true. It's safe.

---

### Post by scorp123 on 2009-07-17
> **NOTAGEEK said:**
>  ```
User-agent:         Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.11) Gecko/2009060308 Ubuntu/9.04 (jaunty) Firefox/3.0.11                   JavaScript enabled:                      no              yes                            Flash version:                      N/A              Shockwave Flash 9.0 r999         
```

what is this and is this safe to send to a website ???


That's the so called "user agent information string", e.g. your web browser's finger print.

You're sending it to every web page you visit anyway. So yes, it is safe to send for troubleshooting purposes. They probably already have that string in their server logs anyway.

---

### Post by NOTAGEEK on 2009-07-17
> **steveneddy said:**
> Looks like Javascript is not enabled.

Is this true?

Do you have noscript running?

Post a link to the website or the specific video.

as far as i know i have js running...
noscript is not selected in add/remove...
website is yahoo homepage---they have different vids through the day on there...


> **The Cog said:**
> This is safe info to send to them. Your browser sends it every time you visit a web page anyway, which is how their support web site can show it back to you.

thats fair then...


> **scorp123 said:**
> That's the so called "user agent information string", e.g. your web browser's finger print.

You're sending it to every web page you visit anyway. So yes, it is safe to send for troubleshooting purposes. They probably already have that string in their server logs anyway.

thats fair thanks...


what i dont understand is why the support person asked for this info to troubleshoot why i cant watch their vids---and why i have no audio there ???

a friend sent me an email with a .wmv vid and it worked fine and with great audio too...

any ideas would be helpful...

thanks...

---

### Post by scorp123 on 2009-07-17
> **NOTAGEEK said:**
>  what i dont understand is why the support person asked for this info to troubleshoot  He might not be the same person who has access to the server logs.

> **NOTAGEEK said:**
>  Why i cant watch their vids You didn't really tell us anything about the web site you're going to and what kind of videos (and I mean from a technical point of view -- not the content!) they have: Do they use Flash 9? Flash 10? RealVideo? DiVX? XViD? Microsoft Media Player 9? Media Player 10? Do they use some "Digital Rights Management" mechanisms on their stuff??

There might be many reasons why the videos are not working. We're not even sure you have all the codecs and what not installed. Did you install the "ubuntu-restricted-extras" package and do you use the "medibuntu" repository (e.g. for additional codecs)? You haven't told us yet.


> **NOTAGEEK said:**
>  a friend sent me an email with a .wmv vid and it worked fine and with great audio too... Unfortunately this means nothing. Again: we don't know what WMV version that was. Media Player 9? Media Player 10? With DRM stuff inside? Without DRM stuff inside?

If the web site you're trying to access is using highly proprietary codecs such as Windows Media Player 10 + "Digital Rights Management" mechanisms in those files then you're out of luck -- there probably is no way Linux can play such files, except maybe via a Windows virtual machine running inside e.g. VirtualBox.

---

### Post by NOTAGEEK on 2009-07-17
> **scorp123 said:**
> He might not be the same person who has access to the server logs.

 You didn't really tell us anything about the web site you're going to and what kind of videos (and I mean from a technical point of view -- not the content!) they have: Do they use Flash 9? Flash 10? RealVideo? DiVX? XViD? Microsoft Media Player 9? Media Player 10? Do they use some "Digital Rights Management" mechanisms on their stuff??

There might be many reasons why the videos are not working. We're not even sure you have all the codecs and what not installed. Did you install the "ubuntu-restricted-extras" package and do you use the "medibuntu" repository (e.g. for additional codecs)? You haven't told us yet.


 Unfortunately this means nothing. Again: we don't know what WMV version that was. Media Player 9? Media Player 10? With DRM stuff inside? Without DRM stuff inside?

If the web site you're trying to access is using highly proprietary codecs such as Windows Media Player 10 + "Digital Rights Management" mechanisms in those files then you're out of luck -- there probably is no way Linux can play such files, except maybe via a Windows virtual machine running inside e.g. VirtualBox.


yes---the website is yahoo's home page... as for tech info i cant help out and doubt yahoo will be helpful with much info... yahoo sent me a generic troubleshooting email... after clicking various links and then clicking the results link i got the report that i posted at the beginning of this thread... that is when i asked here if it was safe to email this info... if i wasnt such a newbee i likely would be able to give you better answers here...

yes---as per angel at the beginning of this thread (different thread but restricted extras installed) i installed the restricted extras pkg... as for medibuntu repository i have no idea what that is...

its funny that i can watch these vids on a borrowed win 98 pc with ie 6, 15g hdd, and 128 of mem but not on a new quad core pc running 9.04... i would assume i just might be missing a flash, a driver or something small ??? i dont know whats wrong or i wouldnt be taking up space on this forum with this thread...

thats all i know about this issue...

thanks...

---

### Post by scorp123 on 2009-07-17
> **NOTAGEEK said:**
> yes---the website is yahoo's home page...  OK, can you give us an URL then? What video exactly are you trying to watch? That info would be helpful for troubleshooting, ya know :D

> **NOTAGEEK said:**
>  as for medibuntu repository i have no idea what that is... An extra software repository not included per default due to legal reasons. That repository contains tons of extra codecs and media players and what not.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

> **NOTAGEEK said:**
>  its funny that i can watch these vids on a borrowed win 98 pc with ie 6, 15g hdd, and 128 of mem but not on a new quad core pc running 9.04... Well, say "thank you" to Microsoft for making their stuff in such a way so it won't play nice as soon as you use a non-Microsoft OS.

But your suspicion is correct: it's probably just a small thing missing. Now, if you could please send us the URL of the video you're trying to look at? That would help a great deal. Because I (and I suspect many others here as well?) have tons of codecs from "medibuntu" installed. You don't. So if the video plays nice on my PC then we will know it has something to do with codecs. Can we try that please?

---

### Post by NOTAGEEK on 2009-07-17
> **scorp123 said:**
> OK, can you give us an URL then? What video exactly are you trying to watch? That info would be helpful for troubleshooting, ya know :D

 An extra software repository not included per default due to legal reasons. That repository contains tons of extra codecs and media players and what not.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

 Well, say "thank you" to Microsoft for making their stuff in such a way so it won't play nice as soon as you use a non-Microsoft OS.

But your suspicion is correct: it's probably just a small thing missing. Now, if you could please send us the URL of the video you're trying to look at? That would help a great deal. Because I (and I suspect many others here as well?) have tons of codecs from "medibuntu" installed. You don't. So if the video plays nice on my PC then we will know it has something to do with codecs. Can we try that please?

scorp---thanks for working on this with me... i cant watch any of the vids that come up during the day on yahoo... not that many are interesting, but it's frustrating to on occasion try to watch 1 and not be able to... if necessary ill go there and get a url---but i have yet to be able to view any... other sites (youtube for example) i can usually (not always) see the vid but will have no audio... 

at this point would it make sense to just do a major install at medibuntu.org or would you rather i still get a specific url ??? 

i might add at this point that i have right clicked the screen where the vid should be running and a window opens that  says that the vid is running with audio and i dont have either aud or vid---just a blank black screen without a play button...

thanks...

---

### Post by Raff1 on 2009-07-17
[QUOTE=Scorp123]If the web site you're trying to access is using highly proprietary codecs such as Windows Media Player 10 + "Digital Rights Management" mechanisms in those files then you're out of luck -- there probably is no way Linux can play such files, except maybe via a Windows virtual machine running inside e.g. VirtualBox.[/QUOTE]

I understand that DRM is about encrypting the media (in this case the video) in order to make it cumbersome (intentionally impossible) to make a usable copy of it. How come Lunux can't run such videos? Is the encryption key provided by Windows it self whenever you try to play a video using DRM?

---

### Post by Sidewinder1 on 2009-07-17
NOTAGEEK, just so that you know you're not "barking up the wrong tree," I just went to yahoo's homepage and had no problems watching and hearing the video. It maybe, as stated above, a plugin/addon issue, a codec issue, or NoScript. NoScript will not (I don't believe) show up in your list of installed software as it is an add-on/extension within Firefox; you can chech if it's there in Firefox, under Tools---->add-ons.
My setup is relatively vanilla: 8.04 Ubuntu, old Gforce4 graphics card, etc.

HTH,
Side

P.S.
[http://cosmos.bcst.yahoo.com/up/player/popup/?rn=3906861&cl=14556681&ch=4226714&src=news](http://cosmos.bcst.yahoo.com/up/player/popup/?rn=3906861&cl=14556681&ch=4226714&src=news)
is the url that was listed while the video was playing...

---

### Post by NOTAGEEK on 2009-07-17
> **Sidewinder1 said:**
> NOTAGEEK, just so that you know you're not "barking up the wrong tree," I just went to yahoo's homepage and had no problems watching and hearing the video. It maybe, as stated above, a plugin/addon issue, a codec issue, or NoScript. NoScript will not (I don't believe) show up in your list of installed software as it is an add-on/extension within Firefox; you can chech if it's there in Firefox, under Tools---->add-ons.
My setup is relatively vanilla: 8.04 Ubuntu, old Gforce4 graphics card, etc.

HTH,
Side

P.S.
[http://cosmos.bcst.yahoo.com/up/player/popup/?rn=3906861&cl=14556681&ch=4226714&src=news](http://cosmos.bcst.yahoo.com/up/player/popup/?rn=3906861&cl=14556681&ch=4226714&src=news)
is the url that was listed while the video was playing...


how strange... i just clicked the url you posted and got a white screen with a bunch of code in it... when i tried to copy the code to post here it would highlight but only for a second or so... when i right clicked the screen area that small window mentioned above opened and it said the vid was running and audio ebabled...

thanks...

---

### Post by Sidewinder1 on 2009-07-17
I went back to yahoo and tried to get the link properties and it wouldn't really tell me much :-( It probably requires Shockwave, Flash or some such...
Try going into Firefox---->Tools---->Add-ons and try adding/installing some video helper apps. under Plugins; you *should* be able to uninstall/disable them if they screw something up...

---

### Post by NOTAGEEK on 2009-07-17
> **Sidewinder1 said:**
> I went back to yahoo and tried to get the link properties and it wouldn't really tell me much :-( It probably requires Shockwave, Flash or some such...
Try going into Firefox---->Tools---->Add-ons and try adding/installing some video helper apps. under Plugins; you *should* be able to uninstall/disable them if they screw something up...



thanks sidewinder... at this point i think i should look further into medibuntu...

---

### Post by scorp123 on 2009-07-17
> **Raff1 said:**
>  I understand that DRM is about encrypting the media (in this case the video) in order to make it cumbersome (intentionally impossible) to make a usable copy of it.  Not only that: With Microsoft's DRM in Media Player 10 and later you can also limit how many times a video may be watched, or how many days it will remain watchable.

> **Raff1 said:**
>  How come Lunux can't run such videos? The mechanisms are highly proprietary and built into e.g. Windows Media Player. So unless Microsoft releases a Linux version of their crappy Media Player ....

It's the same with DVD's and Blueray disks. The difference being that some Linux-friendly hackers managed to reverse-engineer the mechanisms and thus work around the encryption, so that today we can watch DVD's on Linux, "Content Scrambling System" or not.

Other formats such as Flash, Ogg Theora, MPEG, XViD, DiVX, Real etc. are either very well documented or even open-source themselves, so that these formats should not cause the same amount of trouble and play very well on Linux.

> **Raff1 said:**
>  Is the encryption key provided by Windows it self whenever you try to play a video using DRM? Please use Wikipedia. It's not just about keys -- the OS and the media player have to play along as well. That's why you find such mechanisms in Windows and Mac OS X -- because in these two cases it's one company that controls both the OS and the media player that ships with it: Microsoft controls both the OS and Windows Media Player. And Apple has total control over the Mac hardware (so they could implement DRM even in hardware if they so wish), iPhones, iPods, the Mac OS and Apple QuickTime. On Linux there is no such scenario: No single company owns or controls anything in Linux, in the GNU utilities, in the desktop environments, or anything like that. And if someone were to implement a DRM mechanism in Linux it wouldn't take too long until other kernel hackers remove that code again -- after all that's the purpose of Linux: to be able to change the source code at will. Hence why DRM stuff will likely not ever work with Linux.

[http://en.wikipedia.org/wiki/Protected_Media_Path](http://en.wikipedia.org/wiki/Protected_Media_Path)

---

### Post by NOTAGEEK on 2009-07-17
thread closed...

---

### Post by Sidewinder1 on 2009-07-18
Naah, it ain't closed... :twisted:
BTW, how did you make out with Mediabuntu? Did you get the videos viewable?

---

