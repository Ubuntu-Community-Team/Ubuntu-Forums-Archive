---
title: "Webcam Works in Skype and Ekiga, but not Cheese or Camorama"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Paul133 on 2009-01-02
I needed to get a new webcam and I wanted to make sure I found one that would work with Ubuntu. The logitech quickcam deluxe for notebooks seemed like a great choice. I used easycam2 to get the gspca driver installed and it works with Ekiga and Skype, but I can't get it to work with Camorama or Cheese. I suspect it's a result of the whole problem with the gspca kernel module and v4l/v4l2, but I'm not sure how to solve it. Any advice?

---

### Post by nhasian on 2009-01-02
launch cheese from a terminal with the command

```
cheese
```

if you receive an error like this:
```

(cheese:31132): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:31132): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:31132): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small
```

then you can fix cheese with the instructions from this page:

[http://bugzilla.gnome.org/show_bug.cgi?id=545033](http://bugzilla.gnome.org/show_bug.cgi?id=545033)

---

