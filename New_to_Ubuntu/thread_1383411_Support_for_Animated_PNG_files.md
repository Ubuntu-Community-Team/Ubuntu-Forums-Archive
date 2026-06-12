---
title: "Support for Animated PNG files"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-17
The png format has been around for ages, but Firefox (since v3) and Opera (since 9.5) now support [animated png]("http://animatedpng.com/index.php/about/") files.

Something I've just found out is that Chromium (and I presume Chrome as well) does **not** support animated png files, which is a tad disappointing. Does anyone know whether this support will be coming on that browser shortly?

I have the gimp-gap plugin installed into gimp, but I can't for the life of me work out how to create animations of any sort (even animated gifs) in gimp. The manual seems rather silent on the subject, so can anyone provide a linky for me to bone up on the subject?

Alternatively, is there any other linux app out there that creates animated png files?

---

### Post by koglaa on 2010-01-17
[http://www.youtube.com/watch?v=PmbPDAHCZ6E](http://www.youtube.com/watch?v=PmbPDAHCZ6E) Thats for animated gif's.  And as for png's, I never knew that they came animated :O

---

### Post by ibuclaw on 2010-01-17
Looks like there is a firefox plugin for it.
[https://addons.mozilla.org/en-US/firefox/addon/5519](https://addons.mozilla.org/en-US/firefox/addon/5519)

Regards
Iain

---

### Post by Roger Allott on 2010-01-17
> **koglaa said:**
> [http://www.youtube.com/watch?v=PmbPDAHCZ6E](http://www.youtube.com/watch?v=PmbPDAHCZ6E) Thats for animated gif's.  
Thanks for that. At least I now know how GIMP does animated gifs, but as it seems a bit cumbersome, I'll stick to using Jasc's Animation Shop in Windows for the time being.

I followed a similar procedure to that to see if GIMP has any ability to save animated pngs, but it doesn't. Or at least, it doesn't save them using the same method as that used to save gifs.

> **koglaa said:**
> 
And as for png's, I never knew that they came animated :O
It's amazing that so few people know of animated pngs. There seems to be a bit of a spat between Mozilla geeks and non-Mozilla geeks over the format. The former group likes animated pngs, and the latter group favours mngs.


> **tinivole said:**
> Looks like there is a firefox plugin for it.
[https://addons.mozilla.org/en-US/firefox/addon/5519](https://addons.mozilla.org/en-US/firefox/addon/5519)

Thanks. I actually had that addon already, but it's low in features and provides no compression of the frames. But as the competition is so limited, I suppose it's about the best of what's out there!

---

### Post by Styromaniac on 2010-01-21
Download japng editor here -> [http://www.reto-hoehener.ch/japng/](http://www.reto-hoehener.ch/japng/)
and use Photoshop. If you don't have Photoshop and someone else does, just ask for their install disk.

Follow this link to the instructions I've posted -> [http://animatedpng.com/index.php/blog/applications-that-work-with-apngs/#comment-435](http://animatedpng.com/index.php/blog/applications-that-work-with-apngs/#comment-435)

I'm hoping that it's not too confusing. I wrote the instructions a day after I figured these simple steps out, so I may not be completely correct about the quirkiness of Photoshop's exporting, but the steps will nonetheless make things much easier for APNG creation.

---

### Post by Roger Allott on 2010-01-21
> **Styromaniac said:**
> Download japng editor here -> [http://www.reto-hoehener.ch/japng/](http://www.reto-hoehener.ch/japng/)
and use Photoshop. If you don't have Photoshop and someone else does, just ask for their install disk.

Follow this link to the instructions I've posted -> [http://animatedpng.com/index.php/blog/applications-that-work-with-apngs/#comment-435](http://animatedpng.com/index.php/blog/applications-that-work-with-apngs/#comment-435)

I'm hoping that it's not too confusing. I wrote the instructions a day after I figured these simple steps out, so I may not be completely correct about the quirkiness of Photoshop's exporting, but the steps will nonetheless make things much easier for APNG creation.

Thanks for that, but is the jar file a plug-in for Photoshop? Or is it a cross-platform app for which Photoshop's output is particularly helpful?

---

### Post by laststop on 2010-01-21
[http://sourceforge.net/projects/apngasm/](http://sourceforge.net/projects/apngasm/)

---

### Post by Marvin666 on 2010-01-21
Animpations was never a part of the offical PNG standard. Firefox devoloped the animated png fromat, so it's understandable  for it to not work in other browsers.

---

### Post by Roger Allott on 2010-01-21
> **laststop said:**
> [http://sourceforge.net/projects/apngasm/](http://sourceforge.net/projects/apngasm/)

I can't find any instructions for the use of that utility, but [http://animatedpng.com/index.php/assembler/]("http://animatedpng.com/index.php/assembler/") incorporates it into its online AGNG creation tool.

What I've ascertained by trial-and-error is that the static png files that one puts into the zip file must have filenames that contain no 'odd' characters such as brackets, and I think space characters are a no-no too.

---

### Post by laststop on 2010-01-21
> **Roger Allott said:**
> I can't find any instructions for the use of that utility

Simple:
apngasm output.png frame000.png [1] [10] [/f]

Online version has a 2Mb limit.

---

### Post by Styromaniac on 2010-01-21
> **Roger Allott said:**
> Thanks for that, but is the jar file a  plug-in for Photoshop? Or is it a cross-platform app for which  Photoshop's output is particularly helpful?
It isn't a plugin. It's a Java-based app, so any OS with Java will run it.

> **Marvin666 said:**
> Animpations was never a part of the offical PNG standard. Firefox devoloped the animated png fromat, so it's understandable  for it to not work in other browsers.
Opera also supports the animated png format and it displays them at least as well as Firefox does.

Also, there is a patch that adds APNG support to Webkit browsers (Safari and Chrome), apparently. [https://bugs.webkit.org/show_bug.cgi?id=17022](https://bugs.webkit.org/show_bug.cgi?id=17022)
I have no idea what I'm supposed to do with the code though, so I haven't tried it. The link was posted in this google forums thread -> [http://www.google.com/support/forum/p/Chrome/thread?tid=5600f3ae8ece44d8&hl=en&fid=5600f3ae8ece44d800047cf0573713d3](http://www.google.com/support/forum/p/Chrome/thread?tid=5600f3ae8ece44d8&hl=en&fid=5600f3ae8ece44d800047cf0573713d3)

---

### Post by laststop on 2010-01-22
> **Marvin666 said:**
> Animations was never a part of the offical PNG standard.

So it's unofficial extension. Whatever. At long as it works, it's all good.

---

### Post by Roger Allott on 2010-01-22
> **laststop said:**
> Simple:
apngasm output.png frame000.png [1] [10] [/f]

Sorry, but I don't think I understand your shorthand. By way of example

If I want to animate 3 png images called:
frame001.png
frame002.png
frame003.png

and create an animated png file named:
output.png

I want 250 milliseconds gap from frame001 to frame002
and 575 milliseconds gap from frame002 to frame003
and 780 milliseconds gap from frame003 back to frame001

and the animation is continual loop

and all files are in my home directory

what do I input to the terminal?

---

### Post by laststop on 2010-01-22
It can only do the same delay for all frames. And default delay is 1/10 of a second.

---

### Post by Roger Allott on 2010-01-22
> **laststop said:**
> It can only do the same delay for all frames. And default delay is 1/10 of a second.

OK, so let's assume then that I want a delay of 500 milliseconds between each frame. What would the terminal command be?

What I'm really asking about is the "[1] [10] [/f]" append that you mentioned. I can't work out what these mean.

---

### Post by Styromaniac on 2010-01-23
Hey, guys. Email Max Stepin if you want to beta test the Photoshop plug-in he's working on.
[http://animatedpng.com/index.php/blog/applications-that-work-with-apngs/#comment-436](http://animatedpng.com/index.php/blog/applications-that-work-with-apngs/#comment-436)

[I]"Each layer is treated as animation frame (check out the examples I  used).

Delay dialog is not implemented yet, it's hardcoded as  1/10 sec for now.

I'm mostly interested in cases where plugin  doesn't work. If you'll
find some, let me know.

Thanks.
Max."[/I]

^Those are its limitations as of 1/22/10.

@Roger Allot: I believe that it's a simple division equation.

If ***apngasm output.png frame000.png [1] [10] [/f]*** gets you a 10fps animation, then ***apngasm output.png frame000.png [1] [30] [/f]*** should get you a 30fps animation.

A 500 millisecond delay would be ***apngasm output.png frame000.png [1] [2] [/f]***

---

### Post by laststop on 2010-01-23
> **Roger Allott said:**
> What I'm really asking about is the "[1] [10] [/f]" append that you mentioned. I can't work out what these mean.

If you want 2/3 seconds delay, then the correct command will be

**apngasm output.png frame000.png 2 3**

Square brackets means it's optional. So you can just write 

**apngasm output.png frame000.png**

and you will get 1/10 sec delay.

Add **/f** option to skip the first frame (it's a special apng feature).

---

