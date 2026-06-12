---
title: "Hardware detection help needed"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by cmbcne on 2009-01-03
I'm a slightly experienced Linux user (I know enough to get myself in trouble).  I just visited a friend's house to install Intrepid.  His Windows install was totally screwed up with viruses and he "didn't have the CD" to reinstall (wink, wink, nudge, nudge).

Install seemed to go OK... Except:

Sound:
When we tried to play a song in Banshee I realized he didn't have any speakers.  More then that, though, is the alsamixer gui didn't show any sound cards listed.  He's going to get some speakers, but I have a feeling they won't work 'cause the sound card didn't detect properly.

Video Card & Monitor:
He has a GeForce FX 5200 video card and a Compaq S700 Monitor. The monitor is capable of 1280 x 1024 at 65Hz.  The GeForce card should be able to handle that and more.  What we got, though was 800x600 resolution.  The system prompted us to install the Nvidia drivers, so I did.  After a reboot all we could get is 640x480.  The xorg.conf file was generic -- no specific nVidia or Compaq entries.

Bottom line:  I've installed various versions of *buntu for a couple of years - just to try them - and I've never seen one fail so badly on detecting the hardware.  I know it's fixable, I just don't know how.  Can someone give me a plan of attack?  It's a 45 minute drive to his place, so I need to know what I'm going to do before I go.

---

### Post by EnGorDiaz on 2009-01-03
> **cmbcne said:**
> I'm a slightly experienced Linux user (I know enough to get myself in trouble).  I just visited a friend's house to install Intrepid.  His Windows install was totally screwed up with viruses and he "didn't have the CD" to reinstall (wink, wink, nudge, nudge).

Install seemed to go OK... Except:

Sound:
When we tried to play a song in Banshee I realized he didn't have any speakers.  More then that, though, is the alsamixer gui didn't show any sound cards listed.  He's going to get some speakers, but I have a feeling they won't work 'cause the sound card didn't detect properly.

Video Card & Monitor:
He has a GeForce FX 5200 video card and a Compaq S700 Monitor. The monitor is capable of 1280 x 1024 at 65Hz.  The GeForce card should be able to handle that and more.  What we got, though was 800x600 resolution.  The system prompted us to install the Nvidia drivers, so I did.  After a reboot all we could get is 640x480.  The xorg.conf file was generic -- no specific nVidia or Compaq entries.

Bottom line:  I've installed various versions of *buntu for a couple of years - just to try them - and I've never seen one fail so badly on detecting the hardware.  I know it's fixable, I just don't know how.  Can someone give me a plan of attack?  It's a 45 minute drive to his place, so I need to know what I'm going to do before I go.


could you please post the output of this command in terminal

```
lspci
```

as for video card drivers goto system>administration>hardware drivers 

if it doesnt show...

do this command in terminal then goto system>administration>hardware drivers

```
sudo apt-get install jockey-gtk jockey-common
```

then it should be fine but for the soundcard i suggest you do the lspci above as i said and i will try and guide you

---

### Post by cmbcne on 2009-01-04
Thanks for the reply.  It's such a long drive to his place and we're both busy with business, so my approach is going to be to try to get remote access to his box.  I'm going to try to talk him through opening the port on his router while guessing what he's seeing, then have him do System>Preferences>Remote_Desktop.  If it works I'll be a lot more interactive with this thread.

On the other note: I ran System>Administration>Hardware_Drivers and it found the video card and suggested the nVidia driver.  Things got worse after installing it and rebooting, so I deactivated it and that brought the resolution from 640x480 back to 800x600, which is a bit more usable (but not great).  It did not detect the audio card or the monitor, so I started this thread to see if there's a way to force it to detect those things.

I'll post again after I (A) get remote access to his box, or (B) arrange a time to visit him again.  Please bear with me.

---

### Post by Michael.Godawski on 2009-01-04
hi

perhaps you try to install the nvidia drivers via the enny ng application?


[LIST]
[*][http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
[/LIST]

It helped a lot of people.

---

### Post by cmbcne on 2009-01-04
Thanks Michael.Godawski for the answer.  

As I said above, I'm going to try to get remote access to his box first, because it's a 45 minute drive to his place and we both have busy schedules.  

I did install the driver that the Hardware_Drivers applet suggested and it just got worse (it went from 800x600 to 640x480), so I deactivated it.  I believe the problem is that the monitor is not selected, so the nVidia driver (either the generic one or the updated one) don't know what monitor they're trying to "feed", so the driver defaults to the lowest possible settings for safety sake.  To me it seems that getting the monitor detected properly would be the first step -- or am I out to lunch?

---

### Post by cmbcne on 2009-01-12
UPDATE:
Thanks, all, for sticking with me.

I've been too busy to actually go to his place.  We tried on the weekend to set up remote control, but it didn't work.  I'm not sure, but I think he didn't forward the ports on his router properly -- I was trying to talk him through it "blind" and I thought he did it right, but we must have missed something.  I'll have to actually go there, I guess.   THat could take several days.

What I'd ideally like to have is a Linux version of showmypc.com's no-brainer application.  That is, both ends run the app, the user seeking support clicks a button and gets a password.  The user doing support enters that password.  Both client apps contact the central server which negotiates setting up a SSH tunnel and then launches VNC server and viewer apps 

Is anyone aware of something like that?  Nothing that requires any configuration.

---

