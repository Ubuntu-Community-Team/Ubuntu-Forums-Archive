---
title: "HOWTO - rt2500 (Ralink 802.11g) in Gutsy"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by zoiks on 2007-10-21
I struggled a bit to get my Ralink-based wifi card to work after upgrading from Feisty to Gutsy. I use a Ralink-based 802.11g card with WPA encryption (much stronger than WEP) and my router doesn't broadcast the SSID. I didn't want to run ndiswrapper with Windows drivers, I wanted to run the open source drivers which had worked so well for me in the past.

What I came up with is similar to this solution:
d to mention whether or not this
[http://ubuntuforums.org/showthread.php?t=525833](http://ubuntuforums.org/showthread.php?t=525833)

But there are a few differences. It's also similar to this solution

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

except that link is for an rt73 based card. I'll describe here what worked for me.

**0) This is for Ralink RT2500 based g-cards.** Beforehand, let's be clear this is for a Ubuntu Gutsy Gibbon system (7.10) for setting up a Ralink RT2500 based 802.11g card to connect to a network using WPA encryption with a pre-shared pass key, using the native driver for that chipset (originally provided by Ralink and now maintained by serialmonkey [ [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) ] ). It *may* be generalizable to other Ralink chipset cards. To find out if you have a Ralink RT2500 based wireless card, type the command **lspci** at the command prompt. If you see a line that looks something like

```

03:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```

then you do have such a card. If it's a usb device, maybe try **lsusb** (?) (There are hundreds of brands of wireless cards, some use Ralink and some don't. Even specific brands use Ralink for some "versions" of the card, but not others.)

Also, this assumes you've already set up an access point with an ssid, WPA passkey encryption, and appropriate passkey.

**1) Install build and header requirements.** Make sure you install the build prerequisites:

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

**2) Download, compile, and install rt2500 drivers from serialmonkey.** Download the rt2500 drivers from 

[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

In my case, I downloaded rt2500-cvs-daily.tar.gz, which is the latest CVS snapshot. Unpack the file you downloaded, like so

```

tar -zxvf rt2500-cvs-daily.tar.gz

```

(The file name will depend on what you downloaded.)

Now cd into the directory that you just created and into the Module subdirectory. Then compile and install the rt2500 kernel module. In my case it looked like

```

cd rt2500-cvs-2007102014/Module/
make
sudo make install

```

**3) Blacklist the gutsy-supplied rt2500pci driver.** Now the proper kernel module should be installed, but if your situation is like mine, it is not being allowed to run properly because the kernel had already loaded another module called "rt2500pci" which is mucking things up. In order to put a stop to this, you can blacklist rt2500pci by doing the following

```

sudo su
echo "blacklist rt2500pci" >> /etc/modprobe.d/blacklist
exit

```

This adds rt2500pci to the blacklist file, so that it won't load in the future. (For some unknown reason just issuing the command with sudo doesn't work.)

**4) Add correct lines to the network interfaces file.** Make sure the following lines appear in **/etc/network/interfaces**:

```

auto wlan0
iface wlan0 inet dhcp[INDENT]pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "myssid"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="mypskkeystring"
pre-up ifconfig wlan0 up
[/INDENT]
```

You can use the command
```

sudo gedit /etc/network/interfaces

```

to open the file for editing. In the file, replace "myssid" with your network's SSID, and "mypskkeystring" with the encryption passphrase you use for your network. Leave the ssid and keystring in quotes.

**5) Restart your computer or network.** Now you can either A) reboot, or B) enter the following at the command prompt:

```

sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo modprobe rt2500
sudo ifconfig wlan0 up

```

And with any luck your wireless WAP connection to your network using the rt2500 card will be up and running, and should remain so after any restarts. To see if the correct driver module loaded, type at the command prompt:

```

lsmod | grep rt2500

```

The response should at least contain one line that starts with "rt2500" and *no lines* starting with "rt2500pci".

**6) Install optional RutilT graphical utility.** At this point you can also install the program **rutilt** to provide a graphical configuration utility. The Gutsy-provided version seems to work fine. It has been recommended by others that you first remove the **network-manager** package:

```

sudo apt-get remove network-manager-gnome

```

Then you can install the **rutilt** program by doing

```

sudo apt-get install rutilt

```

Now

```

sudo rutilt

```

will allow you to graphically configure the card for new connections (say, at a coffee shop). Note that you can also access RutilT using the GUI menu by choosing **System | Administration | RutilT WLAN Manager**.

I hope this is helpful to others. There is definitely a possibility I screwed something up here in the description, or that I don't realize there's a much easier way to do it, so don't take it as the word from On High. Also, note that some others have added helpful variants or other information below, so be sure to check the rest of this thread for more information.

One more thing: Please feel free to post your response in this thread to mention whether or not this How-To was useful for your setup. This will be helpful in guiding others. Thanks.

---

### Post by maxol on 2007-10-21
I tried this and now when I run RutilT I get the error 

"Critical error: Can't find any wireless network interface. Code :-3

If I remove"blacklist rt2500pci" from /etc/modprobe.d/blacklist I can see my wireless card again bt cannot connect presumably because its using the rt2500pci driver.

Is there a step missing from this HowTo?

How do I tell Gutsy to load rt2500.ko instead of rt2500pci?

---

### Post by kevdog on 2007-10-21
You can save the reboot if you do the following

