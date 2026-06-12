---
title: "acer aspire one"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by redbook4574 on 2008-09-27
I am trying to use hardy 8.04.01 on an acer aspire one with 120gb hdd

all seems fine but I cannot get the wireless to work - tried the wiki for madwifi but no joy - still not even detected.

Has any body got this working and if so how ??

---

### Post by redbook4574 on 2008-09-27
Well despite the fact that I am assured that the restricted drivers for the atheros wifi do not work on the aspire one, they are working on mine. So one problem down.

Now anybody know how to enable the sd card slots.

---

### Post by poldie on 2008-09-30
> **redbook4574 said:**
> Well despite the fact that I am assured that the restricted drivers for the atheros wifi do not work on the aspire one, they are working on mine. So one problem down.

Now anybody know how to enable the sd card slots.

I followed this guide:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
to getting Ubuntu on my Aspire and the instructions simply don't work as far as getting wifi to work reliably.  It worked briefly, then I tried a reboot and it was gone.  I followed the instructions to the letter.  I've tried sliding the wifi switch (and waiting for 20 seconds or so, in case it takes time to work), fiddling with the network set up (I must have entered my password 100 times) etc.  I can see my wireless router (plus a few others) so there's definitely some life in it, and occasionally I can get online, but sometimes it stops working, and it always goes away after a reboot.

I've tried the built in support.  When I disabled that, then reboot, then look at the settings, the boxes are unticked but there is a message next to them saying `in use` - so are they disabled, or not?

If I am to try them again in the same way you are, should I uninstall the madwifi stuff the guide I linked to above tells you install first?

Do you have any other tips/advice in this area I should try?  I've only been using Linux for a week or so, all on this device. First I tried Linpus, which seemed ok but a bit restricted and flakey.  Ubuntu "seems" better - although I've made it hang twice so far - but if I can't get wifi working I can't really continue with it.  Part of the point of getting this box was to gain experience with Linux, but I was hoping I could concentrate on learning other aspects than just trying to get on the internet!

---

### Post by blackest_knight on 2008-10-01
Re: acer aspire one
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

is pretty good for getting up and running with working wifi and card readers.

just make sure you don't miss a step.

Now we need to disable the hardware drivers that Ubuntu tries to use before the ones we make will function. So
0)
sudo apt-get update
sudo apt-get upgrade

1)
go to System -> Administration -> Hardware Drivers and uncheck everything. It should prompt us to reboot, so lets do it now.

We need to grab the wireless driver, and the things we need to build it, from a terminal:
2)
mkdir source
cd source
wget [http://snapshots.madwifi.org/madwifi...0080801.tar.gz](http://snapshots.madwifi.org/madwifi...0080801.tar.gz)
tar -xzvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo apt-get install build-essential linux-headers-$(uname -r)

And we build and install:

3)
make
sudo make install
sudo modprobe ath_pci

In order to have the wireless work after reboot,

4)
add the following line to /etc/modules ("sudo gedit /etc/modules") to automatically load the module when booting:

ath_pci

You should now have working wireless. However you may want to do the following to prevent problems (the symbol mismatch) when the module is loaded:

5)
Add ath_hal to the DISABLED_MODULES= stanza in /etc/default/linux-restricted-modules-common

(i.e. 'DISABLED_MODULES="ath_hal"')


if that still doesn't work and it might not try this

sudo apt-get install wifi-radar

sudo wifi-radar

worked for me the restricted drivers ubuntu installs initially need to be unchecked.

as for the card readers they seemed to work straight away initially for me but since i upgraded to 1.5 gb ram they seem to get read on an initial boot only and not when inserted??? strange.

the wifi lights don't work on the basis of the instructions given in the guide however the switch is recognised but i am not sure if it does anything with the events generated look at dmesg to see what i mean in the terminal

The 1 gb sim addition is well worth while but tricky coz of stupid cables.

reassembly should be done 1 stage at a time
ie replace the main board and the 2 screws and wifi card and the ssd ribbon then turn on and see if the ssd is found if it isnt adjust the ribbon cable its probably not sat correctly.

now attach facia and the touch pad and power up again to login window check touch pad is working. then attach the keyboard but dont click it in place till you boot and can login you might want to test most keys in a text editor or something then shut down click the keyboard home and attach the screws on the underside.

best to do it this way because you will only have to go back and fix the problems if the cables havent connected properly.

and don't fit a 2gb sodimm it doesnt work at all. no screen nothing (quite scary)

The base memory of 512 is too small for desktop ubuntu to run well (it needs swop). the SSD is very slow compared to the EEE and usually reading and writing to the disk is slowing the aspire down.

I'm going to move swop to the left sdcard but i hardly expect to use it now the ram is sufficient, better battery is the next issue, acer should never have gone for such a small battery its pathetic and ruins the whole portability of the aspire one. I think moving home to the sdcard is also a good idea still less writing to the ssd plus two streams to read and write too should make it perform better.

hope this helps i'm 48 hours into owning an aspire one but its shaping up to be a nice system.

---

### Post by poldie on 2008-10-01
> **blackest_knight said:**
> Re: acer aspire one
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

is pretty good for getting up and running with working wifi and card readers.

just make sure you don't miss a step.
 

Yeah, I did all that.  

8.10 is out this month - perhaps that'll fix it.

---

