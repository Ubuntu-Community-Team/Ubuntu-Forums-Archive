---
title: "Hardware Drivers Downloading and checking"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by zawmai on 2010-08-31
Hi, I was a Windows user.I just started using Ubuntu yesterday and I'm mostly concerned about my drivers, especially my audio and graphics card.I have a Lenovo Ideapad Y560 laptop. When I was using windows, Lenovo offers a list of drivers download for my specific model. For Ubuntu, where can I find the drivers for the hardware. I'm a total noob. >.<             Specs: Intel® Core™ i7-720QM Processor 1.6ghz ATI Mobility Radeon HD 5730 1GB 8GB RAM DDR3

---

### Post by akoskm on 2010-08-31
> **zawmai said:**
> Hi, I was a Windows user.I just started using Ubuntu yesterday and I'm mostly concerned about my drivers, especially my audio and graphics card.I have a Lenovo Ideapad Y560 laptop. When I was using windows, Lenovo offers a list of drivers download for my specific model. For Ubuntu, where can I find the drivers for the hardware. I'm a total noob. >.<             Specs: Intel® Core&#8482; i7-720QM Processor 1.6ghz ATI Mobility Radeon HD 5730 1GB 8GB RAM DDR3

Hi!
You can find the list of installable drivers in System > Administration > Hardware Drivers.
Most of your hardware is - probably - already working, if something isn't and there is no support for it in Hardware Drivers, let us know, or take a look to the [Ubuntu Wiki]("https://wiki.ubuntu.com/").

---

### Post by zawmai on 2010-08-31
I went to System>Administration>Hardware Drivers.
It says: "ATI/AMD proprietary FGLRX GRAPHICS Driver"
I tried to activate it and it gave me this message, "SystemError: installArchives() failed."
what does it mean?

---

### Post by akoskm on 2010-08-31
> **zawmai said:**
> I went to System>Administration>Hardware Drivers.
It says: "ATI/AMD proprietary FGLRX GRAPHICS Driver"
I tried to activate it and it gave me this message, "SystemError: installArchives() failed."
what does it mean?

Make sure that there is no Synaptic / Updater or another package manager program is running, and try again.

---

### Post by zawmai on 2010-08-31
> Make sure that there is no Synaptic / Updater or another package manager program is running, and try again.The hardware installation still doesn't work. I tried re-installing it from the "broken" filter of the package manager.
Now, it shows me this error:
**"E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_amd64.deb: subprocess new pre-installation script returned error exit status 1"**

---

### Post by akoskm on 2010-09-01
> **zawmai said:**
> The hardware installation still doesn't work. I tried re-installing it from the "broken" filter of the package manager.
Now, it shows me this error:
**"E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu4_amd64.deb: subprocess new pre-installation script returned error exit status 1"**

Opent the Terminal (Applications > Accessories) and type the following:
```

sudo aptitude clean

```, it will ask for your root password. After it finished, open again the Hardware Drivers manager - make sure that there is no other package manager running - select the driver and click Activate.
Hope this helps.

---

### Post by zawmai on 2010-09-01
> **akoskm said:**
> Opent the Terminal (Applications > Accessories) and type the following:
```

sudo aptitude clean

```, it will ask for your root password. After it finished, open again the Hardware Drivers manager - make sure that there is no other package manager running - select the driver and click Activate.
Hope this helps.

OK, I typed the code, "sudo aptitude clean" (btw wht does it do?) and the root password. When I checked my "hardware drivers," it says: **no proprietary drivers are in use on this system**. I think it's because I upgraded to ubuntu 10.10.

---

### Post by akoskm on 2010-09-01
> **zawmai said:**
> OK, I typed the code, "sudo aptitude clean" (btw wht does it do?) and the root password. When I checked my "hardware drivers," it says: **no proprietary drivers are in use on this system**. I think it's because I upgraded to ubuntu 10.10.

