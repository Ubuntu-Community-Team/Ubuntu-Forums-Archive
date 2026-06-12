---
title: "Brother Printer MFC-495CW"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by zippytex on 2011-05-29
I receive this error message after installing the scanner for my multi-function device.

Failed to open device 'brother 3:bus4,' devl':  
Invalid Argument

I am using a Toshiba M35X-S311 with 1.5GB memory and Ubuntu 11.04
The laptop is 1.8 ghz.

I used the debi installer for the package.

But when I used the following:

dpkg -i -force-all (brscan.3-0.2.11-4,i386.deb)

I got an error message for the -i

I am a newbie, but tried to follow one step at a time.

If you can help, I sure would appreciate it.:p

---

### Post by wolfen69 on 2011-05-29
> **zippytex said:**
> I receive this error message after installing the scanner for my multi-function device.

Failed to open device 'brother 3:bus4,' devl':  
Invalid Argument

I am using a Toshiba M35X-S311 with 1.5GB memory and Ubuntu 11.04
The laptop is 1.8 ghz.

I used the debi installer for the package.

But when I used the following:

**dpkg -i -force-all **(brscan.3-0.2.11-4,i386.deb)

I got an error message for the -i

I am a newbie, but tried to follow one step at a time.

If you can help, I sure would appreciate it.:p

You need to do ```
*sudo* dpkg -i -force-all 
```

---

### Post by zippytex on 2011-06-03
You need to do sudo dpkg -i -force-all 


I did the above and below are the results I got.

write@write-Satellite-M35X:~$ sudo dpkg -i -force-all
[sudo] password for write: 
dpkg: conflicting actions -f (--field) and -i (--install)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
write@write-Satellite-M35X:~$ ^C
write@write-Satellite-M35X:~$ ^C
write@write-Satellite-M35X:~$

---

### Post by wolfen69 on 2011-06-04
The deb file should be in your home folder to make things easier.

---

### Post by santy_kushwaha on 2011-06-04
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW")

download the cpuswrapper driver for the mfc-495 printer 

just double click it and instal it and then go to system > admin > printing> and there you will see the MFC-495cw printer go to properties and type the printer ip (check the ip from the printer setting) and the click on the device uri and retype the printer ip and choose the brother printer and it will be ready to go 

thats how my printer worked out this process was done on ubuntu 10.10 and i haven't tried it yet on the 11.04 so i'm not sure if it will work or not! just give it a try

---

### Post by plucky on 2011-06-04
> I did the above and below are the results I got.

write@write-Satellite-M35X:~$ sudo dpkg -i -force-all
[sudo] password for write:
dpkg: conflicting actions -f (--field) and -i (--install)

Type dpkg --help for help about installing and deinstalling packages[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

You need to specify what file to install 

Go to wherever the .deb file is located and then run ```
sudo dpkg -i -force-all brscan.3-0.2.11-4,i386.deb
```

Good Luck

---

