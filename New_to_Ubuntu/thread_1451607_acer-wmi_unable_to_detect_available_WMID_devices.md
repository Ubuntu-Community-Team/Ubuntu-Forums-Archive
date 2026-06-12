---
title: "acer-wmi: unable to detect available WMID devices"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by 416inversed on 2010-04-10
I just upgraded my Acer AOD250 to Lucid beta2 and now on boot I'm getting an error
```
acer-wmi: unable to detect available WMID devices
``` 

A quick google search turns up this thread [http://ubuntuforums.org/showthread.php?t=1233149](http://ubuntuforums.org/showthread.php?t=1233149) which recomends running fsck from terminal, but when I do I get a scary warning

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda6 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda7 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.

```

So of course I select 'No.'

Any ideas on how to resolve this?

Should I boot from a liveUSB with those drives unmounted before I fsck?

---

### Post by Didius Falco on 2010-04-10
That would be the best idea. I'm glad you heeded the warning...

You can also force a file check on your next boot by typing this in a terminal window:

```
sudo touch /forcefsck
```

and then reboot.

---

### Post by gordintoronto on 2010-04-10
I suggest you post in the Lucid forum. It's beta software, you should expect it to break.

---

### Post by 416inversed on 2010-04-10
> **gordintoronto said:**
> I suggest you post in the Lucid forum. It's beta software, you should expect it to break.

Oh, I definitely understand Lucid is a beta... I posted here, because I didn't think it was a Lucid specific issue,  given the previous post on the matter mentions both 9.04 & 9.10.

Unfortunately, fsck from a liveUSB didn't seem to fix it.

---

### Post by jlking3 on 2010-04-26
I had the same problem on my Acer Aspire One 532h. I installed libacpi-dev and that seems to have gotten rid of the startup delay and the error message.

---

### Post by jlking3 on 2010-04-26
> **jlking3 said:**
> I had the same problem on my Acer Aspire One 532h. I installed libacpi-dev and that seems to have gotten rid of the startup delay and the error message.

Well, actually, it still is coming up with the message. Maybe I'm just not quick enough to see the error message sometimes. Sorry for the false hope. :(

---

### Post by IeU on 2010-04-29
having the same issue with latest ubuntu release (desktop)

---

### Post by goustaroubunta on 2010-05-03
i also have this problem (at boot it says : acer-wmi: unable to detect available wmid devices) with ubuntu lucid lynx netbook remix on my gfs acer aspire one..
nevertheless it detects the wireless routers and even connects automatically on my password protected netfaster iad 2 without any problems.. you people that have that same message at boot cannot connect to the internet at all? or are you annoyed by the message?

---

### Post by alexzen on 2010-05-07
> **goustaroubunta said:**
> i also have this problem (at boot it says : acer-wmi: unable to detect available wmid devices) with ubuntu lucid lynx netbook remix on my gfs acer aspire one..
nevertheless it detects the wireless routers and even connects automatically on my password protected netfaster iad 2 without any problems.. you people that have that same message at boot cannot connect to the internet at all? or are you annoyed by the message?
I have the same message on an Acer Aspire 5737Z. I can connect without any problems to the internet.

---

### Post by gian unr on 2010-07-29
Hi 

I got the same message during boot (unable to detect wmid device)

I´m using Ubuntu 10.04 LTS on Acer Aspire D250

What to do???

---

### Post by mike555 on 2010-07-29
here is a quick fix. in terminal type ; gksu gedit  , 
 
    then in gedit open  /etc/modprobe.d/blacklist.conf

    at the bottom type "blacklist acer-wmi" without the quotes.

---

### Post by mhpathfinder on 2012-01-06
From mike555:
here is a quick fix. in terminal type ; gksu gedit , 

then in gedit open /etc/modprobe.d/blacklist.conf

at the bottom type "blacklist acer-wmi" without the quotes.

Recently purchased an Acer Aspire One AOD250-1026.  Ubuntu 10.04 installed, tweaked, fast and efficient.
Other than the annoying "No WMID device detected" everything works in Ubuntu 10.04.  Glad to get your fix for it.
Added "blacklist acer wmi to blacklist.conf, as per your post.  Error message gone at boot-up.
Everything still works.
Thanks.

---

### Post by CK000 on 2012-07-14
[SIZE=2][FONT=Garamond]Thank you Mike555, an excellent post for a quick fix, for I had the same annoying problem.[/FONT][/SIZE]

---

