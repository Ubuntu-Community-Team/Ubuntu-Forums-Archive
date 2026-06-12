---
title: "Cant seem to get Webcam working on HP 6735s"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Zeptinune on 2010-02-24
Hey guys me again come to annoy you :D

I've been having a good time with my lovely new linux laptop. But I just realised that the webcam doesn't work. I've gotten around the bug with the wi-fi not working and I've done a lot of tweaking and working out myself but at the moment I can't seem to get this webcam working.

It says [here](http://www.linlap.com/wiki/hp-compaq+6735s) that I can use my webcam with the [UVC Driver](http://linux-uvc.berlios.de/).

I went [here](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) and I followed the instructions from: [3 Build and Installation Instructions]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Build_and_Installation_Instructions") to *First Use: Out with the Old, In with the New*

I did a re-start and well I can't seem to get my cam to work... it works when I use something like GUVC View. But apart from that it wont work in aMSN and other things like tinychat and meegle think my cam is disabled..

Any help? Is there a way to check if my cam installed successfully or did I totally miss something here..? I'm such a noob at all of this.

---

### Post by Temposs on 2010-02-24
Sometimes a webcam just won't work with every program in linux. It's not usually much use asking folks about a specific webcam because there are so many different ones and they all act differently. You said you got your webcam working in some programs, so it does work, as was promised in the tutorial you followed. There wasn't any mention of it working on specific applications, just that it worked at all.

Did you check your specific webcam device id at [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) ?

If you don't know how to find it, you should just be able to do:

```
lsusb
```

And then match the code it tells you for your webcam with a code in the supported devices list. See if it says it's completely supported or if there are issues.

---

### Post by no2498 on 2010-02-24
get 2 programs ( cheese and wxcam ) 1 of the 2 will see it
now open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2 click the bottom test for each
you should also set the plugin to xwindow (no xv)
if cheese brakes it come back an start over
and dont open cheese
cheese has a good help file
my cam opens in more programs than ever before
you may also need a v4l1 to v4l2
im at a loss as to say where to get it
hope this helps some

---

### Post by Zeptinune on 2010-02-26
***04f2:b083*       CKF7063 (HP Compaq 6830s notebooks)       Chicony Electronics       [IMG]http://linux-uvc.berlios.de/ok.png[/IMG]**

Ok so it says my webcam is supported by this driver. But I don't know how to install the driver correctly. I followed this instructions but I think I have to remove the old drivers that it was using before hand (that didn't work at all).

Like I said in my first post, I followed this instructions but can anyone see that I missed anything I was supposed to do?
This webcam works with aMSN but the rest of aMSN crashes every so often and the webcam is mirrored. There isn't an option to change that back either. I want to use emesene with my webcam but it doesn't give me one from the drop down menu I can use..

When I use GUVC my cam works but again, its mirrored which makes everything look really weird. (Not that I really care). I just want it to work.

---

### Post by Zeptinune on 2010-02-26
After doing that 'gstreamer-properties' command I set it to what you said and well when I clicked the 'test' button it worked fine. My cam works without issues, but when I want to go into Emesene to use it, it shows up as CKF7063 which is the name of my Cam, but there is no picture.. and its not automatically selected.

---

### Post by Zeptinune on 2010-02-27
*sigh* Been trying all day today and still no luck, a friend said that Linux Mint would have the drivers already installed, the external cam works ok. But Emesene is still rejecting letting me send it, works in the preview and in the settings... asked on the Emesene forums and still no reply after a few days. ;(

Internal cam is not working at all unless I use UVC Preview or aMsn but then aMsn wont let me use it in a conversation. Starting to think its some sort of firewall issue or I have webcam ports blocked or something. My mind is swimming really, I am almost certain I have the drivers. Both cams seem to be able to work just not when I am in a conversation on Emesene.. ugh. This is such a hassle, everything works flawlessly except for this.

---

### Post by Temposs on 2010-02-27
Yeah, that's why I love my System76 machine. Everything works flawlessly because System76 only builds machines for Ubuntu. None of this hardware incompatibility mess. Your system doesn't work flawlessly because it was built with Windows in mind. 

So, next time you have money for a machine, you may want to research a machine that is built with your OS in mind :-)

In the US, they are System76, ZaReason, and Dell.

---

### Post by no2498 on 2010-02-27
in amsn click the others tap pull the window down
to set the cam up
hope this helps

---

### Post by no2498 on 2010-02-27
for the mirrored pic do you have cheese and or wxcam installed you can change it in them

---

### Post by Zeptinune on 2010-02-27
Thanks for the help no2498 but aMsn doesn't let me use webcam at all in a conversation even when I have it properly configured. It doesn't matter if I use my internal or external cam. Neither will let me send in a conversation.

I can now see other people's webcams in Emesene but I cant seem to be able to send my own which really sucks. It seems that my internal cam just isnt compatible with Emesene at all, but it shows up as being a webcam device and it does work with things like UVC View.

My external cam works fine but for some reason no one can see my cam when they accept the invite to view it. Only I am able to see it, so I am down to **thinking that this is a port problem and I have my webcam ports blocked or something.**

---

