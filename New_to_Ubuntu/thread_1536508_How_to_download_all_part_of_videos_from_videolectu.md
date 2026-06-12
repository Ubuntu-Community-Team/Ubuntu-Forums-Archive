---
title: "How to download all part of videos from videolectures.net"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by lg_undeadorc on 2010-07-22
i used to download videolectures.net video using get_flash_videos along with flvstreamer
it's syntax is like
 get_flash_videos <url>
the problem is videolectures.net provide only url of the first part of multipart videos.
rest of the part of videolectures url are embedded within java script or something like that
so url for first part will be displayed for all part of videos so only first part could be downloaded.
i search the net and i came to know about unplug plugin of mozilla
through it i can get the url but it's based on mms://... protocol
i again searched the net and i came to know about mimms
using mimms for downloading from videolectures.net don't helped me
how can i download rest of the part of videos beside first from videolectures.net

---

### Post by aeiah on 2010-07-22
do you ever see the urls for the proceeding parts? are they predictable urls?

---

### Post by lg_undeadorc on 2010-07-22
> **aeiah said:**
> do you ever see the urls for the proceeding parts? are they predictable urls?
I dont think so. 
for example
the url [http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2/](http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2/)
got 4 videoparts
and i tried 
[http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2_02](http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2_02)
[http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?video=02](http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?video=02)
[http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?video=2](http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?video=2)
[http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?part=02](http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?part=02)
[http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?part=2](http://videolectures.net/mlss2010_scholkopf_lawrence_mlfcs2?part=2)
but none of them worked to access 2nd part video.
I can't predict more than this,if you could please help me

---

### Post by ron999 on 2010-07-23
Hi
I can download those lectures (all the parts) on a Windows computer using a program called **Stream Transport**.

With Linux, some people use **Wireshark** to 'sniff' packets that can then be downloaded with **rtmpdump**.
I don't know how to do this though. :redface:
Maybe others can explain.

---

### Post by lg_undeadorc on 2010-07-23
> **ron999 said:**
> Hi
I can download those lectures (all the parts) on a Windows computer using a program called **Stream Transport**.

With Linux, some people use **Wireshark** to 'sniff' packets that can then be downloaded with **rtmpdump**.
I don't know how to do this though. :redface:
Maybe others can explain.

I tried to use rtmpdump but following error occured:
In the following url
[http://stream-recorder.com/forum/rtm...x-t3838p3.html]("http://stream-recorder.com/forum/rtmpdump-freeware-rtmp-stream-downloader-macos-x-t3838p3.html")

I got 4 step procedure to install rtmpdump on ubuntu
**1)First of all install the tools needed for accessing the code and  compilation**.
code:sudo apt-get install build-essential gcc make subversion  libssl0.9.8 libssl-dev libssl0.9.8

**2)Now check out the latest code from the Subversion repository:**
code:svn co svn://svn.mplayerhq.hu/rtmpdump rtmpdump
**3)cd rtmpdump**
**4)make linux**

