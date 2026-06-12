---
title: "Songbird 1.9.3 install Problem in Ubuntu 10.10"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by jonerich on 2011-03-02
Cant install Songbird 1.9.3 via this method:


[LEFT]wget [http://download.songbirdnest.com/installer/linux/i686/Songbird_1.9.3-1959_linux-i686.tar.gz](http://download.songbirdnest.com/installer/linux/i686/Songbird_1.9.3-1959_linux-i686.tar.gz)
 tar zxvf Songbird_1.9.3-1959_linux-i686.tar.gz
cd Songbird
rm /lib/libgst*.so 
./songbird


I get this in terminal:

[/LEFT]
(songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libfsrtpconference.so': /usr/lib/gstreamer-0.10/libfsrtpconference.so: undefined symbol: gst_pad_get_caps_reffed

 (songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_video_event_parse_still_frame
 ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml

 (songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstffmpeg.so': /usr/lib/gstreamer-0.10/libgstffmpeg.so: undefined symbol: gst_caps_set_value

 (songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsttaglib.so': /usr/lib/gstreamer-0.10/libgsttaglib.so: undefined symbol: gst_tag_list_peek_string_index

 (songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdvdspu.so': /usr/lib/gstreamer-0.10/libgstdvdspu.so: undefined symbol: gst_video_event_parse_still_frame

 (songbird-bin:3828): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstjpegformat.so': /usr/lib/gstreamer-0.10/libgstjpegformat.so: undefined symbol: gst_byte_writer_put_uint8
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
 ././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_xml_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
:P
Any Help is much appreciated

---

### Post by TransitMan on 2011-03-02
Try getting it from Getdeb at this link - [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by jonerich on 2011-03-04
> **TransitMan said:**
> Try getting it from Getdeb at this link - [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)


Thanks for the reply but i have Tried that its an old version 1.8.0. it installs but is so slow and buggy and lock up frequently :( I wanted to install 1.9.3 has alot of inprovements here is the article:

[http://www.omgubuntu.co.uk/2011/02/songbird-hits-version-1-9-3-linux-build-available/](http://www.omgubuntu.co.uk/2011/02/songbird-hits-version-1-9-3-linux-build-available/)

---

### Post by bdombro on 2011-03-24
Are you by chance running x64 ubuntu?

I carelessly tried running the same binary as you on my x64 ubuntu and had the same problem.  So in case anybody needed confirming, x32 binaries STILL don't run on x64 :P

---

