---
title: "Ubuntu dailup server for dreamcast"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by agem on 2007-08-22
I've come across this page [www.kinox.org/articles/linuxdc.html]("http://www.kinox.org/articles/linuxdc.html") on howto setup up your linux box as a dailup server for your Dreamcast. It's based on Slackware with Linux Kernel 2.0.38 and I'm wondering how I would go about doing this with Fawn?

There are still a few titles that are working online with the the Dreamcast and would love to give them a go.

Any help please?

---

### Post by Ryochan7 on 2007-10-04
How is your progress? I just recently got back into the Dreamcast scene and I got a working PC-DC server set up on my Ubuntu Feisty box. If you still need help, I can possibly help out but I don't know if you would be paying attention to this thread anymore. The one thing that I will mention that you might have read already is that you need to have a voice modem for your PC.

---

### Post by agem on 2007-10-06
Hey Ryochan7, yep I'm still interested. 

I do have an external voice modem for me setup. Any help getting my DC online would be great. Plus I reckon a lot of other peeps would be interested as well.

---

### Post by Ryochan7 on 2007-10-10
I don't exactly how much work I did to set up my PC-DC server because I had looked through a lot of guides to get things sorted out and working; I was thinking about making the server again under a fresh install of Ubuntu and trying to document what I had to do but I probably won't have the time for that. However, I will try to help as much as I can.

First off, a guide that worked better for me was [http://ragol.homeunix.net/](http://ragol.homeunix.net/). The guide should cover most of what you will need to get started. For your Dreamcast, you should try to connect to the Internet with Planetweb before you try connecting to a game as connecting to most games will require much more work to start. The version of the Planetweb browser that you have shouldn't matter but, like most guides, I would recommend that you have version 2.0 or greater.

The two key packages that you will need installed on your system will be mgetty and ppp. I didn't have to edit my mgetty config files but I had to edit some of my ppp config files. Here are some links to the config files that I had to edit:

[http://bored.homelinux.net/stuff/etc/ppp/options](http://bored.homelinux.net/stuff/etc/ppp/options)
[http://bored.homelinux.net/stuff/etc/ppp/options.ttyS0](http://bored.homelinux.net/stuff/etc/ppp/options.ttyS0)
[http://bored.homelinux.net/stuff/etc/ppp/pap-secrets](http://bored.homelinux.net/stuff/etc/ppp/pap-secrets)

Look through the guide to find out which portions of those files you will need to change for your network.

Some notes about my setup that are not a part of the guide are that I don't use the inittab method for launching mgetty that is used in the guides and a note about ip forwarding. Instead of the inittab method used in the guides, I launch mgetty via a terminal with "sudo mgetty -D /dev/ttyS0". You need to enable ip forwarding on your Ubuntu system in order for your Dreamcast to access any outside IP address. I do this by enabling the ktune option in the /etc/ppp/options file.

Let me know how far you get and I will try to help out if you get stuck somewhere. Later.

---

### Post by Ryochan7 on 2007-10-19
My current setup does not work with Gutsy. My Dreamcast can establish a connection with my PC modem and mgetty does catch the call but the Dreamcast can't log in to my box. The connection just hangs at that point and it looks like my ppp config needs to be changed or something. I will post an update once I get it working on Gutsy. I first plan on getting a PC-DC server set up on my Debian Etch server and just use that for a while since I will probably have an easier time getting it working on that.

---

### Post by Ryochan7 on 2007-12-15
After doing a fresh install of Gutsy, I was able to easily get my PC-DC server working again. I was busy with school and other things so that is why it took me so long to get things working again.

---

### Post by celticninja on 2008-01-31
When doing this did you ever incur, a "no answer to this telephone number" ? and if so what did you do?

---

### Post by Ryochan7 on 2008-02-02
I haven't gotten that message since I got the PC-DC server working. That error that you posted could be because of many problems but the most likely would be that:

- There is no power between the Dreamcast modem and your PC modem.
- You have an incompatible modem for your PC.
- You aren't initializing the modem fast enough and the phone call does not get answered.

The first issue usually comes with trying to do this with a Winmodem. To get this working with a Winmodem, you would have to make a line voltage inducer so that there is power between the Dreamcast modem and your PC modem as the Dreamcast modem relies on the power coming from your phone line in order to function. A good resource for instructions on how to make a line voltage inducer can be found at the following link.

[http://dreamcast.onlineconsoles.com/phpBB2/guides_pcdcwin98.php#10](http://dreamcast.onlineconsoles.com/phpBB2/guides_pcdcwin98.php#10)

I use an external serial modem for my setup. The modem that I am using is a TRENDnet TFM-560X (NewEgg link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)). Typically, external modems will provide power through the phone line so no line voltage inducer would be necessary; that is the case with the modem that I use.

For the second problem, the main issue will be whether your modem is a voice modem. I am not exactly sure why but you must have a voice modem in order for things to work.

The third issue isn't really a problem as you usually have a good amount of time, even when using a short number, to initalize your PC modem; I have my Dreamcast dial 555. You would wait about 1 second per digit before you attempt to pick up the call; in my case, that would be about a 3 second wait. Also, there is a good window for initializing the modem before the connection can't be made so you shouldn't need to rush things.

That's about all that I can say about the issue without more information. Hopefully, you get things resolved.

---

### Post by Ryochan7 on 2008-05-09
My PC-DC server setup does not seem to work well with Hardy. There are some times when my Dreamcast will connect to my server just fine but most of the time mgetty does not even catch the call. I might have to try to install an older version of mgetty to see if things will work better.

Looks like I will have to start using my Debian Etch box again as a PC-DC server until I get these issues resolved. I should note that I am using a fresh install of Hardy Heron.

---

