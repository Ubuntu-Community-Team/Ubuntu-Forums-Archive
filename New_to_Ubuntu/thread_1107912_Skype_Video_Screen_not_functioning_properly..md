---
title: "Skype Video Screen not functioning properly."
date: 2009-03-27
forum: New to Ubuntu
---

### Post by suomalainen on 2009-03-27
Synopsis:

At issue is the Skype Video Screen. Currently it is unable to display live video streams. In two specidic instances, Skype is unable to stream live video feeds via webcam when:

1) In a live call and the "Start My Video" option has been selected
2) Under the "Video Devices" option a live video stream "TEST" cannot be successfully performed.

A work around has been discovered. However, it isn't a pratical method to follow. The Skype program itself should operate and perform flawlessly as intended.

It is hoped that through the epertise and knowledge of those here that the Skype Video Screen can be restored to its proper functionality.


Please consider the following:


Software/Hardware being used:
Linux-Ubuntu 8.04 LTS
Skype version 2.0.0.72
Logitech QuickCam Chat CQ Chat 961462-0403
HP AMD model a500n Additional info available at:
[http://h10025.www1.hp.com/ewfrf/wc/product?product=405440&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=405440&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us)


Scenario 1

1. Applications ---> Internet ---> Skype
2. Right click on Skype icon in tool bar and choose: Options ---> Video Devices (See picture# 1)
3. Click on the "TEST" button over the black screen (See picture# 2")

IMPORTANT NOTE # 1:
At this point the "TEST" button disappears and the Skype test video screen remains black with no "live" video feed that can be seen.

IMPORTANT NOTE # 2:
If a Skype contact is online a call can be placed to that contact. However, When "Start My Video" is chosen a live video feed does not appear in the lower left hand corner of the Skype video screen. However, a live Skype video feed is being transmitted "live" from Skype to the Contacts computer although that live video feed isn't being properly displayed. THIS FEATURE NEEDS TO WORK SO THAT THE CALLER CAN POSITION THE WEBCAM CORRECTLY DURING A CALL.

4. Right click on Skype icon in tool bar and choose: Quit


Scenario 2

1. Applications ---> Internet ---> Skype
2. Applications ---> Sound & Video ---> TVtime Television Viewer
3. Set TVtime Television Viewer volume to zero (0).

ABOUT TVtime Television Viewer:
tvtime is a high quality television application for use with video capture cards on Linux systems. tvtime processes the input from a capture card and displays it on a computer monitor or projector. See: [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

4. Go to Skype
5. Look for an online contact and make a call to that contact
6. Select "Start My Video"
7. A "live" Skype video feed appears on both the Contacts computer and the computer of the person originating the call. 

IMPORTANT NOTE # 3:
Within the Skype video screen appears both the contacts live video feed and the smaller video of the caller in the bottom left hand corner.

8. End the call with the contact
9. Right click on Skype icon in tool bar and choose: Options ---> Video Devices (See picture# 1)
10. Click on the "TEST" button over the black screen (See picture# 2")
11. Live "TEST" video stream appears (See picture# 3)


Scenario 3

1. Applications ---> Accesories ---> Terminal
2. Enter the following: gstreamer-properties
3. Terminal reports the following, see below, as the Multimedia Systems Selector program opens:

desk@desk-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
desk@desk-desktop:~$

4. Pictures 4 & 5 show the settings of the Multimedia Systems Selector program.


Scenario 4

1. Applications ---> Accesories ---> Terminal
2. Enter the following: lsusb
3. Terminal reports the following:

desk@desk-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08af Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000
desk@desk-desktop:~$

---

### Post by suomalainen on 2009-03-28
bump................

---

### Post by suomalainen on 2009-03-29
Ding dong...... (That's the door bell ringing!)

---

### Post by mikebravo on 2009-03-29
> **suomalainen said:**
> Ding dong...... (That's the door bell ringing!)

This might do you some good.


[http://ubuntuforums.org/showthread.php?t=1101069](http://ubuntuforums.org/showthread.php?t=1101069)  


Having something working and then quit not because of something I have done except to trust the OS really sets my teeth on edge.

---

### Post by suomalainen on 2009-03-30
Thanks MikeBravo but that didn't help....

---

### Post by suomalainen on 2009-03-31
Bump''''''''''''''''

---

### Post by LowSky on 2009-03-31
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

> **suomalainen said:**
> The Skype program itself should operate and perform flawlessly as intended.


I agree that a company out to make money should make a product that works, but how is skype not working an Operating System issue? Clearly its an application issue.

why not check the requiremnts and make sure you system is using the correct versions, here are the applications skype requires
Qt 4.2.1+ 
D-Bus 1.0.0 
libasound2 1.0.12 

also make sure gspca isup to date and running the newest version
also if your running compiz turn it off.

---

### Post by suomalainen on 2009-04-01
Hi LowSky,

You have me confused???? Do you disagree that software should function as intended?????  I'm unclear as to the point you are attempting to argue???

Additionally, You alleged that I stated that because Skype isn't working for me that it is an Operating System issue. You stated the following:

"but how is skype not working an Operating System issue? Clearly its an application issue."

I'm sorry LowSky but your false allegation was uncalled for. I have re-read my post and nowhere did I make such a statement as you suggest. As a matter of fact, I never even used the term "operating system" in my post!!!

What I have done, however, is provided detailed information relating to the issue I'm faced with. I believe that if you provide as much information as possible it will help resolve the issue at hand. It also makes it easier for others to understand what the problem is.

Although I can appreciate your ability to help, I do not appreciate it when my words are taken out of context and improper statements "made-up" that are declared as being authentic statements stated by me. That is clearly wrong!

Finally, if you haven't throughly read my post and at the same time are making things up, how can I possibly trust the integrity of the advice you have to offer???????

---

### Post by s_raiguel on 2009-04-01
I experienced a similar problem with the Logitech Quickcam e1000 and Skype, found this offered as a solution on another website, perhaps it'll help. Try entering, on the command line

 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

This worked for me. As I understand it, it pre-loads a video for linux module into the kernel before starting Skype, though I dont' really understand why this is necessary, and only for Skype. The app "Cheese" works fine, as is. If this works, then you can create a short script file to start Skype in this manner each time, and point your menu item to this script file instead of Skype itself.

---

### Post by suomalainen on 2009-04-01
s_raiguel, Thanks for the info! I'll give it a try and report back. Can you explain the following??? You lost me???

Thanks!

> **s_raiguel said:**
>  If this works, then you can create a short script file to start Skype in this manner each time, and point your menu item to this script file instead of Skype itself.

---

### Post by suomalainen on 2009-04-01
s_raiguel,

I tried the command you offered and received the following error msg in TERMINAL:

desktop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Starting the process...
Skype Xv: Xv ports available: 1
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 68
Skype Xv: No suitable overlay format found

Also, after I entered the command You gave SKYPE launched itself. I tried Options --> video Devices to see if I could see the test video but it still did not work.

---

### Post by anewguy on 2009-04-01
> **suomalainen said:**
> Hi LowSky,

You have me confused???? Do you disagree that software should function as intended?????  I'm unclear as to the point you are attempting to argue???

Additionally, You alleged that I stated that because Skype isn't working for me that it is an Operating System issue. You stated the following:

"but how is skype not working an Operating System issue? Clearly its an application issue."

I'm sorry LowSky but your false allegation was uncalled for. I have re-read my post and nowhere did I make such a statement as you suggest. As a matter of fact, I never even used the term "operating system" in my post!!!

What I have done, however, is provided detailed information relating to the issue I'm faced with. I believe that if you provide as much information as possible it will help resolve the issue at hand. It also makes it easier for others to understand what the problem is.

Although I can appreciate your ability to help, I do not appreciate it when my words are taken out of context and improper statements "made-up" that are declared as being authentic statements stated by me. That is clearly wrong!

Finally, if you haven't throughly read my post and at the same time are making things up, how can I possibly trust the integrity of the advice you have to offer???????

Please don't get upset at people trying to help, no matter what you think of that help.  Even I must admit that your opening post, while very detailed, sounded like a backdoor slap at Ubuntu, even though I'm sure you didn't mean it that way.;)


Is the TV Time application running all the time?  If not, then when you do the option where you adjust a setting in it, start Skype and the video works, are you leaving the TV Time application running while you go to Skype?  Also, since I don't know, you mentioned that software (EDIT: read this - I was last talking about TV Time, and still am) works through a video capture card - is your camera hooked up to such a card or just through USB?  If it is hooked up via such a card, it could be that the video is blocked until an application is run which opens the video stream.  It's also possible you may need to configure TV Time to NOT look at you USB camera as an input source.  I did quite a bit of looking at the TV Time site, and it appears to a product which isn't maintained.  Since you are using TV Time, are you leaving it in a "sleeping" state?  Personally I would completely turn off TV Time and then try Skype again.  If you have a video capture card (I assume you must or otherwise it doesn't really make sense to use the software?), what type of card is it?

If it's USB are you using the usb driver from the TV Time site?

What type of video card or IGP do you have?

I know you gave a lot of detail at the start, but could you also please provide the information above?  I really believe it is something with a conflict or lock of some sort between the TV Time software and other programs accessing your video device.

You may want to try removing TV Time altogether and trying one of the other open source TV programs to see if it helps.

Wishing you the best!
Dave ;)

---

### Post by anewguy on 2009-04-01
Sorry for all the edits it took to make the previous post.  Originally I wasn't going to dig into this, as I don't use the video option.  But looking at the TV Time site and the bug reports got me a little more interested.

Dave ;)

---

### Post by s_raiguel on 2009-04-02
Even if that that "pre-load" command works when entered on the command line, you'll soon found that opening a terminal and re-entering it each time you want to start Skype is a pain. The solution to write a short script file. These can be very useful; they're a lot like the old batch files in DOS. 

To make a script file, open the Text editor and enter the following lines:

#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
exit 0

Then save it as "sky.sh" in your home directory. Now, go to system-preferences-main menu, and edit the "properties" for the menu item internet - skype so that the "command" option is "/home/[user name]/sky.sh". You can now start Skype with the command line options simply by clicking the menu item.

---

### Post by s_raiguel on 2009-04-02
Sorry, I missed the post where you said that preload_etc didn't work, and saw only the question where you asked about script files. You can ignore my post above, since if the command doesn't work from a terminal window, it certainly won't work within a script file. Sorry to hear it didn't help.

---

### Post by s_raiguel on 2009-04-02
It just hit me that you mentioned that the v4l1compat.so wouldn't pre-load. Check with the synaptic package manager, and make sure that the following libraries are installed:
v4l1-0
xserver-xorg-video-v4l
lipt-1.10-plugins-v4l
lipt-1.10-plugins-v4l2

---

### Post by suomalainen on 2009-04-02
Dave,

You publicly called into question my character!

You accused me of making a "backdoor Slap at Ubuntu" and I would like to hear your foundations for such an unsubstantiated remark???? Frankly speaking you don't have a leg to stand on. Certainly, if you had some sort of evidence or factual "proof" that merited such an allegation, You would have backed up Your statement with real and factual evidence. But You elected not to do this!!! Instead, You simply made-up a vague, false and grossly inappropriate accusation and expected that I would take it laying down. Well Sir that is not going to be the case and I certainly will not allow myself to become Your punching bag because You like to fabricate misinformation with no substance or validity! I therefore openly challenge you to provide the exact wording of the statement You claim that I made which is a "Backdoor slap at Ubuntu"! Just for Your information, and as anyone who knows me will attest, I happen to be one of the biggest and most vocal advocates for Ubuntu in my circle. Anyone who knows me would tell You right off the bat that such an accusation is totally out-of-character and wouldn't believe You for a second! As we will soon see, You will be unable to provide supportive information backing this falsehood You alleged against me because it was simply made up and a fantasy construed on your part!!!!

Regardless, I believe reading comprehension plays a large part in the miscommunication, lack of understanding and falsehoods you publicly stated against me. 

Here are a few examples from your recent post:

QUESTION:

"Is the TV Time application running all the time? If not, then when you do the option where you adjust a setting in it, start Skype and the video works, are you leaving the TV Time application running while you go to Skype"

ANSWER

Scenario 2 clearly answers this question

QUESTION

"Also, since I don't know, you mentioned that software works through a video capture card - is your camera hooked up to such a card or just through USB? If it is hooked up via such a card, it could be that the video is blocked until an application is run which opens the video stream"

ANSWER:

I never stated that the Skype software works through a video capture card! Additionally, Scenario 4 and my hardware list already describe the webcam as a USB device.

QUESTION:

"I did quite a bit of looking at the TV Time site, and it appears to a product which isn't maintained."

ANSWER:

BUT TVTime website states ([http://tvtime.sourceforge.net/why.html):](http://tvtime.sourceforge.net/why.html):)

"A community member - tvtime WAS helped by many projects, and we try to give back. Our code can now be found in xine, freevo and mythtv. We're committed to helping all Linux media apps achieve high quality standards for video."

Is this a surprise??? TVTime was created with a specific goal. That goal was achieved and now TVTime is offered free-of-charge to the community. You also claim that it isn't maintained but bugs [if they really can be called and classified as such] can be filed via the TVTime website. The webmaster can also always be contacted. Finally, certainly the TVTime website is being maintained to some degree and paid for if one can still gather information from it, file bug reports, email the webmaster and more importantly download from it.....

QUESTION:

"Since you are using TV Time, are you leaving it in a "sleeping" state? Personally I would completely turn off TV Time and then try Skype again."

ANSWER:

Scenario 1 & Scenario 2 clearly answer this question

QUESTION:

"If you have a video capture card (I assume you must or otherwise it doesn't really make sense to use the software?), what type of card is it?"

ANSWER:

Sabrent PCI TV Turner/Video capture- TV Turner PCI Philips 7130

QUESTION:
If it's USB are you using the usb driver from the TV Time site?

ANSWER:
n/a

QUESTION:

What type of video card or IGP do you have?

ANSWER:

Intel 82Q963/Q965 Integrated Graphics Controller


I look forward to hearing from You how I backdoor slapped Ubuntu and all the community members it comprises, which over the last two years have been a great resource and support mechanism to me.

Regards,

Suomalainen

P.S.
You need to read some of my past posts because I have always said "Thank You" and given credit to others when due!

---

### Post by anewguy on 2009-04-02
I don't get you - people try to help and you jump all over them.  If you don't need the help, or you think you are better, then don't ask.  You did  notice the "even though I'm sure you didn't mean it that way" followed by a wink didn't you?  Loosen up.


Think your detail is perfect? Let me give you an example:

Scenario 2

1. Applications ---> Internet ---> Skype
2. Applications ---> Sound & Video ---> TVtime Television Viewer
3. Set TVtime Television Viewer volume to zero (0).

ABOUT TVtime Television Viewer:
tvtime is a high quality television application for use with video capture cards on Linux systems. tvtime processes the input from a capture card and displays it on a computer monitor or projector. See: [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/)

4. Go to Skype
5. Look for an online contact and make a call to that contact
6. Select "Start My Video"
7. A "live" Skype video feed appears on both the Contacts computer and the computer of the person originating the call. 


You tell me where it says in there whether or not you leave TV Time going.  It simply isn't stated.  You may say it's inferred, but inference is like ignorance (and before you get upset again, ignorance means a lack of knowledge - it's not an insult) when trying to solve a problem.  Doesn't say you exited, doesn't say you didn't.

Did you ever look into the idea that just perhaps TV Time IS somehow stepping on the video stream, regardless of it being USB?  Your other examples don't DISPLAY the video stream - only the one where you started TV Time, changed the volume setting (BTW - look at the forum for TV Time and you'll see unanswered posts about this being a problem AFTER TV Time is exited).  Don't you see the logic in thinking there may be something there causing a problem?  If not, you're no genious either.

Some of us are just trying to help.  Believe it or not there have been occasions on this forum where I have helped someone.  Change your attitude in your responses and you might get some.

Good luck - you're going to need it.

Dave

P.S. - Thanks?  I don't need thanks anyway.  I only TRY to help because of the great amount of help I have gotten here.  I'm no genious, but if there is something I think I may know an answer for I offer it for help.  Play it forward.

---

### Post by LowSky on 2009-04-02
suomalainen Maybe something is getting lost in translation being English isn't not your homeland's primary language.

First to defend myself, Skype not working is not an Ubuntu issue, it is a Skype issue, I clearly mention that you should browse the Skype Forums and even included a link of how to get some help installing Skype for a possible soluiton.
Clearly you didnt even look at the link I suggested as your "character" became an issue.

Here a new link on Skype and Camera, enjoy
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

> **suomalainen said:**
> Dave,
You publicly called into question my character!


1. I don't think he did.
2. Your posts are utterly confusing. The SCENERRIO and the QUESTION/ANSWER thing is very negative, and come off being utterly sacastic and negative, especially towards me and anewguy, when we ask you for specifics.

Your issue from what I know (because you haven't given any data about your system  (like supplying lsusb and lspci reports) stems from your TV card and webcam conflicting in some way being skype/tvtime or something  else. At least from the little, albit extremly long-winded information you did present. The anwser is to remove your TV-card and see if the issue is stll present. If it is then we can rule that out.

s_raiguel and I both asked if you had a few packages installed, and you never responed to that. could you fill us in on that please.

Again we are here to help. I have been a member on this site for a long time. Although this website promotes not to use the RTFM, I do believe that a person should use the Search function of this webste and using of Search engines, like Google. So If we can not give you the answer you crave, then please search around, amybe someone else has found a fix
[http://ubuntuforums.org/search.php?searchid=57438083](http://ubuntuforums.org/search.php?searchid=57438083)
[http://www.google.com/search?hl=en&q=skype+no+video+tvtime&aq=f&oq=](http://www.google.com/search?hl=en&q=skype+no+video+tvtime&aq=f&oq=)

---

### Post by Rocket2DMn on 2009-04-02
Let's please drop the personal attacks and debates about them, there is no need to continue down that course.  Let's keep a professional attitude in continuing to help the OP with his problem.  Please keep in mind our [Forum Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") and that the users here are all volunteers.  We understand that having problems is frustrating, and the community will do their best to offer support and advice.

Thank you.

---

### Post by suomalainen on 2009-04-03
> **LowSky said:**
> suomalainen Maybe something is getting lost in translation being English isn't not your homeland's primary language.

The Forum Moderator asked that personal attacks be dropped! In turn, attention is then diverted upon my homeland, Finland, for not maintaining English as its "primary" language. A fact having no relevance in this present discussion. Do you seriously want to question my poor or below average English skills???

Perhaps as native English speakers you are taking it for granted that this forum is using the English language as its "working" language. Many foreigners that are members of this forum possess a strong command of the English language and perhaps that is being overlooked and not fully appreciated? I would even wager that some foreigners know the English language better than some native speakers. For example, if we take the statement:

> **LowSky said:**
> Maybe something is getting lost in translation being English isn't not your homeland's primary language.

Isn't this grammatically incorrect? Shouldn't the sentence read:

"Maybe something is getting lost in translation? English IS NOT your country's official language."???

If the English only rule is going to be enforced, applied or even suggested, maybe we should adopt British English as the official language of the forum and have moderators prohibit the posting of threads unless they are grammatically correct and free of error and local jargons and dialects??? That's fair isn't it? The "ubuntuforums.org" domain is owned by Canonical, a U.K. company based in the Isle of Man. Additionally, since many of us foreigners learn British English in school and given that this website is owned, operated and maintain by Canonical, A United Kingdom company, this would make perfect sense. MAYBE THEN WE WOULD THEN BE BETTER UNDERSTOOD??? In turn, we could then ban the usage of certain English variants and dialects which many Brits feel has corrupted the English language altogether..... PBS is a valued American company, so maybe this link will add further insight into this perspective:

[http://www.pbs.org/speak/ahead/change/ruining/](http://www.pbs.org/speak/ahead/change/ruining/)

In a recent post, I reflected upon reading comprehension. With that in mind, I posted in post # 1 the following data:

Scenario 4

1. Applications ---> Accessories ---> Terminal
2. Enter the following: lsusb
3. Terminal reports the following:

desk@desk-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08af Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
desk@desk-desktop:~$

Then I'm told:

> **LowSky said:**
> Your issue from what I know (because you haven't given any data about your system  (like supplying lsusb and lspci reports)

I don't know if this is a good thing or a bad thing but YES it is true that we Finn's don't use the English language as our official language. Instead, our country has 3 officials languages. They are Finnish, Swedish and Sami. You can look the Central Intelligence website to learn more:

[https://www.cia.gov/library/publications/the-world-factbook/geos/fi.html](https://www.cia.gov/library/publications/the-world-factbook/geos/fi.html)

We Finn's learn "British English" in school, just like the rest of the world with a few exceptions.

So, I guess because of the variant of English I have learned, we will never come to understand each other. Please accept my best wishes as you walk away and thank you very much for your support.

Suomalainen

---

### Post by Rocket2DMn on 2009-04-03
You have completely missed the point of my post.  Please cease with the personal discussions - language, homeland, insults, and all that.  Please focus on the technical issue at hand and let everything else drop.

---

### Post by LowSky on 2009-04-03
](*,)  
Did you try the solutions that anewguy, s_raiguel, or I offered? For instance installing extra components that s_raiguel and I suggested, or changing your hardware around to check if its a driver conflict? How about removing TVtime?

---

### Post by anewguy on 2009-04-03
This is what I personally would try, but be aware that I am not familiar with your video capture card:

- remove TV Time

- remove your video capture card

- remove all traces of your video capture card driver (if any), including any that may be part of X

- remove Skype completely

- remove the driver for your video camera (if any)

- reinstall the driver for your video camera (if any)

- re-install Skype

- try Skype with video

- install your video capture card, but no driver (if any)

- try Skype with video

- install the driver (if needed) for you video capture card

- try Skype with video

- install TV Time

- without TV Time running, try Skype with video

- start TV Time, but make no adjustments to anything

- try Skype with video

- make the volume adjustment in TV Time

- try Skype with video

These are basic troubleshooting techniques, and you should do them to isolate when the problem is introduced.  Once you find where it is introduced, post back.  The whole idea is to remove EVERYTHING that may be associated with the problem, then reinstall them one at a time until the problem is encounterd.  When you post back, please include screenshots of each step.  If your problem is fixed somewhere in route please let us know when.

Dave

---

### Post by anewguy on 2009-04-06
Have you done any of the suggestions?  What was the outcome?  Have you solved your problem on your own?  If so, post what you did back here so others can see the solution.

---

