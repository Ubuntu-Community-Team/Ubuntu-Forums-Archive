---
title: "Cheese Webcan Booth problems"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-05-20
Cheese worked really well for me with my existing set up in 10.10. Now, however, my camera will not show a picture and so cannot take photos. My camera is USB2.0 2MP UVCAF. I am also having problems with the sound....it is very crackly.....maybe I should go back to 10.10.

---

### Post by no2498 on 2011-05-20
this is the first ? in the cheese help FAQ'S

open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by dunbrokin on 2011-05-20
> **no2498 said:**
> 

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

Thanks for that....never thought of looking there...sorry!

I have v4l2...but not v4l....plugin is already on autodetect.

Result is the same.....no picture no matter what I try.

Is there some driver that I need to load?

---

### Post by no2498 on 2011-05-21
99.9% of the drivers are in the kernel

open a terminal type dmesg click enter
after it stops type lsusb click enter
that should give you a number and name of the cam just in case you need a driver

retry cheese

---

### Post by dunbrokin on 2011-05-21
> **no2498 said:**
> 99.9% of the drivers are in the kernel

open a terminal type dmesg click enter
after it stops type lsusb click enter
that should give you a number and name of the cam just in case you need a driver

retry cheese

Thanks for that. As my webcam was working under 10.10, I assume that the driver is in the new kernal. In any event, Cheese can see the camera....it just wont show a proper picture....just black....so everything works...I can even take a photo...but everything is black.

---

### Post by dunbrokin on 2011-05-22
Cheese is very unresponsive and sluggish on my machine....this was not the case in 10.10.

---

### Post by no2498 on 2011-05-22
try this program wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

if you look you can get it in a deb file 

also in your package manager install v4l2ucp

it comes up in system preferences as video4linux control panel
you can set some cam settings in it

---

### Post by dunbrokin on 2011-05-24
OK, I have found what the problem is....when I logged on as Ubuntu Classic, I was able to use Cheese properly (both the sound and the video - see question about the sound aspect under Multimedia & Video)....both were as per 10.10.

However, then I did an update and after the updates loaded (and still in Ubuntu Classic), Cheese no longer worked properly and reverted to the original problem state.....Bugger!


Weird!!....I clicked on it again now (in classic mode)...just to see what would happen....and I'll be darned...the crazy thing worked....I am stumped!

---

### Post by no2498 on 2011-05-24
glad it started working
the up date must have helped

---

### Post by dunbrokin on 2011-05-24
> **no2498 said:**
> glad it started working
the up date must have helped

Nope...it has not started working properly....it is an intermittent bug which seems to occur on a random basis...well, I have not found the pattern yet.

---

### Post by no2498 on 2011-05-25
run gstreamer-properties again

i had problems and had to do it 7 or 8 times

---

### Post by dunbrokin on 2011-07-23
Am I the only one who is having problems with my webcam in 11.04....I have even bought a new webcam...it seemed to work ok at the start, now it is back to square one....It can be detected...but all I get (most of the time) is a black screen.....very frustrating....this was working perfectly in 10.10....it has been 6 weeks or so since I updated to 11.04...and no webcam. Not looking good for an Ubuntu roll out to the average user I am afraid.

With Guvcview, I get the following error:Unable to start with minimum setup

---

### Post by no2498 on 2011-07-23
in Guvcview i had to set the pics to jpg video code to mpeg format to avi

---

### Post by dunbrokin on 2011-07-23
> **no2498 said:**
> in Guvcview i had to set the pics to jpg video code to mpeg format to avi

Already set to that in mine...but makes no difference ...when I hit Cap.image, nothing happens.

---

### Post by no2498 on 2011-07-23
put any program name at the end of this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so program name

also you have the win 32 code's installed
 or have you did this

sudo apt-get install ubuntu-restricted-extras

---

### Post by no2498 on 2011-07-23
also look in your home folder for the pics

---

### Post by Smilax on 2011-07-23
change the *resolution* under preferences to a lower setting

---

### Post by dunbrokin on 2011-07-23
> **no2498 said:**
> put any program name at the end of this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so program name

also you have the win 32 code's installed
 or have you did this

sudo apt-get install ubuntu-restricted-extras

Restricted already installed....LD_PRELOAD etc....no difference still blank screen with cheese.

---

