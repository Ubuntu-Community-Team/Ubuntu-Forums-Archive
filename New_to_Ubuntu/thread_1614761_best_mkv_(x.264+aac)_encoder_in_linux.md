---
title: "best mkv (x.264+aac) encoder in linux"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-11-06
):PHey, I was wondering what's the best x.264 encoder in linux. Actually I'd love to get a video encoder which supports mkv container, converts audio to aac(with sbr and ps ofcourse8)!), and gives MOST options to encode in x264. In short, an application which gives BEST quality+compression at smallest size.

In windows, staxrip is one such good encoder. In linux, what can compete with staxrip?:guitar:

---

### Post by dhiman33 on 2010-11-06
:PAlso I'd be happy if u tell me the best x.264 video encoder software, and the best aac encoder software(sbr+ps).Then I'd join them using some mkvmuxer! pls name one. Also I'd need a tool to extract vid stream and aud stream from ANY movie. What good tools are there?(virtualdubmod?)

---

### Post by P4man on 2010-11-06
handbrake is nice and easy to use, but Im not sure if it works properly with 10.10 yet. The "best" and most powerful would be ffmpeg (on which most other encoders and decoders are based). Its a command line app though, not very intuitive to use but all the power you could ever want and it might be worth learning if you are serious about encoding.

---

### Post by FakeOutdoorsman on 2010-11-06
> **dhiman33 said:**
> ):PHey, I was wondering what's the best x.264 encoder in linux. Actually I'd love to get a video encoder which supports mkv container, converts audio to aac(with sbr and ps ofcourse8)!), and gives MOST options to encode in x264. In short, an application which gives BEST quality+compression at smallest size.

In windows, staxrip is one such good encoder. In linux, what can compete with staxrip?:guitar:

x264 is an encoder than can produce H.264 video (a video format).  x264 will give you the best results if you want H.264 video.  You can use x264 directly or via FFmpeg (or other tools like Hanbrake).  FFmpeg will probably do what you want, but first you need to enable some encoders:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg[/url]

Now you can use FFmpeg to encode to H.264 video and AAC audio:
```
ffmpeg -i input.foo -vcodec libx264 -vpre medium -crf 22 -acodec libfaac -aq 100 -map_meta_data 0:0 -threads 0 output.mkv
``` 

See the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more info and examples. If you don't like command-line then try Handbrake.

> **dhiman33 said:**
> Also I'd need a tool to extract vid stream and aud stream from ANY movie. What good tools are there?(virtualdubmod?)

FFmpeg can also extract audio and video.  Audio example - I know input.mkv has MP3 audio, so I will copy the audio to a MP3 container:
```
ffmpeg -i input.mkv -acodec copy output.mp3
```
Video example - I know input.mkv has H.264 video:
```
ffmpeg -i input.mkv -vcodec copy -an output.mkv
```
What if you want to skip the first 12 seconds of the input and make the final video 1 minute and 20 seconds long?  This next example can do this:
```
ffmpeg -ss 12 -i input.mkv -t 00:01:20.00 -vcodec copy -an output.mkv
```
Notice in these examples that the video or audio tracks are being copied, so there is no re-encoding and no quality loss.

---

### Post by dhiman33 on 2010-11-07
:)Excellent response,fakeoutdoorsman! But does ffmpeg convert to aac with sbr+ps(in other words high efficiency v2 acc):-\"? And can u give some gui frontend to ffmpeg? What is winff? Does it provide all options as in ffmpeg command line?

