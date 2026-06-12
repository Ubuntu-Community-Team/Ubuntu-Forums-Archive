---
title: "Volume Icon restore instructions."
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-12-16
Oh boy I was a dummy.  I accidentally removed my volume control icon from the upper panel.  I didn't mean to, and would like to have it back, but I can't for the life of me find how to get it to show on the panel again.  It used to be right next to the shut off icon and my name.  

Any way to get it back???

---

### Post by KommaH on 2009-12-16
Right-click on the panel and select "Add to Panel", then search for the volume/sound control and add it to the panel. From there, right click on the newly-created icon and select "Move", and move it to the tray.

---

### Post by chillyomi on 2009-12-16
:guitar: Thnkx Man same thing happened to me with the shutdown good thing i found this thread before i started a new one

---

### Post by mustard greens on 2009-12-16
in case you are using 9.10, there will be no volume applet option under add to panel. in 9.10 there is an applet titled "notification area".  by adding the notification area to the panel you will get your volume applet back.  

P.S. in case you are wondering I have already reported this as a papercut.

---

### Post by jamieleshaw on 2009-12-16
Don't know if this is helpful but I will put it in anyway.
To Reset Panels type
rm -f ~/.gconf/apps/panel
then type
sudo /etc/init.d/gdm restart
;)

---

### Post by Desert Sailor on 2009-12-18
Thanks guys...that was it.  I am using 9.10 and would have never guessed "Notification" area if you hadn't posted.  I love this place.

---

### Post by chris282 on 2009-12-18
Thanks all.

Another dummy right here.

- Chris

---

### Post by smulla on 2009-12-18
Thank you I was in my wits end. I didn't know they changed it to Notification area :guitar:

Like a dummy I was inserting all kinds of commands in terminal and installing software I didn't need

---

### Post by jrybon on 2010-01-26
I lost mine by uninstalling pulseaudio (which was interfering with Skype).  Can anyone think of a way to put it back? Or recommend another?

---

### Post by aaguy on 2010-02-02
> **mustard greens said:**
> in case you are using 9.10, there will be no volume applet option under add to panel. in 9.10 there is an applet titled "notification area".  by adding the notification area to the panel you will get your volume applet back.  

P.S. in case you are wondering I have already reported this as a papercut.

Thank you!!!  Spent a half hour trying to figure this out.  "Notification area" is a label I will not forget.

---

### Post by BavarianPH on 2010-04-04
In Lucid Ubuntu 10.4 (beta 1) the "Volume" & "Chat" icons are restored by   adding the "Indicator Applet" from the "Add to Panel" option.  (Adding the "Notification Applet" to the panel does not restore these in Lucid.)

---

### Post by slotto on 2010-04-11
Thanks!

---

### Post by bohemier on 2010-04-16
It's in the indicator applet in Lucid 10.4 (using beta at the moment)

---

### Post by Dangger on 2010-04-23
> **bohemier said:**
> It's in the indicator applet in Lucid 10.4 (using beta at the moment)

Thanks, I think in the past version this applet used to be for chat and email. They have moved chat to "Indicator Applet Session" and moved audio/sound to "Indicator Applet"

---

### Post by ubunterooster on 2010-04-24
> **bohemier said:**
> It's in the indicator applet in Lucid 10.4 (using beta at the moment)

Seriously, that is a pain. Why was it moved again? Anyway, thanks. :)

---

### Post by syed8bpl on 2010-04-28
> **mustard greens said:**
> in case you are using 9.10, there will be no volume applet option under add to panel. in 9.10 there is an applet titled "notification area".  by adding the notification area to the panel you will get your volume applet back.  

P.S. in case you are wondering I have already reported this as a papercut.
thanks man

---

### Post by jaybok on 2010-04-30
Just updated to 10.4 and wanted to remove the "chat" from the panel and in doing so removed volume as well.  Adding the indicator applet worked for me.  Thanks guys.

---

### Post by starweb350 on 2010-05-01
Thanks everyone!
I had the same problem after upgrading from Karmic to Lucid.
This was actually the ONLY problem I encountered during the upgrade. 
Since I seem to be stuck with the envelope I am thinking of switching back to evolution from thunderbird.

---

### Post by skrimpy on 2010-05-02
> **bohemier said:**
> It's in the indicator applet in Lucid 10.4 (using beta at the moment)

