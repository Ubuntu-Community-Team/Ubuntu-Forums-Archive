---
title: "Starting from scratch"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by burtzacarach on 2009-01-20
I'm using Windows XP Pro atm to run two webcams and a music player in my car. I do mobile vlogs and a late-night talk show with my friends from the driver's seat. What I'm wondering is, is there a way to install a version of unix/linux that would only give me functionality for my two USB web cams and maybe a music player? I have limited processing power and capturing video from two cams at once uses a lot of it, so I'd like to be able to take advantage of as much of it as i can. I have done a full hardy install before, but the usage I'm thinking of is more like a "turn the computer on, get a prompt, press y and start capturing" feel. Do I start at the kernel level, or are there any real bare bones distros out there? Hopefully my question wasn't worded too poorly, it's tough for me to explain what it is I'm trying to do.
Thanks for all your help forums, you've been good to me.

---

### Post by stderr on 2009-01-20
The [server edition]("http://www.ubuntu.com/products/whatisubuntu/serveredition") is probably what you're looking for - no X installed by default. You can configure the drivers, whatever... 

By default you'll get a TTY with a textual login prompt. After login, you'll be presented with a terminal. Mine is:

ace@ace1:~$

You can write a simple bash script if you like and I suppose start it when bash starts, so you login and get presented with your prompt. Or more simply just invoke whatever application, alias or script you fancy.

---

### Post by cmnorton on 2009-01-20
This is an interesting post with at least two possibilities. You could either consider this an embedded Linux application (even though it is on standard hardware) or a regular installation with perhaps auto login and an auto-start application. 

This post has given me cause to go look up a few things of which I am not aware. Thank you.

---

### Post by burtzacarach on 2009-01-20
> **stderr said:**
> no X installed by default. You can configure the drivers, whatever... 

Is it likely that I'll have drivers for USB webcams? I have no experience configuring a server edition and writing scripts is completely new to me. As we speak, Bush is riding away on his helicopter. Good Riddance. But anywho. I know I can find a basic music player, but the camera are logitech and I'm not sure whether drivers are universal or if I'll need to find unix drivers for that camera. I'd like for the video from the two cameras to maybe capture to my memory and have the memory write it to the disk? I'm just trying to get the most power out of what I have. Will I really be saving processing power by switching to unix?

---

### Post by cmnorton on 2009-01-20
The server idea is a good one, and you would have virtually the same driver config on the desktop edition. Either way, as I posted earlier, you have some customization work ahead of you. You'll have fun (I think), and there is a lot of support out there for writing shell scripts.

As a suggestion in Ubuntu, put #!/bin/bash instead of #!/bin/sh on the first line of your shell script, and protect it with executable privilges chmod 755 script-file.

---

### Post by egalvan on 2009-01-20
> **burtzacarach said:**
> I'm using Windows XP Pro atm to run two webcams and a music player in my car. I do mobile vlogs and a late-night talk show with my friends from the driver's seat. .

So this is very interesting. could you post the exact hardware that makes this possible?

I'd very much like to experiment along these lines.

Thank you.

---

### Post by burtzacarach on 2009-01-20
> **egalvan said:**
> So this is very interesting. could you post the exact hardware that makes this possible?

I'm running a logitech pro 9000 and a GE EasyCam Pro, both mounted on the rear-view mirror. the Logitech captures using it's own software and the GE captures with AMCAP. They're both given enough bandwidth from a Gateway MX3231 Laptop's USB ports, running an Intel Celeron M processor 1.5GHz and 446MB RAM. The logitech records audio for both seats and both cameras are on a 240x360 resolution. It's fun.

---

### Post by stderr on 2009-01-20
> **burtzacarach said:**
> Is it likely that I'll have drivers for USB webcams? I have no experience configuring a server edition and writing scripts is completely new to me. As we speak, Bush is riding away on his helicopter. Good Riddance.

