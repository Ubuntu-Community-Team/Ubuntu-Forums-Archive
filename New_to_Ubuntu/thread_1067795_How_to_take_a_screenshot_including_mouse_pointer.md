---
title: "How to take a screenshot including mouse pointer?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by 2CV67 on 2009-02-12
The default Ubuntu "Take Screenshot" application has a box to tick for "Include pointer" but it does not seem to work, or at least not reliably.

Does it?

I tried KSnapshot but that seems to have no option for including the pointer.

I read about Scrot but it does not seem to be available for Intrepid.

Finally, all I could find was Gimp, which is bad news as an interface but it will show the pointer, if only for full-screen shots which you then need to crop.

Did I miss something?

I would be satisfied with the options of the default application, most of the time, if I could really make the "Include Pointer" feature work.

If I could stop it closing after every shot, that would be a bonus!

Thanks for any suggestions.

---

### Post by jolx on 2009-02-12
scrot is available for intrepid - [http://packages.ubuntu.com/search?keywords=scrot&searchon=names&suite=intrepid&section=all]("http://packages.ubuntu.com/search?keywords=scrot&searchon=names&suite=intrepid&section=all")

---

### Post by 2CV67 on 2009-02-12
> **jolx said:**
> scrot is available for intrepid - [http://packages.ubuntu.com/search?keywords=scrot&searchon=names&suite=intrepid&section=all]("http://packages.ubuntu.com/search?keywords=scrot&searchon=names&suite=intrepid&section=all")

Ah - thanks for that!

I suppose I was really meaning Gscrot with GUI interface.

Following your post, I checked a bit further & it seems Gscrot is now being renamed to Shutter & is not quite ready to go yet?

Sounds like it would be the answer to the question, as soon as it is reliably available.

Is it likely to appear in Synapt any time soon?

---

### Post by jolx on 2009-02-12
[PPA for Shutter]("https://launchpad.net/~shutter/+archive/ppa")

---

### Post by 2CV67 on 2009-02-12
> **jolx said:**
> [PPA for Shutter]("https://launchpad.net/~shutter/+archive/ppa")

Thanx jolx for pushing me towards Shutter!

After a few minutes trial, I am already convinced this is just what I was looking for & seems to be a particularly well-thought-out tool.

You get to select with/without pointer & that works.

You can choose delays, surrounds etc & that works.

You can save one or several combinations of criteria into "Profiles" to re-select in one click.

You can capture the whole screen or any window or any rectangle you want, with or without pointer.

The Shutter/Gscrot window gets out of the way when it should but does not keep closing & needing re-opening.

The option for capturing any rectangle is particularly well thought out as it presents you with a screen to do your selecting on, but then waits until you press "Enter" before taking the shot, unlike Screengrab, for instance, which takes the shot as soon as you have created a rectangle - like it or not.

Without talking about the various save options.

Obviously a good application!

On the downside, I had never heard of PPAs and would probably not have dared to go ahead with this installation without your recommendation...
The written instructions on the [PPA page]("https://launchpad.net/~shutter/+archive/ppa") are short but ambiguous & confusing for a noobie.
The next link ["Follow these instructions"]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") adds to the confusion & goes over my head, being apparently aimed at developers.
Most reassuring was the [Utube video]("http://www.youtube.com/watch?v=UUZOQsNo_ws") which made it look feasible or at least worth a try.

I followed the video, selecting only the "deb....intrepid main" line (not the "deb-src..." line??).
I never got warned or asked about OpenPGP keys, so did nothing there (why??).

I did not find any kind of Help or Tutorial....
[This was the best description]("http://maketecheasier.com/gscrot-a-powerful-screen-capture-tool-for-linux/2008/11/14") I found.

Going through the installation, the references are "Shutter" but in Synapt it is still Gsrcot for now.

Hope that review may encourage others to try it & hope also there is or will be a Help function soon.

I consider this thread [SOLVED] now. :D

Thanks for your help!

---

### Post by Vadi on 2009-03-06
Can you see if our [new guide here]("http://shutter-project.org/faq-help/ppa-installation-guide") is better?

---

### Post by 2CV67 on 2009-03-06
> **Vadi said:**
> Can you see if our [new guide here]("http://shutter-project.org/faq-help/ppa-installation-guide") is better?

Yes - much better!
Thanks & congratulations!

I could probably have done that OK without the other video I had to use previously.

A couple of comments, since you asked:
1. Your screenshots look rather fuzzy & low-grade, which is ironic for a screenshot tool site...
2. If you click on a screenshot to see it bigger, then I don't like the way your 'close' button is hidden at the bottom. Surely 'close' buttons are conventionally at top right?

Thats what you get for asking questions!
Don't think I am ungrateful - it's a great application & your new installation guide is very welcome! :D

---

### Post by Vadi on 2009-03-06
No, it's all valid feedback. I'll look into the blurry thumbnails.

The "close" button - hm, I'll see if I can duplicate the buttons on top. Because in these types of image viewers, that's where they usually are, but I see your usability concern.

---

### Post by 2CV67 on 2009-03-06
> **Vadi said:**
> No, it's all valid feedback. I'll look into the blurry thumbnails.

The "close" button - hm, I'll see if I can duplicate the buttons on top. Because in these types of image viewers, that's where they usually are, but I see your usability concern.

You are welcome!
Hopefully it will be a better experience for future users.
Keep up the good work.

"Feedback, the breakfast of champions." ... (Ken Blanchard)

---

