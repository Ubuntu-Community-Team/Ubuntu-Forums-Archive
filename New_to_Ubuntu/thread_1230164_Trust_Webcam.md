---
title: "Trust Webcam"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by harfin on 2009-08-03
I have in the last few days been moving my PC (Dell Dimension E520) to use Ubunto in lieu of Windows XP Pro.

I guess you already know this, but Ubuntu is **great**. 

However I'd be grateful for any suggestions others may have to solve the following problem 

When I try to activate the text picture in Skype all I get is a multi coloured gibberish pattern.

My webcam is a Trust WB-1400T

The camera works fine in Ekiga and in Cheese Webcam Booth. 

The image is distorted in Camorama.

Any suggestions please?

Alan

---

### Post by DexterLB on 2009-08-03
Skype uses v4l1, and Ubuntu Intrepid, Jaunty and Karmic use v4l2. So, instead of running skype with this command:
```
skype
```

Run it wit this command: ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

I hope this helps :)

---

### Post by shantiq on 2009-08-03
> **harfin said:**
> I have in the last few days been moving my PC (Dell Dimension E520) to use Ubunto in lieu of Windows XP Pro.

I guess you already know this, but Ubuntu is **great**. 

However I'd be grateful for any suggestions others may have to solve the following problem 

When I try to activate the text picture in Skype all I get is a multi coloured gibberish pattern.

My webcam is a Trust WB-1400T

The camera works fine in Ekiga and in Cheese Webcam Booth. 

The image is distorted in Camorama.

Any suggestions please?

Alan

[B][COLOR=Blue]

yes alan went through the same thing 3weeks ago the same process

ekiga ok skype no good

turns outs trust webcams are not UVC and therefore not picked up by 9.04

in the end after 2 weeks of research i found out the best fit are logitech UVC cams

a complete list is there

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

and from   [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)



[/COLOR][/B]Many webcams will "just work" in Ubuntu. There is a USB standard that defines USB streaming video called UVC. This stands for Universal Video Class, and it does for webcams what UMS does for USB memory sticks and hard drives. This allows one driver to work with many webcams. When looking to purchase a webcam for use with Ubuntu, you should look for a UVC compatible camera. The [Linux-UVC]("http://linux-uvc.berlios.de/") project has a good list of UVC compatible webcams as well as [The Quickcam Team]("http://www.quickcamteam.net/devices") for Logitech cameras. 
[B][COLOR=Blue] 


i got logitech E 3500 and it got picked up in a millisecond


hopes this helps


i changed from xp to 9.04 and i thought that having to buy a new cam was a small price to pay



shan[/COLOR][/B]

---

### Post by harfin on 2009-08-03
> **DexterLB said:**
> Skype uses v4l1, and Ubuntu Intrepid, Jaunty and Karmic use v4l2. So, instead of running skype with this command:
```
skype
```Run it wit this command: ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```I hope this helps :)

Thank you for that very quick reply - however, I did as you suggested and got the error message 

[INDENT]Details: Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)

[/INDENT]Hmm.

Alan
:confused:

---

### Post by DexterLB on 2009-08-03
Before doing that, try installing libv4l
```
sudo aptitude install libv4l
```
and then try running skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by harfin on 2009-08-03
> **shantiq said:**
>  **[COLOR=Blue]turns outs trust webcams are not UVC and therefore not picked up by 9.04[/COLOR]**

Thanks for the reply. 

I had already looked at another list of webcams in the forum (can't remember where of the top of my head) and my camera (WB-1400T) was listed as working fine with Skype.

:confused:

Alan

> **DexterLB said:**
> Before doing that, try installing libv4l
```
sudo aptitude install libv4l
```and then try running skype with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Did as you suggested and this time I got:
[INDENT]Details: Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)
[/INDENT]
:confused:
Alan

> **harfin said:**
> Did as you suggested and this time I got:[INDENT]Details: Failed to execute child process "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so" (No such file or directory)
[/INDENT]:confused:
Alan

Any further suggestions anyone?

Alan

---

### Post by frasten on 2009-09-01
> **harfin said:**
> Any further suggestions anyone?

Alan

As you can see with:
```
dpkg -S /usr/lib/libv4l/v4l1compat.so
```

that file is included in the package libv4l-0.

So run this command:
```
sudo apt-get install libv4l-0
```

and you should fix your issue.

---

### Post by absurdus_delirium on 2009-09-08
Well, hello all! First post in the Ubuntu community! :P
Thanks for the help, ppl! I followed Dexter's suggestion and they worked for a  VIMICRO USB2.0 PC Camera (VC0323) with me but:
1) As soon as I close Terminal, I lose the application as well, but I think that's quite normal (yea, absolute Linux n00b here):P)
2) I get the following ```
libv4lconvert: Error decompressing JPEG: error: more then 63 AC components (70) in huffman unit
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes)
```Cheers!

---

### Post by DexterLB on 2009-09-09
> **absurdus_delirium said:**
> As soon as I close Terminal, I lose the application as well, but I think that's quite normal
When you close the terminal, the command which it's executing (e.g. bash or sh, depending on your settings) is ended the "hard" way. It's preferred that you don't close terminals, and type 'exit' instead. Closing the terminal won't do any harm, but if you want to be a geek, start typing exit :D. Anyway, when sh or bash is terminated, it terminates a command that's running inside. So, if you want to run command foo in the background append & at the end:
```
 foo & 
```
Instead of
```
 foo 
```

> **absurdus_delirium said:**
> I get the following ```
libv4lconvert: Error decompressing JPEG: error: more then 63 AC components (70) in huffman unit
X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes)
```
There's something about this console error in [ this bug. ](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/320353) Do you get black screen or some distorted picture?

---

