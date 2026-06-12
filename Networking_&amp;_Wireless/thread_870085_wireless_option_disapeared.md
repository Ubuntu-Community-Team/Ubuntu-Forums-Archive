---
title: "wireless option disapeared"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by Jonomac on 2008-07-25
Hi, I bought basically a new computer. The things I used again were the hard drive dvd drive.  I had Ubuntu 8.04 (all new updates as of July 23rd) installed on the hard drive. When I rebooted after connecting everything into the new computer, the option for wireless internet was gone.  So, I thought it was a kernel error or something so I rebooted into an older kernel  can't remember which one.  Well, that didn't work, so i thought it was ndiswrapper.  I use ndiswrapper and the windows drivers for the linksys wusb54gsv2 ( they used to work , so drivers are good ).  I uninstalled ndiswrapper and removed the .sys files from /etc/ndiswrapper/wusb54gvs2/  then reinstalled ndiswrapper and put the .sys back where they belong. ( the usb adapter was not plugged in while i was doing any of this by the way.) then i put in the modification to the usb power controller, ( forget what it's called ) opened a terminal
typed
ndiswrapper -l
gave the correct result as it always has, device (notpresent as i hadnt connected it yet) and driver valid or whatever it is.
then
sudo modprobe ndiswrapper
waited..........nothing happened...like it didnt go to the next line like it was supposed to. 
pluged in the device
opened a different terminal
typed lsusb ........again nothing happened not even going to the next line.  so i said...ok ive messed some things up ...time to start over...thankfully ubuntu is great about that just put cd and reinstall (backing up files u want to keep of course)
so i did that, reformated and reinstalled ubuntu 8.04 from cd.  
install ndiswrapper from the cd and go from there....looks like the same thing again.  hang on modprobe ndiswrapper ...freezing all usb devices...( i have an external harddrive connected via usb and cant load files from it after doing sudo modprobe ndiswrapper.  before i run that command evertying is ok...(well no wireless internet but duh) anyway...
can someone still reading help me out, i have reinstalled like 4 times now and get the same result trying slightly different approaches..rebooting b4 modprobing ndiswrapper and same result..
any info i would be  happy to provide just let me know which terminal commands to run. thanks in advance for any help anyone can give me

---

