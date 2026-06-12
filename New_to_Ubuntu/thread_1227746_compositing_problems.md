---
title: "compositing problems"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-07-31
Hi Ya'll,
 I have been having some issues with the compositing turning off. I get a message telling me that I need to turn on the compiz fusion?? I have tried to go to the desktop appearance, and put the effects on, and it will only last for a while before it seems to turn it self off again, and then my screen goes all haywire, and I get blank spots where windows were open, and AWN closes.

---

### Post by Shig on 2009-07-31
Hi AndyP79

Check out compiz-check - It will run some tests on your system and help to indentify what is wrong. Post the output of the script here once you've run it, as it will provide some useful information to those who might be able to help with your problem.

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Instructions for running the script are on the site.

It would also be useful to know if you have made any changes to your Ubuntu install before the problem occurred.

---

### Post by AndyP79 on 2009-07-31
HI Shig,
 Thanks for the reply. I am sorry, but I went to the site, and this looks to be more technical then I understand. I am not too much for the command line or items that go along in it. 

I had no problem before with compiz. All of a sudden it just went. Last update or change was 2-3 days before, and everything was fine. I did add google gadgets, but it seems to work fine also. 

Could anyone walk me through this compiz check thing, in plain english please? 
Thanks

---

### Post by Shig on 2009-07-31
Basically, open a terminal (Accessories->Terminal) and type:

```

wget http://blogage.de/files/9124/download -O compiz-check
chmod +x compiz-check
./compiz-check

```

---

### Post by AndyP79 on 2009-07-31
Okay, this is what I got, now what? Thanks.


andy@andy-laptop ~ $ wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check
--2009-07-31 11:51:46--  [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download)
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/octet-stream]
Saving to: `compiz-check'

    [    <=>                                ] 28,360      39.4K/s   in 0.7s    

2009-07-31 11:51:47 (39.4 KB/s) - `compiz-check' saved [28360]

andy@andy-laptop ~ $ chmod +x compiz-check
andy@andy-laptop ~ $ ./compiz-check

Gathering information about your system...

 Distribution:          Linux Mint 
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8200M G (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Shig on 2009-08-01
Seems to be all in order, meaning you have all the right software and hardware configuration to run compiz.

Try running through the below tutorial on setting up Compiz to see if it doesn't fix the problem and get compiz running for you again:
[http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-8.04-nvidia-geforce-fx-5200)

---

### Post by AndyP79 on 2009-08-01
Okay, so I looked at the howtofirge page.  What I did was try the other driver. I have been using the 180, which is the recommended one, but I tried the 173, and when I restarted, I had my AWN back, and everything seems to be in order. Maybe for whatever reason, becuase of some unknown program or update, I just have to use that. I won't question, as it works now.
 Thanks for your help. apperciate it.

---

