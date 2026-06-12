---
title: "sound problems"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by pdlethbridge on 2010-01-24
This seems to be a two-fold problem. My computer is a p4 2.6 gig on a MSI pe main board with 1 gig of memory and 256 mg video card but no sound card. I have a tv capture card to watch tv at the computer and everything seems to work fine. I use ubuntu 9.04 Jaunty and have, at times, upgraded to 9.10 Karmak, and here lies one of the problems. No sound, nothing, not a peep. Tv card will work because I can back date the kernel to 2.6.28.17 using the start up manager, but I still get no sound for anything. When I checked the 'add to panel' menu, there is no sound icon to choose. Researching here and on line, google, didn't help. I'd like to keep up with the newest software but this problem is beyond me. Could this be a reportable bug???:confused:](*,)](*,)
The second problem may be a heat issue as the sound will work for a while in 9.04/wine/ roller coaster tycoon, then quit. Back on the desktop everything is fine. Any help or guidance would be greatly appreciated. Paul

---

### Post by pdlethbridge on 2010-01-24
bump

---

### Post by Mariane on 2010-01-24
Join the club. I think you need alsa. 

I posted here how to install it: 
[http://ubuntuforums.org/showthread.php?t=1386856](http://ubuntuforums.org/showthread.php?t=1386856)

It didn't solve my problem (no output to the headphones) but at least it got the sound working out of the speakers. 

The sound problems so many people are experiencing are caused by something called pulse audio which is remplacing alsa in 9.10. 

Pulse audio can do many exotic things, such as allowing you to set the volume differently on different applications, even on the applications which don't natively provide a volume setting. Geeks have no problem getting it to work and they love it. Ordinary people mostly can't get it to work at all. 

I've spent a lot of my spare time troubleshooting after the 9.10 upgrade, and my new laptop is now running Debian because I'm giving up on Ubuntu. 

Whoever decided to replace alsa by pulse audio in 9.10 should be shot. 

Mariane

---

### Post by tea for one on 2010-01-24
> **pdlethbridge said:**
> This seems to be a two-fold problem. My computer is a p4 2.6 gig on a MSI pe main board with 1 gig of memory and 256 mg video card but no sound card. I have a tv capture card to watch tv at the computer and everything seems to work fine. I use ubuntu 9.04 Jaunty and have, at times, upgraded to 9.10 Karmak, and here lies one of the problems. No sound, nothing, not a peep. Tv card will work because I can back date the kernel to 2.6.28.17 using the start up manager, but I still get no sound for anything. When I checked the 'add to panel' menu, there is no sound icon to choose. Researching here and on line, google, didn't help. I'd like to keep up with the newest software but this problem is beyond me. Could this be a reportable bug???:confused:](*,)](*,)
The second problem may be a heat issue as the sound will work for a while in 9.04/wine/ roller coaster tycoon, then quit. Back on the desktop everything is fine. Any help or guidance would be greatly appreciated. Paul

Good evening

Right click top panel
Select "Add to panel"
Select "Volume control"
Click "Add"

This will insert the sound applet to the panel

Right click sound applet
Select preferences

See if that helps.

However, I did notice from your original post that you "upgraded" to Karmic, in my experience, a fresh install seems to give less problems than an upgrade.

Best wishes

---

### Post by pdlethbridge on 2010-01-24
When I checked the 'add to panel' menu, there is no sound icon to choose from. Now I only use one panel at the bottom, I would assume that the top panel wouldn't have it either. I don't have the 9.10 cd to run, I just upgraded from 9.04 in up date manager.

---

### Post by pdlethbridge on 2010-01-25
bump

---

### Post by joebasolo on 2010-01-25
I also have a BIG problem with sound... I get a false 1/2 second click/buzz on any audio.. I looked @ applets to add to task bar and no sound/audio anything that I saw.. I will read the other post on another thread for trying ALSA but I wish that they had added the option to the Preferences/Sound app? Seems like it should be there to me?

---