Also, can someone name an audio convertor which converts anything to aac with sbr+ps?(In case ffmpeg can't do that)

---

### Post by MrWES on 2010-11-07
Just a thought here. Why do you want to transcode the video portion of the mkv file? Since most are already in h.264 anyhow.

Read post #4 of this thread:
[http://ubuntuforums.org/showthread.php?p=9370090#post9370090]("http://ubuntuforums.org/showthread.php?p=9370090#post9370090")

---

### Post by andrew.46 on 2010-11-07
Hi dhiman,

> **dhiman33 said:**
>  But does ffmpeg convert to aac with sbr+ps(in other words high efficiency v2 acc):-\"? 

In FakeOutDoorsman's examples aac encoding uses libfaac and this does not support HE-AAC v2. However NeroAacEnc will use spectral band replication and parametric stereo:

```

Advanced features / troubleshooting:
-lc           : Forces use of LC AAC profile (HE features disabled).
-he           : Forces use of HE AAC profile (HEv2 features disabled).
-hev2         : Forces use of HEv2 AAC profile
                Note that the above switches (-lc, -he, -hev2) should not be
                used; optimal AAC profile is automatically determined from
                quality/bitrate settings when no override is specified.

```

There is no gui available for NeroAacEnc as far as I am aware and IMHO for FFmpeg a period of time learning the commandline is time well spent.

Andrew

---

### Post by stmiller on 2010-11-07
Yeah faac is limited to 160kbps max. The software was never written to do any higher.

So any projects that use faac (ffmpeg, handbrake, etc) have this "limitation".

Nero is the best AAC encoder on the planet - as often discussed on hydrogenaudio. :P

---

### Post by JohnAStebbins on 2010-11-07
> **stmiller said:**
> Yeah faac is limited to 160kbps max. The software was never written to do any higher.

So any projects that use faac (ffmpeg, handbrake, etc) have this "limitation".

Nero is the best AAC encoder on the planet - as often discussed on hydrogenaudio. :P

Not quite true.  HandBrake has patched faac to allow up to 320kbps for stereo and up to 768kbps for 6 channel aac.  But you are correct about Nero ;)

---

### Post by dhiman33 on 2010-11-08
:shock:Oh no, neroaacenc can only convert from wav files! So I've to convert a file to wav and then to aac using this. Is their any simpler way like decoding an mp3 to wav and then wav to acc++ in one go?(Still messy as there's no gui.)

Handbrake has no stable release for meerkat. Forget abt it now.[-(

What about winff? Is it a good gui for ffmpeg? Can it do do everythng that ffmpeg can?

Also there is a convert option in vlc player. Is it better than ffmpeg?

And does ffmpeg uses the original(and best!) x.264 from videolan?Or it's some other version?

---

### Post by dhiman33 on 2010-11-08
OMG when I'm going to install ffmpeg extra 52 from medibuntu it says i've to remove something for it!(libavcodec & libavutil). When I try to remove libavutil it says I've to remove loads of things! What to do?

---

### Post by JohnAStebbins on 2010-11-08
> Handbrake has no stable release for meerkat. Forget abt it now.
The last 'stable' release is nearly a year old.  The nightly builds are far more stable now, especially considering that we are gearing up for the next 'stable' release and are doing nothing but bug fixes.

But if you insist on only using 'stable' releases, it'll be out soonish. Just so we are clear though, HandBrake's stable releases are more for the sanity of the developers than for the convenience of the users.  With everyone using the same release, it's much easier to field issues that come up on the forums.  Usually, within a couple weeks of a release we have fixed all the issues that the unwashed masses finds for us and again, the nightly build becomes better than the release. Fixes are not backported into the release.

---

### Post by anjilslaire on 2010-11-08
Agree with Stebbins. I' using the nightly build repo & it's great. Thanks, btw

---

### Post by FakeOutdoorsman on 2010-11-08
> **dhiman33 said:**
> :shock:Oh no, neroaacenc can only convert from wav files! So I've to convert a file to wav and then to aac using this. Is their any simpler way like decoding an mp3 to wav and then wav to acc++ in one go?(Still messy as there's no gui.)
If you want to use the non open-source neroAacEnc you do not need to convert to wav and then to aac.  You can use FFmpeg to decode most formats, and then pipe it to neroAacEnc for encoding. Example:
```
ffmpeg -i input.foo -f wav - | neroAacEnc -ignorelength -if - -of output.mp4
```

> **dhiman33 said:**
> What about winff? Is it a good gui for ffmpeg? Can it do do everythng that ffmpeg can?
WinFF is limited by it's presets, and last time I looked at WinFF the presets were incompatible with newer versions of FFmpeg, such as one that you would compile yourself.  if you want to use WinFF, then you should probably use FFmpeg from the repository although I can't guarantee everything will work.  You can make your own presets though.

> **dhiman33 said:**
> And does ffmpeg uses the original(and best!) x.264 from videolan?Or it's some other version?
There is only one x264.  If you absolutely wanted the "best" x264, then you would compile the latest because it is actively developed and updated often.

---

### Post by andrew.46 on 2010-11-09
Hi John,

> **JohnAStebbins said:**
> Not quite true.  HandBrake has patched faac to allow up to 320kbps for stereo and up to 768kbps for 6 channel aac.  But you are correct about Nero ;)