The steps 1-3 went well
but when moving to step 4
*the following error occured*
**make: *** No rule to make target `linux'.  Stop.**

Beside this url , i also looked at other and none of them helped me
How could i compile rtmpdump on ubuntu 10.4 and use it to download  videos from videolectures.net

---

### Post by ron999 on 2010-07-23
Hi
I think that step 4 should be:-
```
make SYS=posix
```

These were the 5 steps that I used:-
1) I downloaded source tarball **rtmpdump-2.3.tgz** from here:-[http://rtmpdump.mplayerhq.hu/]("http://rtmpdump.mplayerhq.hu/")
2) Then I extracted it.
3) Then I changed directory:-  **cd /home/ron/Downloads/rtmpdump-2.3**
4) Then used:-  **make SYS=posix**
5) Then used:-  **sudo make install**

---

### Post by ron999 on 2010-07-23
OK
I followed some of the 'how-to' in post #27 here:- [http://stream-recorder.com/forum/showpost.php?p=14540&postcount=27]("http://stream-recorder.com/forum/showpost.php?p=14540&postcount=27")

So the command to download part 2 of your lecture is:-

```
rtmpdump -r rtmp://oxy.videolectures.net/video/ -y 2010/pascal2/mlss2010_sardinia/scholkopf_lawrence_mlfcs2/mlss2010_scholkopf_lawrence_mlfcs2_01 -a video -s http://media.videolectures.net/jw-player/player.swf -w e2436d6201f4265a0a0ad974165a3b26a6f302ba8e7cfebd6dfad2cac28105e1 -x 50038 -o part2.flv
```

Phew!=D>

Maybe it gets easier after a while.:rolleyes:
I'll let you calculate the commands for the other parts yourself. I don't want to spoil your fun. :biggrin:

> ron@ubuntu:~$ rtmpdump -r rtmp://oxy.videolectures.net/video/ -y 2010/pascal2/mlss2010_sardinia/scholkopf_lawrence_mlfcs2/mlss2010_scholkopf_lawrence_mlfcs2_01 -a video -s [http://media.videolectures.net/jw-player/player.swf](http://media.videolectures.net/jw-player/player.swf) -w e2436d6201f4265a0a0ad974165a3b26a6f302ba8e7cfebd6dfad2cac28105e1 -x 50038 -o part2.flv
RTMPDump v2.3
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
INFO:   duration              3725.60
INFO:   width                 352.00
INFO:   height                257.00
INFO:   videodatarate         400.00
INFO:   framerate             25.00
INFO:   videocodecid          4.00
INFO:   audiodatarate         128.00
INFO:   audiodelay            0.03
INFO:   audiocodecid          2.00
INFO:   canSeekToEnd          TRUE
279294.347 kB / 3725.61 sec (100.0%)
Download complete


---

### Post by lg_undeadorc on 2010-07-23
> **ron999 said:**
> OK
I followed some of the 'how-to' in post #27 here:- [http://stream-recorder.com/forum/showpost.php?p=14540&postcount=27](http://stream-recorder.com/forum/showpost.php?p=14540&postcount=27)

So the command to download part 2 of your lecture is:-

```
rtmpdump -r rtmp://oxy.videolectures.net/video/ -y 2010/pascal2/mlss2010_sardinia/scholkopf_lawrence_mlfcs2/mlss2010_scholkopf_lawrence_mlfcs2_01 -a video -s http://media.videolectures.net/jw-player/player.swf -w e2436d6201f4265a0a0ad974165a3b26a6f302ba8e7cfebd6dfad2cac28105e1 -x 50038 -o part2.flv
```Phew!=D>

Maybe it gets easier after a while.:rolleyes:
I'll let you calculate the commands for the other parts yourself. I don't want to spoil your fun. :biggrin:

It's working now. Thnks a lot but can't we stop download at middle and resume it later from same position.

---

### Post by elexhobby on 2011-12-09
lg_undeadorc or ron999,

Could you please explain how did you determine the various parameters e.g. ```
2010/pascal2/mlss2010_sardinia/scholkopf_lawrence_mlfcs2/mlss2010_scholkopf_lawrence_mlfcs2_01
``` that go into the rtmpdump command, from the source code?

I wish to download all parts from [http://videolectures.net/mlss05au_roweis_pgm/](http://videolectures.net/mlss05au_roweis_pgm/)
but am unable to do so.

Thanks in advance.

---

### Post by ron999 on 2011-12-09
> **elexhobby said:**
> ... or ron999,

Could you please explain how did you determine the various parameters... 

Hi
The method shown in post #7 above is flaky.:(


This is a more rugged procedure to obtain RTMPDump parameters :-

**1**
Start the server with this command:-
```
sudo iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT && rtmpsrv
```

**2**
See the message in console:-
[SIZE="3"]**Streaming on rtmp://0.0.0.0:1935**[/SIZE]

**3**
Refresh the page and play the video, now wait till the RTMPDump command appears in console.

**4**
Interrupt the server:- [SIZE="3"]**Ctrl-c**[/SIZE]

**5**
Stop the server with this command:-
```
sudo iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
```

**6**
Copy and paste the RTMPDump command to download the video.
:D

---

### Post by elexhobby on 2011-12-09
That's mind-blowingly simple! Thanks a ton!

---

### Post by elexhobby on 2011-12-10
There was an error in the download and I received the following error:

```

Caught signal: 13, cleaning up, just a second...
ERROR: WriteN, RTMP send error 32 (42 bytes)
ERROR: RTMP_ReadPacket, failed to read RTMP packet body. len: 66506
60139.752 kB / 759.85 sec (15.1%)
Download may be incomplete (downloaded about 15.10%), try resuming

```

The download started from scratch when I entered the same command again. Is there a way to resume download?

Edit: I tried using the --resume option, but got the following error:
```
WARNING: Stream does not start with requested frame, ignoring data...
```
The command I had issued is as follows:
```

rtmpdump --resume -r "rtmp://oxy.videolectures.net/video" -a "video" -f "LNX 10,3,183,10" -W "http://staticcdn.viidea.com/player/lib/flowplayer.unlimited-3.2.7.swf" -p "http://videolectures.net/mlss2011_vandenberghe_convex/" -y "flv:v002/98/tcdxuthy3kmoj3raohpplpll65zoowy7" -o tcdxuthy3kmoj3raohpplpll65zoowy7.flv

```

---