### Post by dunbrokin on 2011-07-23
> **Smilax said:**
> change the *resolution* under preferences to a lower setting

No difference.

---

### Post by dunbrokin on 2011-07-23
> **no2498 said:**
> also look in your home folder for the pics

None there.

---

### Post by dunbrokin on 2011-07-23
Does this help:

 pj-indulgence kernel: [14807.687273] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Jul 24 01:18:44 pj-indulgence kernel: [14807.711372] uvcvideo: Failed to query (131) UVC probe control : -32 (exp. 26).
Jul 24 01:18:44 pj-indulgence kernel: [14808.167099] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Jul 24 01:18:44 pj-indulgence kernel: [14808.207660] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Jul 24 01:19:00 pj-indulgence kernel: [14823.694977] BUG: unable to handle kernel paging request at 00100104
Jul 24 01:19:00 pj-indulgence kernel: [14823.695021] IP: [<f8d717b2>] uvc_queue_cancel+0x42/0xa0 [uvcvideo]
Jul 24 01:19:00 pj-indulgence kernel: [14823.695064] *pdpt = 0000000029f1a001 *pde = 0000000000000000 
Jul 24 01:19:00 pj-indulgence kernel: [14823.695099] Oops: 0002 [#1] SMP 
Jul 24 01:19:00 pj-indulgence kernel: [14823.695123] last sysfs file: /sys/devices/virtual/dmi/id/board_version
Jul 24 01:19:00 pj-indulgence kernel: [14823.695159] Modules linked in: binfmt_misc cryptd aes_i586 aes_generic vboxnetadp vboxnetflt vboxdrv parport_pc ppdev nfsd exportfs nfs lockd fscache nfs_acl auth_rpcgss sunrpc snd_hda_codec_hdmi snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_usb_audio snd_hwdep snd_usbmidi_lib snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event i915 snd_seq arc4 uvcvideo snd_timer videodev drm_kms_helper iwlagn usb_storage iwlcore uas snd_seq_device mac80211 hid_logitech btusb cfg80211 snd bluetooth drm joydev ff_memless i2c_algo_bit soundcore snd_page_alloc usbhid video hid psmouse serio_raw dell_laptop dell_wmi dcdbas sparse_keymap lp parport firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci ahci libahci e1000e
Jul 24 01:19:00 pj-indulgence kernel: [14823.695630] 
Jul 24 01:19:00 pj-indulgence kernel: [14823.695642] Pid: 12137, comm: cheese Not tainted 2.6.38-10-generic-pae #46-Ubuntu Dell Inc. Latitude E4300                  /0D201R
Jul 24 01:19:00 pj-indulgence kernel: [14823.695715] EIP: 0060:[<f8d717b2>] EFLAGS: 00210006 CPU: 0
Jul 24 01:19:00 pj-indulgence kernel: [14823.695748] EIP is at uvc_queue_cancel+0x42/0xa0 [uvcvideo]
Jul 24 01:19:00 pj-indulgence kernel: [14823.695779] EAX: ef3da0e8 EBX: ef3da080 ECX: 00200200 EDX: 00000003
Jul 24 01:19:00 pj-indulgence kernel: [14823.695812] ESI: ef3dae38 EDI: 00100100 EBP: efdafefc ESP: efdafee0
Jul 24 01:19:00 pj-indulgence kernel: [14823.695845]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jul 24 01:19:00 pj-indulgence kernel: [14823.695874] Process cheese (pid: 12137, ti=efdae000 task=e75bd860 task.ti=efdae000)
Jul 24 01:19:00 pj-indulgence kernel: [14823.695914] Stack:
Jul 24 01:19:00 pj-indulgence kernel: [14823.695926]  00000000 00000000 00200296 ef3dae2c ef3da080 ef3dae18 00000000 efdaff10
Jul 24 01:19:00 pj-indulgence kernel: [14823.695984]  f8d71839 ef3da000 ef3da000 edfb9a80 efdaff1c f8d74e83 efd9d8f0 efdaff34
Jul 24 01:19:00 pj-indulgence kernel: [14823.696042]  f8d71a49 00000008 e8c0fa00 edfb9a80 e7e6ae80 efdaff44 f8cff1b2 edfb9a80
Jul 24 01:19:00 pj-indulgence kernel: [14823.696099] Call Trace:
Jul 24 01:19:00 pj-indulgence kernel: [14823.696120]  [<f8d71839>] uvc_queue_enable+0x29/0xa0 [uvcvideo]
Jul 24 01:19:00 pj-indulgence kernel: [14823.696156]  [<f8d74e83>] uvc_video_enable+0x63/0x70 [uvcvideo]
Jul 24 01:19:00 pj-indulgence kernel: [14823.696191]  [<f8d71a49>] uvc_v4l2_release+0x89/0xd0 [uvcvideo]
Jul 24 01:19:00 pj-indulgence kernel: [14823.696227]  [<f8cff1b2>] v4l2_release+0x42/0x60 [videodev]
Jul 24 01:19:00 pj-indulgence kernel: [14823.696261]  [<c1133b25>] __fput+0x95/0x1c0
Jul 24 01:19:00 pj-indulgence kernel: [14823.696285]  [<c1133c6d>] fput+0x1d/0x30
Jul 24 01:19:00 pj-indulgence kernel: [14823.696308]  [<c11309ae>] filp_close+0x4e/0x70
Jul 24 01:19:00 pj-indulgence kernel: [14823.696334]  [<c11311d5>] sys_close+0x75/0xd0
Jul 24 01:19:00 pj-indulgence kernel: [14823.696359]  [<c100ab5f>] sysenter_do_call+0x12/0x28
Jul 24 01:19:00 pj-indulgence kernel: [14823.696386] Code: 55 e8 8d b3 b8 0d 00 00 89 45 f0 e8 d9 07 7c c8 89 45 ec 8b 83 b8 0d 00 00 39 c6 74 45 8d 74 26 00 8b 48 04 ba 03 00 00 00 8b 38 <89> 4f 04 89 39 b9 01 00 00 00 c7 00 00 01 10 00 c7 40 04 00 02 
Jul 24 01:19:00 pj-indulgence kernel: [14823.696638] EIP: [<f8d717b2>] uvc_queue_cancel+0x42/0xa0 [uvcvideo] SS:ESP 0068:efdafee0
Jul 24 01:19:00 pj-indulgence kernel: [14823.696690] CR2: 0000000000100104
Jul 24 01:19:00 pj-indulgence kernel: [14823.745265] ---[ end trace 7a1a2adfff25fbd4 ]---
Jul 24 01:19:00 pj-indulgence kernel: [14824.056474] dell-wmi: Received unknown WMI event (0x11)
Jul 24 01:19:27 pj-indulgence acpid: client 19801[0:0] has disconnected
Jul 24 01:19:27 pj-indulgence acpid: client connected from 12462[0:0]

---

### Post by dunbrokin on 2011-07-23
Or this

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

---

### Post by no2498 on 2011-07-24
every one gets some of these
i see you get some i dont
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


try this i seen it some time ago

BicyclerBoy 
Skinny Soy Caramel Ubuntu

  
Join Date: Apr 2009
Location: Aotearoha
 Beans: 656 
 Ubuntu 10.04 Lucid Lynx 	Re: Webcam not working (Dell SP2208WFP) 
Try from terminal
rmmod uvcvideo
 modprobe uvcvideo
 dmseg

 Repeat these (<5) until the camera initialises okay..

 You could try this ppa to update some v4l components..

[https://launchpad.net/~libv4l/+archi...ilter=maverick](https://launchpad.net/~libv4l/+archi...ilter=maverick)


sudo rmmod uvcvideo
sudo modprobe uvcvideo

---

### Post by dunbrokin on 2011-07-24
> **no2498 said:**
> 

  

rmmod uvcvideo
 modprobe uvcvideo
 dmseg




Thanks, this is what I get...

pj@pj:~$ rmmod uvcvideo
ERROR: Module uvcvideo is in use
pj@pj:~$ modprobe uvcvideo
pj@pj:~$ dmseg
No command 'dmseg' found, did you mean:
 Command 'mmseg' from package 'sunpinyin-utils' (universe)
 Command 'dmesg' from package 'util-linux' (main)
dmseg: command not found


The lunchpad link you gave does not exist it seems.

---

### Post by no2498 on 2011-07-25
they ubuntu/linux has been dropping v4l to use v4l2 only
as for dmesg that should still work

you do need to have skype and things turned off
you can put any program name at the end of this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so

---

### Post by dunbrokin on 2011-07-25
This was part of the outcome of dmesg:

The inbuilt camera on my laptop works no problem....but the plug in does not work. It is a new webcam (bought last week) and it did work for the first few times and then stopped. This is what happened with my old one...and I assumed there was something wrong with it...so replaced it.

[  733.288301] usb 2-4: new high speed USB device using ehci_hcd and address 6
[  733.450154] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62e0)
[  733.454912] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input18
[  733.486768] 6:3:1: cannot get freq at ep 0x84
[  733.611916] 6:3:1: cannot get freq at ep 0x84
[  733.643018] 6:3:1: cannot get freq at ep 0x84
[  733.758403] uvcvideo: Failed to query (GET_MAX) UVC control 3 on unit 3: -32 (exp. 2).
[  733.777051] uvcvideo: Failed to query (GET_DEF) UVC control 9 on unit 3: -32 (exp. 2).
[  733.779787] uvcvideo: Failed to query (GET_DEF) UVC control 9 on unit 3: -32 (exp. 2).
[  733.785200] uvcvideo: Failed to query (GET_RES) UVC control 9 on unit 3: -32 (exp. 2).
[  733.821432] uvcvideo: Failed to query (GET_RES) UVC control 4 on unit 1: -32 (exp. 4).
[  733.827921] uvcvideo: Failed to query (GET_DEF) UVC control 13 on unit 1: -32 (exp. 8).
[  733.837932] uvcvideo: Failed to query (GET_MIN) UVC control 6 on unit 1: -32 (exp. 2).
[  738.260033] uvcvideo: Failed to query (131) UVC probe control : -32 (exp. 26).
[ 3821.350545] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1)
[ 3821.350551] Disabling lock debugging due to kernel taint
[ 3821.351033] CPU1: Core temperature/speed normal
[ 3899.988035] [Hardware Error]: Machine check events logged
[14479.591333] exe (28705): /proc/28705/oom_adj is deprecated, please use /proc/28705/oom_score_adj instead.
[21529.757567] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).
[21529.763934] uvcvideo: Failed to query (131) UVC probe control : -32 (exp. 26).
[21566.094312] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[21566.096953] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[21594.386434] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[21594.393931] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[21603.154953] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[21610.137269] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[21610.189390] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[60195.095476] usbcore: deregistering interface driver uvcvideo
[60209.728972] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_0.3M (0c45:63fe)
[60209.770638] input: Laptop_Integrated_Webcam_0.3M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input19
[60209.770870] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62e0)
[60209.777896] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input20
[60209.778059] usbcore: registered new interface driver uvcvideo
[60209.778065] USB Video Class driver (v1.0.0)