sudo ifconfig <interface> down
sudo modprobe -r rt2500pci
sudo modprobe rt2500
sudo ifconfig <interface> up

---

### Post by zoiks on 2007-10-21
> **maxol said:**
> I tried this and now when I run RutilT I get the error 

"Critical error: Can't find any wireless network interface. Code :-3

If I remove"blacklist rt2500pci" from /etc/modprobe.d/blacklist I can see my wireless card again bt cannot connect presumably because its using the rt2500pci driver.

Is there a step missing from this HowTo?

How do I tell Gutsy to load rt2500.ko instead of rt2500pci?

Hmm... Here are a couple of guesses:

In your system I think the rt2500 module is not loading for some reason. When that module loads, it should create the wlan0 device/interface.

Presumably, if you type

```
sudo lsmod | grep rt2500
```

you get nothing, right? (while rt2500pci is blacklisted)

If you type

```
sudo modprobe rt2500
```

does this cause the module to be loaded properly? You can tell by reissuing the lsmod command above.

If you type

```
sudo locate rt2500.ko
```

do the responses include the following line

/lib/modules/2.6.22-14-386/extra/rt2500.ko

? It appears that on my system, that is the location from which rt2500 is being loaded (and the location that "sudo make install" in the rt2500 Module directory put the kernel module in). Maybe all you need to do is type

```
sudo depmod -a
```

for your system to figure out where the appropriate modules are located.

---

### Post by maxol on 2007-10-21
> sudo modprobe rt2500

Did the trick.

---

### Post by odiseo77 on 2007-10-21
Hi people. I was connecting to a WPA-TKIP encrypted network with Network Manager and the rt2500pci module (the Gutsy's default module), but the connection was unstable and a bit slow, and every now and then I just got disconnected from my network. So, navigating through ubuntuforums.org I found this thread which was helpful but I didn't followed strictly; what I did was to followed some parts from this howto (thank you, zoiks) and [this one]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Debian_rt2500_Howto"). I'll explain what I did (maybe this could enrich this thread):

1) Install the rt2500 driver source from the repositories (you obviously need a working network to do this):

```
sudo apt-get install rt2500-source
```

(The above command will install the beta rt2500 driver)

2) Make sure you have the kernel headers installed (I think they come installed by default on Gutsy, but it's better to make sure it's installed):

```
dpkg -l linux-headers-`uname -r`
```

You should see an output like this one:

```
 dpkg -l linux-headers-`uname -r`
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Nombre         Versión       Descripción
+++-==============-==============-============================================
ii  linux-headers- 2.6.22-14.46   Linux kernel headers for version 2.6.22 on x
```

If it's not installed, then proceed to install it as explained by zoiks:

```
sudo apt-get install linux-headers-`uname -r`
```

3) Stop any running services you have working (so, if you connected through NM or other application, stop it).

4) Remove the rt2500pci module from the running kernel:

```
modprobe -r rt2500pci
```

5) Blacklist the rt2500pci module as explained by zoiks; actually, I had a "permission denied" error when running the command, even with sudo. so what I did was the following:

```
sudo -s
echo "blacklist rt2500pci" >> /etc/modprobe.d/blacklist
```

6) Uninstall NM as explained by zoiks:

```
sudo apt-get remove network-manager-gnome
```

7) Now that the wrong module is blacklisted and removed from the running kernel, we can compile the rt2500-source driver we installed before, on step 1.

```
sudo m-a a-i rt2500-source
```

If everything goes fine, you should see a blue screen in your terminal with a progress bar indicating the compilation and building of the module; then it will also auto install itself automatically.

8 ) Add the rt2500 module to the running kernel:

```
sudo modprobe rt2500
```

The module should already be in the kernel next time you boot; if it's not, add it to your /etc/modules file:

```
sudo -s
echo rt2500 >> /etc/modules
```
(taken from the guide I link at the beginning of this post).

9) Edit your /etc/network/interfaces file according to your requirements. This may vary depending on which type of encryption you're using. For a detailed guide on how to edit the /etc/network/interfaces file I'd suggest reading [this]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500"). NOTE: If you installed the rt2500-source driver as I suggested above, it won't be named ra0 but wlan0, so, in case you follow this guide you must change all the references for ra0 in your interfaces file to wlan0.

10) After you've edited and saved your /etc/network/interfaces file, proceed to stop the network and start it again:

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

That's it, if everything went fine, you should have a working network now (and on every boot).

Yes, I know these are a bunch of steps, but It's not that hard as it seems :)

Thanks to zoiks for the guide and I hope my addendum can be of help for anyone.

Regards.

---

### Post by kevdog on 2007-10-21
Some of those two step sudo commands can be combined in one statement for example

echo rt2500 | sudo tee -a /etc/modules

---

### Post by theharshone on 2007-10-21
Will this also work for the rt2570 driver?

---

### Post by kevdog on 2007-10-21
Probably -- but you would have to be the first to check.

Im not certain why the built in driver doesnt work since it is the serial monkey driver (although an older version if you are compiling the cvs version of the serial monkey drivers).  Hopefully someone will be able to elucidate the reason why the inconsistencies.

Basically the solution now has defaulted to the old Feisty solution, where you downloaded the cvs sources, compiled them, set up appropriate blacklist statement, unloaded modules you didnt want to use, and then loaded the new modules, used a command line to test the connection, and then made these command line statements permanent by adding them to the /etc/network/interfaces file.  I know this process worked on Feisty numerous times, and Im already seeing this happen with two people with the rt2500 driver in Gutsy.  I have no reason to suspect any different with the rt2570 driver.

