---
title: "Connecting the internet"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by bingeonbingo on 2010-10-18
I am new to ubuntu and am **using ubuntu 9.1**. Its an awesome OS but the problem is that I _can't connet to the internet_ in it. I have a** broadband connection (ADSL) with Nokia-Siemens C110 modem** and **donot have an ethernet driver**, so **I'll connect to the net using USB cable**. Since **I am a beginner** so I'll need detailed info to set up a net connection. Any kind of help would suffice.


-Thank you.

---

### Post by ibizatunes on 2010-10-18
firstly install ubuntu 10.10 the networking support will be better!
and you may have more success

---

### Post by MooPi on 2010-10-18
If you don't want to install 10.10 we can also help. 
Can you post the contents of your /etc/network/interfaces file.
In terminal: ```
gedit /etc/network/interfaces
```
Copy and paste the results back here.

---

### Post by TBABill on 2010-10-18
I would strongly caution against advising a new user to install 10.10, especially when they are questioning networking issues. 10.10 is plagued right now with a great deal of connectivity issues and for an inexperienced user they may be overwhelming, particularly when 10.04 is performing so well and seems to have stabilized over the past couple months. A search of the forums for wireless, wifi and router will confirm the 10.10 issues many (not all) are experiencing. 10.04 had them as well but they seem to have been worked out for the most part from what I see as new posts.

---

### Post by bingeonbingo on 2010-10-19
When I typed *gedit /etc/network/interfaces* in the terminal, a dialogue box opened and there it was written:

[I]auto lo
iface lo inet loopback[/I]


:confused:

---

### Post by dineshs on 2010-10-19
> 
I have a broadband connection (ADSL) with Nokia-Siemens C110 modem and donot have an ethernet driver, so I'll connect to the net using USB cable. 

Dont you have ethernet port in your PC?If yes why dont you connect your modem via ethernet?What does ```
sudo lshw -C network
```say when you do this?please post result
Check whether pages are loading
Note:If your modem is not configured follow [this]("http://www.itshams.ir/uploads/2/Cms/User/File/2/Siemens.pdf")

---

### Post by bingeonbingo on 2010-10-19
I do have an ethernet port in my pc but it is damaged so I use the USB port instead.

---

### Post by amjjawad on 2010-10-19
> **ibizatunes said:**
> firstly install ubuntu 10.10 the networking support will be better!
and you may have more success

That's not a good advice!
As previously mentioned, 10.10 has many issues so far.

---

### Post by amjjawad on 2010-10-19
> **bingeonbingo said:**
> I do have an ethernet port in my pc but it is damaged so I use the USB port instead.

Just to understand your situation better.
How do you connect now to the internet? through your USB port?
If yes, then try to find the driver for your Wireless Adapter while you're connected unless you're using another machine at the moment.

---

### Post by dineshs on 2010-10-19
I havent tried USB port in ubuntu.You may look [here ]("https://help.ubuntu.com/community/UsbAdslModem")
In my opinion you may purchase a new ethernet card if the above guide doesnt help

---

### Post by Lakez on 2010-10-19
> **dineshs said:**
> I havent tried USB port in ubuntu.You may look [here ]("https://help.ubuntu.com/community/UsbAdslModem")
In my opinion you may purchase a new ethernet card if the above guide doesnt help

Same opinion here, if the USB modem ( not one of my favorite things ) doesn't give you an internet connection, just go buy a new ethernet card, which is in my opinion better to get internet.

---

### Post by Hippytaff on 2010-10-19
Whats the output of
 
```

lsusb

```
 
```

rfkill list

```
 
```

iwconfig

```
 
oh...and
 
```

lsmod

```

---

### Post by bingeonbingo on 2010-10-21
Can't there be any way to connect to the internet via USB cable? :cry:

---

### Post by bingeonbingo on 2011-04-27
> Whats the output of

Code: lsusb

Code: rfkill list

Code: iwconfig

oh...and

Code: lsmod

These are the output of what you asked for.

---

### Post by Hippytaff on 2011-04-27
If the usb wireless device was plugged in when you got the output of those commands it is not being recognised. Can unplug it, then plug it back in again and post the output of```
dmesg | tail 
```

---

### Post by bingeonbingo on 2011-04-27
> If the usb **wireless** device was plugged in...

Its not wireless, its  wired.

---

### Post by Hippytaff on 2011-04-27
ok...can you still do the command :-)

---

### Post by bingeonbingo on 2012-04-04
Ok I've bought a new dlink lan card and in my ubuntu 11.10 when I turn on the modem, after a while two arrows show up saying wired conection established (or something like that) but I still cannot connect to the internet. Any help?? :confused:

---

### Post by amjjawad on 2012-04-04
> **bingeonbingo said:**
> Ok I've bought a new dlink lan card and in my ubuntu 11.10 when I turn on the modem, after a while two arrows show up saying wired conection established (or something like that) but I still cannot connect to the internet. Any help?? :confused:

This is a October 19th, 2010 old thread :)

Have you checked the previous posts?
You need to get back to us a bit faster ;)

---

### Post by oldos2er on 2012-04-04
Closed, necromancy.

bingeonbingo, please start a new thread.

---

