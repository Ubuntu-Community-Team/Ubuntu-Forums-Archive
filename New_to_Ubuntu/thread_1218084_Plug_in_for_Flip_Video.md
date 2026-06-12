---
title: "Plug in for Flip Video"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by sanderella on 2009-07-20
When I try to run my Flip video with Movie Player, I a message that Ubuntu can't find the right plug in. It is called

[I]application/x-ms-dos-executable decoder 
[/I]
Does anyone know if it could be/become available for us Ubuntu users? Thanks.

---

### Post by 3rdalbum on 2009-07-20
Are you sure you've opened a *video* with Totem? That MIME type you've posted basically means "Microsoft Windows program". From what I've read, some Flip Video units just save video in MPEG-4 format, and some save into 3ivx format. Both are playable with ffmpeg-based players like Mplayer and with Totem if you have the "gstreamer-ffmpeg" package installed. Totem should play MPEG-4 anyway regardless of installed ffmpeg support.

You will probably also need the "unstripped" versions of the "libav*" packages - just do a search in Synaptic for "libav", and install the packages with "-unstripped" at the end of the name.

---

### Post by sanderella on 2009-07-20
Thank you, will look into this.:)

---

### Post by sanderella on 2009-07-20
:( I did that, but it has made no difference. 

I found a previous post with this problem, and he marked it SOLVED, so I have sent him a message to find out how he did it. Thanks for your help.

---

### Post by sanderella on 2009-08-02
I plugged it in and it just worked without any help from me. :confused:

---

### Post by freeediver on 2009-11-03
I have a couple threads going on this issue but have not received any advise, I can't download and view flip videos sent thru the Flip video service. Flip support will not help they only offer support for Mac and Windows.

---

