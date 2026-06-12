---
title: "Acer 3820tg battery life"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by redmorning on 2010-11-04
Hi folks,

I bought my new laptop Acer 3820 tg 2 months ago. Installed a fresh ubuntu 10.04, dual boot with windows 7 (already installed). I had problems with brightness, microphone, headphones etc. i solved all of them (thanks to ubuntuforums). The last and one of the most important issue is the battery life. In windows i get more than 5 hours battery life but in ubuntu it is maximum 1 hour 35 min. This is probably related to graphic card that i use. I tried to activate "ATI/AMD proprietary FGLRX graphics driver", the result is, like already mentioned in many threads, blank screen after booting ubuntu. As i know there isn't a solution for this graphic driver yet. So now i'm using the intel. 
I'm not sure and want to ask this if these subjects are related (battery life - graphic card) or not, is that the reason? 
-If so and you already know a workaround please let me know.
-If not, what may cause the short battery life?

Everytime battery is full i plugout the laptop to keep battery live longer. (I'm not sure if this is a good strategy) So 1h 35 min, too short.

Thanks in advance.

---

### Post by redmorning on 2010-11-07
bump!

---

### Post by f4lkon on 2010-11-11
Hi. You have to disable the Radeon Card.

Open up Terminal and type

```
gedit timelinex_acpi.c
```

paste the following code inside and save.

```
/* 
 * timelinex_acpi.c
 * 
 * Linux kernel module that disables the discrete graphics board for Acer
 * Aspire TimelineX 3820TG (Core i5). Other TimelineX laptops could work, but I don't know.
 *
 * Based on the original lenovo_acpi.c by Sylvain Joyeux <sylvain.joyeux@m4x.org>, 2009
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle); //     status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("timelinex_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("timelinex_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 0; //     atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("timelinex_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("timelinex_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);
```


Close the file timelinex_acpi.c and create a new file with

```
gedit Makefile
```

and paste following code inside

```
ifneq ($(KERNELRELEASE),)
  obj-m := timelinex_acpi.o
else
  KERNELDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif
```


save and close the Makefile. Now you have to type following:



```
make
sudo cp timelinex_acpi.ko /lib/modules/`uname -r`/kernel/

sudo depmod

echo timelinex_acpi | sudo tee -a /etc/modules > /dev/null
```


done. Deny Radeon module to start with

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and add following string at the end

```
blacklist radeon 
```

After reboot your Radeon is deactivated.

Now you can install TLP.

```
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp
```

Start tlp with 
```

sudo tlp bat
sudo tlp start
```

Now you should have an energy consumption between 10W and 12W in idle.

---

### Post by redmorning on 2010-11-11
f4lkon,

I followed your steps and saw the increasing time so fastly, now i'm testing it with 
```
acpi -V
```
i calculated that it will be about 4 h 30 m, but not sure for now. Recharging it now and post the results here as soon as possible.

by the way,man, THANK YOU VERY MUCH, i'm really very happy. for all scripts, thank you.

i just want to ask; do i have to put this 
```
sudo tlp bat
sudo tlp start
```
to startup to run them in every boot?

---

### Post by f4lkon on 2010-11-13
hi. once setuped it should be fine. set tlp into battery mode with sudo tlp bat. check the settings with tlp-stat. restart and check again with tlp-stat.

---

### Post by redmorning on 2010-11-13
thank you very much.

---

### Post by ipcnx on 2011-01-02
**f4lkon, **Thanks! You your post is very helpful to me.

---

### Post by worldsayshi on 2011-02-12
Confirming that f4lkon's solution is at least not harmful (to me anyway).

Telling from a short observation period, battery life seems significantly improved (5 hours estimated!) and temperature also seems to have dropped. 

Thanks f4lkon!

**Update:** This can be harmfull, see below. Lately, f4lkon's solutions shouldn't be needed. Read on.

---

### Post by redmorning on 2011-02-12
f4lkon, i'm still grateful to you,

i just want to add a little remark; 
In each kernel update you have to go through those steps again, 
```

sudo tlp bat
sudo tlp start

```
is not enough, so delete old auto-created files and re-run necessary commands (just above).

---

### Post by worldsayshi on 2011-02-14
Ouch. Seems the solution may have caused some serious trouble after all, directly or indirectly. The latest kernel isn't booting. Running the old kernel works but leaves me with old battery consumption.
  Unsure what to do...

Can I get the error output from booting the new kernel somehow? I can see errors on the screen as I boot. The bootup freezes after a long series of error messages.

**Update2:** This can be harmfull, see below. Lately, f4lkon's solutions shouldn't be needed. Read on.

---

### Post by Avitensis on 2011-02-16
Hi to all,
I have some problems with this walktrough. Editing the timelinex_acpi.c was no problem. Creating the makefile works too (even if I wondered that gedit didn't ask for a name while saving the new file), but afterwards the problems begin:
the make command retrieves the following:

[I]oliver@oliver-Aspire-3820:~$ make
make -C /lib/modules/2.6.35-25-generic/build M=/home/oliver  modules
make[1]: entering '/usr/src/linux-headers-2.6.35-25-generic'
scripts/Makefile.build:44: /home/oliver/Makefile: File not found
make[2]: *** no rule to create »/home/oliver/Makefile« end.
make[1]: *** [_module_/home/oliver] error 2
make[1]: leaving '/usr/src/linux-headers-2.6.35-25-generic'
make: *** [default] error 2
oliver@oliver-Aspire-3820:~$ [/I]

(I had to translate the german passages, hope thats correct)
It seems that there are some serious errors in this part but I don't know where exactly the problem is.Can sombode help me pls!?
Thanks in advance AvI

---

### Post by Tuul on 2011-02-17
Having some quite serious issues after applying the fix.
Unable to suspend/hibernate.
Investigations of syslog took me to this:
```
radeon 0000:02:00.0: IH ring buffer overflow (0xFFFFFFFF, 65535, 65550)
radeon 0000:02:00.0: IH ring buffer overflow (0xFFFFFFFF, 15, 65550)
Freezing of tasks failed after 20.01 seconds (1 tasks refusing to freeze):
modprobe      D f4d7be60     0   716      1 0x00800004
f4d7be70 00000086 00000002 f4d7be60 f4d7be4c c05d99e0 c08c4700 c08c4700
fdd85ab3 00000001 c08c4700 c08c4700 fd84edfb 00000001 00000000 c08c4700
 c08c4700 f4cde580 00000001 f70db894 f70db898 ffffffff f4d7be9c c05c8fb6
Call Trace:
[<c05c8fb6>] __mutex_lock_slowpath+0xd6/0x140
[<c0400fe8>] ? really_probe+0x98/0x150
[<c05c8ec5>] mutex_lock+0x25/0x40
[<c040114e>] __driver_attach+0x4e/0x90
[<c04005a3>] bus_for_each_dev+0x53/0x80
[<c0400e6e>] driver_attach+0x1e/0x20
[<c0401100>] ? __driver_attach+0x0/0x90
[<c0400835>] bus_add_driver+0xd5/0x280
[<c036d010>] ? pci_device_remove+0x0/0x40
[<c040147a>] driver_register+0x6a/0x130
[<c036d315>] __pci_register_driver+0x45/0xb0
[<f94f7017>] alsa_card_azx_init+0x17/0x19 [snd_hda_intel]
[<c0101132>] do_one_initcall+0x32/0x1a0
[<f94f7000>] ? alsa_card_azx_init+0x0/0x19 [snd_hda_intel]
[<c0180cbb>] sys_init_module+0x9b/0x1e0
[<c0219472>] ? sys_write+0x42/0x70
[<c05ca5d4>] syscall_call+0x7/0xb
...restarting tasks done...

```

The same is also present on the screen while suspending for what I guess must be  20 seconds and a blank screen after that as if i had locked the machine.

battery life's awsome tho ;)

---

### Post by worldsayshi on 2011-02-24
The kernel wouldn't boot today. Had to switch to the previous kernel, without the fix. Seems to have caused kernel panic. This has happened 'on occasion' before but now it doesn't boot even for repeated restarts. How would I go about reverting this fix in the newest kernel from this older one?

UPDATE: I removed the blacklist and the inclusion of this module in /etc/modules. Now the (newer) kernel is booting again. Back to lousy battery time... Might try rebuilding and reinserting the module some other time. Is there possibly a newer version of this fix?

**Update:** Lately, f4lkon's solutions shouldn't be needed. Read on.

---

### Post by Sxooter on 2011-03-01
I too got this problem.  I fixed it by doing what you said, removing the radeon from the blacklist, then after booting I went into the directory in my home where I built the timelinex_acpi.ko file originally.  ran make again, copied it back to the /lib/.... /kernel dir same as before over the old one, put the radeon back in the black list and viola, I'm booting again without the ATI card eating my battery.

---

### Post by andregus on 2011-03-11
I did that and it seems to be working but how can I see if the API card is really turned off?

---

### Post by worldsayshi on 2011-04-18
Here's a related thread. And the origin of the timeline_acpi fix it seems. There is probably more info there. I have only looked into it a little bit:
[http://ubuntuforums.org/showthread.php?p=9446283#post9446283](http://ubuntuforums.org/showthread.php?p=9446283#post9446283)
(The fix code is in its entirety at the bottom of the page.)

Another possibly helpful community doc page:
[https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline)

---

### Post by Sxooter on 2011-04-18
With Ubuntu 10.10 all I have to do now is

sudo su
echo "OFF"  > /sys/kernel/debug/vgaswitcheroo/switch

and it's off.  You can tell because now the battery shows ~4.5 hours or so instead of ~2 hours left.

---

### Post by andregus on 2011-04-20
> **Sxooter said:**
> With Ubuntu 10.10 all I have to do now is

sudo su
echo "OFF"  > /sys/kernel/debug/vgaswitcheroo/switch

and it's off.  You can tell because now the battery shows ~4.5 hours or so instead of ~2 hours left.

That's right but last time I tried that it was quite buggy. I'm not sure what the problem was but I think it caused kernel panic quite often. Have you had any problem with that?

---

### Post by Sxooter on 2011-04-20
I've had no problems with kernel panics or anything doing that.  But I just started using it a few weeks ago. Before that I was using acpi_call which worked fine but the machine couldn't suspend and wake up.

---

### Post by worldsayshi on 2011-04-26
> **Sxooter said:**
> With Ubuntu 10.10 all I have to do now is

sudo su
echo "OFF"  > /sys/kernel/debug/vgaswitcheroo/switch

and it's off.  You can tell because now the battery shows ~4.5 hours or so instead of ~2 hours left.

Seems to work for me as well. :D Hope it stays that way.

There goes another reason for using Windows now and then.

Update: Still seems to work fine. I don't use hybernation very often so haven't tested that much.

---

### Post by Sxooter on 2011-04-26
After further testing, suspend works fine, but hibernate, the machine wakes up with the GPU powered up and gets ~2 hours of battery life, and there's no way top turn it off without a reboot.

---

### Post by 3177 on 2011-04-26
In my experience, acer laptops never get much more than 2 hours using ubuntu 10.04+.
Back 9.04,9.10 mine got 3 hours, (4720z by the way) but that was with display and what not turned down. As for sleep or hibernate, they,ve never worked after the first update for me. this doesn't effect me though as I have it set to shutdown when I put the screen down, and my system re-boots in 11 sec.

---

### Post by Sxooter on 2011-04-26
Well the 4820 and it's brethren have pretty big batteries, so that helps. 4 hours is typical now for me with full screen brightness and wifi on just browsing / email etc.  Suspend has worked perfectly whether or not I use vga_switcheroo, but the acpi_call method means suspend breaks.

---

### Post by Cangar on 2011-04-29
Hi all,

i just started using ubuntu 10.10 and also thought, better battery lifetime would be sort of nice.

the problem by now is, that everything just broke. i did everything exactly like said at the first page and then tried to reboot to finish it. 

yeah. how to say... i cant get into my ubuntu anymore, cant edit anything, it just wont boot. there is a gigantic list of error messages and then it just stops doing anything. 
problem is, that i urgently need to use it for university. i was wondering to install it again in a virtual box and just forget the rest... 

did anyone experience anything like that? anything i can do now? i tried to start it with the second mode (asks me while booting after telling it to boot ubuntu) and the difference is the following: in the first just stops and i get a black screen. the second mode gives me a screen and then stops after giving me all those error messages.

i´m quite frustrated, because i need to have my ubuntu -.-'
thought i´d just go through that thing at the first page and get my good battery lifetime and now that -.-


hope you know what to do (just to mention, im not a linux pro ;) used windows all the time, just now for the university...)

cangar



edit: i was able to boot with the 3rd mode, just a question, what are  these settings? seems to be like it was before, because when i wanted to  edit that things i've done away, they just werent there. i just want to  restore my ubuntu like it was before... and then look for another thing  how to get more battery life... can it be, that the mistake was,  because i have 10.10 and the code was for 10.04?

edit 2: a friend told me that the settings while booting are the kernel... now i know why its working with the old one. the copy thing just goes into the new. i now deleted the copied file in that lib directory (timelinex_acpi.ko) and reedited the blacklist back to before. furthermore i deleted everything in my home directory that had to do with it. it now boots again with the new kernel, but takes longer than before! does anyone know what that might be?
i also tested to remake all of this and do it again like explained up in here, but it didnt work. exactly the same... the sudo echo "OFF" > /sys/kernel/debug/vgaswitcheroo/switch command didnt work, because he didn find the file... i looked for it and there is no vgaswitcheroo directory... any hint here? i be really pleased to turn off that radeon card, i dont need it with ubuntu -.- also i want to edit the screen brightness, but thats another thing...

edit again: learned something agian ;) i rebooted in the new kernel and there it was: the switch thing. so i was able to change that settings, now there is OFF at the first one, pwr and a + at the second one. it works! but still at booting there seems to be something not working right, i can see a flash of letters and think i can read something like error or so... but it is booting and working and i now have much more battery life, so thank you and sorry for editing all the time :D whoever reads this, i hope you dont make the same mistake! if u have ubuntu 10.10 just forget, whats on page 1 and just edit that switch file! now i check up that brightness thing ;)

---

### Post by Cangar on 2011-04-29
Hi all again,


i think, that problem changed something really important in my ubuntu... booting and shutting down now takes loads more time. whats quite disturbing: today i managed to get my multitouch pad running, but after some hours, it wont work again. i used the same script... furthermore while shutting down and boot, there are even more error messages now -.- can anyone tell me, how to get my system back to how it was before doing what it says on page 1???


thanks,
cangar

---

### Post by jimbox on 2011-05-07
Hi all,

Has anyone gotten 11.04 to dual boot successfully with Windows? I've been trying forever and always end up with a blank screen on startup (right after I select linux in grub but before any purple ubuntu screen) and having to reinstall. One thing I noticed though is that it boots into ubuntu fine if I select discrete in BIOS or if I select to boot with the 2.6.35-28 kernel. So I don't know if it could be a problem with the switching or the kernel. Any help would be much appreciated!

-JimboX

---

### Post by worldsayshi on 2011-05-17
Edit: Double posted...

---

### Post by arj154 on 2011-10-17
hi, because im stupid, i restarted after i blacklisted the graphics card and i hadnt installed that other thing. So how do i make it work again?

---

