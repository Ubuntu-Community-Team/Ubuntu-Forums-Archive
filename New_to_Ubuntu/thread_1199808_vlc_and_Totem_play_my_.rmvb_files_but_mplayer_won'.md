---
title: "vlc and Totem play my .rmvb files but mplayer won't"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-29
vlc and Totem play my .rmvb files but mplayer won't any suggestions?

I can open rm or rmvb files in totem or vlc but mplayer won't open them says can't recognizes -vo

Have tried changing all the internal codecs 

Any suggestions are appreciated

Thanks


Powel

---

### Post by powel212 on 2009-06-29
Avidemux can't open them either. Would love to be able to re-encode them in Avidemux too if anyone knows how to accomplish that.

Damn real media files.

Powel

---

### Post by LowSky on 2009-06-29
you could always use real player...

[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

any reason you need mplayer?

---

### Post by powel212 on 2009-06-29
I love Mplayer.

I have a problem with RealPlayer. I have not used it in years. The reason being I found it to act more like a virus than a media player when I did use it so many years ago. Maybe it has changed.

But mplayer and Totem both work so well.

Powel

---

### Post by powel212 on 2009-06-30
Still looking for help on getting Mplayer to run my .rmvb files.

anyone have any insight here.

I am sure I am missing something very simple because Mplayer used to play .rmvb files in ibex. I guess there is a configuration error somewhere on my box.

Any help is appreciated.

Powel

---

### Post by andrew.46 on 2009-06-30
Hi powel212,

> **powel212 said:**
> Still looking for help on getting Mplayer to run my .rmvb files.

Can you post the full terminal output from:

```
mplayer -v *myfile.rmvb*
```

MPlayer can certainly play rmvb files so there must be a small error in configuration there somewhere.

Andrew

---

### Post by powel212 on 2009-06-30
mplayer -v myfile.rmvb outputs:

```
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz (Family: 6, Model: 23, Stepping: 10)                                                                 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                  
Compiled with runtime CPU detection.                                         
get_path('codecs.conf') -> '/home/drock/.mplayer/codecs.conf'                
Reading /home/drock/.mplayer/codecs.conf: Can't open '/home/drock/.mplayer/codecs.conf': No such file or directory                                        
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory                                                        
Using built-in default codecs.conf.                                          
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder                                                                       
CommandLine: '-v' 'myfile.rmvb'                                              
init_freetype                                                                
get_path('font/font.desc') -> '/home/drock/.mplayer/font/font.desc'          
font: can't open file: /home/drock/.mplayer/font/font.desc                   
font: can't open file: /usr/share/mplayer/font/font.desc                     
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay                     
get_path('fonts') -> '/home/drock/.mplayer/fonts'                            
Using nanosleep() timing
get_path('input.conf') -> '/home/drock/.mplayer/input.conf'
Can't open input config file /home/drock/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('myfile.rmvb.conf') -> '/home/drock/.mplayer/myfile.rmvb.conf'

Playing myfile.rmvb.
get_path('sub/') -> '/home/drock/.mplayer/sub/'
File not found: 'myfile.rmvb'
Failed to open myfile.rmvb.

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)

```

Powel

---

### Post by mc4man on 2009-06-30
Just to get you moving towards a solution, there seems to be a small bit of confusion

mplayer -v [COLOR="Blue"]myfile[/COLOR].rmvb 

replace the blue w/ the actual name of your .rmvb 

The command assumes the file is is loose in your home folder, so either put it there if not already or 
mplayer -v [COLOR="Blue"]/path/to/myfile[/COLOR].rmvb 

(unless your .rmvb happened to be named "myfile", sorta doubt

---

### Post by powel212 on 2009-06-30
&#21704;&#21704;(haha)

Yes I can be a tool sometimes.

```
drock@jaunty:~$ mplayer -v /home/drock/anactualfile.rmvb
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team         
CPU: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz (Family: 6, Model: 23, Stepping: 10)                                                                 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                  
Compiled with runtime CPU detection.                                         
get_path('codecs.conf') -> '/home/drock/.mplayer/codecs.conf'                
Reading /home/drock/.mplayer/codecs.conf: Can't open '/home/drock/.mplayer/codecs.conf': No such file or directory                                        
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory                                                        
Using built-in default codecs.conf.                                          
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder                                                                       
CommandLine: '-v' '/home/drock/anactualfile.rmvb'                            
init_freetype                                                                
get_path('font/font.desc') -> '/home/drock/.mplayer/font/font.desc'          
font: can't open file: /home/drock/.mplayer/font/font.desc                   
font: can't open file: /usr/share/mplayer/font/font.desc                     
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay                     
get_path('fonts') -> '/home/drock/.mplayer/fonts'                            
Using nanosleep() timing                                                     
get_path('input.conf') -> '/home/drock/.mplayer/input.conf'                  
Can't open input config file /home/drock/.mplayer/input.conf: No such file or directory                                                                   
Parsing input config file /etc/mplayer/input.conf                            
Input config file /etc/mplayer/input.conf parsed: 81 binds                   
Setting up LIRC support...                                                   
mplayer: could not connect to socket                                         
mplayer: No such file or directory                                           
Failed to open LIRC support. You will not be able to use your remote control.
get_path('anactualfile.rmvb.conf') -> '/home/drock/.mplayer/anactualfile.rmvb.conf'                                                                       

Playing /home/drock/anactualfile.rmvb.
get_path('sub/') -> '/home/drock/.mplayer/sub/'
[file] File size is 1071899991 bytes           
STREAM: [file] /home/drock/anactualfile.rmvb   
STREAM: Description: File                      
STREAM: Author: Albeu                          
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: rm format                                      
Checking for YUV4MPEG2                                     
ASF_check: not ASF guid!                                   
Checking for NuppelVideo                                   
Checking for REAL                                          
REAL file format detected.                                 
real: Header size: 18                                      
real: Header object version: 1                             
real: File version: 0                                      
Chunk: PROP (504f5250) (size: 0x32, offset: 0x12)          
First index chunk offset: 0x3fe27d19                       
First data chunk offset: 0x3ff                             
Flags (9): [save allowed]                                  
Chunk: CONT (544e4f43) (size: 0x40, offset: 0x44)          
Chunk: MDPR (5250444d) (size: 0xac, offset: 0x84)          
Found new stream (id: 0)                                   
Stream description: Audio Stream                           
Stream mimetype: audio/x-pn-realaudio                      
==> Found audio stream: 0                                  
[real] Audio stream found, -aid 0                          
Found audio stream!                                        
version: 5                                                 
header size: 78                                            
coded_frame_size: 930                                      
sub_packet_h: 16                                           
frame_size: 930                                            
sub_packet_size: 186                                       
samplerate: 44100, channels: 2                             
audio fourcc: cook (6b6f6f63)                              
======= WAVE Format =======                                
Format Tag: 28515 (0x6F63)                                 
Channels: 2                                                
Samplerate: 44100                                          
avg byte/sec: 8010                                         
Block align: 186                                           
bits/sample: 16                                            
cbSize: 16                                                 
Unknown extra header dump: [1] [0] [0] [3] [8] [0] [0] [25] [0] [0] [0] [0] [0] [6] [0] [5]                                                               
==========================================================================   
### skipping 0 bytes of codec info                                           
Chunk: MDPR (5250444d) (size: 0x70, offset: 0x130)                           
Found new stream (id: 1)                                                     
Stream description: Video Stream                                             
Stream mimetype: video/x-pn-realvideo                                        
==> Found video stream: 1                                                    
[real] Video stream found, -vid 1                                            
video fourcc: RV40 (30345652)                                                
### skipping 0 bytes of codec info                                           
Chunk: MDPR (5250444d) (size: 0x255, offset: 0x1a0)                          
Found new stream (id: 2)                                                     
Stream mimetype: logical-fileinfo                                            
Got a logical-fileinfo chunk                                                 
### skipping 535 bytes of codec info                                         
Chunk: DATA (41544144) (size: 0x3fe27924, offset: 0x3f5)                     
Packets in file: 1159308                                                     
Reading index table from index chunk (1071807769)                            
size: 77132 bytes                                                            
entries: 5508                                                                
stream_id: 0                                                                 
next_header_pos: 1071884901                                                  
Reading index table from index chunk (1071884901)                            
size: 15070 bytes                                                            
entries: 1075                                                                
stream_id: 1                                                                 
next_header_pos: 1071899971                                                  
Reading index table from index chunk (1071899971)                            
size: 20 bytes                                                               
entries: 0                                                                   
stream_id: 2                                                                 
next_header_pos: 0                                                           
Auto-selected RM audio ID = 0                                                
Auto-selected RM video ID = 1                                                
VIDEO:  RV40 [00400040,20100801]  640x480  (aspect 0.00)  29.00 fps          
AUDIO:  cook [6B6F6F63]                                                      
VIDEO:  [RV40]  640x480  24bpp  29.000 fps    0.0 kbps ( 0.0 kbyte/s)        
[V] filefmt:11  fourcc:0x30345652  size:640x480  fps:29.00  ftime:=0.0345    
Clip info:                                                                   
 author: ken22                                                               
 copyright: nike                                                             
 comment:                                                                    
get_path('sub/') -> '/home/drock/.mplayer/sub/'                              
X11 opening display: :0.0                                                    
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)                          
vo: X11 running at 2424x1050 with depth 24 and 32 bpp (":0.0" => local display)                                                                           
[x11] Detected wm supports NetWM.                                            
[x11] Detected wm supports FULLSCREEN state.                                 
[x11] Detected wm supports ABOVE state.                                      
[x11] Detected wm supports BELOW state.                                      
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms          
xscreensaver_disable: Could not find XScreenSaver window.                    
GNOME screensaver disabled                                                   
[VO_XV] Could not grab port 280.                                             
[VO_XV] Could not grab port 281.                                             
[xv common] Drawing no colorkey.                                             
[xv common] Maximum source image dimensions: 2046x2046                       
==========================================================================   
Opening video decoder: [realvid] RealVideo decoder                           
realvideo codec id: 0x40004000  sub-id: 0x01081020                           
opening shared obj '/usr/lib/codecs/drvc.so'                                 
Error: /usr/lib/codecs/drvc.so: cannot open shared object file: No such file or directory                                                                 
ERROR: Could not open required DirectShow codec drvc.so.                     
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
realvideo codec id: 0x40004000  sub-id: 0x01081020                           
ERROR: Could not open required DirectShow codec drvc.dll.                    
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
realvideo codec id: 0x40004000  sub-id: 0x01081020                           
opening shared obj '/usr/lib/codecs/drv4.so.6.0'                             
Error: /usr/lib/codecs/drv4.so.6.0: cannot open shared object file: No such file or directory                                                             
ERROR: Could not open required DirectShow codec drv4.so.6.0.                 
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
realvideo codec id: 0x40004000  sub-id: 0x01081020                           
ERROR: Could not open required DirectShow codec drv43260.dll.                
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
realvideo codec id: 0x40004000  sub-id: 0x01081020                           
opening shared obj '/usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc'         
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory                                         
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.                                                                          
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Cannot find codec matching selected -vo and video format 0x30345652.         
Read DOCS/HTML/en/codecs.html!                                               
==========================================================================   
==========================================================================   
Forced audio codec: mad                                                      
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders             
dec_audio: Allocating 192000 + 65536 = 257536 bytes for output buffer.       
FFmpeg's libavcodec audio codec                                              
INFO: libavcodec init OK!                                                    
AUDIO: 44100 Hz, 2 ch, s16le, 64.1 kbit/4.54% (ratio: 8010->176400)          
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
[dummy] Was reinitialized: 44100Hz/2ch/s16le
[dummy] Was reinitialized: 44100Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...

```

Powel

---

### Post by andrew.46 on 2009-07-01
Hi Powel,

Oops I guess I was less than clear about the *myfile.rmvb* thing :-). I notice that you are using Karmic Koala but looks like an older version of MPlayer, your version should be marked rc3?

Could you see if you have any joy from:

```
mplayer -vo xv -vc ffrv40 /home/drock/anactualfile.rmvb
```

this forces the FFmpeg real video codec and would normally be enough to get Real Video files going. Another step that is often required is to install libstdc++5.

All the best,

Andrew

---

### Post by powel212 on 2009-07-01
I installed libstdc++5 - still no love.

Here is the output with "forced"

```
drock@jaunty:~$ mplayer -vo xv -vc ffrv40 /home/drock/anactualfile.rmvb
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team                        
CPU: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz (Family: 6, Model: 23, Stepping: 10)                                                                 
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                  
Compiled with runtime CPU detection.                                         
mplayer: could not connect to socket                                         
mplayer: No such file or directory                                           
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/drock/anactualfile.rmvb.
REAL file format detected.            
Stream description: Audio Stream      
Stream mimetype: audio/x-pn-realaudio 
[real] Audio stream found, -aid 0     
Stream description: Video Stream      
Stream mimetype: video/x-pn-realvideo 
[real] Video stream found, -vid 1     
Stream mimetype: logical-fileinfo     
VIDEO:  [RV40]  640x480  24bpp  29.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 author: ken22
 copyright: nike
 comment:
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Forced video codec: ffrv40
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.1 kbit/4.54% (ratio: 8010->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video

```

Thanks for your help

Powel

---

### Post by andrew.46 on 2009-07-01
Hi powel,

Seems a little as the FFmpeg decoder should play this file quite well. Never fear there are a few options. Could you check you MPlayer's ability to play real video files as follows:

```

andrew@skamandros~$ **[COLOR="Purple"]mplayer -vc help | grep rv40[/COLOR]**
rv40        realvid   problems  Linux RealPlayer 9 RV40  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40  [drvc.bundle/Contents/MacOS/drvc]
ffrv40      ffmpeg    working   FFmpeg RV40  [rv40]

```

Can I ask if this version of MPlayer is the Karmic one or the Jaunty version? And is it possible you can post the problem file somewhere?

Edit: Perhaps if posting the file is a problem you could have a look at this file:

```
wget http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/samplerv.rmvb
```

This one plays perfectly with MPlayer as follows:

```

andrew@skamandros~/samples$ **[COLOR="Purple"]mplayer -afm ffmpeg -vfm ffmpeg samplerv.rmvb [/COLOR]**
MPlayer SVN-r29408-4.2.4 (C) 2000-2009 MPlayer Team

Playing samplerv.rmvb.
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  720x576  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 copyright: (C) 2005
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
**[COLOR="Purple"]Selected video codec: [ffrv40] vfm: ffmpeg (FFmpeg RV40)[/COLOR]**
==========================================================================
==========================================================================
Trying to force audio codec driver family ffmpeg...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 6 ch, s16le, 131.3 kbit/3.10% (ratio: 16408->529200)
**[COLOR="Purple"]Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio)[/COLOR]**
==========================================================================
AO: [oss] 44100Hz 6ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x576 => 720x576 Planar YV12 
A:  79.2 V:  79.2 A-V:  0.007 ct: -0.631 1967/1967 20%  1%  1.2% 1 0 

Exiting... (End of file)

```


All the best,

Andrew

---

### Post by powel212 on 2009-07-01
Actually I am running Mplayer in Jaunty for these tests. I am testing karmic on another platform.

Here is the output with the sample file you suggested.
```
                                                             
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1                  
Compiled with runtime CPU detection.                                         
mplayer: could not connect to socket                                         
mplayer: No such file or directory                                           
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/drock/samplerv.rmvb.
REAL file format detected.        
Stream description: Video Stream  
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 0    
Stream description: Audio Stream     
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 1    
Stream mimetype: logical-fileinfo    
VIDEO:  [RV40]  720x576  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:                                                           
 copyright: (C) 2005                                                 
xscreensaver_disable: Could not find XScreenSaver window.            
GNOME screensaver disabled                                           
==========================================================================
Trying to force video codec driver family ffmpeg...                       
Opening video decoder: [realvid] RealVideo decoder                        
Error: /usr/lib/codecs/drvc.so: cannot open shared object file: No such file or directory                                                                 
ERROR: Could not open required DirectShow codec drvc.so.                     
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
ERROR: Could not open required DirectShow codec drvc.dll.                    
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
Error: /usr/lib/codecs/drv4.so.6.0: cannot open shared object file: No such file or directory                                                             
ERROR: Could not open required DirectShow codec drv4.so.6.0.                 
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
ERROR: Could not open required DirectShow codec drv43260.dll.                
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Opening video decoder: [realvid] RealVideo decoder                           
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory                                         
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.                                                                          
Read the RealVideo section of the DOCS!                                      
VDecoder init failed :(                                                      
Cannot find codec matching selected -vo and video format 0x30345652.         
Read DOCS/HTML/en/codecs.html!                                               
==========================================================================   
==========================================================================   
Forced audio codec: mad                                                      
Trying to force audio codec driver family ffmpeg...                          
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders             
[cook @ 0xf96fa0]MC_COOK not supported!                                      
Could not open codec.                                                        
ADecoder init failed :(                                                      
ADecoder init failed :(                                                      
Opening audio decoder: [realaud] RealAudio decoder                           
Error: /usr/lib/codecs/cook.so: cannot open shared object file: No such file or directory                                                                 
ERROR: Could not open required DirectShow codec cook.so.                     
Read the RealAudio section of the DOCS!                                      
ADecoder preinit failed :(                                                   
ADecoder init failed :(                                                      
Opening audio decoder: [realaud] RealAudio decoder                           
Error: /usr/lib/codecs/cook.so.6.0: cannot open shared object file: No such file or directory                                                             
ERROR: Could not open required DirectShow codec cook.so.6.0.                 
Read the RealAudio section of the DOCS!                                      
ADecoder preinit failed :(                                                   
ADecoder init failed :(                                                      
Opening audio decoder: [realaud] RealAudio decoder                           
ERROR: Could not open required DirectShow codec cook.dll.                    
Read the RealAudio section of the DOCS!                                      
ADecoder preinit failed :(                                                   
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
ERROR: Could not open required DirectShow codec cook3260.dll.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/codecs/cook.bundle/Contents/MacOS/cook: cannot open shared object file: No such file or directory
ERROR: Could not open required DirectShow codec cook.bundle/Contents/MacOS/cook.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x6B6F6F63.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)
```

> Could you check you MPlayer's ability to play real video files as follows:

```
mplayer -vc help | grep rv40
rv40        realvid   working   Linux RealPlayer 9 RV40 decoder  [drv4.so.6.0]
rv40win     realvid   working   Win32 RealPlayer 9 RV40 decoder  [drv43260.dll]
rv40mac     realvid   working   Mac OS X RealPlayer 9 RV40 decoder  [drvc.bundle/Contents/MacOS/drvc]

drock@jaunty:~$

```

Thanks again for your help

Powel

---

### Post by andrew.46 on 2009-07-01
Hi Powel,

Looks like you are missing the better parts of FFmpeg :-). Since you are using Jaunty you have a couple of choices:

