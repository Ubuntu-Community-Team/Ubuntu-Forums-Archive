---
title: "Camera + Tv Card"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by mastablasta on 2010-02-28
So finnaly after quite a bit of testing with various distros LiveCDs i decide to dual boot an old desktop computer with Ubuntu. This computer will be either given away or i will keep it.
 
It all worked well. However two things mentioned in title remain to be solved.
 
I checked the forums and i ofudn thread relaiting this hardware. However all are old and as i understand things changed quite a bit since then.
 
 
THE CAMERA &Skype - Philips SPC 200NC
I found the old thread dating back to 2005 on how to install the drivers for it. 
[http://ubuntuforums.org/showthread.php?t=107922](http://ubuntuforums.org/showthread.php?t=107922)
 
However as i understand the drivers already come with new version of ubuntu, and they do not need to be compiled or anything. Is this true? ALso hwo to install it then?
 
The camera (as well as TV tuner card) gets recognised by skype correctly. However when i click on test video the light on camera goes on and off and then nothing happens. Any ideas what to do here?
 
 
TV CARD - WinFast PVR 2000
 
I also found an old thread about a sound not working [http://ubuntuforums.org/showthread.php?t=96012](http://ubuntuforums.org/showthread.php?t=96012), but my card is not working at all.
I found numerous other reports that it works well in Linux ([http://www.linux.com/archive/forums/topic/336](http://www.linux.com/archive/forums/topic/336)). I installed TV Time but all it does is giving me an error saying there is no signal form device (it does seem to recognise the device). I also tried MeTV. same thing. MeTV even says there is no device.
 
What i wonder is how come any programme has a problem with the card since clearly Skype detects it. Doesn't that mean that it has the drivers installed? Or do i still need to install them? How do i do that?
 
 
 
Also some guides say that i should put some file into /etc/modules, but when i try to go to etc it says that it doesn't exist. does etc mean "some folders"?
 
 
I am guessing i will still have a lot of work to do when installing the remote controler of the card....

---

### Post by mastablasta on 2010-03-01
Bump.

---

### Post by no2498 on 2010-03-02
for your camera 
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each 1
if it comes on you need something to see it with
cheese sees most all webcams

---

### Post by mastablasta on 2010-03-05
> **no2498 said:**
> for your camera 
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each 1
if it comes on you need something to see it with
cheese sees most all webcams


well that didn't really do much. I mean when i type in that in terminal i get to choose the video input. again both are recognised - the TV tuner and the camera. So i went withthe camera and the picture appears. also in cheese i can see myself perfectly. but what about skype? when i click on options and test thecamera light turns on and off and that's it. BTW i downloaded bta skype 2.1 from their website (instead of using the one in repositories)


And how ot make the TV tuner to work. clearly it is recognised, so i am guessing that Ubuntu has drivers for it. But in TV ime it keeps saying no signal and such.

EDIT: TV TUNER although recognised does not work with gstreamer test.

---

### Post by no2498 on 2010-03-05
sorry i dont use skype i do see a lot of problems for skype
try the cam in ekiga softphone
you have it already under applications internet

---

### Post by mastablasta on 2010-03-08
Ok so i am guessing this is a Skype issue? I could try and ask for help there, although i do not knwo why the thing does not "just work" in skype.
 
What about the TV tuner, does anyone have any idea how to make it work? or which programme to use to make it work?

---

### Post by mastablasta on 2010-03-11
I was just thinking - i've been focusing on Skype a bit too much. 
 
I am wondering is it possible to use either Pidgin or default Empathy to do a video connection with Yahoo messanger?

---

### Post by mastablasta on 2010-03-15
Webcam is now SOLVED. YAY!
 
It was a skype issue sort of. Skype needs to be run like this and it works perfectly.
 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
 
More about this here:
[http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux](http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux)
 
----
 
Still haven't solved the Tv tuner issue. Can anyone help, please?

---

