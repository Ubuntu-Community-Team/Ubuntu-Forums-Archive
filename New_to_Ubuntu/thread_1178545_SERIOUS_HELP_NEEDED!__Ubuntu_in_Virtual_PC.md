---
title: "SERIOUS HELP NEEDED!  Ubuntu in Virtual PC"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by ericsavage on 2009-06-04
I have been using Ubuntu for about the past year off and on.  I am in a Networking class in college and we are to download a version of Linux and work with it during our tasks.  We are to download the version, in my case I picked Ubuntu, into Virtual PC and perform our tasks there.  I start up my Virtual PC, wait for it to ask for the boot disk, place my Ubuntu disc in the drive, and then hit enter.  I get the start up screen where it says Ubuntu.  Then it goes to the language screen with the log in ways just behind it.  I have let it just count down and when it does, Ubuntu prints out a list, like you would see on a command screen, and just stops, nothing else.  I have also clicked on escape, and clicked Install Ubuntu, Install Ubuntu with no change to your computer, and the other install one (can't remember what it is), and I get the same thing that I got before with the list. If anyone out there knows how I can install this disk and use it like I were using the real Operating System, I would gladly appreciate some help on this.  My professor says that I can use it just as a live disk, but where are things in Ubuntu like Installation Packages, User Authentication Method, and System Terminal Konsole?  As you can see, I need a lot of help, and this is the last place that I have turned to.  Please, help!  Thanks so much for reading and for any help that I receive.

---

### Post by marshall.robert on 2009-06-04
Basically, in a nutshell, Virtual PC is terrible. It is only good for running Microsoft operating systems. Look in to VMWare; they are vastly superior in the virtual pc market. VMWare Workstation is probably the one you want to go for, but there are other options such as VMWare Player but you cant make virtual machines with Player. If you can find an older version of VMWare Server (1.x) then you can use that for free and it is very similar to Workstation, although it does require a serial which is free to get but requires registration.

I personally use VMWare Workstation, which gives me very good results, but you have to pay for it. VMWare Server 2 I found hard to manage and work on a local machine, which is why i suggested hunting down a 1.x version.

Hope this helps a bit.

EDIT: [Click Here for the WMWare Server page.]("http://www.vmware.com/download/server/") [Click Here for VMWare server 1.0.9.]("http://register.vmware.com/content/eula-109.html")

---

### Post by s.fox on 2009-06-04
Hi and welcome to the forums,

As an alternative you could try using [VirtualBox]("https://help.ubuntu.com/community/VirtualBox")

Hope this helps.

-Ash R

---

### Post by learningcurb on 2009-06-04
Give the free VMware Player version a try.  It's a very polished product and works out of the box with minimal setup.  You have two options with VMware Player:

1. Get a VMX file from [http://easyvmx.com/supersimple.shtml](http://easyvmx.com/supersimple.shtml) Switch the OS choice to Ubuntu Linux (not 64 bit), and perhaps increase the memory somewhat if your system can support it, depending on which apps you are running.  If you only run off a LiveCD, you can choose not to have a virtual hardrive.  The LiveCD/ISO image choice doesn't really matter -- on Ubuntu you can manually setup the CD drive from inside VMware.  I'm not sure how this works on Windows however.

Then you just download the file, uncompress it and open the .vmx file with VMware player.  Specify the Ubuntu LiveCD or an iso image of it from inside VMware player and it should be smooth sailing from there.  If you choose to install Ubuntu to the virtual machine though, it will take a while.

2. Or you can download a virtual machine someone else has built already.  Vmware has huge directory of third-party created VMs here: [http://www.vmware.com/appliances/](http://www.vmware.com/appliances/)  

There's a website called VMplanet which has a Ubuntu 9.04 desktop VMware image here: [http://www.vmplanet.net/node/95](http://www.vmplanet.net/node/95)  Of course there is some security risk when downloading a third party created VM image because anything could be on it, but VMPlanet seems to be one of the bigger and more reputable sites for this.  The advantage of downloading a third party VM is that your changes will be persistant and you won't need to spend an hour or so installing the VM to disk.

---

### Post by achase79 on 2009-06-04
I found this url for setting up ubuntu in Virtual PC [http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/]("http://arcanecode.com/2008/04/24/installing-ubuntu-804-under-microsoft-virtual-pc-2007/")

---

### Post by vinutux on 2009-06-04
virtualpc windoes oriented

vmware not free

virtualbox is best ---------free, multiplatform, opensource

---

### Post by vinutux on 2009-06-04
virtualpc windows oriented

vmware not free

virtualbox is best ---------free, multiplatform, opensource

---

### Post by Johan-Steyn on 2009-06-04
Hi ericsavage,

Virtualbox is definitely the way to go. 

However, virtualbox ose (as packaged in the repository) does not have usb support.

So install the deb package for the latest (non-ose) but still free virtualbox 2.2.4.

Here is the link: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Really awesome app!

Regards, 

JS

---

