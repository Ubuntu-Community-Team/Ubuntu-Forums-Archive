---
title: "[SOLVED] Can't install ndiswrapper in Edgy"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Wildboar on 2007-04-12
I'm having trouble installing Ndiswrapper in Edgy.  When following the installation instructions in "Install" file, I can't create a link to the kernel from modules.  Instructions aren't clear which directories I need to be in to run these steps.  Subsequent tries to install fail.

Frankly I haven't worked with unix for about ten years and don't remember all the neat stuff.  I have to keep rebooting to XP to get online and look up solutions that I can understand, if I can find them, then reboot to try it, what a pain.

Does anyone know good step-by-step instructions for newbie to getting this thing running?

Here's my relevant info:

Edgy Eft
NDISWrapper, Ver 1.38
Netgear WG311v3
Dual Boot w/XP
XP drivers on hand, three versions
AMD Athalon
Brain fried otherwise competent computer guy.

---

### Post by renzokuken on 2007-04-12
have you tried using automatix to install ndiswrapper. removes the hassle of compiling anything yourself.

[www.getautomatix.com](www.getautomatix.com)

---

### Post by Wildboar on 2007-04-12
Quote:  Have you tried using automatix to install ndiswrapper. removes the hassle of compiling anything yourself.

Sounds good except that automatix wants to access the internet to run and I can't get my networking hooked up without ndiswrapper.  Any other sugestions?

---

### Post by renzokuken on 2007-04-13
hehe, good point, overlooked that didnt i.

in that case you will need the actual ndiswrapper deb file.......i cant remember what the url is for all the repos but hopefully someone can help on that front.

download the ndiswrapper .deb file on a pc with a working connection, transfer it to your ubuntu desktop with a flash key, then run the following command to install the .deb file

```
sudo dpkg -i ndiswrapper-version-number.deb
```

obviously replace version number with the actual file name.........you may also need the ndiswrapper-common and ndiswrapper-utils .debs too

---

### Post by EvanPMeth on 2007-04-13
Just for reference the ndiswrapper through the repositories didnt work for me on edgy , did not correctly install modules. I had to build from source. With out internet it will be a little harder, because there are a few dependencies:
**linux-headers-2.6.17-10-386** ( or which ever version kernal you are running to check type 'uname -r'  ) 
**build-essential** (has a good amount of deps by itself)
__there are probably more i just forgot__

*Since you do not have internet connection you will have to download all the dependencies in deb format from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) be sure you get the right corrosponding packages "edgy" "i386" etc (good luck :) )*
(or you could just find a really long ethernet cord)

To build from source. it is actually pretty easy;

- get the tarbell from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page")
- untar: **tar xvfz ndiswrapper-1.41.tar.gz**
- change directory: **cd ndiswrapper-1.4.1.tar.gz**
- start the build process: **make**
(check for errors or missing dependencies)
- if all goes well with make:
**sudo make install**

(now ndis wrapper is intalled)
Now for the fun stuff ( configuring ndis, actually its easy)
I have had the most luck with having the wireless card im installing out of the machine or not plugged in durring the instalation process.

- Locate your drivers .inf file, DO NOT just copy the .inf file leave it in its directory, the inf just tells ndis what and how to use the other files, it is not the actual driver.
- install it **sudo ndiswrapper -i YOURINF.inf**
- update modules **sudo depmod -a**
- test ndis module **sudo modprobe ndiswrapper**
- initiate ndiswrapper as a system startup module **sudo ndiswrapper -m**

