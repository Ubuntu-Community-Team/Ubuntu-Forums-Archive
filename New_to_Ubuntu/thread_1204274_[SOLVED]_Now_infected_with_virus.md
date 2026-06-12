---
title: "[SOLVED] Now infected with virus"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by ericstrom on 2009-07-04
Please help. It looks like my 9.04 has been infected by a virus. I was browsing a web page and suddenly got a malware alarm and the screen turned to a MS Windows like view. The same screen now shows up first when I boot up. I can still run ok but it sure looks like a virus. 

Would you please suggest the next step in getting rid of it. Is there a way to run a visus scan to get this garbage off my PC ?

Thanks in advance for your suggestions

---

### Post by donkyhotay on 2009-07-04
Sounds like a scam, many virus makers create webpages that have popups that look like 'official' microsoft alerts to convince you to install their 'cleaner'. Generally the 'cleaner' is a virus itself that steals your information, and if you ever actually pay the company with a credit card online for this service, well... it's not good. If you're in linux the most it can do is install as an add-on into firefox. Cleaning out the add-ons should fix it.

---

### Post by scorp123 on 2009-07-04
> **ericstrom said:**
> It looks like my 9.04 has been infected by a virus. I was browsing a web page and suddenly got a malware alarm and the screen turned to a MS Windows like view. The same screen now shows up first when I boot up. I can still run ok but it sure looks like a virus.  This is a joke, right? :lolflag:

---

### Post by TeoBigusGeekus on 2009-07-04
Screenshot please.

---

### Post by ericstrom on 2009-07-04
This is not a joke at all.

---

### Post by dfreer on 2009-07-04
> **ericstrom said:**
> The same screen now shows up first when I boot up.

Sounds like the OP did get "infected", to what extent though? I'd check your startup programs, see if it's running in Wine, perhaps firefox is saving the tab?

---

### Post by scorp123 on 2009-07-04
> **donkyhotay said:**
> Sounds like a scam, many virus makers create webpages that have popups that look like 'official' microsoft alerts ....  Oh yes, good you mention that. I forgot about those ...

@Eric:

There are no viruses for Linux and usually nothing can infect your Linux system the same way as it was possible on Windows.

What's puzzling me is what you said that this pop-up is still there ... even after a reboot (which shouldn't be necessary anyway ...) ???

Are you sure you're really looking at a genuine problem and not the victim of a prank by a friend or something like that? (I've done such stuff myself .... :twisted: ... And this sure sounds like someone is fooling around with you?)

---

### Post by scorp123 on 2009-07-04
> **TeoBigusGeekus said:**
> Screenshot please.
+1 for the screenshot.

---

### Post by Penguin Guy on 2009-07-04
A screenshot would be nice.

---

### Post by rajeev1204 on 2009-07-04
> **ericstrom said:**
> Please help. It looks like my 9.04 has been infected by a virus. I was browsing a web page and suddenly got a malware alarm and the screen turned to a MS Windows like view. The same screen now shows up first when I boot up. I can still run ok but it sure looks like a virus. 

Would you please suggest the next step in getting rid of it. Is there a way to run a visus scan to get this garbage off my PC ?

Thanks in advance for your suggestions


What do you mean 'during bootup'?

---

### Post by sdlynx on 2009-07-04
> **Penguin Guy said:**
> A screenshot would be nice.

yeah I'm finding this hard to believe.

---

### Post by kwacka on 2009-07-04
is it possible if you are running Ubuntu using 'wabi'?

Sorry, I know nothing about wabi - been windows free for a few years now)

---

### Post by donkyhotay on 2009-07-04
The only thing I can think of is some sort of add-on that accidentally got installed into firefox that simply gives an 'official windows' notice of being infected with malware when firefox is launched.

---

### Post by Penguin Guy on 2009-07-04
> **kwacka said:**
> is it possible if you are running Ubuntu using 'wabi'?

Sorry, I know nothing about wabi - been windows free for a few years now)
Very good point - if you are running WUBI then there is an easy solution. If you running proper Ubuntu, however, then this is far more serious.

---