Thanks.

---

### Post by TnTonly on 2010-05-04
I've just upgraded Ubuntu 10.04 and now I have 2 volume icons, one belongs to Indicator Applet, have a nice graphical icon like the rest of the theme. The other belongs to Notification Area with the Network Manager, and has an incredibly ugly icon. I don't know how to remove the other volume icon, as I have to remove the entire Notification Area as well as the Network Manager icon. 

This only happens with my account. The Guess Session seems to be not affected by this. Does anyone have any solution?

Edit: Since the topic is marked [SOLVED], I don't think posting my problem here is a good idea, so I moved my post here
ubuntuforums.org/showthread.php?t=1452740

---

### Post by Hilko on 2010-05-09
> **BavarianPH said:**
> In Lucid Ubuntu 10.4 (beta 1) the "Volume" & "Chat" icons are restored by   adding the "Indicator Applet" from the "Add to Panel" option.  (Adding the "Notification Applet" to the panel does not restore these in Lucid.)

I lost my volume indicator after the last lucid updates. Adding the "Indicator Applet" from the "Add to Panel" option did not work for me. Neither the notification area.

How do I get them back? Someone please help..

---

### Post by DjWolfEase on 2010-05-09
Yeah no kidding. 
Ok so I had the volume control by adding it in start up applications but then when I downloaded skype the input volume did not work. So I was all like.. aight.. I'll just forum this puppy problem and get going.. when the forum said delete pulse audio I was like.. hey no worries.. I'm on it.. then BAM I delete pulse audio and restart and still skype sound is not working ANDDDDD and and andddd I lost my bloody volume icon again. now get this.. thinking it would be just as easy as the last time.. I went to system - preferences - start up applications to re do the whole thing and.. what's this??? volume control is already there! ok so now I have volume control checked in the start up  applications... with no volume control icon.. I still don't have skype working.. AND TO BOOT.. when I upgraded to lucid lynx I lost EVERYTHING  on my harddrive.. wth.. please someone just help me out here. I would like input on my skype and MIN my volume control back! I've come to accept losing my 6000 songs and 5 years of contracts and documents.. that i can live with..(honestly I think their gone for good) just help a brotha out! 
Thanks.

---

### Post by X_Splinter on 2010-05-10
> **BavarianPH said:**
> In Lucid Ubuntu 10.4 (beta 1) the "Volume" & "Chat" icons are restored by   adding the "Indicator Applet" from the "Add to Panel" option.  (Adding the "Notification Applet" to the panel does not restore these in Lucid.)

Thanks.

Also if you want to restore both panels to default type in the terminal

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Hilko on 2010-05-11
> **X_Splinter said:**
> Thanks.

Also if you want to restore both panels to default type in the terminal

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

Yeah, my panels are restored to default. Apparently the default panel has no volume icon.

---

### Post by X_Splinter on 2010-05-11
> **Hilko said:**
> Yeah, my panels are restored to default. Apparently the default panel has no volume icon.

Ok, now that is strange...

---

### Post by vevel on 2010-05-13
> **DjWolfEase said:**
> Yeah no kidding. 
Ok so I had the volume control by adding it in start up applications but then when I downloaded skype the input volume did not work. So I was all like.. aight.. I'll just forum this puppy problem and get going.. when the forum said delete pulse audio I was like.. hey no worries.. I'm on it.. then BAM I delete pulse audio and restart and still skype sound is not working ANDDDDD and and andddd I lost my bloody volume icon again. now get this.. thinking it would be just as easy as the last time.. I went to system - preferences - start up applications to re do the whole thing and.. what's this??? volume control is already there! ok so now I have volume control checked in the start up  applications... with no volume control icon.. I still don't have skype working.. AND TO BOOT.. when I upgraded to lucid lynx I lost EVERYTHING  on my harddrive.. wth.. please someone just help me out here. I would like input on my skype and MIN my volume control back! I've come to accept losing my 6000 songs and 5 years of contracts and documents.. that i can live with..(honestly I think their gone for good) just help a brotha out! 
Thanks.

