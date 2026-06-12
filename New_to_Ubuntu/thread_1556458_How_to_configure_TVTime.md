---
title: "How to configure TVTime?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by DayLite on 2010-08-19
I am new to Ubuntu so please keep your instructions very simple and clear.

I have Hauppauge HVR 950Q installed. It is recognized in Ubuntu10.04 (/dev/video1)

I downloaded TVTime Television Viewer. All the configurations are done in the terminal. I do not understand how to use it, like what the symbols mean or what to write. This is what is on my terminal when I type in tvtime-configure.

```
daylite@daylite-desktop:~$ tvtime-configure
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/daylite/.tvtime/tvtime.xml
usage: tvtime-configure [OPTION]...

  -a, --widescreen           16:9 mode.
  -A, --nowidescreen         4:3 mode.
  -b, --vbidevice=DEVICE     VBI device (defaults to /dev/vbi0).
  -c, --channel=CHANNEL      Tune to the specified channel on startup.
  -d, --device=DEVICE        video4linux device (defaults to /dev/video0).
  -f, --frequencies=NAME     The frequency table to use for the tuner.
                             (defaults to us-cable).

                             Valid values are:
                                 us-cable
                                 us-cable100
                                 us-broadcast
                                 china-broadcast
                                 southafrica
                                 japan-cable
                                 japan-broadcast
                                 europe
                                 australia
                                 australia-optus
                                 newzealand
                                 france
                                 russia
                                 custom (first run tvtime-scanner)

  -F, --configfile=FILE      Additional config file to load settings from.
  -h, --help                 Show this help message.
  -g, --geometry=GEOMETRY    Sets the output window size.
  -i, --input=INPUTNUM       video4linux input number (defaults to 0).
  -I, --inputwidth=SAMPLING  Horizontal resolution of input
                             (defaults to 720 pixels).
  -m, --fullscreen           Start tvtime in fullscreen mode.
  -M, --window               Start tvtime in window mode.
  -n, --norm=NORM            The norm to use for the input.  tvtime supports:
                             NTSC, NTSC-JP, SECAM, PAL, PAL-Nc, PAL-M,
                             PAL-N or PAL-60 (defaults to NTSC).
  -R, --priority=PRI         Sets the process priority to run tvtime at.
  -t, --xmltv=FILE           Read XMLTV listings from the given file.
  -l, --xmltvlanguage=LANG   Use XMLTV data in given language, if available.
  -x, --mixer=DEVICE[:CH]    The mixer device and channel to control.
                             (defaults to /dev/mixer:line)

                             Valid channels are:
                                 vol, bass, treble, synth, pcm, speaker, line,
                                 mic, cd, mix, pcm2, rec, igain, ogain, line1,
                                 line2, line3, dig1, dig2, dig3, phin, phout,
                                 video, radio, monitor
daylite@daylite-desktop:~$ 1

``` 

How do I change the conf.? I have to change the default from video0 to video1

---

### Post by sikander3786 on 2010-08-19
Hi.

Just run *tvtime* and from the program itself (gui) you will be able to change the input as well there are almost all the options present for tweaking. Don't need to manually configure the .conf files.

Is your TV Tuner Card properly detected and the modules loaded?

---

### Post by DayLite on 2010-08-19
> **sikander3786 said:**
> Hi.

Just run *tvtime* and from the program itself (gui) you will be able to change the input as well there are almost all the options present for tweaking. Don't need to manually configure the .conf files.

Is your TV Tuner Card properly detected and the modules loaded?

How do I load the modules? How do I get it to be detected? I tried to run the program and it stays on the screen for a second then disappears. I know to right click on my mouse and it should bring up a menu, but it is gone in a flash. This is what my terminal says.

```
daylite@daylite-desktop:~$ tvtime 
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/daylite/.tvtime/tvtime.xml
videoinput: Cannot open capture device NAME: No such file or directory
Found "USB camera : USB Audio (hw:0,0)"
Segmentation fault
daylite@daylite-desktop:~$ 

```

---

### Post by sikander3786 on 2010-08-20
Check out the link. It might help you.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

---

### Post by DayLite on 2010-08-20
> **sikander3786 said:**
> Check out the link. It might help you.

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

Thank you for posting. It didn't help :confused:

---

### Post by chee on 2010-10-26
I am having the same issues,  I just converted back to Ubuntu (10.10) and everything is working great except my HVR-950Q.   Mythtv seems to see that it is there,  but I can't watch TV,  I thought it was because I didn't know how to set it up properly but I can't get TvTime to work (does the same thing as stated above),  nor Kaffeine,  nor VLC.   It might be something simple but all the posts I have read said that the new distros have the firmware already on them and the thing should work no problem.

I may have to start  a new thread I guess.  I am pretty new but really want to learn this stuff.

---

### Post by chee on 2010-10-26
here is the terminal message I got when I typed tvtime:

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/wes/.tvtime/tvtime.xml
videoinput: Driver refuses to set norm: Invalid argument

    Your capture card driver: au0828 [Hauppauge HVR950Q/au0828 1-7:1.0/1]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Found "HVR-950Q : USB Audio (hw:1,0)"
Segmentation fault

not sure if that gives anyone a clue as to what I need to change,  I thought my drivers were fine as I am running 10.10,  maybe I still need to update the firmware and then the driver?

---

### Post by osc3lot on 2010-11-10
This is how I got mine to work in 10.10. Since the most current firmware and driver is included in the kernel there is no need to update it or do anything to it.  If you have a set-top box through your cable company or satellite company you just need to tell tv time to use the channel the box is outputting on.

for channel 3

tvtime -c 3
or for permanent change sudo tvtime-configure -c 3

for channel 4

tvtime -c 4
or for permanent change sudo tvtime-configure -c 4

However if you have cable that doesn't have a box you probably will have to scan the frequencies to establish a channel list for tvtime to use.  This can be done by utilizing this command.  

tvtime-scanner

I hope this helps.

---

