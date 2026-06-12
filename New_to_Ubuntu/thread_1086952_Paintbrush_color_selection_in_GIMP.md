---
title: "Paintbrush color selection in GIMP"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by sks24 on 2009-03-04
I can't figure out how to select a color for my paintbrush in GIMP.  All I want to do is just point to a few things in a screenshot using a bright green or yellow hand-drawn arrow, and I've looked through the help files, but I give up!](*,)

I feel like such an idiot.  I'm sure it's all right in front of me, but, please . . . somebody help me!

Thanks in advance,
SKS

---

### Post by Het Irv on 2009-03-04
You should see a black box over a white box in the Toolbar, that is the color selector.  Double-Click on the box on top to change the foreground color.  You should be good to go then.

---

### Post by sks24 on 2009-03-04
Thank you Irv,

I not sure exactly how I got the paintbrush to paint green, but I got it painting green.  I kind of felt like an animal who got lucky with a latch after scratching at it for awhile.  

SKS

---

### Post by bkorb on 2011-05-01
It would be really nice if:

1. these were obvious, and
2. it actually worked.

Foreground always comes out as a pale blue grey no matter what I do. I've tried changing it with the FG/BG tool and by double clicking the black and white boxes on the tool bar.  At least that and the FG/BG tool agree on what the color ought to be.  It would just be nicer if the paint brush color came out as what the two complementary (conflicting?) tools were saying.

---

### Post by Tony Flury on 2011-05-01
Never had a problem with the color selector in GIMP - and btw they are not complimentary - you can set foreground and background to whatever you like - including exactly the same thing - and i don't think you need to double click.

If you are getting a different colour then the one you think you have chosen - check the Mode and the Opacity of your brush - if the Mode is anything other than Normal you may well get a modified colour.

---

### Post by Irvine_himself on 2011-12-13
>  I kind of felt like an animal who got lucky with a latchI know this is an old thread, but I have repeatedly had this exact problem, (albeit intermittently.) and since I have I have finally figured out both the problem and the solution, I think it is best to document it in a thread that has a high ranking Google score. 

The problem is in the "mode of the image", (this is not the same as the brush mode,)

Basically, you go

```
image > mode > RGB

```as in the attached image.

I hope this helps other people, if nothing else it will help me to remember what it is I did.:P

.

---

### Post by asifnaz on 2011-12-13
> **Irvine_himself said:**
> I know this is an old thread, but I have repeatedly had this exact problem, (albeit intermittently.) and since I have I have finally figured out both the problem and the solution, I think it is best to document it in a thread that has a high ranking Google score. 

The problem is in the "mode of the image", (this is not the same as the brush mode,)

Basically, you go

```
image > mode > RGB

```as in the attached image.

I hope this helps other people, if nothing else it will help me to remember what it is I did.:P

.

Nice . I was really looking for that

---

### Post by Frogs Hair on 2011-12-13
I found this useful on more than one occasion . [http://www.gimp.org/tutorials/](http://www.gimp.org/tutorials/)

---

### Post by eshober on 2012-03-16
Thanks for the solution! I was pulling my hair out! It would have taken HOURS reading the tutorial or other docs because I was searching for how to work with with brushes and colors, which has nothing to do with the problem which was that I opened a gif tile and Gimp set index mode.

---

### Post by ageofsteam on 2012-03-16
> **bkorb said:**
> It would be really nice if:

1. these were obvious, and
2. it actually worked.

Foreground always comes out as a pale blue grey no matter what I do. I've tried changing it with the FG/BG tool and by double clicking the black and white boxes on the tool bar.  At least that and the FG/BG tool agree on what the color ought to be.  It would just be nicer if the paint brush color came out as what the two complementary (conflicting?) tools were saying.

Make sure that the settings for the color dropper are set to "sample merged".  When I have this problem, it's usually trying to sample a clear over-layer...

Also, if the photo is HUGE, you might want to set it to sample the average color of, say, 5 square pixels or something.

I can't think of what else woulD be causing your problem. :?

---

### Post by ufmace on 2012-12-12
> **ageofsteam said:**
> Make sure that the settings for the color dropper are set to "sample merged".  When I have this problem, it's usually trying to sample a clear over-layer...

Also, if the photo is HUGE, you might want to set it to sample the average color of, say, 5 square pixels or something.

I can't think of what else woulD be causing your problem. :?
This thread looks dead once again, but I just found another one the hard way that I'd document/suggest you try if you're having this problem.

Go into the Channels tab (usually next to Layers) and make sure that all 4 channels are selected.

I had selected only the Alpha layer to make some changes to it, but I forgot to set it back after I was done. The next time I tried to paint something, in bright red, it would show up as black in one of the upper layers and not at all on the background layer. So of course I was painting only in the alpha channel, which has no color, and shows up as black in every layer but background and nothing in the background.

---

