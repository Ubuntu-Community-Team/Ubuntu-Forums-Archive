---
title: "FireFox crashes..."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by cartisdm on 2009-03-13
When I go to dc101.com and launched the Live Streaming Radio found [at this address]("http://dc101.com/cc-common/ondemand/player.html?world=st") my FireFox begins to play the stream then crashes after about 30 seconds everytime.  I ran "Firefox" from a terminal and here is the output after it crashes

```
e600c00c205365 reserved2:6 header_extension_size:4397
[00000342] asf private debug: found object guid: 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:39
[00000342] asf private debug: read "language list object" 1 entries
[00000342] asf private debug:   - 'en-us'
[00000342] asf private debug: found object guid: 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26
[00000342] asf private warning: unknown asf object (not loaded)
[00000342] asf private debug: found object guid: 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:224
[00000342] asf private debug: read "metadata object" 4 entries
[00000342] asf private debug:   - IsVBR=0
[00000342] asf private debug:   - DeviceConformanceTemplate=L1
[00000342] asf private debug:   - IsVBR=0
[00000342] asf private debug:   - DeviceConformanceTemplate=MP@LL
[00000342] asf private debug: found object guid: 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:3850
[00000342] asf private warning: unknown asf object (not loaded)
[00000342] asf private debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88
[00000342] asf private debug: read "extended stream properties object":
[00000342] asf private debug:   - start=0 end=0
[00000342] asf private debug:   - data bitrate=64040 buffer=1579 initial fullness=0
[00000342] asf private debug:   - alternate data bitrate=64040 buffer=1579 initial fullness=0
[00000342] asf private debug:   - maximum object size=1487
[00000342] asf private debug:   - flags=0x2
[00000342] asf private debug:   - stream number=1 language=0
[00000342] asf private debug:   - average time per frame=1407234
[00000342] asf private debug:   - stream name count=0
[00000342] asf private debug:   - payload extension system count=0
[00000342] asf private debug: found object guid: 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:132
[00000342] asf private debug: read "extended stream properties object":
[00000342] asf private debug:   - start=0 end=0
[00000342] asf private debug:   - data bitrate=304000 buffer=4000 initial fullness=0
[00000342] asf private debug:   - alternate data bitrate=304000 buffer=4000 initial fullness=0
[00000342] asf private debug:   - maximum object size=37018
[00000342] asf private debug:   - flags=0x2
[00000342] asf private debug:   - stream number=2 language=0
[00000342] asf private debug:   - average time per frame=333333
[00000342] asf private debug:   - stream name count=0
[00000342] asf private debug:   - payload extension system count=2
[00000342] asf private debug: found object guid: 0xd9aade20-0x7c17-0x4f9c-0xbc288555dd98e2a2 size:38
[00000342] asf private warning: unknown asf object (not loaded)
[00000342] asf private debug: found object guid: 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:244
[00000342] asf private debug: read "codec list object" reserved_guid:0x86d15241-0x311d-0x11d0-0xa3a400a0c90348f6 codec_entries_count:2
[00000342] asf private debug:   - codec[0] audio name:"Windows Media Audio 9.2" description:" 64 kbps, 44 kHz, stereo (A/V) 1-pass CBR" information_length:2
[00000342] asf private debug:   - codec[1] video name:"Windows Media Video 9" description:"" information_length:4
[00000342] asf private debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114
[00000342] asf private debug: read "stream Properties object" stream_type:0xf8699e40-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0xbfc3cd50-0x618f-0x11cf-0x8bb200aa00b4e220 time_offset:0 type_specific_data_length:28 error_correction_data_length:8 flags:0x1 stream_number:1
[00000342] asf private debug: found object guid: 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:134
[00000342] asf private debug: read "stream Properties object" stream_type:0xbc19efc0-0x5b4d-0x11cf-0xa8fd00805f5c442b error_correction_type:0x20fb5700-0x5b55-0x11cf-0xa8fd00805f5c442b time_offset:0 type_specific_data_length:56 error_correction_data_length:0 flags:0x2 stream_number:2
[00000342] asf private debug: found object guid: 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:38
[00000342] asf private debug: read "stream bitrate properties object"
[00000342] asf private debug:   - stream=1 bitrate=65734
[00000342] asf private debug:   - stream=2 bitrate=311768
[00000342] asf private debug: found object guid: 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:340450
[00000342] asf private debug: read "data object" file_id:0x7eb0b699-0x6f03-0x47e5-0xafa4dbd0bd86318a total data packet:74 reserved:257
[00000342] asf private debug: + 'Unknown' GUID 0x0-0x0-0x0-0x0000000000000000 size:0pos:0
[00000342] asf private debug:      + 'Header' GUID 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c size:5479pos:0
[00000342] asf private debug:      |    + 'Extended content description' GUID 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850 size:302pos:30
[00000342] asf private debug:      |    + 'Content Description' GUID 0x75b22633-0x668e-0x11cf-0xa6d900aa0062ce6c size:70pos:332
[00000342] asf private debug:      |    + 'File Properties' GUID 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365 size:104pos:402
[00000342] asf private debug:      |    + 'Header Extension' GUID 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365 size:4443pos:506
[00000342] asf private debug:      |    |    + 'Language List' GUID 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85 size:39pos:552
[00000342] asf private debug:      |    |    + 'Unknown' GUID 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9 size:26pos:591
[00000342] asf private debug:      |    |    + 'Metadata' GUID 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca size:224pos:617
[00000342] asf private debug:      |    |    + 'Padding' GUID 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8 size:3850pos:841
[00000342] asf private debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:88pos:4691
[00000342] asf private debug:      |    |    + 'Extended Stream Properties' GUID 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a size:132pos:4779
[00000342] asf private debug:      |    |    + 'Unknown' GUID 0xd9aade20-0x7c17-0x4f9c-0xbc288555dd98e2a2 size:38pos:4911
[00000342] asf private debug:      |    + 'Codec List' GUID 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6 size:244pos:4949
[00000342] asf private debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:114pos:5193
[00000342] asf private debug:      |    + 'Stream Properties' GUID 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365 size:134pos:5307
[00000342] asf private debug:      |    + 'Stream Bitrate Propoerties' GUID 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2 size:38pos:5441
[00000342] asf private debug:      + 'Data' GUID 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c size:340450pos:5479
[00000343] asf demuxer debug: found 2 streams
[00000336] main input debug: selecting program id=0
[00000343] asf demuxer debug: added new audio stream(codec:0x161,ID:1)
[00000343] asf demuxer debug: added new video stream(ID:2)
[00000343] main demuxer debug: using demux2 module "asf"
[00000344] main decoder debug: looking for decoder module: 25 candidates
[00000344] ffmpeg decoder debug: libavcodec initialized (interface 3352064 )
[00000344] ffmpeg decoder debug: ffmpeg codec (Windows Media Audio 2) started
[00000344] main decoder debug: using decoder module "ffmpeg"
[00000344] main decoder debug: thread 2812525456 (decoder) created at priority 0 (input/decoder.c:159)
[00000376] main decoder debug: looking for decoder module: 25 candidates
[00000376] ffmpeg decoder debug: libavcodec already initialized
[00000376] ffmpeg decoder debug: postprocessing disabled
[00000376] ffmpeg decoder debug: Extra data: 8 bits left, value: 0
 (wmv3@0xa5980990)
[00000376] ffmpeg decoder debug: ffmpeg codec (Windows Media Video 3) started
[00000376] main decoder debug: using decoder module "ffmpeg"
[00000376] main decoder debug: thread 2790259600 (decoder) created at priority 0 (input/decoder.c:159)
[00000338] access_mms access warning: unimplemented query in control
[00000336] main input debug: meta information:
[00000336] main input debug:   - 'Author' = 'SUMTER, CARISA'
[00000336] main input debug:   - track[0]:
[00000336] main input debug:      - 'Codec Name' = 'Windows Media Audio 9.2'
[00000336] main input debug:      - 'Codec Description' = ' 64 kbps, 44 kHz, stereo (A/V) 1-pass CBR'
[00000336] main input debug:   - track[1]:
[00000336] main input debug:      - 'Codec Name' = 'Windows Media Video 9'
[00000336] main input debug: `mms://a1802.v289256.c28925.g.vm.akamaistream.net/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf' successfully opened
[00000376] main decoder debug: no usable vout present, spawning one
[00000377] main video output debug: window size: 320x240
[00000377] main video output debug: looking for video output module: 6 candidates
[00000377] xvideo video output warning: no free XVideo port found for format 0x30323449 (I420)
[00000377] xvideo video output warning: no free XVideo port found for format 0x32595559 (YUY2)
[00000377] xvideo video output warning: no free XVideo port found for format 0x36315652 (RV16)
[00000377] x11 video output debug: XShm video extension v1.1 (with pixmaps, opcode: 148)
[00000377] x11 video output debug: Window manager supports NetWM
[00000377] x11 video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000377] x11 video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000377] x11 video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000377] main video output debug: using video output module "x11"
[00000377] x11 video output debug: x11 image size 400x300 (0,0,400x300)
[00000377] main video output debug: waiting for thread completion
[00000377] main video output debug: got 2 direct buffer(s)
[00000377] main video output debug: picture in 320x240 (0,0,320x240), chroma I420, ar 4:3, sar 1:1
[00000377] main video output debug: picture user 320x240 (0,0,320x240), chroma I420, ar 4:3, sar 1:1
[00000377] main video output debug: picture out 400x300 (0,0,400x300), chroma RV32, ar 4:3, sar 1:1
[00000377] main video output debug: looking for chroma module: 5 candidates
[00000378] main private debug: Registering subpicture channel, ID: 2
[00000378] main private debug: Registering subpicture channel, ID: 3
[00000378] main private debug: Registering subpicture channel, ID: 4
[00000378] main private debug: Registering subpicture channel, ID: 5
[00000377] main video output debug: using chroma module "i420_rgb"
[00000377] main video output debug: indirect render, mapping render pictures 0-7 to system pictures 2-9
[00000377] main video output debug: thread 2766142352 (video output) created at priority 0 (video_output/video_output.c:421)
[00000377] x11 video output debug: x11 image size 400x300 (0,0,400x300)
[00000344] main decoder debug: no aout present, spawning one
[00000383] main audio output debug: looking for audio output module: 5 candidates
[00000383] pulse audio output debug: Pulse mainloop started
[00000383] pulse audio output debug: Pulse stream connected
[00000383] pulse audio output debug: Pulse initialized successfully
[00000383] pulse audio output debug: Buffer metrics: maxlength=44100, tlength=39688, prebuf=19844, minreq=3968
[00000383] pulse audio output debug: Using sample spec 's16le 2ch 44100Hz', channel map 'front-left,front-right'.
[00000383] pulse audio output debug: Connected to device alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 (0, not suspended).
[00000383] main audio output debug: using audio output module "pulse"
[00000383] main audio output debug: output 's16l' 44100 Hz Stereo frame=1 samples/4 bytes
[00000383] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[00000383] main audio output debug: filter(s) 'fl32'->'s16l' 44100 Hz->44100 Hz Stereo->Stereo
[00000385] main private debug: looking for audio filter module: 24 candidates
[00000385] main private debug: using audio filter module "float32tos16"
[00000383] main audio output debug: found a filter for the whole conversion
[00000383] main audio output debug: looking for audio mixer module: 3 candidates
[00000383] main audio output debug: using audio mixer module "trivial_mixer"
[00000383] main audio output debug: input 's16l' 44100 Hz Stereo frame=1 samples/4 bytes
[00000383] main audio output debug: filter(s) 's16l'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
[00000412] main private debug: looking for audio filter module: 24 candidates
[00000412] main private debug: using audio filter module "s16tofloat32"
[00000383] main audio output debug: found a filter for the whole conversion
[00000383] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo
[00000413] main private debug: looking for audio filter module: 24 candidates
[00000413] main private debug: using audio filter module "bandlimited_resampler"
[00000383] main audio output debug: found a filter for the whole conversion
[00000383] pulse audio output debug: Pulse stream started
[00000383] main audio output warning: buffer is 46042 in advance, triggering downsampling
[00000383] main audio output warning: resampling stopped after 4111753 usec (drift: 22450)
[00000383] main audio output warning: buffer is 40192 in advance, triggering downsampling
[00000383] main audio output debug: audio output is starving (22927), playing silence
[00000338] access_mms access warning: EOF
[00000343] asf demuxer warning: cannot peek while getting new packet, EOF ?
[00000336] main input debug: EOF reached
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000383] main audio output warning: resampling stopped after 6204856 usec (drift: 17112)
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: waiting decoder fifos to empty
[00000336] main input debug: closing input
[00000342] asf private debug: free asf object 0xd2d0a440-0xe307-0x11d2-0x97f000a0c95ea850
[00000342] asf private debug: free asf object 0x75b22633-0x668e-0x11cf-0xa6d900aa0062ce6c
[00000342] asf private debug: free asf object 0x8cabdca1-0xa947-0x11cf-0x8ee400c00c205365
[00000342] asf private debug: free asf object 0x7c4346a9-0xefe0-0x4bfc-0xb229393ede415c85
[00000342] asf private warning: unknown asf object 0x26f18b5d-0x4584-0x47ec-0x9f5f0e651f0452c9
[00000342] asf private debug: free asf object 0xc5f8cbea-0x5baf-0x4877-0x8467aa8c44fa4cca
[00000342] asf private warning: unknown asf object 0x1806d474-0xcadf-0x4509-0xa4ba9aabcb96aae8
[00000342] asf private debug: free asf object 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a
[00000342] asf private debug: free asf object 0x14e6a5cb-0xc672-0x4332-0x8399a96952065b5a
[00000342] asf private warning: unknown asf object 0xd9aade20-0x7c17-0x4f9c-0xbc288555dd98e2a2
[00000342] asf private debug: free asf object 0x5fbf03b5-0xa92e-0x11cf-0x8ee300c00c205365
[00000342] asf private debug: free asf object 0x86d15240-0x311d-0x11d0-0xa3a400a0c90348f6
[00000342] asf private debug: free asf object 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365
[00000342] asf private debug: free asf object 0xb7dc0791-0xa9b7-0x11cf-0x8ee600c00c205365
[00000342] asf private debug: free asf object 0x7bf875ce-0x468d-0x11d1-0x8d82006097c9a2b2
[00000342] asf private debug: free asf object 0x75b22630-0x668e-0x11cf-0xa6d900aa0062ce6c
[00000342] asf private debug: free asf object 0x75b22636-0x668e-0x11cf-0xa6d900aa0062ce6c
[00000344] ffmpeg decoder debug: ffmpeg codec (Windows Media Audio 2) stopped
[00000344] main decoder debug: removing module "ffmpeg"
[00000344] main decoder debug: thread 2812525456 joined (input/decoder.c:191)
[00000344] main decoder debug: killing decoder fourcc `wma2', 0 PES in FIFO
[00000412] main private debug: removing module "s16tofloat32"
[00000413] main private debug: removing module "bandlimited_resampler"
[00000383] pulse audio output debug: Pulse Close
[00000383] main audio output debug: removing module "pulse"
[00000385] main private debug: removing module "float32tos16"
[00000383] main audio output debug: removing module "trivial_mixer"
[00000376] ffmpeg decoder debug: ffmpeg codec (Windows Media Video 3) stopped
[00000376] main decoder debug: removing module "ffmpeg"
[00000376] main decoder debug: thread 2790259600 joined (input/decoder.c:191)
[00000376] main decoder debug: killing decoder fourcc `WMV3', 0 PES in FIFO
[00000336] main input debug: Program doesn't contain anymore ES
[00000343] main demuxer debug: removing module "asf"
[00000338] access_mms access debug: closing stream
[00000338] main access debug: removing module "access_mms"
[00000336] main input debug: thread 2822749072 joined (input/input.c:412)
[00000283] main playlist debug: creating new input thread
[00000414] main input debug: waiting for thread completion
[00000414] main input debug: `mms://207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf' gives access `mms' demux `' path `207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf'
[00000414] main input debug: creating demux: access='mms' demux='' path='207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf'
[00000415] main demuxer debug: looking for access_demux module: 0 candidates
[00000415] main demuxer warning: no access_demux module matched "mms"
[00000414] main input debug: creating access 'mms' path='207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf'
[00000416] main access debug: looking for access2 module: 6 candidates
[00000416] access_mms access debug: waiting for connection...
[00000416] main access debug: net: connecting to 207.138.82.106 port 80
[00000416] main access debug: connection in progress
[00000414] main input debug: thread 2822749072 (input) created at priority 0 (input/input.c:265)
[00000416] access_mms access debug: connection(tcp) with "207.138.82.106:80" successful
[00000416] access_mms access debug: generated guid: babac001-e68c-f0bd-925a585a3ce5b605
[00000283] main playlist debug: garbage collector destroys 1 vout
[00000377] main video output debug: removing module "i420_rgb"
[00000377] main video output debug: removing module "x11"
[00000377] main video output debug: thread 2766142352 joined (video_output/video_output.c:461)
argn=onmediacomplete, argv=LinuxMediaComplete();
argn=onmediacompletewitherror, argv=LinuxMediaComplete();
argn=type, argv=application/x-mplayer2
argn=pluginspage, argv=http://www.microsoft.com/Windows/MediaPlayer/
argn=id, argv=MediaPlayer
argn=src, argv=http://dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525
argn=,, argv=
argn=width, argv=400
argn=height, argv=60
[00000417] main private debug: translation test: code is "C"
[00000417] main private debug: module bank initialized, found 218 modules
[00000417] main private debug: opening config file /home/dan/.vlc/vlcrc
[00000417] main private debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000417] main private debug: looking for memcpy module: 1 candidate
[00000417] main private debug: using memcpy module "memcpy"
[00000419] main playlist debug: waiting for thread completion
[00000419] main playlist debug: thread 2766142352 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000420] main private debug: waiting for thread completion
[00000420] main private debug: thread 2790259600 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000421] main interface debug: looking for interface module: 1 candidate
[00000421] main interface debug: using interface module "hotkeys"
[00000421] main interface debug: thread 2755103632 (interface) created at priority 0 (interface/interface.c:231)
[00000422] main interface debug: looking for interface module: 1 candidate
[00000422] main interface debug: using interface module "screensaver"
[00000422] main interface debug: thread 2812525456 (interface) created at priority 0 (interface/interface.c:231)
[00000419] main playlist debug: adding playlist item `http://dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525' ( http://dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525 )
[00000001] main private debug: removing all interfaces
[00000419] main playlist debug: creating new input thread
[00000423] main input debug: waiting for thread completion
[00000423] main input debug: `http://dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525' gives access `http' demux `' path `dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525'
[00000423] main input debug: creating demux: access='http' demux='' path='dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525'
[00000424] main demuxer debug: looking for access_demux module: 0 candidates
[00000424] main demuxer warning: no access_demux module matched "http"
[00000423] main input debug: creating access 'http' path='dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525'
[00000425] main access debug: looking for access2 module: 7 candidates
[00000425] access_http access debug: http: server='dc101.com' port=80 file='/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525
[00000425] main access debug: net: connecting to dc101.com port 80
[00000423] main input debug: thread 2804132752 (input) created at priority 0 (input/input.c:265)
[00000287] main interface debug: thread 2831141776 joined (interface/interface.c:258)
[00000287] main interface debug: removing module "screensaver"
[00000285] main interface debug: thread 2839534480 joined (interface/interface.c:258)
[00000285] main interface debug: removing module "hotkeys"
[00000001] main private debug: removing playlist handler
[00000284] main private debug: thread 2847927184 joined (playlist/playlist.c:247)
[00000416] access_mms access warning: cannot fill buffer
[00000425] main access debug: connection in progress
[00000416] access_mms access warning: cannot fill buffer
[00000416] access_mms access warning: cannot fill buffer
[00000416] access_mms access warning: cannot fill buffer
[00000416] access_mms access warning: cannot fill buffer
[00000416] access_mms access warning: cannot fill buffer
[00000425] access_http access debug: protocol 'HTTP' answer code 200
[00000425] access_http access debug: Server: Apache/1.3.41 (Unix) PHP/4.4.9
[00000425] access_http access debug: Transfer-Encoding: chunked
[00000425] access_http access debug: Content-Type: video/x-ms-wma
[00000425] main access debug: using access2 module "access_http"
[00000416] access_mms access warning: cannot fill buffer
[00000426] main private debug: pre-buffering...
[00000426] main private debug: received first data for our buffer
[00000423] main input debug: creating demux: access='http' demux='' path='dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525'
[00000427] main demuxer debug: looking for demux2 module: 45 candidates
[00000427] ts demuxer warning: TS module discarded (lost sync)
[00000427] m3u demuxer debug: playlist type: 2 - 2
[00000427] main demuxer debug: using demux2 module "m3u"
[00000423] main input debug: `http://dc101.com/cc-common/ondemand/Services/genasx.php?ua=9d6a6b9a311f74f6894da452d2526673&id=2525' successfully opened
[00000419] m3u playlist debug: starting playlist playback
[00000419] main playlist debug: adding playlist item `mms://a664.l2013111095.c20131.g.lm.akamaistream.net/D/664/20131/v0001/reflector:11095?auth=caEbeaIb6duaTbraObdbhb5cycLbyahdLcL-bjUVcn-4q-PL1W8_1nqEHnm2FBukCtAr&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM' ( mms://a664.l2013111095.c20131.g.lm.akamaistream.net/D/664/20131/v0001/reflector:11095?auth=caEbeaIb6duaTbraObdbhb5cycLbyahdLcL-bjUVcn-4q-PL1W8_1nqEHnm2FBukCtAr&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM )
[00000419] main playlist debug: adding playlist item `mms://a825.l2013111096.c20131.g.lm.akamaistream.net/D/825/20131/v0001/reflector:11096?auth=caEbUaZcqaWbPaEaKdRc2awc6bDaUdjdnaX-bjUVcn-4q-RLYX6_9omDAns4FCrjxtEq&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM' ( mms://a825.l2013111096.c20131.g.lm.akamaistream.net/D/825/20131/v0001/reflector:11096?auth=caEbUaZcqaWbPaEaKdRc2awc6bDaUdjdnaX-bjUVcn-4q-RLYX6_9omDAns4FCrjxtEq&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM )
[00000423] main input debug: EOF reached
[00000416] access_mms access warning: cannot fill buffer
[00000416] access_mms access warning: cannot fill buffer
[00000423] main input debug: closing input
[00000427] main demuxer debug: removing module "m3u"
[00000425] main access debug: removing module "access_http"
[00000423] main input debug: thread 2804132752 joined (input/input.c:412)
[00000416] access_mms access warning: cannot fill buffer
[00000416] access_mms access warning: failed to receive command (aborting)
[00000416] access_mms access debug: Connection closed
[00000416] access_mms access debug: waiting for connection...
[00000416] main access debug: net: connecting to 207.138.82.106 port 80
[00000416] main access debug: connection in progress
[00000416] main access debug: connection aborted
[00000416] access_mms access error: failed to open a connection (tcp)
[00000416] access_mms access error: cannot connect to server
[00000416] main access debug: net: connecting to 207.138.82.106 port 80
[00000416] main access debug: connection in progress
[00000416] main access debug: connection aborted
[00000416] access_mms access error: cannot connect to 207.138.82.106:80
[00000416] vcdx access warning: Can't get file status for 207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf:
No such file or directory
[00000416] vcdx access warning: could not retrieve file info for `207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf': No such file or directory
[00000416] vcdx access warning: can't open nrg image file 207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf for reading
[00000416] access_file access warning: 207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf: No such file or directory
[00000416] cdda access warning: could not open 207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf
[00000416] main access warning: no access2 module matching "mms" could be loaded
[00000414] main input error: no suitable access module for `mms://207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf'
[00000419] main playlist debug: creating new input thread
[00000434] main input debug: waiting for thread completion
[00000434] main input debug: `mms://a664.l2013111095.c20131.g.lm.akamaistream.net/D/664/20131/v0001/reflector:11095?auth=caEbeaIb6duaTbraObdbhb5cycLbyahdLcL-bjUVcn-4q-PL1W8_1nqEHnm2FBukCtAr&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM' gives access `mms' demux `' path `a664.l2013111095.c20131.g.lm.akamaistream.net/D/664/20131/v0001/reflector:11095?auth=caEbeaIb6duaTbraObdbhb5cycLbyahdLcL-bjUVcn-4q-PL1W8_1nqEHnm2FBukCtAr&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM'
[00000434] main input debug: creating demux: access='mms' demux='' path='a664.l2013111095.c20131.g.lm.akamaistream.net/D/664/20131/v0001/reflector:11095?auth=caEbeaIb6duaTbraObdbhb5cycLbyahdLcL-bjUVcn-4q-PL1W8_1nqEHnm2FBukCtAr&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM'
[00000435] main demuxer debug: looking for access_demux module: 0 candidates
[00000435] main demuxer warning: no access_demux module matched "mms"
[00000434] main input debug: creating access 'mms' path='a664.l2013111095.c20131.g.lm.akamaistream.net/D/664/20131/v0001/reflector:11095?auth=caEbeaIb6duaTbraObdbhb5cycLbyahdLcL-bjUVcn-4q-PL1W8_1nqEHnm2FBukCtAr&aifp=1234&CPROG=SIMULCAST&MARKET=WASHINGTON-DC&MNM=2&NG_FORMAT=aor&NG_ID=wwdc101fm&OR_NEWSFORMAT=&REQUESTOR=WWDC-FM&SERVER_NAME=wwwdc101com&SITE_ID=2079&STATION_ID=WWDC-FM'
[00000436] main access debug: looking for access2 module: 6 candidates
[00000436] access_mms access debug: waiting for connection...
[00000436] main access debug: net: connecting to a664.l2013111095.c20131.g.lm.akamaistream.net port 1755
[00000434] main input debug: thread 2804132752 (input) created at priority 0 (input/input.c:265)
[00000414] main input debug: thread 2822749072 joined (input/input.c:412)
[00000283] main playlist debug: thread 2856319888 joined (playlist/playlist.c:248)
[00000283] main playlist debug: deleting playlist item `mms://a1802.v289256.c28925.g.vm.akamaistream.net/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf'
[00000283] main playlist: stopping playback
[00000283] main playlist debug: deleting playlist item `mms://207.138.82.106:80/7/1802/28925/v0001/cchannel.download.akamai.com/28925/1687/richmedia/Gateway-HiBallEventsDC101.wmv?MSWMExt=.asf'
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: removing module "memcpy"
Segmentation fault

```

