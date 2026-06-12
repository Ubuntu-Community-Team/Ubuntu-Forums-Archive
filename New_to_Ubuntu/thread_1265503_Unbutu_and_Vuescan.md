---
title: "Unbutu and Vuescan"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Aloha Sunshine on 2009-09-13
Hi,
 
I am really new to Unbuntu, is this an operating system that would replace my Windows XP? I stumbled unto this web page as I was searching for a resolution to my problem with my film/slide scanner.
 
I was using a Brookstone Slide & Negative Scanner earlier this year which was received as a gift. I had done a quick restore after my computer crashed in May of this year. At that time I did not install the scanner software. Now that I want to scan some slides I am not able to install the software. The software is an"ArcSoft PhotoImpression 6. I checked for updates to this software, message states that I have the latest version.
 
Checked ArcSoft.com. There is no PhotoImpression 6. PhotoImpression 6.5 Gold is now listed. This seems to be a photo editing progrm. Nothing is mentioned about removing dust or other particles from the film or slide.
 
I then checked for film/slide scanners. On the TigerDirect web site there were several reviews that stated similiar problems. One of the comments mentioned using Vuescan software. Upon checking for Vuescan software, I noticed "Vuescan with Ubuntu 8.10 Linux". 
 
Can you provide more information on using Ubuntu vs. Windows XP? If I was to install Ubuntu, how would I go about doing this. Is there instructions included when the download is done?
 
Any help would be greatly appreciated. I am 68 yrs young and is trying to complete a family history scrapbook for my family.
 
 
Aloha from Hawaii
:KS, ):P

---

### Post by cariboo on 2009-09-13
Your WIndows programs, will not run on Ubuntu. You can use Gimp, Applications-->Graphics-->Gimp to edit, resize, etc your photos. Check the [sane project]("http://www.sane-project.org/") to see if your scanner is supported. Vuescan is a proprietory program, that you have to pay for inable to use it.

To install Ubuntu, go [here]("http://www.ubuntu.com/GetUbuntu/download") and download the iso and burn it to a cd. Then boot from the CD. It is a live CD so you can try Ubuntu before you install it.

---

### Post by mapes12 on 2009-09-13
Hi and welcome to the forum

As cariboo907 comments there is great support in Ubu for your requirements. However, you still may be able to run your favourite windows applications by installing them through [WINE]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by emarkay on 2009-10-20
VueScan IS available for Ubuntu.
[http://www.hamrick.com/](http://www.hamrick.com/)

However as for your slide/negative scanner...  I am debugging this now - so far, no luck.

---

### Post by tifff on 2009-12-08
Vuescan works perfect with karmic (out of the box when used as root), for normal user one has to adjust /lib/udev/rules.d/40-libsane.rules as indicated in
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/121082](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/121082)

---