sudo stands for the superuser mode, aptitude is the package manager, just can open the manual page for most console applications with ```
man <application name>
``` command, replacing the <application command> with the actual program.
aptitude clean from *man aptitude, clean: Removes all previously downloaded .deb files from the package cache directory (usually /var/cache/apt/archives).*
With this command we deleted all the previously downloaded .deb files from your system - the ati driver too, which may caused the error message.
It says that there are no proprietary drivers in use, that's okay.
Can you activate now the ATI driver?

---

### Post by zawmai on 2010-09-01
> **akoskm said:**
> sudo stands for the superuser mode, aptitude is the package manager, just can open the manual page for most console applications with ```
man <application name>
``` command, replacing the <application command> with the actual program.
aptitude clean from *man aptitude, clean: Removes all previously downloaded .deb files from the package cache directory (usually /var/cache/apt/archives).*
With this command we deleted all the previously downloaded .deb files from your system - the ati driver too, which may caused the error message.
It says that there are no proprietary drivers in use, that's okay.
Can you activate now the ATI driver?

THnx for the code. What are .deb files?
It's now called "Additional Drivers," instead of "Hardware Drivers."
How can I activate the ATI driver? It doesn't show me any drivers to activate.

---

### Post by Calash on 2010-09-01
> **zawmai said:**
> OK, I typed the code, "sudo aptitude clean" (btw wht does it do?) and the root password. When I checked my "hardware drivers," it says: **no proprietary drivers are in use on this system**. I think it's because I upgraded to ubuntu 10.10.

You do know 10.10 is still in development and far from stable at this point?

If you are testing then you probably should look for support in the development forum.

---

### Post by zawmai on 2010-09-01
> **Calash said:**
> You do know 10.10 is still in development and far from stable at this point?

If you are testing then you probably should look for support in the development forum.

I did not know that....
So, How do I downgrade to 10.04?

---

### Post by akoskm on 2010-09-01
> **zawmai said:**
> THnx for the code. What are .deb files?
It's now called "Additional Drivers," instead of "Hardware Drivers."
How can I activate the ATI driver? It doesn't show me any drivers to activate.

10.10 is still in development phase, if your are going for stability switch back to 10.04 as Calash suggested and try there what I posted above.
My advice doesn't apply to 10.10, since I have no idea what's happening in the development version.

---

### Post by uRock on 2010-09-01
Reinstall. 

How did you manage to upgrade to 10.10?

---

### Post by zawmai on 2010-09-01
> **uRock said:**
> Reinstall. 

How did you manage to upgrade to 10.10?

I changed the update-manger settings on the "updates" tab. From updating **only long term support release **to **normal releases only, **whichi THOUGHT WAS STABLE.

Re-install with a cd?

---

### Post by uRock on 2010-09-01
Yup, use the CD.

---

### Post by akoskm on 2010-09-01
> **zawmai said:**
> I changed the update-manger settings on the "updates" tab. From updating **only long term support release **to **normal releases only, **whichi THOUGHT WAS STABLE.

Re-install with a cd?

Don't forget to [check the media]("https://help.ubuntu.com/community/HowToMD5SUM#Check the CD") before installation!

---

### Post by zawmai on 2010-09-01
Ok, I reinstalled Ubuntu 10.04 LTS and the activated the ATI proprietary driver. Thnx.

---

### Post by akoskm on 2010-09-02
> **zawmai said:**
> Ok, I reinstalled Ubuntu 10.04 LTS and the activated the ATI proprietary driver. Thnx.

Good to hear, have fun with Ubuntu! :)

---

### Post by Calash on 2010-09-03
> **zawmai said:**
> I changed the update-manger settings on the "updates" tab. From updating **only long term support release **to **normal releases only, **whichi THOUGHT WAS STABLE.

Re-install with a cd?

That is odd.  Did you open update-manager from the terminal with any commands, such as -d?

That is the setting all my systems are on and I have never see it offer the beta unless you tell it to, with the -d command.

It may be a bug.

---

