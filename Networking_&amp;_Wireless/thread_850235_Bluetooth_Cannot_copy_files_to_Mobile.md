---
title: "Bluetooth: Cannot copy files to Mobile"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by TRANQU111TY on 2008-07-05
I am getting this error every time I try to copy something over to my Mobile via Bluetooth:

```
Error while copying "Diablo 2 Theme music - Wilderness.mp3".

There was an error copying the file into obex://[00:18:13:CE:EA:52]/Memory%20Stick/MSSEMC/Media%20files/audio/Music.

Operation not supported by backend
```

I can transfer files from my Mobile no problem just having this problem when transferring files **to** it.

---

### Post by TRANQU111TY on 2008-07-07
Also when I try to OBEX Push the file I am trying to copy onto my mobile, the 'Bluetooth file transfer' window comes up and sits at the connecting status and nothing happens.

---

### Post by dsumedh on 2008-08-04
>Also when I try to OBEX Push the file I am trying to copy onto my mobile, the 'Bluetooth file transfer' window comes up and sits at the connecting status and nothing happens.

>I can transfer files from my Mobile no problem just having this problem when transferring files to it.

Well... I am facing the exact same problem with my SE phone on ubuntu(Hardy) up-to-date system!
Unfortunately I am unable to offer a solution...but just to know you are not alone!

---

### Post by billybag on 2008-08-07
i am having the same problems. i remember looking into it a few days ago and found that hardy no longer uses OBEX but something else now (i am sorry i cannot remember what it is) this may help someone else but it didnt help me. i still cant put anything on my phone and it makes me angry

---

### Post by mexp on 2008-08-10
Found this: [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs-obexftp/+bug/230518](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs-obexftp/+bug/230518)

I have the same problem, but the Bluetooth applet / Send File option works fine.

---

### Post by nvshaji on 2008-08-11
I can confirm the same problem with Nokia N82 and Hardy (AMD64). Copying from phone to PC works fine in nautilus, but not other way around (PC to phone). But can use the applet to send individual files and receive them as messages successfully in the phone.

---

### Post by Beto on 2008-08-13
Same problem here with Nokia 5300. Phone to Notebook works ok, but the other way around cannot be done.

---

### Post by mikealive on 2008-08-14
i'm having the same exact problem with the nokia n82. i can sent to the computer but can't receive from the computer. it's really frustrating.

---

### Post by richardkhe on 2008-09-08
got the same problem here..
Any fix on this?
I can't seem to get obexftp working though (ubuntu newbie)

Laptop: Asus A8E (i think it's not the hardware)
OS: Ubuntu (hardy heron)
Phone: SE W710i

---

### Post by mikealive on 2008-09-09
anybody come up with a solution yet? this is really making ubuntu unusable if i can't send files via bluetooth.

---

### Post by FBulovic on 2008-09-13
I copy paste back and forth without problem Ubuntu 8.04 - Nokia N81. If BT gives you hard time, authorize paired device or use USB cable. I put together some tutorials on [www.2010-solutions.co.za](www.2010-solutions.co.za).

Cheers
F Bulovic

---

### Post by FBulovic on 2008-09-15
> **FBulovic said:**
> I copy paste back and forth without problem Ubuntu 8.04 - Nokia N81. If BT gives you hard time, authorize paired device or use USB cable. I put together some tutorials on [www.2010-solutions.co.za](www.2010-solutions.co.za).

Cheers
F Bulovic

It looks that I was talking lies here. BT mounted file system is read only so only way to write file to phone is to use 'Send file' which is working. USB cable works 100% as stated.

---

### Post by FBulovic on 2008-09-16
If one wants to transfer files to phone obexftp works 100%. For those who do not know how to use obexftp, here is tutorial [http://www.2010-solutions.co.za/](http://www.2010-solutions.co.za/)

---

### Post by fuchur on 2009-02-02
Just want to revive this old thread to say that as of recently, Jaunty no longer has this problems.  The fix was announced in the corresponding bug report. 

I could verify this myself since I'm testing jaunty in a  Virtualbox. 
So as of April, this problem will be  gone.

---

### Post by TRANQU111TY on 2009-02-13
> **fuchur said:**
> Just want to revive this old thread to say that as of recently, Jaunty no longer has this problems.  The fix was announced in the corresponding bug report. 

I could verify this myself since I'm testing jaunty in a  Virtualbox. 
So as of April, this problem will be  gone.

Thanks for keeping us up to date!

---

### Post by realmagnum on 2009-03-03
> **fuchur said:**
> Just want to revive this old thread to say that as of recently, Jaunty no longer has this problems.  The fix was announced in the corresponding bug report. 

I could verify this myself since I'm testing jaunty in a  Virtualbox. 
So as of April, this problem will be  gone.


Finally!

Anyone knows if this issue will be fixed in Intrepid Ibex? I don't like change my operating system every 6 months...

---

### Post by justutkarsh on 2009-03-16
still there in intrepid
unable to copy files to and fro on mounted mobile thru obex nautilus

---

