---
title: "Can't save for web in GIMP"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by kapi on 2010-04-19
have just realised that when I'm saving images in GIMP as jpg and even at 72 pixels pi the file sizes are massive compared to photoshop.

I mean from a file that's maybe 124kb in PS to 504ks in GIMP 

any ideas?

---

### Post by mcduck on 2010-04-19
> **kapi said:**
> have just realised that when I'm saving images in GIMP as jpg and even at 72 pixels pi the file sizes are massive compared to photoshop.

I mean from a file that's maybe 124kb in PS to 504ks in GIMP 

any ideas?

Are you sure you are using the same quality setting in both Photoshop and Gimp? And have you looked at the "Advanced Options" in Gimp's save dialog? Since youa re saving for web you'd want to disable saving thumbnail, comments, EXIF data etc...

Also note that changing the DPI setting in Gimp doesn't change the image's resolution, it only changes the default DPI value saved in the image (meaning that the resolution stays the same, but the size it would be if you printed it changes). Thus, changing the DPI doesn't effect file size. So make sure that both your images have the same resolution as well...

---

### Post by kapi on 2010-04-19
Thanks will try that now

Kapi

---

### Post by Crazedpsyc on 2010-04-19
Can you save it as a PNG? gimp can compress PNGs, just save it as [filename].png and it will give you the option to save with up to 9 levels of compression, without lowering the quality.

---

### Post by kapi on 2010-04-19
Ok so I did a quick test in GIMP and PS

an image of 800 x 533 at 72ppi

I used a 60 % quality setting in both and it's shocking.

Original file size = 634k

after saving

ps = 35k

GIMP = 563k

---

### Post by kapi on 2010-04-19
Also tried the png

No good am really disappointed with GIMP am and have been a huge fan for years

---

### Post by mcduck on 2010-04-19
> **kapi said:**
> Ok so I did a quick test in GIMP and PS

an image of 800 x 533 at 72ppi

I used a 60 % quality setting in both and it's shocking.

Original file size = 634k

after saving

ps = 35k

GIMP = 563k

Like I said, the DPI/PPI value has nothing to do with file size.

What are the other options you are using when saving the file? 

I just tried, using the same photo on both Photoshop and Gimp, I resized it to 640x400, and saved as JPG, with 60% quality, optimized, and progressive disabled (also all the other advanced options in Gimp disabled). The result: file size from Photoshop is 70KiB, and from Gimp 36,1KiB..

---

### Post by VernonA on 2010-04-19
I assume you used the same original image in both applications. An image that's 800x533 using 24-bit colour would be 1.28Mb in size. If you compress this by 60%, the result would be about 600Kb, which is in-line with the image Gimp produced. I'm sure you know JPEG is a lossy format, so it is up to you how much "loss" you can tolerate. Gimp asks you to express it as a percentage, which makes some sense. However, there are other ways of looking at it. A smarter method might say "on the scale of perfect-image to total-crap, how far down do you want to go?" to which you might answer 60%. As JPEG compression is very good, you might well be able to shrink an image to 35Kb and think its halfway down the crappiness scale! What I'm suggesting is that Photoshop and Gimp have different interpretations of what "60% compression" mean. The real test is to shrink the images until they **are** the same size, using trial-and-error if necessary, and see if you can tell them apart. I doubt if Gimp is anywhere near as bad as you are thinking.

---

### Post by kapi on 2010-04-19
OK I apologise, I'll go and sit in the corner with a numpty hat on LOL.

I tried a new image an it reduced from 2.3 mb to 413k, so great.

what I'm working on is the photos from work and they didn't seem to respond.

So for future reference when I go in to the image setting and 'scale image' and then set the ppi to 72 then thats primarily for print or have I got that wrong? I was always informed that the dpi/ ppi etc should be 72 for the web.

Thanks for your help, it's really appreciated

---

### Post by mcduck on 2010-04-19
> **VernonA said:**
> I assume you used the same original image in both applications. An image that's 800x533 using 24-bit colour would be 1.28Mb in size. If you compress this by 60%, the result would be about 600Kb, which is in-line with the image Gimp produced. I'm sure you know JPEG is a lossy format, so it is up to you how much "loss" you can tolerate. Gimp asks you to express it as a percentage, which makes some sense. However, there are other ways of looking at it. A smarter method might say "on the scale of perfect-image to total-crap, how far down do you want to go?" to which you might answer 60%. As JPEG compression is very good, you might well be able to shrink an image to 35Kb and think its halfway down the crappiness scale! What I'm suggesting is that Photoshop and Gimp have different interpretations of what "60% compression" mean. The real test is to shrink the images until they **are** the same size, using trial-and-error if necessary, and see if you can tell them apart. I doubt if Gimp is anywhere near as bad as you are thinking.

Like I said, I used the same original file.

You can't calculate the resulting file size from JPG conversion that way. That depends on the actual contents of the image, so 60% (or "6" in many programs) quality doesn't mean 60% file size.

Both programs use the same scale for image quality, that's really pretty much a standard, even though if the programs represent it as scale from 0 to 10 or 0% to 100% may differ. It's still the same scale.

I'd say that the original poster's difference in file size comes from all the other settings (saving thumbnail, possible EXIF data, progressive versus linear and so on).

..and also smaller differences in resulting file size can be a result from simply checking the file size using a different operating system/file manager, as some tell you file sizes in Kib, others in KB, and many in KiB even though they say KB... ;)

