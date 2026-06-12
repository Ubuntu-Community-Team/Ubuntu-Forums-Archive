---
title: "How to rotate photos?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by redmistpete on 2010-08-10
Hi,

whenever I view photos on Ubuntu (Lucid), they are always oriented correctly. However, when I upload them to any web-page any portrait photos are rotated on their side. There seems to be no easy way to correct this; if I first click rotate in ubuntu, it rotates the image so that it is on its side but when it's uploaded to a web-page it is still on its side :(

The only solution I have found is to load the image into GIMP, rotate it and then save it but this uses lossy compression for JPG's and is a hassle to have to do this for the hundreds++ of photos I've taken. Is there an easier way - on windows, all the portrait images are side-on to start with and once I've clicked the rotate button, they're good to go (but again this compresses the image).

Also any JPEG/JPG files are ignored by EVERY photo website I've tried because the file extension is upper-case. They all say this is a fault with Ubuntu and that I should rename all the file-extensions for my images. No chance, even with a batch converter it is way too much hassle to convert every image name so, as it stands, I can't upload to anywhere but facebook (only 5 images at a time!) and even then half of them are the wrong orientation. Please help - it's doing my tiny head in now.

Thanks.

---

### Post by SoFl W on 2010-08-10
Just a question because of a problem I had with some files I imported from another computer on the network. Are you sure the permissions are correct on the files you are rotating?  When I was using image viewer (aka eog, Eye of Gnome) I would rotate the photo, save it but it wouldn't change the rotation.  It did not give an error saying it couldn't save the file, it acted like it did.   Check file permissions.


(Red Mist... watched *Kick **** last night)

---

### Post by Joe of loath on 2010-08-10
Just to clarify, in EoG you're rotating it, pressing ctrl-s, and closing, right?

---

### Post by SoFl W on 2010-08-10
Actually using the File-> Save menu but yes.

---

### Post by AlphaLexman on 2010-08-10
Many modern digital cameras 'know' if you take a picture in landscape or portrait mode.

That data is saved to the exif data within the jpeg. Most photo manipulation software can read the orientation data and correctly rotate the image on your screen.

Uploading an image to the internet may not always make this adjustment. That is why re-saving the file resets the orientation.

---

### Post by jcolyn on 2010-08-10
> **redmistpete said:**
> 
There seems to be no easy way to correct this; if I first click rotate in ubuntu, it rotates the image so that it is on its side but when it's uploaded to a web-page it is still on its side :( 

Where in Ubuntu can you do this?? Ubuntu is not an image editing program. This is done in Gimp or other image viewing/editing program

> **redmistpete said:**
> The only solution I have found is to load the image into GIMP, rotate it and then save it but this uses lossy compression for JPG's and is a hassle to have to do this for the hundreds++ of photos I've taken. Is there an easier way - on windows, all the portrait images are side-on to start with and once I've clicked the rotate button, they're good to go (but again this compresses the image).

You can choose how much/little compression at save..

> **redmistpete said:**
> Also any JPEG/JPG files are ignored by EVERY photo website I've tried because the file extension is upper-case. 

If you are importing photos from a digital camera the default is upper case which can be changed in camera.

> **redmistpete said:**
> They all say this is a fault with Ubuntu and that I should rename all the file-extensions for my images. No chance, even with a batch converter it is way too much hassle to convert every image name so, as it stands, I can't upload to anywhere but facebook (only 5 images at a time!) and even then half of them are the wrong orientation. Please help - it's doing my tiny head in now.

Thanks.

Ubuntu is not at fault. The blame is cast due to ignorance on their part.. Anything I save in Ubuntu whether it be an image file or document is saved lower case..

At the time the image is captured in camera meta data is written to the file giving the original orientation of the file. Most image viewers and editing software will turn it but many websites lack the ability to do this so they read meta data and show it according to the data.

Also some imaging import software will automatically orient it properly....

Since you don't like jpg's what extension are you posting them as???

---

### Post by Zimmer on 2010-08-10
[http://www.lonelyplanet.com/thorntree/thread.jspa?messageID=16863558](http://www.lonelyplanet.com/thorntree/thread.jspa?messageID=16863558)

Not all camera Manufacturers implement the EXIF standard the same... (it is not so 'standard' )

As above, Ubuntu is not to blame for your Uppercase JPEG.. My Minolta saves in Uppercase, my Samsung in lowercase...
also
[http://www.impulseadventure.com/photo/exif-orientation.html](http://www.impulseadventure.com/photo/exif-orientation.html)

---

### Post by SpeedGonzo on 2010-08-10
Maybe this post comes in handy :) - incl. rotation

[http://mylinuxmint9.blogspot.com/2010/07/tip-11-adding-image-reizer-to-context.html](http://mylinuxmint9.blogspot.com/2010/07/tip-11-adding-image-reizer-to-context.html)

---

### Post by SoFl W on 2010-08-11
> **Zimmer said:**
> (clip)As above, Ubuntu is not to blame for your Uppercase JPEG.. My Minolta saves in Uppercase, my Samsung in lowercase...(clip_

SONY is uppercase, and I am a command line type of person.  My standard was filenames in lower-case, this often screwed me up.

---

