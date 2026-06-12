---
title: "How do I stream live video over the internet using Ubuntu 10.10?"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by seventhsamurai on 2010-10-26
Hi there

So I'm not exactly an Ubuntu, or even a computer expert. I have a necessity to stream live video over the internet. Basically, my brother-in-law is getting married, and there are relatives in parts of the world who cannot attend, so I need to hook up a camera and webcast the wedding as it happens. Is there a not too complicated way to do this?

I am running Ubuntu 10.10 64-bit on an Intel Core Duo 2.93 GHz machine with 4 GB RAM.

Is there any software that could accept an input via firewire from a Sony camera or DVCAM deck in standard definition and send it out onto the net, or am I asking for too much with the limited knowledge that I have?

I'd appreciate any help you can offer. I've been reading the forums online but most are pretty old, offering solutions for older versions of Ubuntu. I'm hoping since it's evolution, things may have become easier.

---

### Post by seventhsamurai on 2010-10-26
Nobody?!

---

### Post by seventhsamurai on 2010-10-26
So for anyone who may be interested, I guess I have made a little progress from where I started, reading up on more forums and doing more google searches. Still do not have it up and running but I'm hoping I'm on my way to do so.

Step 1

Download and install **Theorur** from Synaptic Package Manager. This is a program that can read an input from a Firewire DV source and stream from your machine.

First of all, check whether Ubuntu reads your DV camera. Ubuntu 10.04 never used to recognize my old JVC Mini DV camcorder. But 10.10 does. Easy way to see if it works is to install Kdenlive, go to the Record monitor tab and hit the connect button. If you see an image, your DV camera should work. You don't need Kdenlive anymore, unless you want to do some video editing.

Step 2

Go to [giss.tv]("http://giss.tv") and sign up for a channel/mount point. Once the account is created, it will send it you an email with a lot of information and instructions for activation. It takes about 24 hours to get activated.

This is as far as I have got now. Next step is to hook up the camera and actually get the damned thing to work. Will update as I go. Hoping some others try this too and can share their experience.

---

### Post by ArgusVision on 2010-10-26
I wish I had some direct experience with this to share... The closest thing I've done in this arena is Zoneminder. It's a Digital Video Recorder That's primarily used as a Camera Surveillance System. It works with multiple inputs of various types and uses a web interface. I don't know if it would be what you're looking for, but it is available in the repos. 
For details the site is [www.zoneminder.com](www.zoneminder.com) . 
Good luck.

---

### Post by HermanAB on 2010-10-27
The esiest way would be making a Skype conference call.

Another way is to set up a free account at justin.tv

---

### Post by seventhsamurai on 2010-10-27
> **HermanAB said:**
> The esiest way would be making a Skype conference call.

Another way is to set up a free account at justin.tv
Thanks. I attempted Justin.tv, but it doesn't seem to able to read from a DV camera connected via firewire.

---

### Post by seventhsamurai on 2010-10-28
Theorur over giss.tv worked like a charm. Go for it. giss.tv actually does not recommend Theorur for streaming, but I was unable to get any of their recommended programs to run on Ubuntu 10.10 64-bit.

So far, no issues with Theorur. At the viewer end, this setup doesn't seem to work on Google Chrome browser. On Firefox, it works beautifully.

ENJOY!

---

### Post by ArgusVision on 2010-10-28
[COLOR="SeaGreen"]Good Job![/COLOR] Don't forget to mark the thread solved. And if you happened to write down some steps to share I'm sure some future user would appreciate it.

Again, Congrats on solving this.

---

### Post by seventhsamurai on 2010-10-28
No more steps really. It's all too easy. Just as I had outlined above, make sure the camera is working, download Theorur and register for the mountpoint at giss.tv. After 24 hours, once its activated, input the info from the automatic email sent by giss.tv into Theorur (server, password, port etc). Select your video options based on your uploading speed, and the downloading/streaming speed of your end viewer and just hit "start streaming". Piece of cake.

---

