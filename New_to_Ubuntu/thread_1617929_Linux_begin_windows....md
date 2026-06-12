---
title: "Linux begin windows..."
date: 2010-11-10
forum: New to Ubuntu
---

### Post by vinceCOOK on 2010-11-10
Hello Forum people,

Please can you help with with beginnings in Linux.

I have a Linux system with just the command window.

I typed "ls /" ......and it showed me it has rudimentary folders
like bash and root and bin and etc.

What method can i use to start the "windows gui x11 environment"?

Presuming the above system is available?

Alternatively, how do i aquire and install a Linux package manager installer tool?

Once installed, how do i execute that PM tool and tell it to go find and download and install the x11 environment?

Finally, how then do i execute and begin the x11 windows environment on the screen?

Thankyou

Vince.

---

### Post by jtarin on 2010-11-10
From what source did you obtain the distribution of Linux you have installed. The name or link to download page.

---

### Post by CharlesA on 2010-11-10
Running ***startx*** usually starts the GUI if one is installed.

---

### Post by vinceCOOK on 2010-11-10
Hello Charles

Uh...."startx" just resulted in a message saying "command not found"

will take another look

thanks

Vince.

---

### Post by brian mcgee on 2010-11-10
Hmm, wild shot in the dark, but try:
```
startx
```The output of the following commands might help us identify your system:

```
cat /etc/issue
```and

```
uname -a
```

---

### Post by vinceCOOK on 2010-11-10
Hello

When i type "startx" at the command prompt

it says that the program is not currently installed but
"you can install it by typing

"sudo apt-get install xinit"


should i install it....and THEN type  "startx" at a new
command prompt?

thanks

Vince.

---

### Post by brian mcgee on 2010-11-10
Do you want the standard Ubuntu desktop? If so, run the following command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by vinceCOOK on 2010-11-10
Hello Forum People,

Hello everybody and brian

Yes i just want to have a familiar Ubuntu GUI desktop.

This is my system after the recommendations earlier in this
thread...

see below...
----------------------------------------------------------------

cat /etc/issue............gives the output below

ubuntu 10.10 \n\l

uname -a ................gives the output below

Linux ip-10-122-230-159 2.6.35-22-virtual #33-Ubuntu SMP Sun Sep 19 23:54:13 UTC 2010 i686 GNU/Linux

----------------------------------------------------------------

Brian, if i install the ubuntu desktop is it large?

When it's been installed, how do i start that desktop from the
command prompt...?

thanks

Vince.

---

### Post by mastablasta on 2010-11-10
First - did you maybe in use server version or minimal install?
 
You should use desktop version.
 
Another option is that you might need to install graphics card drivers or use a command parameter to enable the propper graphics. 
 
with propper install of desktop system the ubuntu should automaticly load the GUI on start and will be just like running windows (sort of). no command line is needed.
 
did you try to boot from CD and run it live? how did you install it?

---

### Post by vinceCOOK on 2010-11-10
Hello,

Well i am still trying to get the familiar windows
environment GUI of Linux x11......up and running.

i will try to install the ubuntu GUI desktop
as per the instructions of this thread and see
if that "windows environment" will start up
atomatically when ubuntu boots up.



thanks

Vince.

---

### Post by brian mcgee on 2010-11-10
Yep, ubuntu-desktop is large. Run the following to get details on ubuntu-desktop package:

```
apt-cache show ubuntu-desktop
```This is what is normally installed when you install Ubuntu. The graphical environment should start automatically on boot, or you should get an error.

---

### Post by vinceCOOK on 2010-11-10
Hello,

Uh...well this computer is a virtual ubuntu box
on Amazon web servers.

I don't want to over-complicate this.

I just installed the program "xinit" and that was fine.

tried the command

sudo startx

The system tried stuff but says NO SCREENS are available
and says the primary device is not PCI.

This looks like it's talking about graphics cards.

What i don't understand is ALL THE HARDWARE is virtual stuff
bellonging to amazon. So the virtual machine does not appear
to like stuff concerned with X.

My graphics card is AGP.  But this is only a dumb terminal using
PUTTY to talk to a virtual linux box in Amazon's data center in eastern america.

My graphics card should not be part of the equation right?

What i can't understand is why these virtual boxes are not
arranged with a GUI windows desktop in the outset?

