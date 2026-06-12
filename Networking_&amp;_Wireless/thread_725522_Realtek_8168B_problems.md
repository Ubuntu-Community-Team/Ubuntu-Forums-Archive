---
title: "Realtek 8168B problems"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by SalamanderSSC on 2008-03-15
I've been having a bunch of problems with a RTL8111/8168B PCI Express gigabit ethernet controller.  For some time, I was unable to get it to actually work, then I installed the windows driver using ndisgtk, which worked very well.  However, most of the time when the computer is restarted the windows wireless drivers gui says that the hardware isn't even there and it doesn't work at all.
Anyone know how to fix it?

---

### Post by nator on 2008-03-22
Somebody else figured this out, I am just a n00b for this stuff, but my Realtek RTL8111B/C is now working.

[http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998](http://www.linuxquestions.org/questions/linux-networking-3/no-network-detected-realtek-81118168-issue-615047/#post3029998)

Props to jio23

And retyped here due to type-o's in the original

Note: the file version in this example is "r8168-8.004.00", the latest is "r8168-8.005.00"

1 - Downloaded current driver from :
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)
2 - Unpacked on the Desktop
3 - $ sudo mv r8168-8.004.00 /usr/src
4 - $ cd /usr/src/r8168-8.004.00
5 - $ sudo make clean modules
6 - $ sudo make install
7 - $ sudo depmod -a
8 - $ sudo insmod ./src/r8168.ko
9 - $ lsmod -a | grep 8186 #just to check it was there
10 - $ cd /etc/modprobe.d
11 - $ sudo touch blacklist-network
12 - $ vi blacklist-network # add "blacklist r8169" to the file
13 - $ sudo update-initramfs -u #to make the change permanent
14 - reboot
15 - ethtool -i eth0 #to see new driver assigned

---

### Post by GroteBozeWolf on 2008-04-25
I had the same problem.. After a while i figured out i had to load the r8168 driver instead of the r8169 driver, because that driver doesn't work. I compiled the r8168 driver from source. Download the latest source from realtek. Then patch it with this patch:
[http://ubuntuforums.org/showpost.php?p=4718501&postcount=4](http://ubuntuforums.org/showpost.php?p=4718501&postcount=4)

It's a bit messy, i fooled around a bit to get it compiled, because there is a problem with a path in the Makefile. It *might* have worked as well if i had put the whole driver in /src and a copy in /src/src.
The driver is not very stable, if i copy a lot of data, it crashes my laptop. I hope the r8169 driver will be usable in the near future.


untar the realtekdriver in /usr/src

cd /usr/src/realtekdriver/src

sudo patch < /home/roel/patchfilename.patch
cd ..

Then i did some tricky stuff; there's a problem with a path in the realtek driver.


sudo make modules

(error) It can't find /src/src
sudo mkdir /src

Make a symlink in /src/src
sudo symlink /src/src /usr/src/realtekdriver/src 

(still in /usr/src/realtekdriver/src)
sudo cp ./* /src
sudo make modules

it compiles now.. cd to /src/

sudo make install
sudo depmod -a

Blacklist the old module. Open /etc/modprobe.d/blacklist, add a line:
blacklist r8169

Update initramfs, it won't work without this!
sudo update-initramfs -u

---

### Post by nullness on 2008-05-01
There has been a new version of the driver out for over a week r8168-8.006.00, see the last couple posts on page 2 in: [http://ubuntuforums.org/showthread.php?p=4718501](http://ubuntuforums.org/showthread.php?p=4718501)

I've been using the new driver with the changes from the patch in the thread i linked above for a week now and I've sent over 100GB and received over 100GB during that time and have yet to have any issues at all.  Make sure you do not set your MTU above 4096 (Driver doesn't let you by default) and you should be okay.

I'm on Hardy Server amd64 with a Realtek RTL8111/8168B built-in adapter.

---