### Post by raymondh on 2010-01-25
Hope this helps

[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

Raymond

---

### Post by pdlethbridge on 2010-01-25
After down loading and burning a CD of 9.10, I put it in a unused area of my hard drive so I could duel boot. It seemed okay at first but as I downloaded updates and installed a couple of necessary files, I started to notice little things that would cause me to trash this OS. Even though the sound worked from square one, it was never right, it would skip and pause like a scratched old record.
The tv card and tvtime software were unfixable, just got the blue screen, no picture.
The software I use for my canon pixma 1500 printer returned an error on installing it.
This has got to be the biggest mistake that Canonical has made, acts just like windows me or vista. It just isn't right.
They should take a step backwards and go with what works and allow more options including a kernel change in the start up manager. When software that works is broken in a new OS, please, please fix it.
I'm back with my favorite 9.04 and I'll stick with that and wait until April. I hope the problems are fixed by them. I don't even want to go back to windoz. I love this OS

---

### Post by tea for one on 2010-01-26
[QUOTE=pdlethbridge;8725075]After down loading and burning a CD of 9.10, I put it in a unused area of my hard drive so I could duel boot. It seemed okay at first but as I downloaded updates and installed a couple of necessary files, I started to notice little things that would cause me to trash this OS. Even though the sound worked from square one, it was never right, it would skip and pause like a scratched old record.

Good morning

Just to satisfy my curiosity, after you did a fresh install of 9.10:-

(a) The volume applet was visible in the top panel by default?

(b) The volume applet was also in the "Add to Panel" drop down list in the event that it had to be restored?

---

### Post by pdlethbridge on 2010-01-26
The volume control was visible on the top panel, but missing in the add to panel applet

---

### Post by tea for one on 2010-01-27
> **pdlethbridge said:**
> The volume control was visible on the top panel, but missing in the add to panel applet

Good morning

I have only just realised that there are differences in the "Add to Panel" menu between 8.04, which I use and 9.10, which is causing you problems.

It does seem that, occasionally, it is better to try and help when the OS is the same version.

I'm not completely familiar with 9.10 yet, but I would like to suggest that there may be some worth in investigating if the notification area/applet is part of the difficulty.

When you read the fora, many people have sound issues.

I doubt if I can offer any more advice with this because I generally use the 8.04 LTS version at the moment.

I am going to keep my eye on this thread to see if any other suggestions appear.

Best wishes

---

### Post by tea for one on 2010-01-27
> **pdlethbridge said:**
> The volume control was visible on the top panel, but missing in the add to panel applet

Good evening

Apparently, in Karmic 9.10, the volume control will appear as follows:-

Right Click Panel
Select "Add to Panel"
Scroll down to "Notification Area" and select
Click "Add"

I hope this works for you, I've just tested it on a live USB persistent Ubuntu 9.10 OS and it was successful.

The Ubuntu developers like to keep us on our toes.

Good luck

---

### Post by pdlethbridge on 2010-01-27
The install of an operating system can have some serious ups and downs. I downloaded and burned a 9.10 cd and formated and installed it over the old OS but kept the home folder intact. There were some problems caused directly by the home folder. For instance, I couldn't find the applications, places, systems icon,(found it in the add to panel applet)The sound was still choppy, tvtime didn't work,(tried several things) and the drivers I was using for my canon pixma ip1500 printer were not allowed to finish downloading because of one file ( libsys2, I think.)
So I re-installed the OS, formated and repartitioned the drive to , one, give me more space for the OS, and two, format and enlarge the home folder. I left the home folder blank as I have certain files backed up on a fat32 partition at the end of the drive. It went okay and I got to the desktop so I did my usual putting the panel at the bottom. Again, I was unable to get tvtime to work, the sound was still choppy, and after spending time looking for canon drivers, I gave up. This took several hours, but as I'm handicapped, I have the time on my hands.
With the let out of a big sigh, I have gone back again to 9.04. If I'm up to it, I try it again next week. I WILL make it work.

---

