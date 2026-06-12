---
title: "installing wvdial without internet connection"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by salima on 2010-09-04
i am hoping a moderator will be able to open the attached pdf file for me and paste it into the message because i am not able to-working with broken equipment that may shut down any second...

i have ubuntu 10.04 and need to connect modem with wvdial, which is on the iso file but not installed. the pdf shows instructions how to do this offline using synaptic and i am stuck on the last step. the instructions are from a thread and there is a bug report, it is a known issue. want to connect huwaei ec325. i had it going in 8.10, all i need is wvdial.

there may be something wrong with my synaptic package manager...please open the file and print for me into the message...also move to a different forum if it is better than here.

Edit -
I am trying to connect my huwaei ec325 modem with wvdial like i did in 8.10 and have got everything ready but no wvdial...i tried this but i think it wont work unless i am online...right?

root@salima-desktop:~# wvdialconf
The program 'wvdialconf' is currently not installed. You can install it by typing:
apt-get install wvdial
root@salima-desktop:~# apt-get install wvdial
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package wvdial
root@salima-desktop:~#

i tried to follow these directions for installing while offline from another thread:

Update for Ubuntu 10.04
Although wvdial and dependencies are included into CD of 10.04 are NOT installed by default!
Bug#400573
You do not need to download them, just use the .iso or LiveCD or LiveUSB following the procedure below:
1. right click ubuntu-10.04-desktop-i386.iso and 'open with archive mounter'
(or mount LiveCD/LiveUSB)
2. right click on icon created (from 1) to 'browse folder'
3. create a folder on Desktop (ex. named 'wvdial')
4. copy into that folder all 4 .deb files that exist into .iso/LiveCD/LiveUSB
5. use System > Administration > Synaptic Package Manager
and then from menu File > Add downloaded packages > double click Desktop and then the folder
you created at point #3, click open, follow instructions to install

 here is where i got stuck-when i click on OPEN it goes back to ground zero...page disappears
also the options are only 'ADD, CANCEL, OPEN'________________________
no need to read on if you see what i am doing wrong and can help me out...but i suspect there mabe something wrong with the synaptic manager because it will not list any packages other than what are installed and if i click on reload it gives me a long list of 'failed to fetch'...but maybe this is because i am not online?

I found this synaptic problem in the help files:
Under some rare circumstances the actual installation or removal of a package can fail. As a
consequence all other marked changes are canceled, too.
Synaptic Package Manager requires a clear environment with no half installed packages to
perform additional changes. But at the moment there is no way to continue canceled installations
within Synaptic Package Manager.
To fix this situation type the following command in a terminal, then press Return: apt-get install -f
apt-get install -f
here is what happened when i tried the fix:
root@salima-desktop:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@salima-desktop:~#
synaptic still does not work when following the above instructions
..i have also seen threads that say i need modeswitch and modem manager which i believe i do not have but nay not need.

---

