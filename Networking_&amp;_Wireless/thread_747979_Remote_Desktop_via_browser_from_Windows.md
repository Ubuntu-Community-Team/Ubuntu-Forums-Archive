---
title: "Remote Desktop via browser from Windows"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by jcr1 on 2008-04-07
Hi all,

I remember once (many years ago) a linux user showing me on my own XP machine that he could login to a linux machine via the internet just through my own web browser. He didn't need to install anything on my machine.

How can I do this? Sometimes I would like to access my ubuntu machine at home from my works XP machine where I can't install any software.

Is it possible?

Cheers,

Jon

---

### Post by ginge6000 on 2008-04-07
[www.logmein.com](www.logmein.com)

Scrap that, it doesn't support Linux (note to self - read message before posting!)

---

### Post by superprash2003 on 2008-04-07
yes.. for that you need to run an apache webserver and enable remote desktop on your pc and use a java script

---

### Post by jcr1 on 2008-04-07
<insert blank clueless expression>

Not entirely sure what you mean superprash2003? Can you elaborate or point me somewhere to read up?

Many thanks,

Jon

---

### Post by superprash2003 on 2008-04-07
since you want to access your computer from a browser.. it must be on a website.. this website has to be hosted by you in your computer.to host a website you need a software called apache .. you can install apache using the guide here [http://ubuntuguide.org](http://ubuntuguide.org) .then you need to enable remote desktop system->preferences->remote desktop .. and you need to open port 3389 in your modem so that you will be able to access your machine from the internet.Then you will need to place a javascript in your website which you created using apache..i will insert the javascript in here after you setup apache and remote desktop

---

### Post by prshah on 2008-04-07
> **jcr1 said:**
> 
I remember once (many years ago) a linux user showing me on my own XP machine that he could login to a linux machine via the internet just through my own web browser. He didn't need to install Jon

Yes, you can do this with VNC, which is free and OSS.

After setting up VNC on your local machine, you can access it remotely through any java-enabled browser.

Note that if you have a dynamic ip address, you will have to subscribe to dyndns.org (also free).

---

### Post by prshah on 2008-04-07
> **superprash2003 said:**
> since you want to access your computer from a browser.. it must be on a website.. this website has to be hosted by you in your computer.to host a website you 

Nope. You're completely off the track. What he needs is VNC.

---

### Post by christianxxx on 2008-04-07
> **prshah said:**
> Nope. You're completely off the track. What he needs is VNC.

First thing I thought about was something similar to a webbased ICA-client. I've seen this before, and surely it requires a webpage (although not nescessarily a webSITE).
But for connection to a Linux-machine, I don't know if this will work...

---

### Post by jcr1 on 2008-04-07
OK...will do a bit of reading up and try and understand it a bit more... Trying to get my head around the concept of my computer being on a website...I know it isn't literally on a website, but ....

Is this also something I can set up on my existing std desktop install of ubuntu, i.e. nothing like installing the sever edition etc? 

Cheers,

Jon

---

### Post by superprash2003 on 2008-04-07
well i think you do need apache..and i'm not off track , im sure about that cause i run this setup!!!there probably are other ways..i'm just helping him with this way..

---

### Post by superprash2003 on 2008-04-07
yes you definetly can do it with the desktop version

---

### Post by jcr1 on 2008-04-07
Hmm... quite a few replies whilst writing my previous one lol...

Ok so I shall also read up on VNC.

How do I determine the issue with the dynamic IP address?

Thanks again!

Jon

---

### Post by jcr1 on 2008-04-07
Uh oh...now which route do I go down?

---

### Post by superprash2003 on 2008-04-07
since your ip keeps changing you can get a free domain like myname.no-ip.org or myname.servehtp.com so this domain name will always point to your computer even if the  ip keeps changing!! [www.no-ip.com](www.no-ip.com) and [www.dyndns.org](www.dyndns.org) provide this service

---

### Post by prshah on 2008-04-07
> **jcr1 said:**
> OK...will do a bit of reading up and try and understand it a bit more... Trying to get my head around the concept of my computer being on a website...I know it isn't literally on a website, but ....


IT HAS NOTHING TO DO WITH HOSTING A WEBSITE.

Sorry about that; made me feel better.

You can run your ordinary ubuntu desktop and install vncserver with the command ```
sudo apt-get install vncserver
``` which will also install vnc-java which will allow you to connect to your computer remotely using ANY java supporting browser.

VNC is easy to setup and use; for a quick, fast and dirty grounding, visit [www.realvnc.com](www.realvnc.com), but DONT install that; use the command I have given above instead.

---

### Post by jcr1 on 2008-04-08
Ahh thank you prshah, that website helped a lot!

I can give it a go now.

Thanks everyone.

Jon

---

### Post by jcr1 on 2008-04-15
OK, so I got myself registered with no-ip.com so I have a domain name.no-ip.com resolving a certain ip address (not sure where that came from)

I installed vncserver and vnc-java

I ran vnc...it asked to create a password, i did....then what?

What do I do next? specifically...how do I now go abouot logging onto my machine from a remote location via a browser?

I guess I need to configure vnc and somehow link it to that no-ip thingy?

Thanks in advance.

---

### Post by jcr1 on 2008-04-15
To add to this...

I thought I would just type in the <name>.myvnc.com in a browser to see what happens...

It throws up a login window for netgear...which I believe is my router! It is my router...I typed in the usr and passwd for my router and I get through to it!!

This is not good as it is a generic username and password that I did not set...

A little concerned now!!

Plus...how is this getting me to running my desktop?

---

### Post by jcr1 on 2008-04-15
ok solved the access to my router...I could change the password!

---

### Post by prshah on 2008-04-16
> **jcr1 said:**
> 
I thought I would just type in the <name>.myvnc.com in a browser to see what happens...
It throws up a login window for netgear...which I believe is my router! It is my router...I typed in the usr and passwd for my router and I get through to it!!
This is not good as it is a generic username and password that I did not set...
A little concerned now!!
Plus...how is this getting me to running my desktop?

You have to enable a DMZ (passthrough) in your router. Essentially, you have to tell your router to pass information _from_ the WAN (Internet) to a particular host ("DMZ host") on your network. The "host" address will be the LAN ip address of the machine that is running vncserver. 

I cannot tell you EXACTLY how to setup the DMZ host in your router; it varies from brand to brand and model to model. Typically, look for "DMZ host" and you should be good to go. Or Netgear has excellent free support.

Once you do this, your earlier web address will connect to your vncserver rather than your router.

---

### Post by jcr1 on 2008-04-16
Many thanks again. Will check it out tonight. 

I tried to connect from work today (even if it is just to the router for now) and it timed out. Could this be something to do with work's security or something else? My main interest in this is to access home from work. I have no admin control in work.

---

### Post by jcr1 on 2008-04-16
ok...I enabled DMZ in my router...put in the ip addy of my computer (i think) by looking at "attached devices" in my router and putting in the ip addy it had there for my laptop.

Now when I go to <name>.myvnc.com address it just goes stright away to "unable to connect"

Is this because I have done something wrong...or because I can't connect to the machine I am working on?

---

### Post by prshah on 2008-04-16
> **jcr1 said:**
> ok...I enabled DMZ in my router...put in the ip addy of my computer (i think) by looking at "attached devices" in my router and putting in the ip addy it had there for my laptop.
Now when I go to <name>.myvnc.com address it just goes stright away to "unable to connect"
Is this because I have done something wrong...or because I can't connect to the machine I am working on?

OK forgot to mention this; you have to also open the relevant port; for vnc it is 5900. Again, more background information on 
[www.realvnc.com/support/portforward.html](www.realvnc.com/support/portforward.html)

And also make sure that vncserver is running.

---

### Post by jcr1 on 2008-04-16
OK am getting a bit lost with the setup of the router...

I don't know if I did the no-ip right

How do i know if vncserver is running...i open a terminal and enter vncserver...all looks ok, but nothing opens...nothing shows in the taskbar...how do i check its running?

In my router I have remote management....dmz server....cant find port forwarding...

Eek bit lost.

---

### Post by prshah on 2008-04-17
> **jcr1 said:**
> OK am getting a bit lost with the setup of the router...
I don't know if I did the no-ip right
How do i know if vncserver is running...i open a terminal and enter vncserver...all looks ok, but nothing opens...nothing shows in the taskbar...how do i check its running?
In my router I have remote management....dmz server....cant find port forwarding...
Eek bit lost.

OK lets take it step by step. Forget the no-ip part for now. 

As you said, in a terminal, give the command vncserver. Leave the terminal open.

Then, open the website "http://www.whatismyip.com" that will tell you what your external (Internet) IP is.

Open a browser, and type the following in the address bar:
```
http://xxx.xxx.xxx.xxx:5900
```

where the x's are replaced by your ip address. If that works, then your setup is OK, just need to work on your no-ip.com stuff.

If it doesnt work, try ```
http://127.0.0.1:5900
``` in your browser bar.

Post back results here.

---

### Post by jcr1 on 2008-04-17
Thanks for the reply. Will try that when I get home tonight.

---

### Post by cozmicharlie on 2008-04-17
Just wanted to jump in and let you know I used superprash2003's method (running vnc through Apache) and it worked great.  Very simple, it took me about 15 minutes and I have a remote desktop I can access from the web.

Thanks superprash2003 for your help.

---

### Post by jcr1 on 2008-04-18
Both return "Unable to Connect".

---

### Post by prshah on 2008-04-18
> **jcr1 said:**
> Both return "Unable to Connect".

Ok considering the previous post, maybe you should try superprash2003's method. 

In the meantime, I will be setting up vnc myself over the weekend. Maybe I can let you know how it goes.

---

### Post by jcr1 on 2008-04-19
When running the test page on vnc website I get this:

> The IP address requesting this web page is xx.xxx.xxx.xxx (REMOTE_ADDR)

Connecting to port 5900 ... succeeded.

Waiting for server to send version string... failed: (111, 'Connection refused') 

So it seems to be the right ip addy, port 5900 connects (could it do this even if port forwarding wasn't enabled?)

---

### Post by jcr1 on 2008-04-19
When I run 'vncserver' from a terminal, what should happen? Shoud some app open, of an icon appear in the taskbar? Nothing seems to visually let me know its running.

---

### Post by jcr1 on 2008-04-22
> **prshah said:**
> Ok considering the previous post, maybe you should try superprash2003's method. 

In the meantime, I will be setting up vnc myself over the weekend. Maybe I can let you know how it goes.

Any joy setting this up at the weekend?

---

### Post by prshah on 2008-04-23
> **jcr1 said:**
> Any joy setting this up at the weekend?

Yes, I got it working; after a fashion. I noticed that I was getting font "fixed" errors- font not found. Using the -fp (font path) switch, I got vncserver loaded and working with the command ```
vncserver -httpport 8080 -fp /etc/X11/fonts
``` Note that this is not the exact command, (not at my home machine now), will give the exact command later today; but this is close enough.

Now, I can access my machine through both vncviewer as well as the browser, but: I get only a blank "X" screen, no window manager/desktop manager. Apparently the vncserver sets up a whole "new" X server on display :1

I have yet to figure out how I can get it to access my :0 display.

But I'm getting there.. slowly.

---

### Post by jcr1 on 2008-04-23
Cool, well let me know how it goes...I'm at a bit of a loss. 

In the meantime I might try that other apache method...thats if I get the time, which is unlikely.

Thanks for your help though!

---

### Post by jcr1 on 2008-04-23
I would do a thankyou thingy, but can't see how to lol

---

### Post by prshah on 2008-04-23
> **jcr1 said:**
> I would do a thankyou thingy, but can't see how to lol

The exact command ```

vncserver -fp /usr/share/fonts/X11/misc -httpport 8080 :1
```

Wish I could be of more help; no thanks required till it's done!

---

