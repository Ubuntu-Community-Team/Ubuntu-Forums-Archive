---
title: "64 bit Skype webcam"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by gordon3056 on 2010-05-17
I'm trying to get my logitech webcam to work for video and mic with Skype with no luck I think I'm too used to windows

---

### Post by BandD on 2010-05-17
does the webcam have a built in mic? or is the mic seperate?

i might know of a fix for the webcam but i'll have to wait until i get home to trak it down.

---

### Post by gordon3056 on 2010-05-17
Yes it does THANKS

---

### Post by BandD on 2010-05-17
I don't have too much experience with usb microphones.  But I think there is a way to tell PulseAudio server to use the usb device rather than the sound card line-in/mic.  I think if you install either PulseAudio Device Chooser or PulseAudio Volume Control (go to software center and search "pulse" they should be the 2nd and 3rd choices) you'll be able to select the usb microphone on an "input" tab.

You can this fix for the video.  If it works then I can tell you how to make it permenant.  Close and exit skype completely.  Go to Applications --> Accessories --> Terminal and type in ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
When skype opens up go to options --> viedo devices and click test.  Let me know if that gets the video working.

---

### Post by Directive 4 on 2010-05-17
does it work with cheese (from software centre)

---

### Post by gordon3056 on 2010-05-17
The video hasn't worked haven't tried the mic yet got this though

gordon@ubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

---

### Post by kimberley on 2010-05-18
I have the same problem as above ie I cannot get a picture using  my Logitech Quick cam messenger on Skype or aMSN although it works on Cheese.  I have upgraded to the latest version 10.4.

When I entered the code below as suggested above by BAND D  on the terminal Skype came up and when I entered password I got a test picture OK under the video option.  However. when I closed the terminal and opened Skype in the normal way I have NO PICTURE.Can anyone please tell me what to do now.  I am new to Linux.  

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by BandD on 2010-05-18
I could be wrong but I think you might need to install the 32-bit version of "canberra-gtk-module".  You can check out the little program developed by a forum member that will do this automatically [here]("http://ubuntuforums.org/showthread.php?t=474790")  It's called getlibs.  It might work.  See the first usage example on that thread and give it a try after downloading it.

---

### Post by BandD on 2010-05-18
> **kimberley said:**
> I have the same problem as above ie I cannot get a picture using  my Logitech Quick cam messenger on Skype or aMSN although it works on Cheese.  I have upgraded to the latest version 10.4.

When I entered the code below as suggested above by BAND D  on the terminal Skype came up and when I entered password I got a test picture OK under the video option.  However. when I closed the terminal and opened Skype in the normal way I have NO PICTURE.Can anyone please tell me what to do now.  I am new to Linux.  

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


Here's how to make this piece of code permanent.  In a terminal type ```
sudo gedit /usr/bin/skype2
```

Then when the text editor opens copy and paste ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```. Save and close the text editor.

In a terminal: ```
 sudo chmod 755 /usr/bin/skype2
``` in order to make the file executable by all users but only root can change the file.

Then right click on the appilcations menu and select "edit menus".  Click on the internet section in the left column, then select Skype in the right column.  Click on Properties.  In the command box write skype2. Close the menu editor.  

Go to applications --> skype to launch skype and test it out.  It should work.

---

### Post by David Oxland on 2010-05-18
BandD and Kimberly
I've been watching this as it's my problem too.
And using the script "LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype"
 is the one that works for me(copied from elsewhere) but using the making code permanent procedure went along fine until  I did and got this

david@david-desktop:~$ skype2
bash: /usr/bin/skype2: Permission denied

I think I'm on the right track, thanks very much,
now just need to give permission?

One last bit of help with permissions would be appreciated
David

---

### Post by BandD on 2010-05-18
Sorry I forgot to add a step to change the permissions.  

```
sudo chmod 755 /usr/bin/skype2
```

That should do it.

---

### Post by kimberley on 2010-05-19
[COLOR=Red]**BAND D  Thanks a million!**[/COLOR]  Your explanation was straightforward and after many, many months of struggling my web cam now works on Skype.  I am over the moon as I have family dotted around the globe.

---

### Post by David Oxland on 2010-05-19
BanD my thanks too!
Working fine!

---

### Post by mikewhatever on 2010-05-19
> **gordon3056 said:**
> I'm trying to get my logitech webcam to work for video and mic with Skype with no luck I think I'm too used to windows

Try opening the sound preferences, Input tab. Can you see your webcam there? If you do, click it to select as your input device.

---

