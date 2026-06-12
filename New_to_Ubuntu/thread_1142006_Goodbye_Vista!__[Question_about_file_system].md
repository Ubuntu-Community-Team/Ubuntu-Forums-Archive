---
title: "Goodbye Vista!  [Question about file system]"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by sarahm300 on 2009-04-28
First off, nice job Ubuntu guys!  9.04 right from the install works great with my ThinkPad!  I'm very very impressed.

I'm trying to enable the ThinkPad's middle trackpoint button by following these instructions - [http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/](http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/)

How do I access the etc/hal/fdi/policy/ folder so I can create a new file called mouse-wheel.fdi ?  

It says root is the owner so I can't make any changes.  When I try to login as root, it says I can't.  

I'm coming from MS land where I was logged in as admin and I could just right click the directory and take ownership and change the permissions.  How does one do this in Linux land?

Oh and Vista & MS can kiss my **** :-)

Sarah M

---

### Post by Tibuda on 2009-04-28
You can open the file as root if you run gedit with gksu. Press Alt+F2, and type "gksu gedit". It will ask for your password and open gedit as root. Then you can edit any file in your system. Just remember this is dangerous.

---

### Post by sarahm300 on 2009-04-28
Thanks Daniel.

Now what is the author at the link above talking about when he says:  

[COLOR=Blue]You need a very recent xserver-xorg-input-evdev (git snapshot) that I put into my PPA at “deb [http://ppa.launchpad.net/mvo/ubuntu](http://ppa.launchpad.net/mvo/ubuntu) intrepid main”[/COLOR]

I have no clue where to start.

Sarah M

---

### Post by kostkon on 2009-04-28
> **sarahm300 said:**
> Thanks Daniel.

Now what is the author at the link above talking about when he says:  

[COLOR=Blue]You need a very recent xserver-xorg-input-evdev (git snapshot) that I put into my PPA at &#8220;deb [http://ppa.launchpad.net/mvo/ubuntu](http://ppa.launchpad.net/mvo/ubuntu) intrepid main&#8221;[/COLOR]

I have no clue where to start.

Sarah M
Since this post is rather old ( 2008 ) and since you have 9.04 then you already have a recent version of this package, so I assume you can skip this step.

---

### Post by Didius Falco on 2009-04-28
> **sarahm300 said:**
> Thanks Daniel.

Now what is the author at the link above talking about when he says:  

[COLOR=Blue]You need a very recent xserver-xorg-input-evdev (git snapshot) that I put into my PPA at “deb [http://ppa.launchpad.net/mvo/ubuntu](http://ppa.launchpad.net/mvo/ubuntu) intrepid main”[/COLOR]

I have no clue where to start.

Sarah M

Hi,

You don't have to add his Repository to get this - it's been added in to Jaunty. Just follow the above instructions to create the file and you should be good to go.

Just for your future reference, Repositories are software package servers. There are the official ones, and then there are 3rd party ones. You have to decide which 3rd party ones are trustworthy, but the "biggies", like Medibuntu, are well-known.

the ```
deb [http://ppa.launchpad.net/mvo/ubuntu](http://ppa.launchpad.net/mvo/ubuntu) intrepid main
```

Part is what you'd add to your Software Sources 3rd Party list in order to download from his repository. You'd also add a public key file that looks like this:

```
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iQCVAwUASe8LnxKRlkcOsS8FAQKlGgQA1fN/uKFC++1aKdPfNBm1CGhnQQo7yaGz
Jfm//Ug5AQ3w1UhgWlO2SLnfqoS+wpcbUzg1K+m5lxuiWdN/BHNFwBOWN+pzn6x9
QidsneeZLtmFVvbFWAz+im50EKfYqEjQbfuKpEzEQn95mX6VwxArY7Nh2hX7KhQN
vKwf8q7b850=
=Hd1j
-----END PGP SIGNATURE-----
```by grabbing the key and saving it to a file, which you'd then import into the "Authentication" tab.

That's enough to get you started. Enjoy your Ubuntu!!

---

### Post by sarahm300 on 2009-04-29
Thanks everyone!  All I had to do was create the mouse-wheel.fdi and now I'm good to go.

Ok now I'm off to find a replacement for MS Outlook.  Can anyone recommend an email client that will connect to my Exchange 2007 server at home?

Sarah M

---

### Post by halovivek on 2009-04-29
hi if you are looking to access like yahoo mail and other things. 
use zimbra yahoo mail client.
if you can configure general mail like office and all use Thunderbird.
For zimbra just download from [here]("http://h.yimg.com/lo/downloads/zdesktop/1537/zdesktop_1_0_build_1537_linux_i686.sh").
To install zimbra follow these [steps]("http://www.howtoforge.com/how-to-install-zimbra-desktop-on-ubuntu8.04")
For Thunderbird go to add/remove programs and search Thunderbird and give apply. it will install automatically.

---

### Post by Tibuda on 2009-04-29
> **halovivek said:**
> hi if you are looking to access like yahoo mail and other things. 
use zimbra yahoo mail client.
if you can configure general mail like office and all use Thunderbird.
For zimbra just download from [here]("http://h.yimg.com/lo/downloads/zdesktop/1537/zdesktop_1_0_build_1537_linux_i686.sh").
To install zimbra follow these [steps]("http://www.howtoforge.com/how-to-install-zimbra-desktop-on-ubuntu8.04")
For Thunderbird go to add/remove programs and search Thunderbird and give apply. it will install automatically.

No, he want to connect to MS Exchange Server. You have to install the [evolution-mapi]("apt:evolution-mapi") package, which will allow Evolution (the default Ubuntu mail client) to connect to Exchange servers. If you don't know how to install packages in ubuntu, read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

