---
title: "Instructions for using homepna to connect to internet on Ubuntu"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by phonghao on 2007-07-19
Hi all,

 I am newbie so i read all posts about using homepna but i still can't connect to internet. I am using Ubuntu 7.04  and my card is SMC2812USB. Can you all tell me instructions, step by step, to make it working well? Thanks so much.

---

### Post by hafuch on 2007-11-05
Hi Phonghau (and other HomePNA users),

To get your homepna connection up and running in Gutsy Gibbon (as well as in Feisty Fawn and Edgy Eft, try the following (it works perfectly for an AMD 79C978 homepna / ethernet PCI card):

Open a terminal (Applications-->Accessories-->Terminal) and type:

sudo gedit /etc/init.d/module-init-tools

In the file that opens up, scroll down until you find the line that reads:

# Loop over every line in /etc/modules

On the line below this, add the following line :

modprobe -r pcnet32 > /dev/null 2>&1

Finish by saving the file and closing it.

Next, type the following in the terminal:

sudo gedit /etc/modules

In the file that opens up, add the following line at the end:

pcnet32 homepna=1

Save and close the file, then reboot.

Your homepna connection should work fine after that.

Let us know if you're still experiencing problems or if this worked for you.

This is tried and tested for Gutsy Gibbon 7.04, and it has worked perfectly for me.

Many thanks to escifell for this solution posted back on 12 June 2006.

(escifell's original post is here: [http://ubuntuforums.org/showthread.php?t=193167](http://ubuntuforums.org/showthread.php?t=193167))

Kind regards. I hope this has been helpful.

Hafuch

---

