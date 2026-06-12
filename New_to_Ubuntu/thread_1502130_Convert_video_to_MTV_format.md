---
title: "Convert video to MTV format"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by anewguy on 2010-06-05
I bought a *cheap* MP3/Video player at MicroCenter today - an iVO-Sound m260.  For something so cheap ($15.99 - but it's only 2gig) it actually works quite well.  I was able to convert a music cd (i.e., cda format) to mpeg3 via a Windows program, but am looking for a way to do so in Ubuntu (ffmpeg?).  But the biggest *thing* for me right now is the video - the book says it wants AVI/MTV formatted video.  A video conversion program was included on the device and create a MTV file, but for some reason the player doesn't seem to like "ver 7".  I've tried several AVI formats but they all come up with "unknown format", so I assume I need to stick with MTV.  Is there a GUI'd program in Ubuntu that would do this (okay, I'm getting lazy in my old age, hence the *hope* for a GUI'd program).

Thanks in advance!

Dave ;)

---

### Post by mapes12 on 2010-06-05
I'm not sure if this is what you want but I use WinFF (it's in Synaptic) and DownloadHelper as  a FF add on:- [http://www.downloadhelper.net/](http://www.downloadhelper.net/)

---

### Post by fatality_uk on 2010-06-05
WinFF should do the job. Had to Google MTV file format but hit lucky!
[http://wiki.multimedia.cx/index.php?title=MTV](http://wiki.multimedia.cx/index.php?title=MTV)

---

### Post by TeoBigusGeekus on 2010-06-05
Or mobile media converter...

---

### Post by anewguy on 2010-06-05
I had already installed winff, but MTV is not an option in the output type.  Am I missing some kind of add-on I need to install to get that format?

Thanks

Dave ;)

---

### Post by ron999 on 2010-06-05
Hi
WinFF is a great converter, but it's just a gui for ffmpeg.
If ffmpeg will convert your files to MTV then so will WinFF.

But I don't think that ffmpeg will convert to MTV.
When I test my version of ffmpeg it tells me that it will de-code MTV but no mention of en-code.
This is the command to use:-
```
ffmpeg -formats | grep -i mtv
```

When I run the command it shows 'D' to signify decode.
But there is no 'E' to signify encode.
Try it yourself.
This is my result:-
```
D  MTV             MTV format
```

---

### Post by anewguy on 2010-06-05
> **ron999 said:**
> Hi
WinFF is a great converter, but it's just a gui for ffmpeg.
If ffmpeg will convert your files to MTV then so will WinFF.

But I don't think that ffmpeg will convert to MTV.
When I test my version of ffmpeg it tells me that it will de-code MTV but no mention of en-code.
This is the command to use:-
```
ffmpeg -formats | grep -i mtv
```

When I run the command it shows 'D' to signify decode.
But there is no 'E' to signify encode.
Try it yourself.
This is my result:-
```
D  MTV             MTV format
```

Exactly - I had already installed all the "extras" for ffmpeg before I even installed winff (what can I say - I'm lazy and wanted a GUI ;) ).  I haven't found much luck finding any Linux based program that will do it.  Some Windows programs do, but most of those aren't free, and I'd prefer to keep things in Linux if at all possible.

Thanks

Dave ;)

---

### Post by ron999 on 2010-06-05
By the way, the program to use with Ubuntu for ripping CDs to mp3 or whatever is SoundJuicer. It's probably available in the repository.

---

### Post by anewguy on 2010-06-05
> **ron999 said:**
> By the way, the program to use with Ubuntu for ripping CDs to mp3 or whatever is SoundJuicer. It's probably available in the repository.

Thank you!!  I'm going to install that right away!

Dave ;)

---

### Post by anewguy on 2010-06-06
BTW - still looking for a Linux program to convert AVI to MTV format.  It also needs the basic configurables, such as setting the video aspect.

Thanks
Dave ;)

---

### Post by ron999 on 2010-06-06
Maybe you'll get lucky...:)

But in the meantime you could test the supplied converter program with a PC that has Windows 98 or XP.

If it works OK then consider the nuclear option of installing Windows 98 or a (dodgy) XP in a Virtual Machine in Ubuntu or in a separate partition.

There's also a (remote) chance that your converter program will work in Ubuntu with Wine.

---

### Post by anewguy on 2010-06-06
Yeah, the converter program works in Windows - I had to set the video aspect correctly to get it to work.  I've tried loading into Wine, but tons of missing dll's, and I'm not crazy about manually adding all of them to Wine.  Maybe I'll do that yet.

Would prefer no virtual machine.  I dual-boot now, but would like to get back to a purely-Linux environment (not being a purest, not about the cost, I guess just being weird ;) ).

