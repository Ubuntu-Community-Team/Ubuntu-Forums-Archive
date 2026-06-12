---
title: "Canoscan LiDE 200"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by eWetten on 2009-05-16
Absolute beginner barely covers what I am to Ubuntu.  My ex boyfriend got me set up and I have never done so much as install a program myself, I fail really hard at understanding Linux, but it is something I support so I want to try!

Like an idiot I bought a scanner because I was brainwashed by the ex that Linux supports everything, but apparently everything doesn't include my new CanoScan LiDE 200 scanner!

I tried plugging it in and nothing happened.  XSane doesn't support it, WINE didn't seem to like the disc that came with the scanner and as I don't speak Linux the internet is remarkably unhelpful.  

So any help would be greatly appreciated!  I want my faith in Linux restored, I hate windows but I think I am too stupid for this Linux stuff!

---

### Post by waspbr on 2009-05-16
first of all, don't hesitate to ask questions around the forums whenever need help or feel overwhelmed, learning a new operating system takes a bit of time.

now the bad news, I have a canoscan myself, and sadly enough like your model, the 200, it is not supported by linux. So long story short, it will not work. I dual boot with windows XP so its not a deal breaker for me. 

sorry to be the one to tell ya the bad news, the bad thing here is that linux is not really to blame for this. Some manufacturers simply won't bother releasing drivers for linux.

---

### Post by autumnraine on 2009-12-11
I wrote to Canon (copied below), and this is the response I got. I encourage EVERYONE who owns one of these scanners or would consider buying one (they're REALLY good and portable) to write to Canon's customer support: if enough of us do, maybe we could get a driver for the scanner soon, and maybe we could even convert Canon into a Linux friendly company!

 ------------------------------ ----------------------
You wrote:
--------------------------------------------
on: 2009-12-11 04:00:09, Customer wrote: ......


I own a LiDE 200. I am satisfied with my scanner, however I am VERY unsatisfied with your neglect to produce a Linux driver for it. Like many other people, I have recently left Windows behind for the simplicity, flexibility and stability of Linux distributions like Ubuntu. Until you make a policy of producing Linux drivers for your products, I will not be buying anything from you nor can I recommend your products to any of my family or friends.
 
Response:
-------------------------------

Dear  Nelson Alexander

Thank you for your E-mail inquiry regarding your CanoScan LiDE 200 Scanner.

It is only through our customers comments and suggestions that we are able to manufacture quality products that our customers will be able to use on a consistent basis. The fact that you took the time to write to us is indeed appreciated. Please be assured that your comments have been forwarded to the appropriate Department for their information and review.

Should you require further assistance, please feel free to email us or visit our customer support website at [http://www.canon.ca]("http://www.canon.ca/")


Sincerely,

Mike B.
Technical Support Representative
Customer Information Centre
Canon Canada Inc.
Do you have a story to tell? Visit [http://www.canontellyourstory.ca]("http://www.canontellyourstory.ca/") for your chance to win prizes!

---

### Post by JoesCat on 2010-05-09
Just googled for Canoscan Lide 200 which brought me here.
Thanks for the feedback, thus saving me from buying one.

The price was nice, but if it isn't supported, no point in buying one.[-X

Think I'll be looking at Brother instead as I see more support from the manufacturer in terms of linux and their hardware.\\:D/

---

### Post by lavinog on 2010-05-09
You can check here for supported scanners:
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)
I wonder how it isn't supported.  I have a Canoscan lide 20 (not 200) and it worked just fine out of the box with xsane.  I had a much earlier model before this one and it worked too.
I have had issues with canon printers in the past, and have since warned friends and family to not buy canon printers.

---

### Post by JoesCat on 2010-05-09
Thanks, that's a good list to use when comparing stuff at a store.

When I looked for info, I wasn't able to find Canon info easily, but managed to find brother info on their website, I ended-up finding info here: [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html)

When it comes to purchases and recommendations...
Supported hardware == worth considering or recommending.
Not-supported == leave it on the shelf for someone else.

---

### Post by clickwir on 2010-05-28
Well crap. I had tested someone elses Cannon LIDE 30 or something and it worked fine under Ubuntu. So I just assumed this would. So I went and bought a LIDE 200.

Looks like I'll be sending this one back.

Anyone have any suggestions on a scanner that is supported and works with just one USB plug? Preferably as slim and sleek as this one?

---

### Post by bts on 2010-06-13
> **JoesCat said:**
> Just googled for Canoscan Lide 200 which brought me here.
Thanks for the feedback, thus saving me from buying one.


The same is true for me. I found this Canon product on Amazon today, but apparently it is unusable with Linux. Several years ago I had the same trouble with a Canon printer, and their support returned very stupid answers ('you are using a non-standard operating system'). Dinosaurs... 

Thanks for this article.

---

### Post by lavinog on 2010-06-14
Give it zero stars on any online store's rating system.

---

### Post by desertdog on 2010-06-14
A developer at the Sane project is finishing up adding support for the Canon Lide 100 and 200. 

You have to download the latest source code and compile from source.

[http://mp610.blogspot.com/2008_04_01_archive.html](http://mp610.blogspot.com/2008_04_01_archive.html) explains how to do this.

---

### Post by rosenth on 2010-07-20
here its supported in unstable
[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON)
may you try this and aware us?

---

### Post by moshman on 2010-08-05
Hello,

I have tried the method proposed by desertdog when I come to the ./configure comande the message No such directory that comes, anyone has a clue to get over this?

Moshman

---

### Post by pandanuma on 2010-08-05
moshman,  you have to change to the directory where the downloaded package installed, then run 
./configure
make
make install

---

### Post by mojo risin on 2010-08-05
Just for info, I have a Lide 25 and it is working fine :)

---

### Post by Motomouse on 2010-09-14
Testing my Lide 200 finally with development sane snapshot.

Looking good, Lide 200 support is in the pipe! 

Regards 
Motomouse

---

### Post by clickwir on 2010-09-14
wow, it's a long time coming. I thought they forgot about it. 

I wonder how long it'll take to get into mainline Ubuntu. Hopefully, if it works well, not too long. 

I liked the scanner, it was decent hardware. Just didn't have any way to use it. Thanks for the update!

---

### Post by spike852 on 2010-09-25
The latest version of xsane installed without any problems or error messages, but the LiDE 200 is not seen.

It is showing up as connected if I run lsusb, but xsane does not recognize it. Any thoughts?

Output of lsusb:
```
:~$ lsusb
Bus 003 Device 003: ID 03f0:0d17 Hewlett-Packard LaserJet 1012
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04a9:1905 Canon, Inc. 
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Output of scanimage -V
```
:~$ scanimage -V
scanimage (sane-backends) 1.0.22git; backend version 1.0.22
```

So it looks like I have the latest and greatest version of the sane-backends, but no joy.

---

### Post by moshman on 2010-09-26
I don't understand.

---

### Post by dli8ilb on 2010-11-05
> **spike852 said:**
> The latest version of xsane installed without any problems or error messages, but the LiDE 200 is not seen.

It is showing up as connected if I run lsusb, but xsane does not recognize it. Any thoughts?

Output of lsusb:
```
:~$ lsusb
Bus 003 Device 003: ID 03f0:0d17 Hewlett-Packard LaserJet 1012
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04a9:1905 Canon, Inc. 
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Output of scanimage -V
```
:~$ scanimage -V
scanimage (sane-backends) 1.0.22git; backend version 1.0.22
```

So it looks like I have the latest and greatest version of the sane-backends, but no joy.

i'm having the same exact problem as you, spike.  i'm using 9.10 (karmic).

---

### Post by dli8ilb on 2010-11-06
here is the solution (slightly modified for the LiDE 200 model), tested and working in Karmic:

[QUOTE=desertdog]To get this working, here are the steps to take:

**1**) You need some usb libraries, so, in a terminal type:

sudo apt-get install libusb-dev build-essential libsane-dev

**2**) To get the sane backends from git you need git-core. If you don't already have it, type this (also in a terminal):

