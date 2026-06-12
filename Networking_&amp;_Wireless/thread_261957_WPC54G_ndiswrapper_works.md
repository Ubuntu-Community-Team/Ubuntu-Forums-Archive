---
title: "WPC54G ndiswrapper works"
date: 2006-09-20
forum: Networking &amp; Wireless
---

### Post by crusty_collins on 2006-09-20
After much cussing and banging my head against the wall.... I was able to get this pcmcia wireless card working.  Initially I used the bcm43xx included with xubuntu and got spotty results.  After a re install, I followed the [directions]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") to the letter and BANG everything came up without me doing any additional configuration.  
Just a note that I tried to load all of the following distros without success.
dsl
dsl-n
gentoo
knoppix
and for some unknow reason ubuntu did not recognize the card ?????. (user error)

This was an important project because I am trying to convert all my friends and family to linux.

Specs
IBM thinkpad T21
PIII 512 Meg
Linksys WPC54g

additional boot options on install are ( noacpi linux floppy=thinkpad)

---

### Post by Melcar on 2006-09-21
I will give it a try.  I have been trying for several days now attempting to install a WPC54Gv2 (as well as a Trendnet card) on an old Latitude notebook.  I was this close to re-installing Win98[-X .

---

### Post by Melcar on 2006-09-21
I think I'm Linux-retarded because after following several guides (including the one on the link) I just can't get my WPC54G to work.  I keep hitting a wall when I modprobe ndiswrapper:

" (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/diswrapper.ko): Invalid argument "

---

### Post by syno on 2006-09-22
try 'sudo modprobe ndiswrapper'

---

### Post by woody_green on 2006-09-22
I'm also using WPC54G. It worked almost out of the box. Almost, because there's something weird about it. I can surf the net, but I can't log in to Yahoo. When I tried it in Windows, I can surf and I can log in. I'm using a proxy server, by the way.

---

### Post by alex_mayorga on 2006-09-22
Guys you might be being impacted by [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34068]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34068")

How I get through:

cd /lib/firmware/`uname -r`/acx/default
sudo mv tiacx111c16 tiacx111c16.old
sudo ln -s ../1.2.1.34/tiacx111c16 tiacx111c16
sudo rmmod acx
sudo modprobe acx
[SIZE="1"]Reference (in Spanish): [http://diego.bloog.cl/blog/2006/06/10/configurando-una-linksys-wpc54g-v2-en-ubuntu-dapper/](http://diego.bloog.cl/blog/2006/06/10/configurando-una-linksys-wpc54g-v2-en-ubuntu-dapper/)[/SIZE]

Hope it helps.

---

