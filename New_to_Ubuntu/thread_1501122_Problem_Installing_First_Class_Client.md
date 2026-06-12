---
title: "Problem Installing First Class Client"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by Mjg40 on 2010-06-03
I'm trying to install the first class email client, but no matter what version I download or how i install it whenever I go to launch it nothing happens. Can anyone help me?

the latest version of the program can be downloaded here:

[http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.tar.bz2](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.tar.bz2)

thanks in advance :)

---

### Post by jms1989 on 2010-06-03
well what seems to be the problem? from the looks of it you just need to run the program. Based on the file structure of the tarball, it can be simply copied a directory and ran.

---

### Post by pr92 on 2010-06-03
I was able to install it on ubuntu 10.04 and it shows up under internet in the apps menu

---

### Post by Mjg40 on 2010-06-03
yes, thats what I'm doing with it; i unpacked it and installed the files to my computer and everything appears perfectly normal. The problem is that when i go to launch it from the menu nothing happens, my computer doesn't display an error message or start the process, it's like it doesn't exist and it just won't run the program

---

### Post by maybememe on 2010-06-14
When running from the terminal I get... 

```
sudo /opt/firstclass/fcc
/opt/firstclass/fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
bryan@bryan-desktop:~$ 

```

---

### Post by sandyd on 2010-06-14
> **maybememe said:**
> When running from the terminal I get... 

```
sudo /opt/firstclass/fcc
/opt/firstclass/fcc: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
bryan@bryan-desktop:~$ 

```
can you do```

sudo ls /usr/lib/libqt-mt*
```

---

### Post by Jussi01 on 2010-07-05
> **carlee said:**
> can you do```

sudo ls /usr/lib/libqt-mt*
```

Ive this same issue, here is the output of said command:


jussi@Galaxy:/opt/firstclass$ sudo ls /usr/lib/libqt-mt*
/usr/lib/libqt-mt.so.3  /usr/lib/libqt-mt.so.3.3  /usr/lib/libqt-mt.so.3.3.8


The issue for me is I'm running a 64bit system. I'm guessing I need to link that lib somewhere, but not sure.

---

### Post by pcherry on 2010-07-06
```
sudo getlibs /opt/firstclass/fcc

```
...will install libqt3-mt package and you should be all set.

---

