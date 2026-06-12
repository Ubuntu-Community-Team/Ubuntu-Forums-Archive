---
title: "How to set up a HomePNA connection?"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Karri on 2007-03-11
Hi,

How do I set up my HomePNA (PCI card) connection in Ubuntu 6.10?
I'm a Linux n00b so step-by-step instructions please.

---

### Post by Karri on 2007-03-11
Seriously, no one knows?
That's definitely the end of the road then. :(

---

### Post by chili555 on 2007-03-11
Lot's of posts if you search the forum for homepna. What have you tried so far?

This one looks especially promising: [http://www.ubuntuforums.org/showthread.php?t=193167&highlight=homepna](http://www.ubuntuforums.org/showthread.php?t=193167&highlight=homepna)

What kind of card do you have? sudu lspci -vv

---

### Post by Karri on 2007-03-11
Awesome, somehow I couldn't find this when searching. I tried something different in Xubuntu, it didn't work, now I have Ubuntu on another machine...
Going to try this later, thanks!

---

### Post by chili555 on 2007-03-11
Post back if you get stuck. We'll get you going.

---

### Post by hafuch on 2007-05-01
Hi Karri (and other HomePNA users),

I'm only sorry I haven't seen your post until now, but to get your hpna (homepna) connection up and running in Edgy Eft, do the following (it works perfectly for an AMD 79C978 homepna / ethernet PCI card):

Open a terminal (Applications-->Accessories-->Terminal) and type:

sudo gedit /etc/init.d/module-init-tools

In the file that opens up, scroll down until you find the line that reads:

# Loop over every line in /etc/modules

On the line below this, add the following line :

modprobe -r pcnet32 > /dev/null 2>&1

Finish by saving the file and rebooting.

Your hpna connection should work fine after that.

Let us know if you're still experiencing problems or if this worked for you.

I've tried this both in Edgy Eft 5.10 and in Feisty Fawn 7.04, and it has worked perfectly for me.

Many thanks to escifell for this solution posted back on 12 June 2006.

(escifell's original post is here: [http://ubuntuforums.org/showthread.php?t=193167](http://ubuntuforums.org/showthread.php?t=193167))

Kind regards. I hope this has been helpful.

Hafuch

---

### Post by zuketti on 2007-08-23
Hi yesterday I upgraded my ubuntu 6.10 to 7.04 and 
in ubuntu 6.10 I typed 
sudo rmmod pcnet32
sudo modprobe pcnet32 homepna=1
and network worked fine but
now it doesn't work and your example did not work either. 
Can anyone help me?

---

