---
title: "ubuntu 9.10 excruciatingly slow shut down"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by occams_beard on 2010-01-09
When I shut down, it takes about 40 - 60 seconds or so. Also, the upsplash (?) never shows up. i.e, the white ubuntu logo. Instead I get a tty console login console hanging there for a long time.  Eventually it goes away, and then I get various messages... They seem to differ each time.

Usually it'll say something like "killed upsplash" then I get a message saying "Jetty not installed" (This was from when I installed netbeans from the repo, I think, I've since uninstalled it, but why's it complaining about jetty? )

Other times I get messages about VirutalBox, and MySQL not being able to shut down.

I've no idea where to begin to try and fix this. I do know on a fresh ubuntu install it shuts down nice and quick.

Any ideas how I can get my speedy shutdown back?

---

### Post by Temposs on 2010-01-09
What are your system specs?

And what apps do you typically have running when you shut down? 

Please provide a screenshot of the System->Administration->System Monitor showing the processes that are running in a typical session.

---

### Post by Temposs on 2010-01-09
Also when you make the screenshot, also test shutting down to confirm that it takes a long time to shut down from that point.

---

### Post by occams_beard on 2010-01-09
Hi, I've attached the screen shots. One shows a typical session, the other is right before a shutdown. I did shutdown after taking the second screenshot and it took about 30 seconds. There was no upsplash, and I got the usual message saying "jetty not installed"

Another note, I usually leave my system running for days on end. The longer it is up, the longer the shutdown appears to take. This morning for instance, I had not rebooted in a week, and the shutdown took extremely long. Guestimate, about a minute or so.

My system specs: Intel Core 2 Quad Q6600, 3 GB DDR2 Ram,  500 GB SATA Drive. Running Karmic 64 Bit

---

### Post by Temposs on 2010-01-09
Yeah, I mean, the more stuff you have open the longer it'll take to shut down, of course. And sometimes if you keep the session running for a long time, opening and closing programs a lot, sometimes you'll get extra daemon or runtime/vm processes hanging around even when you thought you closed everything. Have you tried booting up and then shutting down immediately? Have you tried shutting down Virtualbox before shutting down the machine? Virtualbox can be really hefty to exit because it has to close out of a virtual machine.

---

### Post by Temposs on 2010-01-09
Here's what my top processes from my session look like. I'll test my shutdown time. You can see my machine is no better than yours.

---

### Post by oldsoundguy on 2010-01-09
> **Temposs said:**
> Yeah, I mean, the more stuff you have open the longer it'll take to shut down, of course. And sometimes if you keep the session running for a long time, opening and closing programs a lot, sometimes you'll get extra daemon or runtime/vm processes hanging around even when you thought you closed everything. Have you tried booting up and then shutting down immediately? Have you tried shutting down Virtualbox before shutting down the machine? Virtualbox can be really hefty to exit because it has to close out of a virtual machine.
 
Yea,and if you have open items in Virtual Box, they have to shut down FIRST.  It is Windows crap, so your guess is as good any as to how long it will take for THAT stuff to clear and quit.

Best bet is to manually shut down your open windows FIRST.

---

### Post by llawwehttam on 2010-01-09
Hmm if it wasn't ubuntu I would have said try init 0.

As it is ubuntu could you post the output of ```
shutdown -hk
```

---

### Post by Temposs on 2010-01-09
Ok, so when I tried shutting down from my typical session that I've had open forever with all my usual apps, it took 58 seconds to shutdown, and it didn't show the usplash, just like you experienced.

However, observe the attachment below, which are my processes after starting up with nothing else running but what I have starting up by default. I timed my shutdown from here, and it was 7 seconds! So, big difference. AND it shows the usplash in this case. So, I'm not sure what's causing the issue here, but it definitely seems to be a lot slower as a result of having certain programs opened when you shut down. It may be normal. Maybe the usplash icon doesn't show if it takes too long to shut down all the apps you have open. That's what I'm guessing.

---

### Post by skodaman on 2010-04-08
I do not know if this is what you require  but if you just want to speed up the shutdown time.

Press Alt+F2
Type  gconf-editor
click Run
go to  apps> indicator-session
in R/Hand box put tick at end of line.to enable
Reboot and 60 sec delay should have been cancelled out.

                                                        J.J

---