---

### Post by dunbrokin on 2011-07-25
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

Does work...in that the light on the camera comes on....but no picture appears.

---

### Post by no2498 on 2011-07-26
open cheese click edit preferences try setting the size smaller 
this program works pretty good
guvcveiw  
it finds the mic

---

### Post by dunbrokin on 2011-07-26
> **no2498 said:**
> open cheese click edit preferences try setting the size smaller 
this program works pretty good
guvcveiw  
it finds the mic

Thanks for your help, but I am afraid that neither of those suggestions make any difference.

---

### Post by no2498 on 2011-07-27
try gstreamer-properties again

---

### Post by dunbrokin on 2011-07-27
> **no2498 said:**
> try gstreamer-properties again

~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(2125): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2:
system error: Input/output error]

---

### Post by dunbrokin on 2011-07-27
...and again...

$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error setting pixformat: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video1' cannot capture at 1600x1200 [gstv4l2object.c(2093): gst_v4l2_object_set_format (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
Call to S_FMT failed for YUYV @ 1600x1200: Input/output error]

---

### Post by dunbrokin on 2011-07-27
Or even....

~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not get buffers from device '/dev/video1'. [gstv4l2bufferpool.c(404): gst_v4l2_buffer_pool_new (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src3:
error requesting 2 buffers: Device or resource busy]

---

### Post by no2498 on 2011-07-27
do you have any cam programs open like skype

---

### Post by dunbrokin on 2011-07-27
> **no2498 said:**
> do you have any cam programs open like skype

Nope, I rebooted my machine and closed Skype before doing that last one....

---

### Post by no2498 on 2011-07-27
unplug one of the cams

---

### Post by dunbrokin on 2011-07-27
> **no2498 said:**
> unplug one of the cams

The inbuilt one works whether I leave the other one plugged or unplugged.....its the non inbuilt one that is the problem.

---

### Post by no2498 on 2011-07-27
the fn f4 keys is only for the built in cam
do both cams come up in lsusb
and in gstreamer-properties  what cam is listed 
as cheese uses gstreamer to run the cam

---

### Post by dunbrokin on 2011-07-27
> **no2498 said:**
> the fn f4 keys is only for the built in cam
do both cams come up in lsusb
and in gstreamer-properties  what cam is listed 
as cheese uses gstreamer to run the cam

That is the problem....sometimes the plug in shows and sometimes it does not...I cannot find a pattern. But, even when it shows on cheese or on gstreamer-properties, all you can see is a black screen....no picture.

---

### Post by halibaitor on 2011-07-27
> **no2498 said:**
> try this program wxcam

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

if you look you can get it in a deb file 

also in your package manager install v4l2ucp

it comes up in system preferences as video4linux control panel
you can set some cam settings in it

I have been looking for a web-cam program that works better than Cheese, so I downloaded wxcam.  When attempting to install I get an error because libasound2 is not >>1.0.24.1.  I only have version 1.0.22, and that is all that is available in the package manager.  How do I go about getting the newer version?

---

### Post by dunbrokin on 2011-07-28
This is extremely frustrating....I had forgotten to install Medibuntu and now installed it....my camera worked with Cheese straight off...perfect. I rebooted my computer to make sure.....and bu**er me....the darn thing stopped working again.....AAAARRRGGGHHHHH!!!!!! This is ridiculous...what is happening here?

---

### Post by no2498 on 2011-07-28
halibaitor
look for browse all files

i use ubuntu 10.04 the best i could get loaded was 1.0.6
that is with getdeb


dunbrokin
best i can say is i had to do

gstreamer-properties

like 7 or 8 times

---

### Post by no2498 on 2011-07-28
[http://ubuntuforums.org/showthread.php?t=1777612](http://ubuntuforums.org/showthread.php?t=1777612)

see if this helps

---

### Post by dunbrokin on 2011-07-28
> **no2498 said:**
> halibaitor
look for browse all files

i use ubuntu 10.04 the best i could get loaded was 1.0.6
that is with getdeb


dunbrokin
best i can say is i had to do

gstreamer-properties

like 7 or 8 times


Dude, I have done it a 100 times....the new kernel, 11.04,  (in my opinion) has got some serious issues....what else can explain this?

---

### Post by dunbrokin on 2011-07-28
> **no2498 said:**
> [http://ubuntuforums.org/showthread.php?t=1777612](http://ubuntuforums.org/showthread.php?t=1777612)

see if this helps

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gstreamer0.10-gconf
E: Couldn't find any package by regex 'gstreamer0.10-gconf'

---

### Post by no2498 on 2011-07-28
think your on to something now

E: Unable to locate package gstreamer0.10-gconf
 E: Couldn't find any package by regex 'gstreamer0.10-gconf'
 __________________

---

### Post by halibaitor on 2011-07-28
> **no2498 said:**
> halibaitor
look for browse all files
i use ubuntu 10.04 the best i could get loaded was 1.0.6
that is with getdeb


Sorry to be such a pain...  I don't know what you mean by the "browse all files"..  where am I to look for that feature?

I did manage to install getdeb, but can't figure out where it went after the install.  I did a re-boot on the computer, but it still doesn't show, so all I can access is the same old versions of Libasound2.  

I would love to be able to find version 1.0.6.  I'm wondering, if the software has advanced to that point, why some type of later version isn't available in the normal package manager.

---

### Post by no2498 on 2011-07-28
just under the down load 

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by dunbrokin on 2011-07-28
> **no2498 said:**
> think your on to something now

E: Unable to locate package gstreamer0.10-gconf
 E: Couldn't find any package by regex 'gstreamer0.10-gconf'
 __________________

Thanks, so where do I go from here?

---

### Post by no2498 on 2011-07-29
myself im not sure you may need to ask on their post
they said they fixed it
 sorry i cant help any more than that

---

### Post by dunbrokin on 2011-08-03
This is really driving me nuts. I bought a new webcam. Top of the range Logictech as I figured that the cheap ones that I was using were not working properly with the new 11.04 kernel, though they worked perfectly with 10.10. Same problem, worked great for a day or so...even took some photos etc. Now, dead. The I have tired it under Cheese, guvcview and gstreamer-properties. Sometimes, it is just not recognised, sometimes I get the webcam light to turn on but no picture. I am on a Dell Latitude E4300. Surely, I am not the only one having this problem. I was trying to persuade a friend to give up Windows and try Ubuntu...but when he heard about my saga with the webcam he said :&^%$ it, forget it, I can't be putting up with that kind of hassle"....Hmmm!

The crazy thing is that the internal webacam works first time every time...but not the external one.

---

### Post by dunbrokin on 2011-08-04
Some of the error messages I have had recently:


(gstreamer-properties:15693): GStreamer-CRITICAL **: Failed to deactivate pad v4l2src9:src, very bad

(gstreamer-properties:15693): GStreamer-CRITICAL **:
Trying to dispose element pipeline8, but it is in PAUSED instead of the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.
This problem may also be caused by a refcounting bug in the
application or some element.

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video1' cannot capture at 1920x1080 [gstv4l2object.c(2093): gst_v4l2_object_set_format (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
Call to S_FMT failed for YUYV @ 1920x1080: Input/output error]

---

### Post by dunbrokin on 2011-08-04
bump!

---

### Post by dunbrokin on 2011-08-05
Does this help any?


Aug  5 22:06:29 pj-indulgence kernel: [  390.653360] dell-wmi: Received unknown WMI event (0x11)
Aug  5 22:07:23 pj-indulgence kernel: [  445.197321] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Aug  5 22:07:40 pj-indulgence kernel: [  461.436102] usb 2-4: new high speed USB device using ehci_hcd and address 7
Aug  5 22:07:41 pj-indulgence kernel: [  462.315823] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0821)
Aug  5 22:07:41 pj-indulgence kernel: [  462.329180] input: UVC Camera (046d:0821) as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.2/input/input18
Aug  5 22:07:52 pj-indulgence kernel: [  473.577190] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:13:31 pj-indulgence kernel: [  812.772535] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:13:36 pj-indulgence kernel: [  817.622782] usb 2-4: USB disconnect, address 7
Aug  5 22:13:43 pj-indulgence kernel: [  824.736064] usb 2-4: new high speed USB device using ehci_hcd and address 8
Aug  5 22:13:44 pj-indulgence kernel: [  825.562152] 8:1:2: cannot set freq 24000 to ep 0x86
Aug  5 22:13:44 pj-indulgence kernel: [  825.612319] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0821)
Aug  5 22:13:44 pj-indulgence kernel: [  825.617729] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
Aug  5 22:13:44 pj-indulgence kernel: [  825.622099] input: UVC Camera (046d:0821) as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.2/input/input19
Aug  5 22:13:44 pj-indulgence kernel: [  825.804923] uvcvideo: Failed to query (GET_MAX) UVC control 10 on unit 2: -32 (exp. 2).
Aug  5 22:13:44 pj-indulgence kernel: [  825.812640] uvcvideo: Failed to query (GET_RES) UVC control 10 on unit 2: -32 (exp. 2).
Aug  5 22:13:44 pj-indulgence kernel: [  825.850503] uvcvideo: Failed to query (GET_MAX) UVC control 13 on unit 1: -32 (exp. 8).
Aug  5 22:14:17 pj-indulgence kernel: [  858.498001] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.514603] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.565242] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.595118] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.612042] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.628450] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.649289] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.707893] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.729035] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.763425] uvcvideo: Failed to query (131) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  858.954021] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  859.075291] uvcvideo: Failed to query (131) UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  859.164549] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:17 pj-indulgence kernel: [  859.222319] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:18 pj-indulgence kernel: [  859.347026] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
Aug  5 22:14:18 pj-indulgence kernel: [  859.414276] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:18 pj-indulgence kernel: [  859.444132] uvcvideo: Failed to query (130) UVC probe control : -32 (exp. 26).
Aug  5 22:14:18 pj-indulgence kernel: [  859.482155] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
Aug  5 22:14:18 pj-indulgence kernel: [  859.540536] uvcvideo: Failed to set UVC commit control : -32 (exp. 26).
Aug  5 22:14:33 pj-indulgence kernel: [  874.563564] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).

---

