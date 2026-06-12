---
title: "Mostly Hardware Compatibility Questions For A Beginner"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by AndrewVT on 2010-06-10
Hi All,

A little background, I am a very advanced computer user in the windows world.  Right now I have hit my breaking point with windows for my current project and want to try something new.

The project: Home Theater PC
The Problem: I cant get my 5450 HDMI audio to work with more then one channel (front left) in Vista, Ive been thinking of trying out the Linux based OS and this was my breaking point.

First question, is all my hardware compatible.  This is a computer built from spare parts that were upgraded out of my watercooled gaming computer.
EVGA750i FTW Mobo [8gb DDR2 ram, some random HDD, a samsung CDRW, pw supp, etc]
Quad core 9400
HIS(ATI) 5450 VC w/ HDMI 7.1 audio out (or so it says)
EVGA9500GT (1GB DDR2 model) - not used but I couldn't find a static bag to store it in.

HT Relevant Hardware - Panasonic 50'' Plasma TV taking HDMI input and outputting audio via optical to a samsung HT 422 model in a box speaker set.  

Second Question, what is the best version of linux.  I'm leaning towards Ubuntu just because it looks simpler for the home theater purpose.  Redhat looks OK too but it looks to much like windows (I love windows...shame on me...but I don't want this to have a windows feel, its more like a really cool cable box.

Third Question, are all plugins relevant to HULU, south park studios, etc compatible with linux systems.

Fourth Q, simply put, good idea vs bad idea is this going to work or should I go buy W7 (already have 2 computers running 7) and hope that throwing money at my problems will make them go away.

Thanks, 
Andrew

PS - I just moved to vermont from NYC.  I don't have access to a microcenter anymore (360mile drive) so replacing hardware is out and bestbuy (although much better stocked then the one at home) is a laughable option for real computer parts.  I also don't do mail order...returns are to much of a pain and I don't like waiting.

---

