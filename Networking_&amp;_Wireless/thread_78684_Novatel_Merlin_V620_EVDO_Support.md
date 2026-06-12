---
title: "Novatel Merlin V620 EVDO Support?"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by d1c1ple on 2005-10-18
Anyone tried using and connecting to Verizon EVDO network using Ubuntu?

---

### Post by malacandra on 2005-10-23
I have the same card with Sprint and would really like some help in getting it to work.

The system "sees" the card but I can't figure out how to determine what /dev/ it is using and how to set it up to dial.

Thanks!

---

### Post by malacandra on 2005-10-28
At leas here's how I did it.

Insert the Merlin Card.

type **dmesg|tail** to make sure Linux sees the card.

Then type **rmmod usbserial**
followed by [B]modprobe usbserial vendor=0x1410 product=0x1110/B]

Then do **dmesg|tail** again. You should see that it has attached itself to a particular spot. Mine goes to /dev/ttyUSB0

From there you should do the following to shut down all other network cards:
[B]killall dhclient
ifconfig eth0 down
ifconfig wlan0 down[/B]

Now, you should be able to go ahead and congfigure your dial up using whatever tool you like, pointing it to /dev/ttyUSB0, or whichever has the card attached.

(BTW....I have my Palm set to sync on the same device node and it works fine, provided you don't do both at the same time.

Once in a while, it seems when you insert the card, it attaches to a different node. Just remove it and try again, or edit your config to dial on the new node.

Enjoy!

PS - I'm writing this while cruising down the interstate, connected by my Sprint Merlin!

---

### Post by mattengland on 2005-12-11
d1c1ple and malacandra,

Are your V620 cards still working on your Ubuntu-based laptops (presuming they've always been working and that you are using them on a laptop)?

I am considering running Ubuntu on an IBM Thinkpad, and my V620-based EVDO service from Verizon is very important to me, so I'd like to know I can get all this stuff to work without a significant problem.

Does malacandra's procedure work for others?  I see that it (the procedure) does not appear to require a download of extra software (eg, a 3rd-party driver)...which I find surprising.

Thanks for any feedback,
-Matt

---

### Post by mattengland on 2005-12-11
Fyi:

It looks like there's a much deeper thread on this topic here:

[http://www.linuxquestions.org/questions/showthread.php?t=300962](http://www.linuxquestions.org/questions/showthread.php?t=300962)

...and that malacandra is writing there as well.

-Matt

---

### Post by dryicezero on 2005-12-16
I have succesfully configures the Sierra 580 Wireless Card (Sprint PCS version) with Debian Sarge (stable).  Should work the same with Ubuntu.  The directions are posted on my blog @

[http://dryicezero.blogspot.com](http://dryicezero.blogspot.com)

or my website @

[http://netglobalstudios.com](http://netglobalstudios.com)

//Dryicezero

---

### Post by mattengland on 2005-12-16
[QUOTE=dryicezero]I have succesfully configures the Sierra 580 Wireless Card (Sprint PCS version) with Debian Sarge (stable).  Should work the same with Ubuntu.  The directions are posted on my blog @

[http://dryicezero.blogspot.com](http://dryicezero.blogspot.com)

or my website @

[http://netglobalstudios.com](http://netglobalstudios.com)

//Dryicezero[/QUOTE]

Excellent work, Dryicezero.  I'm posting the permalink for future reference:

[http://dryicezero.blogspot.com/2005/12/sprint-sierra-580-evdo-card-linux.html](http://dryicezero.blogspot.com/2005/12/sprint-sierra-580-evdo-card-linux.html)

-Matt

---

### Post by TVMA on 2005-12-19
Has anyone tried the above steps to also get the Novatel Merlin S260 EVDO card to work as well?

Thanks in advance for any assistance. If I can get my Novatel card to work with my toshiba satellite I will no longer need a reason to have windows on it...

Josh

---

### Post by Ainvar on 2006-01-20
Any update on this also? I tried reading the thread a few post up that turned into 5 pages of deadends on getting the v620 card from verizon to work.

---

### Post by mattengland on 2006-05-07
[QUOTE=mattengland]Excellent work, Dryicezero.  I'm posting the permalink for future reference:

[http://dryicezero.blogspot.com/2005/12/sprint-sierra-580-evdo-card-linux.html](http://dryicezero.blogspot.com/2005/12/sprint-sierra-580-evdo-card-linux.html)

-Matt[/QUOTE]

For those looking for a guide:  have you seen the above link?

Also, for the author of this guide (Dryicezero):

Where did you find all the parameters/values for these settings?

I have yet to try this on my V620, but I thought I'd read up a little to intelligently try to follow what's happening before I try the install/configuration.

Thanks,
-Matt

---

### Post by Ainvar on 2006-05-11
For the V620 card to work correctly you have to edit some .c files and recompile the modules for the kernel. This is te only way I got it to work in the past. The first link the the threads gives a lot of detail but right now I dont feel like redoing the kernel all the time with the dapper updates. Also you dont get the speed you do when in Windows when running this.

It would be nice if this was actually addressed in the kernel officially and things worked out a little better.

---

### Post by mattengland on 2006-05-11
For what it's worth, here's another article/discussion for EVDO support on Ubuntu and other Linuxes (it's my favorite one thus far):

[http://kenkinder.com/evdo-pc5740/](http://kenkinder.com/evdo-pc5740/)

I'm still trying to solve a couple issues myself (I can connect but can't stay connected), and have put out cash bounty asking for help to solve them at the discussion thread attached to the above article.

-Matt

---

### Post by Gforce on 2006-10-03
I know this is an old thread, but since I am new to ubuntu and the last post applies to me directly, I figured might as well ask the question.  When I say I am new to Ubuntu, I also mean new to linux as well.  I have a sprint pc5740 card but unlike most trying to use it for laptops, I have it installed in a desktop due to my location.  I am too far away for DSL and They don't allow cable access where I live.  The EVDO was my only option for high speed.
I have tried several different methods to make this work, but most of them require writing files to /etc/ppp/peers/ folder.  Ubuntu says I don't have permission to write to that flder.  What gives?

---

### Post by Gforce on 2006-10-03
OK I found another solution here. [http://ubuntuforums.org/showthread.php?t=132473&highlight=pc5740](http://ubuntuforums.org/showthread.php?t=132473&highlight=pc5740)
I tried and it works.  Now if there was only a way I could set it up to automatically dial upon bootup I'd be a happy camper

---

### Post by hggdh on 2007-01-26
Feisty comes with kernel 2.6.20 (currently at RC5 AFAIK). This kernel (and, in fact, since 2.6.19 RC1 or RC2) has v620 support coded in ./drivers/usb/serial/airprime.c.

This is to say... upon installing the default Feisty kernel, your should be all set to use the v620. Automagic discover by HAL/udev, and all of that.

In theory.

I am currently trying it -- my previous kernel was Edgy 2.6.17, and at this level I had to use an unofficial airprime.c that Greg K-H had written... which meant compiling the kernel, etc, etc. But it worked.

On 2.6.20-RC5 standard I am getting disconnected from the Verizon network continuously, with intervals varying from 5 to 20 minutes. I am still trying to figure out where the issue is. It is Verizon disconnecting me, and I can see no errors, no weird PPP stuff, nothing.

If any of you has v620, and is trying Feisty, I would like to know how it is going. Any provider will do, but I am really curious on experiences on Verizon.

---

### Post by smuir111 on 2007-02-07
[http://doc.gwos.org/index.php/EV-DO](http://doc.gwos.org/index.php/EV-DO)

This is how I got mine to work.  Very quick to setup.  I am running Edgy.

Like others however, I can use it for about 30-45 seconds at which point it stops working and finally disconnects.

Has anyone been able to make it stay connected like normal?  My guess is that I am missing a parameter somewhere, because it works fine in Windows.

---

### Post by hggdh on 2007-02-07
I had a similar problem while running Edgy (kernel 2.6.17), and eventually resolved it by

(1) installing a non-official patch from Greg K-H for airprime.c (the module that provides support for the v620), and

(2) disabling pings (i.e., commenting out lcp-echo-interval and lcp-echo-failure in the PPP configuration. I do not use wvdial, so I do not know how/where you should do it.

I am now running Feisty (kernel 2.6.20-6), with the default, official, airprime module. I do not have any problems nowadays.

BUT

when I first moved to Feisty, at 2.6.20-5, I was getting disconnected very frequently. From then to now I have made two changes, and I did not have time to test which one of them did the trick:

(a) moved to 2.6.20-6
(b) added "options airprime endpoints=1" under /etc/modprobe.d (the new airprime module, since about 2.6.19-rc2, will add 3 endpoints, giving you /dev/ttyUSB[0-5])

Again, I do not yet know which of the two options did it.

---

### Post by smuir111 on 2007-02-07
I am running Edgy 2.6.17-10.  Can you point me in the direction to get the Greg K-H airprime.c fix please.  I would like to try it.  Thanks.

---

### Post by smuir111 on 2007-02-07
Also, how do I install this file?

Thanks again.

---

### Post by hggdh on 2007-02-08
Grab it off [http://lkml.org/lkml/2006/5/31/237](http://lkml.org/lkml/2006/5/31/237) (the Linux kernel mailing list); it is at the bottom of the e-mail, all of it. Cut & paste it off, and save as airprime.c. This is the one I used.

This is a replacement for the original airprime.c kernel module in 2.6.17 (/usr/linux/drivers/usb/serial); it will have to be made & replaced in your system. I am not sure how to do that (I usually recompile the whole kernel & modules, since I want it with a restricted set of features), but I am certain we can find some sort of instructions somewhere here. Of course, you can always build the whole set of modules and then copy in just the new airprime.

You will need either linux-headers and/or linux-source, plus the kernel-package and build-essential packages (at least). For simplicity I suggest you use your current kernel configuration as the basis for the build.

After making the module, it will have to be placed in the correct /lib/modules/<whatever>; then you sudo rmmod airprime && sudo depmod -a && sudo modprobe airprime.

BUT -- if you have never recompiled the kernel, or kernel modules... I really suggest we get someone to prepare the steps more carefully. There is *always* the risk of hosing your system, if not done correctly.

---

### Post by rolando-ve on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108177](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108177) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello, well I`m in Feisty finnal release, and everybody say that how this works with kernel 2.6.20 this will support Merlin v620.

In fact, this one runs, but just for few seconds, I have 120 Cards V620, and don't know how to patch the new kernel to works fine with that.

Let me know if someone have the solutions.

> **hggdh said:**
> Feisty comes with kernel 2.6.20 (currently at RC5 AFAIK). This kernel (and, in fact, since 2.6.19 RC1 or RC2) has v620 support coded in ./drivers/usb/serial/airprime.c.

This is to say... upon installing the default Feisty kernel, your should be all set to use the v620. Automagic discover by HAL/udev, and all of that.

In theory.

I am currently trying it -- my previous kernel was Edgy 2.6.17, and at this level I had to use an unofficial airprime.c that Greg K-H had written... which meant compiling the kernel, etc, etc. But it worked.

On 2.6.20-RC5 standard I am getting disconnected from the Verizon network continuously, with intervals varying from 5 to 20 minutes. I am still trying to figure out where the issue is. It is Verizon disconnecting me, and I can see no errors, no weird PPP stuff, nothing.

If any of you has v620, and is trying Feisty, I would like to know how it is going. Any provider will do, but I am really curious on experiences on Verizon.

---

### Post by hggdh on 2007-04-20
v620 support seems to be stable at 2.6.20.

I made two changes to get my Verizon connection working:

1.  added 'lcp-echo-interval 0' and 'lcp-echo-failure 0' to my provider definition in /etc/ppp/peers (alternatively, you can *comment out* the above entries under /etc/ppp/options). The provider file looks like this now (notice that you will have to change the user identification string, and adjust to the correct TTY -- in my case, it is ttyUSB0 because this is the single USB modem device I use):

> hggdh@here:/etc/ppp/peers$ cat verizon
ttyUSB0 
230400
user [email]123456789@vzw3g.com[/email]
remotename verizon
defaultroute
usepeerdns
debug
crtscts
lock
noproxyarp
noauth
novj
novjccomp
lcp-echo-interval 0
lcp-echo-failure 0
connect "/usr/sbin/chat -v -e -f /home/hggdh/ppp/verizon-connect"
disconnect "/usr/sbin/chat -v -e -s -f /home/hggdh/ppp/verizon-disconnect"
hggdh@here:/etc/ppp/peers$ 

/home/hggdh/ppp/verizon-connect  is:

> ABORT "BUSY"
ABORT "NO CARRIER"
ABORT "NO ANSWER"
SAY "Starting Verizon-Wireless PPP conneciton...\n"
'' 'ATZ'
'OK' 'AT&F&D2&C1E0V1S0=0'
'OK' 'AT+IFC=2,2'
SAY "Dialing...\n"
'OK' 'ATD#777'
'CONNECT' ''

/home/hggdh/ppp/verizon-disconnect is:

> '' '\K'
'' '+++ATH0'
SAY "Verizon-Wireless disconnected\n"

Nothing fancy in these two PPP scripts.

2. During my tests I noticed that the new driver creates 3 endpoints by default. AT this point in time I did not know if this was part of my problem or not, but I did remember that on 2.6.17 the unofficial drive was using one single endpoint, so I changed /etc/modprobe.d/options and added the following line:

> options airprime endpoints=1

At the time I did it I went on with:
(a) removed the v620;
(b)  'sudo rmmod airprime'
(c) re-inserted the v620

You would only need to do (a)-(c) one time; you can also reboot (end result is the same, just takes longer :-))

I do not know if setting one single endpoint is necessary or not: it was working, and I left it as is.

But this was it. Works flawlessly now. There is a good chance all you need is to inhibit the lcp-echo* from being driven: by default PPP will ping the remote every so often and, if no response, it will drop the connection; how many times to try, and what the interval will be are set by the above lcp-echo* parameters.

---

### Post by scotttkd on 2007-04-20
I thought I would add this info to this post...I am embarrassed  to admit how easy it was to get verizons new usb720 device working in feisty.  I started by researching the forums and copied all of the dialing settings and config scripts and got primed to go postal on the command line when I got a lazy thought and tried the GnomePPP that I had downloaded.  I started PPP, plugged in my usb720, clicked on autodetect, it did, so I left all the settings it gave me as is, added the dialing info from the other posts in this thread and hit connect.  VIOLA...I am on line, stable and working faster than I could believe.  

Now if I could get Firefox to recognize video formats properly I would be a happy ubuntu camper.

---