---

### Post by zoiks on 2007-10-22
> **kevdog said:**
> Probably -- but you would have to be the first to check.

Im not certain why the built in driver doesnt work since it is the serial monkey driver (although an older version if you are compiling the cvs version of the serial monkey drivers).  Hopefully someone will be able to elucidate the reason why the inconsistencies.

Basically the solution now has defaulted to the old Feisty solution, where you downloaded the cvs sources, compiled them, set up appropriate blacklist statement, unloaded modules you didnt want to use, and then loaded the new modules, used a command line to test the connection, and then made these command line statements permanent by adding them to the /etc/network/interfaces file.  I know this process worked on Feisty numerous times, and Im already seeing this happen with two people with the rt2500 driver in Gutsy.  I have no reason to suspect any different with the rt2570 driver.

The failure to get the network going with the gutsy-supplied module, in the case of rt2500pci, has something to do with the module not accepting "set" as a private ioctl command. From what I understand, the driver is supposed to allow the "set" commands so that encryption mode and pre-shared key can me set, but in gutsy's case the "set" command returns an error. You'll notice in the /etc/network/interfaces file, you'll see some "iwpriv wlan0 set ..." lines. These lines are rejected by the gutsy driver, but if you recompile and install rt2500 from scratch, they are accepted.

Deeper than that, I don't know.

---

### Post by Tobis84 on 2007-10-22
Will this work with a USB-type of rt2500-based card?

I can see the reference to af PCI-driver...

---

### Post by MariusSilverwolf on 2007-10-22
> **Tobis84 said:**
> Will this work with a USB-type of rt2500-based card?

I can see the reference to af PCI-driver...

Read my war story here: [http://ubuntuforums.org/showthread.php?t=586017](http://ubuntuforums.org/showthread.php?t=586017)

---

### Post by rustybronco on 2007-10-22
> **theharshone said:**
> Will this also work for the rt2570 driver?

> **kevdog said:**
> Probably -- but you would have to be the first to check.

and Im already seeing this happen with two people with the rt2500 driver in Gutsy.  I have no reason to suspect any different with the rt2570 driver.I will reinstall gutsy tonight, give it a go and then post the results if no one else does it in the mean time.

---

### Post by Zenguy on 2007-10-22
Thank you...thank you...thank you!

After playing (unsuccessfully) with NDISWrapper and struggling with parts of the SerialMonkey puzzle, I finally have working RT2500 wireless in Gutsy.

Following your post worked for me.

---

### Post by bigboy_pdb on 2007-10-23
For those of you who don't want to use ndiswrapper (and you'd prefer to use the modules that came with Gutsy) you might want to try the solution that worked for me. It can be found here:
[http://ubuntuforums.org/showthread.php?t=587727](http://ubuntuforums.org/showthread.php?t=587727)

---

### Post by LordYama on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Using the default rt2500pci driver, I found that my Belkin RT2500-based PCI card would not see or connect to any wireless points unless I pulled out my wired Ethernet card (leaving the **wireless as the only network interface**). After this, NetworkManager would be able to see and connect to networks, but I could not successfully configure a wireless network manually. The solution is to configure /etc/network/interfaces with the following:

```
auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 down
        wpa-driver wext
        wpa-key-mgmt WPA-PSK
        wpa-proto WPA
        wpa-ssid *<ssid>*
        wpa-psk *<passphrase>*
        pre-up sleep 20
        pre-up ifconfig wlan0 up
```

Note that the **passphrase is stored in clear text**, which is a potential security problem. Also, moving between a NetworkManager-managed connection to a manually-defined one requires a reboot.

---

### Post by bigboy_pdb on 2007-10-23
You can use the command "sudo chmod 600 /etc/network/interfaces" to change the permissions of interfaces so that only root can read/write from/to the file. This will correct your security problem. Also, if you're using gedit to edit the file, run "sudo rm /etc/network/interfaces~" to get rid of the temporary file (which will still be readable by the group & others).

---

### Post by kevdog on 2007-10-23
Unless you have the wired and wireless on a different subnet, most likely they will not work at the same time.  Rather than pulling out your Ethernet card however, you can always bring the interface down like this

sudo ifconfig eth0 down

In fact, you could probably do something like this (untested):

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig eth0 down
        pre-up ifconfig wlan0 down
        wpa-driver wext
        wpa-key-mgmt WPA-PSK
        wpa-proto WPA
        wpa-ssid <ssid>
        wpa-psk <passphrase>
        pre-up sleep 20
        pre-up ifconfig wlan0 up

---

### Post by godoy on 2007-10-24
Works fine to me!!
Thx

---

### Post by starlily on 2007-10-24
I had my rt2500 working fine in Feisty with ndiswrapper, and it broke when I upgraded to Gutsy. I could see APs but not connect at all. I tried a lot of things, but the fix finally was this: I have both "rt2500" AND "rt2500pci" in /etc/modprobe.d/blacklist, everything else is exactly as it was before. 

I hope this helps someone else.

---

### Post by zoiks on 2007-10-25
> **LordYama said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Using the default rt2500pci driver, I found that my Belkin RT2500-based PCI card would not see or connect to any wireless points unless I pulled out my wired Ethernet card (leaving the **wireless as the only network interface**). After this, NetworkManager would be able to see and connect to networks, but I could not successfully configure a wireless network manually. The solution is to configure /etc/network/interfaces with the following:

```
auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 down
        wpa-driver wext
        wpa-key-mgmt WPA-PSK
        wpa-proto WPA
        wpa-ssid *<ssid>*
        wpa-psk *<passphrase>*
        pre-up sleep 20
        pre-up ifconfig wlan0 up
```

Note that the **passphrase is stored in clear text**, which is a potential security problem. Also, moving between a NetworkManager-managed connection to a manually-defined one requires a reboot.

FWIW, I've tried this solution and it didn't work for me. I have no ethernet cable plugged in, but being a laptop, it's not simple for me to just yank the ethernet card (eh, but I figured I'd try anyway. :) ). The wireless card, of course, is a removable cardbus card.

