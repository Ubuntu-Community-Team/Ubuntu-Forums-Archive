---
title: "why is my mp3 player mounting in gphoto2://[usb:002,003]/ ?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-09-02
Hello, in the past, when i plugged in my mp3 player (sansa clip) into my ubuntu computer. I could see it on /media/ alongside my ipod. but now it seems to be located in a weird location: 

gphoto2://[usb:002,003]/

Please advise.

how can i fix the location?

---

### Post by Schendje on 2009-09-02
This also happens with my Creative Zen V Plus. Instead of being a simple usb drive, it gets all tricky.

Does anyone know why this is?

It's also annoying because it won't read or do anything to files that have a large path or filename. This is really annoying, because I can't modify the folders or read their contents.

(Btw, I think you can select different modes on the Sansa Clip, it's somewhere in it's system options, you could try that.)

---

### Post by hanzj on 2009-09-02
You're right. I see MTP and MSC. Last time it was plugged in, the label had MTP. What are they? What's the difference and which should I pick?

---

### Post by perce on 2009-09-02
[MTP]("http://http://en.wikipedia.org/wiki/Media_Transfer_Protocol")

[MSC]("http://en.wikipedia.org/wiki/USB_mass_storage_device_class")

---

### Post by hanzj on 2009-09-02
Your MTP link seems to be faulty.
Here's the link: [http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)

---

### Post by Znupi on 2009-09-02
I have a Philips SA6025 which uses MTP and it works flawlessly with Rhythmbox. It isn't mounted anywhere, from what I can figure. If MTP doesn't work for you (Sansa might use some proprietary MTP extensions), try MSC, that should work without any problems.

---

### Post by hanzj on 2009-09-02
znupi,
thanks. i switched the sansa clip's usb mode from Auto-Detect (which put it to MTP) to MSC. Now, i see that it's location on the ubuntu computer is
Location: /media/disk
The gphoto part got out.

I observed that Sansa Clip added some files onto the disk:

[LIST]
[*]DID.bin
[*]MTABLE.SYS
[*]RES_INFO.SYS
[*]SYS_CONF.SYS
[*]version.sdk
[/LIST]
Do I need those? Should I keep them? Or can one delete them safely?


Another question: Is there any advantage to switching back to MTP/Auto-Detect?

thanks.

---

### Post by Znupi on 2009-09-02
Generally, you should keep those files. Still, I don't think deleting them would make the device unusable. Also, if they are not that big, do they really bother you?

The only reason why MTP would be advantageous would be if you were to use a special music managing application that only supported it. Fortunately, Rhythmbox has support for mass storage device music players and will let you manage it even in MSC mode.

---

### Post by Schendje on 2009-09-02
> **hanzj said:**
> 
I observed that Sansa Clip added some files onto the disk:

[LIST]
[*]DID.bin
[*]MTABLE.SYS
[*]RES_INFO.SYS
[*]SYS_CONF.SYS
[*]version.sdk
[/LIST]
Do I need those? Should I keep them? Or can one delete them safely?

I'm not sure (my Sansa Clip hasn't been delivered yet) but I'm guessing they're just regular old system files containing settings and whatnot. I'd leave them in.

> **hanzj said:**
> 
Another question: Is there any advantage to switching back to MTP/Auto-Detect?

According to this: [http://www.zolved.com/synapse/view_content/6125/Understanding_the_two_USB_modes_--_MSC_and_MTP_--_on_Sandisk](http://www.zolved.com/synapse/view_content/6125/Understanding_the_two_USB_modes_--_MSC_and_MTP_--_on_Sandisk)

> MTP mode is for MP3 files and WMA files with DRM (digital rights management). These WMA music files with DRM including purchased downloads and (maybe) subscription music tracks require MTP to transfer and update the DRM licenses. MTP mode is required for use with subscription music services such as Yahoo Music Unlimited To Go, Rhapsody To Go, and Napster To Go.

So no, unless you're using those kinds of files.

Edit: oh, Znupi beat me. I didn't realize the posts were so young still. :)

---

### Post by hanzj on 2009-09-02
The 5 files add up to 677.7 kb. They mess up the "home" folder of the Sansa Clip. I guess I could ignoe, or make them hidden.

---

### Post by Znupi on 2009-09-02
You can't make them hidden ;)

---

### Post by hanzj on 2009-09-02
you're right. I thought I could.

---

