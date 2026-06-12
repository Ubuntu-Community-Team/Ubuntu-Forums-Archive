---
title: "Wireless Problems"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by wheelern on 2010-07-02
Ok, so I am very, very new to Linux and Ubuntu. I recently installed Ubuntu 10.04 with Wubi on my notebook to run it along Windows 7. I'm using an HP Pavilion dv5 1235dx, nothing fancy but it does the job. Installation of Ubuntu went smoothly, as far as I can tell, but there is something going on with the drivers for my wireless card. I know there have been some bugs with my card (Broadcom BCM4312 14e4:4315), but I haven't been able to get it working. I have not yet tried a simple ethernet connection, haven't gotten the chance. I followed this steps from [http://bit.ly/diBnoD]("http://bit.ly/diBnoD"), but that doesn't seem to work. Something changes in the network connections, but it acts like the wireless card isn't even enabled. The unfortunate thing about my notebook model is that the way to enable wireless is via a heat-sensor button. There's not a real good way to tell whether or not you've turned it on or off. Usually it changes colors, but nothing happens when I'm using Ubuntu. Is there anything I can do? Maybe a way in the terminal to enable my card? I'm not very experienced in working in the terminal, but if you take me through step by step I will be able to do it.

If you need me to give you any more info, just give me the code to work through.

Thanks, in advance :)

---

### Post by apb2390 on 2010-07-02
For my ASUS netbook, my broadcom card was causing some trouble too. I would recommend trying madwifi (attached at bottom of post).

To install madwifi, you'll need to download madwifi to your home folder. Then you'll need to extract the madwifi files to a ,directory using the terminal. Open up a terminal ( Keyboard Shortcut "ctrl + alt + t" OR Applications > Accessories > Terminal) and type
```
cd ~/
```
than type:
```
tar -gunzip madwifi-hal-0.10.5.6.tar.gz
```
and it will extract it.

After this you'll need to install th software, in a terminal, type
```
cd ~/madwifi-hal-0.10.5.6-r4100-20090929
```
then configure it by typing
```
./configure
```
then
```
make
```
and finally
```
sudo make-install
```

Let them run, than once they're done, reboot. Attempt to connect to a wireless network, and see if it works!

Link [http://www.mediafire.com/?35mjdx2n21g](http://www.mediafire.com/?35mjdx2n21g)

Cheers,
apb

---

