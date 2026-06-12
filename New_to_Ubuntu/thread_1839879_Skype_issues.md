---
title: "Skype issues"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by 00anthony00 on 2011-09-06
I loaded skype via Ubuntu software centre and apparently have version 2.2.0.35_0lucid1 (skype) downloaded
after successfully signing up, the Skype test call,  "echo123", is what I know as gated, it stops and starts and so cannot hear what is being said coherently as well as my webcam isn't working with skype
I am an absolute beginner though know the basics like, getting an output from terminal and can handle any thing with specific instructions.
there are 5 more pieces of software available for Skype at the software centre, 2 plugin's, an API wrapper, extra functionalities, a management tool and a secure peer to peer VOIP server, do I need to download these as well?
Thank you

---

### Post by nipunshakya on 2011-09-06
First off all, welcome to the forum.
I have had the same problem too...but then, i just opened the settings panel of the skype( right click on the tray notification icon opens it)...have you tried that yet? if not, do it to see if your mic and webcam is configured correctly.....
Is it just skype or does other applications don't run your mic and webcam ??

---

### Post by nipunshakya on 2011-09-07
i just got this information over the internet...hope it might help you out.....check out this link..

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

Regards,NeptuneTech

---

### Post by 00anthony00 on 2011-10-08
Thanks for responding and apologies for the delay in returning, I had difficulties getting back in here

when you say "the settings panel" do you mean "options"?
in Video Device I have: Select Webcam USB 2.0 Camera (/dev/video0)
in Advanced: Connection: Automatic Proxy Detection selected  with two other options available:
HTTPS Proxy
SOCKS Proxy

I cannot get Cheese to run properly, whilst it recognises the camera and gives me a monitor when I click 'start recording' the programme effectively freezes and I have been unable to use the programme at all
though
I mainly use the camera for Vloging on youtube and it runs ok in the main there with their 'instant' uploader
and the microphone works ok with youtubes uploader

with skype currently neither the microphone nor the camera work, also on the audio test and when calling another the sound breaks up so is inaudible beyond hearing the sound breaking up

I have looked at the link you gave thank you for that, though my camera which is 
ID 0c45:62e0 Microdia MSI Starcam Racer - output from terminal command lsusb
is not listed, though I was sure when I first looked there (4 weeks ago) there was one close to the ID reference the last 2 numbers being different, though cannot find that again to-day
ok
found it, though this is the details off the link
 MSI Starcam 370i or Clip 
    7.10 - 8.04  
    0c45:60c0 or 0c45:60fc 
    msicam(modified gspca) 

    You need to download driver from [http://pamplast.com/gspca/](http://pamplast.com/gspca/). Blacklist sn9c102,gspca modules so there is no conflict. 
and the link it gives goes to a site that  only seems to have windows drivers and I dont understand what - "Blacklist sn9c102,gspca modules so there is no conflict." - means and my version is 10.04 LTS and the camera doesn't exactly match anyway?

I am using Skype (Beta) Version 2.2.0.35

I have tried various remedies suggested in the link and am just concerned about the consequences of putting things through the terminal unnecessarily, can I cause issues doing that ?

ultimately at a guess (and I am guessing) there appears to be some sort of conflict between the hardware (camera and microphone) and programme (Skype) that I guess is consequential to configuration.

as well... .
is a fully updated version of ubuntu 10.04 LTS the same or comparable to 10.10 (Maverick Meerkat) or does that not matter? I ask as there doesn't seem to be references to 10.04 LTS in the material at the link you gave.

Let me express my GRATITUDE to you for assisting me and being a part of this project and thereby making it possible, it is WONDERFUL and greatly enjoyable learning and resolving my own conflicts.
I say this here as I have a tendency to thank and rather than waste 'type' will say it once massively here and once more at the resolving of each issue.

I believe there is an Ubuntu group quite local and will seek them out one day to further my involvement.

should I go get cheese fixed fixed first or is that a different issue itself?

Thank you
anthony

---

### Post by 00anthony00 on 2011-10-11
the documents at this link given 

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

relates to version 10.10 (Maverick Meerkat) and the link to "earlier versions" there has no mention of 10.04 LTS, the one I am utilising, as asked above, "can I assume that my fully updated version of 10.04 LTS is equivalent to 10.10 (Maverick Meerkat)"?, in fact the link to "earlier versions" only covers up to 9.04 (Jaunty Jackalope).
without knowing this I am reluctant to meddle or am I being too specific in my interpretation, my lack of understanding of programming holds me back here coupled with my concern of creating further problems consequential to tampering, utilising the wrong guidelines.
I await your assistance.
Thanks

---

### Post by 00anthony00 on 2012-08-11
I have resolved this issue, what appears to be occurring is that the microphone in my camera is conflicting with my microphone input (external mic) to resolve it I have to have the camera mic checked in sound preferences and then the external mic works?? (same occurrence when using youtube uploader where I have camera mic checked in sound preferences and audio mic checked in uploader)
another thing to add was that the references for the camcorder in the links here, my camera had a different model number when checked in the terminal.
forgive the stunted explanations here it has been a while since I resolved this and cannot remember beyond the fix the full details, I am aware tht I never marked this as resolved and needed to that.
thanks as always.

---

