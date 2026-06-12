---
title: "Need help with wireless."
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by dilton on 2008-10-13
I am trying to configure my broadcom wireless card to work with hardy and I'm facing some issues. I am using this guide [http://blog.stevienova.com/2008/04/25/ubuntu-804-hardy-heron-linux-is-cool-linux-wireless-is-not-10-step-program/]("http://blog.stevienova.com/2008/04/25/ubuntu-804-hardy-heron-linux-is-cool-linux-wireless-is-not-10-step-program/")

When I type step 10 into Terminal this is what i get

This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to create output directory: No such file or directory


Am i supposed to type it in exactly how it shows in the tutorial or am i supposed to substitute something in for the ../../? I am new to ubuntu so all help is appreciated. Thank you.


Dilton

---

### Post by insineratehymn on 2008-10-13
Is it just me, or is there some funny font in that line 10? This is what I see verbatim:
> 10) sudo ../../b43-fwcutter-011/b43-fwcutter -w â&#8364;&#339;/lib/firmwareâ&#8364;? wl_apsta.o

Are you doing this in another language?

If not, look here: [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

---

### Post by parajuito on 2008-10-13
that step ten is not well written its supposed to be sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta.o

---

### Post by dilton on 2008-10-13
That revised step 10 seemed to do what it was supposed to, no error messages. I will restart and let you know how wireless went.

---

### Post by dilton on 2008-10-13
SUCCESS, wireless is now working, thank you!

---

### Post by parajuito on 2008-10-13
im glad it worked :)

---

