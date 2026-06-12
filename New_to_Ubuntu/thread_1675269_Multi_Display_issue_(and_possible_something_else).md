---
title: "Multi Display issue (and possible something else)"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2011-01-25
Ok so I got a bit fed up of windows 7 and have been growing fonder of ubuntu recently to the point where this is pretty much the last machine not running linux!

Its an AMD64 Dual core X7750, 4gb mem, soundblaster audigy, AMD crossfire motherboard and an ATi HD4650 graphics card, SATA 160gb main and SATA500gb secondary (where linux seems to live).

The other day I aquired a reasonable second monitor and decided to go dual head, which initially I had some issues with ATi drivers (I have another thread on this) but then when I plugged the second monitor in, I had it working and adjusted the resolutions to match the monitors, it then wanted a reboot and now I have a big issue!

basically the background seems to be tiled accross my 2 monitors (at a size smaller than original image which is about the size of the monitors) with an IBM 19" 1280x1024 on the left and a DGIM 19" widescreen 1440x900 on the right. The menus and title bars are all on the right monitor (which is plugged in as no1) and the mouse seems to be stuck on monitor 2, which is where it gets wierd. Its not stuck in 1 spot, I can move it around, but the area its stuck in is of a limited size of say 1024x768 which is what my background has been tiled to. So I cant actually get the cursor to the right screen where all the menu bars are!

Not really sure where to go from here!

Now some other issues which may be related or not to my graphics one:

when I first installed ubuntu I used the recommended proprietry drivers, which causes things to mess right up (couldnt get into ubunut) I then used some suggested commands on my other thread to remove these and then the things started working, but the Ubuntu start screen is of a lower resolution as if its still running a different driver rather than the normal high res you seem to get before drivers.

Something that started happening before my restart when I had 2 monitors was I was playing music through rythembox from a CD and it would play about 20-30 seconds of a track (if that!) and would then jump to the next track and only occasionally could you get it to play a full track! previously it had been ok before the drivers were changed, hence why I am not sure if its a related issue?

Some pointers would be useful on this one as its a little beyond me how to get back to normality and currently I am stuck using windows 7 :(

---

### Post by I8NY on 2011-01-28
I don't think i can fix all your problems but i can try to help.  For the back ground set the image to span get it not to be titled.  I made a costume image to span 2 desktops so it looks correctly.  Now i would recommend having the proprietry drivers but maybe try getting them from ATI and manually installing them.  If you ever get the driver install configure the monitors with amdcccle. (the built in stuff doesn't always work)  But with all these weird problems i would check to make sure you don't have bad RAM of bad hardware and maybe even do a clean install of ubuntu. (bad disc burn?)

---

### Post by Bugsy_malone 666 on 2011-02-01
well I run windows 7 on this machine as well and it runs like a dream most of time (other than the odd internet scripting error) the background itself is the size of the 1440x900 monitor (I think its actually a bit bigger!) but for some reason it has downsized the desktop below any resolution, I think the resolution of the new backdrop is 1024x768 but the main problem is my mouse pointer seems to be locked into one of the tiles on the left monitor and all the menus to try and change anything are on the right monitor so inaccessable!

its odd that initially when I resized everything it was ok, it was when I rebooted it came back with problems.

Think i need to carry on reading to understand some of the commands to maybe get things back to previous!

---

### Post by Bugsy_malone 666 on 2011-02-05
Well The good news is I have eventually managed to cure the problem myself only I am not totally sure how/why.

Basically I went into 'recovery mode' at start up and was greeted with a list of options including one to repair bad packages and going into default video mode (which I am sure I couldnt access before!).

So once I had pressed on the repair bad packages option it took a while to go through things, then said that there were updates needed and I said yes to updates which it then took a little while to download and install everything.

Once this had done I then restarted and went into recovery again but this time selected to go into default video mode, which came up with a small menu asking me if I wanted to revert to a previous config, try to create a new one or use a default one. It wouldnt create a new one for some reason but by selecting the default one I was then able to get the system to operate normally!

Thats not quite the end of it mind as I still ended up with a little problem where by this time the mouse pointer was still trapped in one screen. This time though it was the one with menus! by messing about with the monitor options I went from default to adjusted, got stuck in one screen, then pressed cancel and it was ok I could finally use both screens, so downloaded ATi drivers which gave me a black screen after reboot completely!

So through the same recovery process again only this time I deactivated the ATi driver and set the monitor resolutions up and it seems to be working ok ( I have rebooted a few times). I am going to download ATi drivers out of the ubuntu software centre as currently it let me use the advanced graphics options for desktop where you can have wobbly windows and other fun graphical items!

Not out of the out of the woods yet but I think for the time being I will close this thread as solved as currently it works!

---