I found [discussion]("http://forum.handbrake.fr/viewtopic.php?f=4&t=15902") concerning this patch, could you give a link to the final accepted version in svn? I am keen to patch my own copy :).

Thanks,

Andrew
[B]
Edit:[/B] Looks like [this is it]("http://trac.handbrake.fr/export/3222/trunk/contrib/faac/A00-bitrates.patch")...

---

### Post by dhiman33 on 2010-11-09
Help!:cry: I've downloaded neroaacaacenc,neroaacdec,neroaactag for linux and can't use them! Pls tell me the way tthe way to use these![-o<[-o<

And pls tell more abt that piping fakeoutdoorsman. Pls explain how that command works. What is piping,btw? Can u give some link that explains how piping works from ffmpeg to neroaacenc?

---

### Post by varun100 on 2010-11-09
in the input.mkv i  have got a file name which is seperated by space..
and its in the partitioned drive whose name also contains a space.

basically how to apply cd command when a directory has a name containing space in it.
i would be very grateful if u would let me know this thing..

---

### Post by dhiman33 on 2010-11-09
Also, someone pls tell ALL the settings of libx264(like psycho-trellis,subpixel motion est. etc.etc....). Pls tell ALL of them.

OMG, I don't know varun's answr.Someone else will know,though.

Ok,I've finally found the way to run neroaacenc; I had to allow it to run it as executable and in the terminal I had to type ./neroaacenc instead of just neroaacenc. Now I want to know more about that piping or whatever u say.

---

### Post by andrew.46 on 2010-11-09
Hi dhiman,

> **dhiman33 said:**
> Ok,I've finally found the way to run neroaacenc; I had to allow it to run it as executable and in the terminal I had to type ./neroaacenc instead of just neroaacenc. 

Perhaps an easier way is to copy the file to /usr/local/bin and make it executable as follows:

```

sudo cp neroAacEnc /usr/local/bin
sudo chmod +x /usr/local/bin/neroAacEnc

```

With this done you can simply type *neroAacEnc* into a terminal and the program will be called.

Andrew

---

### Post by P4man on 2010-11-09
> **dhiman33 said:**
>  Now I want to know more about that piping or whatever u say.

Plenty to read on that with a little bit of googling. Will come in handy more often than you think: [http://www.dsj.net/compedge/shellbasics1.html](http://www.dsj.net/compedge/shellbasics1.html)

---

### Post by FakeOutdoorsman on 2010-11-09
> **varun100 said:**
> ...how to apply cd command when a directory has a name containing space in it...
There are several ways to do this:
```
cd 'directory with spaces/file with spaces.mkv'
cd "directory with spaces/file with spaces.mkv"
cd directory\ with\ spaces/file\ with\ spaces.mkv
```
I usually use the third example because I often use the tab key to complete the file names for me.

> **dhiman33 said:**
> Also, someone pls tell ALL the settings of libx264(like psycho-trellis,subpixel motion est. etc.etc....). Pls tell ALL of them.
Run the command *x264 --fullhelp* for a complete help page listing all of the options.  It is recommended that you simply use the presets as described in the encoding guide I linked to earlier. They will give you excellent results.

---

### Post by JohnAStebbins on 2010-11-09
> **andrew.46 said:**
> Hi John,



I found [discussion]("http://forum.handbrake.fr/viewtopic.php?f=4&t=15902") concerning this patch, could you give a link to the final accepted version in svn? I am keen to patch my own copy :).

Thanks,

Andrew
[B]
Edit:[/B] Looks like [this is it]("http://trac.handbrake.fr/export/3222/trunk/contrib/faac/A00-bitrates.patch")...
Yes, that's it.

---

### Post by dhiman33 on 2010-11-10
:confused:Running the command x264 --fullhelp says that x264 is not installed and i've to install it. But I've already installed libx264! Why I have to once again install x264!:evil: **What's the difference between this two**?I'm totally confused!!](*,)

And also, I know how to use libx264 in ffmpeg(-vcodec libx264). :-sBut how to use this x264 in ffmpeg?

---

### Post by P4man on 2010-11-10
a lib like libx264 is a library. A bit like a DLL in windows, it is used by other programs, you dont invoke it directly from a commandline. x264 is an application that you can use from a CLI. 

I dont really know why youd want to  use x264 in ffmpeg (which uses libx264 normally) but I guess its  possible through piping. Ill let the experts explain the how and why.

---

### Post by dhiman33 on 2010-11-10
:shock:Wait a minute; does it mean I didn't need to install ffmpeg to encode in x264?!! I mean I can just use neroaacenc to create hev2(supercompressed! at 32kbps!) aac/m4a sound track, and x264 to convert a video stream to x264 format?

Though I think ffmpeg is needed to extract video,audio and sub track from movies. Can u people tell me a gui program which can be used to extract streams from mkv files(I use it often:biggrin:) and also to add/remove streams to a mkv file?

---

### Post by andrew.46 on 2010-11-11
Hi dhiman,

> **dhiman33 said:**
> :shock:Wait a minute; does it mean I didn't need to install ffmpeg to encode in x264?!!

You may find that x264 itself can be limited as to its input format, depends on how your copy has been configured. This can be seen as follows:

```

andrew@skamandros~$ **[COLOR="Red"]x264 --help[/COLOR]**
x264 core:107 r55 f9f0035
Syntax: x264 [options] -o outfile infile
[B][COLOR="Red"]
Infile can be raw (in which case resolution is required),
  or YUV4MPEG (*.y4m),
  or Avisynth if compiled with support (no).
  or libav* formats if compiled with lavf support (yes) or ffms support (no).[/COLOR][/B]
Outfile type is selected by filename:
 .264 -> Raw bytestream
 .mkv -> Matroska
 .flv -> Flash Video
 .mp4 -> MP4 if compiled with GPAC support (yes)
Output bit depth: 8 (configured at compile time)

Options:
[...]

```

Here is an example of x264 using its lavf support for a simple encode:

```

andrew@skamandros~/samples$  [B][COLOR="Red"]x264 --crf 24 -o test.mp4 guardians.mov 
lavf [info]: 848x358p 0:1 @ 2397/100 fps (vfr)[/COLOR][/B]
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
x264 [info]: profile High, level 3.0
x264 [info]: frame I:72    Avg QP:20.44  size: 12700                           
x264 [info]: frame P:1697  Avg QP:24.59  size:  5974
x264 [info]: frame B:1580  Avg QP:27.08  size:  1288
x264 [info]: consecutive B-frames: 28.3% 18.3% 11.4% 42.0%
x264 [info]: mb I  I16..4: 33.0% 44.7% 22.3%
x264 [info]: mb P  I16..4: 14.2% 16.6%  3.0%  P16..4: 36.0%  9.7%  4.2%  0.0%  0.0%    skip:16.3%
x264 [info]: mb B  I16..4:  0.5%  0.6%  0.2%  B16..8: 29.4%  2.4%  0.6%  direct: 1.6%  skip:64.7%  L0:37.5% L1:55.8% BI: 6.6%
x264 [info]: 8x8 transform intra:48.5% inter:69.2%
x264 [info]: coded y,uvDC,uvAC intra: 35.6% 52.4% 10.2% inter: 13.3% 19.4% 1.1%
x264 [info]: i16 v,h,dc,p: 33% 27% 13% 27%
x264 [info]: i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 17% 21% 30%  5%  6%  5%  7%  4%  6%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 19% 21%  6%  8%  6%  8%  5%  5%
x264 [info]: i8c dc,h,v,p: 54% 24% 16%  6%
x264 [info]: Weighted P-Frames: Y:19.9%
x264 [info]: ref P L0: 66.6% 14.5% 14.3%  4.3%  0.4%
x264 [info]: ref B L0: 93.3%  5.9%  0.8%
x264 [info]: ref B L1: 97.1%  2.9%
x264 [info]: kb/s:749.59

encoded 3349 frames, 14.48 fps, 749.63 kb/s

```

Mind you, you can only output to mp4 if your copy has been compiled against gpac. So a few little 'gotchas' in there :).

