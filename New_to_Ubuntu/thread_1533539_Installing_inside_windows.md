---
title: "Installing inside windows"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by gannite6364 on 2010-07-18
Does anyone know why 10.4 does not have the option to install inside windows like 9.10 did?.

---

### Post by spiky001 on 2010-07-18
Hi I dont use wubi but at the bottom of the loading screen is there an icon I think that gives other options

---

### Post by waynefoutz on 2010-07-18
you can download Wubi separately here:

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by digitalcitizenx on 2010-07-18
Wubi is not very good software.

IMHO I would recommend using a virtual machine like VirtualBox, which can be freely downloaded from [this location]("http://www.virtualbox.org/wiki/Downloads").

Of course you should have about 2 gigs of RAM for this to work well, but lower amounts of RAM should work sufficiently.

This subject has been discussed many, many times and I believe the majority consensus is that Wubi should be used for a very short term trial period only and that installation of Ubuntu with Windows would benefit by the use of a virtual machine.

---

### Post by Nerevar144 on 2010-07-19
> **digitalcitizenx said:**
> Wubi is not very good software.

IMHO I would recommend using a virtual machine like VirtualBox, which can be freely downloaded from [this location]("http://www.virtualbox.org/wiki/Downloads").

Of course you should have about 2 gigs of RAM for this to work well, but lower amounts of RAM should work sufficiently.

This subject has been discussed many, many times and I believe the majority consensus is that Wubi should be used for a very short term trial period only and that installation of Ubuntu with Windows would benefit by the use of a virtual machine.

umm....  Running Ubuntu in VirtualBox is MUCH slower than running a dual boot configuration via WUBI.  So I don't think that's very sound advice.  The only difference between WUBI installed Ubuntu and liveCD installed Ubuntu is that the WUBI installed version puts Ubuntu in a root.disk file on thhe NTFS partition, which is only slightly slower than it having it's own ext3 or 4 and swap partitions.

Now I have a question.  How can I resize my WUBI installed Ubuntu residing on my NTFS Windows XP partition?  I think it can be done.  It should just make the root.disk file bigger.  Am I correct?  I'd like to give Ubuntu more space on the Ubuntu side since i've been recording lots of stuff with Audacity.  It doesn't look like gparted would be of any help here.

---

### Post by QIII on 2010-07-19
> **Nerevar144 said:**
> umm....  Running Ubuntu in VirtualBox is MUCH slower than running a dual boot configuration via WUBI.

Wubi is not an actual dual boot.

I would like to understand your research that indicates that an OS runs "MUCH" slower in a virtual machine.  Unless you have some pretty heavy lifting to test with -- and some pretty detailed testing methods -- it is not likely that a home user would notice any difference. While there is some measurable difference technically, virtualization is used extensively in the industry because the value of keeping hardware costs down through virtualization is perceived to be worth the nominal inefficiency.  I virtualize Windows and several other OSes using VirtualBox in Ubuntu.  For me, the downside is that I am stuck with the virtual hardware provided by the vm.

[http://wubi-installer.org/](http://wubi-installer.org/) appears to indicate that this officially supported installer is a way for the curious to try Ubuntu out.

It is not intended to be a final solution.

That said, it is definitely a great way to try Ubuntu out.

---

### Post by Nerevar144 on 2010-07-20
> **QIII said:**
> 
...I would like to understand your research that indicates that an OS runs "MUCH" slower in a virtual machine.  Unless you have some pretty heavy lifting to test with -- and some pretty detailed testing methods -- it is not likely that a home user would notice any difference. While there is some measurable difference technically, virtualization is used extensively in the industry because the value of keeping hardware costs down through virtualization is perceived to be worth the nominal inefficiency.  

I personally tested several apps I use and know how they behave both virtually and natively on the same physical hardware.  I tried to run windows in a VM on ubuntu, and found it too slow to run any sort of 3D (Direct3D) application.  A fact of life since the hardware is virtualized.  DirectX is one of the reasons I'm still hooked on Windows.  Wine runs windows Direct3D apps better than a VM in my experience.  So in essence it comes down to what you want to do with it.  Intensive 3D isn't an option for VMs...yet.  But if you just REALLY need MS Office, go right ahead and install Windows as a VM.  It'll work fine, but it would also work under WINE and you wouldn't need a product key for Windows like you do with the VM.

A great reason to use WUBI is the fact that it doesn't mess with the partition table on the HDD.  This is both a blessing and a curse.  It can't hibernate because of that and also the machine will be more sensitive to being powered off without being shut down first.  I had ubuntu nearly wipe out my windows partition a few times because I wasn't using the default installation options.  A WUBI installed Ubuntu doesn't carry that risk.

Anyway, back to my question.  Anyone know how to resize Ubuntu  installed via WUBI on the NTFS (Windows) partition?

---

### Post by QIII on 2010-07-20
> **Nerevar144 said:**
> I personally tested several apps I use and  know how they behave both virtually and natively on the same physical  hardware.  I tried to run windows in a VM on ubuntu, and found it too  slow to run any sort of 3D (Direct3D) application.  A fact of life since  the hardware is virtualized.  DirectX is one of the reasons I'm still  hooked on Windows.  Wine runs windows Direct3D apps better than a VM in  my experience.  So in essence it comes down to what you want to do with  it.  Intensive 3D isn't an option for VMs...yet.  But if you just REALLY  need MS Office, go right ahead and install Windows as a VM.  It'll work  fine, but it would also work under WINE and you wouldn't need a product  key for Windows like you do with the VM.
 
 A great reason to use WUBI is the fact that it doesn't mess with the  partition table on the HDD.  This is both a blessing and a curse.  It  can't hibernate because of that and also the machine will be more  sensitive to being powered off without being shut down first.  I had  ubuntu nearly wipe out my windows partition a few times because I wasn't  using the default installation options.  A WUBI installed Ubuntu  doesn't carry that risk.
 
 Anyway, back to my question.  Anyone know how to resize Ubuntu   installed via WUBI on the NTFS (Windows) partition?
 
If nobody comes along with a better answer, the documentation may help.  This is not an RTFM, just an attempt to avoid reinventing the wheel when something already exists.  If I am not mistaken, this appears to be what you are looking for.  Hope it is.  Looks like there is some risk involved.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

 (No flamethrower below.  I hope you understand that this is intended to be a gentlemanly discussion.  I realize it is an aside.)

Is yours an objective and measured assessment or subjective one with regard to speed?  

Much of what you have spoken of is a result of the virtualized hardware, which I did refer to.  That is, of course, a limitation of virtualization.  Gamers, for instance, would not have any fun at all in a VM.

As for "messing" with partitions... people multi boot all the time.  It just shouldn't be done by a novice charging into it -- and Wubi gives people a chance to explore before tackling something like that.  There are dual booting instructions aplenty and there is always this forum to help folks get it right.  Maybe it doesn't seem dangerous to me due to the fact that I have been doing it for so long?

---

### Post by kepps03 on 2010-07-20
I tried using Wubi @ first. It crashes and does not install inside windows like it use to. Just either use VirtalBox by Oracle (free) or shrink your hard drive and dual boot! Wubi stinks.

---

