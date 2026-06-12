---
title: "Media/Video/dvd"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by thaddeus on 2009-02-25
Hi, completely brand new to Ubuntu, old DECUnix user from years ago but was keen to try Ubuntu on a PC of mine that was due for the bin(And few up with Window problems). First install had problems with the video drivers, when I installed the Nvidia driver that completely messed things up! Had to uninstall driver then re-install Ubuntu 8.10, have left trying to solve Nvidia driver problem but anyting I try to play any type of video, or view youtube I get lots of need to load codec messages, basically I load everything I'm told but still have problems. Is there somewhere I get solutions to these media playing problems?

---

### Post by taurus on 2009-02-25
Install the ubuntu-restricted-extras package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Ms_Angel_D on 2009-02-25
Hi and welcome to ubuntu.


For your video card you may want to try EnvyNg It works very well for my Nvidia cards in all my computers.

Go to System->Administration->Software Sources

Under the 3rd party software tab enable the repositories listed there. Click ok and reload.

Then go to System->Administration->Synaptic Package Manager and Search for EnvyNG

install both envyng-gtk and envyng-core

then from Applications->System Tools Run Envy and install the driver.

As far as Multimedia codecs Open Add/Remove Programs make sure you have show all available applications selected then search for Ubuntu Restricted Extra's and install it.

For DVD's See this: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by thaddeus on 2009-02-25
Done that, had slight challenge accepting the sun license, youtube works now. Will try DVDs again. Thanks a million.

---

### Post by thaddeus on 2009-02-25
Will try to fix my Nvidia problem now!!!

---

### Post by thaddeus on 2009-02-25
Oh, and it is refreshing to be a member, thanks for the welcome, even though I've had some problems it's been great trying to solve them. With Windows, I just gave up most of the time!!!

---

### Post by thaddeus on 2009-02-25
Hi MetalHellsAngel,

did that with the EnvyNg but is doesn't show up under system tools?

---

### Post by Ms_Angel_D on 2009-02-25
Hi thaddeus, you can always launch it this way press alt F2 then in box that opens type 

```
gksu envyng
```

gksu allows you to run it as an administrator.

Angel

---

