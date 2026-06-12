---
title: "It must be a hardware problem, don't you think?"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by Chris Edgell on 2011-01-14
I have mentioned elsewhere that I put Lucid into a friend's computer yesterday morning.  There had been one thing wrong with it, well as far as I could see. 

Here's how the problem looks.  Did you ever see a movie that was a tape of a tape of a tape, until it looked almost like a cartoon -- all big blobs of colors?  That's how it looked.  I tried a different monitor, and then a different mouse, just to rule them both out.  Neither made any difference.

I brought it here, installed Lucid, and then as I used it for a few hours, after an hour or so, the screen would go black and there would be an intermittent flashing of the sign:  "Power Saving Mode".  I thought it must be related somehow to the initial problem . 

The install had been smooth....getting the sound up and running wasn't hard and then this... 

Any speculation on what part of the hardware this could be...(A video card going out maybe???) 

But now, as I look over at that intermittent flashing of the "Power Saving Mode", now I see what must be a screensaver. 

Oh, now I TREAT it like a screensaver and hit the enter key and my stuff I was doing comes back...and then the next time, it doesn't come back and then after a couple rounds of going one way and then the other now for well over an hour that Power Saving Mode sign just flashes every 10 seconds...nothing else.

I remember back when audioMike told me, (I think it was him) :  go get a can of air and go in and clean it out, it may not solve the immediate problem but if you get straightened out, it will add years to your computer.  Shall I do that?

Any ideas?

---

### Post by Rex Bouwense on 2011-01-14
Chris, compressed air is not going to hurt the computer.  Getting the fuzz-balls out of the computer is always a good thing.
In regard to the other thing, did you check System->Preferences->Power Management.  There is a part there called Display.  Make sure that "Never" is the action you want showing under "Put Display to Sleep".  I know you probably checked that already but I spent two hours trying to figure that one out a couple of years ago.
Rex

---

### Post by GabrielYYZ on 2011-01-14
if you're using a video card and your computer has integrated graphics, try the integrated. if possible, try a different video card. 

if that's not it, see if a friend or a computer repair place can check your PSU.

note: i'm assuming PC, if it's a laptop just disregard my advice. i don't know enough about laptop hardware to comment.

---

### Post by Chris Edgell on 2011-01-14
Hi Rex,

I have spent ALL THIS TIME trying to take a screenshot of the desktop but all I get is "Upload Error" and "Invalid File".  But I'll just tell you that when I go to:

Applications>Systems> then there is NO preferences as an option.

---

### Post by Chris Edgell on 2011-01-14
Gabriel, it will take me hours to figure out on my own what is the video card in this Dell and to see if either of the other two machines around here might have an interchangeable one to try.

But tell me, maybe the video card could cause that "big blob" effect -- but could it also be causing this Power Supply event?

Yeah, it is a PC.  

Thanks for your input.

---

### Post by JKyleOKC on 2011-01-14
Those big blobs of color MIGHT be that the system has switched from the normal 24-bit color mode down to the ancient 16-color mode. Win98 would do that whenever I booted it into "safe mode" and the result was definitely cartoonish in appearance.

For Xubuntu the menus are a bit different from those in Ubuntu, and most of the folk on the forums use Ubuntu and aren't aware of that difference. In Xubuntu, open the "applications" menu and choose "Settings." From its submenu, select "screensaver" and from there take the "Advanced" tab. It will have all the display power management settings on it and you can set them. You may have to log out and then log back in, or reboot, to make sure the new settings are in effect.

To identify the video card, trace the cable from the monitor to the back of the machine; if it's plugged into a card, that's the video card. If it isn't, the system is using integrated video on the motherboard.

---

### Post by Chris Edgell on 2011-01-18
Hi,

I have messed around with this "power saving mode" for three or four days now...

Finally, I had Googled "power saving mode problems" and there have read many pages of people who have had this problem.  

[I don't even know if this was happening before--back when I had started this thread about the big blobby looking color patterns on the screen...because the guy is mentally challenged and can't remember... what with me seeing about two different machines he has...seeing if I can get ONE of then going.  I had chosen this one to start with because the other one is merely freezes up...for some reason I thought this would be the easy one; just install a Linux/Ubuntu release and be done with it... not thinking that that color problem could (and most likely would) be a hardware problem.]

ANYWAY, last night I finally went to the monitor...went through ALL the monitor settings, positions, coloration, etc.  AFTER ALL I moved things around (no easy task) and switched monitors.  These are both flat screens, about 16" ones,  NOW this one doesn't start flashing "Power save mode, but it cuts out and then flashes "Auto Image Adjust" At that point I have to do what I did with the other: press Ctrl + Alt + Delete and it restarts.

Now, I'm going to download 9.04 Jaunty Xubuntu after I locate it....and see what happens then.  If that doesn't work, I'm going to his house and just try to get the other one going.

Although I did want to say that the Jaunty machine has a much more simpler yet more comprehensive Screensaver adjustment GUI.  In Lucid, there is no power component where I can see: sleep--Never,

I'm trying to attach screenshots and will if I can.



[http://en.kioskea.net/forum/affich-46233-can-t-exit-power-saving-mode](http://en.kioskea.net/forum/affich-46233-can-t-exit-power-saving-mode)

---

### Post by Chris Edgell on 2011-01-19
Now what can I tell ya'??!!

I installed Jaunty today -- I began the install at 3:30 P.M. and here it is, midnight and it hasn't blacked out on me at all.  That's eight and a half hours where before it couldn't even go an hour.

So, what shall we say...that it's NOT a hardware problem??!!  Does that mean it's in the Lucid release....?  Although all of those pages and pages of people who have had that same problem with "Power saving mode" can't have been just having Lucid Lynx -- so it leaves me wondering WHAT GIVES?  

I'll let you know if somehow the machine reverts to that behavior.

---