> Can u people tell me a gui program which can be used to extract streams from mkv files(I use it often:biggrin:) and also to add/remove streams to a mkv file?

Best program for this purpose is mkvmerge gui, I attach a screenshot of this fine program running. Not sure what version is available in the Ubuntu repository but it is well worth while chasing down the latest version.

Andrew

---

### Post by dhiman33 on 2010-11-12
:KSThanks andrew.46 for the reply. I'm gonna install mkvmerge from software center. I understand now that the problem in using x264 can be the specification of raw input file while I can use libx264 in ffmpeg to input any kind of file. But my question is---can I do everything with libx264 that I can do with x264? Like fine tuning the psy-radius etc. etc. Has libx264 got the same encoding power and lots of settings like x264? If not, can I somehow use ffmpeg to provide the raw input to x264? Pls tell the way then...

---

### Post by andrew.46 on 2010-11-12
Hi dhiman33,

Can I ask have you experimented with x264 encoding yet? Often the best way is to get a couple of test files and dive right in, some of the questions you have asked will then be answered with your own experience. As far as I know FFmpeg cannot adjust the psy-radius settings *as easily* as x264, although this is a trivial matter with x264 itself:

```

andrew@skamandros~$ **[COLOR="Red"]x264 --fullhelp | grep psy[/COLOR]**
                                  Only one psy tuning can be used at a time.
                                  - film (psy tuning):
                                    --deblock -1:-1 --psy-rd <unset>:0.15
                                  - animation (psy tuning):
                                    --psy-rd 0.4:<unset> --aq-strength 0.6
                                  - grain (psy tuning):
                                    --pbratio 1.1 --psy-rd <unset>:0.25
                                  - stillimage (psy tuning):
                                    --psy-rd 2.0:0.7
                                  - psnr (psy tuning):
                                    --aq-mode 0 --no-psy
                                  - ssim (psy tuning):
                                    --aq-mode 2 --no-psy
      --psy-rd                Strength of psychovisual optimization ["1.0:0.0"]
      --no-psy                Disable all visual optimizations that worsen

```

