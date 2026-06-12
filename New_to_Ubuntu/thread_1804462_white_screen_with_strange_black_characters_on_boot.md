---
title: "white screen with strange black characters on booting?"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by pacman93 on 2011-07-14
Hi everyone, I just installed ubuntu 11.04 a few days ago because my old windows xp was running terribly slow and I wanted to try something new. The demoing with the usb drive worked fine but not so when I actually installed it as the sole OS on the laptop. Now when I try to boot up my laptop I only get the standard Dell loading screen, then a white background with many black verticle lines running down the screen and some strange black characters appearing. It then stays in that mode and never goes to the login menu. Whenever I try to type something, it all appears as the strange black characters. I tried pressing shift while the computer is loading like others suggested but couldn't bring up the grub menu. Can someone enlighten me on this? Thanks!

---

### Post by Rex Bouwense on 2011-07-14
I read your post twice and still am not sure if everything worked before you installed.  If that is the case, try booting from the CD or flash drive again.  Can you do that?

---

### Post by fdrake on 2011-07-14
i'd just reinstall everything again. something must have gone wrong with the install. If u can run a check at the cd-rom or at the usb to check that you have all the needed files.

---

### Post by Rex Bouwense on 2011-07-14
Could be a bad install, could be a bad burn (that was why I asked the question), could be a bad download.  We just don't have enough information.

---

### Post by wildmanne39 on 2011-07-14
> **pacman93 said:**
> Hi everyone, I just installed ubuntu 11.04 a few days ago because my old windows xp was running terribly slow and I wanted to try something new. The demoing with the usb drive worked fine but not so when I actually installed it as the sole OS on the laptop. Now when I try to boot up my laptop I only get the standard Dell loading screen, then a white background with many black verticle lines running down the screen and some strange black characters appearing. It then stays in that mode and never goes to the login menu. Whenever I try to type something, it all appears as the strange black characters. I tried pressing shift while the computer is loading like others suggested but couldn't bring up the grub menu. Can someone enlighten me on this? Thanks!Hi, post the information from this script so we can see where everything is located: You will need to boot with the livecd to do this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Jinda on 2011-07-17
I have the exact same issue on a new install of 11.04. If I manage to get grub menu and select recovery menu, i get white blocks on the screen and nothing legible.

If I go into BIOS menu and load failsafe defaults, then I can boot in, but If I shutdown, then the same problem recurs. It may be a graphics issue, but my technical knowhow is too limited at present.

---

### Post by amjjawad on 2011-07-17
> **pacman93 said:**
> Hi everyone, I just installed ubuntu 11.04 a few days ago because my old windows xp was running terribly slow and I wanted to try something new. The demoing with the usb drive worked fine but not so when I actually installed it as the sole OS on the laptop. Now when I try to boot up my laptop I only get the standard Dell loading screen, then a white background with many black verticle lines running down the screen and some strange black characters appearing. It then stays in that mode and never goes to the login menu. Whenever I try to type something, it all appears as the strange black characters. I tried pressing shift while the computer is loading like others suggested but couldn't bring up the grub menu. Can someone enlighten me on this? Thanks!

Hello and Welcome :)

You are required to provide more details so that we could offer the better help.

1) Is Ubuntu the only OS installed on your machine?

2) What's the Hardware Details of your machine where Ubuntu is installed?

3) Did you TRY Ubuntu from the LiveCD/LiveUSB before installing it?

4) Did you check [MD5SUM ]("https://help.ubuntu.com/community/UbuntuHashes")and burned the LiveCD at a low Speed?

---

### Post by wildmanne39 on 2011-07-18
> **Jinda said:**
> I have the exact same issue on a new install of 11.04. If I manage to get grub menu and select recovery menu, i get white blocks on the screen and nothing legible.

If I go into BIOS menu and load failsafe defaults, then I can boot in, but If I shutdown, then the same problem recurs. It may be a graphics issue, but my technical knowhow is too limited at present.
Hi, this information can help us help you.
Please run these commands in a terminal 
```
sudo lshw
```
```
lsmod
```
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

Also are you using unity or logging into classic?

---

### Post by pacman93 on 2011-07-30
Thanks everyone for the help. First to answer the Rex's question. I reinstalled three more times, each time reburning the USB, same issue still persists. To wildmann39, I couldn't run the script for some reason. I will try it again later. To amjjawad, Ubuntu is currently the only OS on my computer. As for hardware details:
```
Processor
Processor Intel Pentium M 1.4 GHz
Data Bus Speed 400.0 MHz
Chipset Type Intel 855PM
Cache Memory
Type L2 cache
Installed Size 1.0 MB
RAM
Installed Size 512.0 MB / 2.0 GB (max)
Technology DDR SDRAM - 333.0 MHz
Memory Specification Compliance PC2700
Form Factor SO DIMM 200-pin
```
When I try to boot from USB, it boots properly. I did not check MD5SUM when burning, didn't have the option to. Lastly to wildmanne39, here is the terminal display:  
```
aojia@aojia-Inspiron-8600:~$ sudo lshw
[sudo] password for aojia: 
aojia@aojia-Inspiron-8600:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
lib80211_crypt_wep     12747  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
nvidia               7098106  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ipw2100                77368  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
libipw                 46641  1 ipw2100
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
lib80211               14570  2 lib80211_crypt_wep,libipw
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
cfg80211              156212  2 ipw2100,libipw
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
dcdbas                 14054  0 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18951  0 
psmouse                73312  0 
parport_pc             32111  1 
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
b44                    35301  0 
firewire_ohci          31504  0 
ssb                    45942  1 b44
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
aojia@aojia-Inspiron-8600:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: unable to create the OpenGL context


```
Thanks everyone for all your help!:D

---

### Post by wildmanne39 on 2011-07-30
Hi, the information from lsmod is that while booted into ubuntu or from the liveusb?

---

### Post by pacman93 on 2011-07-30
Hi wildmanne39, it's from the terminal while booted into Ubuntu without USB (recovery mode of the previous linux release chosen from the grub menu). Thanks

---

### Post by wildmanne39 on 2011-07-30
Hi, ok it is good that you can get into recovery mode now, so do what this link says and you should be able to boot up and check additional driver to see if there is a driver in there for your video card.

You will need to be connected to the internet to check for the driver after you get into ubuntu.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by pacman93 on 2011-07-30
Hi wildmanne39, I entered nomodeset like the link said into my gedit file but I got this error:
```

(gedit:1676): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1676): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.0KJMZV': No such file or directory

(gedit:1676): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1676): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.JU3AZV': No such file or directory

(gedit:1676): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```
When I tried to reboot, it still doesn't work except in the recovery mode. As for the graphics driver, it's this: (I typed lspci in terminal)
```
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)

```
Thanks.

---

### Post by wildmanne39 on 2011-07-31
Hi, ok you need to read the link I gave you, you do not enter anything into gedit.

That is for you to enter when you first boot up, and if you are able to get into gedit then go into additional drivers or synaptic and remove your nvidia driver then reinstall it or if there is another one in additional drivers try it instead.

Also look in synaptic and make sure you have only one nvidia driver installed if you have two remove one.

---