sudo apt-get install git-core

**3**) Now use the git that was just installed to get the sane backends using the following command:

git clone git://git.debian.org/sane/sane-backends.git

That downloads the backends and puts them in a folder called sane-backends in your home folder.

**4**) Change directory into the new sane-backends folder and compile them:

cd sane-backends

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var

make <--- this one takes a while

sudo make install

Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions.

**5**) You need to edit a file, but you need to be root to edit it, so:

sudo gedit /lib/udev/rules.d/40-libsane.rules

and add the following 2 lines:

# Canon CanoScan Lide 200
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1905", ENV{libsane_matched}="yes"

save the file, exit gedit, exit terminal, reboot, and...

SCAN AWAY!
Instructions modified version of Shutter4U's post. [/QUOTE]

at this point, if your scanner still isn't working, do this:

[QUOTE=desertdog]Check file /etc/sane.d/genesys.conf to see if your scanner is listed.

If not, add it with a text editor. Use the format that the other scanners use.[/QUOTE]

in other words:

> 
**6**) sudo gedit /etc/sane.d/genesys.conf

then add the lines: 

# Canon LiDE 200
usb 0x04a9 0x1905

save the file and test with xsane.

thanks to whoever the genius is that made these scanners work with linux, and for desertdog's instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=1238578](http://ubuntuforums.org/showthread.php?t=1238578)

no more Canon products for me, i'm done with that company :mad:

---

### Post by GrouchyGaijin on 2010-11-06
Man,this is  great!
I followed all the steps and now my Lide 100 works.
How do you guys know this stuff????