### Post by bryncoles on 2010-07-07
I'm having this same problem - I can't install firstclass client on my 64 bit lucid! The .deb I try says I don't have permission to run it (or its broken) and the .tar.bz2... well... I have no idea what I'm supposed to do with that. I tried looking at the 'how to install from tar' Ubuntu documentation page, but it makes no sense to me. The install page [here](https://help.ubuntu.com/community/FirstClass) appears to be outdated, as the getlibs package mentioned errors out. 

So, what do I do to get firstclass working? How did anyone else manage?

---

### Post by twisted_steel on 2010-07-18
I just got this working for someone on 64-bit 10.04 by doing the following:

1. Install the 10.009 deb for FirstClass from their [client page]("http://www.firstclass.com/Divisions/FAV13-0024FC95/?Plugin=FC&OpenItemURL=S047C50E4"). 

2. Install getlibs ([deb link]("http://frozenfox.freehostia.com/cappy/getlibs-all.deb")).  I'm not sure where Cappy's site went.

3. Install the 32-bit version of libqt3-mt:
```
sudo getlibs -p libqt3-mt
```

4. Start up the program like normal.  You will need to change the server like you normally would in order to login.

---

### Post by CycleDude on 2010-08-10
I'm running Linux Mint 9 and followed twisted_steel's link (thanks) to the FirstClass client page, downloaded the 10.009 debian intel version, and followed the install instructions in their 'readme' info link.
But I had to point to the folder where the downloaded file was located:

dpkg -i /home/art/Downloads/fcc-10.009-Linux.i686.deb

So it worked, BUT, there are issues with slow response when changing folders, trying to view my webpage in a browser, etc. It automatically pops open Konqueror, even though I changed the fcapp file to use firefox, or even chromium-browser, still didn't show properly. Very frustrating. Not really usable as such.
Would like to stay in Linux and not have to go to Windows to use it normally.

---

### Post by Jetzin on 2010-09-16
Hello,

I am also having trouble installing First Class Client too. I have Ubuntu 10.04 LTS and Firefox 3.6.9.

When I tried to download the installation file V10.009 (Debian Intell) I was getting an error that the file could not be saved because the source code could not be read. I have attached a screen shot of the error message. From the community documentation instructions, I tried using the terminal to download it with this, even thought it points to an older version but that got to 97% and then came up with the same error.
wget -c [http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb](http://www3.firstclass.com/ClientDownloads/FC83ClientDownloadFiles/fcc-8.315-2-Linux-i686.deb)
I used my friends computer running vista and downloaded the file without the error but the file still doesn't work. I tried to run it with GDebi Package Installer and got an error saying that the file could not be opened. I have attached a screen shot of that error message too.

I checked the permissions, all three say "read and write" and the executable option is unticked.

From the community documentation I tried this one
sudo dpkg -i fcc-8.315-2-Linux-i686.deb and this one (that I changed to match the file name)
sudo dpkg -i fcc-10.009-Linux-i686.deb Both came up with

dpkg: error processing fcc-10.009-Linux-i686.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fcc-10.009-Linux-i686.deb

Does anyone have any suggestions? I could be doing everything wrong and not know about it. I am quite new to ubuntu and don't know what I am doing!

Thanks!!,
Grace

---

### Post by twisted_steel on 2010-09-18
Jetzin,

Are you running 32-bit or 64-bit Ubuntu 10.04?

I was unable to download the 10.009 deb file with wget because the connection was continually reset by the server once the download reached approximately 98%.  However, I was able to get the download to work in Chromium on my Ubuntu 9.10 (32-bit) computer.  I was able to run the installer without any problem.  Maybe your download is corrupted.  Try opening a terminal and running 'md5sum fcc-10.009-Linux.i686.deb' in your download directory.  This is what I get for the file on my computer that works:
```
user@hostname:~/Desktop$ md5sum fcc-10.009-Linux.i686.deb 
3d8223ca058dfb853ad196d793bb3919  fcc-10.009-Linux.i686.deb
```

---

### Post by Jetzin on 2010-09-18
Hi TwistedSteel,

I am running 32 bit Ubuntu but I have a 64 bit processor. I had trouble installing the 64 bit version and wasn't sure how long I would last on Ubuntu anyway so I just installed it from the old disk I had - I do intend to update later.

This is what I got when I ran md5sum:

username@hostname:~$ md5sum fcc-10.009-Linux.i686.deb
0f9195e1d173511d5ab3f89f3b7ee592  fcc-10.009-Linux.i686.deb

I know that's a way to check files but I have no idea what all those nubers and letters mean!

I downloaded this file on my housemates computer running vista.

Thanks very much for your help. (I am reading btw - so that I can understand more and eventually won't have to ask stupid questions).

---

### Post by sandyd on 2010-09-18
> **Jetzin said:**
> Hi TwistedSteel,

I am running 32 bit Ubuntu but I have a 64 bit processor. I had trouble installing the 64 bit version and wasn't sure how long I would last on Ubuntu anyway so I just installed it from the old disk I had - I do intend to update later.

This is what I got when I ran md5sum:

username@hostname:~$ md5sum fcc-10.009-Linux.i686.deb
0f9195e1d173511d5ab3f89f3b7ee592  fcc-10.009-Linux.i686.deb

I know that's a way to check files but I have no idea what all those nubers and letters mean!

I downloaded this file on my housemates computer running vista.

Thanks very much for your help. (I am reading btw - so that I can understand more and eventually won't have to ask stupid questions).
md5s don't match. 
Downloaded file you have right now is corrupted

---

### Post by Jetzin on 2010-09-19
Thanks sandyd.

Do you know if it is my issue or would it be FirstClass'? If it's mine, do you know what I should do to get around it? I have tried downloading 5 or 6 times and it's always the same.

---

### Post by twisted_steel on 2010-09-19
> **Jetzin said:**
> Thanks sandyd.

Do you know if it is my issue or would it be FirstClass'? If it's mine, do you know what I should do to get around it? I have tried downloading 5 or 6 times and it's always the same.

I think the problem was on their end.  I just tried downloading again today via Firefox and wget, and both actually download properly.  They also have the same md5sum (3d8223ca058dfb853ad196d793bb3919) as the one from Chromium.  I would try downloading again and it should be fine now.  This is the file that worked:

```
wget -c http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb
```

---

### Post by Jetzin on 2010-09-19
[FONT=Arial]Thanks Twistedsteel.

Unfortunately I had the same problem (see below). At least now I know that it's not something I'm doing and can follow it up with FirstClass. I just assumed it was me!


[/FONT]
[FONT=System]--2010-09-20 08:27:34--  (try:20)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 175012 (171K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,137,700  --.-K/s   in 0.02s   

2010-09-20 08:27:34 (102 KB/s) - Read error at byte 10137700/10310832 (Connection reset by peer). Giving up.
[/FONT]

---

### Post by sandyd on 2010-09-19
> **Jetzin said:**
> [FONT=Arial]Thanks Twistedsteel.

Unfortunately I had the same problem (see below). At least now I know that it's not something I'm doing and can follow it up with FirstClass. I just assumed it was me!


[/FONT]
[FONT=System]--2010-09-20 08:27:34--  (try:20)  [http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb](http://www3.firstclass.com/ClientDownloads/FC100ClientDownloadFiles/fcc-10.009-Linux.i686.deb)
Connecting to www3.firstclass.com|198.133.37.8|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 10310832 (9.8M), 175012 (171K) remaining [application/octet-stream]
Saving to: `fcc-10.009-Linux.i686.deb'

98% [++++++++++++++++++++++++++++++++++++++ ] 10,137,700  --.-K/s   in 0.02s   

2010-09-20 08:27:34 (102 KB/s) - Read error at byte 10137700/10310832 (Connection reset by peer). Giving up.
[/FONT]
Download this ->  [http://cache.dolphinaura.com/frstclass_client/fcc-10.009-Linux.i686.deb](http://cache.dolphinaura.com/frstclass_client/fcc-10.009-Linux.i686.deb)

Part of the benefits of knowing how servers work.

---

### Post by Jetzin on 2010-09-19
Thanks so much Sandyd!!!!! That worked and installed without a hitch. I am reading all that I can understand - and understanding more as I read! One day perhaps I'll know what you did. :)

Thanks TwistedSteel for working me through that too.

---

### Post by sandyd on 2010-09-19
> **Jetzin said:**
> Thanks so much Sandyd!!!!! That worked and installed without a hitch. I am reading all that I can understand - and understanding more as I read! One day perhaps I'll know what you did. :)

Thanks TwistedSteel for working me through that too.
When downloading files, some servers use a faulty "keep alive" setting. Downloading using 30 connections at once solves the problem.

---

