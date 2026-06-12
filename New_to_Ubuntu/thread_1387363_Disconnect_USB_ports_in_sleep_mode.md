---
title: "Disconnect USB ports in sleep mode"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by abhiroopb on 2010-01-21
When I put my laptop to sleep the USB ports keep supplying power to my external hard drive and my fan. Needless to say it is waste of electricity. Is there anyway to switch of the USB ports when the laptop is in sleep mode?

Thanks!

---

### Post by abhiroopb on 2010-01-22
Bumpety BUMP

---

### Post by warfacegod on 2010-01-22
Unplug them?

---

### Post by abhiroopb on 2010-01-22
Sometimes i forgot and the fan just keeps whirring all night long. It's too quiet for me to hear it and just wastes electricity.

---

### Post by warfacegod on 2010-01-22
I'd go looking in the Configuration Editor.

---

### Post by abhiroopb on 2010-01-22
thanks for the suggestion but I couldn't find anything there.

I am guessing I'll have to sort out something with HAL, but no idea how that works./

---

### Post by spillin_dylan on 2010-01-22
Have you checked in your BIOS configuration?  I think I remember seeing something like that on my Toshiba A300's bios setup screens.  "USB charge mode: sleep enable/disable" option or something along those lines.  Not entirely sure if that is a generic thing, or if it's more brand- or model-specific....

---

### Post by abhiroopb on 2010-01-22
From what I remember I haven't seen it. quite confident I don't have anything like that.

---

### Post by no2498 on 2010-01-23
i dont have a lap top
but dont you turn them off wile not in use ?
as in overnight 
910 karmic turns off my webcam if i shut down
804 will not and 710 did not turn it off 
2 computers both desk tops

---

### Post by Settwi on 2010-01-23
To everyone,
Sorry *but* it's not possible to turn the power off to the USB ports when your computer is in sleep  mode.  If it's shut off, you can remove the battery but that's all!
:popcorn: Sorry!

---

### Post by abhiroopb on 2010-01-23
Thanks for that :(

---

### Post by warfacegod on 2010-01-23
> **Settwi said:**
> To everyone,
Sorry *but* it's not possible to turn the power off to the USB ports when your computer is in sleep  mode.  If it's shut off, you can remove the battery but that's all!
:popcorn: Sorry!

Why couldn't you right a script to auto-unmount the USB stuff on Suspend or Hibernate?

---

### Post by abhiroopb on 2010-01-23
How would I go about doing that? And can I "unmount" a fan? 

I basically just want the power cut before it goes into sleep.

---

### Post by warfacegod on 2010-01-24
> **abhiroopb said:**
> How would I go about doing that? And can I "unmount" a fan? 

I basically just want the power cut before it goes into sleep.

Perhaps unmount was an unwise choice of words. No, you can't unmount a fan. But still don't see why writing a script to shut down the usb channels. As for writing it, I haven't a clue.

By the way, are you using Suspend or Hibernate?

---

### Post by abhiroopb on 2010-01-24
Yea thats exactly what I was looking for. 

Suspend - the power light keeps flashing so it's still drawing power.

---

### Post by warfacegod on 2010-01-24
When using Suspend, your System State gets stored in your RAM so there has to be power going to the RAM for it to remember. RAM is what is called volatile memory. Meaning if you cut the power supply to it, whatever it's storing will vanish.

Hibernate also saves your System State but it puts it in your swap space on your hard drive. Hard drives (obviously) are not volatile memory. Which means no power use.

I'd try using Hibernate to see if that shuts down your USB's. However, there's a catch. Your swap space nneds to be as big, if not slightly bigger, than the amount of RAM in your computer.

---

### Post by abhiroopb on 2010-01-24
Thanks. 

Yes I basically knew that. And the reason I suspend to RAM is because it's faster to come out of it (than hibernate). Anyway to cut power JUST to the USB ports?

---

### Post by warfacegod on 2010-01-24
I think it's possible to cut power just to the USB's, perhaps by disabling them, upon Suspend. However, the more I think about this the more I also think that this would be a very difficult thing to achieve. It would require a highly technical understanding of all the hardware involved as well as the software and the ability to write a script or modify the Suspend command.

This seems to be far more trouble than it's worth.

Are you running a fan to keep you cool or the computer?

---

### Post by abhiroopb on 2010-01-24
OK, honestly, I have no idea. So, I just threw it out on the forum.

Currently I have the following:

USB Port 1: Fan to keep computer cool
USB Port 2: Small backup hard drive
USB Port 3: USB hub for stuff like my external keyboard, mouse, webcam, etc.

Anyway I pull all three out as the fan and small external hard drive stay on.

The mouse and keyboard lights go out though. The Hub (belkin) has a separate power source though.

---

### Post by warfacegod on 2010-01-24
I would unmount the external hard drive before shutting down. Regardless of whether it's Hibernate, Suspend, Shutdown, or Restart.

---

### Post by abhiroopb on 2010-01-24
Doesn't it automatically unmount when you shutdown?

---

### Post by warfacegod on 2010-01-24
Personally, I don't trust mine to. I'm not interested in having to replace 260 GB of data because the unmount took too long in shutdown and the OS forced it to shut off. But yes, it should.

---

### Post by abhiroopb on 2010-01-24
Fair enough, but arguably, if you feel that the OS isn't good enough to accommodate a robust auto-unmount system then it's probably not robust enough to do proper copies, writes, reads, etc. etc. You get my point right?

Anyway little of topic!

Anyone else have any ideas?

---

### Post by warfacegod on 2010-01-24
> **abhiroopb said:**
> Fair enough, but arguably, if you feel that the OS isn't good enough to accommodate a robust auto-unmount system then it's probably not robust enough to do proper copies, writes, reads, etc. etc. You get my point right?

Anyway little of topic!

Anyone else have any ideas?

Not at all. I don't trust any OS to auto-unmount properly on shutdown. Whether it be Linux, Mac, or Windows. Especially Windows.

I really think your best solution is to use Hibernate after unmounting your external. Unmounting ought to make the wake up process faster.

---

### Post by abhiroopb on 2010-01-24
> **warfacegod said:**
> Not at all. I don't trust any OS to auto-unmount properly on shutdown. Whether it be Linux, Mac, or Windows. Especially Windows.

I really think your best solution is to use Hibernate after unmounting your external. Unmounting ought to make the wake up process faster.

I was talking more generally about external hard drive usage. I mean if, as you say, you don't trust the OS to auto-unmount then why do you trust it to properly write the data? (I'm not talking about different OSes here, just using the term generically).