now set ndiswrapper in system modules:
**sudo gedit /etc/modules/**

''...add to bottom of the listing...''
**ndiswrapper**

IF you are using a usb device you may have to set the mac address just to be safe
**sudo gedit /etc/iftab/**

''...add to bottom of the listing...''
**wlan0 mac 00:00:00:00:00:00**
[I](I dont think this is needed because I had a usb dongle installed and replaced it with a pci wireless card and updated the ndis wrapper drivers with the pci card drivers and I didnt change the mac address in iftab and it worked fine, i believe the newer versions of ndiswrapper handle mac address checking.)
[/I]

- now setup your wireless interface (wlan0): sudo gedit /etc/network/interfaces
in the interfaces file remove the "#" infront of 

```
# auto wlan0
# iface wlan0 inet dhcp

```

then add your wireless info bellow (essid is the name of your network):
THIS IS FOR A NETWORK WITHOUT  "WEP" for better trouble shooting turn off the wep. (will configure that later).
```

 auto wlan0
 iface wlan0 inet dhcp
        wireless_mode managed
        wireless-essid ACCESS_POINT_NAME

```

*I did this also just in case, dont know if it does anything different:*
**sudo iwconfig wlan0 essid ACCESS_POINT_NAME mode managed**

NOW shutdown the computer and unplug it and plug your wireless card back in.
IF USB do not plug it in now, wait till it starts up again.

Turn your computer back on wait till its done starting up (plug in your usb if not pci) and test that beast: **ndiswrapper -l**
Should look like the following with the driver installed and the device present.
```
mrv8000c : driver installed
        device (11AB:1FAA) present
```
*(yours will reflect the driver and card number of your device)*

test your internet: **ping [www.google.com](www.google.com)**

now if its working you can turn the routers wep back on and set the password by doing the following:
**sudo iwconfig wlan0 essid ACCESS_POINT_NAME mode managed key TEXT_WEP_KEY restricted**

Hope that helps correct me if i messed up on anything: :)

-EvanPMeth

---

### Post by Wildboar on 2007-04-13
Ok, I couldn't figure out what dependancies I needed so I tried going on without them with 1.41.  Went better than with 1.38 but still got two pages of errors.

I went ahead and started the install in my home directory but that probably wasn't the best choice.  

First part went well, unpacked fine, make went fine until (see sample of the two pages of errors below).

I assume it's because I didn't have the dependancies satisfied.  Current questions are:

[B]Does anyone know which dependancies I need to download from [http://packages.ubuntu.com/?](http://packages.ubuntu.com/?)

How to install them (Manually, no connetion to internet while booted to Ubuntu)?

Which directory is best for installing NDISWrapper, Drivers, and dependancies given the  directory structure of Linux.[/B] 

I'll figure this out as I learn more but don't want to clutter up the file structure in the mean time.


```

gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory


In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory


In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;


```

etc...  just a sampeling of the three pages of errors I got

---

### Post by EvanPMeth on 2007-04-13
> Does anyone know which dependancies I need to download from [http://packages.ubuntu.com/?](http://packages.ubuntu.com/?)

How to install them (Manually, no connetion to internet while booted to Ubuntu)?

Which directory is best for installing NDISWrapper, Drivers, and dependancies given the directory structure of Linux. 

Some dependencies might be on the ubuntu cd that you used to install ubuntu, so you can try **sudo apt-get install build-essential** with the cd in. (this will look at your /etc/apt/sources.list file for repositories of packages that are either on internet servers or in your case since you do not have internet, the install cd. If it doesnt come up with anything as in *E: Couldn't find package build-essential* then you will have to go to the packages website.

 (It would almost be easier and faster to move your computer to the router and plug it in, get all  teh dependancies and wireless working and move it back.)

To install them, you just go part way down the page with the package you want to install (eg. [http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10) )  and choose the system you are using, i386 probably, and save it and transfer it to your ubuntu partition and install using gdebi( [http://monkeyblog.org/ubuntu/installing.html#deb](http://monkeyblog.org/ubuntu/installing.html#deb) )

In regards to which directory is best when building the source of ndiswrapper, it doesnt matter where you build it. Building a from source is kind of temporary. The directory is used to compile the source and then "make install" moves the compiled modules and binaries to your system paths, that is why you need to have root privleges when running make install and not make. The original directory with the source and make files init are kind of useless after you install them, unless you want to reinstall or uninstall the program(ndiswrapper). Uninstall reverses "make install" with "make uninstall" (that is only if the source package was designed with that option, some dont have the uninstall option)

Your home(your username) folder is used for storing user preferences and whatever you want to store also, like build folders so thats fine you will not effect the file structure. 

ALSO when do you get the errors when you running make?

---

### Post by Wildboar on 2007-04-13
Ok,
  Got NDISWrapper installed, build-essential from the CD fixed that.  No errors on MAKE or MAKE INSTALL.  When I run NDISWrapper though I get:

```
bret@hand-built-bret:~/WG311v3$ sudo ndiswrapper -i WG311v3.inf
installing wg311v3 ...
couldn't open WG311v3.inf: No such file or directory at /usr/sbin/ndiswrapper line 174.
bret@hand-built-bret:~/WG311v3$ 
```

Did the rest of the steps suggested by Evan.  Forgot where it was but somewhere I got "Invalid driver".

Run NDISWapper again and it says it's says,"wg311v3 already exists".  **NDISWrapper -r** removes it but I get the same response (See code) each time I install.  Tried it with and without card installed.

What silly little thing am I overlooking now?

Thanks for the help thus far.

---

### Post by EvanPMeth on 2007-04-15
Ndiswrapper will seem like it installs a driver even though it doesnt. that is why you can remove it and it says it is already installed. 

If it says that the file is not found, that meens there is not a file by that name in that directory, make sure you have correct spelling and capital letters and in the correct directory. Also make sure you have all of the other files associated with the .inf file in the same directory not just the inf file. 

You could try renaming it to something easy to type in and try it again.

-EvanPMeth

---

### Post by Wildboar on 2007-04-15
Well, I moved the files into the same directory with ndiswrapper and it worked fine.  Ndiswrapper -l shows the card as it should.  I disabled WEP on the router and in XP (same computer) and am able to connect with XP.  

When I try to ping from Ubuntu it says "Network unreachable" or words to that effect and Firefox won't browse to the router or internet.  Any sugestions?

Wildboar

---

### Post by Floppyjoe on 2007-04-16
> **Wildboar said:**
> Well, I moved the files into the same directory with ndiswrapper and it worked fine.  Ndiswrapper -l shows the card as it should.  I disabled WEP on the router and in XP (same computer) and am able to connect with XP.  

When I try to ping from Ubuntu it says "Network unreachable" or words to that effect and Firefox won't browse to the router or internet.  Any sugestions?

Wildboar

you probably need to edit your /etc/network/interfaces file to add  the necessary information about your connection there if you are not using network-manager.
```
sudo gedit /etc/network/interfaces
``` 
I usually add something like this to my network interface:
```
wireless-essid YourRouterSsid
wireless-channel 6 #Your router channel goes here instead of six#
wireless-mode managed

```

---

### Post by Wildboar on 2008-01-10
Update.

Well, my leg finally healed before I ever got it working.  I did however try again when Gutsy came out and everything installed like clockwork.  Up and running now.

Thanks to everyone who tried to help me out back then.

---

### Post by Wildboar on 2008-01-19
Well, I never did get it to work in Edgy but ndiswrapper worked like a charm first try after I installed Gutsy.  I did refer back to this thread to refresh my memory.  

Thanks for the help guys.:guitar:

---