Youtube videos show that you do INDEED get a proper GUI windows Linux box from these services....

hmmmmm

any advice

(i don't want to overcomplicate this....over 3 hours is hard work just to get a GUI desktop in linux up and running)

thanks

Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello

Found this at the bottom of the web page....

[http://alestic.com/mt/mt-search.cgi?search=x+windows&IncludeBlogs=1&limit=20](http://alestic.com/mt/mt-search.cgi?search=x+windows&IncludeBlogs=1&limit=20)

it says that the desktop will work by using "NX no machines" tool.

and some other stuff.

V.

---

### Post by kesman on 2010-11-10
Hey!

If you are running the Ubuntu box on remote via Putty, there's no way to access any graphical interface.

If you wan't to use it graphically, you need to install a vnc or other remote desktop server on it, which is a totally different matter.

---

### Post by vinceCOOK on 2010-11-10
Hello

[http://alestic.com/mt/mt-search.cgi?...ogs=1&limit=20](http://alestic.com/mt/mt-search.cgi?...ogs=1&limit=20)

yes

If you click MORE.......at the bottom of that web page
where it talks about UBUNTU DESKTOPS

THere it tells you exactly how to get the desktop working
on this virtual amazon Linux box.....(using NX NO machine tool)

it's not difficult....it seems

thanks


Vince.

---

### Post by kesman on 2010-11-10
Sweet!

Let us know if you successfully reach the graphical interface, it might be helpful for future users.
The guide there suggest to download an NX-client to your home computer and just connecting to the ubuntu instance on the remote server. Not sure if this works out-of-the-box, but it actually might. You might need to configure the NX server in the ubuntu instance.

---

### Post by vinceCOOK on 2010-11-10
Hello

yes

I will try to let you know what happens with NX machine
and getting the ubuntu desktop working on these virtual machines
from amazon.

Currently these virtual machines are FREE for one year.

They are micro instances and don't appear to stipulate
which LINUX image must go into them. AMzon supply a free
image and many many other images.

Just checking my COSTS and it says ZERO for the virtual machine
that was running the UBUNTU image. As expected the whole chages
page shows ZERO because these mirco instances are now FREE for one year.

also per amazon account they appear to maybe allow you 20 instances...(free micro instances)

it was just interesting me the angle on having free computers
truly for free...

most people use them as servers and apache and things...but there
is nothing to stop you using them as desktop machines and installing your own custom Linux tools.

will let you all know.

thanks

Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello

[http://alestic.com/index.html](http://alestic.com/index.html)

these are the free custom images of ubuntu for Amazon
ec2 virtual machine's.

You copy the code listed for the ubuntu image your
using and then start that instance running inside
an EC2 virtual machine instance.

ye

Vince.

---

### Post by kesman on 2010-11-10
Seems a little complicated.

Be careful when copy-paste:ing commands from an unknown source, there are commands that could ruin your installation if you get lucky, and even do hardware damage if you get unlucky. The latter isn't a problem on Amazon servers though, since I guess they got quite high security settings on the virtual servers.

---

### Post by vinceCOOK on 2010-11-10
Hello

Uh,

I am a bit stuck on the understanding...

Does NX need installing on the remote machine as a SERVER?

I have MX client installed on my local machine fine.

i followed the steps here...



[http://alestic.com/2008/04/ubuntu-desktop-ec2#more](http://alestic.com/2008/04/ubuntu-desktop-ec2#more)


but it does not make clear whether or not you must
first connect to your amazon instance from a terminal connection
on your home desktop  (using Putty tool)

Then, from that terminal window install NX on that distance computer....... and do the other stuff it mentions above here...

Then try doing a desktop GUI connection....from my home machine.

is my understanding OK?

thanks


Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello

Sorry....i got all those commands to work right here...



[http://alestic.com/2008/04/ubuntu-desktop-ec2#more](http://alestic.com/2008/04/ubuntu-desktop-ec2#more)


it just said........ "shadow passwords are now on".
----------------------------------------------------------------

it did NOT really show me creating a new system user...

it did not ask for any NICKNAME creation or a password?

------------------------------------------------------------

I will try to make the desktop connection to the
GUI unbuntu desktop now...

V

---

### Post by vinceCOOK on 2010-11-10
Hello

[http://www.nomachine.com/download-package.php?Prod_Id=2090](http://www.nomachine.com/download-package.php?Prod_Id=2090)

it's looking to me like i must install NX server on the
distant machine...from a Putty command terminal.

how would i upload these files to the distant ubuntu box?...
(they are on my windows desktop here)

Then how would i install them....(dpkg --install file.deb)

THen how do i configure that NX server....on the distant machine?

-----------------------------------------------------------------

All i know is that NX connects from my desktop here to the remote amazon ubuntu machine and it says it can't find the NX service...

thanks

Vince.

---

### Post by kesman on 2010-11-10
From [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
do the following steps:

```
sudo apt-get install python-software-properties && sudo add-apt-repository ppa:freenx-team
```
and then
```
sudo apt-get update && sudo apt-get install neatx-server
```
and then move on to "How to Start/Stop FreeNX" -section

---

### Post by vinceCOOK on 2010-11-10
Hello

Ok thanks

I will work on that now.

Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello,

Ok 

did those commands...

now how do i start it?

sudo /etc/init.d/freenx-server start

perhaps?

thanks

Vince.

---

### Post by kesman on 2010-11-10
Yes, like that but I think it might be already running. I'm having troubles with the first apt-line, it doesn't find the GPG-key but maybe it worked for you.

---

### Post by vinceCOOK on 2010-11-10
Hello

All those commands you gave me appeared to install the stuff...(freenx)

but i also tried simply.....

--------------------------- 

sudo apt-get install freenx  

-------------------------------

and it could not find the freenx package.......





anyhow...it does not like the start command below...
--------------------------------------

sudo /etc/init.d/freenx-server start
--------------------------------------


it says command not recognized....perhaps this is because it is already started?

Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello

I was installing on Maverick mearKat Ubuntu.....version

so have to follow those instructions for that version

will try this again...

also it says you must FIRST have SSL installed and configured
before you install FreeNX

anyhow will try this all later perhaps...

it's certainly not straight forward

V.

---

### Post by vinceCOOK on 2010-11-10
how do you start the SSH deamon?

thanks

Vince.

---

### Post by kesman on 2010-11-10
Could be, could be.

However you managed to install it after adding the repository. To confirm this try
```
sudo apt-get install neatx-server
```
hmmm, for some reason they talk about neatx and freenx -servers there. I checked the source of the packages, and there seems to be only freenx-server -named packages, so the correct installation code would be
```
sudo apt-get install freenx-server
```

---

### Post by vinceCOOK on 2010-11-10
Hello

no

it can't find either of those packages...

(i did find how to start SSH and it is started and working)

so it looks like freeNX is not installed properly here...

well it appeared to try to install and did a whole load of stuff

but when i look inside the /etc/ folder there isn't a folder
for NX orany folder for FREEnx...or NeatNX

Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello

No

[https://help.ubuntu.com/community/FreeNX#Installation](https://help.ubuntu.com/community/FreeNX#Installation) Prerequisites

this page details a load of stuff...and says that FreeNX does not have a package for Maverick mearcat ubuntu.

Youmust first use the LUCID instructions then make some small alterations 

hmmmm

Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello

This is the exact Linux nightmare i hoped to avoid

surely versions of Ubuntu come with a....remote client server
thing that can just be running on port 22?

it appears Ubuntu Maverick Mearcat doesnot even come with SSH
installed?

As for WHY all of this is not automated...it's anybodies guess?

Amazon offers the virtual machines...but you don't arrive right
inside a GUI desktop.

Amazon don't appear to detail HOW you would start a gui desktop.

But i notice that my distant ubuntu machine has a folder for X11 so all the stuff is there ready to go...

it should be simple to do these remote connections into distant machines...

REmote DEsktop in windows does so in seconds....into a distant windows machine....

hmmmm

i find it hard to believe all of this is not set up to GO out of the box with Ubuntu?

hmmmmmmmmm

V.

---

### Post by 3rdalbum on 2010-11-10
It's a security thing. No operating system should be listening to incoming ports by default; it's incredibly bad security practice.

Also, Amazon servers are really designed to be used as the backed of something else, not as your desktop. The command-line is how you remotely administer a Linux server, which is what you have. Go install Ubuntu Desktop (which has a GUI) locally, or look into something like EyeOS.

Edit: Also, Amazon wouldn't preconfigure a desktop - big drain on their RAM and CPU time.

---

### Post by vinceCOOK on 2010-11-10
Hello

Thanks for your input and comments.


I don't doubt what you write or the validity of it...


Having seen videos on youtube of people using these amazon
virtual machines with full desktops it just interested me....(to get it going)


perhaps, as you say...it's totally "logical common sense" on Amazons part
that they have made things presented the way they envision most people will
want to use them. 


I know next to nothing about servers and thin clients or what-have you.


But presumably, a thin client would do very nicely by dialing into these free
virtual ubuntu box's and the desktop.


My idea is simply that having seen the idea working...it would be nice to get it
working here and to have a look at it....just to have the "know how".


Possibly one other reason that this is not totally striaght forward is precisely
because amazon don't want people doing this. That is not to say however,
that it is not possible to do it...(because it is)


I saw a real opportunity for thin clients to use these services advantageosly.


thanks,


Vince.

---

### Post by vinceCOOK on 2010-11-10
Hello,

Will look at the page on FREENX with  Maverick Mearcat ubuntu.


Try those insructions....with SSH installed and configured and running (daemon)


Try to get FreeNX running on the distant machine.


Then try to use NX client on my local dekstop to dial into the distant computer 
desktop.


I wondered if people realize that these virtual machines are indeed virtual full 
computers with ram and cpu etc. Your own software tools can be installed and run
and the machine remembers it's state on power down. You get a reasonable CPU of
1.2ghz zeon  (dual core) and 700 of ram.


It  is a virtual computer.


The fact they are called servers is interesting. But they can do a lot more than
serve data  (if i can get it going)


Basically they are like running Virtual Box on some real computer some place. Say then offerring that spare virtual box over DSL to any user who wants to put any operating system in it and use it....(and do what they like)


Amazon loading will make sure that you get exactly what they offer. So they may only
stick maybe 20 instances of virtual box onto real ZEON chio machines (blade boards)


In summary....it just interested me....hope it interests others as a free computer. But bare in mind, you can have many instances of Remote desktop running from your real home machine. You are allowed many instances by Amazon also (VB instances) within your ONE free account. Hence you can have many computers LIVE on your desktop.


I figured it was extra free cpu power.


Now it seems i am just trying to get it BASICALLY working...


thanks


Vince.

---

### Post by brian mcgee on 2010-11-11
I agree, it's an interesting idea. I've not used FreeNX much, otherwise I'd offer some advice. The only thing I'd suggest is to run SSH on an alternate port once you get everything working. This isn't a silver bullet, but it makes trouble less likely.

Based on the FreeNX installation instructions posted earlier, it shouldn't be too painful to get everything running.

---

### Post by wkhasintha on 2010-11-11
Yes, like that but I think it might be already running. I'm having troubles with the first apt-line, it doesn't find the GPG-key but maybe it worked for you.

---

### Post by kesman on 2010-11-11
> **wkhasintha said:**
> Yes, like that but I think it might be already running. I'm having troubles with the first apt-line, it doesn't find the GPG-key but maybe it worked for you.

Hey!
I'm having the same problem. It's because the ppa -repository isn't yet updated for Maverick. There's another NX which you can download from [www.nomachine.com](www.nomachine.com) that are tested to work with maverick and are supposed to be easier to configure.
To download something from shell, you can use
```
wget http://url.to.the.desired.file
```

---

### Post by vinceCOOK on 2010-11-11
Hello,

Hello again....

Uh...not got much luck here. It is not working.

Just have not found any good descriptions "or how to's....".

will keep reading this thread.

here are some videos....

[http://www.youtube.com/watch?v=ZAB8wCg9MyE](http://www.youtube.com/watch?v=ZAB8wCg9MyE)  (Lin)

[http://www.youtube.com/watch?v=ftsN_L3ljk4](http://www.youtube.com/watch?v=ftsN_L3ljk4)  (RD on windows)



thanks

Vince.

---

### Post by vinceCOOK on 2010-11-11
Hello

[http://alestic.com/](http://alestic.com/)

this is the ubuntu OS image that  can be put into an amazon
virtual micro server instance.  (free)

hope this helps folk if they are interested.

Vince.

---

### Post by wkhasintha on 2010-11-11
vinceCOOK bro

Use [IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG] button to reply someone's post.

---

### Post by vinceCOOK on 2010-11-11
> **wkhasintha said:**
> vinceCOOK bro

Use [IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG] button to reply someone's post.

Ok...never understood how to use these forums...

did you have any luck getting the FreeNXdesktop remote
thing working...?


thanks

Vince.

---

### Post by outleradam on 2010-11-11
Try this..

```
 sudo apt-get install fluxbox x11vnc ssh tightvnserver
reboot
```

Log back in and ```
X11vnc &
tightvncserver
```

Now using a VNC client log into yourVirtualMachineIP:0. And if ip:0 fails then try ip:1

That should get you desktop access.

---

### Post by vinceCOOK on 2010-11-12
> **outleradam said:**
> Try this..

```
 sudo apt-get install fluxbox x11vnc ssh tightvnserver
reboot
```Log back in and ```
X11vnc &
tightvncserver
```Now using a VNC client log into yourVirtualMachineIP:0. And if ip:0 fails then try ip:1

That should get you desktop access.

Outleradam,


OK thanks, i will try this.


It is a bit of an obsession with me...getting these distance virtual machines up and running at Desktop level.


I just find it interesting that you can potentitally tap into free computers and free cpu power. With a 20 meg broadband line it's practical. (i feel)


Also , it's just a free swrvice isn't it. Free space and things...features....resources...even free APPS that are installed and ready to go.


The distance box is an Ubuntu Maverick Mearcat 10.10 box.


I will look for a youtube VNC video. The videos i found earlier in this post, were pretty good, but not perfect.


Outeradam, did you try any of your ideas yourself?...Amazon machines only require a credit card to get the free ONE year offers. (You are not charged and can cancel at any time)


Other wise you can choose more powerfull machines...at like 3 cents per hour or quad core machines at like 10 cents per hour.  (just found it interesting)


The MICRO instances are FREE for one year. There are windows IMAGES and ubuntu images that can go into the micro instances.


You can check that you have not spent anything by looking at account balance....in your Amazon account.


Other useful stuff is earlier in this thread. Web addresses and stuff.


Will let you know what happened


thankyou,


Vince

---

### Post by vinceCOOK on 2010-11-12
> **outleradam said:**
> Try this..

```
 sudo apt-get install fluxbox x11vnc ssh tightvnserver
reboot
```Log back in and ```
X11vnc &
tightvncserver
```Now using a VNC client log into yourVirtualMachineIP:0. And if ip:0 fails then try ip:1

That should get you desktop access.

Hi


tried all of this.


The commands do work and the ubuntu box goes through the installs....however. it has errors on the VNC part.


You get the large greetings boxes as VNC appears to load and install intself.


But then amidst all of that screens of data....there are errors  "no screens found" error.....and mentions of missing library...


It is ubuntu Maverick Mearcat 10.10


Also, VNC is a bit of a strange piece of software...it did not present me with a gui box to actually try to use the tool.


The "VNC viewer" appeared to show a Graphical box requesting an IP for connecting.....tried every possible IP and your advice and nothing connects.


Other such "remote desktop tools" are easier and show a graphical box for connection....but VNC does not.


i am pretty sure i did everything right.....the commands worked etc and VNC seemed operational


I am wondering if the Ubuntu version is not a "desktop" version.


Alestic.com.......offers the Ubuntu version Maverick Mearcat 10.10.......but they stipulate that for a desktop...you need the "desktop version". Non of them are labelled as "desktop" they are only labelled as "server"


[http://alestic.com/](http://alestic.com/)


[http://alestic.com/2008/04/ubuntu-desktop-ec2#more](http://alestic.com/2008/04/ubuntu-desktop-ec2#more)


And it says you must use Nomachines NX client.


not sure what to try next.


thanks


Vince.


see here






T

---

### Post by outleradam on 2010-11-13
It would be easier to work with if you knew a bit more about what you are doing.  You could always install ubuntu server edtion on a virtual machine (VirtualBox) and then test from there.  This way you could get familiar with a local version rather then learning on a remote version.


If you installed fluxbox and x11vnc, then there should have been a desktop up and running.   What VNC client are you running?  Ubuntu comes with one which is a great client.  You simply click connect with SSH, type tightvncserver.  Then connect with VNC to the IP.Add.re.ss:1    the :1 specifies graphics server 1 which would be the tightvncserver.

---

### Post by vinceCOOK on 2010-11-13
> **outleradam said:**
> It would be easier to work with if you knew a bit more about what you are doing.  You could always install ubuntu server edtion on a virtual machine (VirtualBox) and then test from there.  This way you could get familiar with a local version rather then learning on a remote version.


If you installed fluxbox and x11vnc, then there should have been a desktop up and running.   What VNC client are you running?  Ubuntu comes with one which is a great client.  You simply click connect with SSH, type tightvncserver.  Then connect with VNC to the IP.Add.re.ss:1    the :1 specifies graphics server 1 which would be the tightvncserver.
--------------------------------------------------------------

Hello OUtleradam,

Yes, take your comments on-board.

The thing is, it's taking a longer while now. Many hours effort
and nothing has worked.

Reading the thread, it appears other people are having the same issues....they perhaps know a lot MORE than me about Linux...but are not getting any succcess.

I feel it's more tricky than i had imagined. 

My kind of routine is to give it 2 hour slots of effort...

It kind of looks like the sofware is simply incompatable.

There are error messages. 

Yet the distro version(s) are clear. 

The version(s)of connecting software are clear. The principle
idea is not too difficult to understand. 

I think people don't really know how to do this. Maybe
in the past and on some systems they succeeded. 

The thing is, i have got time to look into it.

was just looking for a quik fix for doing this. This thread has kind of helped somewhat with my understanding.

will have to take another look

many thanks

Vince.

---

### Post by vinceCOOK on 2010-11-13
Found this


[http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/](http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/)




going to try it




Vince.

---

### Post by vinceCOOK on 2010-11-14
Hello People,

Finally, the Linux box remote machine is up and running with a Local GUI Desktop.


see the message just before this one.


That small tutorial worked perfectly.


I have the full Ubuntu distant machine and it's Desktop up and running on my local machine. It works surprisingly fast on a 3.5 meg DSL speed.


So, if you, or anybody is interested, they too will get the Linux box's up and running.
These are free to use. (Micro instances of a Linux machine. You can use them just
the same as real hardware linux box. Install and use tools or whatever)


If you ENABLE cloud watch....you can keep a close eye on your CPU habbits.
You can also look at your amazon account $$$$ to notice costs IF ANY!


------------------------------------------------------------------------------------------------




My two misstakes were my hunches all along....


a) i did not fully understand HOW you gave the distant machine an ACCOUNT and password to use


b) i did not  take the earlier thread advice about installing the Ubuntu desktop. I did have a hunch that the Ubuntu SERVER image was missing something.
(well it was....it was missing the GUI Desktop but i was worried that a large download would cost money at Amazon  (but it does not....you get a bucket full of extras for free including LOTS of download bandwidth)


So thanks everybody for the advice.


For me, it's a small achievement in my world. But you never know where it can lead.  Linux computers to use in this manner, can be handy. 


I would show a screen shot but i don't know how to. Sorry.


I followed the tutoria perfectly. Using the Karmick 9.10 ubuntu version downloaded from canonical as an EBS image.


here is the video on setting up your free "AWS cloud computing account" and using "putty" to get into the "distant Linux box" at termnial level.


 [http://www.youtube.com/watch?v=hJRSti6DsJg](http://www.youtube.com/watch?v=hJRSti6DsJg)


When at that level you can carry out the "second full tutorial" mentioned below...



Below is the tutuorial  on how to get a Desktop Linox box  from Amazon "up and running" in 3 minutes.  (plus 15 minutes downloading/installing)


--------------------------------------------------------------------------------------------------


[http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/](http://aws-musings.com/4-easy-steps-to-enable-remote-desktop-on-your-ubuntu-ec2-instance/)


--------------------------------------------------------------------------------------------------


Karmick Ubuntu image is here


[http://alestic.com/](http://alestic.com/)


-------------------------------


Free amazon distant "micro" instance machines for a year...are here


[http://aws.amazon.com/](http://aws.amazon.com/)  (you first need a normal free amazon.com account)


-------------------------------




thankyou,


Vince.

---

### Post by vinceCOOK on 2010-11-14
Hello People,

As it may help user(s) in userland


The final stages of the previuos thread message instruction.....they require some Vi editing
to change a line of text within a Linux file.


My next thing is to try to  make the Ubuntu's desktop SOUND work correct.




Maybe it needs OSS installed or Pulse audio...?


That would then make it a fully functional virtual computer...!

Thankyou


Vince.

---

### Post by kesman on 2010-11-14
> **vinceCOOK said:**
> 
The final stages of the previuos thread message instruction.....they require some Vi editing
to change a line of text within a Linux file.

You can use nano for editing files, it's a lot easier for just text editing.
By the way why do you put so many lines in your text?

---

### Post by vinceCOOK on 2010-11-14
> **kesman said:**
> You can use nano for editing files, it's a lot easier for just text editing.
By the way why do you put so many lines in your text?



Hello There,


Thanks for the reply. Uh, i put lots of lines to maybe help communication. 


TO be honest (IMHO) i really am not much of a reader....but i kind of like
writing...


Sorry if it's useless info. See, the original early thread was requesting that i DETAIL
any success achieved...(if i remember correctly)


Thankyou


Vincent.

---

### Post by vinceCOOK on 2010-11-16
Hello People,

I was very dissapointed to find that upon successfully using "GUI  desktop Linux machines" in the cloud......that non of these box's  support AUDIO & SOUND?

Basically, this completely cripples these virtual cloud computers with regard to any Audio software tools.

The thousands of free audio tools offerred in Ubuntu are useless on these cloud machines.

Also NO SOUND will come from any web sites or web pages. 

THe machines really are heavily crippled by lack of sound support.


These virtual machines are offerred from the tool called XEN.  XEN does not support
sound cards so there is zero chance of this ever working for the virtual machines users.

I understand that MOST global offices only use desktop computers in a  certain fashion. BUT TO NOT have SOUND is a great waste of resources. 

i was very surpirsed and dissapointed to discover the above. Seems like  such a waste of time NOT having AUDIO/sound in a computer.

just my opinion,

Vincent

---

### Post by brian mcgee on 2010-11-16
I've worked with Xen quite a bit, and although I've never spent much time on sound, my understanding is that Xen supports sound just fine. Perhaps Amazon hasn't implemented certain features, or perhaps VNC or FreeNX or whatever you're using isn't passing through audio as expected.

---

### Post by kesman on 2010-11-17
> **vinceCOOK said:**
> 
I understand that MOST global offices only use desktop computers in a  certain fashion. BUT TO NOT have SOUND is a great waste of resources. 
i was very surpirsed and dissapointed to discover the above. Seems like  such a waste of time NOT having AUDIO/sound in a computer.

I disagree. The remote servers are rarely used for desktop use, hence removing the need for sound.

---

### Post by vinceCOOK on 2010-11-17
Hello


Somebody on the thread in the other forum over in asia or someplace was saying that XEN does not support sound cards. (i will have to check this)

Just one forum post at amazon says they had sound working in the Fedora Desktop AMI.... but it was not perfect sound and it was an extremely oblique way of achieving it. They were using pulse audio and esd.

I would still like to get sound working....but it could be extremely difficult...

i am now running the Ubuntu Lucid 10.04 cloud machine.
 
There is a small caviet in the earlier instructions and you solve it by downloading the file with "wget" as advised. Then you follow the instructions. It works giving you Lucid 10.04 LTS.

please can you tell me how to use Vinegare on the ubuntu Desktop?

Vinegarte is in the ubuntu menu and says it is a "remote desktop connection" tool?

It says you can use either SSH or VNC with Vinegare. (to achieve a remote gui desktop connection)

I have many cloud machines at amazon. 

These machines already have SSH installed and running. Is SSH enough to get a remote desktop connection? or do they also need VNC?....(tightvncserver)?

thanks for any advice,


Vince.

---

### Post by vinceCOOK on 2010-11-22
Hello

Did anybody try the free remote Linux machines.....(desktop level)


Currently, it is prooving difficult to run 2 or more remote desktop sessions at the same time.


Presumably you can use several "instances" of the same amazon machine image. (ami)


But NX client does not seem to like the authentication when you try to log into
all 3 of them. It works fine with just a single desktop.


Three or more desktops should be simple to do. It probably is. However, it is not explained anyplace how to run 3 concurrent desktop sessions. 
using NX client.


Even just ONE desktop that could be switched from linux box ...to linux box...linux box
would be ok. 


"Sessions" is the answer maybe?


i will keep trying. The idea here is to have those 3 "free" computers at my disposal
from the same screen, at the same time  (more cpu power for work etc)





thanks


Vincent.

---

