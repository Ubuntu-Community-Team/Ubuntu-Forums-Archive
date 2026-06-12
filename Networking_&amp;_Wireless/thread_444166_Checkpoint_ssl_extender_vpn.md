---
title: "Checkpoint ssl extender vpn"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by bagpussnz on 2007-05-15
Please help.
I'm using the checkpoint ssl network extender for vpn connectivity to the office.

(all the following are using firefox2).

I've verified it works on windows (java6) and also on Suse 10.0 (java1.4.2).

I tried on my Ubuntu 7.04 using the default java (1.4.2 - gcj) - it failed to run (it wouldn't even accept the certificate).
I installed Java6 and tried again  - it prompted for certificate, opened a window prompting for root password and then I got a 
"Failed to initialize" error.

In addition, when I run "snx", I get a segmentation fault. 
Has anyone got this working on Ubuntu?

Regards,
Ian.

---

### Post by chairman on 2007-07-09
I got the same problem :(

---

### Post by ricardoarguello on 2007-09-21
This is how I made it work:

1) To install the SSL Network Extender client I had to do this:

```

$ sudo -s -H
# bash ./snx_install.sh
Installation successfull
# snx
snx: symbol lookup error: snx: undefined symbol: cerr

```

2) To make it work, you need to install libstdc++2.10-glibc2.2:

```
$ sudo apt-get install libstdc++2.10-glibc2.2
```

3) You need to override the libc with this:

```
# LD_PRELOAD=/usr/lib/libstdc++-libc6.2-2.so.3 snx
```


4) That's all!

```
# LD_PRELOAD=/usr/lib/libstdc++-libc6.2-2.so.3 snx -s xxx.xxx.xxx.xxx -c mycert.p12
```

---

### Post by digdug9117 on 2007-10-29
I'm using gutsy and can't find libg++2.8.1.3-glibc2.2 in the repository's. Can you tell me what repository it's in...

---

### Post by ricardoarguello on 2007-10-30
It looks like it is in the universe repo:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libg%2B%2B&searchon=names&subword=1&version=gutsy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libg%2B%2B&searchon=names&subword=1&version=gutsy&release=all")

---

### Post by deloptes on 2008-01-22
Our company just switched to a gateway version of CheckPoint with SNX for linux.

I found a way to make it run. (see below) I am just concerened about the security, because I have to run the stuff as root, because snx needs root access to create and modify ethernet devices etc.

Do you have a suggestion how the thing could be tight up?

The problem in details I have to run firefox as root, then a java applet is using snx to build the connection and from inside this java applet I can lounch programs on my linux system that are executed in the VPN environment AS ROOT .... exactly what I don't like

Thank you in advance

[LIST]
Prepare:
[/LIST]

Find compatible libstdc++-2-libc6. On debian I had a problem with this, because this package is not in the official distro (I needed this before for testing ViaVoice, so thats why it is in this place). You should be able to find it i.e. as RPM package or tar.gz or similar nad install or unpack it somewher. Also the minor version numbers could be different ... don't worry. Important is that it works on your system.

       > 
        locate libstdc++-2-libc6.1
        /opt/custom/ViaVoice/lib/usr-lib/libstdc++-2-libc6.1-1-2.9.0.so
       

[LIST]
Edit:
[/LIST]

Move the snx binary to snx-bin and create a script as shown below
Replace the library path to the library that is installed on your system i.e. th output of the locate program (see above)

       > 
        sudo mv /usr/bin/snx /usr/bin/snx-bin
        sudo 
echo 'LD_PRELOAD=/opt/custom/ViaVoice/lib/usr-lib/libstdc++-2-libc6.1-1-2.9.0.so /usr/bin/snx-bin "$@" ' 
> /usr/bin/snx

        sudo chmod u+rsx  /usr/bin/snx
        sudo chmod go+x  /usr/bin/snx
       


[LIST]
Run firefox as root login and run applications:
[/LIST]


       > 
        xhost +local:0
       
       > 
        kdesudo firefox
       
or
       > 
        kdesu firefox  
       
or
       > 
        gksu firefox  
       

---

### Post by doum on 2008-03-13
Hi,

	
Does someone could send me the snx_install.sh. We have SSL VPN at work, I use it on Windows, but not download the client Linux on the site of Checkpoint, they tell me that I have no right to download

Thank you very much

---

### Post by deloptes on 2008-03-22
Hi, my .snxrc  looks like this (replace HOSTNAME and MY_USER_NAME with yours)

cat .snxrc

server          HOSTNAME
username        MY_USER_NAME
reauth          yes
debug           1
cipher          RC4


regards

---

### Post by ekravche on 2008-04-13
I'm confused. Why do you need to run firefox in order for this to work?

> **deloptes said:**
> Our company just switched to a gateway version of CheckPoint with SNX for linux.

I found a way to make it run. (see below) I am just concerened about the security, because I have to run the stuff as root, because snx needs root access to create and modify ethernet devices etc.

Do you have a suggestion how the thing could be tight up?

The problem in details I have to run firefox as root, then a java applet is using snx to build the connection and from inside this java applet I can lounch programs on my linux system that are executed in the VPN environment AS ROOT .... exactly what I don't like

Thank you in advance

[LIST]
Prepare:
[/LIST]

Find compatible libstdc++-2-libc6. On debian I had a problem with this, because this package is not in the official distro (I needed this before for testing ViaVoice, so thats why it is in this place). You should be able to find it i.e. as RPM package or tar.gz or similar nad install or unpack it somewher. Also the minor version numbers could be different ... don't worry. Important is that it works on your system.

       

[LIST]
Edit:
[/LIST]

Move the snx binary to snx-bin and create a script as shown below
Replace the library path to the library that is installed on your system i.e. th output of the locate program (see above)

       


[LIST]
Run firefox as root login and run applications:
[/LIST]


       
       
or
       
or

---

### Post by deloptes on 2008-04-14
> **ekravche said:**
> I'm confused. Why do you need to run firefox in order for this to work?

because i have to connect first to the website of the company ... for this I need firefox.
It runs there an applet (Network Extender) which talks to the snx binary and does the network and authentification stuff.

The problem is that in SUSE I  was able to install everything trough my user (except it asked once for root access but it goes over sudo or so).
Since then I can use the snx without problems.

Under debian I lack this "extended user rights" so I have to run firefox as root, so it can do the network stuff.

The thing I call extended user rights is very simple. Under Suse, when I want to change some system setting I don't need root password, but I provide my user password. In debian it is not the case and I don't know why it is working like this but it definitely has to do something with how KDE integrates sudo.

If you have ideas or questionis you are wellcome.

kind  regards

---

### Post by deloptes on 2008-06-10
From the command line

```
sudo snx -s YOUR_VPN_SERVER -u YOUR_VPN_USER_NAME
```

works on debian

to disconnect

```
sudo snx -d
```

sudo is needed to set network routing and dns lookups

regards

---

