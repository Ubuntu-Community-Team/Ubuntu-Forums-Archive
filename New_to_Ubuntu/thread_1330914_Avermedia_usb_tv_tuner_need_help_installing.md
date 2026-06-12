---
title: "Avermedia usb tv tuner need help installing"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by DXM31 on 2009-11-18
I just did a fresh install of 9.10 was running 8.04 on my laptop.
It is amazing how everything works right out of the box with 9.10.
But, I thought I would try and us my avermedia us tuner.
I've done some searches and I just get more cofused.
I have downloaded a driver from avermedia, but I don't know how to install it???
I am probably not asking the right questions or doing the right searchs.
I am just trying to get this usb tuner to work.

according to this site it should work
[http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_Volar_%28A868R%29](http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTVHD_Volar_%28A868R%29)
this is my device

---

### Post by skatinjj on 2009-11-18
Can you provide the link where you downloaded your driver from?

---

### Post by DXM31 on 2009-11-18
here you go
[http://www.avermedia.com/avertv/Support/Download.aspx?Type=APDriver](http://www.avermedia.com/avertv/Support/Download.aspx?Type=APDriver)

---

### Post by skatinjj on 2009-11-18
Since I didn't expect it to list other models, which model and version is yours?

---

### Post by DXM31 on 2009-11-18
Oops wrong link..anyway I chose A827Al

---

### Post by skatinjj on 2009-11-18
I am downloading the linux driver now, did you make sure you downloaded the Linux x86 (x64 for 64 bit)?

---

### Post by DXM31 on 2009-11-18
x86
I downloaded it to my desktop then extracted it.

I get these instructions to install:
(1) Use sudo. Recommended for Ubuntu Linux users. You need to type your own
      password:

      $ sudo ./AVERMEDIA-Linux-x86-H826D-0.09-beta.sh
      Password:"Type your password here"
I get invalid command or something

---

### Post by skatinjj on 2009-11-18
[Here]("http://www.avermedia.com/avertv/product/ProductDetail.aspx?Id=448&tab=APDriver") is the link for the driver you would need.

According to the INSTALL text file, all you need to do after downloading and extracting the driver is open a terminal, change to the directory that you extracted to and run this:

```
sudo ./AVERMEDIA-Linux-x86-H826D-0.09-beta.sh
```

It will prompt for your password, so type it in and it should work.

Post any error messages if there are any.

---

### Post by skatinjj on 2009-11-18
Sorry didn't see your reply as I was typing mine, give me a few minutes as I c=am trying to get a VM up while I'm in Windows troubleshooting a friends HDD.

---

### Post by DXM31 on 2009-11-18
It's been awhile how to I to my desktop folder in the terminal?

I know it is home/my name/desktop but I need a map to get there
Thanks

Nevermind DOH!!!

---

### Post by skatinjj on 2009-11-18
After extracting, did you make sure you changed to the same directory it was extracted to?

```
 cd /where/it/was/extracted 
```

---

### Post by skatinjj on 2009-11-18
```
cd ~/Desktop
```

Also, you probably have to run this:

```
chmod a+x (filename)
```

to give the file permission to execute

EDIT
Took sudo out since it is your file you won't need it

---

### Post by skatinjj on 2009-11-18
It is installing for me so it should work after switching to the location it was extracted to then using chmod to allow execution and running the script with sudo

I got to install without any problems.

---

### Post by DXM31 on 2009-11-18
I got the driver installed but it still doesn't work with ME TV or TVtime

---

### Post by skatinjj on 2009-11-18
Can you post the output of

```
lsusb
```

after plugging in your tuner?

Plus, post any errors the programs might of gave when you tried to use them.

---

### Post by DXM31 on 2009-11-18
lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07ca:a868 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
Tvtime just says no signal and No such file or directory Cannot open capure device /dev/video0

---

### Post by skatinjj on 2009-11-18
Since I do not use a tv tuner on my computer, I am not sure I can help you much further.

I will try to look around and post possible solutions though.

---

### Post by DXM31 on 2009-11-18
Thanks at least we got the driver loaded

---

### Post by skatinjj on 2009-11-18
Your welcome and hopefully someone will post soon with some good advice.

---

### Post by DXM31 on 2009-11-18
I need new glasses this is my tuner
[http://www.avermedia.com/avertv/Support/Download.aspx?Type=Document&id=173&tab=UserManual](http://www.avermedia.com/avertv/Support/Download.aspx?Type=Document&id=173&tab=UserManual)

and they don't show any Linux drivers for it...

---

### Post by skatinjj on 2009-11-18
I am not able to find anything about linux support for your tv tuner, sorry.

Maybe someone else will have a suggestion but as far as I can tell, it isn't supported in linux.

---

### Post by fancypants42 on 2010-09-18
Same problem here with Lucid. Driver installs, but no device in /dev/video0

[    1.696057] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.829629] usb 2-1: configuration #1 chosen from 1 choice



lscpu
Bus 002 Device 002: ID 07ca:1826 AVerMedia Technologies, Inc.

---

