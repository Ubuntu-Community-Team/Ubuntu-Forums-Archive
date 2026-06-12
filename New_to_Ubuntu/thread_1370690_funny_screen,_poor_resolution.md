---
title: "funny screen, poor resolution"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by albert s on 2010-01-02
ubuntu 9.10
hi everyone, and thanks for all your help on my partition woes.
this one may be harder, though prob dead easy for you guys,
my screen is really weird, everything is loads bigger than it should be, TOO low res...????
AFAIK it is a Nvidia card, I have looked at a couple of other threads here but Im a bit lost, sorry.
any help much appreciated.
my main problem is pages DONT fit on the screen, even this page requires me to drag it back and forwards.........

thanks.

---

### Post by Methuselah on 2010-01-02
Did you install the nvidia restricted driver or is it still using the driver that came with Ubuntu?

---

### Post by albert s on 2010-01-02
I think I did, I just done a clean install of 9.10 and it told me i needed to install restricted drivers, so I did, Im pretty NOOB at this. and Nvidia settings is showing up on the apps screen.

ps, its a standardish 4:3 LCD if that makes a difference

---

### Post by Methuselah on 2010-01-02
In a terminal do,

```
sudo nvidia-xconfig
```

Then restart and let us know.

---

### Post by albert s on 2010-01-02
no difference, I think Ive included a screenshot  to help you see whats wrong.  [IMG]file:///home/mark/Desktop/Screenshot.png[/IMG]/home/mark/Desktop/Screenshot.png

[IMG]file:///home/mark/Desktop/Screenshot.png[/IMG][IMG]file:///home/mark/Desktop/Screenshot.png[/IMG]

---

### Post by Methuselah on 2010-01-02
To insert an image from your hard-drive you have to select the attachment button ( a little paperclip ) when making a post.
Browse for it and upload then post.

---

### Post by Methuselah on 2010-01-02
Try running the NVidia Settings program you see in your menu.
Select 'X Server Display Configuration' on the left.
Then on the right, on the display tab, see if you can change the resolution.
It is probably set to 'auto' right now.

---

### Post by albert s on 2010-01-02
working now,  ?

---

### Post by Methuselah on 2010-01-02
Yeah, you got it.
Try what I said just before your last post.
640x480 resolution is very out of style.

---

### Post by albert s on 2010-01-02
does this look about right? it looks a lot better to me anyway,  :D

---

### Post by Cheesemill on 2010-01-02
Looks good to me :)

---

### Post by J V on 2010-01-02
Yes, A lot better, but most screens can get 1280 x 1024 or better nowadays... Know what your screen can handle?

---

### Post by Methuselah on 2010-01-02
Yup, that is a lot better.
Good job!

You might want to execute

```

gksu nvidia-settings

```

In a terminal. (Accessories->Terminal)

And when the settings-manager comes up, verify the right resolution and hit the 'Save to X configuration' button.
Otherwise, I'm afraid it might revert to what it was before whenever you restart and you'd hav to keep resetting it manually.

---

### Post by albert s on 2010-01-02
no idea, but at least I get a full page on this setting.
do I just experiment?

---

### Post by albert s on 2010-01-02
it wont allow me,

---

### Post by J V on 2010-01-02
You could but if you get the wrong one you will be stuck until it resets :)

Under my nvidia xserver settings the "auto" choice gets it right, and I'm pretty sure it only shows resolutions it can handle...

Set it to auto, if its the same or too small, you can set it to the highest there...

Edit: Move the window if you're going to double screenshot :)

---

### Post by albert s on 2010-01-02
> **J V said:**
> You could but if you get the wrong one you will be stuck until it resets :)

Under my nvidia xserver settings the "auto" choice gets it right, and I'm pretty sure it only shows resolutions it can handle...

Set it to auto, if its the same or too small, you can set it to the highest there...

Edit: Move the window if you're going to double screenshot :)



ok, but it keeps telling me  something is wrong, graphics are perfect at this setting,...

---

### Post by J V on 2010-01-02
Their as good as they used to be?

The error is worrying, I would get it looked at, but if thats the optimal res then keep it that way :)

---

### Post by albert s on 2010-01-02
> **J V said:**
> Their as good as they used to be?

The error is worrying, I would get it looked at, but if thats the optimal res then keep it that way :)


NO, this is the best setting they have ever been, just keeps telling me something is wrong with my settings, but I can live with that to reset them every time,(for the minute!)

---

### Post by J V on 2010-01-02
Found possible fix...

run this:
sudo nvidia-xconfig

And gratz on your graphics settings and enjoy ubuntu :)

Otherwise try this:
1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

Thread here: [http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)

---

### Post by albert s on 2010-01-02
> **J V said:**
> Found possible fix...

run this:
sudo nvidia-xconfig

And gratz on your graphics settings and enjoy ubuntu :)

Otherwise try this:
1)  open a terminal
2)  sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
2)  sudo touch /etc/X11/xorg.conf  
3)  sudo nvidia-settings
4)  hit "save configuration"

Thread here: [http://ubuntuforums.org/showthread.php?t=1101445](http://ubuntuforums.org/showthread.php?t=1101445)



Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


I really have no idea what this means, I have tried rebooting and it does mean having to go back and reset my graphics, annopying, but not the end of the world,.....

---

### Post by J V on 2010-01-02
ehm... I think it means it should work now... try rebooting...

---

### Post by Methuselah on 2010-01-02
You might need to rename the existing xorg.conf since the error is saying it cannot parse (understand) the existing one and so refuses to change it.

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksu nvidia-settings

```

Then try to save configuration.

[The mv command is 'move' which has the effect of a rename.]

EDIT: I just saw your last post...only do this if you need to after restarting.

---

### Post by albert s on 2010-01-03
thanks for all your help guys, but Im in big trouble now.
eventually got everything up and working, then it asked me to download restricted drivers again(????). I had driver ** installed and it recommended driver 185 (or similar) so I downloaded that and rebooted.
NOTHING HAPPENED......
blank screen, 
ctrl+alt+F2 gets me a command line.
Im doing this off the Live CD.
should I just re-install, there is nothing on the PC just yet, I only installed yesterday, and was just sorting out settings first.
thanks.

---

### Post by Don1500 on 2010-01-03
> **albert s said:**
> thanks for all your help guys, but Im in big trouble now.
eventually got everything up and working, then it asked me to download restricted drivers again(????). I had driver ** installed and it recommended driver 185 (or similar) so I downloaded that and rebooted.
NOTHING HAPPENED......
blank screen, 
ctrl+alt+F2 gets me a command line.
Im doing this off the Live CD.
should I just re-install, there is nothing on the PC just yet, I only installed yesterday, and was just sorting out settings first.
thanks.

In terminal 
```
lspci
```
 and post the results.

---

### Post by albert s on 2010-01-03
Im still running the live CD on the same machine if that makes any difference.


ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7500 LE] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

---

### Post by Don1500 on 2010-01-03
have you done a second re-boot?

(lspci from the live CD is OK, just starting over abd getting info on your system.)

---

### Post by albert s on 2010-01-03
yes, Ive tried to reboot 3 times.

---

### Post by J V on 2010-01-03
take the disk out and reboot...

Also, if you get to a virtual terminal, (ctrl alt F2) hit ctrl alt F7 to get back...

---

### Post by albert s on 2010-01-03
thanks for all your help guys,
I ended up re-installing 9.10 and installing the nvidia drivers before anything else and it found my monitor on AUTO.

---

