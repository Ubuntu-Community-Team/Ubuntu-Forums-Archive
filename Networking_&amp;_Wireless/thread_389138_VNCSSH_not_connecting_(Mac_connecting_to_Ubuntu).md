---
title: "VNC/SSH not connecting (Mac connecting to Ubuntu)"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by marko_4454 on 2007-03-20
Hello I am having problems trying to connect from my MAC (macbook) to my linux ubuntu desktop. I at some point would like to connect from the "outside network" (not 192.168.XX.XX) but as of now, I am trying the internal network only for simplicity.
I would like to be able to control my ubuntu computer with my mac. So pretty bunch VCN.


This is what I have done already:
-enabled port forwarding in sshd_config
-enabled remote login in my mac from the sharing folder
-enabled remote login in ubuntu

**I can connect to my computer (linux) but I cant really do anything.**

I will tell you my steps:
1) [mac] $ ssh -X [email]user@192.168.X.XX[/email]
2) It saves the fingerprint and gives me my prompt.
3) echo $DISPLAY gives me localhost:10.0
    ---During this stage, I cannot do even "xclock" since it gives me "Error: Can't open display: localhost 10.0"
4) If I try to startx in my mac while connected to my ubuntu computer, the ubuntu computer flashes and **logs in as another display**. To access it, I just press Ctrl+Alt+F9 and my current one is in the usual ctrl+alt+F7.
While opening the new display though...I get a bunch of errors:
```
vncext: VNC extension running!
vncext: vncExtinit: unable to bind listeing socket: Address already in use.
**many of these-->**Error opening /dev/wacom: No such file or directory
```
There is no graphical interface for mac.
I ctrl+c in my mac and the display shuts down

Any hope for me? I would eventually like to VNC from the outside network, but as of now, I would like to control my computer from my laptop using a graphical interface. am I taking the wrong approach of something?
-Thanks,
marco

---

### Post by marko_4454 on 2007-03-20
I forgot to say that I have beryl, so my display is different than the default one (I use XGL login)

---

### Post by marko_4454 on 2007-03-22
can anyone help me?

---

### Post by silverhack on 2007-04-08
I just found this thread while I was googling.  I'm setting up the same type of thing - remote X11 from my Mac to my Ubuntu system.  I just installed Fiesty Fawn last night and it's working great.  I got this working by using Ubuntu's remote desktop sharing (see  [http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)  for more help with that - but it's so incredibly easy to set that up).

Once you have the remote sharing turned on, try it out on the Mac.  I use 'Chicken of the VNC' and just put in the IP address of my Ubuntu system and the password I put in for the Remote Desktop.  Bingo!  it just worked!  it was super incredibly easy!

Once you have it working over the LAN, to get it to work from anywhere I use SSH tunelling.  This means you have to setup SSH on your ubuntu system (do 'sudo apt-get install openssh-server' from the command prompt to install it - that's all).  Once ssh server is installed, test it out on your lan from your Mac by opening up the Terminal and do 'ssh username@Ubuntu-IP-address'  (eg 'ssh adam@192.168.1.22' or something like that)

If you can use VNC and also SSH on the LAN - get it working over the Net.  You'll have to setup your router to portforward TCP port 22 to your Ubuntu system.  Once that is done, you should be able to SSH into your Ubuntu system from anywhere.  If you can SSH in, then try to setup the SSH tunnel and use VNC.

To make things easy, I setup a dynamic DNS for my Ubuntu - that's another story (but very easy to do)
To do this:
1) setup the SSH tunnel on the Mac.  Open the terminal again and do 'ssh [email]USER@YOUR.INTERNET.IP.ADDR[/email]ESS -L5900:localhost:5900'  and you should be connected to your ubuntu system.
2) startup the VNC client (again, I use Chicken of the VNC) and have it connect to 'localhost' or '127.0.0.1' and be sure to put in your Ubuntu remote desktop password and hit connect.

That should do it!  It was EXTREMELY easy for me to get this going.  Good luck - maybe this is a really old thread and you don't need this any more, but maybe it will be helpful for another googler.

---

### Post by silverhack on 2007-04-08
Here's some more info for you too...


[http://ubuntuforums.org/archive/index.php/t-11808.html](http://ubuntuforums.org/archive/index.php/t-11808.html)

---

### Post by marko_4454 on 2007-04-08
THanks silverhack!!
I will try that in a while. I also updated to Feisty a couple of days ago, so we are in the same page :)
I also lost XGL/Beryl and have no time to bring it back. But it will be back ;)

---

### Post by russbuss on 2007-05-23
Have you been able to get this to work while running beryl?  In one of your earlier posts, you said that you were.  But, then you said that you had just upgraded to Feisty, so perhaps you aren't anymore.

I can successfully vnc into my ubuntu machine from my mac, but if I have beryl running, the display I get is frozen and unresponsive.  This seems to be a known bug involving beryl and ubuntu's default vnc.

I'm just wondering whether you've discovered a workaround for getting beryl and vnc to be happy together.


Thanks.

---

