---
title: "wireless hard blocked after installing Ubuntu on my Yoga 2"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by FannyG on 2014-10-05
Hello,
I have put  Ubuntu on my Yoga 2 but wireless won't work. I looked for a solution and I found this ([http://ubuntuforums.org/showthread.php?t=2215044&page=3&highlight=haohe](http://ubuntuforums.org/showthread.php?t=2215044&page=3&highlight=haohe)) : 

1) Download the kernel source

$ sudo apt-get install build-essential linux-headers-$(uname -r)
$ cd ~/workspace
$ git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
$ cp ~/workspace/ubuntu-trusty/drivers/platform/x86/ideapad-laptop.c ~/workspace/ideapad/
$ cd ~/workspace/ideapad/

(2) Change the function ideapad_rfk_set(void *data, bool blocked) in ideapad-laptop.c to

static int ideapad_rfk_set(void *data, bool blocked)
{
        struct ideapad_rfk_priv *priv = data;

/* hack to unblock wireless by sending 1 to these bits */
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_RF, 1);
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_BT, 1);
        write_ec_cmd(priv->priv->adev->handle, VPCCMD_W_WIFI, 1);
        return 0;
/* */

        return write_ec_cmd(priv->priv->adev->handle, priv->dev, !blocked);
}

(3) Create a file named Makefile:

obj-m += ideapad-laptop.o
 
all: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

(4) Build the new module

$ cd ~/workspace/ideapad/
$ make

(5) Load the module

$ cp /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko ~/ideapad-laptop.ko.backup
$ sudo cp ~/workspace/ideapad/ideapad-laptop.ko /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/
$ sudo modprobe -r ideapad-laptop
$ sudo modprobe ideapad-laptop
$ sudo rfkill unblock all
$ sudo modprobe -r ideapad-laptop
$ sudo mv ~/ideapad-laptop.ko.backup /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/ideapad-laptop.ko

(6) Blacklist the ideapad module
$ cd /etc/modprobe.d/
$ sudo echo 'blacklist ideapad-laptop' > blacklist-ideapad.conf

(7) Reboot the Yoga 2 laptop


Problem is I can't do step 3. When I enter the code in the terminal it returns : "No command shell found"
I'm not totally familiar with linux and I don't know what to do to fix  it. Please could you help me? I have no wifi I don't know how I'm going  to fix this...

thank you

---

### Post by Hadaka on 2014-10-05
Hi try the simple method first before you re-invent the wheel
[http://ubuntuforums.org/showthread.php?t=2237881](http://ubuntuforums.org/showthread.php?t=2237881)
post #2
hope this helps

---

### Post by Vladlenin5000 on 2014-10-05
> **Hadaka said:**
> Hi try the simple method first before you re-invent the wheel
[http://ubuntuforums.org/showthread.php?t=2237881](http://ubuntuforums.org/showthread.php?t=2237881)
post #2
hope this helps

^^^^
This. Exactly this. Please report back.

---

### Post by FannyG on 2014-10-10
Hi,

I tried it but it didn't work. What should I do know ?

---

### Post by Vladlenin5000 on 2014-10-10
> **FannyG said:**
> Hi,

I tried it but it didn't work. What should I do know ?

Please tell us what you did exactly and also about any error messages that might have popped out...

---

### Post by mark-lamorey on 2014-10-10
Which Yoga 2 ?
I returned my 11s after many hours of struggle - I have heard the PRO is much simpler - per post above.

---

### Post by FannyG on 2014-10-11
I have the Yoga 2 13" not Pro.
I did this :
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all

But I think it works only with the Yoga 2 pro. I didn't get any error but it didn't make any difference.

mark-lamorey, what do you mean by returning your 11? did they repay you ?

---

### Post by mark-lamorey on 2014-10-11
I bought it from a large box store locally, and returned it. A little touchy, but yes they refunded me.

I have read some posts that updating your kernel to 15 will help, but when I tried with a Yoga (9 months ago), I gave up - I do not want to be discouraging.
Not sure it will help, but check what kernel you have (likely 13 with sock 14.04 install) and upgrade it.

---

### Post by weatherman2 on 2014-10-11
> **FannyG said:**
> Hello,
(3) Create a file named Makefile:

obj-m += ideapad-laptop.o
 
all: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean: 
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


The idea is to create a text file called "Makefile" - and put those lines (starting with the obj-m line) into the text file, then save it.  You don't run those lines in a terminal.

You can use gedit to create the text file:

```

gedit ~/workspace/ideapad/Makefile

```

then paste those lines in and save it and try the make in the next step.

---

### Post by wd5gnr2 on 2014-10-11
I have documented what I did to load Kubuntu on a Yoga 2 11 and put a zip file with all the scripts:
[https://docs.google.com/document/d/1XvwBZR9B4nv12ejncjp0FU-2EgVh-FbGlmMKI_vIp0s/edit?usp=sharing](https://docs.google.com/document/d/1XvwBZR9B4nv12ejncjp0FU-2EgVh-FbGlmMKI_vIp0s/edit?usp=sharing)

That might help. The Utopic kernel which you can install as a backport or take the Beta Utopic will handle the Elan touchpad correctly. The other issue I had to solve was the wakeup lan and bluetooth. My solution is a bit of a hack but seems to work so far.

The newer ideapad driver seems to not block the ath9k driver, but it doesn't seem to be needed either from what I can see.

---

### Post by mark-lamorey on 2014-10-12
FannyG - 
file from wd5gnr2 looks good, also get you to kernel 14 - perhaps that was my mistake.
Yoga is very nice machine, try the steps in the doc - [https://docs.google.com/document/d/1...it?usp=sharing]("https://docs.google.com/document/d/1XvwBZR9B4nv12ejncjp0FU-2EgVh-FbGlmMKI_vIp0s/edit?usp=sharing")

---

