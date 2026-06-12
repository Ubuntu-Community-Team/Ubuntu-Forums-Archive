---
title: "Ubuntu vs Mandriva ADSL USB rundown"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by dyadya_sam on 2005-07-08
Hello !
I'll try not to bore you to death with newb questions, really, although I am what you call a newb  :-)  I found the relevant information on the forums, but it's a bit contradictory in suggesting different ways of installing and different from what I did under Mandriva (for example,[http://www.ubuntuforums.org/showthread.php?t=10995&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=10995&highlight=conexant)) and dated as well. 

So let me just do a rundown of things I do under Manvdriva and the problems I'm having when using the same aproach in Ubuntu. Maybe then you can help me sort this mess out.

Off we go, then. I have a Zyxel Prestige 630 USB ADSL, based on the conexant chip and I install it to connect over PPPoATM.

1) First under Mandriva, I make sure the pppoatm package is installed. As far as I understand, Ubunty has ppp 2.4.2  with custom patch that includes PPPoATM. So in Ubuntu I do nothing at all. Is that correct ?

2) Secondly I hotplug my firmware. I just put it under /usr/lib/hotplu/firmware

3) I get the kernel source. And here is the first problem. There is a linux-source-2.6.10 folder, which is I guess what I need. But I can't find the relevant packages in synaptic (although on the forums exactly that was suggested to get the kernel source). And of course I dont have a connection to get it off the net.

4) The there is the /drivers/usb/atm subtree which i get from Accesrunner and put in the kernel tree. As far as I understand the 2.6.12.2 kernel has these drivers already included, so do you think I should get the source from kernel.org, uncompress in /usr/src and use that instead ?

5) Next, I configure and compile the kernel

6) Next I use adsl-setup to setup parameters

7) Then I install linux-atm and linux atm libs (which as far as I know are available as a ubuntu package)

8) Then I compile and install br2684ctl.c
[http://home.regit.org/datas/br2684ctl.c](http://home.regit.org/datas/br2684ctl.c)

and the stdsl.sh script
[http://www.rsw.sk/linux/adsl/stdsl.sh](http://www.rsw.sk/linux/adsl/stdsl.sh)

And, voila ! stdsl.sh start and thats it ! I hope with you corrections, this could be a base for a HOWTO for people with similair hardware.Well, if you can point me in the direction of the**definitive** HOWTO you won't have to answer this  :grin:

---

### Post by dyadya_sam on 2005-07-08
[QUOTE=dyadya_sam]Hello !
I'll try not to bore you to death with newb questions, really, although I am what you call a newb  :-)  I found the relevant information on the forums, but it's a bit contradictory in suggesting different ways of installing and different from what I did under Mandriva (for example,[http://www.ubuntuforums.org/showthread.php?t=10995&highlight=conexant](http://www.ubuntuforums.org/showthread.php?t=10995&highlight=conexant)) and dated as well. 

So let me just do a rundown of things I do under Manvdriva and the problems I'm having when using the same aproach in Ubuntu. Maybe then you can help me sort this mess out.

Off we go, then. I have a Zyxel Prestige 630 USB ADSL, based on the conexant chip and I install it to connect over PPPoATM.

1) First under Mandriva, I make sure the pppoatm package is installed. As far as I understand, Ubunty has ppp 2.4.2  with custom patch that includes PPPoATM. So in Ubuntu I do nothing at all. Is that correct ?

2) Secondly I hotplug my firmware. I just put it under /usr/lib/hotplu/firmware

3) I get the kernel source. And here is the first problem. There is a linux-source-2.6.10 folder, which is I guess what I need. But I can't find the relevant packages in synaptic (although on the forums exactly that was suggested to get the kernel source). And of course I dont have a connection to get it off the net.

4) The there is the /drivers/usb/atm subtree which i get from Accesrunner and put in the kernel tree. As far as I understand the 2.6.12.2 kernel has these drivers already included, so do you think I should get the source from kernel.org, uncompress in /usr/src and use that instead ?

5) Next, I configure and compile the kernel

6) Next I use adsl-setup to setup parameters

7) Then I install linux-atm and linux atm libs (which as far as I know are available as a ubuntu package)

8) Then I compile and install br2684ctl.c
[http://home.regit.org/datas/br2684ctl.c](http://home.regit.org/datas/br2684ctl.c)

and the stdsl.sh script
[http://www.rsw.sk/linux/adsl/stdsl.sh](http://www.rsw.sk/linux/adsl/stdsl.sh)

And, voila ! stdsl.sh start and thats it ! I hope with you corrections, this could be a base for a HOWTO for people with similair hardware.Well, if you can point me in the direction of the**definitive** HOWTO you won't have to answer this  :grin:[/QUOTE]
 Well, after figuring out how to make an offline repository, the aproach is proven to work once again.

So now, there is only the question of configuring ny pppoatm connection.
And there seems to be no adsl-setup util in sight ... That's interesting...

---

### Post by dyadya_sam on 2005-07-08
After a whole day of dodgy dealings it's all set up and working. I guess, a HOWTO for conexant chipsets is underway (since there is only one for the speedtouch one)

Ubuntu turned out to be really, really great !!! And much more ! I am happy I finally decided to try this wonderful distro !

---

