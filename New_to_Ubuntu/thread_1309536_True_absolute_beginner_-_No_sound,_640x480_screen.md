---
title: "True absolute beginner - No sound, 640x480 screen"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by frelnc on 2009-11-01
Hi there:  

I came here to Absolute Beginner Talk and found technically expressed explanations that were so far over my head that I felt embarrassed to even be here, but I don't know where else to go.

I am a complete Linux novice.  

I need REALLY Absolute Beginner Talk. 

Although they remind me of DOS, I still don't understand how to do the command lines and even if I did I wouldn't know what to do with the results once I had them.

I don't have a manual yet - it's on its way - but right now, I have no idea how to change the definition on my monitor from 640x480 to something reasonable, or how to turn on my speakers.  No drivers show up when I try to install them.

I have a Dell Dimension 2300.  

Took me a while to figure out how to install Ubuntu when the OK buttons were off the screen because of the 640x480 definition but I made it through that.  

According to Dell I could have either DNIVIA or ATI drivers - or both.  I downloaded a DNIVIA driver and absolutely nothing happened.  Every place I've looked the answer is always "install drivers" yadda yadda.  I can figure out how to hook them up - got that part - but HOW do I install the downloaded drivers so they show on the drivers screen?

According to Dell the only OS their drivers are suitable for is XP.  So, now what?  

I'm a TRUE Absolute Beginner.  Anybody willing to tackle this kind of ignorance?  :)

MKT

---

### Post by overdrank on 2009-11-01
Hi and welcome, What version of Ubuntu are you using? You can find this under system about Ubuntu.
You may also look under system, administration, Hardware drivers for drivers for your graphics card.
To identify your hardware you may use the command in the terminal
```
lspci | grep VGA
```
The terminal is located under applications, accessories.

---

### Post by waspbr on 2009-11-01
k, first of all welcome. 

Now to the fun bits, when I started out I didn't know anything about the command line either, actually it scared me a bit. But eventually you may see that it is very practical and it saves a lot of time. 

as a first I would recomment this website
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

it has tons of useful information for newcomers.

secondly,you should find out that the strongest point of ubuntu is it's community. people are generally very eager to help you out, sometimes somone is going to guide you through the graphical interface or just give you a command for you to paste into the the terminal window. 

It is very useful if you tell us what version of ubuntu you are using, karmic/jaunty/hardy and what architecture (32 bit or 64 bit). From there we can see what we can work with. 

As a general rule, there first thing I do when I have a fresh install is to check if my system is up-to-date, I am going to give you some steps which may be a little redundant but bare with me. 

1.assuming you are using gnome, go to System > Administration > Software Sources. 

2.Type your password

3.check that the first four boxes of the "ubuntu software" tab are marked and then go to the tab next to it, it should read "other software"or "third party ..." mark the boxes on this tab and close. A dialogue should appear asking you to reload, you may do that, depending on your connection it should take a little while.

4 Go to system>Administration > Update manager, it should check automatically for updates, install those updates. Again, depending on you internet connection this may take a while. 

5. Once this is done, it is probably going to ask you to reboot. 

6. After rebooting, go to system > Administration > Hardware drivers, the drivers for you video card should be listed there. Activate them and follow the instructions on the screen. After that you may need to reboot. 

7. Once all that is done, the system should adjust everything automatically, tho if the resolution is not right you may go to System > Preferences > Display. 

let us know how things go

---