### Post by apjone on 2010-06-10
I would download a Live Linux CD (Ubuntu or other) burn it and boot from it. The Live CD is great for checking basic Hardware Compatibility. After that if you want a media center try Mythbuntu ([www.mythbuntu.org/](www.mythbuntu.org/)) or standard ubuntu/linux with Moovida version 1.0.9 ([http://www.moovida.com](http://www.moovida.com)).

---

### Post by cozmicharlie on 2010-06-10
Welcome to the forums.  I know exactly what you are going through.  I have been setting up a couple media PC on both W7 and Linux.  What I have found is no solution is perfect and it really depends on what you want to do.  

Hardware:  The only problem you may have is the ATI video card.  I have the same card.  I have not been able to install it in Lucid from the live cd (or any other installer).  I had to go back to 9.10 and it works fine.  It is easy to find out if it works in your system.  Download the Ubuntu Live CD, boot to the cd, follow the screen instructions and select "Try Ubuntu without installing".  If it loads then you are good to go - if you end up with a blinking cursor on a black screen then you are going to have problems.  Some people have reported ways to work around this, but I am a fairly knowledgeable user and I wasted lots of time trying to get this to work.  The NVIDIA card will be no problem.  Works great.  As per the sound.  ATI will get sound via HDMI but for NVIDIA you may need SPDIF.  This is a NVIDIA problem with some hardware (same on windows).  You will get all channels.  Make sure you install the latest drivers.

Since you are on the Ubuntu forum I will take a chance and say most of us will recommend Ubuntu. Since you want a completely different experience than Windows, I recommend Ubuntu with XBMC (or Boxee).  You could also look at Mythbuntu but it might be a bit much for someone with no experience in Linux.  XBMC and Boxee are media centers that work great.  You can install both from Ubuntu.  A live XBMC is also available. 

The experience will depend on what you want to do.  You will have no problem with Hulu etc on Linux.  The only limitations will be Netflix and Blue Ray.  Neither works natively in Linux. Since you don't mention Blue Ray, I will assume you don't need that.  Netflix though will not work natively but you could install Virtual Box and run Netflix through VBox (defeats the purpose to me but it is an option).  I do something different.  I have a Roku box and a Hauppage DVR.  I run Roku through the HD-PVR.  That way I can watch via the computer and also record (for later viewing).  

I find the big advantage to Linux is I can play any audio and video format (accept Blue Ray).  The codecs, encoders, transcoders, tagging, cataloging etc are all readily available.  Nice part is they are all free.

I have one box set up with W7 and one with Ubuntu (XBMC) and I much prefer the Ubuntu/XBMC.  

You could also try them side by side - dual boot Ubuntu and W7 and see which one you like better.  

Enjoy and let us know what you decide.

---

### Post by AndrewVT on 2010-06-10
Thanks for the great replies, keep them coming.

Another question.  What is this Lucid I hear so much about?  It sounds like something I should know.

I'm not concerned about the audio from the nvidia, I already disabled it in the bios.  Actually, the only reason I bought the ati was because I would only have to run one cable to my TV and the TV outputs all of my devices to the HT.

I have a bluray player so I am not concerned with playing it on the computer.  This whole project is because I don't want to pay for cable.  I realized that everything I watch is on HULU and being I spent 60 on the video card, the whole mess will pay for itself in 2 months.  

Now I have to go find a place in the middle of nowhere that sells CDRs so I can install this.  For some reason it wont boot from my USB.

---

### Post by apjone on 2010-06-10
Lucid is the Development Code Name for the latest stable Ubuntu release 10.04 . More info @ [https://wiki.ubuntu.com/DevelopmentCodeNames](https://wiki.ubuntu.com/DevelopmentCodeNames)

---

### Post by dookiebowser on 2010-06-10
I'm really not an expert with home theater PCs... but both your mobo and your video card have HD audio 7.1

Try using the mobo instead of the graphics card or vice versa for kicks. Also, if you are using the video cards HDMI, disable the mobo and vice  versa.


If you want to go to linux for Home theater solutions, try GeeXboX. it's a distro that is specifically designed for Home Theater PCs and will run off of a liveCD as well.

[http://geexbox.org/en/index.html](http://geexbox.org/en/index.html)

---

### Post by cozmicharlie on 2010-06-10
*Now I have to go find a place in the middle of nowhere that sells CDRs so I can install this. For some reason it wont boot from my USB.*

Can you typically boot from usb?  Is the usb device bootable?  Let us know how you tried to do this - maybe we can help so you don't have to make the long trip.

---

### Post by AndrewVT on 2010-06-10
so I got my hands on some blank CDs and tried to boot lucid (I'm learning already).  Here is what happens.

First it boots to a screen with what appears to be a keyboard and an arrow pointing to a man in a circle.

Then it goes to a black screen with an old school dos type cursor.

Then it switches to an ubuntu screen with alternating red and white dots.

A few minutes later everything goes dead.

Thoughts, opinions, prayers?

---

### Post by Sef on 2010-06-10
> so I got my hands on some blank CDs and tried to boot lucid (I'm learning already). Here is what happens.

First it boots to a screen with what appears to be a keyboard and an arrow pointing to a man in a circle.

Then it goes to a black screen with an old school dos type cursor.

Then it switches to an ubuntu screen with alternating red and white dots.

A few minutes later everything goes dead.

Thoughts, opinions, prayers?

Another poster had written this about Luci (see post 3 for more info):

> cozmicharlie
Hardware: The only problem you may have is the ATI video card. I have the same card. I have not been able to install it in Lucid from the live cd (or any other installer). I had to go back to 9.10 and it works fine. It is easy to find out if it works in your system. 

---

### Post by AndrewVT on 2010-06-10
Oh, ok, I wasn't sure if that posting was referring to the same thing.  OK, cool.

Just wanted to pause and say thank you to all.  Its quite awesome that such a helpful community could form around a free operating system.  

I'm downloading Karmic Koala (is that the right previous version) and lets see how it rolls.

---