### Post by rajeev1204 on 2009-07-04
> **donkyhotay said:**
> The only thing I can think of is some sort of add-on that accidentally got installed into firefox that simply gives an 'official windows' notice of being infected with malware when firefox is launched.

I believe this could be it.Those add-ons are an easy way to get some malware onto a linux box.

---

### Post by donkyhotay on 2009-07-04
> **kwacka said:**
> is it possible if you are running Ubuntu using 'wabi'?

Sorry, I know nothing about wabi - been windows free for a few years now)

Do you mean 'wubi'? Wubi allows users to install ubuntu 'inside' windows without repartitioning. Even though it's inside windows it is not a virtual machine and is more like a dual-boot. Viruses still can not spread from windows to linux with it. The only way they can move from linux to windows is if it's downloaded and then copied over manually. If a virus tried to infect the wubi 'partition' file from windows, the most it can do is invalidate/corrupt the files and possibly prevent it from booting correctly. Even that is highly unlikely and you would not get the symptoms described.

---

### Post by radtek on 2009-07-04
How about running clamav? Know about it. Not needed IMO at this point.

I've hit some of the nastiest sites out there and NEVER caught a virus. 

Also, I've read that there *are* "linux viruses" but they are in *captivity* and solely for academic purposes. Not in the wild so to speak.

A screenshot or log would be nice. Sounds like there's a bug or corruption if it is true. I don't think we're getting the whole story and/or this is just a troll's attempt at attention.

---

### Post by TeoBigusGeekus on 2009-07-04
Screenshot or you're trolling.

---

### Post by ericstrom on 2009-07-04
I apologize !!!

False alarm. I had so many problems in the past with windows I jumped the gun a little. It showed up in Firefox not on the main Jaunty screen. Then when I rebooted and opened Firefox the same screen showed up and I paniced a bit.

All is OK. Once again, sorry for the confusion. But thanks all for the comments.

---

### Post by jflaker on 2009-07-04
my daughter got that same screen about a week ago on our linux system and she asked me what should she do about it....

It said right on it, Microsoft Windows something...I asked her one question: Are you running windows? she said "No".  Then i asked, look at the screen closely again....what do you think you should do about it?  She said, "close the pop-up"

Social engineering will cause people to do some freaky stuff....like install trojan software

---

### Post by tuskenraider on 2009-07-04
ive seen this browser hijacking.... 
and i think i screamed oh god oh god... my windows has a virus...wait... im using ubuntu... and i closed the browser...  the window tried to keep me from closing it.. and as i was trying it kept trying to download .exe to my computer..  its possible that it could be running in wine? maybe... maybe? who knows... but in my case i couldnt get the window to close with out downloading the program.. so i downloaded it... exited the browser and deleted the .exe..   

also... force quit could be used to eliminate the "nope you cant close this browser window" effect that some sites have... 

and with a much much less serious tone... delete your system32 folder from your ubuntu install... :lolflag:


tusken
p.s  
more .... .... ... LOL

---

### Post by camper365 on 2009-07-04
Antivirus 2009?

---

### Post by rajeev1204 on 2009-07-04
> **tuskenraider said:**
> ive seen this browser hijacking.... 
and i think i screamed oh god oh god... my windows has a virus...wait... im using ubuntu... and i closed the browser...  the window tried to keep me from closing it.. and as i was trying it kept trying to download .exe to my computer..  its possible that it could be running in wine? maybe... maybe? who knows... but in my case i couldnt get the window to close with out downloading the program.. so i downloaded it... exited the browser and deleted the .exe..   

also... force quit could be used to eliminate the "nope you cant close this browser window" effect that some sites have... 

and with a much much less serious tone... delete your system32 folder from your ubuntu install... :lolflag:


tusken
p.s  
more .... .... ... LOL


I had this same issue and i used forced quit to get rid of it.

---

### Post by aysiu on 2009-07-04
The OP has already said it's a false alarm. If you want to start arguing about whether it's possible for Linux to get viruses or not, you can do so in [Recurring Discussions.](http://ubuntuforums.org/showthread.php?t=1204301)

---

