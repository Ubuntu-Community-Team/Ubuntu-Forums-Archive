---
title: "Super User???"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by RustyRus on 2009-06-02
Is the super user account not really used in Ubuntu. Have used this in other Linux iterations but seems SUDO rules now? 
 
My real issue is with Flash. When I go to install flash I get an error message. I followed a manual process trying to extract files into a plugins directory but it says I dont have permissiion to do this. How can I get my user account when in the GUI mode to act as sudo or root or su or whoever. 
 
 
Additionaly this seems like it can be a very great OS. In the infant stages of making my life Windows or Mac free. Again thank you

---

### Post by kukibird1 on 2009-06-02
> **RustyRus said:**
> Is the super user account not really used in Ubuntu. Have used this in other Linux iterations but seems SUDO rules now? 
 
My real issue is with Flash. When I go to install flash I get an error message. I followed a manual process trying to extract files into a plugins directory but it says I dont have permissiion to do this. How can I get my user account when in the GUI mode to act as sudo or root or su or whoever. 
 
 
Additionaly this seems like it can be a very great OS. In the infant stages of making my life Windows or Mac free. Again thank you

The easier way is to install the ubuntu-restricted-extras package which includes flash and various codecs . You can install this from add remove programs or synaptic package manager. Using the terminal put sudo before those manual instructions 
to install the plugin to /usr/lib/mozilla/plugins is another option.

Here is some info on on sudo and gksudo 

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")

---

### Post by starcannon on 2009-06-02
sudo is used for administration and software installations. The root account is disabled by default, and this is done for in order to offer a more secure system.

There is a lot of non-free(libre) stuff you will want to add; and, there is a great repository for those items. You can add those repositories by following [these directions]("https://help.ubuntu.com/community/Medibuntu")
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then you can get a great deal of the restricted media formats by either searching for "ubuntu-restricted-extras" in the Synaptic Package Manager, or by entering this in a terminal:
```

sudo apt-get install ubuntu-restricted-extras

```
If you require Real Media Player, it can be obtained [here]("http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb")
[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

Or by visiting the [this page]("http://www.real.com/linux?src=realhome_linux_bb_0_1_1_0_0_3_0&pcode=rn&opage=realplayer_com") and choosing the Deb Package link underneath the big yellow pill Download Realplayer button.

Whichever way you decide to download that .deb, just double click the RealPlayer11GOLD.deb file and then click on install.

If the default .pdf viewer isn't cutting it for you, you can get the Adobe Reader from [here]("http://get.adobe.com/reader/otherversions/"). Provided your using 32bit Ubuntu, you can just grab the Linux - x86(.deb) file and double click install it after download is complete.

GL and have fun.

---

### Post by RustyRus on 2009-06-02
Thanks guys i got flash installed and got the updates via the shell. Now i am trying to install my video driver which is a Nvida Qaudro and i am getting this error. Any ideas thanks again


rusty@rusty-laptop:~$ sudo sh NVIDIA-Linux-x86-100.14.23-pkg1.run

[sudo] password for rusty: 

sh: Can't open NVIDIA-Linux-x86-100.14.23-pkg1.run
rusty@rusty-laptop:~$

---

### Post by RustyRus on 2009-06-02
Nevermind guys found that it was a restricted driver and had to got to system> admin> hardware drivers. Not really sure I understand why it was just sitting there wating to download but......

---

### Post by Nixie Pixel on 2009-06-02
> **RustyRus said:**
> Nevermind guys found that it was a restricted driver and had to got to system> admin> hardware drivers. Not really sure I understand why it was just sitting there wating to download but......
If drivers are proprietary (that is, not open source), they will not be installed by default. You have to activate them manually, indicating that you wish to be bound by the proprietary licensing agreement.

Hence why you don't get the restricted stuff found in ubuntu-restricted-extras by default, such as Java and Flash.

---

### Post by Bradtek on 2009-06-03
> **RustyRus said:**
>  How can I get my user account when in the GUI mode to act as sudo or root or su or whoever. 


To answer your original question

Either in a terminal or Press Alt F2 and type
```
gksudo nautilus
```
This will give you Nautilus in super user mode allowing you to copy/paste
move extract etc etc to directories you need permission.

---