[LIST=1]
[*]Use the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") MPlayer which I believe should be able to play these files, although I am not 100% sure of this :-). The sticking point will be exactly when the FFmpeg decoders were introduced and I am not entirely sure when this happened. rc2 was a couple of years ago though...
[*]Use the [svn MPlayer guide for Jaunty]("http://ubuntuforums.org/showthread.php?t=1081070") on these forums. I know this one will work as it is my guide :-). Also it picks up the *current* FFmpeg...
[/LIST]

All the best,

Andrew

---

### Post by mc4man on 2009-07-01
Taking a quick look at jaunty mplayer source (MPlayer 1.0rc2-[COLOR="Blue"]4.3.3[/COLOR] ) this is what's in libavcodec
> doug@doug-laptop:~/Desktop/mplayer_1.0~rc2.orig/libavcodec$ ls rv*
rv10.c

In the latest source I built (after building so extra files present

> doug@doug-laptop:~/Desktop/mplayer/svn/libavcodec$ ls rv*
rv10.c  rv30.d      rv30dsp.o  rv34data.h  rv40.c      rv40dsp.d
rv10.d  rv30data.h  rv30.o     rv34.h      rv40.d      rv40dsp.o
rv10.o  rv30dsp.c   rv34.c     rv34.o      rv40data.h  rv40.o
rv30.c  rv30dsp.d   rv34.d     rv34vlc.h   rv40dsp.c   rv40vlc2.h




missed last posts, probably irrelevant

---

### Post by powel212 on 2009-07-01
I will poke around in the mentioned areas.

Thanks for the help guys.

Powel

---

