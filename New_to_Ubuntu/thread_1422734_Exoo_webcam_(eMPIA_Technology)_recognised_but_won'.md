---
title: "Exoo webcam (eMPIA Technology) recognised but won't show picture"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Jalke on 2010-03-05
Hi,
My webcam (Exoo M068 is what it said on the packaging) is recognised by my laptop (Ubuntu 9.10) but it won't seem to work in any programs (skype, cheese, luvcview).  

lsusb gives the following device ID:
Bus 007 Device 005: ID eb1a:2571 eMPIA Technology, Inc. 

lsmod | grep uvc gives me:

uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev

Any idea as to what to do?  The overseas mother-in-law has been bugging me to get it to work so that she can see our new daughter...  

I've got a bit of experience on Linux but am by no means an expert.

---

### Post by no2498 on 2010-03-05
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 and v4l2 click the bottom test button for each 1

cheese has a very nice help file in it

---

### Post by Jalke on 2010-03-06
Thanks for the response.  Video for Linux (v4l) gave me: 
[I]Could not get/set settings from/on resource.
[/I]
v4l2 gave me the Testing Pipeline box.  Nothing happened, it just kept testing.

cheese --verbose gave me:
[I]Cheese 2.28.1 
Probing devices with HAL...
Found device eb1a:2571, getting capabilities...
Detected v4l2 device: UVC Camera (eb1a:2571)
Driver: uvcvideo, version: 256
Capabilities: 0x04000001

Probing supported video formats...
[/I]
I don't see any video image but just coloured bars/rectangles.  

Any other ideas?

---

### Post by mkljun on 2010-03-19
Hi,

I have another problem with the same camera. 

I just plugged it in and it WORKS in cheese and it even works when I test it in Skype. But it doesn't work during the call in Skype. 

Ubuntu 9.10
Skype 2.1.0.81

```

$ lsusb
Bus 001 Device 015: ID eb1a:2571 eMPIA Technology, Inc. 
Bus 001 Device 002: ID 054c:01bd Sony Corp. MRW62E Multi-Card Reader/Writer
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

$ cheese --verbose
Cheese 2.28.1 
Probing devices with HAL...
Found device eb1a:2571, getting capabilities...
Detected v4l2 device: UVC Camera (eb1a:2571)
Driver: uvcvideo, version: 256
Capabilities: 0x04000001

Found device eb1a:2571, getting capabilities...

** (cheese:3240): WARNING **: Failed to open /dev/video0: No such file or directory
Probing supported video formats...
Device: UVC Camera (eb1a:2571) (/dev/video1)
video/x-raw-yuv 640 x 480 num_framerates 1
30/1 video/x-raw-yuv 352 x 288 num_framerates 1
.........................
video/x-raw-rgb 160 x 120 num_framerates 1
30/1 already added, skipping

v4l2src name=video_source device=/dev/video1 ! capsfilter name=capsfilter 
caps=video/x-raw-rgb,width=640,height=480,framerate=30/1;video/x-raw-yuv,
width=640,height=480,framerate=30/1 ! identity

```

The picture is great. I can take photos, record video, etc. 
In Skype I can see the video under Options if I click on Test button. But it won't work during the call :(. Any ideas?

mk

---

### Post by gordintoronto on 2010-03-19
Run Skype by entering this command in Terminal:

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by mkljun on 2010-03-19
> **gordintoronto said:**
> Run Skype by entering this command in Terminal:

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

Already tried it.

Also tried adding XLIB_SKIP_ARGB_VISUALS in the environment before firing  Skype:

```
export XLIB_SKIP_ARGB_VISUALS=1
```

I also added this code to ~/.Skype/username/config.xml inside <config></config> tags:

```
<Video>
<CaptureHeight>480</CaptureHeight>
<CaptureWidth>640</CaptureWidth>
<RecvPolicy>callpolicy</RecvPolicy>
</Video>
```

As I mentioned, I can see the video in Skype Options window, but in the Call window the video is just gray. See screenshots.

---

### Post by mkljun on 2010-03-19
Solved!

I restarted the PC and it works. Just running skype from the command line without loading anything before.

I still have the <video> section in the conf.xml file.

---

### Post by no2498 on 2010-03-19
Jalke
try this
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by mkljun on 2010-03-19
> **no2498 said:**
> Jalke
try this
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

The end quote is missing in your command.

Jalke

I tried a lot of different solutions found on ubuntuforums.org and on skype forums. All can be summarized in three (or four) solutions:

1. Try to run this command from the terminal:
for skype
```
$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
or cheese
```
$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
```
or you can use any other software that uses camera.

2. Try to add a variable to the environment before starting skype (from the terminal again)
```
$ export XLIB_SKIP_ARGB_VISUALS=1
$ skype
```
(or you can start any other software that uses the camera)

3. Enter the video section to the config.xml 
```
$ gedit ~/.Skype/<yourskypeusername>/config.xml
```
add this right before the last line </config>
```
  <Video>
    <CaptureHeight>480</CaptureHeight>
    <CaptureWidth>640</CaptureWidth>
    <RecvPolicy>callpolicy</RecvPolicy>
  </Video>

``` 

4. Try restarting the PC :). It worked for me!


If the options 1. or 2. work, a (bash/sh/csh/...) script can be written to start for example skype. A script is a simple text file that has executable permissions, which can be done like this

```
$ gedit /home/username/skype.sh
```

Now add your commands that work for you (after the shebang line - the one starting with !) in a file. For example

```
!#/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Save file, close gedit, give the file executable permissions and run the script which would start skype in this example:

```
$ chmod +x /home/username/skype.sh
$ /home/username/skype.sh
```

---

### Post by Jalke on 2010-03-20
Thanks for all the ideas but unfortunately none of them worked.  Any more ideas very welcome...

---

### Post by no2498 on 2010-03-22
does this need to be sudo
 LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so cheese

but at that it still should have come on in gstreamer-properties

---

### Post by no2498 on 2010-03-24
there is a lib
i have seen this 1 time only something like v4l1tov4l2so i have only seen it 1 time but its not loading on all computers
i installed it on the computer with 910 karmic on it
is also a make file for the preload so you do not need to do it every time
im sorry i did not copy and save them
i was looking to get my cam working
as we all know some things work for some some things dont

---

### Post by no2498 on 2010-03-24
Jalke
if you unplug the cam you may have gotten dust in 1 side of the plug
computer or cam side
i cam with someone this has happed to
hope this 1 helps

---

### Post by mkljun on 2010-03-24
> **no2498 said:**
> does this need to be sudo
 LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so cheese

but at that it still should have come on in gstreamer-properties

no, run it as a regular user

---

### Post by mkljun on 2010-03-24
> **Jalke said:**
> Thanks for all the ideas but unfortunately none of them worked.  Any more ideas very welcome...

Hmm ... are we both running the version 9.10? No ideas. It worked for me out of the box (except that gray window in Skype).

Can you test the camera on some other PC or even OS?

lp mk

---

### Post by no2498 on 2010-03-24
mkljun i was asking if the v4l1 needs to be v4l1 to v4l2

they/ubuntu put the 2 together 
he uses v4l1

---