I copied as much as I could but it didn't trace back all the way to the beginning.  The terminal window only holds so much

---

### Post by andrew.46 on 2009-03-13
Hi,

I would like to help but:

> 
Licensed Content Access Request

Your IP Address: 61.68.17.116

Due to licensing restrictions, we are not able to allow access to the content you are requesting from outside the United States. We are sorry we can no longer provide access to Canada. If you currently reside in the United States, please select one of the options below to process your request. Please allow up to 60 hours to process your request.



Must be very valuable information :-).

Andrew

---

### Post by cartisdm on 2009-03-13
> **andrew.46 said:**
> Hi,

I would like to help but:



Must be very valuable information :-).

Andrew

Haha, it's just an alternative rock station.  Anybody else able to help?

---

### Post by cartisdm on 2009-03-15
bump?

---

### Post by ALIENDUDE5300 on 2009-03-15
Seems to work fine for me. Could it be a particular add-on you have installed?

---

### Post by kansasnoob on 2009-03-15
So, it appears you're using 8.04. What version of Firefox?

What version of flash?

It works fine for me and I'm running Firefox 3.07 w/Flash 10.0 r22 and only the Flashblock 1.5.8 extension.

Maybe go to Synaptic and search for "flash", then be sure you have no "gnash" or "swfdec" installed??????

---

