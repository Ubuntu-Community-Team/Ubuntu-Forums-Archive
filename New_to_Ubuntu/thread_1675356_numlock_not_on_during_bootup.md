---
title: "numlock not on during bootup"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by flee0308 on 2011-01-25
Can someone advise me on how can I set Ubuntu so that num lock is automatically turned on so that I can use my numpad without pressing num lock? Thanks.

---

### Post by williamts99 on 2011-01-25
> **flee0308 said:**
> Can someone advise me on how can I set Ubuntu so that num lock is automatically turned on so that I can use my numpad without pressing num lock? Thanks.

This is usually a setting in the BIOS, please check the users manual for your computer, available at the mfg website.


Or you can refer to [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by jinba.ittai on 2011-01-25
Bump

I dont like this either!

---

### Post by jinba.ittai on 2011-01-25
> **williamts99 said:**
> This is usually a setting in the BIOS, please check the users manual for your computer, available at the mfg website.


Ive turned the num lock on in bios when booting up and numlock is on when the pc boots up, but when ubuntu starts numlock is off.

---

### Post by williamts99 on 2011-01-25
Please see [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by jinba.ittai on 2011-01-25
> **williamts99 said:**
> Please see [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)


Thanks!

---

### Post by flee0308 on 2011-01-25
> **williamts99 said:**
> Please see [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

Sorry, but I don't quite understand that link. Which advice am I supposed to follow? I am using Ubuntu 10.10.

---

### Post by williamts99 on 2011-01-25
> **flee0308 said:**
> Sorry, but I don't quite understand that link. Which advice am I supposed to follow? I am using Ubuntu 10.10.

Follow the first section if you are not worried about it being on during the login screen.

---

### Post by flee0308 on 2011-01-25
> **williamts99 said:**
> Follow the first section if you are not worried about it being on during the login screen.

Okay, I followed the part up till "Enabling NumLock in GDM (as used in Ubuntu Gnome and Xubuntu XFCE)", and the num lock still isn't turned on when I boot my computer. Do I have to go through that part too? If so, where exactly is**/etc/gdm/Init/Default**?

Oh, and, by the way, my numlock is on when I press the button power of the CPU. But it turns itself off after I choose Ubuntu(among ubuntu safe mode, and another 2 options) in the boot menu.

---

### Post by matt_symes on 2011-01-25
Hi

> Okay, I followed the part up till "Enabling NumLock in GDM (as used in Ubuntu Gnome and Xubuntu XFCE)", and the num lock still isn't turned on when I boot my computer. Do I have to go through that part too? If so, where exactly is/etc/gdm/Init/Default?

Boot into Ubuntu. 

Open a terminal (Application->Accessories->Terminal) and type

```
sudo apt-get install numlockx
```

Enter your password. It will not be echoed to the screen. This is normal. Wait for it to install.

Press ALT and F2 together and type into the run dialog (Case sensitive so use capital I and capital D) 

```
gksudo gedit /etc/gdm/Init/Default
```

to open the file Default with root privilages. Copy and paste these lines

```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
```

before the line exit 0. exit 0 is the last line of the file. It should look something like this...

```
<snip>
     fi
    fi
  fi
fi

if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi

exit 0
```

Save the file, close and reboot Ubuntu.

That is what the guys are trying to get you to do.

Kind regards

---

### Post by flee0308 on 2011-01-25
Wow thanks, this works! Maybe one day I would understand what I am doing, haha.

---

### Post by alonsomm2000 on 2011-05-24
To every body who want or need the numlock on at start on Kubuntu, attached is a script that will install numlockx and add it to kdm (Kde session manager) so it will automatically go on at the login screen.
I notice that Kubuntu 10.10 have problems with numlockx but it work very well with Kubuntu 10.04 and probably with older versions.

Steps needed:
Download activar-numlock.zip
unzip -j activar-numlock.zip
sudo ./activar-numlock

Enjoy it. :P

---

