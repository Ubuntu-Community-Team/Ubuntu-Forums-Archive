---
title: "[SOLVED] Image quality problems"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Goll on 2008-12-29
Does anyone know what this is:
[IMG]http://img514.imageshack.us/img514/2269/89151162dj5.jpg[/IMG]

This is not a scanning problem.
All of the images in my gallery have this, squareness to them..

I haven't seen it on ms so I'm not sure. 
And I've gone through the video card, Nvidia options.

I really have no idea....


I figure I'm doing this right- This is a print screen, so essentially this is what it looks like for me, but maybe not for you...

I have the Hardware proprietary drivers supplied by Ubuntu installed. (The latest.)

Here's the original image: 
[http://ajzimmerman.deviantart.com/art/Weird-People-106853919](http://ajzimmerman.deviantart.com/art/Weird-People-106853919)

---

### Post by cariboo on 2008-12-29
I think you are going to have to explain what the problem is, I see a section of the image you linked to. You say something about a scanning problem, but you say this is a screen shot. What is the problem?

Jim

---

### Post by Goll on 2008-12-29
> **cariboo907 said:**
> I think you are going to have to explain what the problem is, I see a section of the image you linked to. You say something about a scanning problem, but yousay this is a screen shot. What is the problem?

Jim

I said "This is not a scanning problem."
This is a problem with how the linux graphics drivers are working.

Are you seeing the same thing in the original image?
This is not occuring in ms- so this is not a problem with the image.

As I've said, my graphics card is Nvidia. I've heard the drivers supplied by the Ubuntu community are better then the proprietary ones supplied by Nvidia itself.

---

### Post by cariboo on 2008-12-29
I'm a technician, could you show the whole screenshot of  the screen instead of the cropped portion that you posted. I don't see any problem, unless I see the whole screen.

Jim

---

### Post by Dirjel on 2008-12-29
The picture *does* look really pixel-y.  What are you using to open the image?  Is it just the preview in the file browser thing, or are you opening it in a program?

---

### Post by Goll on 2008-12-29
> **cariboo907 said:**
> I'm a technician, could you show the whole screenshot of  the screen instead of the cropped portion that you posted. I don't see any problem, unless I see the whole screen.

Jim

I appreciate the help.
I'm finding this a bit strange. 

I'll split these up a bit. Here's what's happening. I have the image that's shown to everyone on the main page. Then I can press download- and it shows the whole image on its own page. [http://fc20.deviantart.com/fs38/f/2008/355/5/8/Weird_People_by_Ajzimmerman.jpg](http://fc20.deviantart.com/fs38/f/2008/355/5/8/Weird_People_by_Ajzimmerman.jpg)

When I do that, the image looks fine! Like this one below. 

[http://img123.imageshack.us/img123/5499/screenshotju7.png](http://img123.imageshack.us/img123/5499/screenshotju7.png)
And then the page that it's shown on:
[http://img186.imageshack.us/img186/9389/screenshot1my6.png](http://img186.imageshack.us/img186/9389/screenshot1my6.png)
[http://img186.imageshack.us/img186/8627/screenshot2xm0.png](http://img186.imageshack.us/img186/8627/screenshot2xm0.png)

Now, what trips me out, is that it doesn't have distortions in it normally, when it's on a windows platform.
I don't really know what I should be looking for as the problem now.

Here's some more examples:
[http://img242.imageshack.us/img242/4214/screenshot4zk3.png](http://img242.imageshack.us/img242/4214/screenshot4zk3.png)

And then the ones that are fine..
[http://img242.imageshack.us/img242/5818/screenshot5bx6.png](http://img242.imageshack.us/img242/5818/screenshot5bx6.png)
[http://img123.imageshack.us/img123/4426/screenshot6jx7.png](http://img123.imageshack.us/img123/4426/screenshot6jx7.png)

> **Dirjel said:**
> The picture *does* look really pixel-y.  What are you using to open the image?  Is it just the preview in the file browser thing, or are you opening it in a program?

I'm just opening it up in the browser.

---

### Post by cariboo on 2008-12-29
I've had a look at all the images you posted links to, and I don't see any pixelation or wierdness until the images are zoomed to at least 150%, I've got a cheap BFG Nvidia 8400GS video card and a midrange Acer moniotr, so I may not be seeing he same thing you do, plus I'm in my 50's so my eyes may not be as good as they used to be :).

You have to remember the that Microsft has probably spent billions to make things look good on most computers, whereas aside from wages, I doubt if the X11 guys have a million invested in research and development. All Iknow is that most of my wallpapers and pictures look more impressive in Linux, than they do in Vista, with the same hardware.

Jim

---

### Post by shecky on 2008-12-29
It looks fine for me on the webpage, but goes pixely if I use Firefox's image zoom extension on it. You could try using Firefox's default zoom with ctrl+0.

---

### Post by Big_astur on 2008-12-29
As shecky says, i only see your problem if i use the ctrl+mousewheel zoom that firefox has. As soon as i try to zoom in i have your problem. If i download the pic and open it, to preview it, i can zoom as much as i want (for example 250%) that i don't have that problem.

So i think the problem is with the firefox zoom "tool".

---

### Post by Goll on 2008-12-29
> **cariboo907 said:**
> I've had a look at all the images you posted links to, and I don't see any pixelation or wierdness until the images are zoomed to at least 150%, I've got a cheap BFG Nvidia 8400GS video card and a midrange Acer moniotr, so I may not be seeing he same thing you do, plus I'm in my 50's so my eyes may not be as good as they used to be :).

You have to remember the that Microsft has probably spent billions to make things look good on most computers, whereas aside from wages, I doubt if the X11 guys have a million invested in research and development. All Iknow is that most of my wallpapers and pictures look more impressive in Linux, than they do in Vista, with the same hardware.

Jim


> **shecky said:**
> It looks fine for me on the webpage, but goes pixely if I use Firefox's image zoom extension on it. You could try using Firefox's default zoom with ctrl+0.


I've isolated the problem:
Firefox:
[http://img242.imageshack.us/img242/4969/screenshot12ev5.png](http://img242.imageshack.us/img242/4969/screenshot12ev5.png)
Epiphany:
[http://img72.imageshack.us/img72/5598/screenshot11za0.png](http://img72.imageshack.us/img72/5598/screenshot11za0.png)

The images are distorted in firefox. 
I had zoom on..


;) lol...


Well, for those who ever have problems with images. Try zooming out! :D

---

