---
title: "Can't Connect to wireless after MAC is spoofed."
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by UsernameAlreadyInUse on 2007-06-30
I attempted to spoof my wireless mac address, and after spoofing it, I tried to connect back to my wireless router, and it sits there (the nm-applet icon in the top right corner of the screen) with one light lit up (the bottom one) and eventually prompts me for the wep key, which I give again to no avail. I have watch'ed the iwconfig during this process and I cant see anything out of the ordinary, looks like its trying to connect. I have very briefly tested this with another router and got the same result. The closest post I can find about this is this one: [http://ubuntuforums.org/showthread.php?t=252713](http://ubuntuforums.org/showthread.php?t=252713) which provides no solution.

---

### Post by kevdog on 2007-07-01
How did you try to spoof you wireless card???  I thought in order to do this you had to change an entry in the /etc/iftab file.

---

### Post by UsernameAlreadyInUse on 2007-07-01
well, the first time I tried to spoof it, i used:

sudo ifconfig ath0 down
sudo ifconfig ath0 hw ether 00:11:22:33:44:55
sudo ifconfig ath0 up

to which I ran into "This device is busy". I concluded it was the nm-applet, so I went into the system monitor and killed it, and repeated the the lines to no avail. I now assume ubuntu has other automatic mechanisms in place to set up disconnected wireless(and/or wireless interfaces). So on the hunt I went.

I then discovered this way of doing it:

sudo ifconfig ath0 down hw ether 00:11:22:33:44:55 up

which WORKED! (I may have shut down prior nm-applet, I don't recall) I did the ifconfig and I saw my mac address spoofed. Which I had a little party (had been at it for 3 days... this is now day 5.) So I then tried to reconnect via nm-applet to my wireless router, and the first light lit up, and sat there, until it went out and then I got prompted for the encryption key which I have been on this wireless for some time now. Regardless, I put it in, to no avail. After that didn't work, I broke out an old router, and plugged that in so I could do an unencrypted test. It just sat there until it gave up connecting.

The third way is pretty much like the second, accept I found an app called macchanger, and gave that a go. same result.

prior to all of this I did toy around in iftab (mostly guessing) which produced no good results. I also changed my things in /etc/networks/interfaces (or something like that). If you want, I will go back and try and track down as close as possible what exactly I did, but that would take some work, I've since changed it all back. I know in iftab, I just simply changed the mac, and when i booted up, my mac was my original mac. One thing I haven't tried is config'ing the iftab and then spoofing... but I figured before i start running around messing up my ubuntu box further, I should ask.

Questions? Comments?

---

### Post by UsernameAlreadyInUse on 2007-07-02
I remember reading a lot about Trusted Computing a while back, and it seems to me that I recall reading something that referenced the ability for MAC addresses to be spoofed and how this can be used to circumvent trusted computing protections and also allow for anonymous hacking and so on and so forth. I did just buy this laptop, could the wireless card be disallowing me to spoof my MAC address in order to obey Trusted Computing rules? It would really chap my *** if I can't do what I want to do, which is not related to hacking at all, because of the paranoia of a few idiots who don't even know how to turn on a computer.

---

### Post by kevdog on 2007-07-02
Im out of ideas on this one.  If you find out how to do it, please post back, Im curious now!

---

### Post by UsernameAlreadyInUse on 2007-07-03
Well... the plot thickens. I went to the ASUS website (the brand of the laptop) to download my laptop hardware specs so I could do some googleing on the wireless card. Rummaged through their site, found the right PDF (out of about 20 different languages... just fyi) and downloaded it. Tried to open it and it was PASSWORDED! Now one might dismiss this wondering who at asus doesn't know what their doing, but then I remembered another blurb about trusted computing. Which grants the ability to "sign" documents with an encryption that only other activated (and im sure WGA'ed) windows computers can open. So I sent it to my friend using windows who opened it without a hitch. This is absolutely ridicules: disallowing me to open up documentation CONTAINING INFORMATION ON THIS DEVICE because I'm not using a specific OS?

Angry rant aside, I cannot find what wireless card I have in this laptop. I installed wine, and ran acrobat, after some toying, I got it to run, and the PDF opened fine. The PDF is written for a 3 year old child who has never seen a laptop before in his or her life. I am not kidding. It does not list any hardware information about this laptop, only paragraphs and diagrams about how its not wise to shower your laptop. Good to know, because I so had a romantic evening planned for the laptop and yours truly. Man the way this sexy thing starts up with that little Asus chime, is enough to drive any hard core geek wild. When its really late a night and were alone... oh yeah... anyways... I still have no idea whats going on, I will be hunting for the laptop book to see if by chance they decided to stick some random information in there, like what hardware is in this laptop.

Anyone with any ideas? I'm clean out.

---

### Post by Qodosh on 2007-07-04
I have the exact same problem. I am running Ubuntu. And I have a Toshiba Satelite Laptop. I can get the mac address to change if I shut down the interface first and then change it, and then start it up again. But I cant connect to the LAN.  If you find anything out let me know!

---

### Post by UsernameAlreadyInUse on 2007-07-04
Qodosh, can you please tell me what the exact model of your toshiba laptop is? Also if you can, can you tell me what exact wireless card is in it?

---