Basically when I attempt this method (after reverting to rt2500pci), it first complains if there's any mention of eth0 in /etc/network/interfaces, due to there being "no such device".

So then I tried commenting out all the lines for eth0. At least it attempts to do the right thing when I ifup, but it sends a couple of ioctl error messages and then proceeds to fruitlessly try to establish a DHCP connection. (My router provides DHCP.)

Long story short, it didn't work for me, but perhaps that's because I can't just physically remove the ethernet card.

---

### Post by Boef666 on 2007-10-25
First of all, thank you for putting all that effort into a how-to file.

Unfortunatly it did not give the results I would have liked.
The driver I tried to compile did not do so correctly, then blacklisting the driver that did work made me end up without a working wireless card.
Is there any way to remedy this?
As in taking the driver off the blacklist?

The driver installed by Ubuntu does give me a working wireless network card but does not support packet injection. For using Kismet I will need this to work.

Any help on the subject would be more then welcomed. :)

---

### Post by rustybronco on 2007-10-25
> **LordYama said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027) 

>  Tim Gardner wrote on 2007-10-24: (permalink) 
Can you guys try this for me:

wget [http://people.ubuntu.com/~rtg/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40UNRELEASED_i386.deb](http://people.ubuntu.com/~rtg/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40UNRELEASED_i386.deb)
sudo dpkg -i linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.40UNRELEASED_i386.deb
sudo reboot 
something i'm going to try tonight....

---

### Post by Boef666 on 2007-10-25
This did set my sound the right way?

Unfortunetly I can't make any other reports, wireless card is still down.

---

### Post by Kevf on 2007-10-26
'shut down all the services' 

Can someone tell me the exact way of how to do that? I don't want to mess this up again ;)

edit: I do have a laptop that is on the internet. Can I download a certain file on a usb-stick and transfer it to ubuntu? If so: What exact steps do I have to follow?

---

### Post by zoiks on 2007-10-26
> **Boef666 said:**
> First of all, thank you for putting all that effort into a how-to file.

Unfortunatly it did not give the results I would have liked.
The driver I tried to compile did not do so correctly, then blacklisting the driver that did work made me end up without a working wireless card.
Is there any way to remedy this?
As in taking the driver off the blacklist?

The driver installed by Ubuntu does give me a working wireless network card but does not support packet injection. For using Kismet I will need this to work.

Any help on the subject would be more then welcomed. :)

It's quite likely the failure of your driver compilation is to blame. Once you've downloaded the rt2500 source file, untar'ed it, and gone into the Module subdirectory, what text output do you see in the terminal when you type

```
make
```

and then

```
sudo make install
```

?

Taking rt2500pci off the blacklist will once again allow the rt2500pci module to load, and should restore your status to where you were before.

---

### Post by zoiks on 2007-10-26
> **theharshone said:**
> Will this also work for the rt2570 driver?

I don't know, but if you gave it a try and reported back I think it would be useful information.

---

### Post by bd@cb8be8510 on 2007-10-26
I downloaded the new driver from serialmonkey.com (See [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)), compiled and installed the driver and finally after a week my wireless-network was working in Gutsy!

---

### Post by fearevilleet on 2007-10-29
Hi,

I am unable to install the driver. When doing a make I get the error below. Any help is appericated. 


```

root@box:/home/rian/rt2500-1.1.0-b4/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rian/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/home/rian/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c: In function âRT2500_openâ:
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:66)
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ârt2500_init_moduleâ:
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:1009: warning: implicit declaration of function âpci_module_initâ
make[2]: *** [/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/rian/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

```

---

### Post by kevdog on 2007-10-29
fearevilleet

What drivers do you want to compile -- where did you get them?

---

### Post by fearevilleet on 2007-10-29
I am trying to compile drivers for the rt2500, I got them directly off of the serial monkey page.

---

### Post by odiseo77 on 2007-10-29
@fearevilleet: You're using the beta rt2500 driver, right (1.1.0-b4)? Use the [cvs hourly tarball]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz") instead :)

---

### Post by fearevilleet on 2007-10-29
It still errors out when using the hourly.

