---
title: "No internet option"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by Amockineuropa on 2010-10-29
So I just loaded the Ubuntu 10.10. I have been using a dual boot set up for about 2 years w/o problems. I decided since I never use windows to just reload Ubuntu by itself on the entire HD. Loaded fine BUT I have neither wired/wireless internet ability. Under wired it says disconnected but even when hardwired it does not recognize a modem. Under wireless it says device not ready firmware missing. WHAT NOW?

---

### Post by J V on 2010-10-29
If you rightclick the network manager applet you can "Enable networking" to gain access via wire, then download drivers to get wireless working

---

### Post by Amockineuropa on 2010-10-29
I tired a wired connection still not work. It does not even see my modem. Does not list it as an option. I do have another computer on-line so I am able to download drivers if need be. But how do I get it to first recognize my modem?

---

### Post by oldfred on 2010-10-29
Did you have the wired connection connected during the install? If not it may not have configured a wired connection.

What does this show. Also from other computer. (or ipconfig in windows command line)
ifconfig

You may just need to click on edit connections. add/edit eth0 and set it to DHCP under the IPv4 tab.

---

### Post by Hippytaff on 2010-10-29
failing this typing

```

lshw -C network

```and
```

lscpi

```into the terminal (open a terminal with CTRL+ALT+T)

Should give you some info to get started troubleshooting :-)

Edit > Sorry - didn't realise oldfred was already on the case :-) you won't go far wrong with that kind of assistance :-)

---

### Post by Amockineuropa on 2010-10-29
Good point and NO I did not have it wired in during install. Should I hard wire in THEN reload the OS?

---

### Post by gandaran on 2010-10-29
>  Should I hard wire in THEN reload the OS?
not necessarily! what type of modem do you have? is it an ethernet router or something else?

---

### Post by Amockineuropa on 2010-10-29
Ethernet router

---

### Post by DirtyPC on 2010-10-29
Hmm.. thats odd.. I'd recommend getting the drivers from your pc with internet via USB, Generally the wireless wouldnt appear if it didnt detect your card/dongle. Maybe your having compatibility issues?

Could you also post the results of **ifconfig **

---

### Post by Hippytaff on 2010-10-29
> **Hippytaff said:**
> failing this typing

```

lshw -C network

```and
```

lscpi

```into the terminal (open a terminal with CTRL+ALT+T)



maybe this wasn't such bad advice!? :-) post the results and we can have a look...oh and its lsusb not lspci if your using a usb dongle

---

### Post by Amockineuropa on 2010-10-29
No ipconfig using linux only. Like I said in oppening thread the wireless option appears just strates device not ready firmware missing. Under wired it says disconnected. So I then hard wired it in and rebooted and still no internet. Does not show a router availble

---

### Post by DirtyPC on 2010-10-29
Check also if you have a hardware or software modem, if it detects it
wvdialconf /dev/nullIf not installed, type:

sudo apt-get install wvdial

---

### Post by Hippytaff on 2010-10-29
try ifconfig instead of ipconfig

---

### Post by Amockineuropa on 2010-10-29
I am missing wvdial

---

### Post by DirtyPC on 2010-10-29
> **Amockineuropa said:**
> I am missing wvdial
Try: sudo apt-get install wvdial

---

### Post by DirtyPC on 2010-10-29
> **Hippytaff said:**
> try ifconfig instead of ipconfig
Silly me. Hehe, thats *IS *what I meant. Yes, try **ifconfig**

---

### Post by DirtyPC on 2010-10-29
> **harrylucas1 said:**
> Silly me. Hehe, thats *IS *what I meant. Yes, try **ifconfig**
NO! Ahaa not my error, I did put **ifconfig**, its 'if' not 'ip'

---

### Post by Hippytaff on 2010-10-29
I think oldfred suggested ip config from a different machine on the network? haven't re-read but...anyway - sudo apt-get wvial like you said :-)

---

### Post by Amockineuropa on 2010-10-29
missing wvdial

---

### Post by Hippytaff on 2010-10-29
> **Amockineuropa said:**
> missing wvdial

In a terminal do
```

sudo apt-get install wvdial

```

---

### Post by DirtyPC on 2010-10-29
> **Hippytaff said:**
> I think oldfred suggested ip config from a different machine on the network? haven't re-read but...anyway - sudo apt-get wvial like you said :-)
And to think i've only been on this forum for a week, I fell so helpful. :-)

@Amockineuropa, again look at the above posts. If you are having trouble, go into terminal then copy and paste this:

sudo apt-get install wvdial

---

### Post by Amockineuropa on 2010-10-29
Tried package missing not available

---

### Post by DirtyPC on 2010-10-29
> **Amockineuropa said:**
> Tried package missing not available
Strange, I have just done this myself and Its fine.

---

### Post by Hippytaff on 2010-10-29
Hang on...if you've got not internet connection you can't do that anyway. you need to download it, save it to a pen drive, and then install it on the ubuntu machine

heres one of the places you can get it from [http://www.filetransit.com/download.php?id=84965](http://www.filetransit.com/download.php?id=84965)
haven't varified the authenticity of the site though

so once you copy the file to ubuntu machine you need to unpack it (double click on it), chooshe the location (the dafaul is / which is you home directory) then just double click on the file and it should install

---

### Post by DirtyPC on 2010-10-29
> **Hippytaff said:**
> Hang on...if you've got not internet connection you can't do that anyway. you need to download it, save it to a pen drive, and then install it on the ubuntu machine

heres one of the places you can get it from [http://www.filetransit.com/download.php?id=84965](http://www.filetransit.com/download.php?id=84965)
haven't varified the authenticity of the site though
How did I not see that? FML.

---

### Post by DirtyPC on 2010-10-29
Also is you main internet wired or wireless?

---

### Post by Amockineuropa on 2010-10-29
I downloaded the opackage x4 from various sites. Does not seem to want to load though. Maybe not to sure how to install the package I click and extract and still nothing.

---

### Post by DirtyPC on 2010-10-29
> **Amockineuropa said:**
> I downloaded the opackage x4 from various sites. Does not seem to want to load though. Maybe not to sure how to install the package I click and extract and still nothing.
try looking for a .deb file, much easier to install, if not, you can do it via the terminal

---

### Post by Amockineuropa on 2010-10-29
wireless

---

### Post by Hippytaff on 2010-10-29
got it from the link I posted and it looks fine

---

### Post by DirtyPC on 2010-10-29
> **Hippytaff said:**
> got it from the link I posted and it looks fine
Me too, its fine

---

### Post by Amockineuropa on 2010-10-29
I tried it will open with the Software center but the install button is not highlighted. Any other way to install?

---

### Post by DirtyPC on 2010-10-29
> **Amockineuropa said:**
> wireless
I've seen a very similar forum on here actually, which seems to fix wireless devices not being recognised, i'll try and find it now...

---

### Post by DirtyPC on 2010-10-29
> **Amockineuropa said:**
> I tried it will open with the Software center but the install button is not highlighted. Any other way to install?
You tick it and click apply

---

### Post by Amockineuropa on 2010-10-29
Tired must go to bed. I tried everything to no avail. Will try later. Thanks

---

