---
title: "Ubuntu 10.04 Installation Problems (64 bit)"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by Moobones on 2010-05-24
Hello everyone,

I am new to the forums as well as new to ubuntu, and i was wondering if anyone out there could help me out. I have searched endlessly on the internet trying to find a solution for this and pardon me if there is one on these forums.

My problem is that I am trying to install Ubuntu 10.04 64 BIT on my Desktop PC. It usually runs Vista 64bit. I have tried Installing both the 32 bit and 64 bit with the same problem. The problem is that after I boot up from the cd with iso image burned on it, i get to "install ubuntu". The screen then displays Ubuntu with its logo , as well as the dots on the bottom under it, they flash from red to white and so on, until they all go red, and the screen goes black, and the monitor goes to sleep.

My specs are:

Processor: Intel Core 2 Quad CPU Q8200 2.33GHz 2.33GHz
Graphics Card: ATI Radeaon HD 5870 approx. memory 2797 MB
PC: HP Pavillion m9550fr
Ram: 4094 MB 
Screen: HP w2207
Keyboard: G15 Logitech

Please notify me if anymore information is required.
Also I haven tried this but i will, if vista is installed in french do i have to install ubuntu in french as well? I wouldnt think it would matter but i think trying it out would be worth it.

Anyways thanks for the replies in advance and I hope some of you can help me out.

Moobones

---

### Post by roger_1960 on 2010-05-24
Hi

Not sure what the problem is (are you waiting long enough for the install?) but I am sure that the language is not the issue.

Are you trying a WUBI install?

---

### Post by bodhi.zazen on 2010-05-24
My guess is the problem is with your ATI card :

[http://www.overclock.net/linux-unix/732545-how-install-ubuntu-10-04-ati.html](http://www.overclock.net/linux-unix/732545-how-install-ubuntu-10-04-ati.html)

---

### Post by Moobones on 2010-05-24
Thanks for the link bodhi.zazen, however booting from the CD doesnt seem to have a safe mode, so i was wondering, can i try installing a version prior to 10.04 and update from there by going into safe mode?

roger_1960, I dont know what a WUBI install is (sorry just started doing this today haha). What i did was mount the iso onto a CD, which just happens to have a WUBI.exe file on it, but i didnt install from windows, i rebooted and had it boot up from the CD.

Thanks again

---

### Post by bodhi.zazen on 2010-05-24
> **Moobones said:**
> Thanks for the link bodhi.zazen, however booting from the CD doesnt seem to have a safe mode, so i was wondering, can i try installing a version prior to 10.04 and update from there by going into safe mode?

roger_1960, I dont know what a WUBI install is (sorry just started doing this today haha). What i did was mount the iso onto a CD, which just happens to have a WUBI.exe file on it, but i didnt install from windows, i rebooted and had it boot up from the CD.

Thanks again

I would use the "alternate" CD then. Either way (upgrade or fresh install) you will almost certainly need to boot to "recovery mode" and install the ATI drivers from the command line, without a graphical interface.

Alternates would be to stay with 9.10 or you could try Fedora 13 .

---

### Post by Moobones on 2010-05-24
Thanks again for your reply, however could you please guide me as to how to boot to recovery mode as well as installing the ATI drivers?

Sorry but as i said, I'm a newcomer to the ubuntu community and theres alot for me to learn still.

Thanks for your patience.
Edit: NVM i thought boot into recovery mode for install and not for drivers install, my bad

---

### Post by bodhi.zazen on 2010-05-24
> **Moobones said:**
> Thanks again for your reply, however could you please guide me as to how to boot to recovery mode as well as installing the ATI drivers?

Sorry but as i said, I'm a newcomer to the ubuntu community and theres alot for me to learn still.

Thanks for your patience.

If you are new to Linux and Ubuntu, I highly suggest you stay with a release that works with your hardware.

If you are willing to learn ...

After you install, as you boot, hold the shift key, and one of the boot options will be to boot to recovery mode.

To install the ATI driver see:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by rob &lt; on 2010-05-24
[http://ubuntuforums.org/showthread.php?t=1491694](http://ubuntuforums.org/showthread.php?t=1491694) 

check out this thread I made the other day. someone helped me out and it might work for you too.

---

### Post by Moobones on 2010-05-26
> **bodhi.zazen said:**
> If you are new to Linux and Ubuntu, I highly suggest you stay with a release that works with your hardware.

If you are willing to learn ...

After you install, as you boot, hold the shift key, and one of the boot options will be to boot to recovery mode.

To install the ATI driver see:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Once again thank you very much, that fix actually worked when using the commands in dos format, however i did go through about a million installs with 9.10 and not so succesful 10.04.
What really helped though to actually get it installed was the alternate cd version.

once again, thanks:)

---