```

root@box:/home/rian/rt2500-cvs-2007102918/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_main.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/mlme.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/connect.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/sync.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/assoc.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/auth.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/auth_rsp.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_data.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_init.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/sanity.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_wep.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/wpa.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/md5.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_tkip.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_info.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rt2x00debug.o
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/eeprom.o
  LD [M]  /home/rian/rt2500-cvs-2007102918/Module/rt2500.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/rian/rt2500-cvs-2007102918/Module/rt2500.mod.o
  LD [M]  /home/rian/rt2500-cvs-2007102918/Module/rt2500.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
root@box:/home/rian/rt2500-cvs-2007102918/Module# make install
2.6 module install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/rian/rt2500-cvs-2007102918/Module  modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/rian/rt2500-cvs-2007102918/Module/rt2500.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a

```

---

### Post by odiseo77 on 2007-10-29
I don't find any error there; seems pretty clean to me. What do ***lsmod*** and ***iwconfig*** output?

---

### Post by fearevilleet on 2007-10-29
```

root@box:/home/rian/rt2500-cvs-2007102918/Module# lsmod
Module                  Size  Used by
binfmt_misc            12936  1
rfcomm                 42136  2
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nfsd                  220912  13
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0
speedstep_lib           6404  0
cpufreq_userspace       5280  0
cpufreq_stats           7232  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9612  0
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0
video                  18060  0
sbs                    19592  0
button                  8976  0
dock                   10656  0
container               5504  0
ac                      6148  0
battery                11012  0
af_packet              24840  2
sbp2                   24072  0
lp                     12580  0
snd_intel8x0           35484  0
arc4                    2944  2
ecb                     4608  2
blkcipher               7556  1 ecb
snd_seq_dummy           4996  0
rc80211_simple          6912  1
snd_seq_oss            35328  0
snd_mpu401             10152  0
snd_mpu401_uart         9984  1 snd_mpu401
snd_ca0106             36640  0
snd_seq_midi            9728  0
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
snd_ac97_codec        101924  2 snd_intel8x0,snd_ca0106
nvidia               4716468  22
snd_rawmidi            26112  3 snd_mpu401_uart,snd_ca0106,snd_seq_midi
snd_pcm_oss            43008  0
snd_mixer_oss          17920  1 snd_pcm_oss
parport_pc             37412  1
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2500pci              19072  0
rt2x00pci              11520  1 rt2500pci
rt2x00lib              19584  2 rt2500pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rc80211_simple,rt2500pci,rt2x00pci,rt2x00lib
cfg80211                7304  1 mac80211
snd_pcm                80644  4 snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm_oss
parport                37448  3 ppdev,lp,parport_pc
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
eeprom_93cx6            3200  1 rt2500pci
snd_timer              24580  2 snd_seq,snd_pcm
ac97_bus                3456  1 snd_ac97_codec
analog                 13344  0
i2c_core               26112  1 nvidia
pcspkr                  4224  0
gameport               16776  1 analog
iTCO_wdt               11940  0
intel_agp              25620  1
snd                    56708  14 snd_intel8x0,snd_seq_dummy,snd_seq_oss,snd_mpu401,snd_mpu401_uart,snd_ca0106,snd_ac97_codec,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore               8800  1 snd
snd_page_alloc         11656  3 snd_intel8x0,snd_ca0106,snd_pcm
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0
pci_hotplug            32704  1 shpchp
agpgart                35016  2 nvidia,intel_agp
joydev                 11328  0
evdev                  11136  5
ext3                  133896  2
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0
sd_mod                 30336  5
sr_mod                 17828  0
cdrom                  37536  1 sr_mod
ata_piix               17540  5
usbhid                 29536  0
hid                    28928  1 usbhid
usb_storage            73024  0
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ata_generic             8452  0
floppy                 60004  0
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,sg,sd_mod,sr_mod,usb_storage,libata
dmfe                   23196  0
ohci1394               36528  0
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0
ohci_hcd               22916  0
uhci_hcd               26640  0
usbcore               138632  7 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd,uhci_hcd
thermal                14344  0
processor              32072  1 thermal
fan                     5764  0
fuse                   47124  1
apparmor               40728  0
commoncap               8320  1 apparmor

```


```

ra0       IEEE 802.11g  ESSID:"thebox"
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1A:70:52:89:00
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Signal level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by odiseo77 on 2007-10-29
The driver seems to be installed, however, you haven't blacklisted the rt2500pci module (see the beginning of this thread on how to do this). After you've blacklisted the rt2500pci module, you can remove the rt2500pci module from the running kernel and insert the rt2500 module with:

```
sudo modprobe -r rt2500pci
sudo modprobe rt2500
```

Then proceed to configure your network as explained by zoiks at the beginning of this thread.

Best of luck! :)

---

### Post by zoiks on 2007-10-30
Edit: OOPS sorry, it seems this question had been successfully addressed above. Sorry.


> **fearevilleet said:**
> Hi,

I am unable to install the driver. When doing a make I get the error below. Any help is appericated. 


```