These can be used with the *--tune* setting, eg: *--tune film*. For FFmpeg have a look at:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -h | grep psy[/COLOR]**
FFmpeg version SVN-r25726, Copyright (c) 2000-2010 the FFmpeg developers
  built on Nov 12 2010 17:26:26 with gcc 4.3.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 --enable-zlib --enable-libvpx --enable-libxvid --enable-nonfree --enable-gpl
  libavutil     50.33. 0 / 50.33. 0
  libavcore      0.12. 1 /  0.12. 1
  libavcodec    52.94. 4 / 52.94. 4
  libavformat   52.84. 0 / 52.84. 0
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.60. 0 /  1.60. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
   psy                     E.V.. use psycho visual optimization
-psy_rd            <float> E.V.. specify psycho visual strength
-psy_trellis       <float> E.V.. specify psycho visual trellis

```

BTW the input files when using x264 become less of an issue if you see the lavf option marked as 'yes'. have you had a look at this? My best advice again is to grab some sample files and start encoding with different options yourself...

Andrew

---

### Post by hugmenot on 2010-11-12
[LIST]
[*]The presets are usually tuned by experts. I doubt that a newbie can »get best quality, use access to ALL options.« There was a time when people tried to improve MP3 by using insanely long option stirng in Lame encoder. All that was disabled and discouraged later.
[*]What about FFMpeg’s aacenc? Did it progress recently?
[/LIST]

---

### Post by dhiman33 on 2010-11-13
Ok andrew I've tested x264 with 2 test files. First I should tell that when I type x264 --help I see that lavf is enabled(yes). I've tried x264 with 2 mkv files. The first one opened with lavf[info]:widthxheight and converted easily but the second one couldn't be opened. Is there a method by which every file can be opened with x264?

PS: OMG after x264 failed to open the movie it now can't be opened by video players, mediainfo also doesn't show anything!!

---

### Post by dhiman33 on 2010-11-13
:PHmm.. I think the 2nd file didn't open 'cause it had both video &  audio streams. I copied the video stream into an mkv container using  ffmpeg, and now x264 can convert it using lavf [info]: 640x384p suffix  at the end:guitar:. But I have a question. Do I have to necessarily enter the  framerate with lavf along with the frame size,or lavf/x264 can  understand it automatically? In andrews example there's a line---"lavf [info]:  848x358p 0:1 @ 2397/100 fps (vfr)" what's the meaning of 0:1 here? I can  assume u have to write 23.97=2397/100 but what's vfr?(variable  framerate?)


PS: Also I can't understand this-- Please explain it.
ffmpeg -i input.foo -f wav - | neroAacEnc -ignorelength -if - -of output.mp4

---

### Post by FakeOutdoorsman on 2010-11-13
> **dhiman33 said:**
> PS: Also I can't understand this-- Please explain it.
ffmpeg -i input.foo -f wav - | neroAacEnc -ignorelength -if - -of output.mp4

Each command has a "help" option.  If you don't know how to invoke the help, then just run the command with no options and it will often tell you what to type to get the help.
```
$ ffmpeg -h
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
-f fmt              force format
...
```

```
$ neroAacEnc -help
Usage:
neroAacEnc [options] -if <input-file> -of <output-file>
Where:
<input-file>  : Path to source file to encode.
                The file must be in Microsoft WAV format and contain PCM data.
                Specify - to encode from stdin.
                Note that multiple input files can be specified, they will be
                encoded together into a single output file with chapter marks
                indicating source file divisions.