---

### Post by Paddy Landau on 2010-04-19
> **kapi said:**
> So for future reference when I go in to the image setting and 'scale image' and then set the ppi to 72 then thats primarily for print or have I got that wrong? I was always informed that the dpi/ ppi etc should be 72 for the web.
Generally, web pictures have lower quality in order to let people with slower connections load the page in a reasonable time. 72dpi is usually a good compromise.

For printing, that depends on your printer. Modern retail printers usually can cope with 600dpi or more. I find 300dpi fine for day-to-day printing.

---

### Post by kapi on 2010-04-19
Thanks again

I think for the ones for work I'll use PS because Gimp doesn't reduce them
but thanks for all your help

take care

---

### Post by mcduck on 2010-04-19
> **kapi said:**
> OK I apologise, I'll go and sit in the corner with a numpty hat on LOL.

I tried a new image an it reduced from 2.3 mb to 413k, so great.

what I'm working on is the photos from work and they didn't seem to respond.

So for future reference when I go in to the image setting and 'scale image' and then set the ppi to 72 then thats primarily for print or have I got that wrong? I was always informed that the dpi/ ppi etc should be 72 for the web.

Thanks for your help, it's really appreciated

What matters in web use is the actual resolution of the image. DPI/PPI is only for print purposes, although better PDF viewers will also try to use the size when you view an image with them (assuming you have set your monitor's DPI value correctly).

If you view an image in browser, it's size comes purely from it's resolution, so 640x400 image will be 640x400, no matter if you have set the DPI value to 72 or 300. The recommended 74DPI is just a shorthand for figuring out what resolution you might want to use for web, and comes from Photoshops way of changing the actual resolution if you change the DPI value. Photoshop assumes you want the images dimensions (in inches/centimeters) to stay the same, while Gimp assumes you want the image's resolution to stay the same.

---

### Post by utnubuuser on 2010-04-19
There's an online service as well called [http://punypng.com]("http://punypng.com") that'll reduce filesize without reducing image quality.

---

### Post by mcduck on 2010-04-19
> **kapi said:**
> Thanks again

I think for the ones for work I'll use PS because Gimp doesn't reduce them
but thanks for all your help

take care

Gimp reduces them, I'm quite sure I've made that pretty clear, with examples, the exact options, and even explanation in the difference between Gimp and Photoshop. You just have to tell it the resolution you want instead of telling it the DPI you want.

Actually Gimp's way of doing this makes lot more sense when it comes to web/display graphic, since the DPI is meaningless for those purposes and resolution is what defines the image's size.

---

### Post by mcduck on 2010-04-19
> **Paddy Landau said:**
> Generally, web pictures have lower quality in order to let people with slower connections load the page in a reasonable time. 72dpi is usually a good compromise.

For printing, that depends on your printer. Modern retail printers usually can cope with 600dpi or more. I find 300dpi fine for day-to-day printing.

Be carefull with the DPI, though, as it doesn't tell you the actual size of the image and it's usefullness on display graphics is rather questionable anyway, as most people don't have their displays DPI value configured correctly anyway.

The reason you might want to use the DPI is if you wanted the image to show at certain size on the screen (measured in centimeters/inches). But most programs (and all web browsers) just ignore the DPI value and simply display image using it's resolution. So a 640x480 resolution image is mapped to 640x480 pixels on your screen, no matter what the image's DPI is.

In other words if you wanted a CD cover image to display on your screen in it's natural size (120mmx120mm) you'd set the DPI value to same as your display's DPI value is, and the image's size to 120mmx120mm. The resolution would ten be calculated based on these. The problem is that even if the program used to view the image uses DPI value, most people actually have their displays set to 96DPI, and for most displays's even that wouldn't be correct, so the image wouldn't display as 120mm x 120mm anyway.

Of course you *can* use the DPI value when you resize the image, but keep in mind that it's the resolution that actually defines the size on your display and the file size, not the DPI.

For print work the DPI is actually important, as printer's and printing machines respect the DPI value and use it correctly.

---

### Post by Paddy Landau on 2010-04-19
> **mcduck said:**
> ... You just have to tell it the resolution you want instead of telling it the DPI you want.

Actually Gimp's way of doing this makes lot more sense...

Be careful with the DPI...
Yes, you're quite right. When I resize in GIMP, I first set my desired dpi (because the magazine that I edit requires a minimum dpi), then I set the required size in inches.

@kapi: This may be your answer. For example, if I have a picture that I need to reduce to 1 inch high, and I only need resolution 72dpi, then I first set the resolution then the image size (see the attachment).

---

### Post by kapi on 2010-04-20
Cant thank everyone enough for all their comments and help.

You are all correct GIMP does do a fantastic job. For some reason though it fails to reduce the file size in the images that I have received from work. They are JPEG 700x500px and 451k.

when I installed the plugin 'save for web' even that doesn't reduce the file size just the quality. yet when I'm reducing another jpeg from outside the work they work splendidly. Go figure!

Doesn't matter I now know that GIMP is fine and it must be something else

Thanks again and hope you all have a great day

---

### Post by Linuxforall on 2010-04-20
sudo apt-get install gimp-plugin-registry and you will have save for web feature which is very handy.

---

### Post by kapi on 2010-04-20
Yeah did that last night seems quite good.

in fact I entered 

sudo apt-get install gimp-plugin-registry

does this install all the plugins on or just some?

---