---

### Post by warfacegod on 2010-01-24
> **abhiroopb said:**
> I was talking more generally about external hard drive usage. I mean if, as you say, you don't trust the OS to auto-unmount then why do you trust it to properly write the data? (I'm not talking about different OSes here, just using the term generically).

I trust the OS to auto-unmount just fine. I don't trust it to not force kill the process if it's taking too long or locks up during shutdown.

---

### Post by theozzlives on 2010-01-24
Your problem is you're using an active USB hub. The hub don't know the laptop is in suspend, therefore the power stays on. What I would do is see if there's such a thing as a "smart" hub. I don't think a script will cut the power in your case.

---

### Post by abhiroopb on 2010-01-24
No offence but if you'd read above you would have noticed that I was specifically talking about the fan and small external hard drive which are NOT connected through the hub. I don't really mind the hub staying on. But I don't want the HD and fan to always stay on.

---

### Post by theozzlives on 2010-01-24
> **abhiroopb said:**
> No offence but if you'd read above you would have noticed that I was specifically talking about the fan and small external hard drive which are NOT connected through the hub. I don't really mind the hub staying on. But I don't want the HD and fan to always stay on.

My USB on my laptop turns off on suspend. I've tried to charge my phone and it's a "no go". It's odd that yours don't turn off, cause suspend is only supposed to provide power to RAM and the blinking light.

---