### Post by varunendra on 2010-09-04
Try this link to download .deb package of wvdial:
[http://ftp.debian.org/debian/pool/main/w/wvdial/wvdial_1.60.1+nmu2_i386.deb](http://ftp.debian.org/debian/pool/main/w/wvdial/wvdial_1.60.1+nmu2_i386.deb)

If downloads successfully, copy it to your desired machine and try installing manually.
(although this isn't recommended method)


EDIT:
Additional links for dependencies (install them first in the order they are given):
[http://kr.archive.ubuntu.com/ubuntu/pool/main/x/xplc/libxplc0.3.13_0.3.13-1build1_i386.deb](http://kr.archive.ubuntu.com/ubuntu/pool/main/x/xplc/libxplc0.3.13_0.3.13-1build1_i386.deb)
[http://kr.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb](http://kr.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-base_4.4.1-0.2ubuntu2_i386.deb)
[http://ftp.jp.debian.org/debian/pool/main/w/wvstreams/libuniconf4.4_4.4.1-1.1_i386.deb](http://ftp.jp.debian.org/debian/pool/main/w/wvstreams/libuniconf4.4_4.4.1-1.1_i386.deb)
[http://th.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb](http://th.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.4-extras_4.4.1-0.2ubuntu2_i386.deb)
[http://kr.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1_i386.deb](http://kr.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1_i386.deb)

Just download & copy them to your desktop, double-click to install. Install the top one first, then next,...... to the 6th. Install the previously suggested package (wvdial+nmu2) in the last (if required).

However, it will run from commandline only (open terminal, type wvdial, press 'Enter').

If it doesn't help, please provide some description how you used to dial earlier, how was the programs interface, what details you had to feed in it etc.

Also, please confirm:
Is this how your modem looks like? :
 [IMG]http://i621.photobucket.com/albums/tt292/varunjnp/EC325.jpg[/IMG]

---

### Post by salima on 2010-09-04
[SIZE=3]Hey varun![/SIZE]
 [SIZE=3]Thanks, that is my modem all right...all i really needed was to get wvdial...i had followed the instructions and got the files off the iso image and put in a folder, and then they say to add to synaptic and they will install from there. Well they wouldnt...it was driving me nuts until i looked at those files i extracted one more time and they were those little boxes...in the folder on my desktop, just sitting there. Why did they tell me to add them to the synaptic package manager? All i had to do was click on those damn little boxes! dont need no synaptic at all!
[/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]I needn't have posted at all, just kept working on the information i had...but i feel my confidence building already...hope when i come back i will have something more challenging for the community![/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Thanks to everyone-[/SIZE]
 [SIZE=3]salima[/SIZE]

---

### Post by vivek40 on 2010-09-04
Yeah those little boxes are deb files.. You will keep seeing more of them..  :-)

---

### Post by varunendra on 2010-09-04
> **salima said:**
> [SIZE=3][/SIZE][SIZE=3]Why did they tell me to add them to the synaptic package manager? All i had to do was click on those damn little boxes! dont need no synaptic at all![/SIZE]

Because synaptic has the capability to determine the dependencies in advance & thus installing the whole bunch in correct order, in one go.

Anyway, you're trying hard & getting your problems solved ultimately, even through non-standard ways, this is the best part from the point of view of learning as I can see.

Congrats!

---

### Post by qkzoo on 2011-03-14
Hello,

I'm trying Ubuntu again, and have just installed Maverick.  I live out in the sticks and don't have a network connection the Maverick unit can use right now.  All solutions require me to download and install wvdial, but as this thread is titled, I don't have an internet connection on that computer.  With it being Maverick, I assume that the above files won't work for it, so where and what files do I download and install to do this in Maverick?

Thank you in advance for any assistance!

Q

---

### Post by varunendra on 2011-03-15
> **qkzoo said:**
> Hello,

I'm trying Ubuntu again, and have just installed Maverick.  I live out in the sticks and don't have a network connection the Maverick unit can use right now.  All solutions require me to download and install wvdial, but as this thread is titled, I don't have an internet connection on that computer.  With it being Maverick, I assume that the above files won't work for it, so where and what files do I download and install to do this in Maverick?

Thank you in advance for any assistance!

Q

If you have Maverick CD or its iso image, then you can do what Salima did (see post #3).
That is, install the packages from the CD or its iso image itself.

Wvdial installation packages are located in "pool/main/w" directory in the maverick installation CD. Just browse to it, then install the packages (by simply double-clicking them) in the following sequence:-

[LIST=1]
[*]libuniconf4.6_4.6.1-1ubuntu1_i386.deb (located in "**pool/main/w/wvstreams**" directory)
[*]libwvstreams4.6-extras_4.6.1-1ubuntu1_i386.deb (located in "**pool/main/w/wvstreams**" directory)
[*]libwvstreams4.6-base_4.6.1-1ubuntu1_i386.deb (located in "**pool/main/w/wvstreams**" directory)
[*]wvdial_1.60.4_i386.deb (located in "**pool/main/w/wvdial**" directory)
[/LIST]
Please note that it is necessary to install them in above order, otherwise the installer will give "dependency not satisfied" error.

Also, depending upon different released versions of the CD, the packages maybe named slightly differently (not sure though), but they should be located in the same place in the CD as I mentioned above. So look for similar names if exactly same packages are not found.

Hope it helps.

-Varun

---

### Post by qkzoo on 2011-03-15
Thank you.  I think number one and number two should be swapped, only because it yelled at me (really), that it needed the file in number two first.  Once I installed it, the first one installed fine.  The wvdial file seemed to install fine and then I got an "Unhandable Error Due to Apt".  I hit ok, and it said that it was installed, but I clicked the reinstall button anyhow, and it went smooth that time. 

Now onto the next step in this adventure!

---

### Post by varunendra on 2011-03-15
Well, just to make sure the correct sequence, I retried the installation (on a fresh installation on virtualbox) and to my surprise, this time the installation succeeded only with the following sequence:

[LIST=1]
[*]libwvstreams4.6-base_4.6.1-1ubuntu1_i386.deb
[*]libwvstreams4.6-extras_4.6.1-1ubuntu1_i386.deb
[*]libuniconf4.6_4.6.1-1ubuntu1_i386.deb
[*]wvdial_1.60.4_i386.deb
[/LIST]
that is, 3>2>1>4 corresponding to my previous post, and not even what you suggested as a correction.. :)

And the "Unhandable Error Due to Apt" error you mentioned - I got it too - both times, but didn't mention it earlier to avoid confusion, since it got installed anyway.

Let's hope it's normal. Although couldn't understand the reason for sequence change. Same virtual machine, same iso image, no internet connection both times - weird!:confused:

---

### Post by qkzoo on 2011-03-16
I confirm, I installed it on my netbook with a clean install of Maverick, and got the same response.  As long as it continues working then I'm good! :D

---

