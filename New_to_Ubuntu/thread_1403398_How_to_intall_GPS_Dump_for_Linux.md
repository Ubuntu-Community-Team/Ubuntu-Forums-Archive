---
title: "How to intall GPS Dump for Linux?"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Bryan55 on 2010-02-10
Hi.

I'm very new to Ubuntu and have always install via the Softwear Centre, Sinaptec Package Manager or Wine but the program I need is not available via those systems.

It's call "GPS Dump" and can be downloaded from here.
[http://www.multinett.no/~stein.sorensen/]("http://www.multinett.no/%7Estein.sorensen/")
It's use to prepare tack-logs to be uploaded to the "UK XC paragliding League" and no other program will be accepted.

Any help would be much appreciated.
Bryan.

---

### Post by NCLI on 2010-02-10
It looks like you should just right-click the file, go to permissions, and make sure the file is set as executable. Then just double-click it and choose to have it run in a terminal.

---

### Post by patchwork on 2010-02-10
Looks like it's a binary file, compiled on 32bit Ubuntu.  If you trust the source, download the program, and then make the file executable and run the file by typing this

```
cd Downloads    ## or path to where you downloaded the file
sudo chmod +x <filename>           ##   makes file executable
./<filename>                ##  runs file 
```

Drat, beat to the punch again

---

### Post by Bryan55 on 2010-02-11
Thanks for your help. 

Patchwork I did need those command lines.

Below is what I got. I presume that I would then need to compile a command from this list.
However I can see that my GPS instrument (Top-Navigator 9600 bauds) is not supported

> bryan@Bydand:~$ cd Downloads
bryan@Bydand:~/Downloads$ sudo chmod +x gpsdump.0.07
[sudo] password for bryan: 
bryan@Bydand:~/Downloads$ ./gpsdump.0.07

GpsDumpLinux 0.07 commands:

-h   Display this text

-gc  GPS = Brauniger/Flytec family (e.g. Compeo, Competino, 5030..)
-gg  GPS = Garmin (most models)
-gm  GPS = MLR and Digifly Leonardo
-gx  GPS = XCTrainer (MXP2004 protocol at 57600 bauds)

-c"N"   Serial port N. Translates into /dev/ttyS"N"
-cu"N"  USB-to-serial port N. Translates into /dev/ttyUSB"N"

-l"File"  Download a track and save it in a file. Extensions .kml and .igc
          are supported. If the extension is not recognized, both file types
          are generated. For the Brauniger/Flytec models the raw IGC data
          from the GPS is saved. If no name is given gpsdump will make one
          from the time stamp of the first position.

-w"File"  Download waypoints and save them in a file. Extensions .gpx, .wpt
          (Ozi format) and .kml are supported. If the extension is not recognized
          all file types are generated. If no name is given gpsdump will make one
          from the current time. Supported GPS: Garmin and Brauniger/Flytec.

-r"File"  Read waypoints from a file and upload them to the GPS. Supported file
          formats: Ozi and GpsDump/$FormatGEO.

--gap "Time"  Set gap (in integer minutes) between consecutive track points for
              detecting multiple tracks. If set to zero a single track is assumed.
              If not set, a single track is assumed, unless divided by the GPS (e.g. Garmin).
              A list is printed for the user to select from (comma separated input).

-x"File" Convert .igc to .kml

--noana  Skip speed analysis.Looks like I will have to go back to plan A 
See here
_[http://www.paraglidingforum.com/viewtopic.php?t=29888](http://www.paraglidingforum.com/viewtopic.php?t=29888)_

Bryan

---

### Post by patchwork on 2010-02-11
OK, well you shouldn't have to compile anything further....the program is installed.

From the link you posted, the version you have is a command-line only program that requires arguments (the options listed in you output).  If you're not comfortable with this, try to locate the 1.01 version also mentioned in the link you posted.   That version is supposedly gui supported, which gives some people a good warm and fuzzy feeling.  

I have never worked with GPSDump or anything similar (or even a GPS!), so I really don't understand the arguments listed in your output beyond recognizing the names of various manufacturers.

---

### Post by Bryan55 on 2010-02-11
The GPS dump 0,07 that you helped me to install is not going to be of any use to me as it does not list my GPS (Top-Nav) it only works with
> -gc  GPS = Brauniger/Flytec family (e.g. Compeo, Competino, 5030..)
-gg  GPS = Garmin (most models)
-gm  GPS = MLR and Digifly Leonardo
-gx  GPS = XCTrainer (MXP2004 protocol at 57600 bauds)
So please how do I uninstall it? Thanks again for the help.

I've even tried the Windoze version in wine but it can not connect with Com-port 1 (I included...ln -s /dev/ttyS0 .wine/dosdevices/com1)

The v1.0.1 did give me a warm fuzzy feeling but it was short lived as it did not record anything from my GPS. Though it does show signs that it knows my Top-Nav is there as it does not "Timeout" until it stops transmitting however this only happens when I have Cutecom running at the same time. Strangely Cutecom only shows data flowing when I don't get v1.0.1 to connect.

Bryan

---

### Post by patchwork on 2010-02-11
Since it is a stand-alone binary file (no other programs or libraries were installed), removing the program is as easy as deleting the binary.

For instance, if the program is in your Downloads folder still, 

cd  Downloads 
rm <program_name>

I'm sorry you couldn't get it working with your GPS (and that I don't have the knowledge to help you get it working).

---

### Post by platypuss72 on 2011-07-03
please please can anyone enlighten me ...

i have been trying to get gpsdump working on my eeepc ... 

but i have not got it working in any way usable ... 

i have it installed on main pc ubuntu 10.10 , working in wine with gpsdump 4.5 ish with a serial port .. the command version 0.7 works with my serial port - usb converter

BUT now i want it on eeepc to travel and am using just usb to garmin 76sc, also have brauniger iq basic that does not see at all .. 

i have tried the symlink as per other posts to wine but still nothing is picked up in wine on com port .. 
 
i am a newbie  to linux so not understanding the command line to well , but thought even if i can use the linux version i can make backups while away. so is there a simple guide to using this version ?? as i am confused as got it working once and now type the same thing on different computer does not find gps ?? 

ken@ken-eeepc:~/gpsdump$ ./gpsdump -cu0 -gg 
No GPS command found

i have installed gipsy on firefox .. that works with garmin on port /dev/ttyUSB0 , but not with my iq basic (does not see it)

---