<output-file> : Path to output file to encode to, in MP4 format.

-ignorelength : Ignores length signaled by WAV headers of input file.
                Useful for certain frontends using stdin.
...
```

---

### Post by hugmenot on 2010-11-13
> **dhiman33 said:**
> 
PS: Also I can't understand this-- Please explain it.
ffmpeg -i input.foo -f wav - | neroAacEnc -ignorelength -if - -of output.mp4

The dash - represents stdout and stdin. These are pseudo-files.
You basically plug ffmpeg and Nero together with the pipe | so ffmpeg pumps decoded audio data via the pipe into Nero. No need to write temporary files.

---

### Post by andrew.46 on 2010-11-14
Actually the syntax I demonstrated for x264 was more than a little bare, this is an animated move so perhaps something like the following would have been a better example:

```
x264 *[COLOR="Red"]--preset slow --tune animation[/COLOR]* --crf 24 -o test.mp4 guardians.mov 
```

Running this as follows:

```

andrew@skamandros~/samples$ x264 --preset slow --tune animation --crf 24 -o test.mp4 guardians.mov 
lavf [info]: 848x358p 0:1 @ 2397/100 fps (vfr)
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
x264 [info]: profile High, level 3.1
x264 [info]: frame I:37    Avg QP:20.81  size: 16710                           
x264 [info]: frame P:1277  Avg QP:25.33  size:  5288
x264 [info]: frame B:2035  Avg QP:28.20  size:  2171
x264 [info]: consecutive B-frames:  8.7% 27.2%  7.2% 51.6%  1.8%  3.4%
x264 [info]: mb I  I16..4: 33.6% 41.9% 24.6%
x264 [info]: mb P  I16..4: 17.3% 13.6%  2.7%  P16..4: 29.0%  7.4%  2.7%  0.0%  0.0%    skip:27.3%
x264 [info]: mb B  I16..4:  2.7%  3.1%  0.7%  B16..8: 22.8%  3.5%  1.0%  direct: 2.5%  skip:63.6%  L0:36.6% L1:52.4% BI:11.0%
x264 [info]: 8x8 transform intra:42.0% inter:68.2%
x264 [info]: direct mvs  spatial:98.8% temporal:1.2%
x264 [info]: coded y,uvDC,uvAC intra: 32.5% 49.6% 10.4% inter: 10.5% 14.1% 1.2%
x264 [info]: i16 v,h,dc,p: 30% 26% 15% 28%
x264 [info]: i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 13% 14% 27%  6%  8%  7% 10%  6% 10%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 17% 13% 16%  7% 10%  8% 11%  7% 12%
x264 [info]: i8c dc,h,v,p: 52% 26% 14%  7%
x264 [info]: Weighted P-Frames: Y:12.8%
x264 [info]: ref P L0: 68.1% 13.4% 10.6%  2.7%  1.7%  1.2%  0.9%  0.5%  0.4%  0.4%  0.1%  0.0%
x264 [info]: ref B L0: 87.9%  5.5%  2.7%  1.1%  0.9%  0.7%  0.6%  0.3%  0.2%
x264 [info]: ref B L1: 97.9%  2.1%
x264 [info]: kb/s:675.17

encoded 3349 frames, 7.73 fps, 675.21 kb/s

