---
title: "Ready to go got my disc today but....."
date: 2009-07-02
forum: New to Ubuntu
---

### Post by richie1913 on 2009-07-02
Hello again everybody,you will all be pleased to hear that I received my Ubuntu 9.04 Disc today,I have yet to Install It as I have been playing around on it using the demo option,first Impressions are amazement.I was always told that windows good linux or ubuntu bad,linux Is slow and complicated etc etc...Well now that I have actually tried It for myself I am very pleasantly surprised,I really was not expecting menus and windows,(I always had a picture of a blank screen with just a flashing cursor blinking at you),so that part of Ubuntu I found pretty easy to use saying that,I now need help as I cant get my Internet to work.I use a usb dongle from 3 on payg also got a vodafone one but 3 is slightly better so use that the most,If I plug the dongle in nothing happens(the software and drivers are on the dongle for windows and mac osx10.4.11/10.5.2 If thats any help) so I have created the network connection manually but cant find any way of actually telling it to connect.So I was hoping If there was anyone out there that could help me out.Also before I Install Ubuntu would It be better to format the harddrive with something like D-Ban to get rid of windows once and for all.Thankyou all very much and speak to you all again soon.
Richard:lolflag:

---

### Post by WinterWeaver on 2009-07-02
there should be a little networking icon top right. (called the network manager).
left-click, and select the connection :)

---

### Post by Hospadar on 2009-07-02
Have you looked in "network-manager"
It's the little icon in the tray where you pick wifi-networks, etc.  I think if you right-click it and go to edit or add connections (I'm in kde at the moment so I can't say for sure) you'll get a window that looks like this:
[https://help.ubuntu.com/community/NetworkManager0.7#Connection%20Types](https://help.ubuntu.com/community/NetworkManager0.7#Connection%20Types)
and you should be able to set up the connection from there.
I've never personally set up a wireless usb modem like that, so I can't say for sure, but I hear they tend to work pretty well.

That page I linked should help you get started with network manager.
If  you try googling your model number and "ubunut" or "linux" I bet you'll find all kinds of guides and forum threads.

---

### Post by The Cog on 2009-07-02
It might be necessary to reboot with the wireless dongle plugged in for it to be recognised. 

Some wireless chipsets aren't recognised by Linux anyway. If you can't get to see the local networks, try and post the output of these comands: They go in a command prompt, Accessories->Terminal, and you may need to copy/paste the output to a file on a USB stick so you can post it using windows:
[b]ifconfig
iwconfig
lspci -v[/b]

---

### Post by richie1913 on 2009-07-02
Hi all,Winter Weaver  and Hospadar tried that but no sign of my connection.
Hi Cog,the problem I have Is that I am playing around in demo mode at the moment,so If I reboot you know what I mean It will just start in demo mode again,so It Is most probably this that Is causing the problem,but the problem I have Is I dont want to take the plunge If I cant get the usb dongle to work,but I think from what you have said and reading in between the lines the dongle should work,I just need to set it up correctly,could anyone confirm that the payg usb dongles work correctly in ubuntu.Thanks

---

### Post by The Cog on 2009-07-02
Well, boot it with the dongle already plugged in, just in case. Then look for the wireless network widget top-right and see if you can see any networks. If not, post the output from the commands I gave earlier and we can see how much is working and whether you have a chipset that is known to be supported or not. I agree that there's no point trying to install any extra drivers etc. if you're only running from the live CD.

---

### Post by richie1913 on 2009-07-03
Hi The Cog sorry It has took so long to reply but I decided to take the plunge and Istall Ubuntu,same situation everything seems to be working OK but cannot get the dongle working,I have rebooted with the dongle In and have also Inserted the dongle while Ubuntu Is running nothing happens,so I ran the commands you asked me to two of them worked but ispci-v came up as bash,here are the results of.....
ifconfig.
eth0      Link encap:Ethernet  HWaddr 00:40:2b:25:f3:b2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4592 (4.5 KB)  TX bytes:4592 (4.5 KB)
Here are the results from iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

I am totally lost here the dongle Is a 3 usb mobile broadband ZTE MF627 ON PAYG If I cant get It to work I wont have Internet access and will have to go back to windows which I dont want to do so hoping you will be able to help.
Thanks.

---

### Post by caravel on 2009-07-03
Post output of lsusb

There is no easy "plug and play" solution for this device yet - read this thread containing a possible solution:
[http://ubuntuforums.org/showthread.php?t=1065934](http://ubuntuforums.org/showthread.php?t=1065934)

---

### Post by t0p on 2009-07-03
I noticed you say the dongle is a ZTE.  What is the Vodafone dongle?  Is it made by Huawei?  Vodafone may have rebranded it.  If it's called a K3520, it is actually a Huawei E220 (or E120... can't remember).  If it's called a K3565, it's actually a Huawei E160X.

The point of the question is that the Huawei dongles work just fine with ubuntu's Network Manager.  Plug it in and an assistant will pop up offering to set up a mobile broadband connection.  Answer the questions (what country you're in, which mobile service provider you're with) and hey presto!  Connection established!  So it may well be a good idea to check out your Vodafone dongle.

There's also an app [here]("https://forge.betavine.net/frs/?group_id=12") which enables connection - it's called the Vodafone Mobile Connection Card Driver for Linux.  Don't be put off by the fact that the word "Vodafone" is in the name - the tool is being developed by/for Vodafone, but in fact it works with *any* provider's dongles.  The program's a bit hit-and-miss, but it allows you to use the dongle's sms functionality (something Network Manager can't do) and keep track of data usage (ditto) as well as connect to the internet.  So I reckon it may be well worth a try.

---

### Post by richie1913 on 2009-07-03
Hi Caravel,tried the command Isusb and it comes up  as bash,also had a look at the link you provided and Its way over my head I have never used linux before,so am totally in the dark here.
Hi t0p,thanks I have got to pick my daughter up from school now but when I get back I will give my vodafone one a go,hopefully Its as easy as you say,otherwise I will be looking at taking a step back in eyes and have to put up with windows again for now anyway,Post back and tell in about a hour.

---

### Post by nothingspecial on 2009-07-03
its is lsusb 

It starts with a litte L not a big i

---

### Post by theozzlives on 2009-07-03
It's lsusb NOT Isusb

---

### Post by richie1913 on 2009-07-03
I have'nt got a clue what I am doing but thanks for that will try It again.
TO t0pt,thankyou very much,Vodafone accepted and I am now on the Internet,now I can get my learning head on and get to grips with this.Thank-you again,I will use my 3 dongle for my other windows based comp.

---