### Post by David Oxland on 2010-05-19
> **mikewhatever said:**
> Try opening the sound preferences, Input tab. Can you see your webcam there? If you do, click it to select as your input device.

Mikewhatever
I've had this problem too with former installs of Skype and while it works to choose the input and videocam, what is still is a bother, is that most every start up of computer results in it defaulting back to "Internal Audio Analog Stero" and I've not found a way of making  a choice permanent. Just keep getting caught when a contact says "can't hear you". Something keeps changing it back.

---

### Post by kimberley on 2010-05-23
[SIZE=3][COLOR=Red][COLOR=Black]Thanks to Band D my logitech camera now works perfectly on Skype but I now have [COLOR=Red]no sound!!

[/COLOR][/COLOR][/COLOR][/SIZE][SIZE=3][COLOR=Black]I know I will get there eventually.....................[/COLOR][/SIZE][SIZE=3]again with help[/SIZE]

---

### Post by BandD on 2010-05-23
> **kimberley said:**
> [SIZE=3][COLOR=Red][COLOR=Black]Thanks to Band D my logitech camera now works perfectly on Skype but I now have [COLOR=Red]no sound!!

[/COLOR][/COLOR][/COLOR][/SIZE][SIZE=3][COLOR=Black]I know I will get there eventually.....................[/COLOR][/SIZE][SIZE=3]again with help[/SIZE]

I suggest opening a new thread for this since it's not related to a webcam issue.  I'll keep an eye out for the new thread that you start and see if I can help.

---

### Post by BandD on 2010-06-02
@ gordon

Plug in your camera.  Try running  ```
gstreamer-properties
``` in a terminal.  When the window opens, click on the video tab.  In the Default Input section tell me what is listed in the plugin drop down menu and also try the test button and let me know if the video works there.

---

### Post by gordon3056 on 2010-06-02
Video for Linux 2 (V4|2) -> this does the same as :-

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

The video good for a second then goes dark. But the terminal goes wild with line after line of :-

libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff

Others listed  Video for Linux 2 (V4|)

               Custom

               Test Imput

---

### Post by BandD on 2010-06-02
Is there an option that says Video for Linux (v4l)?  Try selecting that and see if there is any improvement.  

After searching google with the specific error that you listed it doesn't seem that there is a fix yet.  It seeems there is active development in trying to address this failure, but everything is being reverse engineered and the progress seems to be slow.  I'm sorry to say that it may very well be that your camera just doesn't have linux support yet.

You could try contacting Logitech and asking them to open up their drivers or requesting linux support for you device.

---

### Post by gordon3056 on 2010-06-03
My webcam works with cheese and aMSN do think this is a skype beta issue and that future releases could solve this problem

---

### Post by forestG on 2010-06-03
There is a slight possibility that your camera will work during a video call but not in the test application embeded in Skype. That was the case for me for quite some time. Sometimes the test camera application is not working. Maybe you should check whether your camera is the by default selected camera or not. 

(P.S) Have you tried running skype after plugging in the camera?

---

### Post by BandD on 2010-06-03
Do you get any error messages when you run cheese from the terminal?  I didn't realize this camera was working with cheese and aMSN...

Which version of skype do you have installed?

---

### Post by gordon3056 on 2010-06-03
When I run cheese from the terminal I get :-

libv4lconvert: Error decompressing JPEG: unknown huffman code: 0000ffff

The same as running skype from the terminal and the video is still dark but earlier in the day it was fine ????????

Skype 2.1 Beta 2 for Linux

---

### Post by no2498 on 2010-06-06
? what flash player you have installed there is a 32 bit and a 64 bit flash player

hope this helps

---

### Post by gordon3056 on 2010-06-06
I've downloaded "libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz" how do I install it ?

---

### Post by Muhammad Ahmed on 2010-06-06
try 
untar that and copy the file that comes out to
/usr/lib/mozilla/plugins/


try sudo cp <drop the file here that is extracted> /usr/lib/mozilla/plugins/

---

### Post by no2498 on 2010-06-06
think he needs to uninstall the 32 bit first

---

### Post by BandD on 2010-06-07
What does flash have to do with with this webcam working in skype?

---

### Post by Arrgoss on 2010-10-09
Hey, thanks everyone who's helping in this thread...

I have the same problem (Logitech Quick cam not working in Skype) only since I upgraded to Lucid Lynx. The webcam works with Cheese and when I run Skype from the terminal with 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
I get the following message when I try to test the webcam:
```
X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes)
```

Any idea how to get around this?

---

