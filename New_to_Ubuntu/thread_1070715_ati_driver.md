---
title: "ati driver"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by delpgdn on 2009-02-15
anybody heard of a new ati driver coming out? ive tried everything on forums and web still cant get card to work

---

### Post by kk0sse54 on 2009-02-15
The proprietary (fglrx) or open source ones?

---

### Post by delpgdn on 2009-02-15
all im trying to do is get card to work no luck

---

### Post by kk0sse54 on 2009-02-15
> **delpgdn said:**
> all im trying to do is get card to work no luck

Can you give us specifics? What type of card is it? Are you trying to install the fglrx proprietary driver and if so can it be installed through Restricted Drivers or are you trying to download the driver from the ati site? I don't exactly know what model your card is but here's a link to installing proprietary ati drivers (fglrx)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by delpgdn on 2009-02-15
card is radeon 9000 tried everything on your page zip

---

### Post by kk0sse54 on 2009-02-15
The card should technically work with this driver [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html) however it is indeed old and hasn't had any updates in a while. So the reason it won't work is becuase it won't work with newer versions of xorg which I believe is something like 7.4 for intrepid. Instead Ubuntu should be defaulting to the open source radeon driver. Does X work at all for you?

---

### Post by delpgdn on 2009-02-15
lspci shows radeon controller  have ati control center but no driver  xorg  etc works tried all you wrote about nothing    i installed restricted drivers zip  nothing under hardware drivers  8.10

---

### Post by kk0sse54 on 2009-02-15
What I'm saying the driver for your card doesn't look like it will work with the newer versions of Xorg because it hasn't been updated since 2006. Thus since X is working for that means that Ubuntu is falling back on the open source radeon driver which should allow you to run a perfectly fine GUI but out fof the box won't give you 3D and thus things like compiz won't work.

---

### Post by qamelian on 2009-02-15
What isn't working? I have the same card and it works out of the box with the default open-source drivers.

---

### Post by delpgdn on 2009-02-15
no control panel for card desktop effects not enable no visible change in anykind of video

---

### Post by kk0sse54 on 2009-02-15
> **delpgdn said:**
> no control panel for card desktop effects not enable no visible change in anykind of video

 Check out this link for desktop effects with open source drivers [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). As for no control panel for card and no visible change in anykind of video I'm sort of lost as to what you mean there.

---

### Post by alexandari on 2009-02-15
I decided to update my ATI driver (bad idea) and so I did it...everything seemed ok but when I tryed to run some D3D applications...the whole screen was like...what`s going on here xD

---

### Post by qamelian on 2009-02-15
> **C!oud said:**
> Desktop effects will not work because 3D is not supported by the open source radeon driver. As for no control panel for card and no visible change in anykind of video I'm sort of lost as to what you mean there.
3D and desktop effects are supported by the open-source driver on the Radeon 9000 and have been for some time. I use the open-source driver and have full use of compiz with no problems at all and have done so since before compiz was a part of the default Ubuntu install.

---

### Post by kk0sse54 on 2009-02-15
> **qamelian said:**
> 3D and desktop effects are supported by the open-source driver on the Radeon 9000 and have been for some time. I use the open-source driver and have full use of compiz with no problems at all and have done so since before compiz was a part of the default Ubuntu install.

Hence why the post was edited almost immediately ;)

---

### Post by qamelian on 2009-02-15
> **C!oud said:**
> Hence why the post was edited almost immediately ;)
Yeah, I had to do a double-take, as I knew that wasn't what I saw the first time around. :lolflag:

---

### Post by delpgdn on 2009-02-15
cant change desktop appearance videos choppy no sign of card working no info of card on system except lspci card works fine under vista

---