### Post by mikechant on 2010-01-25
Have a look at this:
[http://www.linuxquestions.org/questions/linux-hardware-18/how-to-power-off-usb-port-613304/](http://www.linuxquestions.org/questions/linux-hardware-18/how-to-power-off-usb-port-613304/)

In particular, post #8 (I know post #5 says it's not possible but I'd still try this):

power off:
```
echo suspend >/sys/bus/usb/devices/1-2/power/level
```

power on:
```
echo auto >/sys/bus/usb/devices/1-2/power/level
```

replacing 1-2 with the appropriate port number

If /sys/bus/... as above doesn't exist, it might still work if you can find the right location.

If this does work, you can incorporate it into the suspend and resume process (I've seen posts about that before) but obviously try it manually first. Probably needs 'sudo echo...' to get the necessary permission.

---

### Post by abhiroopb on 2010-01-26
Thanks for the link. It looks exactly like what I need.

How could I set it up so that this happens before suspend and undo's after I come out of suspend?

---

### Post by mikechant on 2010-01-26
OK, I put the script shown below in directory
/usr/lib/pm-utils/sleep.d

I named it 85test (bit of a guess, the scripts in this directory run in sequence according to the 2-digit prefix) and made it executable with
```
sudo chmod ugo+x 85test
```

Script:
```
#!/bin/sh
##
## suspend-example.sh
##
case $1 in
   suspend)
     ## COMMANDS THAT YOU WISH TO RUN BEFORE SUSPEND
     echo suspend > /var/log/miketest.txt
   ;;
   resume)
     ## COMMANDS THAT YOU WISH TO RUN AFTER RESUME
     echo resume >> /var/log/miketest.txt
   ;;
   hibernate)
     ## COMMANDS THAT YOU WISH TO RUN BEFORE HIBERNATE
     echo hibernate
   ;;
   thaw)
     ## COMMANDS THAT YOU WISH TO RUN AFTER RESUME FROM SUSPEND TO DISK
     echo thaw
   ;;
esac 

```

This produced a file /var/log/miketest.txt with two lines saying 'suspend' and 'resume' when I did the suspend/resume operation.
So if the echo commands I described earlier work OK you should be able to just plug them into the script above instead of the logging commands.
Actually you might want to include some logging commands as well as the USB related commands while you're testing, just to prove the script is running, then remove them when working OK.

Credit: Script sample was found here:
[http://myricci.com/index.php?option=com_content&task=view&id=41&Itemid=9](http://myricci.com/index.php?option=com_content&task=view&id=41&Itemid=9)

---

### Post by abhiroopb on 2010-01-29
Not sure what happened. But, usually when I click the power button it goes into Suspend. I pressed it this time and I hibernated. Perhaps a bug with the script?

---

### Post by fermulator on 2010-07-11
All,

This is the script I'm using now which has resolved the issue for me in Ubuntu 9.04.

> user@pc:/usr/lib/pm-utils/sleep.d$ cat 85usb_power_mgmt
#!/bin/sh
##
## 85usb_power_mgmt
##
case $1 in
   suspend)
     ## COMMANDS THAT YOU WISH TO RUN BEFORE SUSPEND
     echo "$(date): suspend" >> /var/log/usb_power_mgmt.txt
   ;;
   resume)
     ## COMMANDS THAT YOU WISH TO RUN AFTER RESUME
     echo "$(date): suspend-resume" >> /var/log/usb_power_mgmt.txt
     modprobe -r -v whci_hcd && modprobe -v whci_hcd
   ;;
   hibernate)
     ## COMMANDS THAT YOU WISH TO RUN BEFORE HIBERNATE
     echo "$(date): hibernate" >> /var/log/usb_power_mgmt.txt
   ;;
   thaw)
     ## COMMANDS THAT YOU WISH TO RUN AFTER RESUME FROM SUSPEND TO DISK
     echo "$(date): hibernate-thaw" >> /var/log/usb_power_mgmt.txt
     modprobe -r -v whci_hcd && modprobe -v whci_hcd
   ;;
esac

Which produces the following log:
> user@pc:/usr/lib/pm-utils/sleep.d$ cat /var/log/usb_power_mgmt.txt
Sun Jun 27 17:58:21 EDT 2010: hibernate
Sun Jun 27 17:59:40 EDT 2010: hibernate-thaw
Sun Jun 27 18:00:37 EDT 2010: hibernate
Sun Jun 27 18:49:19 EDT 2010: hibernate-thaw
Sun Jun 27 20:22:51 EDT 2010: hibernate
Sun Jun 27 20:23:57 EDT 2010: hibernate-thaw
Sun Jun 27 20:32:58 EDT 2010: hibernate
Sun Jun 27 20:34:00 EDT 2010: hibernate-thaw
Sun Jun 27 20:36:14 EDT 2010: hibernate
Sun Jun 27 20:37:24 EDT 2010: hibernate-thaw
Sun Jun 27 20:48:46 EDT 2010: hibernate
Sun Jun 27 20:49:54 EDT 2010: hibernate-thaw

The important thing out of this is from the script:
> modprobe -r -v whci_hcd && modprobe -v whci_hcd

Essentially this is removing the usb driver, and reloading it after resuming from suspend (RAM) or hibernation (disk).  This worked for me in Ubuntu 9.04, but you might have to replace whci_hcd with a different driver...mileage may vary

Can someone please confirm this resolves the issue for them on the same and/or different Ubuntu releases?

---

