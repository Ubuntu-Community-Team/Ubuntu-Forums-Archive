---
title: "Ubuntu friendly printer.. Canon PIXMA MX320?"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by humphreybc on 2010-01-10
This is on special at Dick Smith:

[http://www.dse.co.nz/dse.shop/4b49b00e0292dcb2273fc0a87f3b06f2/Product/View/XP3200](http://www.dse.co.nz/dse.shop/4b49b00e0292dcb2273fc0a87f3b06f2/Product/View/XP3200)

I think it should work with Ubuntu - the Canon website has downloadable .deb files for the drivers and even their own scanning software.

This one is cheaper, but I don't think it plays nice with Ubuntu straight away:

[http://www.dse.co.nz/dse.shop/4b49b00e0292dcb2273fc0a87f3b06f2/Product/View/XP5521](http://www.dse.co.nz/dse.shop/4b49b00e0292dcb2273fc0a87f3b06f2/Product/View/XP5521)

Advice please?

---

### Post by Redache on 2010-01-10
It really does depend on which one is best for you.

Epson normally work well with Ubuntu, Canon are half and half but if there's a .deb then it's a safe bet that it will work perfectly.

As far as the Epson is concerned, I could not find the exact model on the Open Printing Database, but there is an entry for a t20, which I would assume is similar if not identical to the t21.

[Open Printing Database Entry]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_T11_S20_T20_T20E_T23_T26_T10")

The Open Printing Database is a good resource for finding out how well printer models function with Linux and it usually tells you what needs to be done to get reasonable or full functionality.

Hope this helps.

---

### Post by ricardo1 on 2010-01-11
hi [humphreybc]("http://ubuntuforums.org/member.php?u=785254")
I'll be interested if you get the Canon Mx320 working for linux. As I'm interested in purchasing this printer also.

I've also found the following info :

MX320 series ScanGear MP Ver. 1.30 for Linux(rpm Packagearchive)
[http://support-au.canon.com.au/contents/AU/EN/0100187101.html](http://support-au.canon.com.au/contents/AU/EN/0100187101.html)

MX320series IJ Printer Driver Ver. 3.10 for Linux (rpm Packagearchive)
[http://support-au.canon.com.au/contents/AU/EN/0100187801.html](http://support-au.canon.com.au/contents/AU/EN/0100187801.html)

Please let me know you go.

cheers :D

---

### Post by humphreybc on 2010-01-11
Hey,

I actually went down to the store today and they had an HP Deskjet F2480 for $89.00 - Printer/Scanner - can't complain! I bought that and installed the latest hplip drivers from their website and scanning/printing works perfectly.

I think the MX320 will work if Canon provide a .deb driver for Linux!

---

### Post by ricardo1 on 2010-01-11
thanks for the update.
It's great that there's good support for all these printers with linux. :)

---

### Post by SirBismuth on 2010-01-11
> **humphreybc said:**
> Hey,

I actually went down to the store today and they had an HP Deskjet F2480 for $89.00 - Printer/Scanner - can't complain! I bought that and installed the latest hplip drivers from their website and scanning/printing works perfectly.

I think the MX320 will work if Canon provide a .deb driver for Linux!

When I was looking for a printer in December, my first port of call was the OpenPrinting Database.  I had decided on an HP printer, as their products seemed to have the best support in Linux.  After checking the OpenPrinting site, the main HP site for specs, and local online and offline vendors, I settled on the Photosmart C4683, as it apparently works OOB.  Not that I mind a bit of setting up, done it enough times with various peripherals already.  Once it was setup, and I was ready to connect the USB cable, I checked and already had the HPLIP "drivers" installed, so I plugged the cable in, and it detected the printer and added it to my Printers automatically, printed a test-page successfully, and haven't looked back.

But yeah, if the vendor supplies Linux-specific drivers, there is a good chance it will work, more than likely with full functionality.  I have tested the scanning with the HP as well, and works fine, will look at that in more detail as the need arises.

B

---

### Post by aarongc on 2010-01-19
Hi, I bought a Canon MX320 back in September 2009 and got it working with Ubuntu (both printing and scanning, even multi-page scanning) after a little looking around. It turns out that Canon does actually provide a .deb -- but only on the Canon Europe website! When I asked Canon USA, even after I found the driver, they flat-out denied its existence. Let me know if you have trouble finding it.

---

### Post by donaldt on 2010-01-19
I have had a Canon PIXMA MX860 for six months.  It works great with bluetooth wireless capability and does scanning, printing and faxing.  I found the best program to use was turboprint (out of Germany).  Yes, I had to pay for it, but it provides everything you need under Ubuntu for the multi-mode printer.  Try it for 30 days free.

Donaldt:

---

### Post by neversleep54 on 2010-01-28
i have ubuntu 64  e canon mx320

NO WORK !!!!!

architecture error i386...


HELP ME PLEASE !!!

---

### Post by neversleep54 on 2010-01-28
[QUOTE=neversleep54;8737240]i have ubuntu 64  e canon mx320

NO WORK !!!!!

architecture error i386...


HELP ME PLEASE !!!

on the web i can found the source
if i compile it do you think that work ?
how can i compile it?

---

### Post by Jason Argonaut on 2010-05-13
What tool  do i use to install those?  ark doesn't work, sh won't run install.sh

---

### Post by Jason Argonaut on 2010-05-13
it doesn't work for me either.

sh -l -e install.sh  on the un-ark'd canon downloads fails completely.  
Isn't there some slightly more sophisticated?

---

### Post by manu7irl on 2010-05-14
That did the trick for me on Ubuntu 10.04 64 bit!
Simply run in terminal from the folder where you placed the 2 packages :

Code:

```
sudo dpkg -i --force-architecture ./cnijfilter-common_3.10-1_i386.deb
```

and then :

Code:

```
sudo dpkg -i --force-architecture ./cnijfilter-mx320series_3.10-1_i386.deb

```




Emmanuel.

Pc configuration :
motherboard : gigabyte GA-MA785G-UD3H
processor : AMD Athlon II quad core 630 2.80Ghz
memory : 2 x 2 Gb DDR2 800Mhz
video card : onboard ATI HD4200
OS : dualboot grub2 Ubuntu 10.04 64bits / Windows 7 32 bits

---

### Post by panicatac on 2010-10-31
This was working for me, but not any more. It can't find a file, libgimp-2.0.so.0

I suspect that this file has been updated, and now has a new name? Does anyone know how I would edit the scangear files so that they call the new version of libgimp?

Or am I on the wrong track here?

---

### Post by Tomas_IV on 2011-01-27
> **panicatac said:**
> This was working for me, but not any more. It can't find a file, libgimp-2.0.so.0

I suspect that this file has been updated<SNIP>

Hi,
I'm not actually on my Ubuntu box, but I have coped with such problems before. If the package was updated indeed, and there is no possibility to install the older version, this might work (in terminal window):
[LIST=1]
[*]Check the installed/available packages. 
```
aptitude search libgimp
```
on my Debian it yields:
```
i libgimp2.0 
p libgimp2.0-dev
p libgimp2.0-doc
```
[*]If there is libgimp2.0 and is not installed, install it with 
```
sudo aptitude install libgimp2.0
```
If it does not help, continue on. If there is not libgimp2.0, you have to try to install, or use already installed, newer version. Then proceed to next step.
[*]Search for the exising library files in the filesystem:
```
dpkg -L libgimp2.0 | grep libgimp-
```
my Debian shows:
```
/usr/bin/libgimp-2.0.so.0.600.10
/usr/bin/libgimp-2.0.so.0
```
so I do have, unlike you, the file needed. Of course, your libgimp package might be of other version than 2.0, so in the dpkg command use the one found in previous step. 
The file with the longer filename is the actual library, the other is a symbolic link and there could be more of them. As you have this problem, either the symbolic link does not have the exact name needed, so there is for example something like *libgimp-2.0.so* instead of *libgimp-2.0.so.0* or the library is really higher version, so there could be something like *libgimp-2.0.1.so.0*. In either case proceed to next step.
[*]Create additional symbolic link with the right name:
sudo ln -s /usr/bin/libgimp-2.0.so.0.600.10 /usr/bin/libgimp-2.0.so.0
sudo ldconfig
Of course, the first file in the *ln* command should be the one from *your* listing from previous step.
[/LIST]
Now cross your fingers and try to run the software, first time in  the terminal window to see messages. If the symbolic link had only changed name and the library on your system is actually of the version 2.0, it should work with high probability. If the library is higher version, it still might work, but it could also crash right avay during starting or it could run, but be unstable. 
It is good idea to keep note of such manual changes to your system somewhere, because such manually added files in the /usr tree may cause a problem later -if the library in some update has the symbolic link back again, the one you created manually will prevent the update to be installed. So you should know you added this file and delete it to solve the problem.

---

### Post by hmazuji on 2012-02-10
deleting post because it doesn't add any value

---

### Post by hmazuji on 2012-02-10
deleting post because it doesn't add any value

---

### Post by adamns on 2012-02-26
This worked perfectly for me. 

Disconnect printer from computer.

[FONT=Arial Black]**sudo add-apt-repository ppa:michael-gruz/canon** 
[B]sudo apt-get update
[/B]**sudo apt-get install cnijfilter-mx320series**[/FONT]

[FONT=Arial Black]After *canon printer driver* installed properly, connect canon printer to your computer and turn it  on. Canon printer will be automatically detected by the system. Printer ready to use.

Here is the link to where I found it:

[http://ubuntuportal.com/how-to-install-canon-printer-driver-for-linux-ubuntu/](http://ubuntuportal.com/how-to-install-canon-printer-driver-for-linux-ubuntu/)
[/FONT]

---

### Post by hmazuji on 2012-03-30
i couldn't use this solution.  i think i had a problem with the add or apt command, then another with adding the apt command using package manager.  is this a 32 bit driver ?  i have tried to use a i386 driver on amd64 operating system, and it doesn't want it.
the solution i am going to try next is to download the source code, and use:
[http://www.webmonkey.com/2010/02/compile_software_from_source_code/](http://www.webmonkey.com/2010/02/compile_software_from_source_code/)

---

### Post by kurt18947 on 2012-03-30
> **hmazuji said:**
> i couldn't use this solution.  i think i had a problem with the add or apt command, then another with adding the apt command using package manager.  is this a 32 bit driver ?  i have tried to use a i386 driver on amd64 operating system, and it doesn't want it.
the solution i am going to try next is to download the source code, and use:
[http://www.webmonkey.com/2010/02/compile_software_from_source_code/](http://www.webmonkey.com/2010/02/compile_software_from_source_code/)

I don't have a Canon but Brother has a similar problem.  The drivers are 32 bit, there are no 64 bit printer drivers.  Among the "pre-install requirements" is this:
**Related distributions**Debian 64 bit version, Ubuntu 64 bit version**Related products/drivers**printer/PC-FAX drivers**Requirement****ia32-libs** or **lib32stdc++** is required to be installed."Perhaps this applies to Canon as well.  My understanding is that the above permit a 64 bit O.S. to use 32 bit hardware drivers.

---

### Post by hmazuji on 2012-04-08
[SIZE=4]i have the feeling that this is a gnome problem or that i'm using the wrong shell.  the directions on
[http://www.webmonkey.com/2010/02/compile_software_from_source_code/#disqus_thread](http://www.webmonkey.com/2010/02/compile_software_from_source_code/#disqus_thread)
weren't comprehensive enough, and i can't post questions there regarding their directions as: "Comments for this page are closed."
i have downloaded the source code from:
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MX_series/PIXMA_MX320.aspx?DLtcmuri=tcm:14-731997&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MX_series/PIXMA_MX320.aspx?DLtcmuri=tcm:14-731997&page=1&type=download)
i have downloaded gcc and g++ using synaptic package manager.
i have:
tar xzvf cnijfilter-source-3.10-1.tar.gz
the source file.
cd cnijfilter-source-3.10

this is where i am stuck.  can't continue with the directions because
root@debian:/home/lou/Downloads/cnijfilter-source-3.10# ./configure
comes back with:
bash: make: command not found

as with
root@debian:/home/lou/Downloads/cnijfilter-source-3.10# make
bash: make: command not found

i couldn't continue on with the installation.

what do i do now ?
(beside run a futile search on google for "[/SIZE][SIZE=4]bash: make: command not found")[/SIZE]

---

### Post by ixtok on 2012-04-08
I just installed a canon pixima printer the other day using similar drivers obtained from the Canon-asia support area.

I downloaded the printer and scanner deb packages. They downloaded into my a dirictory I created called "canon" in my home directory.

Using the file viewer, I navigated to the canon directory and I clicked on one and as it is a tar file, I chose to extract it. A new directory was created within the download directory containing the necessary files.

I opened the terminal and typed "dir" this lists the directories. I typed "cd canon" to get to the canon directory.

I typed dir to list the directories and files within that directory.

I typed "cnijfilter....3,40-1-deb" to enter that directory

I typed "dir" to list the files in that directory, it listed a file  install.sh

I typed sudo ./install.sh

The terminal took over and installed everything, asked a couple of questions and the printer works.

I did the same thing as above with the appropriate file for the scanner.

Printing works fine but to scan I have to use the terminal and type "scangearmp"  

Probably there are faster ways of doing this, but this worked for me.

Good luck in solving your problem.

---

### Post by hmazuji on 2012-04-16
i can't remember if the folder contained an "install" script.

let me check this and get back to you if it works.

---

### Post by hmazuji on 2012-05-03
install.sh doesn't work:

root@debian:/home/lou/Downloads/cnijfilter-source-3.10# cd cnijfilter
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# ls
acconfig.h  autogen.sh    configure.in  include  LICENSE        NEWS    src
AUTHORS     ChangeLog    COPYING       INSTALL  Makefile.am  README
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# INSTALL
bash: INSTALL: command not found
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# ./INSTALL
./INSTALL: line 1: To: command not found
./INSTALL: line 3: syntax error near unexpected token `newline'
./INSTALL: line 3: `        ./autogen.sh --program-suffix=<Printer Model Name>'
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# ./autogen.sh

**Error**: You must have `autoconf' installed to.
Download the appropriate package for your distribution,
or get the source tarball at [ftp://ftp.gnu.org/pub/gnu/](ftp://ftp.gnu.org/pub/gnu/)

**Error**: You must have `automake' installed.
Get [ftp://ftp.gnu.org/pub/gnu/automake-1.3.tar.gz](ftp://ftp.gnu.org/pub/gnu/automake-1.3.tar.gz)
(or a newer version if it is available)
root@debian:/home/lou/Downloads/cnijfilter-source-3.10/cnijfilter# cd ..
root@debian:/home/lou/Downloads/cnijfilter-source-3.10# install.sh
bash: install.sh: command not found
root@debian:/home/lou/Downloads/cnijfilter-source-3.10#

---

### Post by hmazuji on 2012-07-04
1. how do you install autoconf ?

2. how do you install automake ?

---

### Post by hmazuji on 2012-07-04
does anyone know how to make install work ?

---

