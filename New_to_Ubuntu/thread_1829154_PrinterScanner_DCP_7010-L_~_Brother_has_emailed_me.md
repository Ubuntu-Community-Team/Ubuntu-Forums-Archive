---
title: "Printer/Scanner DCP 7010-L ~ Brother has emailed me re their 64-bit Scanner Drivers"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by Andavane on 2011-08-20
Brief details of current problem re scanner drivers.

In 32 & 64 bit machines the Printer is now picked up automatically in Ubuntu 11.04 on both architectures.

In 11.04 the scanner drivers are working fine on my old 32-bit laptop,
however none of our efforts can persuade them to work on 64-bit machines.

The tests have included:
> "andavane@andavane-think:~$ brscan-skey -l
brscan-skey: command not found
andavane@andavane-think:~$ dpkg -i --force-all brscan2-0.2.5-1.amd64.deb
dpkg: error: operation requires read/write access to dpkg status area
andavane@andavane-think:~$ "
I get (after restarting the OS):

"andavane@andavane-think:~$ dpkg -i --force-all brscan2-0.2.5-1.amd64.deb
dpkg: error: operation requires read/write access to dpkg status area
andavane@andavane-think:~$"

Shortening the thread of correspondence, Brother has written to me:

> 
Dear John
Thank you for your email.
I am going to see if I can install this on a 64 bit system and test.
If you come across anything in the meantime please let me know.
Kind regards,
Allan Stewart

Technical Support Advisor


If anyone *has* cracked this, please let us know.
Personally, I feel the driver has a bug as the 32-bit drivers work perfectly.

---

### Post by Andavane on 2011-08-27
Brother  has replied to my query thus:
> Dear John
I have set this up and tested it ok.

 After installing 11.04 I installed Sane and the related packages that it prompted it needed installing via the package manager.

 In terminal I then changed the directory to where the package was located and installed with the command:
[B]
sudo dpkg  -i  --force-all  brscan2-0.2.5-1.amd64.deb[/B]

I then added the following text to the end of the device list (Before the line "# The following rule will disable ..."): in the following file:

/lib/udev/rules.d/40-libsane.rules

[B]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
[/B]
After that I restart the pc and it tested ok.

Unfortunately when I tried it I got this result:
> andavane@andavane-HP-dm1:~$ sudo dpkg --force-all brscan2-0.2.5-1.amd64.deb
[sudo] password for andavane: 
dpkg: error: need an action option

Type dpkg --help for help about installing and un-installing packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
andavane@andavane-HP-dm1:~$ 


I'm a bit out of my depth again.
am studying the instruction but would appreciate any feedback.
I think it means I made a botch of installing the driver... ?

---

### Post by plucky on 2011-08-27
> andavane@andavane-HP-dm1:~$ sudo dpkg --force-all brscan2-0.2.5-1.amd64.deb
[sudo] password for andavane:
dpkg: error: need an action option


Your command is incorrect.

It should be ```
andavane@andavane-HP-dm1:~$ sudo dpkg [color=red]-i[/color] --force-all brscan2-0.2.5-1.amd64.deb
```

You forgot the **-i** to tell dpkg to install the package.

Good Luck

---

### Post by Wim Sturkenboom on 2011-08-27
As plucky said

from your quote of brother's post
```

sudo dpkg [COLOR="Red"]**-i**[/COLOR] --force-all brscan2-0.2.5-1.amd64.deb

```
from your quote of your own attempt
```

sudo dpkg --force-all brscan2-0.2.5-1.amd64.deb

```
Reading is an art ;)

---

### Post by Andavane on 2011-08-27
Yes Guys thanks very much - I used to be a proof reader :oops:
Progress definitely made.
The driver has gone on all right, but no result so i installed the scan-key tool according to: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn3.html")
Unfortunately I have now received the following from the terminal:

> andavane@andavane-HP-dm1:~$ sudo dpkg -i --force-all brscan-skey-0.2.1-3.amd64.deb
[sudo] password for andavane: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (amd64) does not match system (i386)
Selecting previously deselected package brscan-skey:amd64.
(Reading database ... 212571 files and directories currently installed.)
Unpacking brscan-skey:amd64 (from brscan-skey-0.2.1-3.amd64.deb) ...
dpkg: dependency problems prevent configuration of brscan-skey:amd64:
 brscan-skey:amd64 depends on libc6 (>= 2.3.4-1).
dpkg: error processing brscan-skey:amd64 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 brscan-skey:amd64
andavane@andavane-HP-dm1:~$ 

I don't like the look of the package architecture being wrong.
It's definitely a 64-bit machine.

---

### Post by Wim Sturkenboom on 2011-08-27
Just to verify (it should be as you managed to install the 64bit brscan), can you post the results of *_uname -a_* ?
```

fortyfourgalena@desktop-01:~$ **uname -a**
Linux desktop-01 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 x86_64 GNU/Linux
fortyfourgalena@desktop-01:~$ 

```

And after that I'm probably out of here because I don't know much about packages and their managers.

---

### Post by Andavane on 2011-08-27
Results:

> andavane@andavane-HP-dm1:~$ uname -a
Linux andavane-HP-dm1 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux
andavane@andavane-HP-dm1:~$ uname -m
i686
andavane@andavane-HP-dm1:~$ 


---

### Post by Wim Sturkenboom on 2011-08-27
Looks like the 32 bit version of the operating system ;)

You might be running it on a 64 bit architecture, but that is not the same as using a 64 bit OS,

---

### Post by Andavane on 2011-08-28
Oh golly what have I done now.
I wonder if there's a way to test the usb stick I used.
It says it's 64 bit.
I'll boot from it and see if I can tell that way.
Am on a 32 bit machine atm and will test when I can get that 64-bit model.

---