Don't use skype, so unfortunately can't help there -- for the volume control, you might check this thread:
[http://ubuntuforums.org/showthread.php?t=1466400&page=5](http://ubuntuforums.org/showthread.php?t=1466400&page=5)
For some reason, I didn't have the package 'indicator-sound' installed, and when I added that (could be done via synaptic, sudo apt-get install indicator-sound, etc.) my volume control came back. 
Here's a snip from my dpkg installed list:
$ dpkg --list | grep indicator
```
ii  evolution-indicator                                           0.2.8-0ubuntu1                                  GNOME panel indicator applet for Evolution
ii  indicator-applet                                              0.3.7-0ubuntu1                                  GNOME panel indicator applet
ii  indicator-applet-session                                      0.3.7-0ubuntu1                                  Clone of the GNOME panel indicator applet
ii  indicator-application                                         0.0.19-0ubuntu4                                 Application Indicators
ii  indicator-me                                                  0.2.6-0ubuntu1                                  indicator showing user information and status
ii  indicator-messages                                            0.3.6-0ubuntu2                                  GNOME panel indicator applet for messages
ii  indicator-session                                             0.2.8-0ubuntu2                                  An indicator showing session management, status and user s
ii  indicator-sound                                               0.2.3-0ubuntu1                                  A system sound indicator.
[...]

```

---

### Post by johnrobert on 2010-05-15
Just wanted to thank BavarianPH for pointing me to the Indicator applet. Worked for me. :)

---

### Post by ZaqW on 2010-06-11
BavarianPH your a life saver that was it... Why cant they name things accordingly these days haha:p

---

### Post by heyandy889 on 2010-07-29
Sweet boogans maloogans. Thank you all for the help. I couldn't figure it out!

I'm using the Lucid Lynx 10.4 Ubuntu. The fix for me was right clicking the top panel, clicking "Add to Panel...", selecting "Indicator Applet", and clicking "Add." That gave me my volume icon back. 

Also a problem for me was figuring out that I had to right click and select "Move" to move the panel icons, not just left-click and drag.

---

### Post by ruffneck on 2010-08-10
> **KommaH said:**
> Right-click on the panel and select "Add to Panel", then search for the volume/sound control and add it to the panel. From there, right click on the newly-created icon and select "Move", and move it to the tray.

Thanks KommaH, worked for me!

---

### Post by stanz on 2010-10-20
> **vevel said:**
> 
For some reason, I didn't have the package 'indicator-sound' installed, and when I added that (could be done via synaptic, sudo apt-get install indicator-sound, etc.) my volume control came back.
Installing this, was an instant fix - 
no startup addition..
no terminal code...

I thinks installing esound has this effect for me (10.04 amd64 - after update/grade),
as that was uninstalled as par synaptic.

Thx

---

### Post by Shooree on 2010-10-26
thanks, guys.

---

### Post by wildbill46 on 2010-10-26
](*,)  Thanks, you forum folks can fix anything!  I'm running 10.04 and this volume icon was really getting to me.  However, like always, just go to the forum and start reading.  The indicator applet made my day.  Thanks

---

### Post by markackerman8@gmail.com on 2010-11-09
after trying the 6 0r so other possible fixes I thought I was in for a dead end,  but:

sudo apt-get install indicator-sound
&#8728; clicking "Add to Panel...", selecting "Indicator Applet"

worked and mythtv started working with my hvr-950Q as well.

Thanks a bunch! :KS

---

### Post by billyfish010 on 2010-11-09
After reading all the above posts the easiest way I found to replace my lost applet was like this. "Use Alt+F2 to open the Run Application app, paste **gnome-volume-control-applet** into the text field, and click the Run button - it was dead simple

---

### Post by reggiecl on 2010-11-13
> **bohemier said:**
> It's in the indicator applet in Lucid 10.4 (using beta at the moment)

Thanks, your solution works great!

---

### Post by Wanda's on 2011-08-02
OH ! It was the indicator option in the Add to Panel that brought up the missing icons! ](*,)

 I think :KS's about all of you!

---

### Post by Rahbee Kannuhn on 2012-01-04
> **stanz said:**
> Installing this, was an instant fix - 
no startup addition..
no terminal code...

I thinks installing esound has this effect for me (10.04 amd64 - after update/grade),
as that was uninstalled as par synaptic.

Thx

Knowing the name of what I needed did the trick.
Thanks.
In my case mine was already installed, the name for it was less than intuitive I guess.

---

