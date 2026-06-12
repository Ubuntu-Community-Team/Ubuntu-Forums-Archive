---
title: "Sync Computer and TV"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by Johannes85 on 2009-12-01
Hi!

I am an absolute beginner when we are talking Ubuntu so please bare with me if i ask "stupid" questions.

Im running Ubuntu 9,10 *Karmic koala*

My problem is:

I like watching movies and i got some on my computer. i would like to be able to plug in a HDMI cable between my computer and tv (witch worked perfectly with crappy vista)

I am able to make my computerscreen visible on my tv but not with the same resolution.

It would be perfect for me to be able to plug my Cable in my computer and then the computermoniter would turn black and the picture would show on the tv.

My normal resolution on the PC is 1280x800 and the TV is 1900x1080

I have the newest driver for my Nvidia card and a program called Nvidia X server setting.

I have searched this support site but found the articles very cryptic.

I really hope someone can help me!

---

### Post by Dougie187 on 2009-12-01
The easiest way I have found to hook a computer up to a TV with a native TV resolution would be to disable the laptop LCD. Someone else might have another solution but this is what I do when I want to watch something.

First, Plug in your TV.

In the "Nvidia X Server Settings" program go to the "X Server Display Configuration" section on the left.

Then click the "Detect Displays". Then click on the TV in the "Layout" box and click the "Configure" button, select "Twin View" and hit ok.

Then click on the Laptop's screen in the layout box, click configure, and select "Disabled" then hit ok, and hit apply. It should turn off your laptop's screen and turn on the TV. Then you can quit the NVidia settings  thing and watch your movie's or whatever.

After you are done, just go back through, and turn back on your laptop's screen with twinview and turn off your TV screen and everything should be back to normal.

The reason this works for me, is that I hate having my laptop screen on when I'm using it on a TV anyways. So, if anything this could at least be a temporary solution.

---

### Post by Johannes85 on 2009-12-01
Thanks you i will try that.

I just hoped there where a way for this to be automated in some way.

---

### Post by Dougie187 on 2009-12-01
Not that I know of. This is just the simplest way I have found to do it. I mean, you might be able to write a script to do it for you, but I think in general you will have to do something no matter what.

---

### Post by Hospadar on 2009-12-01
I *think* nvidia-settings can be scripted with a saved configuration file (from nvidia settings).  So I *believe* you could set yourself up in nvidia-settings the two ways you want (with and without the tv) and then make some little icons that run nvidia-settings the two ways you want

Look at "man nvidia-settings" for more info.

I think the command line switches you are interested in are "-l" (just loads a configuration file, does not open up the GUI or prompt for input) and "--config=filename", which allows you to specify a non-default configuration (one of your saved configs for example)

---

