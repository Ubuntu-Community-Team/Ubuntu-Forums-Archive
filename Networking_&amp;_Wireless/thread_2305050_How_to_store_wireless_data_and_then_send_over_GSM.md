---
title: "How to store wireless data and then send over GSM?"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by mindeee on 2015-12-02
I have two buildings within 100 meters. I called them and building A building B. Between buildings A and B is two audio channels and one data channel. In building B I need laptop/PC  with relevant software to store this data and forward on GSM  when it needed. What kind of software I need for laptop/PC and How can I forward stored data over GSM?

---

### Post by tgalati4 on 2015-12-02
Welcome to the forums.  What is the Use Case?  Perhaps draw a diagram to show the network topology.  Are you trying to get data from B to A?  Describe the audio channel,  Is it a 75 Ohm cable?  Is it a digital mp3 stream on a Cat6 cable?  Describe the digital channel.  Is it a single Cat6 cable between buildings?

For store-and-forward, you could set up a GSM cellphone with a USB (or bluetooth) connection on one computer and then use modem commands to dial the number and transmit the data.  There are a lot of ham radio programs that perform this type of function.

---

### Post by mindeee on 2015-12-02
My question is. What software must be in PC1 to store all data received from building 1 and how to reach this data remotely from PC2. Or how to send data from PC1 to PC2. [IMG]http://i1228.photobucket.com/albums/ee457/mingas1/1000%20hallmark/3g%204g.jpg[/IMG]

---

### Post by tgalati4 on 2015-12-02
Perhaps treat the data as a fax and use faxing tools:

> tgalati4@Mint17 ~ $ apt-cache search mgetty
iaxmodem - software modem with IAX2 connectivity
mgetty - Smart Modem getty replacement
mgetty-docs - Documentation Package for mgetty
mgetty-fax - Faxing tools for mgetty
mgetty-pvftools - Programs for listening and manipulating pvf and rmd files
mgetty-viewfax - Program for displaying Group-3 Fax files under X
mgetty-voice - Voicemail handler for mgetty
mingetty - Console-only getty


What format is the data that is captured in PC1?  Is it a simple text file?  Is it a PDF file?

For the GSM connection, you would probably use a USB-to-GSM [dongle]("http://www.store4g.com/huawei-e398/") and then follow commands similar to this thread:

[http://ubuntuforums.org/showthread.php?t=1466490&highlight=GSM%2C+modem%2C+transmit](http://ubuntuforums.org/showthread.php?t=1466490&highlight=GSM%2C+modem%2C+transmit)

Set up a VPS (virtual, private server) in the cloud to accept the data.  Use PC1 to push the data into the VPS, then use PC2 to read the data.  The data could be stored as files and use a web interface to add data and retrieve data.  Here are some tools to explore:  [https://blog.profitbricks.com/top-49-tools-internet-of-things/](https://blog.profitbricks.com/top-49-tools-internet-of-things/)

This is a complicated problem, and will, perhaps require a complicated solution.  Break it down to the simplest elements and then work on each element.

Ultimately, you want to get data from Building 1 to PC2.

---

### Post by mindeee on 2015-12-03
Hi data on PC1 is in S/PDIF format. I have to record and store this data on PC1 somehow and and when if required I need to reach this stored records from PC2 or PCx from any remotely location. This type of challenge is first for me, so It would be good for me something not too complicated. 
I need data from building 1 but I can't skip building 2 because all system between building 1 and building 2 installed and can't be be changed. So now building 1 I can reach only through building 2.
Thanks

---

### Post by tgalati4 on 2015-12-03
So let's focus on the first step first, recording [S/PIDF]("http://https://en.wikipedia.org/wiki/S/PDIF") data.  First of all, S/PDIF is simply an optical or RF transmission of a digital audio stream--2-channel pulse code modulation (PCM) in this case.  So to record a PCM audio, install *sox* and use the *rec* command.

```
sudo apt-get install sox
man rec
man soxformat
```

You need to write a script to check for data on the PCM device (perhaps /dev/snd/pcmC0D0c).  You need a way to check when new data is written to this device.  You may run into a 2GB file limitation, as others have discovered.  There are several devices, your system may be different:

> tgalati4@Mint17 /dev/snd $ ls -la
total 0
drwxr-xr-x   3 root root      220 Nov 22 13:59 .
drwxr-xr-x  16 root root     4180 Dec  1 15:42 ..
drwxr-xr-x   2 root root       60 Nov 22 13:59 by-path
crw-rw----+  1 root audio 116,  7 Nov 22 13:59 controlC0
crw-rw----+  1 root audio 116,  6 Nov 22 13:59 hwC0D0
crw-rw----+  1 root audio 116,  5 Nov 22 13:59 hwC0D1
**crw-rw----+  1 root audio 116,  4 Nov 22 13:59 pcmC0D0c**
crw-rw----+  1 root audio 116,  3 Dec  2 08:51 pcmC0D0p
crw-rw----+  1 root audio 116,  2 Nov 22 13:59 pcmC0D2c
crw-rw----+  1 root audio 116,  1 Nov 22 13:59 seq
crw-rw----+  1 root audio 116, 33 Nov 22 13:59 timer

Some reading:  [http://ubuntuforums.org/showthread.php?t=2141741&highlight=sox+record+PCM+file](http://ubuntuforums.org/showthread.php?t=2141741&highlight=sox+record+PCM+file)

[http://ubuntuforums.org/showthread.php?t=1626666&highlight=sox+record+PCM+file](http://ubuntuforums.org/showthread.php?t=1626666&highlight=sox+record+PCM+file)

You want to search these forums for how to record a live audio stream--since that is what you are doing.  There are lots of ways to do it.  But you must get that part working reliably before you can consider how you are going to "store-and-forward" the data through your GSM modems.

---

