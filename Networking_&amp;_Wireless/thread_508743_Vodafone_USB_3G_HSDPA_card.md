---
title: "Vodafone USB 3G HSDPA card"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by Nunu on 2007-07-24
Hi guys

I have heard of a lot of poeple having problems with getting there Vodafone USB 3G card to work on 6.06LTS I know it is an almost forgotten version but what the hay for those of you having probelms with this device here you go...

I managed to download the driver for the Huawei e220 from 

_[COLOR="RoyalBlue"]https://forge.vodafonebetavine.net/projects/vodafonemobilec[/COLOR]/_

I donwloaded the driver and tried to install it... but due to 6.06LTS that seems like Python was not part of the package when shiped, I had some major problems getting the driver installed.

What I did then was to copy the file vodafone-mobile-connect-card-driver-for-linux from the downloaded package to etc/X11 by using the su command and then cp (SU is not recomended if you are not willing to rebuild the machine... I think there is thread about it someware on the Wiki.) once the driver was copied to this location I simply ran the sudo -s pppconfig comand in terminal and created a new connection using the following config in sequance

Providor Name :3G
DNS: dynamic
Authentication: PAP
User name: in SA you can add anything and it will still work however I don't know about              other countrys
Password: again in SA can be left as password but other countrys might have password requierments
speed: 460800
pulse or Tone : Tone
Phone number : the local number in SA is *99***1#
Modem config: say yes to probe and then edit the result in manual configuration as /dev/ttyUSB0

Once this is done browse to the folder where the downloaded driver is stored. You might want to decompress the content to make it easyer. once in the folder, browse to /contrib/e220/files and then run in the following command **sudo -s huawei-mobile-sh.** 

if this is succesfull you can now connect to the internet using the command pon 3G(depending what you named this file during the PPP configuration).

This did work for me as i managed to do a system update through Update manager and post this message on the forum

Next step is to see if i can get the package installed the way it was intended. 

P.S remeber when ever you restart the machine you will need to run the **sudo -s huawei-mobile.sh** command

P.S.S if you want to disconnect from the internet run **poff** in Terminal

Enjoy!!!

---

### Post by lynx75 on 2007-08-03
Hi Nunu, I've got the same problem with my Vodafone 3 Card model E620 with Ubuntu 7.04.

My post is linked below :

[http://ubuntuforums.org/showthread.php?t=514951&highlight=vodafone](http://ubuntuforums.org/showthread.php?t=514951&highlight=vodafone)

Unfortunately at this moment no one help me with this issue. 
If you need more information try to download the documentation in the link below:

[http://www.vodafonebetavine.net/web/guest/projects/open_source?p_p_id=bvblogs&p_p_action=0&p_p_state=normal&p_p_mode=view&p_p_col_id=column-2&p_p_col_pos=1&p_p_col_count=2&_bvblogs_struts_action=%2Fext%2Fbvblogs%2FviewPost&_bvblogs_postId=243&#p_bvblogs](http://www.vodafonebetavine.net/web/guest/projects/open_source?p_p_id=bvblogs&p_p_action=0&p_p_state=normal&p_p_mode=view&p_p_col_id=column-2&p_p_col_pos=1&p_p_col_count=2&_bvblogs_struts_action=%2Fext%2Fbvblogs%2FviewPost&_bvblogs_postId=243&#p_bvblogs)

It's an absolutly frustation, I must use my 3g card, but if I won't work in a short time I must use windows on my laptop.

Bye,
lynx

---

### Post by uberdonkey5 on 2008-07-15
New to forum and pretty new to ubuntu (Sept 2007). I was gonnna give up with Linux due to connection problems with my vodaphone connect pen (the virtually virus free aspect of Linux on the internet was one reason I wanted to use it).

Like other users, I had a problem with computer identifying pen (I use Inspiron 1520). Also, when I tried downloading from official site it didn't load. Jes' can't find site I did download it from but basically I just used gutsy gibbon version (7.10) though I now have 8.10.

Anyhow, I solved problem of pen not being recognised just by putting the pen in a different USB port.

---

