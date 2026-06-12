---
title: "how to install microsoft fonts in ubuntu 11.04"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by sukantamech on 2011-08-04
Please help me in installing how to install microsoft fonts in ubuntu 11.04.. I am new user in ubuntu 11.04.

---

### Post by spook1980 on 2011-08-04
i would recommend installing the restricted extras package as that will do your fonts install flash add mp3 support etc, etc,

open up a terminal...

sudo apt-get install ubuntu-restricted-extras

---

### Post by Dead root on 2011-08-04
Download this file to your home : [http://www.box.net/shared/tvokeevkuk](http://www.box.net/shared/tvokeevkuk)

[COLOR=black]```
unzip Windows-Original-Fonts.zip
```Then

```
[COLOR=black]mv Windows\ Fonts/ windows[/COLOR]
```[COLOR=black]

then move it to font

```
[COLOR=black]sudo mv windows /usr/share/fonts/[/COLOR]
```[COLOR=black]

Close and restart your firefox and you'll be be able to see the same font as Windows while browsing the Internet.
[/COLOR][/COLOR][/COLOR]

---

### Post by grahammechanical on 2011-08-04
Do a search in the Ubuntu Software Centre for mscorefonts and install the package ttf-mscorefonts-installer. This will install legal MS fonts.

Regards.

---

### Post by walt.smith1960 on 2011-08-04
> **spook1980 said:**
> i would recommend installing the restricted extras package as that will do your fonts install flash add mp3 support etc, etc,

open up a terminal...

sudo apt-get install ubuntu-restricted-extras

Excellent way. Fonts and much more. If you want to add fonts from other sources, one easy way to to create a hidden fonts folder in home (/home/.fonts).  Copy .ttf files there and they will be available. The limitation with this is those fonts will be available _only_ to that user afaik.

---

### Post by melrokz on 2011-08-04
If you have Windows, you may copy your ttf fonts in C:\Windows\Fonts to /usr/share/fonts/truetype/ folder.

***You need root privileges for this.

---

### Post by MARP1961 on 2011-08-04
You will need to set up ms fonts if you use LibreOffice or OpenOffice too.

Go to Synaptic Package Manager, search for and install msfonts.

---

### Post by sukantamech on 2011-08-13
Thank you all for your constant support.



I am using 64bit ubuntu 11.04 destop. I have just recently installed  ifort, Intel composer XE 2011.5.220. just after installation, i have given the  following command... but facing problem in that...

Please suggest me what to do.....!!! (sukantamech07@gmail.com)



[COLOR=SeaGreen]sukanta@Energy:~$ /opt/intel/composerxe-2011.5.220/bin/compilervars.sh intel64
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator
[: 121: intel64: unexpected operator

ERROR: Unknown option 'intel64'
 
 Syntax:
 /opt/intel/composerxe-2011.5.220/bin/compilervars.sh <arch> [MKL_interface] [mod]

<arch> must be one of the following
ia32 : Set up for IA-32 target
intel64 : Set up for Intel(R) 64 target
mic : Set up for Intel(R) MIC target

mod (optional) - set path to MKL F95 modules

MKL_interface (optional) - MKL programming interface for intel64
Not applicable without mod
lp64 : 4 bytes integer (default)
ilp64 : 8 bytes integer

sukanta@Energy:~$[/COLOR]

---

### Post by sukantamech on 2011-08-13
[COLOR=DarkSlateBlue]My pc configuration is 64bit i3 processor, 500gb hdd, 4gb ram[/COLOR]

---

### Post by asharpham on 2011-09-21
I'm having the same problem trying to install ms fonts. I have 11.04 on a 32-bit machine. First I've tried 'sudo apt-get install ubuntu-restricted-extras' but I get a message about EULA which has <ok> at the bottom and can't get out of it. How do you continue from here?

I've also tried copying and pasting into /usr/share/fonts but it keeps telling me I don't have permissions. How do I get permissions?

In Terminal I've used 'sudo su' to enter as root in order to copy the fonts into /usr/share/fonts but I don't know how to express that I want all files in the directory I'm copying from.

If someone can tell me how to gain 'permission' to get into the fonts sub-directory, I'd be happy.

Thanks,
Alan.

---

### Post by oldos2er on 2011-09-21
> **asharpham said:**
> I'm having the same problem trying to install ms fonts. I have 11.04 on a 32-bit machine. First I've tried 'sudo apt-get install ubuntu-restricted-extras' but I get a message about EULA which has <ok> at the bottom and can't get out of it. How do you continue from here?

Use Tab to select 'Ok,' then press Enter.

> I've also tried copying and pasting into /usr/share/fonts but it keeps telling me I don't have permissions. How do I get permissions?

In Terminal I've used 'sudo su' to enter as root in order to copy the fonts into /usr/share/fonts but I don't know how to express that I want all files in the directory I'm copying from.

Run ```
gksudo nautilus
``` to give yourself permission to copy/paste to a system folder. You may need to open another nautilus window with 'gksudo,' one for source and one for destination, depending on how your system is set up.

---

### Post by asharpham on 2011-09-22
Thanks so much oldos2er. Both these methods worked fine. To copy into the fonts subdirectory, I used your suggestion, gksudo nautilus, then dragged the folder holding the fonts into it. I wasn't sure if LibreOffice would recognise the folder so I copied all its contents into the msttcorefonts folder, replacing existing ones as I went. This way i got all the fonts I had before my computer crash, not just the ones from ms fonts.

Regards,
Alan.

---

### Post by P05TMAN on 2011-09-22
> **melrokz said:**
> If you have Windows, you may copy your ttf fonts in C:\Windows\Fonts to /usr/share/fonts/truetype/ folder.

***You need root privileges for this.

If you do it this way, these fonts will be available in LibreOffice? Is it legal to do this?

---

### Post by holycow131415 on 2012-05-15
Easiest way would be to install the ttf-msfonts package from synaptic. If you install it from the software center, the EULA agreement that you need to accept doesnt pop up (from my experience anyway) which stalls the installation. The agreement may pop up in back of synaptic, so just move synaptic to the side so you can accept the agreement.

---

