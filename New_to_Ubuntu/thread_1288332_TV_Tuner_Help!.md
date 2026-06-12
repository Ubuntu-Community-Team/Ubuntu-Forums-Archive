---
title: "TV Tuner Help!"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by iom_cb on 2009-10-11
Hi There!

Ubuntu newbie here! Seriously impressed by it and have replaced Windows completely now.

I'm having problems with my tuner card though ... have googled and tried all sorts!

Here are some details:

chris@chris-desktop:~$ dmesg | grep -i dvb
[   11.859268] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   11.859273] usb 3-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   11.979338] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   12.688037] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   12.688127] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.688461] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   12.799429] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   13.307009] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.307307] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   13.313267] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[ 13.857012] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:04.2/usb3/3-1/input/input6
[   13.859360] dvb-usb: schedule remote query interval to 50 msecs.
[   13.859365] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   13.859627] usbcore: registered new interface driver dvb_usb_dib0700
chris@chris-desktop:~$ 

TVTIME READ:

No such file or directory
Cannot open capture device /dev/video0

Any help will be appreciated!

---

### Post by relay_man on 2009-10-11
This has been covered quite a bit recently.
I just did a search for "tv tuner card" and got quite a bit of 
good info.  Have you searched the forums yet?

---

### Post by iom_cb on 2009-10-11
as i stated in my question; I have spend alot of time searching this.

I have followed all the instructions I can find and it should be working! 

Don't assume that because I'm asking a question I've not looked for the answer!

Any help guys?

---

### Post by sandyd on 2009-10-11
see the last post
[http://ubuntuforums.org/showthread.php?t=1220166](http://ubuntuforums.org/showthread.php?t=1220166)

---

### Post by howefield on 2009-10-11
Looks like the tuner is working and ready to go.

Try a different tv application ? There are several, my preferred option is Kaffeine and works fine with that tuner. At least it does with mine.

---

### Post by laceration on 2009-10-11
TV programs are lacking in linux, to say the least.  I think the paltry replies you got here are indicative of that too. That's why I wrote my own program (see link in my signature).
Go to [http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan) where you can learn how to make a channels.conf file.  There are also some instructions at the OSTV website but they are USA specific. It entails installing a program called dvb-utils and then scanning for channels. Then at the command line test in MPlayer
```
$ mplayer dvb://ABC
```
ABC being the name of a channel in your channels.conf file.

Then, of course, I recommend OSTV!  Check it out.

---

