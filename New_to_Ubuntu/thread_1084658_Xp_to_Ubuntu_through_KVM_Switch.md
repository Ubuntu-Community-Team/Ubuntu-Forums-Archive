---
title: "Xp to Ubuntu through KVM Switch"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by GrimmReaperVI on 2009-03-02
I link my old XP computer with the Vista partition (when Vista boots up) of my new computer via a KVM switch. How do I link my XP with my Ubuntu partition? (when Ubuntu boots up?) I'm using the latest version. :confused:

---

### Post by Dougie187 on 2009-03-02
Personally I am confused by your post.

Do you mean, you have two computers, one with vista and one with ubuntu, and you want to use a KVM switch to connect both to the same monitor and keyboard/mouse?

Or, do you mean that you have one computer, with two partitions on it, one with vista, and one with ubuntu, and you want a KVM switch to switch between partitions?

If you mean the latter, I don't think it can be done.

Also, I guess you might mean, that you have two computers, one with xp, and the other with vista and ubuntu, and you want to link the xp to the vista/ubuntu machine with a KVM switch. 

In this case, you can't directly link it with a specific partition on the second computer, but if you boot the second computer up into ubuntu, then it should be as straightforward as setting it up in vista.

---

### Post by GrimmReaperVI on 2009-03-02
> **Dougie187 said:**
> Also, I guess you might mean, that you have two computers, one with xp, and the other with vista and ubuntu, and you want to link the xp to the vista/ubuntu machine with a KVM switch. 

In this case, you can't directly link it with a specific partition on the second computer, but if you boot the second computer up into ubuntu, then it should be as straightforward as setting it up in vista.

Sorry to confuse you, I have 2 PCs. Well, I don't think it's straightforward... I put the cd in (which is Windows compatible) and...where do I install the driver? I tried wine, but I can't find a reasonable directory to install stuff... Plus, I try switching PCs after I've installed it (somewhere in the desktop :P) and it doesn't work...

---

### Post by maybeway36 on 2009-03-02
The KVM switch I used to use doesn't need a driver, you just press a button with your foot. :)

---

### Post by robert shearer on 2009-03-02
> **GrimmReaperVI said:**
> Sorry to confuse you, I have 2 PCs. Well, I don't think it's straightforward... I put the cd in (which is Windows compatible) and...where do I install the driver? I tried wine, but I can't find a reasonable directory to install stuff... Plus, I try switching PCs after I've installed it (somewhere in the desktop :P) and it doesn't work...

KVM switch operations will vary with brand/model.
What instructions for changing between computers does yours use? What happens when you use them?

Mine changes computers by tapping the 'scroll-lock' key twice followed by the 'esc' key once.  (it needed no drivers for linux or windows just plugged and worked)

With Ubuntu the xorg.conf file needs to be edited as the default monitor setting is based on the kvm switch.(it will 'see' this as it is between the computer and the monitor.)

I had to add lines to xorg.conf that specified the monitor brand, model, vertical and horizontal sync ranges.
Once this had been done I could boot into a desktop with my desired resolution (1024x786) rather than the default it had set (800x600)

---

### Post by GrimmReaperVI on 2009-03-04
My switch's combination is scroll lock three times. Nothing happens when I press it :(
What should I add to the xorg.conf?

---

### Post by robert shearer on 2009-03-04
> **GrimmReaperVI said:**
> My switch's combination is scroll lock three times. Nothing happens when I press it :(
What should I add to the xorg.conf?

Well, maybe you need to make sure that the kvm switch is working correctly first.
Does your Windows computer show up when connected to the switch?
Are you able to connect another Windows computer and see if it will switch between the two.?

This would help as you would then know if you are trying to configure Ubuntu to work with a **working kvm switch.**

A switch **should **just plug and play and the xorg.conf mod is just to change the default resolution.

Here is the modified section of my xorg.conf...

Section "Monitor"
	Identifier	"Configured Monitor"
	VendorName      "Acer"
         ModelName      "AC713"
        Option          "DPMS" "true"
        HorizSync       30.0-72.0
        VertRefresh     50.0-160.0
EndSection

Note that this is for my Acer monitor and yours will be different. 
**You must use the correct  HorizSync and VertRefresh  for your monitor or you may damage it severely!**

Google for the specifications of your monitor and use those.

to edit the xorg open a terminal and type..

```
sudo gedit /etc/X11/xorg.conf
```

hit enter and the file will open,

then scroll down and add the details that you have found for **YOUR** monitor.

save and close then reboot.

NOTE You should backup the xorg.conf first so that it can be reinstated if things go pear-shaped.

This new xorg tells Ubuntu to use the parameters listed when it boots rather than probing the monitor(or kvm switch) at each boot.
You will need to change it or reinstate the original if you change monitors.

---