root@box:/home/rian/rt2500-1.1.0-b4/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rian/rt2500-1.1.0-b4/Module/rtmp_main.o
In file included from /home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:50:
/home/rian/rt2500-1.1.0-b4/Module/rt_config.h:58:40: error: linux/config.h: No such file or directory
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c: In function âRT2500_openâ:
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: âdeprecated_irq_flagâ is deprecated (declared at include/linux/interrupt.h:66)
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:343: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c: In function ârt2500_init_moduleâ:
/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.c:1009: warning: implicit declaration of function âpci_module_initâ
make[2]: *** [/home/rian/rt2500-1.1.0-b4/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/rian/rt2500-1.1.0-b4/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2500.ko failed to build!
make: *** [module] Error 1

```

Hi fearevilleet.

From what I can tell you may be using an older slightly incompatible version of the code. Your version has an include for linux/config.h in the file rt_config.h in the source. One of two things should fix it. 1) Download a newer version (like the current CVS) from serialmonkey. or 2) In the file **Module/rt_config.h**, remove the line that looks like

```
#include <linux/config.h>  //can delete
```

#1 would be more reliable, but #2 may be a quicker fix.

---

### Post by zoiks on 2007-10-30
> **fearevilleet said:**
> It still errors out when using the hourly.

```

root@box:/home/rian/rt2500-cvs-2007102918/Module# make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/rian/rt2500-cvs-2007102918/Module/rtmp_main.o

[...]
[...]

/sbin/depmod -a

```

BTW, that's what the output is supposed to look like - there are no errors here.

---

### Post by cmirandamora on 2007-11-02
Hi! First of all, sorry for my bad english. I´m new in Ubuntu and I was about leaving it because of my problems with the wireless (it worked fine with XP and another distros out of the box but I couldn´t with Gutsy)

I tried all the ways of this post but it didn´t work.

Finally I did it work just changing the output channel of the router: it was set on 13 and I changed it to 1 and suddenly everything worked :guitar:.

I´ve been doing tests and it didn´t worked in channel 9; in channel 6 the speed was very slow (I have 3 Mb ADSL and my downloads hardly were 32 kbs).

With channel 1 the download speed doesn´t reach more than 150 kbs; with the other distro and in XP, and in channel 13, I could get 350 kbs. 

¿Is there any way I can change the Channel reception in the card or the driver?

¿Can anybody try this solution to see if it works for them?

---

### Post by odiseo77 on 2007-11-03
> **cmirandamora said:**
> ¿Is there any way I can change the Channel reception in the card or the driver?

¿Can anybody try this solution to see if it works for them?

You should be able to change the reception channel by editing your /etc/network/interfaces file. Look for your wireless device section, then look for the first iwpriv line and copy the following before it:

```
pre-up iwpriv wlan0 set Channel=13
```

(I guess channel 13 is the one you want to use?)

That should do it; just make sure the channel you set here, matches your router's channel.

Regards.

---

### Post by markymarknz on 2007-11-16
Works great.
Thanks for the howto saved me a lot of time :)

---

### Post by eric0919 on 2007-11-18
I ams till have problems with my rt2500 wireless.  I'm connecting using wep encryption because that's what my 2wire modem/router is set for.  It looks like this how-to is expecting you to use wap.  Is this correct?  How do I change it?

Thanks Eric

---

### Post by tenner on 2007-11-18
Great HOWTO... I was having trouble getting WPA going with my RT2500 card and this got me going straightaway.

But I have a question -- I've seen this on other commenters' suggestions too.  Why is there the need to do this:

<code>
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
</code>

before anything else?

Now that my network is working, I want to understand the process more fully.  Thanks!

---

### Post by Pollywoggy on 2007-11-19
After upgrading to Gutsy (actually a clean install not an upgrade) I was unable to use the same /etc/network/interfaces and wpa_supplicant.conf to connect.

I blacklisted the Ubuntu-supplied rt2500pci driver and installed the CVS version from Serialmonkey and I changed my /etc/network/interfaces to look like the one in the howto, but still no banana.  I then installed rutilt and that alone made the difference.  I would not be able to connect on the command line but I am connecting in a KDE session.  BTW I had not changed my router setup since Feisty and I am using a Linksys WRT54GS with DD-WRT installed.  My FlipStart PC is also able to connect to the router using WPA.

So Rutilt is the ticket.  Thanks for the suggestion.

---

### Post by Sonic Reducer on 2007-12-16
> **zoiks said:**
> ```

auto wlan0
iface wlan0 inet dhcp[INDENT]pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "myssid"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="mypskkeystring"
pre-up ifconfig wlan0 up
[/INDENT]
```

so would i do this for WEP? my ESSID is Jones Wi-Fi and i am using WEP (easier to set up the Wii and 360 for)

```

auto wlan0
iface wlan0 inet dhcp[INDENT]pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "[COLOR="Lime"]Jones Wi-Fi[/COLOR]"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=[COLOR="Lime"]WEP[/COLOR]
pre-up iwpriv wlan0 set WPAPSK="[COLOR="Lime"]my wep key[/COLOR]"
pre-up ifconfig wlan0 up
[/INDENT]
```

---

### Post by Pollywoggy on 2007-12-16
When I was using WEP, I just used one of the graphical utilities and it worked.
Rutilt is one and raconfig was the other.  I believe some of the other graphical utilities for KDE will also work with WEP.

---

### Post by Sonic Reducer on 2007-12-16
> **Pollywoggy said:**
> When I was using WEP, I just used one of the graphical utilities and it worked.
Rutilt is one and raconfig was the other.  I believe some of the other graphical utilities for KDE will also work with WEP.

so how did you get the serial monkey drivers working?

---

### Post by kevdog on 2007-12-16
```

pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down

```

This has been found simply by trial and error.  This is a long documented solution that spans many generations of ubuntu versions.

WEP is different than WPA 
For the appropriate command line syntax use my guide about connecting from the command line.

---

### Post by Pollywoggy on 2007-12-16
> **Sonic Reducer said:**
> so how did you get the serial monkey drivers working?


I followed a tutorial that I believe I found on Ubuntuforums but this was with Feisty.  I am not certain whether the same instructions are valid for Gutsy.

I am using WPA now (in Gutsy) and I can't use any of the graphical tools successfully, only command-line activation works.

The Ralink rt2500 also worked under Linspire 5.0 and Freespire 1.0 but not Linspire 2 or Freespire 6.0.  I don't know if this has something to do with the fact that their distributions are now based on Ubuntu rather than Debian.

---

### Post by kevdog on 2007-12-16
Ok -- at least the command line works!!

What gui are you trying to use.  Network Manager and ra based cards dont often get along.  Other guis that might work would be wicd and rutilt.  I would have a go at these.

---

### Post by Wazeem on 2007-12-16
> **Pollywoggy said:**
> I followed a tutorial that I believe I found on Ubuntuforums but this was with Feisty.  I am not certain whether the same instructions are valid for Gutsy.

I am using WPA now (in Gutsy) and I can't use any of the graphical tools successfully, only command-line activation works.

The Ralink rt2500 also worked under Linspire 5.0 and Freespire 1.0 but not Linspire 2 or Freespire 6.0.  I don't know if this has something to do with the fact that their distributions are now based on Ubuntu rather than Debian.

Hi, I have a rt2500usb based adapter and had loads of problems with my ubuntu 7.10. Although your problems may differ here is what i did to get mine to work...

first install ndiswrapper and the relevant windows driver.

if you done that, in the command line type "lsmod" and see if the module (driver) for your wireless is listed. What you should be looking out for is ndiswrapper (it wont say the driver name). If it says some other drivers name then that could be your problem. I had the rt73usb driver load automatically and that was the issue.

to check if thats the problem type "sudo modprobe -r <the driver name as you see it on the list>" and then type "sudo modprove ndiswrapper". See if that sorts it.

If that does search on google how to "blacklist drivers" and just follow one of the tutorials and blacklist the offending driver.

Hope it works for you.

---

### Post by thrice_loved on 2007-12-17
:D 
I only completed numbers 4 and 5 in Zoiks' original post (I didn't change the driver or uninstall network manager or anything) - just added the lines to the interfaces file and restarted the network and now my WPA is working beautifully.

Mine is a "RT2500 802.11g Cardbus/mini-PCI" (from hardware information)
The computer had been refusing to connect (no encryption, wep and mac addresses had been ok, but when I tried WPA it would ask for a password, sit for about a minute, not connect and then ask me for the password again). 
But now it's lovely (quick and solid) thanks Zoiks :)

Edit:  * was wrong - It worked for about nearly a week until we turned the external harddrive on and my wireless stopped working. I think it may have been becasue the router changed the ip addresses - not sure, anyway I started over and followed ALL of zoiks' instructions and it's solid again (been about a fortnight now :) ). *

---

### Post by kevdog on 2007-12-17
Double post

---

### Post by dtfinch on 2007-12-22
I get an instant hard freeze with the latest serialmonkey driver when I try to enable the wireless connection in network manager.

---

### Post by kevdog on 2007-12-22
There is a known conflict between network manager and the ra drivers.  Although it works for some people, others have suggested uninstalling network manager, and use either the command line or /etc/interfaces file, wicd, or rutilt.

---

### Post by dtfinch on 2007-12-23
After days of troubleshooting, moving the wireless card from the first pci slot to the second pci slot seems to have fixed the problem. So odd. It was working in the first slot under Breezy.

---

### Post by johnnyhop on 2007-12-23
zoiks,

In response to your post on 10/21 I tried to update the rt2500pci driver to rt2500 and with the attempt all was proceeding well with the install with only what I perceived to be a minor glitch with step 1) Install build and header requirements.  The command:  sudo apt-get install build-essential linux-headers-`uname -r` where uname was replaced with john (my user name) and 'xx' apostrophes were of course omitted, returned the message "-r unrecognized option"  I omitted the -r and tried the command again.  Apt went through the usual procedures then returned a message "linux headers are up to date."  The rest of the steps appeared to go well but when all was done and after reboot 'lshw' reported the device logical name to continue to be ra0 while 'lsmod' showed one reference in the left column "ra2500" but there was nothing in the column to the right of the bit size column.  There was no showing of "ra2500pci."  It was also noted that /etc/modprobe.d/blacklist added "blacklist rt2500pci" to the file and about the time I initiated the "sudo make install" command the file /etc/modprobe.d/ralink was either created or modified.  It contained only the line "alias ra0 rt2500."  Naturally there was no wireless connection to the access point at this time.  To put all back to the previous state  I simply removed "pci" from the line "blacklist ra2500pci" and rebooted.  

My primary goal was to establish a connection to the wireless access point without having to re-enter WPA-PSK after each boot up and to re-establish the connection should it momentarily drop out without having to reboot (sometimes in only 15 or so minutes) and re-enter the WPA-PSK.  Satisfactory results were obtained by removing Network-Manager and installing Wicd.

---

### Post by j_Doe on 2007-12-23
Thanks for the original post.  It worked with the removal of network manager.

---

### Post by jocheem67 on 2007-12-29
Hi all,

I can confirm a succesful installation using this howto of the rt61 serialmonkey driver ( the cvs-one )..
Just had to change rt2500 into rt61, and do a " sudo strip rt61.ko"  after the make-command....

My trouble with the embedded rt61 pci was speed-dropping, especially gutsy updates affected by that.

I removed network-manager, and installed rutilt. There I' ve been able to configure my wireless..

Thanks for your howto!!!!

By the way: I did remove the repeating " ifconfig wlan0 up and down"  lines from your example /etc/network/interfaces...I only use "  ifconfig wlan0 up"  
Don' t see a reason for bringing the connection down and up again ( ? )

---

### Post by kevdog on 2007-12-29
The multiple up/down statements are needed for some people.  I dont know why they are needed exactly, and Ive never seen an explanation explaining the problem, I think these methods were found by trial and error.  Im glad to see you are at least experimenting rather than taking the instructions as gospel.  Good job.

---

### Post by jocheem67 on 2007-12-29
It's funny, using the rutilt utility I could actually see my connection going down and up again several times..
After deleting the multiple up and down stuff, there is a steady connection right after booting. No speeddropping, no instability...

Great stuff:)

---

### Post by johnnyhop on 2008-01-08
Zoiks,

I apologize for hastily claiming your instructions for installing the rt2500 driver didn't work.  I mentioned returning to rt2500pci and using Wicd which provided connectivity at boot up. This worked well for a few days, but still not as good as in WinXP.  There's a readme file within rt2500-cvs-2007.../module which mentions the need to configure the /etc/Wireless/RT2500STA/RT2500STA.dat file.  Once that was done I was up and running with the rt2500 driver.

---

### Post by lode303 on 2008-01-09
Thanks a lot. Everything in the original post worked beautifully. 

I got the Asus WL 107g and was really excited to use it with Ubuntu. Alas, the connection was spotty and had poor transfer rates while I sat next to the router itself. Everything is running smoothly and I like the reutilt manager better than the default network manager too!

One question, should I apt-get remove network-manager in addition to network-manager-gnome? It doesn't seem to be causing a problem so far but who knows.

---

### Post by icheyne on 2008-01-10
:)> **Boef666 said:**
> The driver installed by Ubuntu does give me a working wireless network card but does not support packet injection. For using Kismet I will need this to work.

[http://ubuntuforums.org/showthread.php?t=662994](http://ubuntuforums.org/showthread.php?t=662994)

---

### Post by rlgoddard on 2008-01-27
I just want to say that although the supplied rt2500pci driver worked for me in Xubuntu Gutsy, switching to the rt2x00 serialmonkey driver using the directions at the top speeded up my internet connection considerably.  I used to get 90kbp-100kbps.  I now get between 480kbps-500kbps.  I also was able to upgrade from WEP to WPA as well.  Thanks a lot for your help!

Take care,
Russ

---

### Post by cap601 on 2008-02-02
I've tried these instructions but I cannot make them work.  After following them KNetworkmanager (I'm on Kubuntu Gutsy) either doesn't accept my card exists or says that no access points exist (depends on various fiddles I've made).  After a reboot I also could not revert to the default drivers (which did work but at a reduced speed).  I've since reinstalled but would like help on sorting out this problem.

---

### Post by dwijiguru on 2008-03-05
Thanx for the detailed steps, Zoiks. It worked almost all the way - I could see the wireless connection established through the rutilt interface. But when I pulled the network cable and downed eth0, wlan0 was not picking the line. A reboot did not change this either. Not sure why ...

> **odiseo77 said:**
> 
10) After you've edited and saved your /etc/network/interfaces file, proceed to stop the network and start it again:

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
```

Doing the networking restart had it working just right. Thanx Odiseo !

I will try out something that one of the others has suggested, disabling both rt2500 and the 2500pci modules and blacklisting them.

btw, this was on an Averatec 3250HX.

regards
guru

---

### Post by williecdog on 2008-03-13
Whatever you do, don't have a space in a directory that is higher in the hierarchy than you are in when you try to compile the source.

For instance, this didn't work:

```
williecdog@EveningJava:~/RT2500 Wireless Driver with WPA/rt2500-cvs-2008031316/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** No rule to make target `Wireless'.  Stop.

```

But this did:

```
williecdog@EveningJava:~/rt2500/rt2500-cvs-2008031316/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
CC [M]  /home/williecdog/rt2500/rt2500-cvs-2008031316/Module/rtmp_main.o
.
.
. 
 
```

---

### Post by russbuss on 2008-03-15
Just wanted to thank Zoiks for this how-to.  I had been having a terrible time with the rt2500pci driver.  While I could connect to my network, it would slow down to a crawl for no apparent reason.... Seriously, 200 Bytes/sec??!!!

Anyhow, I followed the instructions on the first page and they worked almost perfectly.  I never got any error messages of any kind.  The only thing I had to do slightly differently to actually get my wireless connection working was to uninstall the network-manager and install RutilT.  With network-manager still installed, just issuing: ```
sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo modprobe rt2500
sudo ifconfig wlan0 up
```
never got my connection to work.

However, once I had uninstalled network-manager, installed RutilT, and I configured the network connection in RutilT, I was able to connect immediately.  This includes the added bonus of RutilT being far superior to network-manager.

I wish I understood why the rt2500pci driver is so crappy, but I suppose all that matters is that this workaround, well, works.

Thanks again.

---

### Post by disk11 on 2008-03-31
Blacklisting rt2500pci makes my system lock up at the login screen, and rt2500 doesn't show up in lsmod.  Any suggestions?

---