Thanks

Dave ;)

---

### Post by anewguy on 2010-06-06
I tried reinstalling the app to Wine again, and then used winetricks to download some video codecs.  It takes a *long* time for the application to start, and then it hangs at 4% done.  I ran the program from a terminal so I could copy the output here in case anyone can make any sense out of the messages from wine:

```
dave@dave-desktop:~/.wine/drive_c/MP3 Player/VideoConverter_2.17.00$ ./VideoConvert.exe
Successfully registered DLL qt.ax
Successfully registered DLL qt2.dll
Successfully registered DLL mp4.ax
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:client_side_dib_copy potential optimization: client-side color-index mode DIB copy
Successfully registered DLL C:\MP3 Player\VideoConverter_2.17.00\qt2.dll
Successfully registered DLL quartz.dll
Successfully registered DLL C:\MP3 Player\VideoConverter_2.17.00\mp4.ax
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 96
fixme:quartz:Parser_QueryInterface No interface for {56a868a6-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868a6-0ad4-11ce-b03a-0020af0ba770}!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x178ba8,0x181598): stub
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 96
fixme:quartz:Parser_QueryInterface No interface for {56a868a6-0ad4-11ce-b03a-0020af0ba770}!
fixme:qedit:SampleGrabber_IMemInputPin_GetAllocatorRequirements (0x153ee0)->(0x324e00): semi-stub
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 96
fixme:qedit:SampleGrabber_IMemInputPin_GetAllocatorRequirements (0x153d18)->(0x325288): semi-stub
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AVISplitter_seek Moving position to 0.000 s!
fixme:quartz:AVISplitter_seek Moving position to 0.000 s!
fixme:quartz:MediaControl_StopWhenReady (0x11cb00/0x11cb04)->(): stub !!!
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 96
fixme:quartz:Parser_QueryInterface No interface for {56a868a6-0ad4-11ce-b03a-0020af0ba770}!
fixme:qedit:SampleGrabber_IMemInputPin_GetAllocatorRequirements (0x157e20)->(0x1b4d590): semi-stub
fixme:quartz:AVISplitter_InitializeStreams stream 0: frames found: 0, frames meant to be found: 96
fixme:quartz:Parser_QueryInterface No interface for {56a868a6-0ad4-11ce-b03a-0020af0ba770}!
fixme:qedit:SampleGrabber_IMemInputPin_GetAllocatorRequirements (0x157a50)->(0x1b4da18): semi-stub
Channl:1, BitsPerSample:16, SamplesPerSec:16000, AvgBytesPerSec: 32000
fixme:quartz:MediaSeeking_SetRate (0x1576b8/0x1576c0)->(10.000000): stub !!!
fixme:quartz:AVISplitter_thread_reader Receiving error: 80040209
fixme:quartz:AVISplitter_thread_reader Thread 0 terminated with hr 80040209!
fixme:qedit:SampleGrabber_IPin_EndOfStream : stub
fixme:quartz:FileAsyncReader_WaitForNext Returned: 258 (00000000)
err:quartz:PullPin_Thread_Process Processing error: 8004022e
fixme:quartz:FileAsyncReader_WaitForNext Returned: 258 (00000000)
err:quartz:PullPin_Thread_Process Processing error: 8004022e
Successfully registered DLL C:\MP3 Player\VideoConverter_2.17.00\qt2.dll
Successfully registered DLL quartz.dll
dave@dave-desktop:~/.wine/drive_c/MP3 Player/VideoConverter_2.17.00$ 

```

Thanks

Dave ;)

---

### Post by anewguy on 2010-06-07
I've tried several tools that ffmpeg based and none can convert to mtv format.  I then tried to encode mtv using ffmpeg itself but apparently there is not mtv encoder:

ffmpeg -i PICT0001.AVI -f image2 -vcodec mtv menu


Does anyone know of a native ffpmeg mtv encoder?

Thanks

Dave ;)

---

### Post by anewguy on 2010-06-07
Bump.  I found an older post on the net regarding getting this running in Wine.  I followed those instructions (register qedit.dll, copy qedit.dll to windows/system32, unregister qedit.dll, then register qedit.dll again) and beside just sounding a little weird it also didn't work for me.  There was mention of using direct-x 9, so I loaded that using winetricks.  I had to manually register several ocx and dll files, and a couple just wouldn't register.  Still no go.

So far I've gotten it to say it's converting, get to 4% done, and just hang.

The program is VideoConverter 2.17.

Any help either getting it working in Wine or finding a native Linux app that will convert video to MTV format (used by a bunch of extremely cheap MP3/MP4 players made in China) would be greatly appreciated!


Thanks!
Dave ;)

---