---

### Post by davposs on 2010-11-09
I just wanted to thank everybody who contributed to this thread - with particular thanks to desertdog, dli8ilb, spike852 and rosenth.
As a result my Lide 200 scanner finally works (after months of trying). 
I was so delighted I thought it was time to signup to the forums and try and help as well - so this is my first shy attempt at a post.

One simple issue I did have that might help others is that after I:
-  installed the 'make' 
-  made desertfog's config file changes
I could get scanimage to work (list, test and actual scan options)  but not xsane.

I finally tracked it down to what I assume was a hangover from a previous install and sane related files in /usr/local. After I manually deleted these  then both xsane and then simplescan worked.

---

### Post by maitland on 2010-11-25
well, i got everything installed and the permissions, but when scanning with xsane it seems like the scanner is trying to move in reverse.  the led bar is at the "top" of the scanning area, and it tries to move further in that direction making a clicking sound

scanimage gives an I/O error when i try to use that.

I am using a version of 9.04

any ideas?

---

### Post by maitland on 2010-11-26
well, i tried the daily snapshot, but still no love.

what are the versions of the dependencies that are found in the versions of Ubuntu that ya'll are using?  libusb-dev, etc...

maybe if i update all of those, it will work??

---

### Post by davposs on 2010-12-01
I have to confess I'd be tempted to pursuade you to try upgrading to 10.10 as the install process is a bit convoluted and I suspect there may be a number of package dependencies. 
Perhaps wait to see what other posts you get with other ideas and if nothing comes try the full upgrade.

I do know that once I did have a problem that the bar stopped halway and then xsane no longer worked. I'm now scratching my head to remember what I did to fix it - I think it was run scanimage -T,  which took the bar back to the start position.

---

### Post by maitland on 2010-12-11
thing is, i'm not running a vanilla *ubuntu.  I have an Indamixx netbook, and the OS is built on 9.04.  If I tried to upgrade, I would undoubtedly break all sorts of things that are working great, now.  doesn't seem worth it.

I'll try that scanimage -T thing though.  thanks for the input.  I'm sure if i hack at it a bit i can get it working.

---

### Post by headcount on 2010-12-12
Got this working thanks to [dli8ilb's post](http://ubuntuforums.org/showpost.php?p=10080046&postcount=20).  I'm running Ubuntu 10.10 64-bit.

The key was to make sure you have backend version 1.0.22.  I had 1.0.21 at first and couldn't get the thing to work.  

Thanks again!

---

### Post by maitland on 2010-12-13
@ headcount:

definitely tried the latest unstable version.  also, I tried a daily snapshot.  it says on the sane webpage that they are "working on" 2400 dpi support... so, that must mean they are doing something to it... 

it's starting to look like the problem must be related to one of the other associated packages...  I guess I could try to update to all the latest versions of every package that is required to build the backend...  

is this what they call, "dependency hell?" :D

@ davposs:

I tried running scanimage -T.  it failed due to "I/O error" the first 2 tiimes.  then it magically worked the 3rd time.  everything was a "PASS" except for the first 2 entries.  (which are the only 2 that attempt to make a real sized scan, it appears).  the damn thing is just running in reverse.  there is no question about it.  I wonder if i could hack the code to just make it go in the opposite direction... ?

---

### Post by hornord on 2010-12-19
> **dli8ilb said:**
> here is the solution (slightly modified for the LiDE 200 model), tested and working in Karmic

This worked perfectly on Lucid. Thanks a lot for the walkthrough!

---

### Post by theultimate on 2011-02-09
dli8ilb thank you very much! I've been trying for months to get the scanner working  with Maverick 64bit. I did everything as described and the scanner works now with Xsane perfectly.

---

### Post by fermulator on 2011-03-05
TIP:  With the latest version of sane-backends, [linux support for Canoscan LiDE 200 is COMPLETE]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=LIDE+200&bus=any&v=04a9&p=1905")! (we no longer need to clone the git repo and compile...)

 1) We need to get support from sane-backends, so add this PPA: [https://launchpad.net/~robert-ancell/+archive/sane-backends](https://launchpad.net/~robert-ancell/+archive/sane-backends), and install sane extras.

```
sudo add-apt-repository ppa:robert-ancell/sane-backends
sudo apt-get update
sudo apt-get install libsane libsane-extras sane-utils
```

 2) Test that it works by running simple-scan as root:
```
gksu simple-scan
```
    If scanning doesn't work as a regular user, continue with step 3.

 3) To allow us to scan as a regular user, we need to modify the USB permissions for the scanner, so follow step 5 from > **dli8ilb said:**
> Now everything is installed, but you still won't be able to scan (except as root) until you set up some permissions.

5) You need to edit a file, but you need to be root to edit it, so:

