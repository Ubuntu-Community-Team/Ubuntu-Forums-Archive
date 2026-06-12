---
title: "annoying flash problems Ubuntu 8.04"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Allison83 on 2009-01-14
I am very new to this and know pretty little about computers and operating systems. I am trying to be able to play flash games/watch flash with Ubuntu 8.04. When I enter  locate libflash into the terminal I get:
/usr/lib/openoffice/program/libflash680li.so  
and I thought I should see abode listed there. I have installed, uninstalled and reinstalled adobe 10 several times and I am just not able to find the problem. This is what is happening...

on youtube, initially it seems like it just never loads and then I hit play TWICE to get it to load and then it will play for a few seconds and then stop while I usually still hear the audio.If I try to jump forward or back in the clip, it freezes my firefox sesion.

clips on cnn.com just never load and flash games will usually load initially (though not every time) and then just fail.
I have been trying to find answers online for several hours before posting here but everything I try fails.

Any ideas?

Thanks,

Allison

---

### Post by donkyhotay on 2009-01-14
How are you installing flash? Are you installing from the download at adobe.com or from synaptic? If you have been installing from adobe.com I would recommend installing from synaptic as it's much easier and (for me at least) less likely to have problem. If you don't know how to do that you just type
```
sudo apt-get install flashplugin-nonfree
```
into the terminal.

---

### Post by Allison83 on 2009-01-14
Hi,

I did this and this is what I got:

james@james-acer:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@james-acer:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so


and nothing has changed when I try the flash stuff

Allison

---

### Post by Therion on 2009-01-14
Try this...

Open Synaptic Package Manager.
Search on "Gnash".  
Remove any "Gnash" related packages.
Close Synaptic.
Open a Terminal.```
sudo apt-get install ubuntu-restricted-extras
```Enter your password, answer yes to any prompts you might get and then just let *apt-get* do it's major groove thaaaang.
Go back to YouTube and see if you're up and running.

---

### Post by Allison83 on 2009-01-14
Hey,

 Ok, I tried that. I was not able to delete these "gnash" things because (it appears) they are not actually installed. So, I did type the command into the terminal. Youtube seems to run a little better but not much. CNN and flash games still don't work.

Thanks,

Allison

---

### Post by lavinog on 2009-01-14
are you using 32bit or 64bit
also locate is not going to be accurate until you run 
```
sudo updatedb
```

---

### Post by lavinog on 2009-01-14
what version is listed when you go here:
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

---

### Post by Allison83 on 2009-01-14
Hey,

 OK...

I went to the site about and it said I have "9,0,100,0" installed.
And when I entered the above command I got a command not found error.
32 bit? 64 bit? I don't know. It's an Acer 290 notebook, I looked to find the answer, I found one sight that suggested it's 64 but I don't know, this site seemed questionable either way.

Thanks,

Allison

---

### Post by avtolle on 2009-01-14
IIRC, the latest version of Flash with 8.04 is 9. It might be that a newer version is in the backports repository; I don't know (running on PPC, so no Flash available).

---

### Post by gmjs on 2009-01-14
Hi Allison,

I've found that Flash Player 10 seems to run much better than the previous versions.

You can download a .DEB file from the Adobe website ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)).  Just select the **.deb for Ubuntu 8.04+** option from the drop down list.  When downloaded, double-click the file and select 'Install Package' to install.  Give Firefox a restart.

If this doesn't work, you can download the **.tar.gz** file and install it manually (it's not too difficult).  I'd try the **.deb** package first though.

Hope this helps,

Graham

---

### Post by avtolle on 2009-01-14
Allison, what gmjs suggests is the best way to get Flash Player 10 on 8.04 from looking around. However, as you have version 9 installed, I suggest you remove it before installing 10. Also, from reading a couple of things I found by Google, your 8.04 needs to be fully updated before installing 10. Best of luck

---

### Post by lavinog on 2009-01-14
> **Allison83 said:**
> Hey,

 OK...

I went to the site about and it said I have "9,0,100,0" installed.
And when I entered the above command I got a command not found error.
32 bit? 64 bit? I don't know. It's an Acer 290 notebook, I looked to find the answer, I found one sight that suggested it's 64 but I don't know, this site seemed questionable either way.

Thanks,

Allison

Which version of ubuntu is installed?
```
uname -a
```
ubuntu comes in 32bit and 64 bit installs, most computers these days can handle 64bit ubuntu, but many people will choose to install 32 bit.
The reason why I ask is that the 64bit version of flash has many issues...adobe released a native 64 bit flash as beta recently, and switching to that fixed many problems including youtube issues.

---