Good riddance indeed, and not a millisecond too soon. Let's hope they exile him to Timbuktu! Although I'd rather see him put in Iraq, or even better before a war crimes tribunal, where he should be. But I digress :p

How familiar are you with the 'nix command line? It probably won't be too difficult to configure, depending on quite how much you're looking to configure it ;)

[This link]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech") may give you some guidance re: webcam support, although it's probably a bit out of date. You can see the different drivers that you may need to use. Then it's a case of finding a CLI app (or possibly writing something) to interface with that. 

I'm none too familiar with webcams and therefore the related packages in Linux - maybe someone else has some suggestions?

---

### Post by snowpine on 2009-01-20
Here's a crazy suggestion: Try getting the cameras and everything working on a full Ubuntu setup. This will let you easily figure out what drivers, applications, etc. are needed to make it work. Take lots of notes of what you need. Then, use that information to build up your minimal system from scratch. The reason I suggest this is that a full install is a more "forgiving" environment than a minimal command line install. Just my 2 cents.

ps There are also Linux distros specifically for multimedia--Ubuntu Studio is the best known obviously; another intriguing alternative is dyne:bolic, which is designed for live video and dj'ing on the go using modest hardware.

---

### Post by egalvan on 2009-01-20
> **burtzacarach said:**
> logitech pro 9000 and GE EasyCam Pro,
Gateway MX3231 , running Intel Celeron M 1.5GHz and 446MB RAM.
 The logitech records audio for both seats and both cameras are on a 240x360 resolution. It's fun.

OK, got that. I can get that running in my truck no problem.


what do you use for the "live" part?
Is it interactive? Are you chatting with your friends?

Or have I mis-understood?

Is it record-only?

This would be ideal for "video-based directions" or tours, though.
Drive to your destination with the cam  facing foward, and dictate the turns as you go, then email /snail-mail the video... no more lost folks who mistook the convenience store...

---

### Post by burtzacarach on 2009-01-20
> **stderr said:**
> How familiar are you with the 'nix command line? It probably won't be too difficult to configure, depending on quite how much you're looking to configure it ;)

I'm not at all familiar with the command line. With all of these fully formed distro's out now, and with me starting so recently, there wasn't much purpose for me to use the command line. I picked up linux thinking I would have to work from the command line to get my computer up and running, even basically, but I haven't had to use it. Where is it that I can get help on commands and writing scripts?

---

### Post by burtzacarach on 2009-01-20
> **egalvan said:**
> O
what do you use for the "live" part?
Or have I mis-understood?
Is it record-only?

Oh, sorry. I've just woken up and I suppose my eyeballs haven't yet adjusted to the sun. I do go "live". I have my laptop hooked into Verizon's EVDO Rev.A network via PCMCIA card. However, recording and post-production for traveling question-and-answer sections and stunted debates can be a lot of fun in their own right. Sometimes the best material isn't completely improvisation, and although I am devotedly against scripted material, there's nothing quite like topic-guided conversation.

---

### Post by egalvan on 2009-01-20
> **burtzacarach said:**
> Oh, sorry. I've just woken up and I suppose my eyeballs haven't yet adjusted to the sun. I do go "live". I have my laptop hooked into Verizon's EVDO Rev.A network via PCMCIA card. ...

gotcha, many thanks.

ErnestG

---

### Post by burtzacarach on 2009-01-20
> **snowpine said:**
> ...Try getting the cameras and everything working on a full Ubuntu setup. This will let you easily figure out what drivers, applications, etc. are needed to make it work. Take lots of notes of what you need. Then, use that information to build up your minimal system from scratch... ...another intriguing alternative is dyne:bolic, which is designed for live video and dj'ing on the go using modest hardware.

Thanks for the idea. It seems a little bit more on my level. So what I'd do is install only the drivers and programs I need to get my mobile station to work on a basic unix distro?
I'm also going to give the dyne:bolic a try. I've read the site's information and it sounds very interesting, like you said.

---