gksu gedit /lib/udev/rules.d/40-libsane.rules

and add the following 2 lines:

# Canon CanoScan Lide 200
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="1905", ENV{libsane_matched}="yes"

save the file, exit gedit, exit terminal, reboot, and...

---

### Post by lavinog on 2011-03-19
Just bought a LiDE210, and got it working with lucid 64 and the robert-ancell ppa.
The only change to the above instructions is the product id in 40-libsane.rules:
```

# Canon CanoScan Lide 210
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="190a", ENV{libsane_matched}="yes"

```

For other models you can get the required information by plugging in your scanner and typing lsusb:
```

Bus 001 Device 008: ID 04a9:190a Canon, Inc. 

```
the 04a9 is the idVendor number (canon in this case)
the 190a is the idProduct.

---

### Post by GammaQuantum on 2011-04-19
I tried the ppa on a Maverick-32 Bit Install on my iMac Core 2 Duo.

When I attach my scanner to the USB and start `gksu simple-scan` and try to scan, the scanner head moved a little back and forth and simple-scan then fails. I did not see any light.

How can I get my LiDE 200 to work?

---

### Post by tattvajit on 2011-05-15
Still unable to get Canon LIDE 200 to work after following all instructions in this thread. Running 11.04. This is what happens on running "gksu simple-scan":

** (simple-scan:6015): WARNING **: Unable to start device: Error during device I/O

---

### Post by GammaQuantum on 2011-05-15
I managed to get my scanner to work using xsane. It is not as simple as simple-scan or scanimage, but it does the trick.

---

### Post by tattvajit on 2011-05-15
xsane worked for me too.

---

### Post by lavinog on 2011-05-16
> **GammaQuantum said:**
> I managed to get my scanner to work using xsane. It is not as simple as simple-scan or scanimage, but it does the trick.

if it works in xsane shouldn't it work with simple-scan?  I thought they both used the same SANE backend.

---

### Post by GammaQuantum on 2011-05-17
Maybe simple-scan uses some different default values than xsane, so it might create different results.

---

### Post by Swagman on 2011-05-17
I wonder if the OP eWetten is still using Ubuntu ?

---

### Post by GammaQuantum on 2011-05-17
Hopefully he/she is still subscribed to this thread!

If he/she did not like 9.04, chances are that 9.10, 10.04, 10.10 and 11.04 were not tried out at all.

Anyway, people trying to find support for their LiDE 200 now have a partial answer.

---

### Post by fermulator on 2011-05-22
Yeah this sucks.  I usually use xsane, which still works.  But since [my post on March 5th]("http://ubuntuforums.org/showpost.php?p=10526638&postcount=31"), "simple-scan" no longer works.  Similar to other reports, clicking "scan" causes the scanner to move around a little, then gives up and says "Failed to scan".

In the meantime, please use "xsane" image scanner (it's more complicated to use, but at least it works).

I'm not sure why simple-scan would stop working, yet xsane still works ... they should theoretically use the same command sequences...

---

### Post by Lateralis on 2011-05-23
I was just in the process of writing a somewhat ranty post about Canon and how crap their support is and that I still couldn't get the scanner to work, even after trying the steps in this thread multiple times.  I tried running gksudo xsane once and that didn't work.  I tried it a second time for a bit of a laugh, just before I posted my post, and amazingly, it worked!

---

### Post by codebirth on 2011-07-30
Hi!

I just registered to say thanks. Followed the steps on dli8ilb post and I finally can scan on Ubuntu :D

[http://ubuntuforums.org/showpost.php?p=10080046&postcount=20](http://ubuntuforums.org/showpost.php?p=10080046&postcount=20)

Thanks dli8ilb!

---

### Post by davposs on 2011-10-22
I want to echo codebirth's comments
Having previously got this all working under 10.10 I did a complete pc rebuild and at the same time upgraded to 11.10.
 Followed the steps on dli8ilb post (again) and it all works for me  - even using SimpleScan (which I confess to liking ..)
Thanks (again).

I actually do a serious amount of scanning using this thing. Very very occasionally the scanner hangs halfway and I can't bring it back using SimpleScan.
I usually power off/on on the scanner and then run scanimage -T in a terminal - and this seems to resolve the issue
Stress it seems to happen very rarely.

---

### Post by iaw4 on 2012-09-13
I tried it for a Canoscan LiDE 100 under ubuntu 12.04.1.  I even went so far as updating the 40-libsane.rules .  (the LiDE 100 has device id 1904 instead of id 1905.)  however, it still fails.  same results in simplescan and gscan2pdf---failed to scan and IO error, respectively.

xsane works, however.

/iaw

---

### Post by gwendolynrae on 2013-02-06
This still works in 2013 with ubuntu 12.10.  This is the first time I've ever done any coding in the terminal and now I can scan.  Thank you!!

---