```

The result is quite spectacular! Can I say, not for the first time: I love the commandline :).

Andrew

---

### Post by P4man on 2010-11-14
Question to all the command line transcode experts here; I have a bunch of video's in mkv and mp4 containers (usually h264 video) which have 6 channel AAC audio. XBMC doesnt handle the audio well on a stereo set, I have to convert it to stereo or better (since I might add a DTS audio set later), add a stereo stream and set it as first stream, keep the 6 channel audio for possible future se.

Im doing this now with a variety of apps like avidemux but its pita as I have a lot of such movies.  How could I do this from the command line? THe video stream shouldnt be touched, just copied.

---

### Post by dhiman33 on 2010-11-14
"ffmpeg -i input.mp3 output.wav | neroaacenc -hev2 -if -of out.m4a" ---why this shouldn't work?](*,) what are the errors in this command? I think I'm doing o.k, I first convert the mp3 to wav and pass it to neroaacenc as stdin, so after "-if" I leave a blank space:tongue:. But this only gives the wav file as output and writes it in the disk, neroaacenc is not triggered! :evil:Should I change that "output.wav" to something else? I can't find these info's on ffmpeg help or manual, so pls answer with proper explanation.:-?

---

### Post by FakeOutdoorsman on 2010-11-14
> **P4man said:**
> Question to all the command line transcode experts here; I have a bunch of video's in mkv and mp4 containers (usually h264 video) which have 6 channel AAC audio. XBMC doesnt handle the audio well on a stereo set, I have to convert it to stereo or better (since I might add a DTS audio set later), add a stereo stream and set it as first stream, keep the 6 channel audio for possible future se.

Im doing this now with a variety of apps like avidemux but its pita as I have a lot of such movies.  How could I do this from the command line? THe video stream shouldnt be touched, just copied.
*mkvmerge* is probably your best bet because it can allow you to re-order the streams (see the *--track-order* option, I think). FFmpeg can add an additional stream too, but I'm not sure how (or if it's possible) to re-order the streams in a particular order for the output:
```
ffmpeg -i input -vcodec copy -acodec copy output -i input.audio -acodec copy -newaudio
```

Once you get your *mkvmerge* command working you can then add it to a script to do the work for you for all of the files.

> **dhiman33 said:**
> ```
ffmpeg -i input.mp3 output.wav | neroaacenc -hev2 -if -of out.m4a
```why this shouldn't work?](*,) what are the errors in this command? I think I'm doing o.k, I first convert the mp3 to wav and pass it to neroaacenc as stdin, so after "-if" I leave a blank space:tongue:. But this only gives the wav file as output and writes it in the disk, neroaacenc is not triggered! :evil:Should I change that "output.wav" to something else? I can't find these info's on ffmpeg help or manual, so pls answer with proper explanation.:-?
Why don't you simply adapt the example I gave you? Why are you making a .wav file? The whole reason to use a pipe ( | <-- this is a pipe ) is to avoid intermediate files, such as the *output.wav* you are attempting to create.  Why do you want to use *-hev2*?  From *neroAacEnc -help*:
> Note that the above switches (-lc, -he, -hev2) should not be used; optimal AAC profile is automatically determined from quality/bitrate settings when no override is specified.

---

### Post by dhiman33 on 2010-11-15
Fakeoutdoorsman, when I first used ur method it didn't work!:shock:(for some typo of mine I guess:oops:) I thought ur command itself had some typo in it:---), so I tried other methods. But now I've tried ur method once again and it works now! Though I still don't understand how that command works--hugmenot gives a little hint but I can't fully understand it.

8-)To P4man-- To reorder streams u might need to use -map command?

for eg. say ffmmpeg has 3 streams, stream0.0 is video, stream 0.1 is audio in eng. and stream 0.2 is audio in hindi. U wanna get an output which has stream 0.1=hindi and stream 0.2=eng audio.

U do--"ffmpeg -i a.mkv -vcodec copy -acodec copy -map 0.2[: 0.1] -acodec copy -map 0.1[: 0.2] b.mkv"--Right now I'm typing this from windows so I can't test this command for u, but I think this command will work o.k.:guitar:

---

### Post by hugmenot on 2010-11-15
> **dhiman33 said:**
> Fakeoutdoorsman, when I first used ur method it didn't work!:shock:(for some typo of mine I guess:oops:) I thought ur command itself had some typo in it:---), so I tried other methods. But now I've tried ur method once again and it works now! Though I still don't understand how that command works--hugmenot gives a little hint but I can't fully understand it.


Yeah, you glossed over what I wrote and just left out the dashes.

Imagine two programs:

```
decoder -i input -o temp
encoder -i temp -o result
```

Depending on the programs they may support writing to stdout and/or reading from stdin. If *both* do you can combine them with a pipe

```
decoder -i input -o - | encoder -i - -o result
```

A theoretical variant of this could also be this

```
decoder input - | encoder - result
```

The dash character is just a symbol – think water main.

---

### Post by hugmenot on 2010-11-15
> **P4man said:**
> Question to all the command line transcode experts here; I have a bunch of video's in mkv and mp4 containers (usually h264 video) which have 6 channel AAC audio. XBMC doesnt handle the audio well on a stereo set, I have to convert it to stereo or better (since I might add a DTS audio set later), add a stereo stream and set it as first stream, keep the 6 channel audio for possible future se.

Im doing this now with a variety of apps like avidemux but its pita as I have a lot of such movies.  How could I do this from the command line? THe video stream shouldnt be touched, just copied.


I would use mencoder because ffmpeg doesn’t downmix to stereo. It just uses the two first channels and discards the rest.

Copying video data is -ovc copy in mencoder.

---

### Post by P4man on 2010-11-15
Thanks. I just found avidemux and mkvmerge let me do this and both support job lists, so thats good enough for me. I just extract and downmix the audio with avidemux and then merge the stereo track as a new (and default) audio track in mkvmerge. Thats not a whole lot more work than a bash script since there is a variety of codecs used anyhow. Only thing missing is a way to boost center channel volume, but I can live with that. Thanks for the tips anyway

---

### Post by hugmenot on 2010-11-15
Your center channel probably just get discarded.

If only you didn&#8217;t insist on keeping the original audio as the second stream in the file, it would be a one-liner in mencoder. It can even mix the channels for you. If you use the [hrtf]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-surround.html") filter it can preserve some spatial audio for use with headphones.


```
mencoder in.mkv -ovc copy -oac mp3lame -lameopts cbr:br=128 -channels 2 -o out.mkv
```

or 

```
mencoder in.mkv -ovc copy mp3lame -lameopts cbr:br=128 -channels 6 -af hrtf -oac -o out.mkv
```


You can also mix the channels freely. From the man page:

```
 pan=n[:L00:L01:L02:...L10:L11:L12:...Ln0:Ln1:Ln2:...]
        Mixes channels arbitrarily.  Basically a combination of the vol&#8208;
        ume  and  the  channels filter that can be used to down-mix many
        channels to only a few, e.g. stereo to mono or vary the  "width"
        of  the  center speaker in a surround sound system.  This filter
        is hard to use, and will require some tinkering before  the  de&#8208;
        sired result is obtained.  The number of options for this filter
        depends on the number of output channels.   An  example  how  to
        downmix  a six-channel file to two channels with this filter can
        be found in the examples section near the end.
           <n>
                number of output channels (1-8)
           <Lij>
                How much of input channel i is mixed into output channel
                j  (0-1).  So in principle you first have n numbers say&#8208;
                ing what to do with the first input channel, then n num&#8208;
                bers  that  act on the second input channel etc.  If you
                do not specify any numbers for some input channels, 0 is
                assumed.

        EXAMPLE:
           mplayer -af pan=1:0.5:0.5 media.avi
                Would down-mix from stereo to mono.
           mplayer -af pan=3:1:0:0.5:0:1:0.5 media.avi
                Would give 3 channel output leaving channels 0 and 1 in&#8208;
                tact, and mix channels 0 and 1  into  output  channel  2
                (which could be sent to a subwoofer for example).

Play a 6-channel AAC file with only two speakers:

  mplayer -rawaudio format=0xff -demuxer rawaudio \
    -af pan=2:.32:.32:.39:.06:.06:.39:.17:-.17:-.17:.17:.33:.33 \
    adts_he-aac160_51.aac

You might want to play a bit with the pan values (e.g multiply  with  a
value) to increase volume or avoid clipping.



```

---

### Post by P4man on 2010-11-16
avidemux doesnt seem to discard the center channel, that would make all conversations un-understandable (and thats pretty much what happens in XBMC when using 6channel aac audio). I also noticed an option for dynamic range compression which seems to get me a better result.

Ill play with mencoder this weekend though. I just browsed through the manpage and its.. well, impressively complete lol.

---

### Post by dhiman33 on 2010-11-16
Hi hugmenot!:KS

    Thnks for the reply, now I clearly understand that command including pipe:guitar:. Your explanation really helped,bro.\\:D/

---

